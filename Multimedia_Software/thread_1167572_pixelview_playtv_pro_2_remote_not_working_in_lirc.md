---
title: "pixelview playtv pro 2 remote not working in lirc"
date: 2009-05-23
forum: Multimedia Software
---

### Post by vigmax on 2009-05-23
Hi i have a pixelview playtv pro2 pv-4500 card which has a H-338 remote.
please guide me how to configure the remote
i got the card working but can't get the remote working
My bttv config:
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=70 tuner=43 radio=1 automute=0 pll=1

Thanks in advance

---

