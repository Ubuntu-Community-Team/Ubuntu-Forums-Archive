---
title: "Alesis multimix 8 recording interface in Ubuntu"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by herot on 2006-06-28
Hi, i just bought a Alesis Multimix 8 recording interface and i want to use it in Ubuntu... it plugs into the computer via a USB cable... When i plug it into my Dapper box, it DOES get recognized (it shows up as USB Sound Codec)... but im not sure how to make the recording programs like Audacity receive audio input from the Alesis...

i go to preferences --> sound | then select "USB Sound CODEC" for my default sound card... but when i record in "Sound Recorder" and select "Line-In" it never records anything (or maybe im playing back to the wrong card or something)

another problem is that when i DO switch the default sound card to "USB Sound Codec" and then i decide i want to switch back to the VIA (which normally works fine) it doesn't seem to start working again until after a reboot... there must be some way to restart the sound system without rebooting.

also, assuming i get this thing working... how will i be able to record and then playback what i just recorded WITHOUT restarting the sound system? (alsa?) Can i use two sound devices at the same time? (without having to switch all the time in preferences...)
The mixer was automatically recognized by XP and the mixer comes with special recording software... but i should be able to use any software for mixing right??

Does anyone have any experience with this OR ANY other computer interface mixers like this and using them with Ubuntu?

---

### Post by herot on 2006-06-29
Well, this will be the first time ive never gotten a response in Ubuntu forums!

i must be alone with this thing!  ;)

---

### Post by lunatic77 on 2006-06-29
I don't know the answer to your issue.....but i am jealous of your 512 *GB* of RAM though. :)

Actually I'm having a similar issue with my Firewire interface.  Hope someone has the answer.

---

### Post by herot on 2006-06-29
LOL! i guess id be jealous too
no for real though i got a Bluegene /L out in the shed, i just can't make it record!
j/k ;)

---

### Post by lunatic77 on 2006-06-29
i got some bluejeans in the closet, they don't seem to be able to record either :)

---

### Post by Washington Irving on 2006-07-04
Hmmm, I can't help you either but I am going to buy an Alesis MultiMix 12USB and was hoping to run it (primarily) on ubuntu like you. Maybe it's best to run it on :evil:windows:evil: with the cubase software (which is better than Audacity anyway).

---

### Post by herot on 2006-07-05
yeah thats what ive been having to do... seems like switching main audio devices in ubuntu is really buggy right now (not to mention making the Alesis work with Audacity)... most times when i try switching to a different default audio device (or just switching devices in the volume control interface) i cant go back to my original device anymore... 

and then i can only play music again after a restart of the sound system... but i dont think i should have to restart x or my sound system everytime i switch devices...

if anyone has more information or advice on this subject please let us know !!!

---

### Post by Washington Irving on 2006-07-06
I think the Alesis Multimix USBs are exactly the same as the old multimixes but with added USB functionality so maybe you could use the 2 track out instead of the usb output.

---

