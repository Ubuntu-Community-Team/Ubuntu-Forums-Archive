---
title: "Amarok 2.3.2 reports zero tracks on CD"
date: 2010-11-08
forum: Multimedia Software
---

### Post by Robertjm on 2010-11-08
Hi all,

Am having a problem with my Amarok v2.3.2 installation under Ubuntu 10.04 Lucid Lynx.

My desktop computer has only one CD drive. When I insert a CD into the machine it shows up under Local Music as "Audio CD" however, it says there are zero tracks on the disc.

If I open up the CD through Ubuntu's Nautilus folder listing I see nine .wav tracks. I can right click on one of them and tell it to open with Amarok, which does add it to the current playlist and it plays just fine. 

In doing a cursory google search I've come up with several references to this problem, but they've generally been when someone has two CD/DVD drives in their system. As I said earlier, I only have a single drive.

Robert

---

### Post by mc4man on 2010-11-08
Don't use Amarok 2, so a bit of a guess. I could imagine Amarok 2 is default configured to use /dev/cdrom
If so, it's possible your drive, even though you only have one, may have gotten 1 /dev links. (/dev/cdrom1, /dev/dvd1, ect.

To check run 
```
sudo lshw -C disk
```

If under the *-cdrom entry you see for logical name: /dev links with a 1 (or higher), then you'll need to adjust amarok 2, or just change.

To change - 
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

If there is just one entry for your cd/dvd drive then just edit the individual links, ie. remove the number 1 (or whatever it is

Ex. (your 'drive' name would be different, just remove the red
> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD+-RW_UJ-867S (pci-0000:00:1f.1-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom[COLOR="Red"]1[/COLOR]", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw[COLOR="Red"]1[/COLOR]", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd[COLOR="Red"]1[/COLOR]", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw[COLOR="Red"]1[/COLOR]", ENV{GENERATED}="1"

If there are multiple listings the easiest thing is to do is to delete all the entries, leaving just this and  reboot. The file will be rewritten, Then open it again and check, there should only be 1 drive listed. If you happen to get 1 entries again then just edit the lines as above.

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

---

### Post by Robertjm on 2010-11-08
Thanks for the suggestion.

Here's what I have:

robertjm@robertjm-desktop:~$ sudo lshw -C disk
...
*-cdrom
       description: DVD writer
       physical id: 0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r
       configuration: status=open
...

Just for kicks I checked the CD rules file and this is what I have:

SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-0:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-0:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-0:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-0:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

As you can see I don't have anything with the "1" after it so I'm not sure what to think.

Robert

---

### Post by mc4man on 2010-11-08
I remembered I had a amarok 2 install on a 64 bit maverick i'm not using. 
A little fooling around  - At first it wouldn't do anything at all, showed the disk but nothing worked.
Went into ~/.kde/share/apps/ and deleted the amarok folder and also the 3 amarok rc files in  ~/.kde/share/config

Then it played an audio cd ok.

(after that switched the /dev/cdrom to /dev/cdrom1, rebooted and amarok, while showing the disk refused to play. Deleted all the above and it still refused to play. Switched back, rebooted, deleted  the 3 rc files again and it's playing the cd.

So I'm gathering it wants /dev/cdrom which you have, so maybe try deleting  only the  3 rc files, if no good then try the folder.

---

