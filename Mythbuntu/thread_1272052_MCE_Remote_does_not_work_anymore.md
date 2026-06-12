---
title: "MCE Remote does not work anymore"
date: 2009-09-21
forum: Mythbuntu
---

### Post by menny on 2009-09-21
Hi,
A weeks ago my mceusb2 (RC-6, "Windows Media Center Remotes (new version Philips et al.)") remote stopped working.
After several tries to activate it, I re-installed Mythbuntu 9.04.
This did not solved the problem.
So, I installed Windows 7, and the remote worked perfectly there....
So, I re-installed Mythbuntu.
The remote does not work, but I found out the followings:
There is no error when LIRC loads:
```
menny@laura2:~$ sudo /etc/init.d/lirc restart --verbose
 * Stopping remote control daemon(s): LIRC                                                                                                            [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                                           [ OK ]
menny@laura2:~$

```

But "irw" does not output anything.
If I kill the lircd, and do mode2, I get signals:
```
menny@laura2:~$ sudo killall -9 lircd
menny@laura2:~$ sudo mode2 -d /dev/lirc0
space 100000
pulse 2700
space 850
pulse 500
space 400
pulse 450
space 400
pulse 500
space 850
pulse 500
space 850

```

Anyone care to help?
I'm quite confused...:confused:

Menny

---

### Post by novellahub on 2009-09-22
In the Mythbuntu control center, are you checking the option to dynamically map the remote control functions when selecting the mceusb2 remote (Infrared Devices)?  I had to do that option with my HP mceusb2 RC6 remote.

---

### Post by menny on 2009-09-22
@novellahub, tried it, didn't fix my problem.
Thanks.

---

### Post by oobe-feisty on 2009-10-09
Hi menny thanks for all your great work on fill_mythvideo_metadata.pl
are you still having problems? 

it is most likely a problem with your lircd.conf or hardware.conf 

the best way to test is to run irrecord and see if you can generate your own if you can then it is most likely a problem with the lirc generated configs ( make sure you shut down lircd first)

attached are some configs i use for my mce remote not the same as the one above but similar i have used the one you have before though and should work with the configs also 

make sure you have your lircrc files set properly

---

### Post by menny on 2009-10-09
> **oobe-feisty said:**
> Hi menny thanks for all your great work on fill_mythvideo_metadata.pl
are you still having problems? 

it is most likely a problem with your lircd.conf or hardware.conf 

the best way to test is to run irrecord and see if you can generate your own if you can then it is most likely a problem with the lirc generated configs ( make sure you shut down lircd first)

attached are some configs i use for my mce remote not the same as the one above but similar i have used the one you have before though and should work with the configs also 

make sure you have your lircrc files set properly

Hi, actually, i solved it a few weeks ago, and I used the same method you described.
Thanks for the support.

The problem was the mceusb codes file (they were specified in the hardware.conf file, as you said). Once i regenerated the codes with irrecord, it started to work.

Thanks for offering you help :)

Menny

---

### Post by doobiest on 2010-02-03
> **oobe-feisty said:**
> Hi menny thanks for all your great work on fill_mythvideo_metadata.pl
are you still having problems? 

it is most likely a problem with your lircd.conf or hardware.conf 

the best way to test is to run irrecord and see if you can generate your own if you can then it is most likely a problem with the lirc generated configs ( make sure you shut down lircd first)

attached are some configs i use for my mce remote not the same as the one above but similar i have used the one you have before though and should work with the configs also 

make sure you have your lircrc files set properly


I can confirm your config file works with my mediagate IR02(K) on Karmic.  strange that such an old post would give me full functionality vs. the default mce config in the latest ubuntu version.

---

