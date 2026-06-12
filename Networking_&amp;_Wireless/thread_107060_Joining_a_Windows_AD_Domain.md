---
title: "Joining a Windows AD Domain"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by zachariah on 2005-12-22
Greetings all

First of all, thanks to the Ubuntu community for providing a Linux distro that works straight away and actually manages to successfully use a Windows AD server to log on. This is just the sort of functionality that will get Linux desktops into the mainstream.

Some teething problems, all because I'm a newbie to Linux:

I used SADMS to configure a test box (Dell GX60 with Ubuntu 5.10). It boots up fine and any random Active Directory user can use their login details to get to the GNOME desktop.

Hooray! But:

1) Every login I get an error saying the HAL could not be initialised. Is this something to worry about? Everything else seems to work regardless. If a Windows box could not use the HAL (I'm assuming they both mean hardware abstration layer) it would be fatal. The error does not appear when using a local user unique to the Ubuntu box.

2) Is there a way to add a desktop shortcut to the Windows server profile folder? Every domain user has a unique folder on a Windows server (path is something like \\server\group-x\group-y\username) which holds their files. I'm sure Linux can use a start-up macro to add a link to such a folder for any given user, but I've no idea how.

Thanks in advance for replies, you'll be helping hundreds of students to move away from Windows if this is successful!

---

### Post by zachariah on 2006-01-17
OK doesn't look like too many people are interested, but here's an update:

After much further tinkering and actual learning of stuff, I've pretty much got what I wanted. Kubuntu 5.10 together with SADMS has allowed me to create a Linux box that local users can log on to with sudo privileges, while domain users can log in as well, and inside their Home folder is a link to all the network shares available on the Windows server. A few more steps required to get the 'My Docs' folder than on a Windows computer, but not a problem.

Printing is fine, as long as a sudo user has already installed the device. There's still the /dev/dsp error at startup for domain users but I can get round this.

Now comes the REALLY hard part of showing a test box off to new users.

One big remaining question:

What software do you guys recommend for saving all the settings and replicating them on an identical box? Everything should be the same except for the Host name. The monitors will also be different, is there a way to get the system to re-detect the monitor at startup? I don't fancy editing xorg.conf for every new system.

---

### Post by peatcom on 2006-04-19
Hi,

Most interesting! This is really good news to me: joining an AD domain. Could you please tell me how to do this, or where I can find information about it?

Thanks

---

### Post by vinfred on 2006-04-20
You may find more documentation about samba in [http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Process to connect to AD domain is widely explained

vinfred

---

