---
title: "eth0 wont connect"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by bknight99 on 2011-03-07
Hello all, I'm a linux newb trying to play with xubuntu on an older machine and dual boot with xp already installed. I burned the iso and tried it out on my laptop as a live cd and it connected to the internet fine.  When i put it on the machine as a live cd or to install it won't auto configure and connect. I have also tried to give it a static ip, and I made sure auto dhcp is enabled on my router. Are there any other tips and or tricks to try and get it to configure? Can this have anything to do with xp already being installed? Thanks in advance for your time and patience with us newbs!

---

### Post by RyanRahl on 2011-03-07
It wouldn't have anything to do with WinXP. It's most likely a driver problem. Find out what chip-set the network interface has and check for compatibility. I've personally never had a NIC not work but i'm sure it's possible, try a different NIC if you have one laying around.

---

### Post by Cheesehead on 2011-03-07
1) Open a Terminal window. Accessories --> Terminal
You can make the window bigger. It helps.
You will probably need to to several cut-and-paste actions
To COPY from the Terminal, use SHIFT+CTRL+C
To PASTE into your web browser, use CTRL+V

2) Do the following command
```
lspci -vv
```
It will print you a big list. Network device entries are clearly labelled. Find the entry for your flaky network interface (wired? wireless?) and post that entry here (not the whole response, please).

3) Do the following command
```
ifconfig
```
Find the entry for your flaky network interface (wired? wireless?) and post that entry here.

4) [wireless only] Do the following command
```
iwconfig
```
Find the entry for your flaky network interface and post that entry here.

---

### Post by bknight99 on 2011-03-07
Hey thanks for all your help. I did find another nic and threw it in. Got the same result. So I took the long route and built a static ip for the mac. It appears to work so far, I'll let you know when I can get back to downloading updates. Thanks

---

