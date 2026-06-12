---
title: "Adobe Reader Read Out Loud doesn't work in Ubuntu 14.04 LTS"
date: 2014-05-28
forum: Multimedia Software
---

### Post by 95kreaninw95 on 2014-05-28
I have managed to install Adobe Reader from Adobe's website with its .deb package just fine on Ubuntu 14.04 LTS 64-bit. [FONT=Monaco, Menlo, Consolas, Courier New, monospace][COLOR=#333333]According to [/COLOR][/FONT]AcrobatHowTo ( [https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo) ) I have installed "[COLOR=#333333][FONT=Ubuntu]libgnome-speech7" as suggested.

But when I tried to run:

[/FONT][/COLOR]```
sudo /var/lib/dpkg/info/acroread.postinst configure
```

The Terminal return:

```
sudo: /var/lib/dpkg/info/acroread.postinst: command not found
```

I found out that there is no acroread.postinst in my system. And in Adobe Reader's setting, reading option is just gray out.

 Can someone help me, how to make Adobe Reader reads out loud in my Ubuntu machine? Thanks.

---

### Post by Yellow Pasque on 2014-05-28
Acrobat's a 32-bit only affair, so make sure you have i386 libraries installed.
```
sudo apt-get install libgnome-speech7:i386 libespeak1:i386 libportaudio2:i386 libasound2-plugins:i386
```

---

