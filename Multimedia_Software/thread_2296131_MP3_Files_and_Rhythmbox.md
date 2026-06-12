---
title: "MP3 Files and Rhythmbox"
date: 2015-09-23
forum: Multimedia Software
---

### Post by tb75252 on 2015-09-23
I am using Ubuntu 14.04 LTS, 64-bit.

I would like to be able to play MP3 files such as the one on this site:  [http://somafm.com/metal/](http://somafm.com/metal/)

I did install "ubuntu-restricted-extras".  Nevertheless, when I click on the link for the MP3 file, Rhythmbox opens but nothing else happens.[URL="http://somafm.com/metal/"][COLOR=#000000]

Any ideas why?[/COLOR]
[/URL]

---

### Post by mc4man on 2015-09-23
look for it in Rb's radio tab.

---

### Post by tb75252 on 2015-09-23
> **mc4man said:**
> look for it in Rb's radio tab.
Aaah, now I understand!  Thank you very much for your help.

---

### Post by Dasmat_Besra on 2015-09-27
Hello @tb75252 are you able to play mp3 and mp4 files in your ubuntu trusty?

---

### Post by tb75252 on 2015-09-27
> **Dasmat_Besra said:**
> Hello @tb75252 can you able to play mp3 and mp4 files in your trusty?
Not sure I understand what you mean with "trusty"...
I am able to play mp3 files with Rhythmbox after having followed mc4man's instructions.
I am not familiar with mp4 files.  Perhaps somebody else can offer some help with that?

---

### Post by Dasmat_Besra on 2015-09-27
Ubuntu 14.04 can be called as Trusty. By the way can you please provide me the mc4man's post link where he described about how to play mp3 files. Thanks

---

### Post by tb75252 on 2015-09-27
> **Dasmat_Besra said:**
> Ubuntu 14.04 can be called as Trusty. By the way can you please provide me the mc4man's post link where he described about how to play mp3 files. Thanks
Here is the link:  [http://ubuntuforums.org/showthread.php?t=2296131](http://ubuntuforums.org/showthread.php?t=2296131)

---

### Post by Dasmat_Besra on 2015-09-28
> **tb75252 said:**
> I am using Ubuntu 14.04 LTS, 64-bit.  I would like to be able to play MP3 files such as the one on this site:  [http://somafm.com/metal/](http://somafm.com/metal/)  I did install "ubuntu-restricted-extras".  Nevertheless, when I click on the link for the MP3 file, Rhythmbox opens but nothing else happens.[[COLOR=#000000]  Any ideas why?[/COLOR] ]("http://somafm.com/metal/")Could you please help me to install the "ubuntu-restricted-extras".  How did you done that & does it requires internet connections to install?

---

### Post by tb75252 on 2015-09-28
> **Dasmat_Besra said:**
> Could you please help me to install the "ubuntu-restricted-extras".  How did you done that & does it requires internet connections to install?
Hi.  Follow these instructions:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

In essence, you will issue two commands:
```
sudo apt-get install ubuntu-restricted-extras
```
and
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

