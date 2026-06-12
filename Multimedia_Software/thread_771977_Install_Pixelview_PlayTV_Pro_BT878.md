---
title: "Install Pixelview PlayTV Pro BT878"
date: 2008-04-28
forum: Multimedia Software
---

### Post by jeffimperial on 2008-04-28
Hi, all. I have an old TV capture card that I's like to use with my newly installed and beautifully running Hardy. How to do that?

Thanks!

---

### Post by xbisont on 2008-06-21
hey, have you get it done? i have that same old card, i haven't try to get it work since i used to use win2k (few years ago), just today i decided to give it a try, but  i just found buggy howto's for some previus releases of ubuntu. so if you can help me, that would be great

---

### Post by miki81 on 2008-06-27
I have that card too.
How to ?

---

### Post by shadow-of-sin on 2008-07-14
I have that card too and have successfully managed to get it working, here's how I got it working:
1. First type the following command in the terminal:
```
lspci | grep Bt878
```
You should get an output like so:
```
04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

2. Type the following command:
```
sudo nano /etc/modules
```
Then add "bttv" on a  new line

3. Now create /etc/modprobe.d/bttv:
```
sudo nano /etc/modprobe.d/bttv
```
And copy and paste the following
```
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=16 tuner=5 radio=0 pll=1 adc_crush=0
```
note: your tuner no. may vary, there's a helpful list here: [http://mandrivausers.org/index.php?showtopic=43596](http://mandrivausers.org/index.php?showtopic=43596) (scroll down to "Tuners")

4. Now install xawtv:
```
sudo apt-get install xawtv
```

5. Now to watch tv, use the following command:
```
xawtv -c /dev/vbi0
```

(6). If you get a black screen in xawtv and some errors in the command line like this:
```
v4l2: read: Device or resource busy

```
To find out what process is using the device use this command:
```
sudo fuser /dev/vbi0
```
Then kill the process using:
```
kill <process_id- from previous command>
```
(much of this is from the tutorial here:[http://ubuntuforums.org/showthread.php?t=153935](http://ubuntuforums.org/showthread.php?t=153935) , however for some reason tvtime doesn't work for me)

---

