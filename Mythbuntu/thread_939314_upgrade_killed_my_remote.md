---
title: "upgrade killed my remote"
date: 2008-10-05
forum: Mythbuntu
---

### Post by trubblemaker on 2008-10-05
I just upgraded and lots of things went bad... the last on on my list is to get my remote back to working...

On install it was a matter of picking my remote and all the work was done for me this time I can't get it to work at all.

irw => no results

it's a hauppage pvr-350 remote and worked just before I did the upgrade.

Any idea's welcome.

---

### Post by nrune on 2008-10-05
Go into mythbuntu control center.

Go to IR devices

Disable any remote that is present.

Apply

then go back to IR Devices

Select your remote, it should be there

and Apply.

Should fix it. 

Mike

---

### Post by trubblemaker on 2008-10-06
Thanks for the help, I tried several times and variants on your idea with no luck.  Should I uninstall and re-install lirc?

---

### Post by DemonBob on 2008-10-06
post your /var/log/daemon.log

---

### Post by trubblemaker on 2008-10-06
didn't have anything related in my
/var/log/daemon.log

Here's excerpt of the last couple of minutes including reboot. (edited to get to the point)
```

Oct  6 23:05:20 telli lircd-0.8.3pre1[5296]: accepted new client on /dev/lircd
Oct  6 23:05:20 telli lircd-0.8.3pre1[5296]: could not get file information for /dev/lirc0
Oct  6 23:05:20 telli lircd-0.8.3pre1[5296]: default_init(): No such file or directory 
Oct  6 23:05:20 telli lircd-0.8.3pre1[5296]: caught signal

```

Here's relevant dmesg entry:

```
[   74.841283] lirc_dev: IR Remote Control driver registered, at major 61 
[   75.063077] lirc_pvr150: ivtv i2c driver #0: no devices found

```

---

### Post by trubblemaker on 2008-10-06
if it helps output of trying to run irw:
```
 connect: Connection refused

```

---

### Post by trubblemaker on 2008-10-07
turns out lirc hadn't been fully installed for some reason.  Running```
 sudo dpkg --configure -a
```
Fixed the remote .(Could use *irw *to see the buttons being pressed.)

After that I used myth-control-center to configure the remote.

I have no idea why the lirc wasn't installed, but now it's fixed.

Thanks for the help!

---

