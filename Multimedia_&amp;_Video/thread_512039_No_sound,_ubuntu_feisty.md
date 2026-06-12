---
title: "No sound, ubuntu feisty"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by saescavipica on 2007-07-28
Hi

i've just installed Ubuntu feisty  and ther's no soud, i'm new at this, so  my knowledge about the command line is basic,  this is what i've got,  so i hope you can help me! thx. 

[IMG]http://img530.imageshack.us/img530/6048/pantallazoua6.png[/IMG]

---

### Post by kyphi on 2007-07-31
Go to System (top panel) then Preferences then Sound and place a tick into the box that says 'Play System Sounds'.

By the way, nice background picture.

---

### Post by saescavipica on 2007-07-31
hi kyphi, thx for replying! 

well i just did it and the option was already marked, so i hope there's something else to do! 

btw, here's the background 
[http://www.deviantart.com/deviation/23126601/?qo=4&q=celestial+light+&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5]("http://www.deviantart.com/deviation/23126601/?qo=4&q=celestial+light+&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5")

---

### Post by timmahhny on 2007-07-31
[http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty]("http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty")

This should do the trick
Good luck
Timmahhny

---

### Post by saescavipica on 2007-07-31
hi timmahhny

from the post you sent me i did this. Terminal:

**asoundconf list**

and got this:
[B]
Names of available sound cards:
VT82xx[/B]

Then I tried checking the ALSA driver but didn't find anything for my card, and it is recognized as Realtek High Definition Audio in Windows 

Hope somebody could help me, thanks again.

---

### Post by kyphi on 2007-07-31
Your sound device is supported in Ubuntu and I am not aware of any conflicts in Feisty.

Have you tried a right click on your speaker icon in the top panel and accessing 'Open Volume Control'.  You could place a music CD into one of your drives and try adjusting some of those controls.

...and, thanks for the link to your wallpaper.

---

### Post by Commodore Guff on 2007-07-31
I have the same onboard audio, and it too doesn't work.
Never really got any help with it, but I have found a few cases of the same problem, as well as [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373").

---

### Post by timmahhny on 2007-07-31
> **saescavipica said:**
> hi timmahhny

from the post you sent me i did this. Terminal:

**asoundconf list**

and got this:
[B]
Names of available sound cards:
VT82xx[/B]

Then I tried checking the ALSA driver but didn't find anything for my card, and it is recognized as Realtek High Definition Audio in Windows 

Hope somebody could help me, thanks again.

I take it the VT82xx is the motherboard sound card, correct?
Try the following:
Click on Systems->Preferences->Sound
Play around with some of those settings. Not sure if that will help.
You can as others has stated, right click on the volume icon, make sure sound is turned up,
then click on preferences, and make sure the settings are correct. 
I am knew to Ubuntu, well not new, new, but troubleshooting is very new to me in Ubuntu.
 I can only pass on what worked for me. 
 good luck, and I will continue to look for some answers for you.
Timmahhny

---

### Post by kyphi on 2007-08-01
Can you find some useful information here?

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by saescavipica on 2007-08-01
hi! i've been doing what you say but doesn't  seem to be workin

**kyphi:**
 
> Your sound device is supported in Ubuntu and I am not aware of any conflicts in Feisty.

Have you tried a right click on your speaker icon in the top panel and accessing 'Open Volume Control'. You could place a music CD into one of your drives and try adjusting some of those controls.

...and, thanks for the link to your wallpaper.


Well, when i tried to listen to a cd it didn't open, says it can't be shown «cdda:///dev/hda» and that there was an error while tryin to execute the application; in the other hand  i right clicked on the speaker icon and i moved volume there,  on file menu theres an option *changing device * and there appear 2 devices: 

[LIST]
HDA VIA VT82xx (alsa mixer)
[/LIST]
[LIST]
Realtek ALC861-VD (oss mixer)
[/LIST]

i'm not sure what does it mean, but earlir while looking for drivers for a VT82xx i din't find anything, there where some for VIA cards, however, so i don't know if it's important or could help

(drivers for via I found [http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-VIA]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-VIA"))

and bout the wallpaper, you're welcome i think it's a good one! thanks a lot!!1

**timmahhny:**

the same, i selected all the options there and tried to test, i checked the volume, nothing happens, but thanks a lot!!

---

### Post by saescavipica on 2007-08-01
thanks kyphi for the link, gonna check it!

p.s. please check my last reply, thx.

---

### Post by timmahhny on 2007-08-01
This is interesting.
I will, as I am sure others will, continue to look for answers. 
I will say this about Ubuntu Forums. The people here are the best. 
I have never had a problem with Ubuntu that this forum could not figure out.
And this will give me motivation to really break down Ubuntu and learn it. 
Don't give up. Ubuntu is worth the little hassles you may encounter. 
 Timmahhny

---

### Post by kyphi on 2007-08-01
>   * HDA VIA VT82xx (alsa mixer)

    * Realtek ALC861-VD (oss mixer)

Have you toggled between the two entries to see if one of them works?

If the cd will not play that is another problem but at the moment we need a sound source.  You could try the 'Experience Ubuntu.ogg' in Examples in your Home folder.

---

### Post by saescavipica on 2007-08-01
hey, Thank you so much for tryin' to help me!

**timmahhny ** 

Yep, i'm new and that's why i'm here, because i know that if there's a place where i can find the help i need, it's gonna be here! even with my inexperience i've learned a couple of good thinks these days, that's cool!

**kyphi ** 

> Have you toggled between the two entries to see if one of them works?

yes, i changed the option and then reboot, but didn't see any changes! 

Anyway, i have the doubt about the drivers, do you know if those ones that i found have something to be with my sound card? maybe not, i mean.. i just don't know nothing about sound cards!!

well, thanks again
have a nice day*

---

### Post by BobLand on 2007-08-01
Since nothing else has worked, take a look at this thread.  This process will work for most users with generic cards.  However, there are cases where it doesn't work using the mo'board's sound chip.

[http://ubuntuforums.org/showthread.php?t=457373](http://ubuntuforums.org/showthread.php?t=457373)

---

### Post by saescavipica on 2007-08-07
Hi everybody!

I have tried all your suggestions, but haven't succeed! i really hope somebody could help me, as i told you i'm new!1 if you need some info, please ask, i will be glad to do whatever to have sound! 

thanks a lot.

---

### Post by timmahhny on 2007-08-07
saescavipica: Is this a laptop or PC?
If a laptop, do you have a physical switch that is in the off position?
There are a few models that have an off switch for their audio.

 Has your sound ever worked running Ubuntu?

Did you upgrade from an earlier release?

 And you are running Fiesty correct? Ubuntu 7.04? (What ever the current version is)

 I too am a newbie, only running Ubuntu for about a year and half. The people here have always solved the few problems I have encountered running Ubuntu.

 And your audio card is a VIA, correct? Any more information on the card would help.

 I will continue to look for your answer.

 Take care
-Timmahhny

---

### Post by saescavipica on 2007-08-08
Hi Timmahhny

It's a PC, I didn't upgrade ubuntu, it's my first time! and i have never had sound!!.. 

About te sound card, as you can see at the image i posted, there's the info related to the sound card, if there's a way to get more specific information through the command line, let me know. Finally, I'm a little confused about the sound card, cause (you can see, i posted it) there appear to be two or something like that, i'm not sure..

> in the other hand i right clicked on the speaker icon and i moved volume there, on file menu there's an option changing device  and there appear 2 devices:

    * HDA VIA VT82xx (alsa mixer)

    * Realtek ALC861-VD (oss mixer)


thanks!

---

### Post by timmahhny on 2007-08-08
>  in the other hand i right clicked on the speaker icon and i moved volume there, on file menu there's an option changing device and there appear 2 devices:

* HDA VIA VT82xx (alsa mixer)

* Realtek ALC861-VD (oss mixer) 
You want to make sure you have the alsa mixer set as default.
I will look up some command line codes for you to run, so we can start to figure out why this is happening. 
 this is the first time, I have attempted to help troubleshoot in Ubuntu, but I will give it my best shot, so bear with me. 
If the volume is set to alsa mixer and below that you have options, like master, surround, etc... try each one. You can tell if you are getting sound by either playing a cd, or open up the sound option, under:
System
Preference
Sound
There should be three tabs: 
Devices, Sound, and system beep.
Under the devices, if Auto detect is selected, try manually selecting your card.
Click on the sound tab to see if it worked, but selecting a sound, then hit the play button.

 One final suggestion for now.
Have you tried to type into the Synaptic Package Manager your audio card? See what it spits out to you. You might also want to extend the repositories to third parties. 
 If you don't know how to do that, let us know.

See how that works for you, then post back here
Good luck!
Timmahhny

PS:
I know this sounds dumb, but you are running off of an installed card correct? Not the motherboard?
One of two things:
You may have your lines hooked up to the wrong ports.If so, try moving the jacks to the motherboard audio, select the realtech audio card and see if you get sound that way.
If so, post back here

---

### Post by timmahhny on 2007-08-08
One more suggestion:

 Right click on the  volume icon, select volume control, and make sure PCM is not muted.
I just "fixed" my mothers laptop, and that was the problem
Keep us posted
Timmahhny

---

### Post by saescavipica on 2007-08-08
HI Timmahhny

> If the volume is set to alsa mixer and below that you have options, like master, surround, etc... try each one.

I checked out alsamixer and everything is pcm is on, didn't see nothing like surrond or master. Btw, when i opened alsamixer there's was this info:
card: hda via vt82xx
chip: realtek alc861

> You can tell if you are getting sound by either playing a cd

I can not play a cd, i tried it before, it just doesn't play, somebody told me it could be another prob.

> open up the sound option, under:
System
Preference
Sound
There should be three tabs:
Devices, Sound, and system beep.
Under the devices, if Auto detect is selected, try manually selecting your card.
Click on the sound tab to see if it worked, but selecting a sound, then hit the play button.

I've already done it..  some of they show a pop up:

*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Recurso ocupado o no disponible*

[IMG]http://img116.imageshack.us/img116/8840/pantallazo1ud7.png[/IMG]

the others show another pop up which says *prove* and a blue bar, but nothing happens, there's no sound..

[IMG]http://img257.imageshack.us/img257/6526/pantallazorx3.png[/IMG]

> Have you tried to type into the Synaptic Package Manager your audio card? See what it spits out to you. You might also want to extend the repositories to third parties.

Yes, i just did it, but didn't find anything for my sound card

> I know this sounds dumb, but you are running off of an installed card correct? Not the motherboard?
One of two things:
You may have your lines hooked up to the wrong ports.If so, try moving the jacks to the motherboard audio, select the realtech audio card and see if you get sound that way.
If so, post back here

Uhm, i'm not sure about it, but i have sound in windows, so i think the card is installed correctly.

> 
Right click on the volume icon, select volume control, and make sure PCM is not muted.

I did it and it's turned on! anyway, there's something about PCM i wanna ask, maybe you know. There's a program installed, called QAmix (configurable mixer for ALSA) and there appear PCM as locked, i've tried unlocking it, but doesn't work, when i reopen QAmix pcm is locked again,  i'm not even sure what's the program for.. but maybe it could help in some way!!

[IMG]http://img402.imageshack.us/img402/6705/pantallazo2xd9.png[/IMG]

well, that's everything i've done, thanks a lot Timmahhny.

wish somebody knows what to do! thank you.

---

### Post by timmahhny on 2007-08-08
> Quote:
I know this sounds dumb, but you are running off of an installed card correct? Not the motherboard?
One of two things:
You may have your lines hooked up to the wrong ports.If so, try moving the jacks to the motherboard audio, select the realtech audio card and see if you get sound that way.
If so, post back here  

Uhm, i'm not sure about it, but i have sound in windows, so i think the card is installed correctly.


 I am asking if you have more than one sound card. Is the sound card from your motherboard, a built in sound card, or do you have a second sound card. For example, my sound card for my motherboard is a realtech, but I installed an Audigy Pro and use that sound card. 
 
 attached is a picture of my setup on the one Ubuntu PC.
the Audio for the motherboard is up near the top, but I use the Audigy sound card, located near the bottom. 
If you are having problems with the sound card that **you installed** try moving the jacks to the motherboard sound jacks and see if that works. This will tell me that during the installation process, your audio files were installed correctly.
 
 As I have said before, I am new to Ubuntu, but I fix, repair, troubleshoot Mickey Mouse (Microsoft) Operating Systems. I have re-read what others have said, and researched to my best ability, your sound card. I am still looking by the way. and it might be a bad install.  
You might want to use Synaptic Package Manager, type in Audio Drivers, and mark them for a reinstall.
 But before you do that, let me know how many audio cards you have. 

Keep the faith, keep trying, and please don't give up on Ubuntu.
Timmahhny

---

### Post by saescavipica on 2007-08-09
Hi Timmahhny.

I haven't installed any other sound card, i checked my pc and there's just the motherboard audio.  I tried typing *audio drivers * at synaptic but there were no results. Thanks a lot!1

---

### Post by Midwest-Linux on 2007-08-10
I just spent several hours trying to resolve this problem on my IBM machine. I cannot, so i am wiping my HD clean of Feisty 7.04 and now installing Dapper Dan in hopes of that making the soundcard recognized. My problem is also that there is slash mark on the speaker volume icon on the desktop. The soundcard worked fine when I had Win 98 on that machine, but not for Feisty. Good luck.

---

### Post by timmahhny on 2007-08-10
saescavipica:
Try going here and follow these instructions to see if Ubuntu sees your [**_ click here to read about your sound card_**.]("http://http://ubuntuforums.org/showthread.php?t=205449&highlight=Sound")

 It might be a bad install or a bug in Feisty Fawn. I would also do what the post said and file a bug report. Maybe they have a fix for it.
 
 I have Feisty on five machines, three PC and two laptops. Only had sound problem after I did an update, but that was readily fixed; by following some directions in ubuntu forums. 

 Check the link out, see if that helps, if not, post back here.
Sorry that you are going through all of this. I can only say that Ubuntu is worth any hassel you will have. Once Ubuntu is tweaked to your liking, you will not want to go back to any other OS. 
Just my opinion. 
Timmahhny

---

### Post by saescavipica on 2007-08-10
hi timmahhny!

well, i had used this guide before, i followed some of these steps and ubuntu failed, when i rebooted the pc it didn't asked me to log in, ubuntu appeared in english (it was in spanish before) and all of my personal data was lost, then i rebooted again and couldn't acces. Now everything's ok.

So far I'd like to know which is my sound card?! hope you can help me timmahhny.

I'll keep trying, thanks a lot!

---

