---
title: "New Intel drivers for mobile 915GM/GMS, 910GML"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by knubbe on 2006-01-07
Finally there are new drivers on Intel.com for the Intel 910 and Intel 915 chipset. Dated 1/5/2006! (the previous version was from 2004 :???: )

[Click here]("http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1862&lang=eng") and choose Linux from the drop-down box.

Anyone who has tried it yet? The readme says Suse is the only OS supported.. but maybe it works anyway?

Sincerely

---

### Post by no1wantdthisname on 2006-01-08
Meh, got my hopes up.  Tried to install, but just shows a bunch of errors.  

I'm probably just be doing it wrong though.

---

### Post by mo_x on 2006-01-08
[QUOTE=no1wantdthisname]Meh, got my hopes up.  Tried to install, but just shows a bunch of errors.  

I'm probably just be doing it wrong though.[/QUOTE]
Posting the errors might give you some help :)

---

### Post by no1wantdthisname on 2006-01-08
Well, I've already removed the files but here's what I did.
The dri-intel*.tar.gz file contains a folder called xc.  I've seen this folder while building X.org so I tried compiling by doing make World.  Just a bunch of errors.  ./configure and make don't work either.

So I just aliened the dri-intel*.rpm file.  The only important thing that I can see installed is a archive in /usr/X11R6/dripkg.  This archive contained another folder named dripkg.  
There's an install.sh file in this folder so I just did sudo sh install.sh.
During the compiling of modules, there's some error and it doesn't work.

That's as far as I got before giving up.  The readme.txt on the website doesn't give any help in installing the drivers either, so I'm not even sure how to correctly install this.  I'm getting tired of trying to fix this dri.
Hopefully someone else can figure it out.

---

### Post by Jeff250 on 2006-01-08
Yeah, I got about as far as you did. 	:neutral:

---

### Post by shof2k on 2006-01-09
There are some up to date drm modules are dri.freedesktop.org/snapshots.  These improved my fps from 360 to 670.

---

### Post by Xealot on 2006-10-11
Im getting this error when trying to run the install.sh script

Makefile:173: *** Cannot find a kernel config file.  Stop.


(It's located in dri.log)
I got the full kernel source, a config in /boot and a correct symlink /usr/src/linux -> /usr/src/sourcecode

Whats wrong? :S maybe im just too tired to realize..

---

### Post by mtron on 2006-10-11
i would say you don't have the kernel headers of your current kernel installed.

---

### Post by Gargamella on 2006-10-11
i have used alien to change the rpm to debian packet,i installed it without problems,now i still have to reboot hoping it will work.

Thank you very much

---

### Post by Gargamella on 2006-10-11
mmm now i've got Mobile 915GM/GMS/910GML Ex         and
Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller    installed

and my notebook says lenovo site:
Original description: Celeron M 380(1.6GHz), 512MB RAM, 80GB 5400rpm HD, 15in 1024x768 LCD, **Intel 900**, CDRW/DVDRW, 802.11abg wireless, Bluetooth/Modem, 10/100 Ethernet, touch pad, 8c Li-Ion batt, WinXP Home

but for example my screensaver is slow and i think it doesnt work well,

i played Wolfestein 3 - enemy territory with windows and the same hardware,

do you think will work?


p.s.  new drivers didn't work for me

---

### Post by Diabolis on 2007-07-06
I tried to run install.sh like this:

```
sudo sh install.sh
```

Of course it didn't work, I got this error: "Bad fd error", After that I found this link: [http://diveintomark.org/archives/2006/09/19/bad-fd-number](http://diveintomark.org/archives/2006/09/19/bad-fd-number) And I tried this:

```
sudo bash install.sh
```

it seemed to work, but I got another error:

```
Compiling new agpgart module...
ERROR: AGPGART module did not compile
Compiling DRM module...
ERROR: Kernel modules did not compile

```
I looked at dri.log file (which was created in the same folder where install.sh is located) and it says the following:

```
make -C /lib/modules/2.6.20-16-386/build SUBDIRS=/home/gaston/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.20-16-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.

```
this is where I'm stuck

---

### Post by sgetmanenko on 2007-07-18
The script will now compile the [: 1361: ==: unexpected operator
DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


[: 1361: ==: unexpected operator
[: 1361: ==: unexpected operator

Compiling DRM module...install.sh: 1361: Syntax error: Bad fd number
stas@zaika:~/Desktop/dripkg$ 
stas@zaika:~/Desktop/dripkg$ 
stas@zaika:~/Desktop/dripkg$ 


That's my story.... dissapointing

---

### Post by sgetmanenko on 2007-07-18
Could you explain a little about this link?  [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) 
Which file is it and the installation instructions... Thanks!

---

### Post by Diabolis on 2007-07-18
I guess those are drivers too and they come in different versions for different architectures, look up for yours. I downloaded the driver from the intel site and it didn't have any instructions.

---

