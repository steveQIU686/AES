This repository contains a simple C implementation of AES-128 and a Correlation Power Analysis (CPA) attack targeting its first-round S-box outputs.

AES-128 consists of 10 rounds, preceded by an initial AddRoundKey operation that XORs the plaintext with the secret key. The first round then applies the nonlinear S-box to each resulting byte. The Hamming weight—the number of set bits—of these intermediate values can correlate with the device’s measured power consumption.

The CPA attack evaluates all 256 guesses for each key byte by computing the Pearson correlation between predicted S-box-output Hamming weights and measured power samples across encryptions with varying plaintexts. The largest absolute correlation identifies a candidate key byte and its associated sample position.

In our experiment, the attack recovered the full 128-bit key using 10,000 power traces collected from an STM32F417 microcontroller featuring an ARM Cortex-M4 core. Analysis completed in under three minutes on an Apple M5 MacBook Pro.
