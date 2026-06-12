---
title: "Media Sharing"
date: 2009-06-10
forum: Multimedia Software
---

### Post by neo_omni on 2009-06-10
My son has a laptop running vista. How can I connect my Ubuntu laptop to his (on existing wireless network) to watch the video media he has stored on his hard drive.

---

### Post by mikeym on 2009-06-10
Create a share on his computer by right clicking the folder and on share. 

You may need to install windows file sharing called samba (or smbfs for the client).

```

sudo aptitude install smbfs

```

On the ubuntu machine click on places and network then browse for his computer and open the share. (This is the easiest way.)

There's much more info [here.]("https://help.ubuntu.com/community/SettingUpSamba")

---

