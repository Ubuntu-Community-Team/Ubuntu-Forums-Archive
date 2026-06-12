---
title: "Ubuntu 12.10 Fresh Install, No Wired Connection + No Wireless"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by JoshuaCumming1989 on 2013-01-27
Hi all. I made a fresh install of Ubuntu 12.10 last night on my desktop computer and for some reason I'm finding it pretty much impossible to connect to the internet via ethernet and wireless. I've scoured the internet searching for solutions but nothing works. I've tried installing NDisWrapper which I've done many times before on 10.10 and above. But it says "FATAL: Module Not Found" or something similar. But I've never had any problems before, I've always found NDisWrapper pretty easy to install, without any hitches, until now that is.

My ethernet interface is an Intel Corporation 82567V-2 Gigabit Network Connection.

My network controller is a Realtek Semiconductor Co., Ltd RTL8190 802.11n Wireless LAN

The network controller is being stated as being unclaimed, whereas the ethernet interface is not. I have no idea what that means but I've seen people bring up the whole unclaimed thing before so I thought that'd be handy to know.

Any help would be fantastic.

---

### Post by robbie 348 on 2013-01-27
I had a similar problem a while back. I switched the computer off, unplugged it for about a minute, re-booted and it found everything.

---

### Post by JoshuaCumming1989 on 2013-01-27
Yeah I've been installing different packages since last night and trying different supposed solutions I've found online, most of which have stated that you need to reboot so certain changes can be put in place. Rebooting hasn't solved the issue mate.

---

### Post by JoshuaCumming1989 on 2013-01-27
Oh and I should probably mention this too. I was about to try a fresh install of 12.04, but the booted USB wouldn't connect to the internet either so I guess the same problem is occurring with 12.04 too.

---

### Post by JoshuaCumming1989 on 2013-01-27
I have just "fixed" the "FATAL: Module NDisWrapper not found" error by uninstalling the version provided by Ubuntu and installing the latest. Unfortunately. Now NDisGTK is telling me my wireless driver is invalid which I know is untrue because it's the driver I've always used.

---

### Post by JoshuaCumming1989 on 2013-01-27
Sorted! Turns out I was stupidly using a x64 driver when I should've been using x86. If anyone needs any help with NDisWrapper on Ubuntu 12.10, be sure to let me know!

---

### Post by stans on 2013-03-12
Joshua ! Thanks for your offer to help as I will take you up on it. I also am getting the 'unclaimed' message... and was confused as it appears that ndiswrapper isn't installed but does respond to 

stan@stan-DX4300:~$ ndiswrapper -l
net819xp : driver installed
	device (10EC:8190) present

BUT -

stan@stan-DX4300:~$ modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


I copied rtl819xp.sys and net8190.inf from a working windows 7 system (64 bit).

If I have the wrong version of the driver would I still be getting the response indicating device present ?

---

