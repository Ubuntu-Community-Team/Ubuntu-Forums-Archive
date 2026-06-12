---
title: "picasa won't start - how to debug?"
date: 2009-05-27
forum: Multimedia Software
---

### Post by gronkx on 2009-05-27
I have a fresh install of 9.04 (from i386, but on AMD x2 CPU).

Most things seem to work, compiz is enabled and working, sound works, and I've added the google repository.

I can install picasa fine, but it won't start.  Running "picasa" from a terminal does nothing - no error message, no warnings.

How can I enable debugging so I can figure out the problem?

Do I need to install the amd64 version of picasa?  Should I have installed the 64 bit version of ubuntu?

---

### Post by loell on 2009-05-27
try

**WINEDEBUG=1 picasa **

see if it spits any error.

---

### Post by gronkx on 2009-05-27
It seems to be working now.    For the record, I had to set the WINEDEBUG=1 as an environment variable, with:  

```
setenv WINEDEBUG 1
```I also had to remove the existing ~/.picasa directory, even though I thought I'd checked that option in synaptic when I uninstalled it.

The message that gave me the clue I needed was:

```
 regedit: Can't export. regedit: Can't export. Registry keyRegistry key
```

---

### Post by abooks on 2010-04-11
I have the same problem. This is what I get when I run Windebug1:

$ WINEDEBUG=1 picasa 
/opt/picasa/bin/wrapper: line 46:  5038 Segmentation fault      "${WINELOADER:-wine}" regedit /E $registry_export HKEY_CURRENT_USER\\Software\\Wine\\Fonts\\External\ Fonts
/usr/bin/picasa: line 139:  4943 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/opt/picasa/bin/wrapper: line 46:  5143 Segmentation fault      "${WINELOADER:-wine}" regedit /E $registry_export HKEY_CURRENT_USER\\Software\\Wine\\Fonts\\External\ Fonts
/usr/bin/picasa: line 175:  5047 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

I didn't follow how the other guy fixed it: I'm still a n00b. Can you explain it in terms clear to the meanest intelligence?

---

### Post by xc3RnbFO8P on 2010-04-11
> ~/.picasa
Its a hidden folder in your home folder,
in Nautilus (filemanager) edit> show hidden files (or use ctrl - h)
Then in Synaptic Package Manager find Picasa and **mark for complete removal**
Now you get [Picasa]("http://picasa.google.com/linux/download.html#picasa30") 
and install it again.

---

### Post by abooks on 2010-04-11
In index of file:///home there's a listing ".picasa". Am i supposed to do something with that?

By the way, do I need Wine to run this?

---

### Post by xc3RnbFO8P on 2010-04-12
> **abooks said:**
> In index of file:///home there's a listing ".picasa". Am i supposed to do something with that?
Delete the Picasa folder.

> By the way, do I need Wine to run this?
[http://picasa.google.com/linux/faq.html]("http://picasa.google.com/linux/faq.html")

---

### Post by chunky bacon! on 2011-01-26
> **Ringi said:**
> Its a hidden folder in your home folder,
in Nautilus (filemanager) edit> show hidden files (or use ctrl - h)
Then in Synaptic Package Manager find Picasa and **mark for complete removal**
Now you get [Picasa]("http://picasa.google.com/linux/download.html#picasa30") 
and install it again.

I was experiencing the same problem with Picasa from google's repository (2.7), and these instructions fixed the issue for me.  Thank you.

---

