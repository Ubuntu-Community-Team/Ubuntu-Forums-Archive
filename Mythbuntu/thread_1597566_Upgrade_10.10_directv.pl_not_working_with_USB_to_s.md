---
title: "Upgrade 10.10 directv.pl not working with USB to serial"
date: 2010-10-15
forum: Mythbuntu
---

### Post by Peldar on 2010-10-15
Hi all,

I thought the upgrade had broken my live tv feed, however further investigation showed that live tv failed to start because myth could not change the channel with the directv.pl script.

Still debugging, has anyone seen similar issues with the upgrade and how it affects USB -> serial communications?

---

### Post by Peldar on 2010-10-15
unloading and reloading module seams to correct, other threads indicate issue with kernel

sudo modprobe -r pl2303
sudo modprobe pl2303

Now USB serial working, and directv.pl script also.

---

### Post by lledurt on 2010-10-17
Peldar,
I have the same problem, but your your solution did not seem to fix it.  Do you have any other suggestions.  I also pressed the red reset button on both of my Directv boxes for a few seconds.
In myth I get the black screen then back to the menu.  PS -aux shows several stray directv.pl precesses running. Running 'directv.pl on' seems to send it for a loop and doest return anything.  I have to use cont-c to get out of it.
I would appreciate any other ideas you or anyone else has.
P.J.

---

### Post by IceCap on 2010-10-19
> **lledurt said:**
> Peldar,
I have the same problem, but your your solution did not seem to fix it.  Do you have any other suggestions.  I also pressed the red reset button on both of my Directv boxes for a few seconds.
In myth I get the black screen then back to the menu.  PS -aux shows several stray directv.pl precesses running. Running 'directv.pl on' seems to send it for a loop and doest return anything.  I have to use cont-c to get out of it.
I would appreciate any other ideas you or anyone else has.
P.J.

  Few months ago the directv.pl stopped working all of a sudden for me (maybe it was some small update).  Here is what I did that fixed it:

```
chmod 777 /dev/ttyS0
```

  This was to fix possible access issues with the serial port (make sure you are using ttyS0 for your directv.pl).

  The second thing that I did was to reinstall the setserial package.  Honsetly, I don't know which one did the trick but try these.  It might work.  Note that was on 9.04, so YMMV.

  IC

---

### Post by lledurt on 2010-10-21
I fixed it.  directv.pl is in the precess of being updated for the 10.10.  The test version worked for me.

[http://www.pdp8online.com/directv/directv_test.pl](http://www.pdp8online.com/directv/directv_test.pl)

I think he is going to put out the new final version in a few days.

---

### Post by drumz on 2010-11-22
Thank you, the new script (following the link you posted) worked.

---

### Post by grummel1 on 2011-01-11
Try to type

```
stty -F /dev/ttyUSB0 clocal
```

before running your script.
(I had a similar problem 
with a prolific 2303 usb-to-
serial converter
after an upgrade to 
ubuntu 10.10).

---

