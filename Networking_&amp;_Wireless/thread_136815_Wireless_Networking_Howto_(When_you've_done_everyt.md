---
title: "Wireless Networking: Howto (When you've done everything and still can't get online)"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by jasper24 on 2006-02-26
I posted this "How-To" because it took me several weeks of tweaking and playing to get my Broadcom 4318 online and working. First off, I want to say that I am not a guru and this may or may not work for you. It worked for me with wonders.

This is what I did:

1) Get fwcutter from belios.de

2) tar zvxf bcm43xx-fwcutter-003.tar.bz2

3) Make sure you have g++ and make installed in Adept before moving forward.

4) cd bcm43xx-fwcutter-003

5) make
You will see something like this:
```
cc -std=c99 -O2 -fomit-frame-pointer -Wall -pedantic -D_BSD_SOURCE
-DFWCUTTER_VERSION_=0.0.1   -c -o fwcutter.o fwcutter.c
cc -std=c99 -O2 -fomit-frame-pointer -Wall -pedantic -D_BSD_SOURCE
-DFWCUTTER_VERSION_=0.0.1   -c -o md5.o md5.c
cc -std=c99 -O2 -fomit-frame-pointer -Wall -pedantic -D_BSD_SOURCE
-DFWCUTTER_VERSION_=0.0.1 -o fwcutter fwcutter.o md5.o
```

6) sudo make install
You will see something like this:
```
install -o 0 -g 0 -m 755 fwcutter /usr/local/bin/
```

7) Now, find your device driver (.sys) and copy it into the bcm43xx-fwcutter-003 directory.

8) Go back into the bcm43xx-fwcutter-003 directory

9) Now, type "fwcutter" drivername.sys
For me, I did this:
```
fwcutter bcmwl5.sys
```
You should see the following if you did it correct:
```
fwcutter can cut the firmware out of bcmwl5.sys
  filename :  bcmwl5.sys
  version  :  3.100.64.0
  MD5      :  e7debb46b9ef1f28932e533be4a3d1a9

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more
recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the
moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
[root localhost fwcutter]# make installfw
if ! [ -d /lib/firmware ]; then mkdir /lib/firmware; fi
install -o 0 -g 0 -m 600 bcm43xx_*.fw /lib/firmware
[root localhost fwcutter]# ls /lib/firmware
bcm43xx_initval01.fw  bcm43xx_initval04.fw  bcm43xx_initval07.fw
bcm43xx_initval10.fw   bcm43xx_microcode5.fw
bcm43xx_initval02.fw  bcm43xx_initval05.fw  bcm43xx_initval08.fw
bcm43xx_microcode2.fw  bcm43xx_pcm4.fw
bcm43xx_initval03.fw  bcm43xx_initval06.fw  bcm43xx_initval09.fw
bcm43xx_microcode4.fw  bcm43xx_pcm5.fw
```

Now, if all went well, the firmware for your device should be installed.

Now, you will need to setup your essid and other network settings. I won't get into details with that, as it varies with each person.

When you're ready to try it out and everything is configured type:
```
sudo dhclient eth0
```
*eth0 is the name of my wireless device. Yours may be different (i.e. wlan0) To find the name of your device type iwconfig.

At this point, you should see the light come on and the device start to search for an AP.

I hope this helps someone. Trust me, I know how you feel, wanting to get it working and nothing working for you. Let me know if I can help.

Jasper

---

### Post by Lambert on 2006-02-26
What version of ubuntu are you running? And what kernel version?

---

### Post by jasper24 on 2006-02-26
First, I was on Kubuntu 5.10 and it worked fine. So, I got adventurous and thought I would try it on Dapper. I managed to get the card to fire up, but there appeared to be a bug and it wouldn't work. So, I popped in an Atheros card and it worked like a charm.

It's on my work box, I'll get the kernal info for you as soon as I get back to it.

Jasper

---

### Post by mweston on 2006-03-18
OK, I've tried just about everything else - so ......

matt@Dapper:~/fwcutter/bcm43xx-fwcutter-003$ sudo make install
Password:
cc -std=c99 -O2 -fomit-frame-pointer -Wall -pedantic -D_BSD_SOURCE -DFWCUTTER_VERSION_=003 -o bcm43xx-fwcutter fwcutter.o md5.o
install -o 0 -g 0 -m 755 bcm43xx-fwcutter /usr/local/bin/
matt@Dapper:~/fwcutter/bcm43xx-fwcutter-003$ fwcutter bcmwl5.sys
bash: fwcutter: command not found

It looks like I don't have FWcutter installed - what did I miss ? How do I install it ?

---

