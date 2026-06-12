---
title: "Can't get remote to work"
date: 2010-08-14
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-08-14
I have had my Mythbuntu box for almost 2 years now, and have never got my remote control to work. It's about time I did.That's my job for this weekend.

I have just upgraded to 10.04, and was delighted to find after doing so that I can now move the cursor about on the Ubuntu desktop using my remote, so at some level, something must be working (even that much never worked in previous versions). However, it doesn't do anything in the MythTV frontend.

I suspect it is something to do with not having the right lircd.conf file.

First question: I have seen conficting descriptions of the correct location of the lircd.conf file. Mythbuntu seems to have put it in /etc/lirc, but the instructions [here]("http://www.mythtv.org/wiki/LIRC") say it is in /etc. Does it matter? Any idea which is correct? 

My remote is some kind of Imon device, but the trouble is I'm not entirely sure which. It came with my case, a Silverstone Grandia GD02. If I run lsusb I get the following output:

```
15c2:0035 SoundGraph Inc.
```

The case has an LCD display, which connects as a separate monitor.

I have tried running irw, and nothing I press on the remote does anything. That would be a result of the wrong lircd.conf file, right? I've tried using various lircd.conf files, but without success. I wonder if I should have restarted something after putting the file in place? Or isn't that necessary?

I have also tried running irrecord, to see if that gives me any clues (or if all else fails, so that I can create my own lircd.conf file), but without success. When I try to run it, I get the following output:

```
irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
```

I tried stopping lircd by typing "sudo killall lircd", but that didn't help. I also tried running irrecord as sudo in case it was a permission thing, but again, I got the same error message. Is there something else I should be doing to get irrecord to work?

I'm running out of ideas now. Any thoughts or suggestions would be very welcome.

Many thanks
NM

---

### Post by ozybushwalker on 2010-08-15
Remote control support, in my opinion, is the murkiest area of Mythbuntu. I have found it very hard to get any documentation on how the USB based remote controls interface with LIRC, consequently it is difficult to determine why a particular remote control that is described as Windows Media Centre Edition compatible doesn't work. And "genuine Microsoft" Windows Media Centre Edition remote controls don't seem to be available in Australia. Fortunately I've been able to use the remotes that came with my tuner cards, but getting them working hasn't been very straightforward. Though I have a couple of different types of "MCE compatible" I'm reluctant to do any experimentation with them for fear of breaking what I already have working and it taking a long time to get the problem sorted out.

---

### Post by NautiusMaximus on 2010-08-18
Sorry, a lot of questions there, and I don't suppose anyone is going to be able to answer all of them.

I suspect the most productive avenue for me to try will be irrecord. If anyone has any suggestions for what I need to do to get that working, that would be great.

---

### Post by LowSky on 2010-08-18
You need to set up the controller using LIRC. the Soudgraph iMON has been suported for a while now.

The easiest thing to do is to go into synaptic and reinstall LIRC, it will bring up lirc's configuraiton screen and you should be able to pick your remote control.

[http://www.mythtv.org/wiki/Imon#iMON_PAD_Remote_Control](http://www.mythtv.org/wiki/Imon#iMON_PAD_Remote_Control)

---

### Post by NautiusMaximus on 2010-08-21
Thanks for the suggestion, LowSky, but sadly, no joy.

I re-installed LIRC from Synaptic as you suggested, but the behaviour is exactly the same as before. The remote moves the cursor in the Ubuntu desktop, but does nothing in MythTV frontend, and I still can't run irrecord.

I didn't see any configuration screen after the reinstallation. Perhaps if I could call it up from somewhere it would help?

Any other suggestions? If I can just figure out what I need to do to run irrecord, everything I've read suggests that that's likely to be very helpful.

---

### Post by NautiusMaximus on 2010-08-28
Bump

---

### Post by LowSky on 2010-08-28
Go into Mythbuntu Control center, pick the remote from their under the infared option.

al check out the link I supplied last time, it should help with additional setup

---

### Post by NautiusMaximus on 2010-08-29
Oh my god! It actually bloody works!

Thanks very much for your help, LowSky. I had actually tried doing as you suggest before, but this time I did the same and then rebooted the computer after doing so, which seemed to make all the difference.

When I say "it works", of course, that is slightly overstating the case. Pressing buttons on my remote control while in the MythTV front end now affects the behaviour of the machine, although you probably won't be too surprised if I tell you that it doesn't do so in an entirely predictable and useful manner.

Still, that is serious progress. Now that I have it sort of working, I dare say with the help of some googling and the fact I can now learn something about what key presses are doing what from irw (which now gives me useful output), I am in with a fighting chance of sorting it all out.

I'll start a separate thread if I run into further trouble.

---

### Post by NautiusMaximus on 2010-08-29
OK, well now I have it working much better. The strange behaviour that happened at first turned out to be due to a considerable number of duplicate entries in the auto-generated lircrc file. Once I removed all the duplicates, everything pretty much just worked.

Hurrah!:D

---

