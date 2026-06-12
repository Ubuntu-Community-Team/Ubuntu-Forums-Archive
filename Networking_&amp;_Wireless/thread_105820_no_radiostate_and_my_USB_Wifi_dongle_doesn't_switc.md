---
title: "no radiostate and my USB Wifi dongle doesn't switch on!"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by DidRocks on 2005-12-19
Hello.

I am having trouble with my TrendNet (TEW-424UB) dongle. I've used ndiswrapper (1.4, the one which ubuntu provided) to install the last xp driver (download in [www.sis.com)](www.sis.com)). This one is sis163u). I made all the installing process :
ndiswrapper -i sis163u.inf
ndiswrapper -l
 i received :
Installed ndis drivers:
sis163u driver present, hardware present

I'm starting to smile!
well, next :
depmod -a
and modprobe ndiswrapper with no kernel crashing (contrary to the same driver from my CD)

But, i see no light on my dongle ! and a iwlist wlan0 scan send me directly :
wlan0     No scan results

I read through this forum and found that i might have to replace RadioState|1 to RadioState|0 in all configuration files in /etc/ndiswrapper/sis136u . But when i opened them, i don't see any RadioState line ! I tried to put it (with 1,  then 0), with rebootin, modprobe ndiswrapper ... but nothing worked !
Any help would be greatly appreciated... 

Thanks in advance.

---

### Post by DidRocks on 2005-12-20
None of you have experienced the same issue? :???:

---

### Post by DidRocks on 2006-01-29
I'm going to be totally desperated (i don't know if we can say that in english)...

What is very strange is that when i don't connect my dongle, a sudo ndiswrapper -l make :
Installed ndis drivers:
sis163u driver present



and when i connect it :
Installed ndis drivers:
sis163u driver present, hardware present

So, my usb dongle is detected but not switch on ... What can force it to do this? please, give me some help!

---

### Post by metalheart on 2006-01-29
Hi,

Having problems with the same hardware as yours. Is the wlan0 interface showing up for you? I had problem with XP drivers with this and changed to Win98 drivers. Now the wlan0 is showing up at least. I havent got it working yet.

Update: Updated ndiswrapper to version 1.7 and the wlan0 is now up with XP drivers too. And light is on. Maybe you have to update ndsiwrapper to version 1.7. The process is described [here]("http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7")

Update2: Got it working with WPA. Look at [WPA Howto]("https://wiki.ubuntu.com/WPAHowto")

---

### Post by DidRocks on 2006-01-30
Thanks metalheart . I'll give it a try, so, i just follow WPA Howto and i drop ndiswrapper, that's it?

Just a (other) question: how do you know the name of your usb's interface?

---

### Post by gosh on 2006-01-30
lsusb

gives the names of your usb-interface

---

### Post by DidRocks on 2006-01-30
it works perfectly (with ndiswrapper 1.8 for me!)
Thanks both of you!

---

### Post by cemptor on 2006-02-15
What version of the OS do you have?

I have Dapper Drake Flight 3 for x86_64 on an Opteron 144 (64 bit) system. I've tried the ndiwrapper procedure with versions 1.8, 1.9 and 1.10 of ndiswrapper with no success. Same error as you got.

Made a debian package for ndiswrapper 1.10

Installed it using dpkg -i

installed the sis163u.inf driver using ndiswrapper -i (after editing the controls files to change "i386" to "amd64" as the architecture.

ndiswrapper -l says:
driver installed, hardware present

depmod -a gives no errors

modprobe ndiswrapper hangs

dmesg shows

"loadndiswrapper could not be started"...

please point out what I could have done wrong. 

The driver I downloaded was off the Sis website, and listed under the AMD64 folder, although to does not explicitly state it supports a 64 bit OS. Of course, no native linux driver available.

---

### Post by DidRocks on 2006-02-17
I have breezy version in 32 bits.

All your procedure looks great ...
Perhaps this is due to the 64 bits version of the driver since it worked for me with ndiswrapper 1.8 ... I'm sorry, i can't help you on this fact ... :-k

---

