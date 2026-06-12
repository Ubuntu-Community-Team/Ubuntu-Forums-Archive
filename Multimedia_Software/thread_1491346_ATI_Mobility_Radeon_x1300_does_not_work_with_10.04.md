---
title: "ATI Mobility Radeon x1300 does not work with 10.04"
date: 2010-05-23
forum: Multimedia Software
---

### Post by iluvzinta on 2010-05-23
Hi I have an ATI radeon x1300 graphics card on my Toshiba Satellite A100 P542 laptop. I am new to ubuntu. On installation, I was pleased with the mac feel as I use mac at my home. 
However, I have a big problem. I just cant get the card to work. In the hardware options, my card isn't displayed in proprietary thingy.

 I later realised that my graphic driver is no longer supported by ATI and there are no official drivers. So I tried all the alternatives available in Ubuntu software centre. I currently have everything related to ATI, fglrx, xorg etc installed. But seems like all these things are of no use, as my graphics driver still isn't recognized and I cant use Compiz fusion. Leave alone compiz fusion I cannot run good quality videos. The screen gets sluggish when I do that.

I will be really grateful if someone can help me get my graphics card (ATI radeon x1300) working. I dont want to use windows but this graphics prob on ubuntu is giving me a big headache. Pls pls pls help.

---

### Post by Mark Phelps on 2010-05-23
If you load everything you can find, why are you surprised that the result doesn't work.  The "shotgun approach" most always does NOT work in the end.

You need to remove everything associated with the fglrx driver.  There is no such driver that will work with your card and current Ubuntu versions.

You need to replace the fglrx driver with the open source driver.

The link below provides the instructions:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Rrogers on 2010-05-24
I agree with Mark.  I tried to get the fglrx working and had to take it out.  I followed the intstructions at:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
and it worked.  That page seems more extensive than the one that Mark mentioned; but I can say it worked in my case.

Ray

---

### Post by iluvzinta on 2010-05-24
@Mark @Rogers Thanks a ton for your help. Will try it out and let you know how it goes.

---

### Post by iluvzinta on 2010-05-25
Thanks guys it worked!!! Couldn't be more happier :)

---

### Post by amdemas on 2010-05-26
Hey guys I have an x1600 will this work for me as well? where do you get the open source driver from?

---

### Post by boombox1387 on 2010-06-13
> **amdemas said:**
> Hey guys I have an x1600 will this work for me as well? where do you get the open source driver from?

Hey amdemas, have you tried out Ubuntu with your x1600? Are you having problems?  I'm pretty sure the x1600 should work well with composited graphics (Compiz) out of the box.  Generally, the open source drivers are already installed when you set the computer up.  If you're having any problems, the link in Mark Phelps' post should be able to help.

Personally, I have a radeon x1300 that works well out of the box, but with Ubuntu 10.04, kernel modesetting (which allows for a pretty boot screen) was causing significant problems with sluggishness, so I had to turn that off.

Anyway, hopefully you've found an answer by now, but if you're still having problems, feel free to report back here (or start a new thread).

---

### Post by Mark Phelps on 2010-06-14
> **amdemas said:**
> Hey guys I have an x1600 will this work for me as well? where do you get the open source driver from?

I have an x1650 -- and the open source drivers work fine.

They are installed automatically when you install the OS.

---

### Post by Confused Computer User on 2010-06-15
> **Mark Phelps said:**
> I have an x1650 -- and the open source drivers work fine.

They are installed automatically when you install the OS.

I have the X1600 and I'm no happy camper. From a clean install everything is slow. I have to go to Appearance->Effects->None else it's a mess.

I've been trying to get it to work and asked around on the forum as well as googled to no end. Thing is, there are other users who encountered problems with this specific model.

---

### Post by boombox1387 on 2010-06-15
> **Confused Computer User said:**
> I have the X1600 and I'm no happy camper. From a clean install everything is slow. I have to go to Appearance->Effects->None else it's a mess.

I've been trying to get it to work and asked around on the forum as well as googled to no end. Thing is, there are other users who encountered problems with this specific model.

