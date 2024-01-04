# Poker Keys Generation

The purpose of this repo is to brute force search for keys which enable to uniquely identify a poker hand with a few sums, bitshift and bitmask.

It turns out that such keys exist and are small enough to encode a card (among 52) in 32 bits.

Cf. conversation [this rust-lang forum conversation](https://users.rust-lang.org/t/rust-vs-c-vs-go-runtime-speed-comparison/104107).

The runtime is crazy fast.

## Run

Commands:

```sh
# run
cargo run --release
```

Output:

```txt
---------- key_gen_suit ----------
start key_suit
n_sol=1  - key=[0, 1, 26, 36]
n_sol=2  - key=[0, 1, 28, 39]
n_sol=3  - key=[0, 1, 29, 37]
n_sol=4  - key=[0, 1, 32, 39]
n_sol=5  - key=[0, 2, 30, 39]
n_sol=6  - key=[0, 2, 31, 38]
n_sol=7  - key=[0, 3, 30, 35]
n_sol=8  - key=[0, 3, 32, 37]
n_sol=9  - key=[0, 3, 33, 38]
n_sol=10 - key=[0, 3, 34, 39]
n_sol=11 - key=[0, 4, 34, 39]
n_sol=12 - key=[0, 5, 32, 35]
n_sol=13 - key=[0, 5, 34, 37]
n_sol=14 - key=[0, 5, 35, 38]
n_sol=15 - key=[0, 5, 35, 39]
n_sol=16 - key=[0, 5, 36, 39]
n_sol=17 - key=[0, 7, 36, 38]
n_sol=18 - key=[0, 7, 38, 39]
n_sol=19 - key=[0, 8, 36, 37]
n_sol=20 - key=[0, 9, 37, 39]
n_sol=21 - key=[0, 10, 35, 36]

runtime = 2.521934ms

---------- key_gen_flush_five ----------
start key_gen_flush_five
bootstrap -> keys=[0, 1, 2, 4, 8, 16, 32, 0, 0, 0, 0, 0, 0]
key[7]=56 - runtime key=7.063µs, total=7.121µs
key[8]=104 - runtime key=7.001µs, total=16.613µs
key[9]=192 - runtime key=15.834µs, total=34.273µs
key[10]=352 - runtime key=34.449µs, total=70.568µs
key[11]=672 - runtime key=112.758µs, total=185.256µs
key[12]=1288 - runtime key=297.355µs, total=484.966µs
runtime = 487.248µs
key=[0, 1, 2, 4, 8, 16, 32, 56, 104, 192, 352, 672, 1288]

---------- key_gen_flush_seven ----------
start key_gen_flush_five
bootstrap -> keys=[1, 2, 4, 8, 16, 32, 64, 128, 0, 0, 0, 0, 0]
key[8]=240 - runtime key=109.268µs, total=109.315µs
key[9]=464 - runtime key=229.071µs, total=341.85µs
key[10]=896 - runtime key=646.945µs, total=990.718µs
key[11]=1728 - runtime key=1.771158ms, total=2.763919ms
key[12]=3328 - runtime key=4.810497ms, total=7.579193ms
runtime = 7.585494ms
key=[1, 2, 4, 8, 16, 32, 64, 128, 240, 464, 896, 1728, 3328]

---------- key_gen_face_five_parallel ----------
start key-gen-face-five
bootstrap -> keys=[0, 1, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
key[3]=22 - runtime key=74.545µs, total=74.583µs
key[4]=94 - runtime key=39.853µs, total=117.955µs
key[5]=312 - runtime key=78.19µs, total=198.485µs
key[6]=992 - runtime key=338.141µs, total=538.795µs
key[7]=2422 - runtime key=937.108µs, total=1.480134ms
key[8]=5624 - runtime key=1.931103ms, total=3.41773ms
key[9]=12522 - runtime key=4.55858ms, total=7.988386ms
key[10]=19998 - runtime key=4.862458ms, total=12.861756ms
key[11]=43258 - runtime key=21.126663ms, total=34.00014ms
key[12]=79415 - runtime key=31.878195ms, total=65.888516ms
runtime = 65.898854ms
key=[0, 1, 5, 22, 94, 312, 992, 2422, 5624, 12522, 19998, 43258, 79415]

---------- key_gen_face_seven_parallel ----------
start key-gen-face-seven
bootstrap -> keys=[0, 1, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
key[3]=22 - runtime key=70.365µs, total=70.409µs
key[4]=98 - runtime key=47.363µs, total=120.718µs
key[5]=453 - runtime key=240.734µs, total=363.939µs
key[6]=2031 - runtime key=1.966433ms, total=2.332749ms
key[7]=8698 - runtime key=3.07561ms, total=5.413021ms
key[8]=22854 - runtime key=8.197314ms, total=13.621627ms
key[9]=83661 - runtime key=78.407706ms, total=92.039178ms
key[10]=262349 - runtime key=420.376551ms, total=512.427753ms
key[11]=636345 - runtime key=1.429980545s, total=1.942419178s
key[12]=1479181 - runtime key=5.961829758s, total=7.904258582s
runtime = 7.904269558s

```
