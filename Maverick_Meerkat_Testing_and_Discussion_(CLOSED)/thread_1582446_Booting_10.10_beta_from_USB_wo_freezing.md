---
title: "Booting 10.10 beta from USB w/o freezing"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by radbis on 2010-09-26
Hi Everyone,
It's a just small trick.

[LIST=1]
[*]Download Universal USB Installer for Win from Pendrivelinux,
[*]Download Maverick and Lucid isos,
[*]Install Lucid with option for 10.04 with or w/o persistence, as you want,
[*]After that, open USB and copy "syslinux" folder on your desktop,
[*]Burn again same stick with Maverick,
[*]Open USB and replace syslinux folder wit that one copied on your desktop.
[*]Thats all.
[/LIST]
Enjoy your fully working 10.10 :)
Radek Biskupski

---

### Post by FishRCynic on 2010-09-26
"Download Universal USB Installer for Win from Pendrivelinux,"
Please provide link.

Does this run in wine? 


tia.

---

### Post by radbis on 2010-09-26
Here is a link:
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.7.9.9.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.7.9.9.exe)
Burn maverick on USB with 10.04 option also. There's no 10.10 option.
Regards
Radek

---

### Post by FishRCynic on 2010-09-26
> **FishRCynic said:**
> "Download Universal USB Installer for Win from Pendrivelinux,"
Please provide link.

Does this run in wine? 


tia.

thanks for the link
it is an .exe file

the 2nd question appears to be missed

Does this run in wine?

(if it doesn't then not much use to linux only users and not solved)

cheers
and again
tia.

---

### Post by cariboo on 2010-09-26
The solution the op posted should work no matter what you use to create a usb device, as all it does is use an older version of syslinux.

---

### Post by radbis on 2010-09-26
You are absolutely right. Win app is just for example. Making a bootable stick are many ways.
With syslinux we should wait for a stable version, hope so ;)

---

### Post by FishRCynic on 2010-09-26
Irregardless of line 1 then:

Sorry I still do not understand why syslinux is to be downgraded.

the first thread this was an issue in was a broken flash drive. a new flash drive solved the problem.

related threads concerned an 10.04 issue making the 10.10 beta live usb.
I have created and booted several today from a sept 2 maverick iso (amd64)
with no issues. (using lucid amd64 Startup disk creator)
(I could not duplicate the problem this is solving)
so after a brief bout of google

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

This bug was fixed in the package usb-creator - 0.2.24

---------------
usb-creator (0.2.24) maverick; urgency=low

  [ Mario Limonciello ]
  * Mangle whether the 'ui' keyword is in syslinux.cfg based on the OS version.
    (LP: #608382)

  [ Colin Watson ]
  * GTK frontend: don't grey out "Make Startup Disk" when the source is a
    physical CD.
  * Use python-debian for Ubuntu release version comparison.
  * Add an --allow-system-internal option (Unix only) to allow installation
    to system-internal devices such as hard disks. This is useful when
    preparing test USB images in KVM.
 -- Colin Watson <cjwatson@ubuntu.com> Tue, 07 Sep 2010 10:40:37 +0100



*************************************************************************

Is this a work around for and if so is there still an issue with lucid not creating a maverick bootable live usb?

If this is an issue with syslinux then it would suggest that the boot cd itself is not bootable from which the live usb is being made.

---

### Post by radbis on 2010-09-26
Very nice investigation :) Couldn't find nothing like this.
problem is very clearly described, but those are just hypothesis.
I tried many changes in original syslinux.cfg including remove "ui". No effect. of course it happened because burned with 10.04 profile, but many people did it this way. So this is for them.
So, I prefer to have and play with working Maverick rather than thinking what more could I change or fix or burning from cd by startup disk creator on other Linux distro. or some other way. I mean this is temporary, just for a while. You can go this way or other.
Lucid syslinux is tested and work for me. I don't aspire to be guru on Linux. If is working then is funny.
Regards
Radek

---

### Post by julianb on 2010-09-26
radek, i like your solution better than  the solution i used (which also worked) ... i installed lucid from a usb stick, and then upgraded it to maverick using the command line (server) instructions here 
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by RJ12 on 2010-10-01
Ok, right now I don't have a Linux Machine available, but I want to test Maverick. So I burnt Lucid to my USB, but I don't see a "syslinux" folder, only an "isolinux" one. Which files do I need to copy over. I attached a screenshot of the contents of my flash drive.

---

### Post by cariboo on 2010-10-01
I'll provide the screen shot :)

---

### Post by RJ12 on 2010-10-01
> **cariboo907 said:**
> I'll provide the screen shot :)

Hmm...

Should I rename ISOLINUX to SYSLINUX?

Edit: Wow! I forgot the screenshot, here it is

---

### Post by cariboo on 2010-10-01
Are you sure you've got the right image? 10.04 uses isolinux, while Maverick uses syslinux. I noticed that today, as the thumbdrive I used previously had Lucid on it.

As an aside, the only way I've been able to create a reliable usb drive using Win 7, is using unetbootin, I've never been able to get the included windows utility to work.

---

### Post by RJ12 on 2010-10-02
Well, radbis said to make a lucid USB and copy the syslinux folder to my desktop, and then make the maverick usb and put the syslinux folder from your desktop and replace it with the one on the USB.

---

### Post by RJ12 on 2010-10-02
I am so stupid! All I had to do was get the newest version of Unetbootin and BAM! I am loving the RC and the new Ubuntu Font!!

---

