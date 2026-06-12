---
title: "URGENT!! Need to fix video driver settings"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by ossBASHA on 2007-12-03
I attempted to play around with my resolution settings as I wanted to increase it. I entered this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

I changed the video driver to "ati" which is the one I have and bumped up the resolution only to find that I get no video output. I rebooted and could not get ubuntu to boot and rebooted in recovery mode.

How can I restore the default settings?

Thanks!

---

### Post by erfahren on 2007-12-03
a backup of xorg.conf would automatically be created by that.

when you boot into Recovery Mode it will ask for the root password. If you haven't set up the root user account I don't know whether you use your own user password or not. Someone else may have to answer that if you have problems.

Anyway, once you get logged in you'll have the root command prompt - "#"
change directory to /etc/X11 - type (those are 1's not L's):
```

cd /etc/X11

```
then  (small "L"):
```

ls

```
look for one of the backups and:
```

cp xorg.conf.xxxxxxx xorg.conf

```
(replace those x's with what's in the name of the backup file)

I'd tell you to backup your current one before doing all that but it's unbootable anyway, so that wouldn't be of much use :)

to reboot from the command prompt ("shutdown -reboot now"):
```

shutdown -r now

```

good luck

---

### Post by erfahren on 2007-12-03
note: edited my post above, now it's
"If you *haven't* set up the root user account I don't know whether you use your own user password or not."

oops

---

### Post by ossBASHA on 2007-12-03
I tried that command and I think it'll fix my problem. However, I don't have root setup. I'll try to figure that out first.

Thanks a bunch

---

### Post by erfahren on 2007-12-03
just try your user password, see:
[http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

---

### Post by ossBASHA on 2007-12-03
I tried it from root and it did not work.

Can someone please help?

---

### Post by ossBASHA on 2007-12-03
Problem solved.

Thanks erfahren!

---

### Post by erfahren on 2007-12-03
what did you try exactly?

while at the command prompt (in recovery mode) did you find a backup version of the xorg.conf and copy it over the messed up one? (when I said to "cp xorg.conf.xxxxxxx xorg.conf")

that copys the backup one (which should be there) over the existing (messed up) xorg.conf

there may be other ones in there. there may be one with "safe" on the end.

at the command prompt change directory into /etc/X11 and write down what you see after doing the "list" 
```

ls

```

---

### Post by erfahren on 2007-12-03
> **ossBASHA said:**
> Problem solved.

Thanks erfahren!
ok, you posted that as I was typing.

good to hear. you're welcome!

---

### Post by ossBASHA on 2007-12-03
Btw I entered 
```
ls -l
```

Which provided a configuration that previously was not on the list. I copied it (it said default monitor setting) and it worked fine.

So, I'm back to my original problem of wanting to up my resolution from 1024*748 and not sure what to do. Not to mention scared of messing things up again :)

---

### Post by erfahren on 2007-12-04
well you mentioned that you have an ATI video card (which one?)
type:
```

lspci

```
and see the line "VGA compatible controller:"

the ati driver you selected *may* have been the open source ati driver

did you try going to System > Administration > Restricted Drivers Manager and enable the video driver? (it's not enabled by default).

btw: the proprietary driver for ATI cards is called "fglrx" If you enable it (and reboot) you can type:
```

fglrxinfo

```
you should see something like:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

note: There hasn't been great support by ATI for Linux but it's getting better. As a result, there's lots of info on these forums about ATI cards.  

Sometimes you can get more relevant search results by searching the forums using Google than the forum's search tool. in Google do like:
*name-of-video-card* site:ubuntuforums.org

---

