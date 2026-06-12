---
title: "pvr150 records in mono not stereo!"
date: 2009-03-09
forum: Multimedia Software
---

### Post by scooter29 on 2009-03-09
Does anyone know how to change th ivtv driver for the hauppauge pvr150 as it records everything in mono, I know the sound card is working right as I put DVD movie in and playback in stereo.:confused: This is all I have left to a really great PVR! :popcorn: Please help.

---

### Post by scooter29 on 2009-03-12
As popular as this card is someone has to have had this problem before and fixed it. This is the problem with these forums, no one feels like they should help anyone else learn and or fix their programs as they are free and open source!? [-( What is the point, I have googled and really found nothing relavent to the current versions of this software. I feel that if we help each other, ultimately we have a better community all around and the software gets better. So does anyone know how to resolve this issue, so I can record in stereo?:???:

---

### Post by wolfen69 on 2009-03-12
perhaps it's as simple as no one knows the answer. it may not be a common problem. believe me, that if someone knew the answer, they would have helped you by now.

you could also try joining other forums like at [MythTV Forums]("http://www.mythtvtalk.com/forum/") to see if anybody there has an answer.

---

### Post by scooter29 on 2009-03-12
I have seen posts when I google dating back to 2006, apparently when ivtv was incorporated into the kernel. It states building ivtv from source and modifying a line before compiling. I however don't want to render my system useless as, it took me a long, long time to get my irblaster working. I have by the way reponded to a post from someone asking how to do it and shared my knowledge or at least what it took me to get it working, as no post, on any forum gave specific enough directions to get it working. I'm sure someone else has had this same situation as I found threads from google. It's just discouraging to ask a question and days later no response. So I do thank you for at least responding. :)

---

### Post by wizard10000 on 2009-04-24
PVR-150 won't do stereo over the coax input - you have to use the composite input to get stereo.

---

### Post by electrogulp on 2009-05-02
Hi, I read up that you're became to have composite and s-video fully functional...   How have you done?
I'm doing a MythBuntu media center, with inside an Hauppauge Nova-T 500 and an Hauppauge PVR-150. All is working good, but I don't know how to configure the PVR-150 to capture from composite in!!! Could you help me?
I created a new video source called Composite, so I added It to the input channel Composite 1 and Composte2, giving them the same name "Composite".
In this way when I'm plaing TV, switching to the "Composite" input I've got an error that's sound like this:
"An error is occourred while I was searching to show the video"
Where's the problem? Please help me.

Thanks for all your answer

---

### Post by scooter29 on 2009-05-02
I'm not using coax; s-video in rca stereo cables in. s-video out rca stereo out. only one channel working!

---

### Post by scooter29 on 2009-05-02
Selecting inputs on your tv cards is done in mythtv setup. You can get there through mythbuntu control centre. Slow down when you go through the steps and you will see where to change it. I believe it's set to coax by default.

---

### Post by scottac on 2009-05-27
> **wizard10000 said:**
> PVR-150 won't do stereo over the coax input - you have to use the composite input to get stereo.

Really?  could someone please confirm this for me.  I was really about to order this card...

thanks guys...

---

### Post by wizard10000 on 2009-07-15
> **scottac said:**
> Really?  could someone please confirm this for me.  I was really about to order this card...

thanks guys...

Can't confirm my own post, but it won't do stereo over coax in Windows either.  I have one in a Jaunty machine and the spousal unit has one in a Windows XP machine.  Neither will do stereo over coax.

---

### Post by bsntech on 2009-08-05
Just stumbled upon this thread through Google as I also have noticed that the recording through my PVR-150 is in mono on everything.

However, I can CONFIRM that stereo over coax DOES work.  I used to use Windows XP for my system and the drivers I received with the PVR-150 I purchased allowed for stereo recording through WinTV.

I just began pondering the idea of MythTV not recording in stereo using the PVR-150 because my wife and I just watched a really old recording from last year when I was still using Windows XP.  I noticed that the sound was much better and in stereo mode versus all of the recordings I've had in MythTV.

But, as an addendum to the Windows XP stereo mode, I was only able to get stereo mode to work with the drivers I received on the CD with the hardware.  All driver updates since then all seem to only show mono mode.  Kind of fishy why all of these driver updates since then "break" the original driver's stereo mode.

Hauppauge tech support couldn't tell me one way or the other why this happened - they just told me over and over to completely remove all drivers using the hwclear.exe file and re-install the newest drivers.. still didn't work.

---

### Post by bsntech on 2009-08-06
I've been searching for a good portion of the day on this PVR-150 issue and no stereo sound in Ubuntu 9.04 Jaunty.

I came across some information on the [ivtvdriver website]("http://ivtvdriver.org/pipermail/ivtv-devel/2007-January/003961.html") where the developers told a user (back in 2007) to download the ivtv drivers and go into one of the files and turn off a workaround:

> Can you try the following: edit ivtv-driver.c, search for '112' and 
change the line below from:

	itv->pvr150_workaround = 1;

to:

	itv->pvr150_workaround = 0;

Unfortunately, you then have to recompile the ivtv drivers into the kernel to reload it all.  I don't have too much experience doing this myself - and this fix was issued two years ago - so who knows if it will work.  I saw a few posts about this same thing as above - some note that it works and others don't.

Apparently there are several "types" of the PVR-150 out there; you have your standard PVR-150 and you also have the Media Center Edition - plus possibly other one-off type cards.

Too bad that there isn't some sort of quick yes/no or config change in a ivtv config file that would turn on/off the workaround behavior.

In the posts on the page above, it also mentions that you can issue this command at a terminal:

v4l2-ctl --all

It will show you the current recording for the audio (mine was showing lang1).  If you then issue this command:

v4l2-ctl -t stereo

It will then change it to stereo - but it is short-lived.  I made some recordings (of the same show on the same channel that was in stereo) before issuing the command above - and then some recordings after issuing the commands above, and didn't notice any kind of improvement in the sound quality.

---

