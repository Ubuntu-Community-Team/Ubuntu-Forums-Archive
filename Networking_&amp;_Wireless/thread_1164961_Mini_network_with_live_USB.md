---
title: "Mini network with live USB"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by qandthepit on 2009-05-20
I need to demonstrate basic networking to some students. No spare machines so thought I'd connect a couple of Windoze boxes to a spare switch and boot them both into Ubuntu on live USB drives. I've given them appropriate static IPs and they can happily ping each other and talk to a printer on the same switch. But what would I need to do to demonstrate basic file sharing - i.e. browse a folder on one machine from the other? Is that even possible with this setup? (No Internet connection, obviously, so can't easily add stuff on the fly that's not already in the distro). I'm a Linux beginner - used live distros before but never to try and connect to another live distro!

---

### Post by sanderj on 2009-05-20
File Sharing on a LAN is quite easy: use your Ubuntu file browser to righ-click a directory, and then select Share (or something like that). Ubuntu will then install and activate Samba. After a a few minutes, the share can be seen by other Ubuntu (and Windows) machines.

See the description from [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> 
Ubuntu 8.04 And Later

For Ubuntu 8.04 (Hardy) and later, shared folders are created directly from the folder. Browse to the location of the folder you would like to share, right-click the folder, and choose Sharing Options. Click the Share this folder check box, and click Install Services. Enter your password, and the Samba server packages will be downloaded and installed. 


---

### Post by qandthepit on 2009-05-20
Thanks, that's what I tried in the end, and it worked great. Only trouble was, I had to temporarily connect my machines to the "real" network to grab the packages from the Internet. Is there any easier way I can integrate those packages onto the live distro beforehand? I've used Slax and that kind of thing was really easy on there - if you suddenly find you need something extra you can just dump a "module" into a folder on the USB and it includes it in the boot. Is it easy to tweak a Ubuntu live distro in advance?

---

### Post by dmizer on 2009-05-20
[Knoppix](http://www.knopper.net/) has complete networking capability on the live cd. There are howtos here: [www.pendrivelinux.com](www.pendrivelinux.com) for putting it on a USB key.

---

### Post by NyteWyyrm on 2009-05-20
You might also look at this post: [http://ubuntuforums.org/showthread.php?t=1073838&highlight=build+distro](http://ubuntuforums.org/showthread.php?t=1073838&highlight=build+distro) (I hope I'm giving you the correct link)

I haven't had time to look closely at it myself, but I recalled seeing it after reading your post.

---

