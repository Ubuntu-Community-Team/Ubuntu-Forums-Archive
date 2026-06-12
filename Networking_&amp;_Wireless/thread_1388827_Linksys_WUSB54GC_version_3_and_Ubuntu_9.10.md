---
title: "Linksys WUSB54GC version 3 and Ubuntu 9.10"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by azagaros on 2010-01-23
I have been through these threads with no luck to getting the thing to work. 

[http://ubuntuforums.org/showthread.php?t=1273401&page=1](http://ubuntuforums.org/showthread.php?t=1273401&page=1)
and 
[http://ubuntuforums.org/showthread.php?t=1273401&page=2](http://ubuntuforums.org/showthread.php?t=1273401&page=2)

Some where there has to be someone who has the magic info to make this thing to work on ubuntu 9.10 32/64 bit.  I am tired of getting my hopes up and getting them dashed when I pull up the nextwork manager or iwcongig info that looks like this:

```
ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

To add to the frustration with this issue every time I see some help it leads to a dead end, I see over and over for many people too.  I would like to see some magic instructions that work the first time.  I seem to get these thread between updates to and of something.  

It is things like this that make me not want to stick with a flavor of Linux and go back to the hated Windows.  Come on Linux world.  Help us become believers to change.

---

### Post by bkratz on 2010-01-23
Have you seen this one yet?

[http://ubuntuforums.org/showthread.php?t=1353044&highlight=WUSB54GC](http://ubuntuforums.org/showthread.php?t=1353044&highlight=WUSB54GC)

---

### Post by azagaros on 2010-01-23
These directions are real clear..SSID??? What the hell is it... 

I just want the card to scan for networks and come alive, like it suppose to... Am I asking too much for that?

I am experience computer user... these directions are being a little too deep for what should be simple operations or am I just being that stupid.

AuthMode == can't I have that auto? Like I don't care...I can decide that when i get that to see the networks around it...

Do I need to a clean install.....hmm I am not on the -14 I am on the -17

Forgive the questions plz... I just want info that makes the card works not warp my mind with things I don't need to be concerned with until I find a network to connect to..

I just might put this box back to the 32 bit vista that was on it to save the head ache.

---

### Post by pdc on 2010-01-23
If you copy and paste the following command in a terminal,

> lsmod | grep rt

it looks to see if any rt modules are already loaded; I understood that the rt2870 is already part of the 2.6.31 kernel that is Ubuntu 9.10 and so one may not need the drivers; 

but one may need the firmware?

the solution for some has been to blacklist some of the several rt modules that they may also have loading 

eg you will sometimes see the advice

> blacklist rt2x00lib
blacklist rt73usb

and is recommended to be inserted into the file

> /etc/modprobe.d/blacklist 

so by issuing the command at the top, it will tell you if you have already got any rt modules loading .........

---

### Post by azagaros on 2010-01-23
Those instructions were what I needed.  I pieced my way through most of it and I got a working adapter after the first reboot.  It connected to the network.

Now on to the other task is disabling the other network adapter on the laptop which wasn't as good as this one. Now that one is working crudely I believe.

The other instructions got me.  I have been looking for a solution for so long.

I appreciate the help. thank you

---

