---
title: "Can't use VLC or Totem for playing 5.1 encoded video"
date: 2009-06-20
forum: Multimedia Software
---

### Post by Dissel on 2009-06-20
Hi,

I am using Intel D945GTP Micro ATX main board with Logitech X-540 5.1 surround sound system.

My motherboard have Intel HD 5.1 channel audio support in-built and using WinXP with vlc player I can play any 5.1 encoded video file & DVD flawlessly.

But if I try to do that in Ubuntu it failed...here is the actual msg pop up

> Audio output failed:
The audio device "surround51" is already in use.
Audio output failed:
VLC could not open the ALSA device "surround51" (Device or resource busy).

My query  is where this device is busy ?

And audio produce by the speaker after certain interval (mean some part not audible & some are)  ...if I select Audio>Audio Device>Stereo there is not much help.

There is no problem with normal stereo encoded file as well as any other audio/video file

Can anyone have face the same problem ?

I am using Ubuntu 9.04 with latest vlc player and all updates.Audio driver HDA Intel (Alsa Mixer) with Line in & Mic In as output checked as well as Swap Center LFE.

and also all volume control preference enabled.

---

### Post by starcraft.man on 2009-06-20
Ok, I'm not sure if this will work, I'm not exactly an audio expert but I have had alsa trouble before.

Open a terminal, Applications > Accessories > Terminal. Type in the following code and hit enter, this will install pulseaudio support, not currently installed with the VLC package currently.

```
sudo aptitude install vlc-plugin-pulse
```