Definitely sounds like the same issue I had with Kernel Mode Setting.  I can't find the forum post that told me how to fix it, but here's the official Ubuntu documentation:  [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Near the top of the page, follow the directions for turning KMS off for ATI Radeon.  To save you a click, it looks like the command should be:
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```

You'll probably need to use sudo to have permissions to do this.  If you have any questions or run into any problems, definitely ask (though I don't know that I have many more answers, hopefully someone will).  Disabling KMS will probably make the Ubuntu boot screen really ugly, but at least you'll be able to use Compiz.

---

### Post by Confused Computer User on 2010-06-16
> **boombox1387 said:**
> Definitely sounds like the same issue I had with Kernel Mode Setting.  I can't find the forum post that told me how to fix it, but here's the official Ubuntu documentation:  [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Near the top of the page, follow the directions for turning KMS off for ATI Radeon.  To save you a click, it looks like the command should be:
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```

You'll probably need to use sudo to have permissions to do this.  If you have any questions or run into any problems, definitely ask (though I don't know that I have many more answers, hopefully someone will).  Disabling KMS will probably make the Ubuntu boot screen really ugly, but at least you'll be able to use Compiz.

Thanks Boom Box.

I keep getting permission denied, even with sudo.

Also, after the last update I'm noticing tearing in the image when playing videos. This only occurs with my ATI Card (by the way, when using it I disable the on-board video memory and make sure the aperture size is down to 4 MB)
When switching to the on-board memory the tearing does not occur. So for now I'll stick with the integrated video memory and wait for Ubuntu 10.10. Hopefully by then this video card mess will be sorted out.

---

### Post by cbrunhaver on 2010-06-16
Well, it's really ATI fault for dropping support (in their proprietary driver) for still very new hardware, dropping everything but their Radeon HD products.  The open source driver isn't perfect but you at least get 2D and 3D acceleration (eve nif compositing is at times glitchy).

Soon, we'll have the gallium3D ATI opensource driver.  Essentially, the video stack is undergoing what happen with the audio stack 1-2 years ago with pulseaudio / audio framework changes.

Power handling is something that isn't talked about much but I really home they sort this out in the open source drivers as well, as I'm sure there are a but of lucid users on laptops that are burning through batteries like no tomorrow using nouveau and the ati open source drivers.

---

### Post by Yellow Pasque on 2010-06-16
> **Confused Computer User said:**
> I keep getting permission denied, even with sudo.

```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy/paste:
```
options radeon modeset=0
```
Save. Quit. Restart.

> Power handling is something that isn't talked about much but I really home they sort this out in the open source drivers as well.
It's getting there: [http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=1)

---

### Post by Confused Computer User on 2010-06-17
> **Temüjin said:**
> ```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy/paste:
```
options radeon modeset=0
```
Save. Quit. Restart.


It's getting there: [http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=1)

Thank you Temüjin. I'll try this as soon as I get home and post back with reults

EDIT.
It Worked. Thank you so much. This is by far the simples solution out there and the only that worked in my case

Thank you again.

---

### Post by sagi456 on 2010-09-30
Hi all,


I have a similar problem with an X1300 Pro (RV516 - X1300/X1550 series). 

Since there is no proprietary driver support for the new Xorg (7.6) in the ATI legacy drivers I am using the open source drivers. 3D acceleration with the open source drivers only partially works (e.g. the game "glest" runs but "glest advanced engine"" won't or IF games in WINE run, they do it VERY slowly-unusable) and I even can't use compiz no matter what I try. 

And "yes" I have tried disabling kms with radeon modeset=0 but when I do so it doesn't get me anywhere..

Does anyone has a clue on how to fix it??

---

### Post by Yellow Pasque on 2010-09-30
> **sagi456 said:**
> H3D acceleration with the open source drivers only partially works (e.g. the game "glest" runs but "glest advanced engine"" won't or IF games in WINE run, they do it VERY slowly-unusable)
You can try the latest open-source driver using: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
This should make 3D a bit faster, but don't expect miracles.

> I even can't use compiz no matter what I try.
I used to have an X1300 and it ran compiz just fine using open-source drivers. You might try running the compiz-check script to see what's wrong.

---

### Post by sagi456 on 2010-10-10
> **Temüjin said:**
> You can try the latest open-source driver using: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
This should make 3D a bit faster, but don't expect miracles.


I used to have an X1300 and it ran compiz just fine using open-source drivers. You might try running the compiz-check script to see what's wrong.

Sorry but I'm a real noob concerning linux. Could you please be more specific? How do I run the compiz-check script?

---

