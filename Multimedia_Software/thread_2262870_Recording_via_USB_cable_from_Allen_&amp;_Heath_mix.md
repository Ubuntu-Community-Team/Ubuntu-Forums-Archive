---
title: "Recording via USB cable from Allen &amp; Heath mixer"
date: 2015-01-27
forum: Multimedia Software
---

### Post by Autodave on 2015-01-27
Our church has an Allen & Heath QU32 digital mixer board.  It has a USB output for going into a DAW program.  

Can anyone give a clue where to start to be able to use this feature?  What programs do I need for Linux to make this work?  Is the a "How-To" guide anywhere that I can access?

I am only interested in 2 channel stereo recording: I do not need more than 2 channel capability.

Any help would be greatly appreciated.

---

### Post by Hugh_Barstead on 2015-01-31
Autodave, if you can run that beast of a mixer then I am sure you have figured this out by now, but for better or worse here is my $0.02.

1) The Allen & Heath QU32 has the ability to record straight to a USB hard drive - just plug one in and go.

2) Assuming you want to record directly to the computer and do not want to deal with the complexities of a full digital audio workshop,try the program "Audacity". It installs from the Ubuntu Software Center. Once installed, use the help menu and type in "USB Recording". The half page of instructions are very simple and easy to follow. I use a (much, much less complicated) Yamaha mixer, and Audacity recognized its USB output straight away, no fiddling with PulseAudio or anything else. Plug & Play! You can then manipulate, edit and export your recording in whatever format you like.

3) With a mixer like that, it is worthwhile to take the plunge and learn to use a full DAW. In the meantime, Audacity will give you what you have asked for.

Hugh Barstead

---

### Post by Rob Sayer on 2015-02-01
The first thing I'd do ... though from a quick search I wouldn't anticipate problems ... is to plug it into the 'buntu machine and make sure it's recognized.  Paste into terminal:

sudo aplay -l

and then enter your password.  It should be listed along with your onboard sond card.  It's probably called a usb codec of some sort.

Allen & Heath seem to have good docs and user forum.  I took a quick look and it should just work.  It'd be worth joining their forum too.

Audacity is indeed a good place to start if you're new to this sort of thing.

After that, Ardour is probably the best Linux DAW AFAIK.  But of course it's more complex along with more powerful.

---

### Post by Autodave on 2015-02-01
Thank you: both of you!  I am soooooooooo glad that Audacity will work.

---

### Post by mörgæs on 2015-02-01
If this solves your problem please mark the thread so.

---

### Post by Autodave on 2015-02-08
OK: I can get Audacity to record from USB.  2 problems still exist though: maybe someone can assist with these.

1. I have to record all 18 channels (all that are in use or turned on).  What I wish to do is take the audio from the board in either stereo or mono even.  The recording goes onto our webite for shut-ins or people away from home can listen to the service.  Audacity forces me to record all the channels and *then convert it to stereo.  *I would rather output the signal to Audacity with all channels mixed already.  

2. I cannot get the sound volume loud enough in Audacity. I have it the whole way up. and that is good for the louder sections.  However, when someone is speaking, the volume is quite low.  I have looked in Audacity and also in the pavucontrol.  Pavucontrl gives me no option to raise the incoming signal.

Any ideas on either of these?

And, Hugh Barstead, that is a beast of a board: no doubt about that.  Once you understand it, it is not all that bad.  But, the learning curve is extreme at the outset. :-)

---

### Post by Rob Sayer on 2015-02-09
Those look like Audacity issues more than ubuntu ones.  Have you asked on the audacity forum or even the A&H ones?

Audacity may not be the best choice ultimately.  It's very good but I don't think it was ever intended for complex mixdowns on a board like that.  Try Ardour.

As far as the levels go, pavucontrol isn't intended for mixing.  There's a *lot* more to sound recording than learning the software commands and menus.  If you don't have proper levels you have to get the mics right.  You can't fix bad micing later.

---

### Post by Autodave on 2015-02-15
Got it to work today and with Audacity.  Took a bit of figuring out, but I think my brain was scrambled due to learning (or trying to learm) the mixer board itself

Thanks to those who replied!

---

### Post by mike4ubuntu on 2015-11-02
> **Hugh_Barstead said:**
> Autodave, if you can run that beast of a mixer then I am sure you have figured this out by now, but for better or worse here is my $0.02.

1) The Allen & Heath QU32 has the ability to record straight to a USB hard drive - just plug one in and go.

2) Assuming you want to record directly to the computer and do not want to deal with the complexities of a full digital audio workshop,try the program "Audacity". It installs from the Ubuntu Software Center. Once installed, use the help menu and type in "USB Recording". The half page of instructions are very simple and easy to follow. I use a (much, much less complicated) Yamaha mixer, and Audacity recognized its USB output straight away, no fiddling with PulseAudio or anything else. Plug & Play! You can then manipulate, edit and export your recording in whatever format you like.

3) With a mixer like that, it is worthwhile to take the plunge and learn to use a full DAW. In the meantime, Audacity will give you what you have asked for.

Hugh Barstead

what kind of yamaha mixer do you use?  I'm considering a YAMAHA MG206C-USB and wanted to know if it is supported in Ubuntu.  Do you know the module (driver) name that is used for the mixer usb?  do you see it with "lsusb" and "aplay -l" commands?

[I]**Update**: I talked to a yamaha tech rep, and most mixers like this will only provide a stereo recording interface through the USB.  You're not going to get a recording channel for each of of the channel strips in the mixer.  Also, chances are, since the ALSA drivers (USB and otherwise) are so broken and/or crippled with the more recent v3/v4 Linux Kernels, you probably won't be able to use Linux to record from it with a recent version of Ubuntu.
[/I]

---

