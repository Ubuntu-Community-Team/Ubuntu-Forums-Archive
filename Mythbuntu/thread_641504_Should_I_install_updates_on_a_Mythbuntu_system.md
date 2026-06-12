---
title: "Should I install updates on a Mythbuntu system?"
date: 2007-12-15
forum: Mythbuntu
---

### Post by vulture99 on 2007-12-15
Hi,

I used MythTV on Fedora for years but got fed up with Fedora issues (Fedora 8 = no sound...aargh!) and tried Mythbuntu 7.10 last night.  I love it!  I had it up and running in no time.  Cheers to the developers.

My question is, the Update Manager says I need to install a bunch of updates.  Do you advise installing these updates, or should I ignore them and just upgrade the entire system every 6 months as new Mythbuntu releases come out?

The updates include a bunch of Gnome and KDE related items, which seems odd since Mythbuntu uses XFCE.

Thanks!

---

### Post by uopjohnson on 2007-12-15
Not sure exactly what updates you are looking at, but I keep my three  mythbuntu systems up to data and I have not regretted it.

---

### Post by Titus A Duxass on 2007-12-16
Horses for courses.

I'm opposed to updating. Once my system is up and running I disable updates.
If it ain't broke don't fix it!

---

### Post by michalikt on 2007-12-16
I let mine update the other day and now regret it.  I have a PVR-150 with the IR receiver port and my remote no longer works.  Hopefully, they will fix it in the next batch of updates and I'll get a functional remote again.

If anyone could point me to a fix in the meantime, I'd really appreciate it.

Ted

---

### Post by axelsvag on 2007-12-16
> **michalikt said:**
> I let mine update the other day and now regret it.  I have a PVR-150 with the IR receiver port and my remote no longer works.  Hopefully, they will fix it in the next batch of updates and I'll get a functional remote again.

If anyone could point me to a fix in the meantime, I'd really appreciate it.

Ted
Are you sure you have not rebooted the system? A lot of us have problem after a reboot because the lirc seems to change and you have to adjust the /lirc/hardware.conf.

---

### Post by michalikt on 2007-12-16
> Are you sure you have not rebooted the system? A lot of us have problem after a reboot because the lirc seems to change and you have to adjust the /lirc/hardware.conf.

Yes, I did reboot.  What changes need to be made?  My conf file is:

> root@mythbox:~# cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
LIRCMD_CONF=""


Ted

---

### Post by vulture99 on 2007-12-16
> **Titus A Duxass said:**
> I'm opposed to updating. Once my system is up and running I disable updates.
If it ain't broke don't fix it!I agree.  I had too many problems with Fedora updates hosing my mythtv box.
I think I'll disable my updates too - how should I do that on the Mythbuntu system?

---

### Post by axelsvag on 2007-12-16
> **michalikt said:**
> Yes, I did reboot.  What changes need to be made?  My conf file is:



Ted

Look in this [HTML][http://ubuntuforums.org/showthread.php?t=590909&highlight=lirc1/HTML]

---

### Post by michalikt on 2007-12-16
> **vulture99 said:**
> I agree.  I had too many problems with Fedora updates hosing my mythtv box.
I think I'll disable my updates too - how should I do that on the Mythbuntu system?

Exit the Mythbuntu frontend.
Applications -> Settings -> Autostarted Applications
Uncheck the Update Notifier.

Ted

---

### Post by michalikt on 2007-12-16
> **axelsvag said:**
> Look in this [HTML][http://ubuntuforums.org/showthread.php?t=590909&highlight=lirc1/HTML]

In that thread, it said:

> I edited the line
DEVICE=""
to
DEVICE="/dev/lirc1"
saved
and restarted lirc.


I tried that but it did not help.  The only lirc item in /dev is lircd.

Ted

---

### Post by vulture99 on 2007-12-16
> **michalikt said:**
> Exit the Mythbuntu frontend.
Applications -> Settings -> Autostarted Applications
Uncheck the Update Notifier.Excellent.  Thanks.

---

### Post by uopjohnson on 2007-12-16
> **michalikt said:**
> I let mine update the other day and now regret it.  I have a PVR-150 with the IR receiver port and my remote no longer works.  Hopefully, they will fix it in the next batch of updates and I'll get a functional remote again.

If anyone could point me to a fix in the meantime, I'd really appreciate it.

Ted

I would start a new thread with this.  You should also update your lirc button mapping by checking the box for that in mcc.

---

### Post by uopjohnson on 2007-12-16
There used to be lots of problems updating fedora because the ivtv drivers would bomb out on new kernels and lots of things had to be built and configured by hand.  I've been running updated ubuntu on now mythbuntu on several machines for about a year now without ever running into a problem with updating.  I think it depends on how close to stock your configuration is.  Most of my hardware is well supported and I run a pretty clean simple configuration so I rarely see problems pop up and I often see improvements in updating.  For instance the lirc-generator update a few weeks ago fixed several problems with the haupege remotes button mappings and kernel updates often have performance and hardware updates.  Not to mention fixing critical bugs and security issues. I say stay up to date.

---

