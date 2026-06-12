---
title: "Can't watch Amazon Instant Video"
date: 2013-11-24
forum: Multimedia Software
---

### Post by nathan10 on 2013-11-24
Hello, I recently switched from Windows 7 to Ubuntu entirely. I am currently running 13.10, coming from 13.04, and before that 12.10. I use Chrome (NOT Chromium) and when I try to run an Amazon Prime video the player loads, then looks like its about to finish loading, then goes to a black screen like it normally does right before the video starts, and then nothing. There is just a black screen. When I go to [chrome://plugins/](chrome://plugins/) to see my plugins I see the Adobe Flash Player - Version: 11.9.900.152 is installed. I saw people saying to install "hal", unfortunately both "hal" and "libhal1" aren't in the repositories apparently. When I try to watch a video in Firefox it doesn't even load, it just says "Adobe Flash is not installed, Amazon Instant Video uses the Adobe Flash. We can take you to the Adobe website..."...etc. It basically just tells me to install Flash. Is there any sort of plugin or browser or other thing I need to get this to work on Linux? It worked fine on Windows but won't on any version of Linux I've tried. Thank you for your time.

---

### Post by send2 on 2013-11-24
While cheking for possible solutions, I found this chain of posts that might help you. I have Ubuntu 12.04 and I followed installing libhal1 and hal, but there where other sugestions, here is a chain of posts related to not being able to watch the videos on Amazon. I use Firefox and can watch videos now. Rats, the pdf copy is too big to upload. Its been awhile and I don't have the direct link to the Amazon customer forum where I saw the sugestions to use. But the sugestions I read where:

check in synaptic to see if you have hal and libhal1 already installed. If not, install both, I tried this for Firefox browser:

```
sudo apt-get install hal
```

```
sudo apt-get install libhal1
```

restart the Firefox browser and see if it works. Also, to check if hal is working 

```
ps aux | grep hald
```

if hal is not working, it needs to be started:

```
sudo hald --daemon=yes
```

Also, make sure that you have the latest flash player installed:

```
sudo apt-get --reinstall install adobe-flashplugin
```

Let me check if I can watch a video in chrome......sorry these settings don't seem to work in chrome, at least from my end. Before you do any of the above, please verify with others here that are more knowledgable than me. Maybe the above can help you....:)

---

### Post by oldos2er on 2013-11-25
Moved to Multimedia & Video.

---

### Post by cactus john on 2013-11-25
Try this

[COLOR=#555555][FONT=consolas]sudo add-apt-repository ppa:mjblenner/ppa-hal[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas] sudo apt-get update[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas] sudo apt-get install hal

This worked for me.[/FONT][/COLOR]

---

