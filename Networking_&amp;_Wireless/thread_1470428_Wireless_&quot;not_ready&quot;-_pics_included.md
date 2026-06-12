---
title: "Wireless &quot;not ready&quot;- pics included"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Mr. End on 2010-05-02
Hello, I'm trying to connect to the Internet using 64-bit lucid, and I'm in quite the foggy situation. The computer recognizes the wireless card, but can not use it to connect to the Internet. here are some screenies:

First: The toolbar app: "Device is not ready"

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs518.ash1/30519_416300018102_547678102_5198906_6881503_n.jpg[/IMG]


Second: The terminal. shows that card is a Realtek 8192 (e se or u etc. I'm not quite sure) Also shows a bit of other stuff.


[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs518.ash1/30519_416300023102_547678102_5198907_1361318_n.jpg[/IMG]
 

Third: Network Connections software: not very helpful. No connection at all.


[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs518.ash1/30519_416300033102_547678102_5198908_1443708_n.jpg[/IMG] 

so my question is... What seems to be wrong and how do I fix it (eg. do I have to install a driver of some sort, change some settings around or write some fancy code etc.?) Walkthroughs are most certainly welcomed.

Thanks!

Erik

---

### Post by slouse on 2010-05-08
I had a similar problem. This solved it for me:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128)
(reinstall wpa-supplicant)

Good luck!

---

### Post by nickallex on 2010-05-08
hi there! hopefully for me to find out how to take care of this part, is there anyway that i can find out step by slow step how to connect my driver in the ttl screen what commands to use how to to find out what part works and in what way?

---

### Post by slouse on 2010-05-12
By the way, after installing some software, the grayed out "Wireless disconnected" problem re-occurred for me and reinstalling wpa-supplicant didn't help. What helped this time was the following procedure found in [http://ubuntuforums.org/showthread.php?p=9289237&posted=1#post9289237:](http://ubuntuforums.org/showthread.php?p=9289237&posted=1#post9289237:) 
detach the wire. Next, please do:
Code:
sudo gedit /etc/NetworkManager/nm-system-settings.conf
If managed = false, please change it to true. Reboot.

---

