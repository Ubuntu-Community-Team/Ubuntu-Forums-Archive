---
title: "Broadcom wireless not working on 11.10"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by bilbo.san on 2012-05-07
Hi,
I am kind of disappointed here. 
I made some research... many seem to have the same issue fixed, but I cant get it right. WHY?!?!

It was working just fine on 10.10 and now after the upgrade...
I purged and re-install, restarted over and over again. copy the WL.ko file to some few dirs... followed instructions here and there. The driver seems to be activated. But still, it doesnt work.

I beg to those experts out there to help me please.
For any help, I appreciate your time.

e.

---

### Post by anspectrum on 2012-05-07
this may not be the answer you are looking for but I faced the same kinda issue with WiFi and also with my Dell notebook mousepad (on 11.10). Did a little bit of searching but thought to better switch to 12.04 instead of spending time on Oneiric

Bingo....just what you hope for. Good luck with your search.):P

---

### Post by bilbo.san on 2012-05-07
> **anspectrum said:**
> this may not be the answer you are looking for but I faced the same kinda issue with WiFi and also with my Dell notebook mousepad (on 11.10). Did a little bit of searching but thought to better switch to 12.04 instead of spending time on Oneiric

Bingo....just what you hope for. Good luck with your search.):P

Thanks!
Did you install it from scratch? or through update and update??

---

### Post by anspectrum on 2012-05-10
Sorry for the delay.....Couldn't log into ubuntuforums because of my other commitments.

Anyways, I didn't make a clean install. Here's what I did.

1. Put in 12.04 live CD and boot from it

2. Get into the instructions page.

3. At one point it will say do you want to upgrade from XXX to YYY (provided you already have some Ubuntu installation).

4. Select above choice (upgrade)

5. Computer does some tideous job.

AND

Presto.

Good luck:p

---

### Post by bilbo.san on 2012-05-10
Thank you !
You know... I tried the LIVE CD, and worked fine. Installed the new one just now, and didnt recognize the WIFI again.

Anyway.
Thanks for the help!
e.

---

### Post by chili555 on 2012-05-10
In order to know the solution, we need to know the card you have. Please open a terminal and open and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by bilbo.san on 2012-05-10
> **chili555 said:**
> In order to know the solution, we need to know the card you have. Please open a terminal and open and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Thanks, I would really appreciate your help.
The result is: 

**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)**

Looking forward to hearing from you.

---

### Post by chili555 on 2012-05-10
Please temporarily get a wired ethernet connection and in a terminal do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Is it working now?

---

### Post by bilbo.san on 2012-05-10
> **chili555 said:**
> Please temporarily get a wired ethernet connection and in a terminal do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Is it working now?

Hey Chilli,
YES!!! it is working now. I REALLY APPRECIATE YOUR HELP! THANK YOU !!! 

But you know... it didnt work the first time. So when checking the driver, the previous STA driver was still on, so I turned it off, then re-installed the ones you told me and I am BACK ONLINE !

Thanks again!

---

### Post by chili555 on 2012-05-10
Awesome! Glad it's working. Have fun!

---

