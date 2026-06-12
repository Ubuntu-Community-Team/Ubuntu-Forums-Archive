---
title: "Upnp, PS3, mediatomb and not me!"
date: 2008-05-22
forum: Multimedia Software
---

### Post by wishful9 on 2008-05-22
ubuntu 64 7.10 gutsy.
mediatomb installed with all dependencies.
config.xml configured correctly.
pretty lax firewall settings.
ps3 firmware 2.35 and ydl6.0.
computer says no

ps3 can't find me??? please help, i'm desperate!

i'm using belkin usb g wifi, and disconnects after ps3 search?? using original rt73usb not serial monkeys, blacklisted rt2500usb and haven't had a single problem except with ps3!

i don't have any sql servers running, and not sure if it's necessary?

---

### Post by wishful9 on 2008-05-25
bump

---

### Post by wishful9 on 2008-05-27
please help i can get mediatomb working on my mobile / cell phone.

but not on the technical marvel that is ps3!

---

### Post by amak79 on 2008-05-30
wishful9,

Is MediaTomb running on the same subnet as the PS3? You should also take a look at the MediaTomb [documentation]("http://mediatomb.cc/pages/documentation#id2535736") regarding network setup.

---

### Post by wishful9 on 2008-06-03
thanks i'll give it a go. i always thought that using same router same subnet would be set up.  mind you i don't know much!  and everyone else seems to have gotten it working first shot?

---

### Post by amak79 on 2008-06-04
> **wishful9 said:**
> i always thought that using same router same subnet would be set up.

That is usually the case but if you have multiple interfaces then MediaTomb might be binding to the wrong one. It could also be the firewall but most firewalls allow all traffic on the local network.

You might want to try [Cidero]("http://www.cidero.com/") which is a UPnP Media Controller. It's a binary Java application so you just need to download and run it. If Cidero can't see MediaTomb then it's most likely a problem with your network. 

Can you also check which NAT type you have? You can check your NAT type by doing an Internet Connection Test in the PS3 Network Settings.

---

### Post by wishful9 on 2008-06-08
subnet didn't work but i'll try couple more things from manual. eth0 is set to default and wlan0 is the only one that works, i'll play with interface settings, need to turn off ipv6 anyway.

it's type 2 nat.

i'll give cidero a try aswell.

---

### Post by wishful9 on 2008-06-08
thanks

---

### Post by Niksss on 2010-06-01
hey..
  o my system cidero is not detecting the mediatomb.. 
  my mediatomb and cidero are runnin on the same machine.. 
  the remote adress of cidero is the default one.. 
do i need to change it to that of my system... ?

wat r the configurations shud i need to do..?

thanks in advance

---

