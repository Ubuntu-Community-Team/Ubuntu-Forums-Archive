---
title: "Youtube video is black--hit dead end in the instructions"
date: 2009-10-20
forum: Multimedia Software
---

### Post by MontoyaF1 on 2009-10-20
Hi,

I'm new to Ubuntu and am rather new to Linux.  I have 9.0.4 on a Gateway MX3215 laptop.  When I go into youtube.com, the video is black with no controls displaying.  Here is what I've done so far:

1.  Downloaded newest version of Adobe Flash from Adobe's website for Ubuntu
2.  Someone said that I needed to "reboot Firefox", whatever that means.  I tried rebooting the laptop and it still doesn't work
3.  Tried following instructions in this thread:

[https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/34022](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/34022)

and it told me to do these steps:

[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

I got to the part where I search for "medibuntu" in the Synaptic Package Manager, but when I search I find nothing.  

Now what do I do?

---

### Post by Niko Johnson on 2009-10-20
try this code.. you might not have the flash plugin installed
```
 sudo apt-get install flashplugin-nonfree 
``` you need to install flash before you can use it :)

---

### Post by MontoyaF1 on 2009-10-21
Thanks, I think that took care of it!
:)

---

### Post by kmrs75 on 2009-10-23
i got the same problem and this is what i get when i 
sudo apt-get install flashplugin-nonfree

ken@ken-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ken@ken-desktop:~$ 


it still is black no video

---

### Post by mdsmedia on 2009-10-23
> **kmrs75 said:**
> i got the same problem and this is what i get when i 
sudo apt-get install flashplugin-nonfree

ken@ken-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ken@ken-desktop:~$ 


it still is black no video

I'm in the same situation, but for me, I think it's because of something I HAVE installed, rather than something I HAVEN'T installed, because YouTube was no problem previously, but now it won't play videos.

---

