---
title: "Trouble seeing other computers on my network."
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2009-11-05
I have 2 desktops on wireless and a laptop on wireless all running from a 54Mbps Netgear switch. The internet works fine on all of them but it's hit or miss with whether or not I can access shared folders between them. I set up a shared folder and then on another computer (they're all in my house), I go to Places - Network and I don't see it there. Sometimes I don't even see the computer that I'm actually sitting at. It's pretty random on whether it'll work or not, what gives?

---

### Post by Iowan on 2009-11-05
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for windows sharing problems... or are you using another method? Machines can ping each other (by names or addresses)?

---

### Post by Maheriano on 2009-11-05
I should have mentioned both machines are Ubuntu.

---

### Post by themattbeballin on 2009-11-05
> **Maheriano said:**
> I have 2 desktops on wireless and a laptop on wireless all running from a 54Mbps Netgear switch. The internet works fine on all of them but it's hit or miss with whether or not I can access shared folders between them. I set up a shared folder and then on another computer (they're all in my house), I go to Places - Network and I don't see it there. Sometimes I don't even see the computer that I'm actually sitting at. It's pretty random on whether it'll work or not, what gives?

I, myself, have never had much luck going through Places > Network, you may have better luck with Places > Connect to Server.

but that is with me connecting to Windows Shares, you may have a different experience connecting Ubuntu to Ubuntu.

But I have connected Ubuntu to Ubuntu going through SAMBA.

In which you may have more luck there.

Then under Connect To Server, instead of connecting to a Linux network, you select Windows Share and then so.

---

### Post by sgosnell on 2009-11-07
Since upgrading to Karmic, I'm having problems seeing my desktop.  The desktop can see the laptop, and access shared folders, but the laptop cannot see the desktop for some reason.  Both are running Ubuntu, and have samba installed, with shared folders.  Last night, just before upgrading the desktop, I could access it, and was playing music from the Music folder.  Since upgrading it to Karmic, I can no longer see it.

---

### Post by headvampyre@hotmail.co.uk on 2009-11-07
wouldnt using nfs be the best option for mainly linux

---

### Post by Iowan on 2009-11-07
Sometimes CIFS gets a bit weird with the master browser and browse lists (thanks MS...), and trying to reverse engineer it hasn't been without it's difficulties, either.  Sometimes I try to connect to a share 2-3 times before the same action mysteriously works. Sometimes, it just takes time for the information to propagate.

---

