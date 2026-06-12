---
title: "Moved from General: ATI card problems"
date: 2009-03-05
forum: Multimedia Software
---

### Post by dougfresh on 2009-03-05
Hey guys,

I'm still having problems with installing my ATI proprietary driver from the ATI driver page. I reformatted my computer after the last time but I am running into a black screen of death after booting up my computer. I am willing to reformat again but I don't understand what the problem is here.

My goals are:
1. Install a working driver for my ATI Radeon x1650 AGP video card
2. Have it work
3. Install WoW
4. Have it run smoothly on Ubuntu.

I have spent days trying to get this to work, read several forums, tried many solutions and none of them seem to work... either from my lack of knowledge of linux at the moment or if it is going to work or not.

I have tried installing it via Ubuntu, I have tried manually installing it using the ATI installation guide for that driver, and each time I get it installed I have the control center and once I change any of the settings and/or reboot I get a black screen. If I can help recover what I have on my Hard Drive right now by using the Live CD that would be great. I have a laptop with Windows on it that I can use, but I am not sure I can do remote desktop or how to do it. My knowledge of Linux is limited so I need some detailed instructions so I can get this working... Any help would be greatly appreciated.

Doug

---

### Post by avrilrox on 2009-03-05
Are you using the **fglrx** driver?
Do you think you could post the output of:

```
cat /etc/X11/xorg.conf

```

---

### Post by dougfresh on 2009-03-05
I am not sure. I don't know if I can boot in safe mode, and if I can will that command still work? I just have no idea what to do or where to start... The black screen of death is irritating me because I just wanna fix it so I can find a solution to this ATI driver garbage.

Doug

---

### Post by avrilrox on 2009-03-05
Are you not able to run that command in a console? Is it not letting you login graphically? If so, you can either change the session mode or boot in recovery mode as root.

---

### Post by dougfresh on 2009-03-05
I will try that when I get home. I'm just getting frustrated because I don't know how to un-do what I did lol.

So I will boot it in root and try the command listed above and post the code if it works on here...

---

### Post by avrilrox on 2009-03-05
Okay. I used to have an Ati card. I really never got it to work properly. I would either get a low performance and crappy video quality or a bad performance when rendering compiz effects.

The fglrx driver truly sucked for me when i played movies or stuff like that. The mesa driver worked awesome for me. It wasn't as good as fglrx at rendering compiz effects though.

---

### Post by Pfredpfudpucker on 2009-03-05
I had the same problem with my ATI Rathon 1300 card.  It does get frustrating, I know how you feel.  I got the card to work great after fiddling with Ubuntu for about a week.

I discovered a few things.  For your video card to work properly, you need to install video drivers which are not native in Ubuntu.  One of the first things that the program does is have you check for updates, let that happen, and then you _might_ get a message that your video drivers need to be downloaded from a third party site.  If you get that message, it will ask if you want to download and install them.  Allow that.

I reinstalled ubuntu four times before I finally figured out how to get the proper drivers (video) installed.  I discovered that if I had downloaded the incorrect drivers for anything (video player codecs for example) when I reinstalled Ubuntu, the installation program does not simply write the slate clean by repartitioning.  It leaves the files where they are, and the new install doesn't work.  I actually had to re-install Windows, at least through the partitioning process.  When I did that I would get a good new install with ubuntu.

I am sure that there was a much simpler way to have solved my problem, but running Linux is not intuitive, and many of the responses from people who want to help are eggheads, and don't understand the there are those of us who need very simple, straightforward advice.  Especially me!

It does help to read the tutorials, especially the "Sticky's from Sticky above.  If you screw it up, you can start over.  

so, I finally figured out the sequence I needed to follow to get ubuntu up and running, but like I said, it is not intuitive.  I will also say the ubuntu is one of the easiest to install and get up and running.  But because some of the drivers cannot be supported by the distribution, because they are proprietary, you have to go out and fish for them.  And after a while you begin to understand how to work with Linux, and it turns out that it is a genuine delight to be "Wniderz FREE".

Good Luck!

---

### Post by dougfresh on 2009-03-05
I guess, I am wondering if anyone knows how I can wipe my hard drive clean again I guess... I just want this video driver to work, and if there is an update via ubuntu, where would I search for it in ubuntu? I know that when I install ubuntu it usually comes up with 262 updates, but I'm not sure if the drivers that come with it support this ATI card, it works but I'm not sure I can run WoW on it which is why I need a working driver. I will keep trying and trying at this until I get it but its just painful. I really like Ubuntu and I don't want to go back to windows and I look forward to learning how to program some stuff and help dweebs like myself in the future when I look back and laugh at this.... Arg.

---

### Post by avrilrox on 2009-03-05
> **dougfresh said:**
> I guess, I am wondering if anyone knows how I can wipe my hard drive clean again I guess... I just want this video driver to work, and if there is an update via ubuntu, where would I search for it in ubuntu? I know that when I install ubuntu it usually comes up with 262 updates, but I'm not sure if the drivers that come with it support this ATI card, it works but I'm not sure I can run WoW on it which is why I need a working driver. I will keep trying and trying at this until I get it but its just painful. I really like Ubuntu and I don't want to go back to windows and I look forward to learning how to program some stuff and help dweebs like myself in the future when I look back and laugh at this.... Arg.

Install Envy and install your drivers using it.
```

sudo apt-get install envyng-gtk
```

---

### Post by dougfresh on 2009-03-05
so how do I use envy after I have installed it?

---

