---
title: "No sound after NVIDIA Driver install"
date: 2009-01-22
forum: Multimedia Software
---

### Post by Bleumunkie on 2009-01-22
So, I've already tried working my way through this, so this is likely to be a longer post... prepare yourself.


ok, now - 

I install from liveCD, and do a complete update.  Base system.  I have sound.  If I install the restricted driver for my video card - NO MATTER WHICH ONE, I lose all sound, except for a static "chirp" every now and then.

I have tried BOTH restricted drivers using the Restricted drivers thingymajig 

- NVIDIA accelerated graphics driver (version 173)
- NVIDIA accelerated graphics driver (version 177) [Recommended]

as well as the latest release from the NVIDIA website (Version 180.22)

every single one kills my sound until I un-install the driver, or re-install ubuntu.

I have tried installing the driver, and then using apt to purge all my sound utilities and then re-install them - no dice

I'm at a dead end with my own knowledge.  I tried searching here, but cant find much relating to the video card driver killing sound.

here are the relevant details.

- desktop system hooked to a 42" LCD tv via a DVI to HDMI cable, - sound still goes analog through a 3.5mm jack to a 3.5mm jack on the back of the TV.

lspci returns this for the sound / video hardware (****PRE- VIDEO DRIVER INSTALL****)

```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600GT (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2286
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb


00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a27
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

```


please help!!!  

I want flashy wobbly windows and OpenGL capability!!!!!!

WITHOUT SACRIFICING SOUND!!!!

I even tried to help myself!!!!  Take pity and help me O' wise users!!!


(as a side note, this all worked fine in 8.04 - had compiz-fusion all installed and flashy, binary blob video driver, sound still worked.  Packed compter up, moved, recently got it out of the box - did fresh install of 8.10 - see above for problem!)

---

### Post by Bleumunkie on 2009-01-22
Nothing, or did it get buried to the third page too fast?

---

### Post by markbuntu on 2009-01-22
What does aplay -l tell you?

---

### Post by Bleumunkie on 2009-01-22
> **markbuntu said:**
> What does aplay -l tell you?

aplay -l PRE BINARY DRIVER

```
bleumunkie@bleumunkie-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


aplay -l POST BINARY DRIVER V. 173 from restricted drivers doohicky

```
bleumunkie@bleumunkie-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm assuming since nothing changed after that binary driver, the others will be the same, so I didnt do the 177 Version listed in the Restricted Drivers doohicky, or the version from the NVIDIA website.

---

### Post by zim2dive on 2009-01-22
Did you try amixer (sound muted) or speakertest ?

---

### Post by Bleumunkie on 2009-01-22
I have made sure that sound isn't muted, and sound occasionally does come out - in a very sharp static chirp.

also, IMMEDIATELY after un-installing the driver, sound returns to normal.

---

### Post by zim2dive on 2009-01-22
have you run alsaconf?

have you re-installed alsa after the nvidia driver install?

so you are saying you have sound if you NEVER install any graphics driver (so you are using the default VESA driver) and lose sound once you do install nvidia driver?

Its probably a good idea to use the newest alsa driver with any nvidia install.

