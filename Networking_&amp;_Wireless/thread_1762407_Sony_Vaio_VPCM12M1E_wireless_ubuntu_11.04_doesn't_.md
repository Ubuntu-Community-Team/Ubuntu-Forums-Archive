---
title: "Sony Vaio VPCM12M1E wireless ubuntu 11.04 doesn't work"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by schoe on 2011-05-19
Hello,

I've been searching all around information, how can I enable wifi, bluetooth and lan on this laptop.
However, nothing works for me...
rfkill unblock all command doesn't work.

How can I fix this problem?

If anyone can give me a clue how to do it in short time that would be just great, because I offered to my friend to repair her computer and install 'better' working Linux, but so far I even cannot enable wireless... :/

---

### Post by schoe on 2011-05-19
Hey, guys, anyone can help me? Maybe I should downgrade installation to 10.04?

---

### Post by josephmills on 2011-05-19
hi there could you please open your terminal (ctrl+alt+t) and type in ```
lspci -nn -k
``` and paste here could we also see a ```
rfkill list all 
``` thanks

---

### Post by zgqcliff on 2011-07-04
[COLOR=#c20cb9]**s**[/COLOR][COLOR=#c20cb9]**udo**[/COLOR] add-apt-repository ppa:markus-tisoft[COLOR=#000000]**/**[/COLOR]rt3090
 [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] update [COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] dkms rt3090-dkms

sudo gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]modprobe.d[COLOR=#000000]**/**[/COLOR]blacklist.conf
[COLOR=#666666]*# Blacklist conflicting RaLink driver modules*[/COLOR]
blacklist rt2800pci 
blacklist rt2800lib 
blacklist rt2x00usb 
blacklist rt2x00pci 
blacklist rt2x00lib 
blacklist rt2860sta

[http://www.techytalk.info/2011/05/ralink-rt3090-ubuntu-driver-ppa/](http://www.techytalk.info/2011/05/ralink-rt3090-ubuntu-driver-ppa/)

---

