---
title: "TV Audio at boot"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by dlehman on 2007-04-23
When I upgraded to feisty the first time I booted I heard audio but did not know what it was didn't think much of it and thought they added some new boot effect.  I just rebooted again to repair some driver issues and had audio at boot again and recognized it as the local news this is strange not really a problem but strange.  

go figure I get tv audio at boot but can't get audio in myth :confused:

---

### Post by Neecapp on 2007-04-23
That is the most unique problem I have ever heard in my entire life and have no idea why it is happening.

But local news on boot up is kinda a funny problem to have. lol.

Hope you get it all figured out. I would say google it.. but I dunno about this one being a broad ranged problem.

:lolflag: 

Best of luck,
Neecapp

Edit:

You might want to check out this thread: [http://ubuntuforums.org/showthread.php?t=413944](http://ubuntuforums.org/showthread.php?t=413944)

---

### Post by reclusivemonkey on 2007-04-24
> **dlehman said:**
> When I upgraded to feisty the first time I booted I heard audio but did not know what it was didn't think much of it and thought they added some new boot effect.  I just rebooted again to repair some driver issues and had audio at boot again and recognized it as the local news this is strange not really a problem but strange.  

go figure I get tv audio at boot but can't get audio in myth :confused:

Can you tell me a little more about how you have this setup? Onboard soundcard or PCI? TV Sound output connected to what input? etc.

---

### Post by dlehman on 2007-04-24
I have a pci sound card and a pci tv tuner card and there is a short cable that runs from the out on the tv card to the line in on the sound card I have never hand myth tv working right but tvtime has worked fine and this setup worked under windows when I used it but when I upgraded to feisty it must be tuning into the last channel I had tvtime set to its not really a problem I'm to worried about fixing I don't reboot that often and it doesn't bother me its just weird, I do with myth would work but thats a whole nother story and will probably never happen unless I get new hardware

---

### Post by reclusivemonkey on 2007-04-25
> **dlehman said:**
> I have a pci sound card and a pci tv tuner card and there is a short cable that runs from the out on the tv card to the line in on the sound card I have never hand myth tv working right but tvtime has worked fine and this setup worked under windows when I used it but when I upgraded to feisty it must be tuning into the last channel I had tvtime set to its not really a problem I'm to worried about fixing I don't reboot that often and it doesn't bother me its just weird, I do with myth would work but thats a whole nother story and will probably never happen unless I get new hardware

Sound can be a little tricky to set up in Myth unless you are familiar with it. I have a similar setup, but I needed to activate recording to the "Line-In" input on my sound card. You can have the level set to 0, and it will still record, so that you don't have the TV Audio on in the background all the time.

I found the easiest way to do this was with rexima, a console mixer. Just

```

sudo apt-get install rexima

```

The start rexima, use the arrow keys to navigate to your line in and press space (I think) to activate recording on this input. You can also use the arrow keys to set the volume to zero.

If you are only using TVTime, then there is a setting in the config to handle the volume; I think on Edgy at least the permissions were set wrong. Look for ~/.tvtime and see what the permissions are. I am at work now so I can't check, but post back if you have any problem.

---

### Post by vickistan on 2007-04-30
I've had and posted a similar problem. When I installed Ubuntu Dapper Drake, I noticed that the sound for tvtime was always on. I could dial it out with volume control if I wanted to play a sound file or something, but other than that, it was always there. I would love to solve this problem. I just found this:

[http://threebit.net/mail-archive/video4linux/msg00068.html](http://threebit.net/mail-archive/video4linux/msg00068.html)

which might be the answer for me. I am going to upgrade my kernel now to see if that works.

Captain Vic

---

