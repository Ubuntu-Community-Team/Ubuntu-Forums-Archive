---
title: "Graphics driver"
date: 2009-08-09
forum: Multimedia Software
---

### Post by jet-san on 2009-08-09
Hi lads

This is my card:
PCI-E Graphics:      512MB ATI HD4850

I've just changed my Ubuntu 32 bit to 64 version.
Last time for drivers I've downloaded this file:
"ati-driver-installer-9-4-x86.x86_64.run".
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)
It works fine, but there is something in my Hardware Drivers.
[http://img37.imageshack.us/img37/7138/screenshot2d.png](http://img37.imageshack.us/img37/7138/screenshot2d.png)
Should I activate it or just install drivers like I did last time?
What do u recommend?

Regards
Jet

P.S.
I wanted to transfer some files to another computer.
I've created new folder "Lifeboat" in "Documents" and went to "Sharing Options".
I've ticked all 3 boxes ("Share this folder", "Allow other...", "Guest access".
Then I tried to get in there from my brother's PC (Win XP).
I've typed "\\168.xxx.x.xx" and pressed "Enter".
IE told it can't find such a file...
It's actually a directory not a file, so what should I do now?
I've tried "\\168.xxx.x.xx/Lifeboat" - doesn't work as well.

---

### Post by Narada on 2009-08-09
You can go ahead with the installation if you want. You may prefer to just use the fglrx package from the Ubuntu repos instead, though. Please read this page in its entirety: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

In regards to the second part of your post, do you have [Samba installed](https://help.ubuntu.com/community/SettingUpSamba)?

---

### Post by jet-san on 2009-08-09
> **Narada said:**
> (...)In regards to the second part of your post, do you have [Samba installed]("https://help.ubuntu.com/community/SettingUpSamba")?

```
samba
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4

```I thought I can just right-click on a folder, choose "Sharing Options" and that's it.
Anyway I have no idea how to connect to this folder from another PC.

Should I install Samba?

---

### Post by Narada on 2009-08-09
You need Samba if you want to browse it over a network with Windows, so yeah. The 'Sharing Options' is just permissions for any other Ubuntu users you have on your system.

---

### Post by jet-san on 2009-08-09
I've been looking for Samba and found this:
[http://img20.imageshack.us/img20/1881/shareo.png](http://img20.imageshack.us/img20/1881/shareo.png)
Is it enough to share files?

I've installed Samba anyway.
What's next?:>

---