see [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by markbuntu on 2009-01-22
This may be a bug in the 173 driver since it does not support hdmi. You might have better luck with a driver newer than 1.77.78 since it is the first nvidia driver that supports hdmi.

---

### Post by Bleumunkie on 2009-01-22
> **zim2dive said:**
> have you run alsaconf?

No, i'll try that.

> **zim2dive said:**
> have you re-installed alsa after the nvidia driver install?

Yes, I have used apt-get --purge remove to un-install all sound items, and then reinstall them, no effect.


> **zim2dive said:**
> so you are saying you have sound if you NEVER install any graphics driver (so you are using the default VESA driver) and lose sound once you do install nvidia driver?

EXACTLY.  I have sound while using the default driver from a fresh install..  Once I install the NVidia Driver, sound goes away.  Once I uninstall the NVidia driver (only know how using the Restricted driver module, so can't say about Version 180.22 from website) the sound comes back as if nothing had happened.

> **zim2dive said:**
> Its probably a good idea to use the newest alsa driver with any nvidia install.

see [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

I will try that, and also try the alsaconf, will report back with results.

> **markbuntu said:**
> This may be a bug in the 173 driver since it does not support hdmi. You might have better luck with a driver newer than 1.77.78 since it is the first nvidia driver that supports hdmi.

No dice, I download and install the driver Version 180.22, the newest driver from the NVidia site, same result.  The only difference is I dont know how to uninstall the NVidia driver installed from the .bin executable.

as a side note, its a DVI to HDMI cable, the video card does NOT have a HDMI port on it.

going to try the suggestions from zim2dive with Version 177 from the Restricted Drivers Doohickey so that I can easily un-install the NVidia driver.... results post to follow.

---

### Post by Bleumunkie on 2009-01-22
Used the script to install the new ALSA, good to go, sound works fine.

Install 177 NVIDIA Driver, nothing.

I tried re-starting ALSA, using the script to re-install after the driver, still nothing


Remove the driver, have perfect sound.

markbuntu - I'd be more than willing to try the same thing with the new 180.22 NVidia driver from the website if you can point me to instructions on how to remove it after should it not work.  I value sound more than wobbly windows and such.

anything else to try?

---

### Post by markbuntu on 2009-01-22
I seem to remember that some people reported that their nvidia card would disable the on board sound in the bios when they are plugged in and they needed to go into the bios and turn it back on after the card is installed. That may be your problem.

---

### Post by Bleumunkie on 2009-01-22
> **markbuntu said:**
> I seem to remember that some people reported that their nvidia card would disable the on board sound in the bios when they are plugged in and they needed to go into the bios and turn it back on after the card is installed. That may be your problem.

Nope, looked with both driver installed and driver un-installed.  Both times BIOS reports that On-board sound is enabled.

---

### Post by Jim2029 on 2009-01-23
I too have this same problem.

---

### Post by zim2dive on 2009-01-23
> **Jim2029 said:**
> I too have this same problem.

Please give specifics..

you have sound when?  via what output port (HDMI, analog jacks, etc) using which driver?

When you install XYZ, you lose sound where?

---

### Post by mozkill on 2009-01-23
I would re-install the system, then back it up with CloneZilla and then experiment with the driver install repeatedly until you get it right.  Once you have it working, make another CloneZilla backup.

---

### Post by Bleumunkie on 2009-01-23
My video goes OUT DVI, into a DVI to HDMI cable, to my TV HDMI port.

My sound goes OUT normal 3.5mm analog plug, into my TV 3.5mm analog plug

---

### Post by Bleumunkie on 2009-01-23
> **mozkill said:**
> I would re-install the system, then back it up with CloneZilla and then experiment with the driver install repeatedly until you get it right.  Once you have it working, make another CloneZilla backup.

Great suggestion, the only problem is that I have no idea what else to try to get it to work.  I'm not worried about messing up my system - its bare bones right now - and I have a bash script that installs everything I install after first boot.

I need suggestions of what to try with the driver / sound system to get it all working.

---

### Post by zim2dive on 2009-01-23
> **Bleumunkie said:**
> My video goes OUT DVI, into a DVI to HDMI cable, to my TV HDMI port.

My sound goes OUT normal 3.5mm analog plug, into my TV 3.5mm analog plug

What driver are you using when it works?  Which drivers have you tried that fail?

Even tho you are not trying digital audio, have you tried following instructions such as [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) to gather debug info?

More debug here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Bleumunkie on 2009-01-23
> **zim2dive said:**
> What driver are you using when it works?  Which drivers have you tried that fail?

Standard VESA driver on new install works.  _ANY_ NVIDIA binary driver, from any source (Restricted Drivers Module, OR NVIDIA website) works perfectly for VIDEO, but kills the audio.

Drivers tried so far that kill audio:
-NVIDIA Version 173 (Restricted Drivers Module)
-NVIDIA Version 177 (Restricted Drivers Module)
-NVIDIA Version 180.22 (NVIDIA Website)


> Even tho you are not trying digital audio, have you tried following instructions such as [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) to gather debug info?

More debug here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I will as soon as I get a chance, I have some other stuff I have to attend to, but I will do that and post results.

---

### Post by Jim2029 on 2009-01-23
> **Bleumunkie said:**
> Standard VESA driver on new install works.  _ANY_ NVIDIA binary driver, from any source (Restricted Drivers Module, OR NVIDIA website) works perfectly for VIDEO, but kills the audio.

Drivers tried so far that kill audio:
-NVIDIA Version 173 (Restricted Drivers Module)
-NVIDIA Version 177 (Restricted Drivers Module)
-NVIDIA Version 180.22 (NVIDIA Website)


That is the same with me.... But I do have sound from the music player... But when the system boots and plays the login sound or I goto play a video on a website, I just get a crickling noise. Waring... I'm a newbie.

Thanks. I don't mean to hijack this thread, but I though the solution may be the same for both of us here.

---

### Post by zim2dive on 2009-01-24
> **Jim2029 said:**
> That is the same with me.... But I do have sound from the music player... But when the system boots and plays the login sound or I goto play a video on a website, I just get a crickling noise. Waring... I'm a newbie.

Thanks. I don't mean to hijack this thread, but I though the solution may be the same for both of us here.

I'm a newbie too.. just trial by fire getting my audio working with nvidia.. as a hint, I've finally thrown in the towel and ordered el cheapo ATI card instead...I got to a point with nvidia where I could have good video or goo audio, but not both.

Still those links I posted were invaluable to me in learning and debugging.  I highly suggest giving them a try.

---

### Post by Black_Monkey on 2009-01-24
I think I've got the same problem, my sound completely went when changing Nvidia drivers. I can't seem to boot without them, so I'm not sure if I'd get sound back without them.

---

### Post by Bleumunkie on 2009-01-24
OK, I feel I have narrowed down the problem, I feel I know what it is, and I feel the NVIDIA driver is retarded.

OK, so I ran all the ALSA diagnostics and everything I could find and think of.

Ran them before driver, and after driver.  Same result every time, so not really worth posting here, and I didn't save it, so now I can't without going through the trouble again.

When the problem first happened, I did the responsible thing, and checked my cables, made sure they where connected and everything was good.  What I didn't check is different cable methods.

My TV also has a VGA PC Connection on the back, In the manual it says you can hook up a PC to that, or through a DVI > HDMI cable, and it will seek audio from the 3.5mm audio jack.

I decided to try the VGA connection, _SHITTY_ picture, but audio!!!!  So the driver isn't killing my audio card settings, driver, or anything.

I restart with my DVI > HDMI cable, no audio.  I play an MP3, and yank the HDMI cable from the back of the TV.  AUDIO!  I HAVE AUDIO!  The obvious problem with this is the now COMPLETE lack of video!

My conclusion now is this.....with the standard no-frills video driver, the NVIDIA card just throws the picture through the cable, no frills, just picture.  Once I install the NVIDIA driver, the driver is telling the card that if its using the DVI port, to report to the display that "Its all digital", probably to assist displays in better tuning themselves to give the best picture.  

However, on my TV, it tells the TV that the AUDIO SIGNAL IS ALSO DIGITAL, AS IF ITS INCLUDED IN THE HDMI CABLE, WHICH ITS NOT!  This makes my TV look for audio on the HDMI port, which its not finding, if I yank the cord, the TV loses digital connection with the card, no longer being told to look for audio on the HDMI port, looks to the analog 3.5mm jack, and bingo, audio.  

This is just a guess, a very well educated guess IMHO, but still a guess.

I have looked for settings in the NVIDIA control panel to see if this can be adjusted and I didn't find anything. I also looked on my TV to try to force it to look for the 3.5mm analog signal, nothing here as well.  

The TV doesn't surprise me - I highly doubt LG would include a setting like that, its going to hardly EVER be used, and really only stands to confuse the less technical user should it ever be accidentally switched.

The driver does, for if this is actually the case, it is a HUGE mistake on NVIDIA's part.  The video standard is virtually Identical between DVI and HDMI, the only difference is that HDMI can carry audio as well.  Probably not a problem on their cards that have a capability to add audio to a HDMI port, but for a card that only has VGA and DVI - this is a large LARGE **_LARGE_** problem.

If anyone can point out fixes, or potential flaws in my theory, PLEASE DO!!!!  I'd love to be wrong and have a solution, however I feel if i'm right, the only solution lies with NVIDIA fixing their driver.

EDIT:  I just realized - If I use computer speakers to play sound, the problem is avoided, however this really makes things retarded, and doesn't fix the fact that NVIDIA is still retarded, and it also kinda kills any chance of using this as a media center pc.

---

### Post by thefear on 2009-02-09
I've had exactly the same issue with a fresh install of 8.10 and debugged the problem to the same conclusion.

I'd agree in saying it is a problem with the NVIDIA driver.

---

### Post by treydeal on 2009-02-14
I had the same problem, and found a fix here:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

I'll sum it up...when I installed the new Nvidia driver, I had to uninstall pretty much everything installed natively by Ubuntu related to Nvidia b/c of a kernel module conflict.  Apparently when I do this, it removes my user from the "audio" group.  You can check this by typing "groups" into the console.  If you do not see "audio" listed, try this:

sudo usermod -g <username> -a -G audio <username>

Make sure you use the -a switch...if you do not, it will make you a member of ONLY the audio group which I can't imagine would be good.  After the add, you need to log out (if you drop all the way to runlevel 3 make sure you actually do "exit") and log back in.  Run the command "groups" again, confirm "audio" is listed there.

Hopefully though, before you've gotten the chance to open up a console and check, you've heard the Ubuntu login sound!

I hope this helps some people with this issue.

---

### Post by Grand on 2009-02-14
> **treydeal said:**
> 

sudo usermod -g <username> -a -G audio <username>



I think it isn't just a problem of adding the audio group.
I have this problem too. My system is a Sony TV with HDMI/DVI for the video and 3.5mm analog plug for the audio.

Fresh install of Ubuntu 8.1: sound ok and video so so but, works.
Install Nvidia driver: video great and no sound on the TV!
What I tried:
[LIST=1][*]I kept the HDMI video link and I plugged my headphones in PC audio output. Sound works.
[*]I kept the HDMI video link and I plugged the output audio in my micro system (from PC), now I have sound perfectly!
[*]I kept the HDMI video link and I plugged the output of my mp3 player to the audio input of my TV and no sound came!
[/LIST]

> **Bleumunkie said:**
> 

However, on my TV, it tells the TV that the AUDIO SIGNAL IS ALSO DIGITAL, AS IF ITS INCLUDED IN THE HDMI CABLE, WHICH ITS NOT!  This makes my TV look for audio on the HDMI port, which its not finding, if I yank the cord, the TV loses digital connection with the card, no longer being told to look for audio on the HDMI port, looks to the analog 3.5mm jack, and bingo, audio.  



So, I agree completely.

---

### Post by orduek on 2009-02-15
> **treydeal said:**
> I had the same problem, and found a fix here:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

I'll sum it up...when I installed the new Nvidia driver, I had to uninstall pretty much everything installed natively by Ubuntu related to Nvidia b/c of a kernel module conflict.  Apparently when I do this, it removes my user from the "audio" group.  You can check this by typing "groups" into the console.  If you do not see "audio" listed, try this:

sudo usermod -g <username> -a -G audio <username>

Make sure you use the -a switch...if you do not, it will make you a member of ONLY the audio group which I can't imagine would be good.  After the add, you need to log out (if you drop all the way to runlevel 3 make sure you actually do "exit") and log back in.  Run the command "groups" again, confirm "audio" is listed there.

Hopefully though, before you've gotten the chance to open up a console and check, you've heard the Ubuntu login sound!

I hope this helps some people with this issue.

I tried your solution and it didn't work :(
I have 9400GT connected to an LCD TV DVI-->HDMI and the sound is connected through analog to a reciever (not the TV). when loading from the internal graphic card everything works, when loading through the Nvidia got crackling noises on TV and no sound on analog.

---

### Post by Grand on 2009-02-16
I was searching when I saw this topic:

[http://www.hardwaresecrets.com/article/600/1](http://www.hardwaresecrets.com/article/600/1)

The problem is that there isn't connection between my spdif out (motherboard) and my spdif in (video card). So the TV cuts the  analogic signal.

So to solve the problem, it's necessary to do the connection above or somehow do the nvidia's driver doesn't send the audio throw the HDMI cable (I don't know how to do this and who knows, please post here).

---

### Post by orduek on 2009-02-18
can anyone use this card connected to TV?
If i'll install Gnome (ubuntu-desktop) ontop the Mythbuntu will it help?

---

### Post by orduek on 2009-02-19
someone?

---

### Post by orduek on 2009-02-21
I have another information about my problem that might help someone help me.

seems like whenever I load Mythbuntu from the Nvidia card (and not the integrated one) the sound is lost. Even before installing drivers or even when connected to VGA. 
When trying to play something from Mplaye i get the NO AUDIO/DEVICE warnning.

---

### Post by orduek on 2009-02-21
Here is my alsa info script output:
[http://www.alsa-project.org/db/?f=bdc377746841ed0e3201976ec97fb0af988351a1](http://www.alsa-project.org/db/?f=bdc377746841ed0e3201976ec97fb0af988351a1)

If someone would find it helpful.
Thanks

---

### Post by orduek on 2009-02-23
Up

---

### Post by danimaldaisy on 2009-02-24
I have the same identical problems....

using my on board nvidia 7100 or a pci-express 9400gt.

if i use older drivers from ubuntu 8.04 or the older one provided in ubuntu 8.10 i get sound.

i even tried ubuntu 9.04 alpha 3 to try out the newest driver for vdpau and STILL get the same problem!!!!!

here is the WEIRD PART!!!!
if i slap in my 8800gs...it magically works with any and all drivers from ubuntu 8.04 through 9,04 alpha 3

it is a EVGA 8800gs (i heard the 9600gso is the same card, but i doubt it)

so much for SAVING ELECTRICITY AND GOING GREEN!!!!!!:mad:

---

### Post by orduek on 2009-02-27
anyone?

---

### Post by Yodu on 2009-03-03
same issue here ... anyone?

---

### Post by immensewok on 2009-03-04
I had a motherboard die recently. After swapping it out for a new one (with an onboard nVidia card that had VGA, DVI, and HDMI out) I lost sound.
I've got VGA plugged into a normal monitor and DVI plugged into the TV via a DVI to HDMI cable. Sound comes out an onboard headphone jack and splits into stereo for the TV.
After fighting with it for a long time (alsa, pulse, changing the TV inputs, voodoo) the fix was to roll back the nVidia drivers from 177 to 173. nvidia-settings (and therefore X) works a little differently but sound works like it should.
Rolling back the drivers didn't work for the original poster but it worked for me so I thought it was worth a mention.

---

### Post by Yodu on 2009-03-06
up

---

### Post by Yodu on 2009-03-06
Ok, as best as I can figure here is a summary of the problem:


We (posters) have our video card hooked up to an LCD via a DVI/HDMI cable. 

The TV is somehow feeling a digital audio tickle, therefore killing the analog audio input, hence no sound.

If there is a way to kill that digital audio tickle, perhaps being generated by the nVidia card, methinks the problem would be solved.

---

### Post by YOURS3LF on 2009-03-17
I'm assuming that your sound card is an 8 channel. After installing Ubuntu 8.10 on my system i had the same issues with my nvidia GeForce 8200gt. I actually fixed it just by switching through my audio ports until one put out audio. I think the drivers run the audio panel different than the audio panel is normally used.

EDIT: I forgot to mention that I'm using the Nvidia v.177 drivers from the hardware drivers menu.

---

### Post by orduek on 2009-03-25
2 months with 9400GT and no luck yet :(

---

### Post by orduek on 2009-04-04
up

---

### Post by manak on 2009-04-07
Just some more confirmation that it's a problem with the nvidia driver. While I'm using Fedora 8 (actually MythDora) I've had the same issues:
My panansonic 50px75 is[LIST]
[*]connected via a dvi-hdmi cable to my motherboard with a 7050 chipset and dvi out
[*]Previous driver 173.14.12, worked fine
[*]The sound was lost when I upgrade to 180.44
[/LIST] 

And of course everything looks fine (aplay -l same, alsamixer unmuted, dmesg shows init, etc)

My solution was found on the TV. I was able to force the TV to select the analog input associated with the hdmi/dvi  input. As soon as I did that all was fine. So this confirms the audio is going out on the analog cables, but it's the TV the is being told to use the digital audio. 

ak

---

### Post by gibxam on 2009-04-09
Do you think you could expand a bit on your solution. I have the same problem except for me unistalling the nvida drivers doesn't work.

---

### Post by Niggle on 2009-04-18
Just posting to confirm what other people have said. Using the jaunty release candidate here.
After installing the nvidia restricted driver (180) sound seems to vanish. Going into the setup menu on the monitor and manually selecting the line-in audio input rather than the digital (or auto-detect) fixes the problem.

---

### Post by Darkjasper on 2009-05-12
This is because the tv is expecting audio to come from the hdmi and i think that nvidia drivers is trying to send it via dvi-hdmi. There is a fix for this in windows were you edit the edid for the install .inf. I dont know much about linux or if you could do something like that to fix the driver from attempting to send audio over dvi.

---

### Post by yellowman on 2009-05-15
Just bougth a new gfx card since the old one broke. And with the new card I also have this exact problem.

Anyone found a solution?

---

### Post by yellowman on 2009-05-16
To answer myself, I followed this procedure: [http://analogbit.com/node/23](http://analogbit.com/node/23) (Fixing Ugly DVI/HDMI Displays due to EDID bugs on nVidia drivers)

Hope it helps someone else until nvidia fixes this.

---

### Post by mr_fett on 2009-07-11
I just upgraded from 8.04 to 9.04 and now I'm having the same issue.  I'm running a Shuttle SN68PTG5 with the onboard NVIDIA GeForce 7050PV and HDMI.  I had video using hdmi and analog audio using the onboard sound in 8.04 no problems.  As soon as I activate the nvidia drivers the sound goes out.

If anyone has found a fix for this or if you would like more info on my system to help diagnose, let me know.

The next thing I'm going to try is the most recent drivers from nVidia since all the posts here are a little old.  I'll try to remember to post here if that fixes it.

---

### Post by ThomasW on 2009-08-31
Solution (at least partial):

I experienced the same thing and thought it was a major problem when I noticed that it works for me if i connect my plug to the rear jack instead to the front panel!

I conclude that the nvidia driver install somehow leads to my motherboards internal connector for the front panel to be deactivated.

Motherboard: ASUS M3N78-VM with GeForce 8200

---

### Post by clwade on 2009-11-04
My sound stopped working after upgrade from nvidia 7600 to 9400.

Everything in the troubleshooting guides looked like sound should be working.

I did same as #48 earlier, and it fixed for me.

Using analog out, DVI->HDMI cable for connection to TV.

---

### Post by Bunnybugs on 2009-11-04
Well, There is a driver problem... the drivers form the wizard are really filled with bugs...

try [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Maybe this will help your sound work again... it&#347; written for 9.04 Jaunty, but it works on karmic

And try to remove the 'Software Modem' driver... this looks like the origin of the sound problem...

I did both, the forum tread, and removing the driver... so I don't exactly know what it is!

---

