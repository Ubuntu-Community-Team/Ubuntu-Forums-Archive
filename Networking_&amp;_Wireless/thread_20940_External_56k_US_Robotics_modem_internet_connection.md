---
title: "External 56k US Robotics modem internet connection problem"
date: 2005-03-19
forum: Networking &amp; Wireless
---

### Post by tonynewbie on 2005-03-19
Help, I'm just learning and I can't get the internet connection to work. Here is what I've done:

1. Manually setup ppp connection during installation (auto-detect did not work).
2. Ran $sudo pon.
Got error message:
/usr/sbin/pppd: pppd is unable to open the /dev/ppp device.
You need to create the /dev/ppp node by executing the following command as root:
mknod /dev/ppp c 108 0
3. Ran the above command as root.
Tried $sudo pon again. Worked!
$sudo poff worked.
Modem lights worked.
Logged out and then logged in.
pon/poff & modem lights still worked.
5. Restarted computer (I'm dual booting with Grub. Windows 98 is on hd1.)
6. pon/poff & modem lights did NOT work.
Got the same error message as before.
7. /dev/ppp had disappeared. (It was there before. I checked.)
How do I correct this?
The permissions of ppp were -rw-r--r-- (644)
Do I change the permissions? or "Make Sticky" ?
or modify Grub ? or ???
8. BTW I also tried Dialup Modem Howto from [http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)
with the same results.

Thanks for any help.

---

### Post by alastair on 2005-03-19
What version of Ubuntu? On my v5 (hoary) system, device "ppp" is created via "udev" from the config file :

/etc/udev/links.conf

Which includes a line (amongst others) :

M ppp	c 108 0

---

### Post by tonynewbie on 2005-03-19
My Ubuntu is Warty 4.10

tonynewbie

---

### Post by tonynewbie on 2005-03-23
Problem solved. I updated to the latest versions of programs on my system (for Warty 4.10) and now my modem settings are remembered.

tonynewbie

---

