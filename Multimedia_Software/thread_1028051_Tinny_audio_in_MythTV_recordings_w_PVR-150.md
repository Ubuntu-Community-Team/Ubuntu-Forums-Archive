---
title: "Tinny audio in MythTV recordings w/ PVR-150"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Lodurr on 2009-01-02
I previously posted that my tinny audio problem in MythTV was fixed by a fresh Hardy install, but over time, the rate of tinny audio recordings versus normal audio recordings kept increasing.  It started happening once a week, and now it happens at least every other day, and I record 5 - 10 shows daily.

By "tinny audio" I mean that it sounds as if the audio is encoded at 32 kbps.  My other recordings sound just fine.  The effect can be reproduced by changing channels repeatedly, eventually I'll get the tinny audio effect, and it will go away usually on the next tuning.

I didn't have this audio problem at all before upgrading from Feisty to Hardy, and my hardware configuration is exactly the same.

Has anyone been able to solve this problem?  Does Intrepid solve this problem?

Thanks.

---

### Post by wolfen69 on 2009-01-02
> **Lodurr said:**
> Does Intrepid solve this problem?



try the [Mythbuntu]("http://www.mythbuntu.org/") live cd (Intrepid) and see how it works.

---

### Post by Lodurr on 2009-01-08
Honestly I just cross my fingers when I start to watch a recording I really wanted, and suffer through it when it has messed up audio.

I found [_this_]("http://www.mail-archive.com/ivtv-users@ivtvdriver.org/msg04220.html") link googling and it seems to address the same problem.  However, they're talking about it in Dapper, and when I had Feisty I never had this problem.  Seems like it was fixed and then unfixed?  The post in the link says that it can be fixed by adding a 50ms pause into the IVTV driver code, but that's definitely beyond my amateur ubuntu-fu skills.

I'm reticent to convert to Mythbuntu because I spent so many hours addressing bugs and irregularities in my current install, I'm not ready to forfeit those hours and possibly run into new problems on another install.  I'll wait until my effort-to-enjoyment ratio becomes more favorable before taking that route.

---

### Post by wkulecz on 2009-01-08
> and when I had Feisty I never had this problem

Real-World 101:  If it ain't broke, don't fix it!


Many computer things are so fragile -- video editing, photo editing & printing (can almost expect it to just work on Windows), real time security monitoring, high end audio, and most certainly PVR "tivo-like" systems to name but a few -- that dedicated systems for the task can save a lot of pain.  With Ubuntu its easy and cheap to have multi-boot setup if necessary to run the version that best meets your needs for the task.

A four port KVM switch is your friend :)

--wally.

---

### Post by Lodurr on 2009-01-14
> **wkulecz said:**
> Real-World 101:  If it ain't broke, don't fix it!I think I was trying to address a different problem when someone somewhere said that upgrading to Hardy would fix that problem.  I can't remember if it did or not, but I know it caused this new problem.

Here's an example clip of one of my recordings that got unlucky and got the tinny audio bug: [http://www.mediafire.com/download.php?zjmdjdunzgi](http://www.mediafire.com/download.php?zjmdjdunzgi)

One out of every 10 to 20 recordings has this bug.

---

### Post by wkulecz on 2009-01-14
> I think I was trying to address a different problem when someone somewhere said that upgrading to Hardy would fix that problem.

That's my point about some advanced applications being "fragile", seemingly non-relavent "other issues" can break the system when addressed.

I learned long ago to have spare partations or drives to install updates to so I can preserve what is currently working "good enough" to be useful in the quest for "better".

I believe one of the major changes with 8.04 and 8.10 over what came prior was the introduction of the "pulse audio" subsystem.  This has caused audio issues for me on one of three systems I upgraded from 6.06.

The suggestion to try the Mythbuntu liveCD by Wolfen69 is a good one, and file a bug report if it also has the problem.  Look for configuration differences between it and yours if it doesn't.

--wally.

---

### Post by nerver on 2009-05-04
Hey Lodurr,

I was wondering if you ever found a solution to this? I'm currently having the same problem. On approximately 1 out of ever 15-20 channel changes the audio is garbled. Changing the channel again fixes it, but the problem is for recordings you never know which one is going to get messed up which isn't good. (and it also affects the GAF)

I've only had this card a short while and am running it on Ubuntu 8.10.

Cheers,
-Sean

---

### Post by nerver on 2009-05-04
Nevermind, I actually just found a solution right after I found this thread.

If anyone stumbles across this and want to know the fix here it is.

All i had to do was add the following line at the end of my channel change script:

```
 ( sleep 5; v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1 ) &
```

