---
title: "WLAN Issue on HP Mini 110-3014TU (Lucid)"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by linuxser on 2011-02-09
I have problem with my Netbook WLAN. I install Ubuntu Lucid 10.04 LTS Desktop to my HP Mini 110-3014TU. Anything work except WLAN, Sound, and Camera.
I've try any problem solutions from Ubuntu Official site, This forum, and also from HP Forum, but no one that work.

Please help me...!!!

---

### Post by mikewhatever on 2011-02-09
How about the output of **lspci** for a start.

Welcome to the forum.:p

---

### Post by linuxser on 2011-02-09
Anything is working normally except WLAN, Sound(fix now), and Camera....

---

### Post by Sanji_ on 2011-02-09
> **linuxser said:**
> Anything is working normally except WLAN, Sound(fix now), and Camera....

Hi, could you give me detail for fixing your sound?
I have the same problem with you. I just buy this netbook yesterday, and really want to fix the sound first.
Thanks b4.

---

### Post by linuxser on 2011-02-10
> **Sanji_ said:**
> Hi, could you give me detail for fixing your sound?
I have the same problem with you. I just buy this netbook yesterday, and really want to fix the sound first.
Thanks b4.
Just install ALSA Backport Module. Your sound will working Nicely.
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

Anyone else, please help me to fixing my WLAN and Camera..... PLEASE......!!!!

---

### Post by whatthefunk on 2011-02-10
What device are you trying to connect with?

---

### Post by linuxser on 2011-02-10
what do you mean?
My machine is HP Mini 110-3014TU. I don't know what is the WLAN type, because there are no one Hardware Driver was detected on my Ubuntu Lucid.
Please Help me...!!!

---

### Post by Sanji_ on 2011-02-10
```
sudo lshw | grep Network
```I think this is WLAN for HP Mini 110-3014 :
> product: AR9285 Wireless Network Adapter (PCI-Express){CMIIW}

---

### Post by linuxser on 2011-02-10
This is Result from my Netbook HP Mini 110-3014 with that Commans:
**PCI (sysfs)**

How about your Sound Sanji_?

---

### Post by Sanji_ on 2011-02-10
My sound was fixed, thanks to you :)
Recently I installed Cheese 2.30.1 to see if my webcam works. And I think i didn't have problem with webcam.
For Wlan, I can see some hotspot from Network Manager Applet 08, but I never try to connect with that. I don't know if it's work or not.

..happy.. happy.. :D

---

### Post by linuxser on 2011-02-11
you are welcome.
I must try that... i'll share my result here...

---

### Post by linuxser on 2011-02-11
Huffffh.....
Finally, i can sleep nicely.
My Sound: Working nicely after installing ALSA Backport.
My Camera, Working too after Installing Cheese Webcam Booth. Thanks Sanji_
My WLAN, finally working nicely after doing tutorials at [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) and [http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963). Thanks All

---

