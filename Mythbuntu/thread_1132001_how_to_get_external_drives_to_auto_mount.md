---
title: "how to get external drives to auto mount?"
date: 2009-04-21
forum: Mythbuntu
---

### Post by Arminius on 2009-04-21
I'm using mythbuntu, and when myth tv starts up automatically, I click on avi, and nothing happens, because the drive they are stored in has not mounted yet, so I have to exit, mount them, then go back into mythtv front end.

so yes how can I make the usb drives auto mount as soon as I boot up mythbuntu?

---

### Post by AlecJ on 2009-04-22
Your not on your own with this one, I've been trying since 8.04 to get an external usb drive to auto mount without any joy. Playing with fstab just upsets the whole system.
I've asked the developers over on #ubuntu-mythtv-dev, still no joy.

Still lets see where this gets us

---

### Post by nickrout on 2009-04-22
have you tried unplugging and plugging the drive back in?

---

### Post by AlecJ on 2009-04-22
yes, next time you come to boot up it still will not auto mount.

---

### Post by WinkingChicken on 2009-05-06
If you want drives to mount automatically at boot time,  add them to your /etc/fstab.

an entry similar to this for my ext3 drive w/ disklabel "bull":
LABEL=bull /disks/bull     ext3     rw            0    2

if you don't want booting to stop if the drive is unplugged or not powered up,  change the last field from 2 to 0.

Another option is  to install package "thunar-volman".   With that package installed,  you can set options to auto-mount external drives using the hotplug system.  I'm not sure if this method will automount on bootup,  or just on login.  I know it works to automount external drives when you are already logged in (that's what I use it for). Prefs are set via System > preferences > removable drives and media.

---

### Post by rtrevor on 2009-05-08
I've had a similar problem - finally worked around it last night by adding an entry for the drive in fstab like this:

UUID=xxx   /media/extHDD   ext4   relatime,user   0   0


and then in XFCE go to the sessions configuration and add a new program to run on startup, command "mount /media/extHDD". I think you need the 'user' option in fstab to allow this to work, as the system then allows a user to mount the partition as defined in fstab without root permissions.


Thanks WinkingChicken - originally the computer failed to boot every time because the external drive had not powered up by the time fsck ran, but it now works with the above - needed to change the last column to a zero!

---

