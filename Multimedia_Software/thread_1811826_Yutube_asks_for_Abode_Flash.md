---
title: "Yutube asks for Abode Flash"
date: 2011-07-25
forum: Multimedia Software
---

### Post by nichos on 2011-07-25
Yutube asks for Abode Flash

Tried to open yutube & it asks for Abode Flash (download here for LINUX).

Downloaded it, is in downloads but, yutube does not see it.

How should I go about it.      .........THANX  ...NICK

---

### Post by haqking on 2011-07-25
if you are usinf firefox then install the flash-aid plugin.

that will donwload and install the most appropriate flash for your system.

you could also install the restricted extras

sudo apt-get install ubuntu-restricted-extras

see here for more information on it:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by nichos on 2011-07-25
Thanx will try.

---

### Post by IWantFroyo on 2011-07-25
Get the ubuntu-restricted-extras package.

That always fixes it.

I didn't know about flash-aid until now though... I'll try it sometime.

---

### Post by Theredbaron1834 on 2011-07-25
Or you can get flash video replacer. It is by the same author as flash aid, I do believe. At least with youtube, it lets you use vlc/mplayer/totem, ect instead of flash. Really good for me, cause my slow eeepc can't really play youtube well, but mplayer does it great.

---

### Post by nichos on 2011-07-26
Thanx all,       _**SOLVED**_

was chasing my tail trying to install it untill this kind chap said
"....you also need to install it.. It is not installed automagically.."

do this:-    sudo apt-get install flashplugin-installer 

& by miracle yutube works fine.

---

