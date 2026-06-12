---
title: "Setup a PPPOE connection on Ubuntu 10.04"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by JuneMTL on 2010-04-29
Hi everyone, I'm new to this forum.....:KS

I've just done a fresh install of Ubuntu 10.04 lucid lynx and as a complete linux noob I can't figure out how to setup a pppoe connection in ubuntu. ( thats after 2 hours of googling and trial and error)


Please be detailed and concise about the solutions :confused: 

Thanks for any help !!  :)

system info: 
its a laptop : Dell Studio XPS 16 connected to a Ethernet hub thats connected to a dsl modem....

---

### Post by JuneMTL on 2010-04-29
A little help please??

---

### Post by Iowan on 2010-04-29
Patience, please! Once/day is considered adequate for thread bumping - >30 minutes...

Wish I could better help with PPPOE. There are a few threads around - but none yet for 10.04. Searching for **pppoeconf** might return some results.

Good Luck!

---

### Post by JuneMTL on 2010-04-29
oh sorry! :D
Thanks for the tip!

---

### Post by Dusal on 2010-05-02
Go to System->Preferences->Network connections. And go to DSL tab and add new connection. Then you can creat new connection. After that you can connect from network manager on taskbar.

If you used pppoeconf before then you must delete settings.

open terminal and
```
sudo gedit /etc/network/interfaces
```
 delete all and leave this two lines then save and close.
```
auto lo
iface lo inet loopback
```

After reboot network manager can works.

I just upgraded 10.04 beta to 10.04 today. pppoeconf is no longer run. Then I solved my problem like this.

---

### Post by Jayakrishnan.Nair on 2010-05-23
> **Dusal said:**
> Go to System->Preferences->Network connections. And go to DSL tab and add new connection. Then you can creat new connection. After that you can connect from network manager on taskbar.

If you used pppoeconf before then you must delete settings.

open terminal and
```
sudo gedit /etc/network/interfaces
``` delete all and leave this two lines then save and close.
```
auto lo
iface lo inet loopback
```After reboot network manager can works.

I just upgraded 10.04 beta to 10.04 today. pppoeconf is no longer run. Then I solved my problem like this.
worked for me
btw pppoeconf works too.only you have to be root or a specific group(forgot name) to connect through it

when will i start posting questions,ubuntuforums has all the answers

---

### Post by shambo on 2011-03-02
Thanks for this tip. I was facing the same problem with pppoeconf.
This sorts things out. great tip.

---

