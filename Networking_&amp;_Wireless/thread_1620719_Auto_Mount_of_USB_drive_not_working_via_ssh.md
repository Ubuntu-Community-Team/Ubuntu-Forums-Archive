---
title: "Auto Mount of USB drive not working via ssh?"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by SwarfEye on 2010-11-13
So, I have this ubuntu machine that lives under my desk and is basically a utility machine.

Mainly I ssh to it and get synchronize/backup files, etc.

When I reboot, for some reason the auto mount for my usb drives doesn't work until I actually hook up the monitor and log in to the gui.  When I ssh in after reboot, I'm unable to access my USB drives!!  "Not Authorized"

I'm not sure how to mount a drive from the command line... really I just want the machine to auto mount the drives when it starts up... gui login or no.

Any suggestions?

Thanks,

Bill

---

### Post by SwarfEye on 2010-11-14
I see this has gotten no reply, so I'm posting to bump this up a bit and see if there is any help out there!

Thanks,

B

---

### Post by neospud1 on 2011-02-01
I have this same issue.

---

### Post by YesWeCan on 2011-02-01
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by jas007 on 2011-06-29
Hey,
I was having the same problem as the op. I installed usbmount
```
sudo apt-get install usbmount
```

which also installed pmount. Then using pmount I can mount the drive that would normally give a not authorized error, using
```
pmount /dev/sdb1
```

As YesWeCan said [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

hope that helps someone.
Jason

---

