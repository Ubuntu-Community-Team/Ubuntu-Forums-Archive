---
title: "SPDIF in Hardy"
date: 2008-05-01
forum: Multimedia Software
---

### Post by devguy on 2008-05-01
I'm a pretty new member to these forums but I've been searching on them for a while now.  I just installed Hardy on my desktop on Sunday and I've had tons of problems (and four reinstalls later, here I am).  One of the big issues I've had is getting SPDIF out of my sound card.  Well, here is what I did:

1) type "aplay -l" in a terminal minus the quotes.
2) if you have a sound card (onboard or otherwise) which can do digital audio output, you should hopefully see it listed.  For example, mine looks as such:
```
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
3) take note of which one is the digital.  In my case, it is card 0, device 1.
4) type "sudo nautilus" into the terminal without the quotes and navigate to "/etc/pulse/" and open "default.pa".
5) add a line at the very bottom like this:
```
 load-module module-alsa-sink device=hw:0,1
```
where the part "hw:0,1" is hardware card 0, device 1 (use the ones you got from step 3).
6) save and exit this file
7) type in these commands to reset PulseAudio:
```
  pulseaudio -k
        pulseaudio -D
```
8) verify using pavucontrol (type "sudo apt-get install pavucontrol" to install it, and once installed, just type "pavucontrol" in the terminal.  You should be able to look in the next tab and see both your standard analog device, as well as the one we added in.  Right click the new one and choose make default (if that is what you desire).

It seems this helps a lot of people, but I needed a few more steps (you may need them as well, so follow these if the above still doesn't work.

9) double click the speaker icon in the notification area (upper right corner near shut down button).
10) make sure that under "file/change device", you see the device that corresponds to the one you found in step two (ex- mine is "SB [HDA ATI SB]").  If it isn't the right one, select the right one.
11) go to "edit/preferences" and with the little menu that pops up, just go ahead and put a check mark next to everything.  Now, close the pop up, as well as the volume control menu.
12) reopen the volume control menu by clicking on the speaker in the upper right again.
13) in the tab labeled "switches", make sure to uncheck the headphone option and to have checked iec958 and iec958 capture (important, although I'm not sure why).
14) in the original tab (playback), make sure that master volume is at a good volume (and not muted).

Hopefully that should do it for you.  I have no idea why one has to go through all this nonsense (especially notifying PulseAudio of the digital device in default.pa).  What is even worse is that on both my desktop and my laptop, I can't even play an mp3 using VLC with PulseAudio without getting serious sound artifacts every few seconds in VLC, so I have to change the output module to ALSA (perhaps just a VLC issue as Totem seems to not have the same problem).

Anyways, I'm using a Gigabyte 790FX motherboard with an ALC889A sound card.  For whatever reason, it is recognized as an ALC882 (as you can see above).  Is there anyway to get DTS:Connect to work in Linux?  I've tried using the Realtek drivers twice, and on both occasions, they completely hosed my install, forcing me to reinstall.

Thanks to [**this**]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/205717/+viewstatus") person for helping me out.

---

### Post by volkswagner on 2008-05-01
I have the same onboard sound as you.  Mine is on Gigabyte.  I have had spdif working under gutsy.  Something broke it though.  I believe it broke during updates.

Anyway not sure if this helps since I am not running Hardy. All I had to do to get it working was use alsa.  First open alsamixer and make sure iec958 is not muted.  Then create and .asoundrc text file in my home directory containing the following.

```
pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```

I was only concerned using inside mythtv which has settings to call alsa.  You may need a config file to include all apps using sound.

I will be checking this thread.  It may help me decide if I want to upgrade to hardy.

---

### Post by devguy on 2008-05-01
Cool, but unfortunately (yes, at this point I believe it to be unfortunate) PulseAudio is the default sound module in Hardy and I'm not sure how to revert it back to ALSA throughout.  It is apparently not as simple as going to "system/prefs/sounds" and just changing everything to the ALSA digital output.

Basically, I just tried to get PulseAudio to do anything through the digital out and apps that have problems with it but can be configured themselves to use ALSA (as apparently VLC does), just do that.

---

### Post by ubusarah on 2008-05-01
I just installed Hardy on a new machine and the HDMI sound doesn't work. I tried "aplay -l" and got this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Nothing says "HDMI"...:confused:

My motherboard is an MSI G33, and the SPDIF cable is connected to an NVidia 8500 card which has an HDMI output connected to my TV. The sound works in Vista.

I have the restricted NVidia drivers installed.

I'll check back; I don't have time to fix this right now... but sooner or later I'll need to fix this. I want to be able to run mythtv too.

---

### Post by ansicplusplus on 2008-05-02
Hy, I just got spdif in hardy working. I post my way here in case it helps someone else.
Step 1: Replace onboard sound with a plain and simple Terratec Aureon 5.1
Step 2: Deinstall pulseaudio and use alsa instead.

I am pretty sure my onboard spdif (asus p4g8x deluxe) isn't broken although I never used it before when my pc had other tasks. However my av-receiver didn't get any sound but the activation/deaktivation of the digital connection. Today I was fed up and replaced it with a Terratec Aureon 5.1 (for about 25 EUR) with optical spdif. 
The card works perfectly and I disabled onboard sound since some apps got confused by 2 spdif ports.

As I learned in the forums, pulseaudio is uncapable of ac3-passthrough at the moment. As I couldn't figure out how to configure the rest of it, I decided to deinstall it. I switched mplayer, vlc and the system-audio explicitly to alsa. For mplayer and vlc I activated the hwac3-codec resp. spdif-passthrough and the use of the device iec958 as sound device.
In case you get error messages regarding an unknown parameter 'AES' try using the device name iec958 instead of something like hw:0,2.

Yours, ansicplusplus

---

### Post by ubusarah on 2008-05-02
Hmm, a solution that requires installing a sound card will be a problem for me, as my new machine doesn't have any slots free...

Actually, that's not entirely true... I do have one of those tiny little PCI Express x1 slot free, but it's blocked by the heatsink on the video card.

For me, the easiest solution will probably turn out to be using DVI and separate audio cables rather than HDMI. I think my TV can only do this on one of its inputs, which is fine provided that I can disconnect the *other* computer currently connected to the TV, which doesn't have an HDMI port.

Getting the onboard SPDIF sound to go through the HDMI connection would definitely be more convenient.

I won't have time to try to get it working until next week at the earlist. :(

---

### Post by zsolt320i on 2008-05-07
Hi,

i have a motherboard Abit KN8 SLI, ant this motherboard has optical output.
Under Win Xp it works well, but under Hardy Heron i can not make to work the passtrough.The pc is connected to the amplifier with optical cable.
What ubuntu recognize is:
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Would it be possible to solve the SPDIF passtrough working?
Heeelp me!
Thanks!

---

### Post by zsolt320i on 2008-05-07
The comment above was sent 2 times, by accident ...

---

### Post by Trollslayer on 2008-06-08
> **ubusarah said:**
> I just installed Hardy on a new machine and the HDMI sound doesn't work. I tried "aplay -l" and got this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Nothing says "HDMI"...:confused:

My motherboard is an MSI G33, and the SPDIF cable is connected to an NVidia 8500 card which has an HDMI output connected to my TV. The sound works in Vista.

I have the restricted NVidia drivers installed.

I'll check back; I don't have time to fix this right now... but sooner or later I'll need to fix this. I want to be able to run mythtv too.

The HDMI part is handled by the graphics system and it seems the nVida card has to enable the routing of the SPDIF audio .
I have an Abit motherboard with built in ATI HDMI video and the HDMI audio shows up on the graaphics chip rather than the audio chip.

---

### Post by Clappy on 2008-08-26
I just did an upgrade that killed my sound (after restart) and I had just gone through 3 days of troubleshooting it. I just killed pulseaudio 

```
pulseaudio -kk
```

and immediately my sound was working again. I'm not comfortable uninstalling pulseaudio because I'm not sure of the dependencies, but I have no problem turning it off. Sound works great and works on multiple programs at once :D

---

### Post by bmwman on 2008-08-30
I have a mobo with onboard Nvidia 7100 and ALC889a sound. Everything works fine but I can't get any sound out of the HDMI. I have the latest Nvidia driver and the latest Alsa-driver-1.0.18rc1. I've tried anything that I can think of and still nothing. When I type "aplay -l" i just get NvidiaHDA 882 Analog and Digital - no HDMI. Also after I installed the latest Alsa in the alsamixergui i see the sound card as ALC885 but in aplay -l its 882. The chip it's actually ALC889a.

Can I edit some file or something to enable the HDMI sound? Video part in the HDMI works fine.

Please give me some ideas.

---

### Post by RawMustard on 2008-09-07
Nvidia doesn't support sound via HDMI on linux yet, probably never will :(

---

### Post by Maheriano on 2008-09-10
I'm also having problems and not sure where to start. I've got SPDIF on my motherboard and also on a Chaintech PCI sound card.

> deemar@chugger:/usr/bin$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by Maheriano on 2008-09-11
Should I make a new thread for more exposure?

---

### Post by carlosbertholdi on 2008-09-30
My problem is that my HDMI device is not even recognize by the aplay -l. Here my reply to this thread at [http://www.nvnews.net/vbulletin/showthread.php?t=97993 ]("http://www.nvnews.net/vbulletin/showthread.php?t=97993")

I install the 173.14.12  driver on my ASUS G1S(with ubuntu gutsy) that has a 8600m GT and one of the "Realtek High Definition Audio" kind of sound card, that is detected as a HDA-intel by the ALSA drivers. So, after I got the 173... driver working I went to the Volume control as "dementor" said, looking for an added device like the one he said, but I found jack ****.

Looking at Preferences I found a Digital thing to select, but it was added to a Recording tab, it didn't do any good. 

But now, my TV is blocking the analog sound so, probably the HDMI output is sending some sort of audio signal to my TV.

My aplay -l output doesn't show any sign of digital device or HDMI or S/PDIF:

[I]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]

I build the ALSA packages I tried every possibility that I could think of. It seems like I have no digital audio on my computer at all (HDMI sound works flawlessly on windows). The only thing that mentions digital audio was the "aplay -L" command:
[I]
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output[/I]

So, I google about this iec958 and the only thing that I find is that you have to unmute it and set volume to zero to make S/PDIF work, but I don't even have this "iec958" showing in alsamixer or "Volume Control". 

If somebody have a ASUS G1S and made HDMI audio work, please, post here.

---

### Post by markbuntu on 2008-09-30
> **devguy said:**
> 
Anyways, I'm using a Gigabyte 790FX motherboard with an ALC889A sound card.  For whatever reason, it is recognized as an ALC882 (as you can see above).  Is there anyway to get DTS:Connect to work in Linux?  I've tried using the Realtek drivers twice, and on both occasions, they completely hosed my install, forcing me to reinstall.

Thanks to [**this**]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/205717/+viewstatus") person for helping me out.

The new 8.9 driver from ati has HDMI audio output support for some cards:

Release notes for 8.9

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)

Have you noticed any crashes when moving streams from the digital output device?
I am wondering because this was reported in the pulseaudio ticket.

You have written very clear and complete directions for doing this. I have had a link to the pa ticket for a while in my guide here. I will be linking this thread into the digital output section. 

Thank You,
Mark


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by am_pcguy on 2008-10-01
I know this may not help but after fighting SPDIF issues with Hardy for about 2 weeks I gave up.  Last weekend I installed Gutsy and sound was working via SPDIF instantly.  

I have an Asus Motherboard with the "Realtek High Definition Audio" onboard sound.  Actually I did get the SPDIF working for multichannel audio by adding the following to /etc/modprobe.d/alsa-base.
```
"option snd-hda-intel model="3jack-dig"
```

I also had to add to ~/.asoundrc :
```
pcm.!spdif {
     type hw
     card 0
     device 1
}
```

With that I could get multi-channel audio via spdif in mplayer.  Stereo sound however would not work.  Also I would have to manually unmute the primary and ICH985 channels in the mixer afte r every boot.  Alsamixer would throw and error so I had to use the mixer in Gnome, alsactl store woudld also throw an error preventing me from storing the alsa settings.

I believe that the problem is with pulse audio, unfortunately uninstalling Pulse Audio proved even more troublesome.  

I had Gutsy up and running in 30 minutes or so with audio working as it should, I'm sticking with that for now.

---

### Post by carlosbertholdi on 2008-10-02
> **RawMustard said:**
> Nvidia doesn't support sound via HDMI on linux yet, probably never will :(

It does work, at least for some systems.

[Here]("http://www.nvnews.net/vbulletin/showthread.php?p=1795369#post1795369"), some people confirm that hdmi sound worked. After the update to 173.14.12 and then 177.78 that i did to my system, the TV start blocking the analog sound that come from the headphone jack, but I still got no hdmi sound, it seems for me that this is an issue with my Asus G1S notebook with linux+nvidia, the people who report that hdmi sound work are desktop users.

---

### Post by carlosbertholdi on 2008-10-07
Finally, I did, I made hdmi sound work on my asus g1s.

Now my aplay -l shows a digital device:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660-VD Digital [ALC660-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I made it work by going to this file "/etc/modprobe.d/alsa-base":
> sudo gedit /etc/modprobe.d/alsa-base

then I delete all the contents of that file and put this:
> options snd-hda-intel index=0 model=3stack-660-digout

at "model" you have to put one that is made for your hardware, look [here]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2") for a complete list of models available.

Then I use alsamixer to unmuted the IEC958.

Now, I have crisp sound on Linux.

---

### Post by dryphi on 2009-01-16
Has anyone tried the above posted solution with Intrepid?

I have been trying to get digital sound to work for some time now. I can get it to work for music by selecting iec958 for everything under Preferences -> Sound; but even after that I get no sound through Firefox or Flash apps. Furthermore I have actually never heard the startup sound!


Edit: I am referring to the first mentioned solution, although I am curious if any other solution would work as well. Please just be specific in a response so I know which of the above solutions work, if any.

---

### Post by Maheriano on 2009-01-16
> **dryphi said:**
> Has anyone tried the above posted solution with Intrepid?

I have been trying to get digital sound to work for some time now. I can get it to work for music by selecting iec958 for everything under Preferences -> Sound; but even after that I get no sound through Firefox or Flash apps. Furthermore I have actually never heard the startup sound!


Edit: I am referring to the first mentioned solution, although I am curious if any other solution would work as well. Please just be specific in a response so I know which of the above solutions work, if any.

I just set up SPDIF in 8.1 yesterday.
1. install 8.1
2. install Pulse Audio
3. double click volume icon (speaker) in panel
4. change drop down menu to your SPDIF device (mine is "ALSA PCM on front:0 (NVIDIA CK804) via DMA (PulseAudio)" when I use SPDIF out on my NVidia motherboard)
5. set volume slider to 0
6. open Pulse Audio Volume Control
7. make sure the only item listed under the Playback tab is the program you're trying to play music from. If some other program is using Pulse Audio, it's not going to be able to send sound to anything else. If you see some other application there, right click and terminate the stream, then restart the application which you want to use sound with.
8. If you do see your application listed under this tab, right click it and make sure the stream is on the right channel. If not, choose to move it to the right channel (front:0 NVIDIA CK804 for me)
9. under Output Devices, right click your device (front:0 NVIDIA CK804 for me) and make sure it's set as default.
10. System - Preferences - Sound - set 4 playback to Pulse Audio. Then set 5th drop down to your device (front:0 NVIDIA CK804 for me)

You're done. If you're using Audacious, go into the options and make sure it's using the Pulse Audio output, then close it and open it again. It should play sound, I'm listening to it right now....

---

### Post by dryphi on 2009-01-17
Okay, this was somewhat helpful. 

I am able to "see" the IEC958 device in PulseAudio Volume Control only after I add the line "load-module module-alsa-sink device=hw:0,2" into default.pa
Also I can get music to play if I set the default device and/or move the stream to this device.

However, the next time I boot-up, it is no longer set as default, and I have to set the IEC958 as default all over again to hear sound.

Can I just set this device as default, and have it STAY as default?  I would like all sound, henceforth, to play via the IEC958 device.

Thank you!

---

### Post by dryphi on 2009-01-17
I got it working!  For the most part...

> **devguy said:**
> 
5) add a line at the very bottom like this:
```
 load-module module-alsa-sink device=hw:0,1
