---
title: "MythTV Remote - Where have the cusor keys gone!"
date: 2009-03-26
forum: Mythbuntu
---

### Post by tobiz on 2009-03-26
I've finally got an unbranded remote working with MythTV, almost! The remote is a UR86E X10 RF with a USB connection, the remote looks very similar to the ATI Wonder. After some problems I've now got most of the keys on the remote to control myth by setting up the /etc/lirc/lircd.conf and ~/.mythtv/lircrc.conf files. If I run irw and ircat at the same time I can see the hex codes from irw and their translation into 'button' codes and then 'button' codes to Myth config codes via ircat - great! The real problem is two important keys don't seem to affect Myth. Whilst the cursor Up and Down keys control Myth ok the cursor Left and Right have no affect, eg when selecting a movie to play navigation is only up and down, similarly for TV programme selection! I've run out of ideas as to what's wrong.  Help would be appreciated.

---

### Post by Slate8 on 2009-03-26
Can you post your ~/.lirc/mythtv config file?

---

### Post by tobiz on 2009-03-26
> **Slate8 said:**
> Can you post your ~/.lirc/mythtv config file?
Attached are the contents of my lircrc.conf file. Note this file is not held in ~/.mythtv/lircrc.conf but ~/.lircrc includes a line which 'includes' a file with the contents as attached. Note ~/.lircrc has several 'includes' such as 'include ~/.lirc/mythtv', which I've hashed out and 'include ~/.lirc/mplayer' etc which I've left in.

---

### Post by tobiz on 2009-03-26
Hi Slate8,
Thanks, you made me look at ~/.lirc/mythtv and that was the problem! There's a mismatch between the button codes for Left and Right. I think that's fixed it now. Too many config files!!

---

### Post by Slate8 on 2009-03-26
Glad you got it sorted. It did sound a bit more complicated than the default setup :)

---

