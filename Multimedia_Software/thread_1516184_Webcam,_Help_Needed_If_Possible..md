---
title: "Webcam, Help Needed If Possible."
date: 2010-06-23
forum: Multimedia Software
---

### Post by WelshWill on 2010-06-23
[CENTER]

**So hi there everyone, I'm new to using ubuntu, as I've had it for around 2 weeks now.  If I'm honest, I'm not really getting the hand of it right now, but I'm sure i will eventually.  **

**I can see many people have this problem too, so I'm not the only one.  Well i guess it's not really a problem but you understand where I'm coming from I'm sure.**

**Well i have been reading around on the forum, i went to this link ([HERE]("http://ubuntuforums.org/showthread.php?t=766683")).  I didn't really understand it at all!**

**My problem i have, is I'm trying to enable my cam on various sites, like Stickam,Cam4,Camfuze,Chatroullete,Tinychat, and lots more.  Me going on them sites has none of your business, so don't ask me why I'm going on them.**


**My main problem, is my cam isn't working on skype, and i go on the computer alot to speak to my girl friend, as I'm in the military, and hardly home right now.  I don't want to switch back to Vista, as i hate it. **



**I have enabled everything on, this site.  [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)  and it's still not working, so anyone do you have any information for me please?  I'd really like to fix this problem.**



**Regards, Will**
[/CENTER]

---

### Post by howefield on 2010-06-23
No one is interested in what you do with the cam, that's a promise. :) :rolleyes:

But even new users can be expected to explain the issue, cut the guff and give potential helpers some useful information.

Let's start with the make/model of the web cam ?

---

### Post by WelshWill on 2010-06-23
> **howefield said:**
> No one is interested in what you do with the cam, that's a promise. :) :rolleyes:

But even new users can be expected to explain the issue, cut the guff and give potential helpers some useful information.

Let's start with the make/model of the web cam ?


My webcam, is built into my laltpop, i have a Hp Pavilion dv9000, I'm not sure what the make of the webcam is! But it's built into my laptop, as i told you.

---

### Post by howefield on 2010-06-23
If you open a terminal and type 

```
lsusb
```

can you see it recognised, post the output of not sure.

Also, try

```
lspci
```

---

### Post by WelshWill on 2010-06-23
> **howefield said:**
> If you open a terminal and type 

```
lsusb
```can you see it recognised, post the output of not sure.

Also, try

```
lspci
```



Sorry, i sound rather dumb here, but what's a terminal? Like i said, i'm new to Ubuntu, i really don't have a clue what that is.  Sorry for me being rather dumb... i know it really does suck.

---

### Post by howefield on 2010-06-23
No worries, go to Applications > Accessories > Terminal and in the window that pops up type the command,..

Using lsusb, my cam shows gives the following output.

Bus 001 Device 003: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

Using a search engine, (like google or yahoo) you could see what you could find on the ID string.

---

### Post by WelshWill on 2010-06-23
> **howefield said:**
> No worries, go to Applications > Accessories > Terminal and in the window that pops up type the command,..

Using lsusb, my cam shows gives the following output.

Bus 001 Device 003: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

Using a search engine, (like google or yahoo) you could see what you could find on the ID string.

Ah terminal is like a Cmd panel then, there you go i learned something new ha thanks.

So i got this.

will@will-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam   <<<<--- Obviously that has to be the webcam, well if not then i guess i'm buggered.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
will@will-laptop:~$

---

### Post by howefield on 2010-06-23
> **WelshWill said:**
> Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam   <<<<--- Obviously that has to be the webcam, well if not then i guess i'm buggered.

Yep, nothing wrong with your powers of deduction ;-)

I'd search for more info using the terms "ubuntu ID 064e:a110" or something similar to that.

---

### Post by howefield on 2010-06-23
[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Looks like this camera should work fine,.

If you are trying to stream/broadcast video to the aforementioned sites, you might take a look at webcamstudio.

[http://www.ws4gl.org/](http://www.ws4gl.org/)

---

### Post by WelshWill on 2010-06-23
> **howefield said:**
> [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Looks like this camera should work fine,.

If you are trying to stream/broadcast video to the aforementioned sites, you might take a look at webcamstudio.

[http://www.ws4gl.org/](http://www.ws4gl.org/)


Works great thank you very much, great member thanks for your time!

---

### Post by howefield on 2010-06-23
> **WelshWill said:**
> Works great thank you very much, great member thanks for your time!

I love a happy ending. Good luck with your linux adventures. :p

---

### Post by markus-267 on 2010-09-14
Hi :)

I chose the model of my webcam according to a list of hardware that is known to work with Ubuntu (Hercules Dual Pix Exchange) and it works i.e. with skype. But i cant get it to connect to some websites (cam4, mebeam).

Having read your postings i tried webcamstudio. My cam worked but i don't know how to connect it with a website or how and where to direct a stream to get it working.

Are there other programs to do that in the Ubuntu-Repositories?

Thank you,
Markus

---

