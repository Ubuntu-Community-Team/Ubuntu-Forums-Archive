---
title: "Mythbuntu 10.4 =&gt; Anyone get a soundgraph IR working?"
date: 2010-06-10
forum: Mythbuntu
---

### Post by seppl82 on 2010-06-10
Dear Colleagues,

i'm trying to get my Soundgraph device working as an infrared reciever since one week.
I've installed Mythbunbu 10.4 64 Bit and started to run all all updates.

The Fact is that the device acts as a Mouse, but i can't get it working with lirc.

**My simple question is: Is there anyone who is able to run that infrared device properly in Mythbuntu 10.4?**

Kind Regards
/Seppl

---

### Post by Modem Mercenary on 2010-06-12
Good evening, Seppl82.

  I haven't had a chance to work on the problem until now, but to answer your question...

  My imon remote and ir receiver is still responding to irrecord.  It looks like you're having the exact same problem as I, with the remote still acting like a mouse and only channel up and down is working.   Unfortunately, I'm still working on a solution. :confused:
 

So far, I have found that the lirc_imon module can take a parameter called "nomouse". I'm trying the directions found [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10") but they don't seem to be working for 10.4 as far as I can tell. 

The article says to create a file in /etc/modprobe.d called lirc.conf 

```
/etc/modprobe.d/lirc.conf
```with the following line:

```
options lirc_imon debug=1 nomouse=1 display_type=1 pad_thresh=5
```I tried the following line in my own system:

```
options lirc_imon nomouse=1
```but it didn't seem to work.  I don't know if it because 10.4 does things different from previous versions or if I'm just doing something wrong.

I'll keep you posted if I get this working properly.  Here's a [[COLOR=Blue]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1484744&highlight=soundgraph") to my original posts that contain my system specifications and lirc configuration files.

I hope to solve this problem soon... until then, Take care all!!

Mod_Merc

---

### Post by seppl82 on 2010-06-13
Hi Mod_Mec,

i've found a solution, hopefully it will help you too.
I have the Antec Fusion Micro 350 case.

ist i've added an udev rule like this

vi /etc/udev/rules/90-lirc.conf

```
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0038", OPTIONS=="ignore_device"
```

next i've did was going to the Mythbuntu Control Centrer
Go to Infrared and selct 

**"Soundgraph iMon Antec Veris"**

Now the Mouse event was away and i can use it properly.
Please check if it works for you and report it so that others have a benefit of it.

---

