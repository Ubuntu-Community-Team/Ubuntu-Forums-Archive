---
title: "Playing MP3 files on Dapper"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by textguru on 2006-12-14
How can I play MP3 files on dapper?

---

### Post by zaflaucich on 2006-12-14
Take a look [here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by sabitha on 2006-12-14
just install xmms

---

### Post by textguru on 2006-12-14
> **sabitha said:**
> just install xmms
how to install xmms?

---

### Post by sabitha on 2006-12-14
> **textguru said:**
> how to install xmms?

$ sudo apt-get install xmms

---

### Post by textguru on 2006-12-14
I have seen instruction on [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28XMMS.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28XMMS.29)

it says:
```
** How to install Multimedia Player (XMMS) **

 [LIST]
[*]Read [#General Notes]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#General_Notes")
[*]Read [#How to add extra repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")
[*]Read [#How to install Multimedia Codecs]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")[/LIST] sudo apt-get install xmms xmms-skins
wget -c [http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb](http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
[LIST]
[*]Applications -> Sound & Video -> XMMS[/LIST]
```

but I cannot find the XMMS after running these steps. What did I do wrong?

---

### Post by drphilngood on 2006-12-14
> **textguru said:**
> ...I cannot find the XMMS after running these steps. What did I do wrong?

Type this in a terminal:

```
xmms
```

---

### Post by textguru on 2006-12-14
what I actually did is when I try to run the first line, it gives me this error:

ubuntu@mypc:~$ sudo apt-get install xmms xmms-skins
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmms-skins

I already downloaded the file and unpacked it thru this command:
wget -c [http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb](http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

But I think I need to install the xmms-skins but need the right repository. Hope you might help.

---

### Post by drphilngood on 2006-12-14
> **textguru said:**
> what I actually did is when I try to run the first line, it gives me this error:

ubuntu@mypc:~$ sudo apt-get install xmms xmms-skins
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmms-skins

I already downloaded the file and unpacked it thru this command:
wget -c [http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb](http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

But I think I need to install the xmms-skins but need the right repository. Hope you might help.

See here:

[http://www.xmms.org/download.php]("http://www.xmms.org/download.php")

---

### Post by x215 on 2006-12-15
Do this.

sudo bash

(then enter your root password)

apt-get install xmms

Viola

Good Luck!

---

### Post by ZERO_SHIFT on 2006-12-15
Automatix I the best choice.

---

### Post by textguru on 2006-12-17
I have read this url: [http://ubuntuclips.org/videos/12](http://ubuntuclips.org/videos/12) and made a successful installation. Thanks for the support!

---