So my whole script looks like this:

```

 #!/bin/sh
 REMOTE_NAME=TTV
 sleep 1
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.8  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME Ok
 ( sleep 5; v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1 ) &
 exit 0

```

Cheers,
-Sean

---

### Post by argus2009 on 2009-11-05
Not for the faint-hearted, but an explanation/history of the problem with a kernel module (ivtv) patch is posted here:

[http://www.mythtvtalk.com/forum/ivtv-issues/12183-pvr-150-audio-issues-w-patch.html](http://www.mythtvtalk.com/forum/ivtv-issues/12183-pvr-150-audio-issues-w-patch.html)

This may help some of you where either the v4l2-ctl workarounds worked inconsistently (like for me) or cannot use the v4l2-ctl hacks because you are using the internal tuner and don't use a channel changing script ...

---

### Post by enricor77 on 2010-07-18
I recently upgraded to 10.4, I am using a PVR-150:
 Live Tv and recordings have a static popping sound. 

I tried to patch the kernel module (ivtv-1.4.0) using the suggestions found here:
[http://www.mythtvtalk.com/forum/search.php?searchid=67473](http://www.mythtvtalk.com/forum/search.php?searchid=67473)
(adapting them to the new driver)

No luck
I tried to install the bleeding edge v4l drivers..changed firmware..Still no luck 
 ](*,)

It used to work for few days with 9.10..

I am desperate...
Should I downgrade to 8.10 ?
[http://ubuntuforums.org/archive/index.php/t-968121.html](http://ubuntuforums.org/archive/index.php/t-968121.html)

Is there a way to make a PVR-150 work under 10.4?

Thank you for your help

---

### Post by nerver on 2010-07-19
I had it working under 9.10 perfectly, have not tried it on 10.04 since I got a PVR from by cable provider. 

Is the audio problem occurring all of the time or only on some of the recordings, etc? If it's not all of the time, have you tried adding the line in my post above to your channel change script? That will reset the audio after a few seconds so if its tinny it will fix a couple seconds into the recording.

If it's all the time then you may have another problem altogether. 

Let me know, if need by I can test out my PVR 150 on 10.04 for you.

Cheers,
-Sean

---

### Post by enricor77 on 2010-07-19
Hi Sean,  Thank you for the reply.  The audio problem is occurring all the time, also running  vlc /dev/video0 Webstreaming works fine instead.   I am using a composite input, with the tuner preset on channel 3.  I have also moved the pvr-150 in another machine with a fresh 9.10 installation,still same issue.  Before patching the driver, I have tried your script without luck,  I am going to try it again..  Thanks, E

---

### Post by nerver on 2010-07-21
hey, sorry for the delay writing back..been a hectic few days.

hmmm that is very strange, so it works through VLC but not with MythTV eh? are you able to capture from the card directly using the command line? I don't know the command off hand but you should be able to find it via google. If not let me know.

I haven't had a chance to try the card on my 10.04 setup yet (the in-laws are staying with us and taking down the TV system to tinker won't go over well. I'll try to do that as soon as I can though.

---

### Post by enricor77 on 2010-07-22
No problem I had a long week as well..

I tried your script, change the source from the cable box to the dvd played, played around with the audio settings (volume etc): no luck.

I am able to capture the stream from the card. I used this command:
cat /dev/video0> test123.mpg
Still the static sound in background. 
No weird message in dmesg.

Are you currently using the 9.10 without any issue, correct? I don't mind going back to 9.10..

This is my hardware configuration:

Gigabyte ga-ma785gm-us2h 
 Integrated video: ATI Radeon HD 4200
 Integrated audio:Realtek ALC889A
 the "trouble maker" PVR-150

Did you patch the ivtv drivers or is it the one that comes with the 9.10 installation?

Thanks,
ER

---

### Post by nerver on 2010-07-23
hey,

I had it working with 9.10 previously. I recently did a clean install of 10.04 but have not used the card on it yet..I will still try at some point for you to see if it works (might be about a week until I can do it)

I never patched any drivers or anything on my old setup though, but I'm pretty sure my installation was mythbuntu 9.10 which i then installed the ubuntu desktop on afterwards. I'm not sure if the mythbuntu distro has pre-patched drivers for the card or not. Which distro are you currently using? Ubuntu or Mythbuntu?  If you have the time/inclination, it might be worth trying a clean install the Mythbuntu 10.04 if you're not using it already.

---

### Post by enricor77 on 2010-07-23
I am using Mythbuntu 10.04, which I upgraded from Mythbuntu 9.10 hoping for a resolution. :(

---