After that, it will install and I want you to open up VLC, just the program, not with video. Go to tools > Preferences then under audio change output type from default to pulseaudio. Close vlc and open with any video file and see if that works. I imagine the same is problem with gstreamer, you can fix it in the gstreamer-properties menu (just run that command as is in the same terminal, go to audio section and pipe your output audio through pulse.

I hope that helps, if not, I'm gonna wager it's a problem with the driver in linux.

---

### Post by Dissel on 2009-06-22
@ starcraft.man Thanks for replying so early.....

I can't make online as my ISP (local exchange guys) plays dirty game with my area.So my response is a bit late...anyhow

Following your suggestion my problem got solve in the case of VLC and the 5.1 file played flawlessly though the the Audio Device Selection field got disabled/grayed...though I don't mind as long as it works properly.

But I can't understand the rest of your suggestion...

[QUOTE=starcraft.man]I imagine the same is problem with gstreamer, you can fix it in the gstreamer-properties menu (just run that command as is in the same terminal, go to audio section and pipe your output audio through pulse.
[/QUOTE]

Where can I found gstreamer-properties menu, or you mean the Totem Properties menu ?

Please can u care to elaborate...Thanks for your help about VLC.

Or may I use the 
> sudo aptitude install gstreamer-plugin-pulse

?????

And it returned me :

Couldn't find any package whose name or description matched "gstreamer-plugin-pulse"

Thanks.

---

### Post by WimJager on 2009-06-22
I had the same problem, and solved it.
Because my localisation is Dutch, I'm not sure how the described options are in English. And also my English isn't very well, so I use screenshots to explain..

EDIT: This seems to work buggy sometimes. Try another audiomethod (pulse, OSS etc.)

- Run VLC (if you have a DVD folder and want to play it with VLC, press the right mouse button -> Open with -> and select VLC.
- In vlc, go to Extra -> options(?) 
[IMG]http://files.getdropbox.com/u/1146839/1e.png[/IMG]

- Show all options and click in the left menu on Audio
[IMG]http://files.getdropbox.com/u/1146839/2e.jpg[/IMG]

- go to the output(?) option under "Audio" and select ALSA:
[IMG]http://files.getdropbox.com/u/1146839/3e.jpg[/IMG]

- go to the outputmodules(?) and click on ALSA:
- Select the first device (or try the other ones if it after the next three steps doesn't work)
[IMG]http://files.getdropbox.com/u/1146839/4e.jpg[/IMG]

LAST STEP:
i'm not sure if it's nessesary, but you can uncheck it when the audio works without this option:
- Go to the tab OSS under outputmodules(?)
- check the checkbox.
- Save the changes.
[IMG]http://files.getdropbox.com/u/1146839/5e.jpg[/IMG]

Test if 5.1 works:
- Go to the Audio option, and select 5.1:

[IMG]http://files.getdropbox.com/u/1146839/6e.jpg[/IMG]

It should work now!
Succes!

---

### Post by starcraft.man on 2009-06-22
> **Dissel said:**
> @ starcraft.man Thanks for replying so early.....

I can't make online as my ISP (local exchange guys) plays dirty game with my area.So my response is a bit late...anyhow

Following your suggestion my problem got solve in the case of VLC and the 5.1 file played flawlessly though the the Audio Device Selection field got disabled/grayed...though I don't mind as long as it works properly.

But I can't understand the rest of your suggestion...



Where can I found gstreamer-properties menu, or you mean the Totem Properties menu ?

Please can u care to elaborate...Thanks for your help about VLC.

Or may I use the 


?????

And it returned me :

Couldn't find any package whose name or description matched "gstreamer-plugin-pulse"

Thanks.

Open a terminal and just type in gstreamer-properties and push enter. There you are. Under audio, you can now switch both from default to pulse and test. You don't need to install a pulse package for gstreamer.

---

### Post by Dissel on 2009-06-23
Thanks in a million....=D>=D>=D> for replying 

@ starcraft.man

 Thanks for your further assistance, I'm so dumb can't get it from your previous reply.

Now my gstreamer-properties look like this. Hope it is alright.

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/GSProp.png[/IMG]


@ WimJager

Thanks for posting step-by-step procedure of VLC audio method. 
But I can't find so much option menu like yours.....

I also want to note down your method too, for my future use as well as the other one, but can't find it.

Here is mine look like

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/VLCPref.png[/IMG]

VLC version is 0.9.9 a.

Thanks in advance.

---

### Post by WimJager on 2009-06-23
On the left lower corner you can choose "All" and "Simple"
Choose All, and more options will appear.

---

### Post by The Bright Side on 2009-07-18
Hey guys,

I have the same problem in VLC... I've been toying around with it a bit, but I can't get the 5.1 to run correctly. When I type

speaker-test -Dplug:surround51 -c6 -l1 -twav

in the terminal, the sound is played back correctly from the speakers/subwoofer, but in VLC, when using this test AVI

[http://www.tfm.ro/ac3/](http://www.tfm.ro/ac3/)

I don't get the correct sound. The center is fine, but all variations of left and right come from both front, back and LFE (left and right respectively). This happens in both ALSA and Pulse. 

Any more ideas? I'm so happy about my new 5.1 system, and I would love to get it to work :-(

---

### Post by The Bright Side on 2009-07-20
I got it to work! Whoever runs into the same problem, here's my solution... In fact, it was a matter of endlessly fiddling around with the settings. Here's the setup that now works for me (pretty straightforward, actually):

- First, select "All" in "Show Settings" in the options menu
- Under "Audio", I have "High Quality Audio Resampling" enabled (it is by default, I think)
- "Use S/PDIF when available" is disabled
- "Peak Protection" disabled, too

- The selected Audio output module is "ALSA audio output"
- In the sub-options of "Output modules", I selected "HDA Nvidia: ALC888 Analog (hw:0,0)" as my ALSA Device Name
- Under "OSS", I enabled "Try to work around buggy..."

Now I can select "5.1" from the Audio Device menu when playing back a DVD, and it works.

---

### Post by Maheriano on 2009-08-11
> **The Bright Side said:**
> I got it to work! Whoever runs into the same problem, here's my solution... In fact, it was a matter of endlessly fiddling around with the settings. Here's the setup that now works for me (pretty straightforward, actually):

- First, select "All" in "Show Settings" in the options menu
- Under "Audio", I have "High Quality Audio Resampling" enabled (it is by default, I think)
- "Use S/PDIF when available" is disabled
- "Peak Protection" disabled, too

- The selected Audio output module is "ALSA audio output"
- In the sub-options of "Output modules", I selected "HDA Nvidia: ALC888 Analog (hw:0,0)" as my ALSA Device Name
- Under "OSS", I enabled "Try to work around buggy..."

Now I can select "5.1" from the Audio Device menu when playing back a DVD, and it works.

This doesn't sound like a solution. If you're not using SPDIF in VLC then it's not being output in AC3, it's probably outputting it in Dolby Prologic which is an analogue simulated 5.1. Yes, it works but is not true 5.1. You need to use SPDIF.

---

### Post by The Bright Side on 2009-08-14
How would I do that? When I enable SPDIF in the menu, I get a loud noise out of my speakers (like when you play a data CD on a music CD player), when I set my audio device to "digital" in VLC, everything stays silent.
My sound card has three regular audio outputs for Front speakers, Center/LFE and Surround speakers, and they're connected to my sound system with three 3.5 mm jack cables. Wouldn't SPDIF require another kind of cable? Optical?

---

### Post by Maheriano on 2009-08-15
> **The Bright Side said:**
> How would I do that? When I enable SPDIF in the menu, I get a loud noise out of my speakers (like when you play a data CD on a music CD player), when I set my audio device to "digital" in VLC, everything stays silent.
My sound card has three regular audio outputs for Front speakers, Center/LFE and Surround speakers, and they're connected to my sound system with three 3.5 mm jack cables. Wouldn't SPDIF require another kind of cable? Optical?
Holy smokes, this is way wrong. Those 3.5 millimeter cables can only transmit analogue audio. It is physically impossible to get digital 5.1 audio (true AC3 or DTS) using those cables. What you need is a toslink (fiber optical) or coaxial cable plugged into the SPDIF port on either your sound card or motherboard. Unhook those other cables, you don't need them at all.

I find it funny how people buy a $500 BluRay player, $3000 television, $2000 audio system and hook it all up with those analogue RCA cables thinking they have Dolby 5.1. I see it all the time. I even have my Playstation 2 hooked up with toslink, sounds much better.

---

### Post by The Bright Side on 2009-08-16
I see! Yeah I know about optical cables and that they are truly digital; however, my computer and sound system are rather on the cheap side, they only have 3.5 jacks. I am only living here for another year or so, so no point for me buying high quality stuff. It sounds great for the time being.

Thanks nonetheless, I will keep your advice in mind! Once I settle down, I will buy some kickass equipment for my viewing and listening pleasure ;-)

---

