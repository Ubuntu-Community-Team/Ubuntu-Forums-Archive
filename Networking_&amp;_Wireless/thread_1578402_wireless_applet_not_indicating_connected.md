---
title: "wireless applet not indicating connected"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by candtalan on 2010-09-20
I have just done a clean install of 10.04.1 for a friend (Lenovo N500 laptop) which also has 9.04  running ok anyway, and although the wireless connects ok (I chose the STA driver), when it is connected, the applet shows the red exclamation mark in the applet indicating wireless not connected, but it is actually IS connected with wireless. 

A wired connection works ok too and is indicated correctly.

The applet is functional when wireless is connecting - the curved lines radiate upwards and seem to change during the connection process. 

Any thoughts to put it right please?

tia

---

### Post by candtalan on 2010-09-20
After spending most of the day on this one I can now add that the applet seems to be part of network manager. With no replies yet to this thread, I began to think it might be seen as a display problem and not a network problem. 

Interestingly the same live usb stick I used to install this laptop runs another machine (netbook) in live session with a correct network manager applet working, so the install media was ok.

I noted that the netbook did not need a proprietary driver to run, so I went back to the problem laptop. After a number of live session experiments I decided to swap wireless drivers. At the original 10.04.1 install I had seen a choice of wireless drivers - a community B43 and a Broadcom STA. I had then chosen the STA. Partly because I had seen various forum comments that the STA appeared to indicate a very much faster speed.

The choice of driver was no longer offered to me however I gleaned that fwcutter could give the B43 driver (I think). I removed the STA driver and installed fwcutter and got the firmware in.

And guess what - the applet works great!

This suggests that the Broadcom STA driver is implicated with the applet problem. Maybe network manager is not being informed about a successful connection in wireless.

Connection information with the STA said 54Mb/s
With fwcutter b43 it says 1Mb/s.

mmm.

I do not know if these speeds are true or in fact how to verify this.

As a speed test I tried downloading the current desktop iso for a short time, and it indicated downloading at my full speed (325kB/sec) so it is hard to believe the slower speed is true, but I am a novice at assessment of wifi speed effects.

Network manager applet is shown as version 0.8
The laptop is Lenovo N500 type 4233-74G

The machine is not mine so I think it is important that the indications are correct, so I think I will stay with the non proprietary driver, also because the indicated loss of speed does not seem to be having an effect in practice?

Comments would be appreciated.

---

### Post by candtalan on 2010-09-21
Just found this which also lists a bug on this

[http://ubuntuforums.org/showthread.php?t=1471504&highlight=applet&page=2](http://ubuntuforums.org/showthread.php?t=1471504&highlight=applet&page=2)

bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270)

This was *very* good to find, at least I am not alone! I was searching for 'wireless applet' rather than network manager so many hours yesterday were spent almost going round in circles and not finding useful things.

At one point I joined someone elses rather similar thread but it was interpreted as a thread hijack by admin, although that was not my intention (apologies), but this took me about 12 hours of searching and whatever, continuously, before I had the thought to try a different driver. 

I am  a GUI guy, with very little experience of wireless, but gaining it fast just now....

---

