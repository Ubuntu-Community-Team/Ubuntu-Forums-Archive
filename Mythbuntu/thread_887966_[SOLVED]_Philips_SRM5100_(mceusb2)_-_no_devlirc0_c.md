---
title: "[SOLVED] Philips SRM5100 (mceusb2) - no /dev/lirc0 created"
date: 2008-08-12
forum: Mythbuntu
---

### Post by Lem on 2008-08-12
Bought one of these thinking - Mario has one, it's bound to work!

I've been through everything and the problems seems to stem from the fact that lirc or udev isn't creating /dev/lirc0. Googled it to death and just found people with similar problems, but no solutions.

Any ideas out there?

---

### Post by superm1 on 2008-08-12
> **Lem said:**
> Bought one of these thinking - Mario has one, it's bound to work!

I've been through everything and the problems seems to stem from the fact that lirc or udev isn't creating /dev/lirc0. Googled it to death and just found people with similar problems, but no solutions.

Any ideas out there?
Hi Lem:

It probably boils down to missing USB identifiers in the driver.  Install lirc-modules-source, and compare the USB id's in lirc_mceusb2.c (in /usr/src/lirc-0.8.3~pre1) with the output of lsusb.  See if you are missing from there.  If so, add yourself in and try to rebuild (using DKMS).  There is a howto somewhere around here that I posted indicating how to do so.

If that works for you, then you'll need to submit a patch upstream to get this working for everyone :)

---

### Post by Lem on 2008-08-13
Thanks,

I'll give it a shot and report back.

---

### Post by Lem on 2008-08-13
Sorted thanks;

For others stumbling across this, here's what you need to do.

```
lsusb
```

Note down the info for your remote, in my case;

```
0471:060d Philips
```

Install the lirc modules source files

```
sudo apt-get install lirc-modules-source
```

Go find the driver;

```
cd /usr/src/lirc-0.8.3~pre1/drivers/lirc_mceusb2
```

Edit the lirc_mceusb2.c file and add in your particulars. Scroll down to where the remotes are listed. If your vendor is not listed than you'll have to add that in. (eg define VENDOR_PHILIPS          0x0471)
NB. Philips is already listed as above.

Now add in the particulars for your remote. In my case;

```
        /* Philips SRM5100 */
        { USB_DEVICE(VENDOR_PHILIPS, 0x060d) },

```

NB. Note from the code you noted down that the first bit is the vendor code (0471) and the second the remote id. (060d)

Now it's time to rebuild the modules.

We'll start by clearing out the old one.

```
sudo dkms remove -m lirc -v 0.8.3~pre1 --all
```

Now it's time to build your new one.

```
sudo dkms add -m lirc -v 0.8.3~pre1
sudo dkms -m lirc -v 0.8.3~pre1 build
sudo dkms -m lirc -v 0.8.3~pre1 install
```

Now update the modules and restart lirc;

```
sudo rmmod lirc_mceusb2
sudo modprobe lirc_mceusb2
sudo /etc/init.d/lirc restart

```

Now run;
```
irw
```

press a few buttons on your remote and you should now get a response. You're done! (You may need to reboot to have it working in mythtv)

---

### Post by superm1 on 2008-08-13
You missed the last critical step :)

Make sure that you send a patch upstream to LIRC so that it can get into the next LIRC release.  If you would like to also see it show up in the next Ubuntu release (in the case that LIRC upstream does very infrequent releases), then submit a bug to launchpad referencing the LIRC CVS commit.

---

### Post by superm1 on 2008-08-13
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)
I've added this to the bottom so this can live on even if it gets lost in the forums :)

---

### Post by psysmic on 2009-01-31
Thanks much for the instructions

Changed the values and this worked for my 03f3:0094 Adaptec, Inc. eHome Infrared Receiver aka Adaptec AVC3610 that comes with some HP laptops

Oh, I had to add Adaptec to the vendor codes before it would make clean

---

### Post by kilian27 on 2009-03-21
Hi everyone!

I also bought this remote, and it works out of the box on Mythbuntu 8.10 (lirc 0.8.3) except for one thing:

When the system starts, the USB receiver is switched off (green light is off). I have to manually activate it by pressing the Power button on the remote. Even then, it is not recognized by the system, but I have to execute "lsusb" to get it working. After this, lircd starts automatically and everything is fine.

Can anyone confirm this behaviour? Is there anything I can do to have the receiver activated automatically?

Background of my problem: I'm running MythWelcome with ACPI wakeup. When I come home in the evening, MythWelcome is already running, but the USB receiver is still of. Activating it manually, then, does not make the remote work in MythWelcome as it was started without the receiver recognized and LIRC running.

Best regards,
Kilian

---

### Post by viniciuscarvalho on 2010-02-10
> **kilian27 said:**
> Hi everyone!

I also bought this remote, and it works out of the box on Mythbuntu 8.10 (lirc 0.8.3) except for one thing:

When the system starts, the USB receiver is switched off (green light is off). I have to manually activate it by pressing the Power button on the remote. Even then, it is not recognized by the system, but I have to execute "lsusb" to get it working. After this, lircd starts automatically and everything is fine.

Can anyone confirm this behaviour? Is there anything I can do to have the receiver activated automatically?

Background of my problem: I'm running MythWelcome with ACPI wakeup. When I come home in the evening, MythWelcome is already running, but the USB receiver is still of. Activating it manually, then, does not make the remote work in MythWelcome as it was started without the receiver recognized and LIRC running.

Best regards,
Kilian

I have the exact same problem. When system restarts I have to sudo dpkg-reconfigure lirc to get it working. 

I'm using XBMC Live 9.11 based on ubuntu 9.10. Anyone got this working?

Regards

---

