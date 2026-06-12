---
title: "WWAN problems."
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by jonjon0789 on 2010-06-12
Using Ubuntu 10.04 Lucid LTS on x64 on an HP Pavilion dv4.  I dual boot using Win7 and on Ubuntu, can see the Windows partition and all its files.  I do use Wine, for those who have shortcuts on that.  I am new to Ubuntu, so any help is totally appreciated.  Basically, I cannot connect to my 3G at work under Ubuntu.  I liked win7, but I am really getting into this Ubuntu ya know?  But no 3G can be a setback...

1. On Win7, I use HP Connection Manager to connect to AT&T 3G (using GSM technologies, aka EDGE/HSPA/UTMS).  I use an internal modem instead of a USB modem.  Modem usually comes on with that program.

2. Modem is an HP un2400 Mobile Broadband Module that uses QualComm GOBI technologies.

3. While randomly surfing thru the file system, I saw a folder called "dev" and I noticed it had alot of folders pertaining to hard drives and usb settings.  Apparently the modem connects to the laptop via an internal USB and on this path, " dev  > serial  > by-id " had a file that is a "Link to character device (inode/chardevice)."

4.  I've tried installing Qualcomm drivers in Wine along with HP software, but it says it is not stable.

... If this was windows, I'd say I'm screwed but with as many ways to customize and fix, I know I can get this working on Ubuntu 10.04

Thanks for any help,

jonjon

---