### Post by eivind on 2006-09-18
Hm, I remember having read once (on [alsa-project.org]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio")) that standards-compliant USB cards should work automagically - read the paragraph about "All USB devices..." This has to mean that the Alesis card isn't standards compliant, as you guys have trouble getting the Alesis work, and other people have had no success in getting e.g. the [Behringer BCA2000]("http://www.behringer.com/BCA2000/index.cfm?lang=ENG") work.

This is quite sad. These cards/mixers are handy, not too pricey, and I was thinking of buying an Alesis multimix 8usb myself. Crap. Guess I'll go for a separate harddisk recorder instead.

Maybe [submitting a bug report]("https://launchpad.net/distros/ubuntu/+bugs/") about the Alesis would help, as it is recognized in Dapper, but doesn't work properly. Go, herot, go!


Edit:
While snooking around for other Linux-compatible mixer/soundcard thingies, I came over [this page]("http://www.phonic.com/help/index.php?pf=kb&page=category&c=12"), which states that Linux drivers for the Phonic [Helix firewire]("http://210.243.85.5/partner/modules/product_explor/products.php?group_id=3") mixers might be available soon. 

But as we all now, "soon" means "not now" and may even mean "not in a very long time".

Still, I'm not too pessimistic about finding USB soundcards that work in Linux. M-audio devices go recommended, but these aren't exactly the same as the Alesis multimix and similar products. They may also be slightly more expensive, but you probably get what you pay for.

Good luck!

Eivind

---

### Post by eivind on 2006-09-29
OK. I wrote an email to Alesis support and asked them specifically about Linux support for the Multimix series (especially USB). Answer follows:

> 
Hello,

Officially we would just support Windows and Mac for OS 
platforms. This uses
the standard USB Audio codec, so if Linux uses this then it 
should work out.
If you are able to get the MultiMix USB mixers to work on 
Linux, then this
is good news. Please pass on the news if you are able to 
get this to work
out. 


Sincerely,

Justin Baro


Technical Support


This doesn't make me much wiser, but I don't sense a right-on badwill towards Linux. There is also a passage to indicate that the Multimix USB *might* work in our beloved operating system, because of the use of the "standard USB Audio codec". Would anybody with such equipment care to try it out further?

Best regards,

Eivind

---

### Post by pixeldotz on 2007-03-05
very very very old thread i know, but i was wondering if anyone had any success with this?

i have a multimix 8 i bought last year and since my MIC  does not work in Edgy (other audio is spot on) i figured i'd give the usb a try before i resort to a dualboot scenario.

---

### Post by bsalt on 2007-03-21
I have a Tascam US-428 that I had working in Ubuntu. I found a thread in ubuntuforums on how to install it and set it up, but it was only for Tascam mixers...

Did you already try typing your model name and the word linux in a google search? That usually works for me... I'm actually back in XP OEM for my Dell, because I need iTunes and in Ubuntu everytime I unplugged my mixer, I had to type in a long hairy command to get it running again... so it was a pain. But good luck!

---

### Post by bsalt on 2007-03-21
I have a Tascam US-428 that I had working in Ubuntu. I found a thread in ubuntuforums on how to install it and set it up, but it was only for Tascam mixers...

Did you already try typing your model name and the word linux in a google search? That usually works for me... I'm actually back in XP OEM for my Dell, because I need iTunes and in Ubuntu everytime I unplugged my mixer, I had to type in a long hairy command to get it running again... so it was a pain. But good luck!

P.S. - [www.ubuntustudio.com](www.ubuntustudio.com) will be coming out with a version of Ubuntu made for multimedia work - so if you give it time, they'd be able to help ya out with ur mixer problem - but I'm sure many people will be bogging them down with support questions...

---

### Post by tdrusk on 2007-05-04
I have this mixer. With Kubuntu 7.04 it works seamlessly.

Finally :)

---

### Post by lneely on 2007-05-15
Just so you know, I have the Alesis Multimix 8 working with full functionality in Ubuntu 7.04.  I did not have to do anything special, except with software configuration (and each software config is different).  In Audacity, all I had to do was select "USB Audio CODEC" for both input and output under preferences.  Still experiencing a bit of a learning curve with Rosegarden, but I have hope now! :)

If you are having problems getting this to work, then you might need to make sure that your USB audio drivers are installed in the kernel (enabled by default in Ubuntu 7.04) and that ALSA is properly installed.

In conclusion:  Huzzah!

Regards,
Levi Neely

---

### Post by pixeldotz on 2007-05-16
i got it working under ubuntu studio. no issues at all.

for some reason neither fiesty nor edgy detected the mixer; though all my other audio devices worked fine.

---

### Post by themobiletechie on 2007-08-24
Good news, I think I've got it to work, Now as this is my first ever post to a forum i hope this goes OK, You never know it could be a good start. Here's what i did, very easy.

Ok I'm using Ubuntu Studio, not sure it makes a difference, haven't tried other versions as yet but this works in "studio"

1 disable your on-board sound card in the bios, this then should only leave you with your usb-sound device (the mixer)

2 under - system - preferences - sound change all sound capture and playback devices to USB Audio, WARNING check volume levels before running test buttons as it's a high pitch tone likely to do some ear damage...... (yes experience being passed on)

My system hung a little after doing this so i restarted and recorded and played back through Audacity no problem haven't tested any other software yet,

HOPE THIS HELPS

---