```
where the part "hw:0,1" is hardware card 0, device 1 (use the ones you got from step 3).
6) save and exit this file


I wanted to point out that the "load-module module-alsa-sink device..." code should NOT be placed at the very bottom of default.pa.  It should be placed under the "### Load audio drivers statically..." subheader, towards the top of default.pa.

When I did this my IEC958 device was properly recognized and set as the default device for playback. I could hear music and even flash videos.


I say "for the most part" above because I'm still not hearing any sounds at startup. I can live with that I just wanted music and movies to playback correctly.

To get proper surround-sound, I also changed the default channels from 2 to 6 per this post:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by Nuuk on 2009-03-17
I am having trouble with a USB DAC (recognised but plays no sound through DAC - only through PC speakers). 

When I click on the speaker icon to get the Panel Volume control, I cannot see PCM listed in the Preferences (only Master).

I also get an error message:

An error occurred while loading or saving configuration information GNOME ALSA Mixer. Some of the config settings may not work properly.

Bad key in directory name 11/apps/gnome/alsamixer/slider_display_names/Sigmatel_STAG 9721,23-Master",; is an Invalid character in key..........

Can anybody tell me what to do now please?

---

### Post by Snyper64 on 2009-04-27
> **dryphi said:**
> I got it working!  For the most part...



I wanted to point out that the "load-module module-alsa-sink device..." code should NOT be placed at the very bottom of default.pa.  It should be placed under the "### Load audio drivers statically..." subheader, towards the top of default.pa.

When I did this my IEC958 device was properly recognized and set as the default device for playback. I could hear music and even flash videos.


I say "for the most part" above because I'm still not hearing any sounds at startup. I can live with that I just wanted music and movies to playback correctly.

To get proper surround-sound, I also changed the default channels from 2 to 6 per this post:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

Thanks dryphi, I finally got my Turtle Beach Audio Advantage USB card working thanks to this. Now my Logitech Z-5500 are putting out beautiful DD and DTS sound again. Now I can finally crack open and watch The Ultimate Matrix Collection I bought a few months ago now that I finally got an apartment big enough(and without paper thin walls) that I can set up my Z-5500s :lolflag: . Audio bliss has finally come back now that I can put my old tinny stereo speakers into storage.

---

### Post by hotani on 2009-05-01
I just lost everything after it was all working fine. Now all I have is digital output via spdif. Sound from any source other than digital is completely silent. My Z5500s display "No Digital Data" where they used to display "Movie" or "Music"

I am running 9.04. Not sure what I did to cause everything to fail so completely.

---

### Post by Snyper64 on 2009-05-01
Look [HERE]("http://ubuntuforums.org/showthread.php?t=1140899") I had more or less the same problem so I ended up just modifying each media player by hand and now everything but M-Player uses AC3.

---

### Post by naszi on 2009-05-18
Hi!

I have an msi ex600 notebook, specs say with spdif jack output.

I followed the instructions for setting spdif up, only result i got out of it was that i see sound-meter in pulse volume control going nicely up und down for the dig out, when playing something in mplayer - but i dont hear anything.

(I dont know whats with amarok, it still plays normally analog.)

Could my dig. cable be wrong? I made one myself, but i heard something about higher impedance for dig. cables, so maybe thats my problem?

---

### Post by Snyper64 on 2009-05-18
Are you getting any sound through your digital out such as stereo? If not than it might be your cable. Use a tester and make sure that you didn't shatter your cable when you were polishing it(Fiber cables are very easy to shatter and i know this from first hand as i have made several of them) or make sure that you polish it enough. It could be as you said and your impedance is too low. You would probably be better off just buying one(I recommend [MonoPrice]("www.monoprice.com") as they offer great cables at an exceptional price and their shipping is cheap) as a machine can polish a cable to perfect impedance and can polish a cable better than a human can do it.

---

### Post by naszi on 2009-05-19
With fiber You mean optical cable, right?
I have coaxial input on my DAC and a normal headphone jack on the laptop..as far as i know i have to use a mono-jack to rca cable, so thats what i made.
I get nothing out of windows either, by the way.

---

### Post by Snyper64 on 2009-05-19
Maybe your soundcard is bad? If you check out the ALSA website they have a list of commands to test out your soundcard.

---

### Post by naszi on 2009-05-19
ok, so today i heard that the normal headphone jack can also be an optical spdif output-i thought it could only be coaxial, so maybe i have to find a 3,5mm optical jack to rca?

Anyway there is no light in the jack while something is playing.

As for my soundcard, with pulseaudio i can easily switch during playback from dig.out to analog, and analog plays without problems-i guess soundcard is fine, also no "analog" problems under windows with it.

i will check alsa utils.

BTW do You have some suggestions what to do under windows? If i could solve it there maybe that gives a clue to what to look for in linux?

---

### Post by Snyper64 on 2009-05-19
Try shining a light into the headphone jack and see if you can see an LED, if not than I doubt your soundcard has this ability.

---

### Post by naszi on 2009-05-21
Sophisticated method to check for optical output:
plug jack in - get it out fast! and voilla, i see the red light for a short time.
So after all, i have optical output, so no wonder it didnt work with electric cables...
Now i have to find a solution to convert optical to coax, a cheap one also.

---

### Post by Snyper64 on 2009-05-21
Your soundcard should have came with a plastic connector that you stick into the headphone jack and has an end that you attach the optical cable to. As for a method to convert optical to coaxial try checking MonoPrice, if they don't have it than it doesn't exist.

---

### Post by naszi on 2010-01-10
I was trying to get my digital output working under linux for a long time now, no success yet.

It is working flawless in windows on the same machine, in windows when i plug in something the driver for the card asks me what i plugged in. i check digital, then it apparently switches the jack-plug to digital, so i get the led shining and sound also.

Under linux however i just cant get it working.

Shouldnt it wor somehow similar to windows, i mean the either the driver is checking constantly the plugs, or i am telling it to switch somehow to digital?

I tried pulseaudio before, there i could switch to digital, but still no sound and/or light in the plug...

---

### Post by perez08319 on 2010-04-10
Read post[ http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9103325#post9103325]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9103325#post9103325") for my simple  solution for 9.10 karmic

---

