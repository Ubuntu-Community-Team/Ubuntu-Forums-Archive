---
title: "bttv (TE104B card)"
date: 2011-09-27
forum: Multimedia Software
---

### Post by tsumaru on 2011-09-27
Hi. 

I have recently been lazy with my updates of ubuntu :o. I run a CCTV box at home that was, up until last week, running Jaunty..

(yeah.. i know.. hit me)

I have in my box 2 capture cards based off the bt878 chip and I have managed to identify it as a TE104B card. (see [http://ubuntuforums.org/archive/index.php/t-938621.html]("http://ubuntuforums.org/archive/index.php/t-938621.html")). I Upgraded to Lucid and noticed an interesting problem with the bttv driver.

my modprobe.d confing for it was as follows:

```
options i2c-algo-bit bit_test=1
alias char-major-81 bttv
options bttv card=0,0
options bttv tuner=0,0
options bttv radio=0,0
options bttv pll=1

``` 

when the PC booted i would get a stacktrace from the driver in dmesg. After a bit of research and playing with around, it would seem that it didnt like the radio/tuner options as the card doesnt have one! I have completely removed the radio option and set my tuner to "4" which according to sources is "No Tuner".

Now, i use Zoneminder.. I can add a monitor on /dev/video0 on input 0 and i get a picture! if i change that monitor to /dev/video0 input 1 i get a different picture. Good so far...

If i add a second monitor on zoneminder so that i end up with one for /dev/video0 -> 0 and /dev/video0 -> 1 i get some strange things happen!.

Both inputs display the same image (Usually the latter input). If i play around with it sometimes the card stops outputting an image altogether.

I suspect its an issue with my setup for the bttv driver as i still use the autodetect option. Does anyone have any suggestions short of testing the config with every known card and see what happens?

(P.S For those of you that come here looking for help with the card outputting a picture that looks like a TV that isnt tuned in, make sure you have the pll option for the crystal set. By default its 0)

Much appreciated

---

