---
title: "no networks showing up"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by deezy23 on 2010-08-15
Hello all, ive searched some threads and there are some very similar to this issue but not quite the same. i just bought a new toshiba c655 laptop and had windows 7 on it. i made the dual boot partition on it, yada yada yada, anyway, on the windows partition i can see two networks at my house. one is mine, one is my neighbors. but when i go to the ubuntu side of things not a single wifi network shows up. i did a little combing of the forums and decided to try installing the ndisgtk package which i obviously need internet for. i thought i would plug it into an ethernet cable running straight from the modom and i could connect and download no problem. however. this has turned out to be quite a mistake. ubuntu does not even recognize the fact i have an ethernet cable plugged in. this may or may not be related, but niether my ipod or my cell phone does not show up when i plug those in and when i try to mount them i get an error message that says they could not be found. help?
 
P.S. Im running 10.04

---

### Post by deezy23 on 2010-08-17
alright... so that may have stumped everyone... how about trying to put ndis wrapper on a flash drive qith my ubuntu desktop and loading it to my laptop? is that possible? because i have no internet connection with either i cannot get ndisgtk or anything from the normal channels. when i try to go to the package manager with my desktop and save it to a flash drive it saves a source code that downloads it from the web, which i, again, cannot do. is there a way, and please dont assume i know ANYTHING, to save the entire package to a flash drive and then open it on my laptop offline?
thanks for looking

---

### Post by dineshs on 2010-08-18
I think it is better to make the wired connection OK first.Can you post the results of
```
sudo lshw -C network
```and```
ifconfig -a
```when your modem is connected via ethernet cable

---

