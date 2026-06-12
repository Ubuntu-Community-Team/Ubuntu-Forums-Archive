---
title: "Jaunty 9.04 Sound Solutions"
date: 2009-04-19
forum: Multimedia Software
---

### Post by markbuntu on 2009-04-19
**Jaunty 9.04 Sound Solutions**

This guide is based on a clean install of Jaunty Jackalope 9.04rc amd64. It is geared towards getting the basic sound scheme properly set up for optimum use.

It is assumed that your sound device is properly recognized and configured and you have at least a login sound. This is not for basic troubleshooting of no sound problems or issues with your laptop speakers, headphones etc. There are links at the bottom of the post for that.

The sound scheme in Jaunty has some important changes that you need to be aware of.  Alsa 1.0.18 and Pulseaudio 0.9.14 are implemented in Jaunty. The new ALSA provides more support and greater functionality for more sound devices than previous versions. Pulseaudio 0.9.14 does some of the same on the sound server side.

The first thing you should check is the volume control on the panel. It has a new Sound Theme tab.  You can set the theme for your system sounds there. If you wish to disable system sounds set Sound Theme:  No Sounds.

Next, check out System/Preferences/Sound.  It has only two tabs, Devices and Sounds. The Devices tab is where you choose the device to play your sounds. We will return to this later.  In the Sounds tab there are numerous sound preferences that can be set for everything from button clicks to email alerts. You can change the default sound or disable it by double clicking on Default.

** Necessary Packages**
As with Hardy and Intrepid, some important packages necessary for optimal sound set up are missing. Open System/Adminstration/Synaptic package manager and search pulse. This is the easiest way to find and install all  the packages we need. Select the following packages 

padevchooser  -this will pull in all the pulseaudio guis and their dependencies

if you plan on using vlc or xmms2 or 32 bit or libao apps etc, you can get those packages now too. If you are not constrained on disk space it is a good idea to get all of the following

vlc-plugin-pulse          -this also pulls in a lot of libs that vlc will need
xmms2-plugin-pulse   -this also pulls in the xmms2 core
pulseaudio-module-lirc - this is to use lirc and your infrared remote with pulse
libsdl1.2debian-all -this wil replace the alsa version with all available drivers
lib32asound2-this is the 32 bit library for 64 bit installs
lib32asound2-plugins -this is the 32 bit plugins for 32 bit apps
libao2 - you need this for apps using the libao cross platform library
asoundconf-gtk -applet for default alsa sound card
audacious-plugins-extra -plugins for audacious for many codecs like MP3, aac, FLAC, WMA, etc

The gnome-volume-control-pulse is somewhat broken so I do not recommend installing or using it yet. If you are using skype or wine then installing the lib32asound2-plugins will remove them and installing wine or skype will remove the lib32asound2-plugins. I don't use either skype or wine so I was unaware of this issue, sorry. You can still install lib32asound2 but not the lib32asound2-plugins. Other applications that depend on the lib32asound2-plugins may not work after you do this so be aware of that. Hopefully this will be fixed soon.

Search alsa and select the following

gnome-alsamixer - this mixer is far easier to use than the alsamixer
alsa-oss - this is the alsa wrapper for oss apps

Click apply and the packages will download and install themselves

Also select the following

ubuntu-restricted-extras

Click apply. This download may take a while, the ubuntu-restricted-extras package is quite large but installs almost all the codecs and java and flash 10.0.22.87 and a bunch of other stuff that you will be needing.  It also updates the gstreamer packages and some other stuff.

A window will pop up during the installation asking you to agree to the sun-java6-jre license terms, click the little box and then Forward.

In System/Adminstration/Users and Groups check that your users and root are members of the following groups. (This is supposed to be taken care of by Policykit and hal but users have reported messages in their logs relating to lack of permission for pulse to gain rt priority so.....)
pulse
pulse-access
pulse-rt

Reboot 

(This may not be totally necessary but I always reboot after installing a bunch of packages just to ensure that everything is cleaned up in the file system.)

**Setup** 

System/Preferences/Sound, change everything to PulseAudio Sound Server except Default Mixer tracks which you should change to you hardware playback device like Playback: HDA ATI SB ALC888 Analog..... or something like that. Default Mixer tracks is where you set what your multimedia keys to control the hardware device. If your keys are controlling PCM volume and you want to control the Master or something like that, you need to change the selection in the panel volume control/preferences.

Click Applications/Sound and Video/PulseAudio Device Chooser.(padevchooser) The icon should appear in the panel. Click on it, choose Preferences/Start Applet on session login so it stays in your panel when you reboot.  Choose it again, click Volume Control.

In Playback you will notice System Sounds. You can set the volume of your system sounds here or mute them with the mute button. In the Output Devices tab you will see your sound device(s). if you right click on the volume bars you can make it the default. If you have already opened an application and it plays on another device this will have no effect and you will need to move the stream manually next time you open it.

Lets' play something. Start Rythmbox and play one of the radio stations. Rythmbox should show up in the Playback tab with the volume bar moving with the sound. Click Output Devices, you should see the same thing in your output device. You can adjust the volume or mute the individual stream in Playback or the entire device in Output Devices

If you have more than one device and rythmbox is playing in the wrong one go back to the playback tab, right click on the volume bars and choose move stream to move it to the correct device. You can also go back to the padevchooser and open Configure Local Sound Server/Simultaneous Output and check the box. That will create a new Simultaneous output.... Virtual Stream in Output Devices. You can move any playing stream to the new device and have sound everywhere all at once.

Lets check if we can record. Leave rythmbox playing.
Open Applications/Sound and Video/Sound Recorder. Click the record button. In the PA volume control recording tab you should now see

gnome-sound-recorder: Record Stream.

right click on the volume bar and choose move stream and move it to the monitor of the output device you are using.  Click stop in sound recorder and then record. Sound recorder should now be recording from rythmbox. Click stop.  Change to the playback tab in the pavolume control. click the speaker on the rythmbox stream to mute it. click play on sound recorder. You should now see stream recorder in playback and hear what you just recorded.

Let's try recording from the microphone. Go back to the recording tab. click record on stream recorder and move the stream to the device instead of the monitor. Click stop. Click record again and make some noise into the microphone. You should see the volume bars move. Congratulations, you are now a recording genius.

You can make a device or monitor the default for new applications by right clicking on it like with playback.

If your microphone does not seem to be working Open the Volume Control from your panel ( the little speaker icon) and check that it is set to the proper device (your hardware). Click Preferences and make sure that the boxes for  Microphone Capture and Mic Boost Capture are checked, close the box. In the Volume Control/ Switches check the Mic Boost Capture box. In /Recording make sure the Microphone is not muted (no red x on the mic icon) and turned up. (Some devices do not have a mic boost option). 

If your microphone volume is very low even turned up all the way, click padevchooser/Manager. In the devices tab find under Sources alsa_input.pci........alsa_capture_0 or alsa_input_usb.... if you are using are usb device, click the Properties button. A new window will pop up. Try adjusting the volume to 150% or so. (This is a common problem with many dell laptops and others.)

Try recording again. If it still does not work check for any other mic switches or controls and play around with them.

Remember, it is the capture/recording settings that are important for recording. Playback settings get your mic to your speakers.

If you are still having problems with your mic it is most likely a problem with the alsa driver. This is a very common issue for laptop users and fixes are very hardware specific. You should try the first link in the troubleshooting section below or a forum or google search for your specific hardware.

Now you know how to use all the basic tools. There will be some updates along shortly so if your sound stops working after an update, check the basics, like the volume controls and switches and stream locations first before taking any more drastic steps.

If flash stops working or you want all the non-free codecs etc  you can follow the Comprehensive Multimedia and Video How To here (I always do this after every new install): 

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)


**Basic Sound Troubleshooting**

If you are having problems getting the sound to work on your laptop go here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If your sound is not working at all or you need some help with your mic or want to enable surround sound or are having other sorts of trouble or have questions about anything else sound wise go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

**KDE/Kubuntu Jaunty**
If you are using KDE4.x or Kubuntu Jaunty with Pulseaudio you should read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)


Well, that is the basics of getting your sound working in Jaunty.  
Feel free to post comments or suggestions.

regards,
mark

---

### Post by iaskedalice09 on 2009-04-19
Also, the following package helped me A LOT.

```

sudo apt-get install libgstreamer-plugins-base0.10-dev

```

That fixed sound in Flash for me.

---

### Post by markbuntu on 2009-04-19
Hmmm....I have no problems with flash from ubuntu-restricted-extras so far, either with alpha, beta, or RC.
Are you using amd64?
Where did you get your flash?

---

### Post by iaskedalice09 on 2009-04-19
I use Gnash.

---

### Post by nwadams on 2009-04-19
some people have problems with the initial mic volume, as it is like 50% or something. the fix I found for people using intel chips involves the gnome-volume-control-pulse because you can change the input volume in a tab there. I've only read your post, i haven't tried it myself so your method may work just as well or even better than mine. I will make sure i try it on my laptop later.

EDIT: however what youve done is great, it summarizes exactly how to get it working for almost every chip. kudos to you.

---

### Post by markbuntu on 2009-04-20
Thanks, 
I had to do a clean install of rc to figure out what people would need since I forgot what i did to get alpha 5 working plus I put ubuntustudio and KDE on top of it so it was sort of a long way from a stock install. I finally got around to it this weekend and wrote that up as I went along.

I tried the gnome-volume-control-pulse and it locked up rythmbox and crashed pulse on me and wrecked my simultaneous output so I removed it. Even after I removed it my simultaneous output is still not working right. I fear a pulseaudio and alsa reinstall may be needed to fix that. I use the simultaneous output a lot with my 2 sound cards and usb devices so not having it is a real pain for me.

I suppose if you have one sound device it would probably work OK but it is basically just a gnomy sort of incomplete pavucontrol right now and will need to be almost entirely rewritten to accomodate the new pulseaudio 0.9.15. It was in the alpha5 desktop seed and then removed in an update soon after so I fear it is not quite ready for prime time.

---

### Post by matthewbpt on 2009-04-20
I find quite often my sound works beautifully until I open the Pulse Audio Volume Control program. After doing that a message pops up saying 'Connection Failed: Connection Terminated' and I have to restart pulseaudio. Note that this isn't everytime, but still quite often, it happens erratically though so I don't know what the cause could be. Have you had this experience?

I use a USB sound card connected to a 5.1 speaker system, its a Creative Sound Blaster Live 24bit.

Any suggestions?

---

### Post by markbuntu on 2009-04-20
That message means that pulseaudio has crashed. If you want to find out what causes that to happen, kill pulseaudio and then run it from a terminal in verbose mode.

killall pulseaudio

pulseaudio -vvv

Then file a bug report at launchpad with hardware info and the messages you get in the terminal. Or at least look in launchpad to see if a similar bug has already been reported. Before you do, make sure the problem is reproducable and does not go away when you are fully updated.

---

### Post by psyke83 on 2009-04-20
markbuntu,

Perhaps it's better to remove the section that advises people to add their user account to the pulse* groups. It should be handled by PolicyKit automatically in Jaunty anyway.

---

### Post by markbuntu on 2009-04-20
> **psyke83 said:**
> markbuntu,

Perhaps it's better to remove the section that advises people to add their user account to the pulse* groups. It should be handled by PolicyKit automatically in Jaunty anyway.

Well, it is not and that is causing problems with user pulse start up. It was the same in Intrepid. Maybe we need a bug report if PolicyKit is supposed to handle this.

---

### Post by psyke83 on 2009-04-20
> **markbuntu said:**
> Well, it is not and that is causing problems with user pulse start up. It was the same in Intrepid. Maybe we need a bug report if PolicyKit is supposed to handle this.

I've done several fresh installs of Jaunty (from alpha 5 or so), and never experienced this problem. Are you sure it's an issue, or is it an issue only when performing a distribution upgrade?

Edit: I just checked - I'm not a member of any of the pulse groups, and experience no issues.

---

### Post by drfox on 2009-04-20
Great thread. I'll let you know if it works for me...I have a Dell E520, and apparently there's a BIOS problem that is interfering with sound.

Sorry, but you have a typo...
lobao2 should be libao2 

Larry

No joy, no sound...BTW, I'm using the latest BIOS from Dell 2.4.0

---

### Post by markbuntu on 2009-04-21
> **psyke83 said:**
> I've done several fresh installs of Jaunty (from alpha 5 or so), and never experienced this problem. Are you sure it's an issue, or is it an issue only when performing a distribution upgrade?

Edit: I just checked - I'm not a member of any of the pulse groups, and experience no issues.

Well, I have been playing with Jaunty also since alpha 5 also and making myself a member of those groups stopped my sound from lagging and dropping out, especially when using combined sinks and when using pulse with jackd on a generic kernel.

Depending on what else you are doing, pulse can fail to reload the alsa buffer in time to prevent dropouts if it is not able to gain high enough nice priority with the kernels Ubuntu is using. 

P.S.I do not do distro upgrades, only clean installs.

---

### Post by markbuntu on 2009-04-23
Since this was just moved here from the closed Jaunty testing forum I figured it could use a bump so more people will see it. Please post if this does not work for you. Basic troubleshooting guide should still work. If you are haivng basic sound problems please go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


Enjoy

mark

---

### Post by jeppo on 2009-04-23
I loaded Jaunty onto a new HP 6730s and was only getting sound from the headphone jack, not the internal speakers.  Very frustrating.

This, however, solved my problem:
Added the line:
```
options snd-hda-intel model=laptop enable=1 index=0
```
to /etc/modprobe.d/alsa-base

Now I have working sound through speakers and headphones.

---

### Post by crjackson on 2009-04-23
> **jeppo said:**
> I loaded Jaunty onto a new HP 6730s and was only getting sound from the headphone jack, not the internal speakers.  Very frustrating.

This, however, solved my problem:
Added the line:
```
options snd-hda-intel model=laptop enable=1 index=0
```
to /etc/modprobe.d/alsa-base

Now I have working sound through speakers and headphones.

Good catch. Thanks jeppo. I have that same laptop but haven't installed jaunty on it just yet. I suspect I'll be trying this over the weekend.

---

### Post by mozychan on 2009-04-23
> **jeppo said:**
> I loaded Jaunty onto a new HP 6730s and was only getting sound from the headphone jack, not the internal speakers.  Very frustrating.

This, however, solved my problem:
Added the line:
```
options snd-hda-intel model=laptop enable=1 index=0
```
to /etc/modprobe.d/alsa-base

Now I have working sound through speakers and headphones.

I was really hoping this would solve my problem, but alas it was a no go.  I'm experiencing the same thing with my HP dv5z laptop and it's really getting on my nerves. 8.10 worked just fine...

Here's my stuff if anyone is willing to lend me a hand:

```
mozychan@mozychan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mozychan@mozychan-laptop:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I upgraded to jaunty and didn't do a fresh install and experienced other conflicts that I've already resolved but this is the only problem that remains.  If I must I will do a fresh install over the weekend when I find the time.

-moose

---

### Post by gransonik on 2009-04-24
My Gateway P-6860FX also lost speaker sound after upgrading from intrepid. However, if I boot into the previous kernel 2.6.27-11, both speakers and headphones work perfectly.  I've tried all kinds of fixes from editing alsa-base.conf to reinstalling alsa drivers without any luck. Maybe the problem lies in the 2.6.28 kernel upgrade from intrepid to jaunty. Any thoughts?

---

### Post by Stalkersway on 2009-04-24
> **matthewbpt said:**
> I find quite often my sound works beautifully until I open the Pulse Audio Volume Control program. After doing that a message pops up saying 'Connection Failed: Connection Terminated' and I have to restart pulseaudio. Note that this isn't everytime, but still quite often, it happens erratically though so I don't know what the cause could be. Have you had this experience?

I use a USB sound card connected to a 5.1 speaker system, its a Creative Sound Blaster Live 24bit.

Any suggestions?

I kill Pulseaudio to get all sounds to work ....No idea why it works though

---

### Post by Carl Hamlin on 2009-04-24
Thank you. My microphone hasn't worked since the first time I put Ubuntu on - 7.04 I believe. Following your instructions, I'm now able to record audio, albeit with an annoying hiss in the background.

---

### Post by adam_kimber on 2009-04-24
> **markbuntu said:**
> 

Click Applications/Sound and Video/PulseAudio Device Chooser.(padevchooser) The icon should appear in the panel. Click on it, choose Preferences/Start Applet on session login so it stays in your panel when you reboot.  Choose it again, click Volume Control.

You are amazing! For some reason my playback was muted even though my volume control said it wasn't! I can now listen to music again. :guitar:

---

### Post by 666porcondissaum on 2009-04-24
For some reason my recording tab sets to mute every time I quit the Volume Control. When starting it and disabling mute seems to be all right. BTW thanks got some nice shots here. Skype is working with no problems(except that mentioned).

---

### Post by linuxrrules on 2009-04-24
I have sound when logging in and I have sound when watching video on sites that do not require Firefox plugins.  Here comes the problem ==> On sites that require firefox plugins to watch movie trailers (such as [http://movies.yahoo.com/):](http://movies.yahoo.com/):)

1) There is no sound
2) After some video plays, Firefox dies (i.e. Force Quit is necessary because Firefox becomes unresponsive and just freezes)

When I type about:plugins in the Firefox address bar, everything is enabled.  Here are the plugins that I have:

Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r124
VLC Multimedia Plug-in
    File name: libvlcplugin.so
    Version 0.9.9a Grishenko, copyright 1996-2007 The VideoLAN Team
DivX® Web Player
    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233
QuickTime Plug-in 7.2.0
    File name: libtotem-narrowspace-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.
VLC Multimedia Plugin (compatible Totem 2.26.1)
    File name: libtotem-cone-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.
Windows Media Player Plug-in 10 (compatible; Totem)
    File name: libtotem-gmp-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

There are lots of suggestions in this thread but I really don't know which ones applies to my situation (if any).  I am not sure if my Firefox crashes and lack of sound (while watching yahoo video trailers) are the result of audio problems or video problems.

Absolutely none of this was a problem in 8.10

I'm up for debugging this, I just don't know where to start.

Suggestions?

Thanks in advance,

---

### Post by linuxrrules on 2009-04-24
There's a colon in between about and plugins, not the smiley face

Lets make it a little easier to read my plugins from the last post

Shockwave Flash
File name: libflashplayer.so
Shockwave Flash 9.0 r124

VLC Multimedia Plug-in
File name: libvlcplugin.so
Version 0.9.9a Grishenko, copyright 1996-2007 The VideoLAN Team

DivX® Web Player
File name: libtotem-mully-plugin.so
DivX Web Player version 1.4.0.233

QuickTime Plug-in 7.2.0
File name: libtotem-narrowspace-plugin.so
The Totem 2.26.1 plugin handles video and audio streams.

VLC Multimedia Plugin (compatible Totem 2.26.1)
File name: libtotem-cone-plugin.so
The Totem 2.26.1 plugin handles video and audio streams.

Windows Media Player Plug-in 10 (compatible; Totem)
File name: libtotem-gmp-plugin.so
The Totem 2.26.1 plugin handles video and audio streams.

---

### Post by linuxrrules on 2009-04-24
Please ignore my last 2 posts.  I didn't read Markbuntu's post and this thread carefully enough before posting probably because it was in the middle of the night.  I am going to try to get it working tonight based on his suggestions.

Thanks.

---

### Post by markbuntu on 2009-04-24
> **mozychan said:**
> I was really hoping this would solve my problem, but alas it was a no go.  I'm experiencing the same thing with my HP dv5z laptop and it's really getting on my nerves. 8.10 worked just fine...

Here's my stuff if anyone is willing to lend me a hand:

```
mozychan@mozychan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mozychan@mozychan-laptop:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I upgraded to jaunty and didn't do a fresh install and experienced other conflicts that I've already resolved but this is the only problem that remains.  If I must I will do a fresh install over the weekend when I find the time.

-moose

Did you try adding

model=dv5

to the end of

/etc/modprobe.d/alsa-base

---

### Post by markbuntu on 2009-04-24
> **666porcondissaum said:**
> For some reason my recording tab sets to mute every time I quit the Volume Control. When starting it and disabling mute seems to be all right. BTW thanks got some nice shots here. Skype is working with no problems(except that mentioned).

I have a similar problem with my usb headset. As long as the pa volume control is open it doesn't crackle. Weird.....

I would suggest filing a bug report at Launchpad. Please include as much specific hardware information as you can if you do.

---

### Post by vanadium101 on 2009-04-25
> **markbuntu said:**
> Did you try adding

model=dv5

to the end of

/etc/modprobe.d/alsa-base

my audio is identical and I've added model=dv5 and no change at all.

one thing i'm wondering is my file is called alsa-base.conf, is this right?

---

### Post by linuxrrules on 2009-04-25
Markbuntu, I followed every singe step in your thread.  Everything works as you outlined it.

_However_, I still have no sound in Youtube, Yahoo movie trailers & MSN trailers.

In this link [https://answers.launchpad.net/ubuntu/+question/68518](https://answers.launchpad.net/ubuntu/+question/68518) it talks about starting the pulse audio sound server.  I googled this and thought that editing /etc/default/pulseaudio and changing PULSEAUDIO_SYSTEM_START=1 (from 0) and then stopping then starting the service via the commands /etc/init.d/pulseaudio stop & /etc/init.d/pulseaudio start would work but it did not.

I have spent many hours on this and it is very frustrating.  I think that I am in the right thread.  If not, can someone please point me to the right one.

Again to reiterate, the sound works great as Markbuntu illustrated it in this thread, except for in YouTube, & movie trailers from Yahoo Movies & MSN

---

### Post by mozychan on 2009-04-25
> **markbuntu said:**
> Did you try adding

model=dv5

to the end of

/etc/modprobe.d/alsa-base

Didn't work.  I've also tried model=mobile and model=any.

I just burned a cd w/ jaunty and ran it live, but it still didn't produce any sound so I figure its pointless to do a fresh install.

-moose

---

### Post by mrbubblesort on 2009-04-25
> **gransonik said:**
> My Gateway P-6860FX also lost speaker sound after upgrading from intrepid. However, if I boot into the previous kernel 2.6.27-11, both speakers and headphones work perfectly.  I've tried all kinds of fixes from editing alsa-base.conf to reinstalling alsa drivers without any luck. Maybe the problem lies in the 2.6.28 kernel upgrade from intrepid to jaunty. Any thoughts?

I have the same model as you, and unfortunately the same problem as well.  Followed everything markbuntu said in this post and his massive posting here:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
but I had no luck. 

This also happened to me when I upgraded from Hardy to Intrepid.  Back then, I fixed it by following the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=380578](http://ubuntuforums.org/showthread.php?t=380578)
but the article it links to is no longer there:cry:  I don't quite remember what it said, but all it did was get my speakers back.  However, I do remember that after about a week or so, they fixed everything in an update.  
 
I'd be willing to just try a fresh install if anyone could confirm that it has worked on a gateway.  If you have any luck though, please let me know;)

---

### Post by amplexus on 2009-04-25
Exceptionally clear guide, Mark. Many thanks. I'm afraid it doesn't work for me, however, having lost sound on upgrading to Jaunty from Intrepid. No sound in headphones or speakers.

Here's my lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Any suggestions welcome. Is it likely, if there's no fix now, that an upgrade will take care of this later?

Cheers, Paul

---

### Post by colo505 on 2009-04-25
Have 2 questions:

1. Which is the preferred interface (OSS/ ALSA) for 5.1 and 6.1 output, including DTS?
2. Which interface supports 96KHz rates with Audigy2?

Thanks

---

### Post by Camilus on 2009-04-25
This helped a lot. Thank you so much.

---

### Post by markitoxs on 2009-04-25
No sound at all for me, however using previous kernel works perfectly.

---

### Post by BrionS on 2009-04-25
Markbuntu, THANK YOU!

I was very happy to see how snappy Jaunty was to start compared to my 8.10 set-up and I heard the initial drums at the log-in screen but then magically my sound disappeared with no apparent reason for it!

Your guide was incredibly helpful and now that I know about the padevchooser tool I think I'll be set for the future too.

I wonder why the Ubuntu team doesn't make that chooser a bit more prominent or create a simplified version of it to choose the default sound card and "move channels" if the wrong sound card is being used.

Apparently Ubuntu is primarily focused on single audio card users, but multiple cards is not uncommon these days (one on-board and one add-in card like SBLive).

Thanks again! Rock on! :guitar:

---

### Post by rabbit251 on 2009-04-26
Most of my sound in this Jaunty upgrade had already been working OK after some dedicated troubleshooting over the last several days. A couple hours ago, I followed the Part A instructions on [psyke83's thread for PulseAudio fixes]("http://ubuntuforums.org/showthread.php?t=789578"), and it fixed a mic issue I was having (the same one nwadams mentioned in post #5, I think). From the psyke83 HOWTO:

> 4. Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

markbuntu, this seems to contradict one of your instructions:

> System/Preferences/Sound, change everything to PulseAudio Sound Server except Default Mixer tracks which you should change to you hardware playback device like Playback: HDA ATI SB ALC888 Analog..... or something like that. Default Mixer tracks is where you set what your multimedia keys control.

Can you reconcile the difference? Do they actually do the same thing maybe? Thanks for all the work you've put into this.

[COLOR="Red"]UPDATE: After I followed this thread's instructions and rebooted, my mic issue came back. I've spent two hours since backtracking and troubleshooting to no avail.[/COLOR]

---

### Post by B Crowther on 2009-04-26
The only solution I have found, nothing above having helped to get my mic working in Skype or Sound Recorder was simple: remove Pulse Audio.
I now have working sound, working mic, working Skype.
A pox on Pulse Audio say I. It was rogue in 8.10, and is worse in 9.04.

---

### Post by rabbit251 on 2009-04-26
B Crowther, can you say what steps you took to remove PulseAudio? I haven't had the guts to try it because I've been made to understand it's even more deeply embedded in Jaunty than Intrepid. But if there were a somewhat safe way of going about it...

---

### Post by The Mad Mule on 2009-04-26
**gransonik** and **mrbubblesort**, I have a similar model, the Gateway P-6831FX, and I too have been struggling with this "sound through headphone jack but not speakers" issue.

There seems to have been a bug report about this filed at the start of this month with no apparent progress: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/358166](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/358166)

So I'm guessing that we either have to wait for a real, official fix, or perhaps removing PulseAudio will do the trick, since it is the root of all the sound problems everybody is experiencing.

---

### Post by mrbubblesort on 2009-04-26
> **The Mad Mule said:**
> **gransonik** and **mrbubblesort**, I have a similar model, the Gateway P-6831FX, and I too have been struggling with this "sound through headphone jack but not speakers" issue.

There seems to have been a bug report about this filed at the start of this month with no apparent progress: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/358166](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/358166)

So I'm guessing that we either have to wait for a real, official fix, or perhaps removing PulseAudio will do the trick, since it is the root of all the sound problems everybody is experiencing.


Yes! Now I remember, the article that I said wasn't there anymore was instructions on how to remove pulseaudio.  I don't have time to try it out now, but I should have time in the next couple of days and then I'll let everyone know if it works.

As B Crowther said, a pox on pulseaudio. :P

---

### Post by anixan on 2009-04-26
Hi i have tried loads of things to get my sound working but nothing works, I have run various testes like the one below and everything looks fine but no audio, can some please help, or suggest more tests for me to run? thanks

```
jackbauer@SGCMAINFRAME:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
jackbauer@SGCMAINFRAME:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0146
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by mrbubblesort on 2009-04-26
Well, just to let everyone know, I removed pulse audio on my gateway as per the instructions found here:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

but it **DID NOT** work. It's looking more and more like this is a kernel issue or whatnot, and everyone who can't get their sound working is just f***ed for awhile.  If you had your sound working in intrepid, **my advice is to not upgrade** until they get it fixed.  As a matter of fact, I think I'll downgrade this weekend if there's no other news by then.

---

### Post by swatsbiz on 2009-04-26
I followed the instructions for enabling all the pulse audio, and immediately flash stopped working in Firefox, I haven't seen anyone with a similar problem here, I'm on 64bit Jaunty.

Any ideas?

---

### Post by dave r on 2009-04-26
:confused: Still have no sound in Amarok, every thing else is working, seems to be a problem with the new Amarok.
Keep trying fixes of here but nothing works. I have evan tried uninstalling and reinstalling Amarok as well, still no sound. Rhythm box works perfectly. In Amarok I have all but sound.

---

### Post by markbuntu on 2009-04-26
> **mrbubblesort said:**
> Well, just to let everyone know, I removed pulse audio on my gateway as per the instructions found here:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

but it **DID NOT** work. It's looking more and more like this is a kernel issue or whatnot, and everyone who can't get their sound working is just f***ed for awhile.  If you had your sound working in intrepid, **my advice is to not upgrade** until they get it fixed.  As a matter of fact, I think I'll downgrade this weekend if there's no other news by then.

There are some problems with the snd-hda-intel driver in the 2.6.28  kernel and updates are coming very soon to fix those issues so please be patient.

---

### Post by markbuntu on 2009-04-26
> **swatsbiz said:**
> I followed the instructions for enabling all the pulse audio, and immediately flash stopped working in Firefox, I haven't seen anyone with a similar problem here, I'm on 64bit Jaunty.

Any ideas?

I wrote those instructions as I was setting up Jaunty 64bit and did not experience that problem but I did see it with pulse 0.9.15. Following the directions for Jaunty here seemed to fix all that.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by markbuntu on 2009-04-26
> **dave r said:**
> :confused: Still have no sound in Amarok, every thing else is working, seems to be a problem with the new Amarok.
Keep trying fixes of here but nothing works. I have evan tried uninstalling and reinstalling Amarok as well, still no sound. Rhythm box works perfectly. In Amarok I have all but sound.

Amarok2 uses Phonon which is the new KDE4 sound manager. If you are using a regular ubuntu gnome install the phonon/KDE4 system settings manager is not installed so it can be difficult to direct amarok to use the correct device. I seem to remember some recent amarok update that claims to allow amarok to call the phonon settings directly but I am not sure about that and have not tried it. ( I am not on Jaunty right now but will try this next time I am).

If you are using KDE4 or Kubuntu Jaunty you should read this.

 
[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by forever_root on 2009-04-26
Hello everyone,
  The following is what worked for me. I hope it works for you. Open a terminal and type

[INDENT]sudo apt-get install phonon-backend-xine

[/INDENT]After that reboot amarok and hopefully everything works.

Cheers,
forever_root

---

### Post by markbuntu on 2009-04-26
Well, I just got around to installing amarok2 on my new jaunty amd64 and it came with the phonon-backend-xine so maybe that is a 32 bit problem. Anyway, amarok would still not play so I installed xine-gui, changed the gui setting to master of the known universe and then changed audio driver to pulseaudio and now amarok shows up in the pulse volume control and plays like it should. 

That was not really something I needed to go through since Amarok is my favorite player.

---

### Post by swatsbiz on 2009-04-27
> **markbuntu said:**
> I wrote those instructions as I was setting up Jaunty 64bit and did not experience that problem but I did see it with pulse 0.9.15. Following the directions for Jaunty here seemed to fix all that.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thanks, that has sorted it!

I'd been through that previously I guess somewhere along the line the pulse audio removed the flashplugin-nonfree, I just hope that the pulse audio still all works!

David

---

### Post by mdurham on 2009-04-28
FWIW. I struggled for hours trying to get the Sound Recorder to work on a fully up-to-date 32bit Jaunty system, all to no avail. I then re-installed Gnome-media which downloaded one small extra file, I don't know what it was because it all happened too fast. Anyway, I can now use my microphone with the Sound Recorder.
Cheers, Mike

---

### Post by dano1 on 2009-04-28
mark, followed your instructions for pulse audio. have sound but there seems to be problems. pulse audio manager will not alow me to connect, please see screenshot. 

Also a copy of userlog. 

Running mythbuntu 9.04 clean install. Any help appreciated.

TIA, danny

fixed. got pulseaudio-module-hal through synaptic. sound is great. gotta thank you mark, been following your posts for a while trying to reslove sound issues, i'm finally catching on ; ).

---

### Post by mavk84 on 2009-04-28
Hi, I have a problem with my laptop (hp dv7 1130el) after upgrading to jaunty. My internal mic is not working anymore and infact the "digital mic1" source in volume preference disappeared. With intrepid it was perfect. Does anybody have a solution for this?
Thanks in advance :)

---

### Post by jasonpeel on 2009-04-28
hi All

basically this worked for me but i have one last issue - 
using an Audigy 2 card with the front panel and rear card and cant get sound out of the card only the front panel via the headphone socket.  any clues on where to go next greatly appreciated.

thanks 

Jason

---

### Post by markbuntu on 2009-04-28
> **dano1 said:**
> mark, followed your instructions for pulse audio. have sound but there seems to be problems. pulse audio manager will not alow me to connect, please see screenshot. 

Also a copy of userlog. 

Running mythbuntu 9.04 clean install. Any help appreciated.

TIA, danny

This was not written with mythbuntu in mind. Mythbuntu has its own peculiarities for configuring sound and I think mythbuntu does not even include pulseaudio but I could be wrong about that. I really do not know anything about mythbuntu.

---

### Post by markbuntu on 2009-04-28
> **mavk84 said:**
> Hi, I have a problem with my laptop (hp dv7 1130el) after upgrading to jaunty. My internal mic is not working anymore and infact the "digital mic1" source in volume preference disappeared. With intrepid it was perfect. Does anybody have a solution for this?
Thanks in advance :)

There is an ongoing thread about people fixing their sound after upgrading/installing Jaunty here.

[http://ubuntuforums.org/showthread.php?t=1136670](http://ubuntuforums.org/showthread.php?t=1136670)

It is always better to join a ongoing thread than start a new one.
1. More people will look at it and help you
2. It gathers important information in one place
3. It keeps the information on the first page(s) so people will look at it and join it instead of starting new threads.

The biggest problem with the forums is that helpful information is fragmented by a zillion threads about the same thing. More people would get more help with their sound if there was not 5,000 threads about "no sound" or "can't get my mic working"

So please, do not start a new thread if you can at all help it but if you do please make the title relevant to your specific problem with your specific hardware.

Sorry about the rant. maybe I should start thread about this.....:lolflag:

---

### Post by markbuntu on 2009-04-28
> **jasonpeel said:**
> hi All

basically this worked for me but i have one last issue - 
using an Audigy 2 card with the front panel and rear card and cant get sound out of the card only the front panel via the headphone socket.  any clues on where to go next greatly appreciated.

thanks 

Jason

Did you check the levels in the alsa mixers and make sure the channels are not muted?
If you are coming from windoze, windoze can reconfigure your outputs for you so make sure you are plugged into the right jacks.
The audigy2 driver also defaults with the analog/digital switch selected for digital so you might want to check that first though that should also effect the headphones.....hmmm... let me know how you make out

---

### Post by mavk84 on 2009-04-28
> **markbuntu said:**
> There is an ongoing thread about people fixing their sound after upgrading/installing Jaunty here.

[http://ubuntuforums.org/showthread.php?t=1136670](http://ubuntuforums.org/showthread.php?t=1136670)

It is always better to join a ongoing thread than start a new one.
1. More people will look at it and help you
2. It gathers important information in one place
3. It keeps the information on the first page(s) so people will look at it and join it instead of starting new threads.

The biggest problem with the forums is that helpful information is fragmented by a zillion threads about the same thing. More people would get more help with their sound if there was not 5,000 threads about "no sound" or "can't get my mic working"

So please, do not start a new thread if you can at all help it but if you do please make the title relevant to your specific problem with your specific hardware.

Sorry about the rant. maybe I should start thread about this.....:lolflag:

sorry about that, but the title of this thread gave me some hopes :lolflag:

I will try every combination in my alsa-base.config and see what happens:)

---

### Post by markbuntu on 2009-04-28
Anyway, for the DV7 try adding 

enable_msi=1

to the end of the /etc/modprobe.d/alsa-base file.

don't forget to reboot.

---

### Post by networm1230 on 2009-04-28
get all plugins gstreamer

---

### Post by linuxrrules on 2009-04-28
I had two problems which I solved.  Both problems didn't exist in 8.10.  The problems first showed up and persisted when I upgraded to 9.04

Problem 1)  Desktop #1 (32 bit Pentium D) had no sound while watching YouTube videos.  All system sound, sound from DVD and sound from Rythmbox worked during this time.  Also during this time, I noticed that when Firefox played one complete video on YouTube or when I tried to switch to another video while the original was playing - Firefox would crash and a 'Force Quit' was necessary.  Again, this playing of video was without sound.

Problem 2)  Desktop #2 (64 bit AMD Quad Core) could not play a video on YouTube.  During this time, I could play a DVD no problem.

I think I read on a site somewhere that Flash could not automatically be reinstalled because of rules governing the fact that it's not open source.  In other words, I don't think Canonical is allowed to uninstall and then reinstall during an upgrade.  If Canonical could, then I wouldn't have never seen the above problems.  However, the user is allowed to uninstall and reinstall.  So, I typed the following two commands below and it fixed the above problems perfectly:

$ sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree
$ sudo apt-get install flashplugin-installer flashplugin-nonfree

---

### Post by slimjim4959 on 2009-04-29
Hello all,

I have read through this thread along with some other guides on the internet but I seem to be having a strange problem.

My system technically does have sound but not right away. At the login screen I get the drum beat but after I type in my name/password the sound cuts out. I get no startup sound, rhythmbox won't play, and firefox has no sound.

If I run ```
sudo /sbin/alsa force-reload
``` then my sound seems to come back. But this is a stop gap and it's kind of annoying to have to run this command everytime I start my computer because it also crashes skype, firefox, pidgin etc.

I was just wondering if anyone had any tips for me because I am completely stumped. I have been searching around for days but I just can't find anything helpful.

I guess I should mention that I am using the Eee PC 1000he with 9.04 netbook edition

Thanks for all of your help!

---

### Post by Rawbin on 2009-04-29
Hi there, 

my sound is working just fine with pulseadio - mostly thanks to this thread (except my mic, i can't record audio from it with audio-recorder - but skype can use it directly somehow, so thats not a big deal)

But here is one question i have (which i think will fit in this thread):

I have a tv card listed as sound source in pulseaudio, and if i open tvtime the volume meter for this recording source shows that sound is playing (i can even record input from this source with audio-recorder, but there is some samplerate problem which makes the sound recorded "squeaky")

i want to "pipe" sound from this source directly to my speakers (since i can't get tvtime to use this pulseaudio source) - i managed to do so using ```
parec -d TV_CARD | paplay -d AUDIO_CARD --rate=32000
``` - sound is good using this method but it's lagging behind the video so maybe someone knows a better way (in 8.10 i used sox, piping two alsa devices, but somehow my tv card isn't listed as a pcm in aplay -L anymore)

any help is appreciated

---

### Post by gorean on 2009-04-30
I really need some help as I have a big need to record music.

This is a clean Jaunty 9.04 install.
Issue:
I can play sound but "aplay" does not show my Tascam us-122l and I can't use it.
It may be worthy of note that keeping the Tascam us-122l plugged in during boot up is problematic in that it more often than not stalls the boot process negotiating for it's desired address.  Plugging it in after boot it inserts itself nicely it seems.
The thought has come to me that it may not show up because the sound servers are already active.
I have stopped and restarted pulse per the man page:
pulseaudio --kill
pulseaudio --start

No change.
There is no man page for "alsa".  Possibly I need to ask for something more specific.

Then I found this command later in this thread.
 "sudo /sbin/alsa force-reload"
{the results follow}
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Terminating processes: 3002 3152lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
james@jaunty:~$ sudo /sbin/alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Terminating processes: 3831 3836lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-usb-us122l snd-usb-lib snd-hwdep snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-usb-us122l snd-usb-lib snd-hwdep snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

So alsa is loading the module but still the Tascam is not offered.
Following is the output for some of the general commands for checking sound stuff.

james@jaunty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is the output of the general commands for checking sound stuff.

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards (lists it fine)
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC655 at irq 17
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/005)

The modules seem to be loaded.

lsmod|grep '^snd'
snd_usb_us122l         23424  0 
snd_usb_lib            24320  1 snd_usb_us122l
snd_hwdep              15108  1 snd_usb_us122l
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  18 snd_usb_us122l,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm


lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

Pulse audio device chooser also does not show the Tascam but it seems likely it gets it's info from aplay.

Other things I have done so far.
First I started with the conventional ubuntu stuff.
Followed the instructions on this page:[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) (title jaunty sound solutions)

Next I found a reference in that thread lead me to:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Titled: Comprehensive Multimedia & Video Howto 
The only thing this installed that might have a bearing on my issue was alsa-oss.  The gstreamer stuff was already installed and the rest was flash and the JRE pack from sun (Java).
One flashplugin did not install.  I can deal with that some other time. I think it has to do with an issue I read about in another thread about rule on the canonical archive site.

All of these tutorials and guides were well written.  It might be helpful to remind the reader to enable the appropriate repository info.
Like, be sure to check the box for Patent and legal issues.  Maybe I missed that.

Anyway, help would be good.  This is the second installation attempt.  The last one finally blew up from a scripted attempt at an alsa upgrade.

---

### Post by johnaaronrose on 2009-04-30
markbuntu,
Any word yet on the hda_intel kernel correction? There is a large amount of confusion! There are a number of threads on Ubuntu Forums and bugs on Launchpad: there are many variants of the options command & others to be applied to various files.

---

### Post by markbuntu on 2009-04-30
> **johnaaronrose said:**
> markbuntu,
Any word yet on the hda_intel kernel correction? There is a large amount of confusion! There are a number of threads on Ubuntu Forums and bugs on Launchpad: there are many variants of the options command & others to be applied to various files.

There are some patches from the alsa devs making their way into the update pool, when they will be released in updates I do not know. 

That said I think that many machines will still need specific options manually entered in /etc/modprobe.d/alsa-base because of the difficulty in autodetecting the zillion configurations OEMs have used to tweak their hda sound chips. 

Most OEMs are not very forthcoming about this information so if you want to help out please bug your manufacturer to publish the specs or at least send them to the alsa devs so proper drivers can be implemented.

---

### Post by markbuntu on 2009-04-30
> **gorean said:**
> I really need some help as I have a big need to record music.

This is a clean Jaunty 9.04 install.
Issue:
I can play sound but "aplay" does not show my Tascam us-122l and I can't use it.
It may be worthy of note that keeping the Tascam us-122l plugged in during boot up is problematic in that it more often than not stalls the boot process negotiating for it's desired address.  Plugging it in after boot it inserts itself nicely it seems.
The thought has come to me that it may not show up because the sound servers are already active.
I have stopped and restarted pulse per the man page:
pulseaudio --kill
pulseaudio --start

No change.
There is no man page for "alsa".  Possibly I need to ask for something more specific.

Then I found this command later in this thread.
 "sudo /sbin/alsa force-reload"
{the results follow}
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Terminating processes: 3002 3152lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
james@jaunty:~$ sudo /sbin/alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Terminating processes: 3831 3836lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-usb-us122l snd-usb-lib snd-hwdep snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-usb-us122l snd-usb-lib snd-hwdep snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

So alsa is loading the module but still the Tascam is not offered.
Following is the output for some of the general commands for checking sound stuff.

james@jaunty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is the output of the general commands for checking sound stuff.

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards (lists it fine)
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC655 at irq 17
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/005)

The modules seem to be loaded.

lsmod|grep '^snd'
snd_usb_us122l         23424  0 
snd_usb_lib            24320  1 snd_usb_us122l
snd_hwdep              15108  1 snd_usb_us122l
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  18 snd_usb_us122l,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm


lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

Pulse audio device chooser also does not show the Tascam but it seems likely it gets it's info from aplay.

Other things I have done so far.
First I started with the conventional ubuntu stuff.
Followed the instructions on this page:[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) (title jaunty sound solutions)

Next I found a reference in that thread lead me to:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Titled: Comprehensive Multimedia & Video Howto 
The only thing this installed that might have a bearing on my issue was alsa-oss.  The gstreamer stuff was already installed and the rest was flash and the JRE pack from sun (Java).
One flashplugin did not install.  I can deal with that some other time. I think it has to do with an issue I read about in another thread about rule on the canonical archive site.

All of these tutorials and guides were well written.  It might be helpful to remind the reader to enable the appropriate repository info.
Like, be sure to check the box for Patent and legal issues.  Maybe I missed that.

Anyway, help would be good.  This is the second installation attempt.  The last one finally blew up from a scripted attempt at an alsa upgrade.

There is a tutorial for loading the firmware for a tascam us122 here. You need to do that for it to work.

[http://alsa.opensrc.org/Tascam_US-122http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122http://alsa.opensrc.org/Tascam_US-122)

---

### Post by markbuntu on 2009-04-30
> **slimjim4959 said:**
> Hello all,

I have read through this thread along with some other guides on the internet but I seem to be having a strange problem.

My system technically does have sound but not right away. At the login screen I get the drum beat but after I type in my name/password the sound cuts out. I get no startup sound, rhythmbox won't play, and firefox has no sound.

If I run ```
sudo /sbin/alsa force-reload
``` then my sound seems to come back. But this is a stop gap and it's kind of annoying to have to run this command everytime I start my computer because it also crashes skype, firefox, pidgin etc.

I was just wondering if anyone had any tips for me because I am completely stumped. I have been searching around for days but I just can't find anything helpful.

I guess I should mention that I am using the Eee PC 1000he with 9.04 netbook edition

Thanks for all of your help!

Maybe you should try reinstalling alsa. This will purge any screwy configuration files which is most likely your problem since you get the drumbeat which means your sound card is recognized and using the correct driver.

You can also try making a new user and see if that fixes your problem.

To reinstall ALSA

(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

---

### Post by WRISOFT.NET on 2009-04-30
My Gateway P-6860FX also lost speaker sound after upgrading from intrepid. However, if I boot into the previous kernel 2.6.27-11, both speakers and headphones work perfectly. I've tried all kinds of fixes from editing alsa-base.conf to reinstalling alsa drivers without any luck. Maybe the problem lies in the 2.6.28 kernel upgrade from intrepid to jaunty. Any thoughts?

---

### Post by mrbubblesort on 2009-04-30
In bit of a rush to catch my flight to China, so if someone has already posted this info, I apologize.     Anyone reading this thread with a Gateway laptop (mine's a 6860-fx), check this thread out:

[http://ubuntuforums.org/showthread.php?t=1140667](http://ubuntuforums.org/showthread.php?t=1140667)

Worked like a charm.  Thanks to everyone who helped out.

---

### Post by karth83 on 2009-05-01
If Internal Mic Volume is low in some laptops especially DELL, you can try it increasing. Click pulse audio applet and goto manager. Select Manager and click Devices tab. Under Sources select alsa input something like that and click properties. Try increasing the volume to 150% or so and test your mic volume using sound recorder. Hope this solves the low volume mic problem.

---

### Post by DarkAngel88 on 2009-05-01
Hi there, just poking to see if I'm the only one with this issue.  Since I upgraded from 8.10 to 9.04, I'm having sound issues with VLC.  Problem is, I've tried virtually everything to get it to work but still no luck, the sound is glitching when using VLC.  Only way now is to use mplayer to watch my videos.

I'm a big vlc fan and I'd like to know if I'm the only one with this issue.  Running version 0.9.15 of pulseaudio btw.

---

### Post by markbuntu on 2009-05-01
> **DarkAngel88 said:**
> Hi there, just poking to see if I'm the only one with this issue.  Since I upgraded from 8.10 to 9.04, I'm having sound issues with VLC.  Problem is, I've tried virtually everything to get it to work but still no luck, the sound is glitching when using VLC.  Only way now is to use mplayer to watch my videos.

I'm a big vlc fan and I'd like to know if I'm the only one with this issue.  Running version 0.9.15 of pulseaudio btw.

Are you using the 2.6.29 kernel with that?
Do you have vlc set to use pulseaudio?
Do you have simultaneous output set or module combine?
Do you have all the xine-xtras. I like vlc too but have not had time to play with it yet with 0.9.15.

Also, I am going to post a pulse0.9.15 guide as soon as I get it fully figured out...maybe this weekend....maybe later, but soon.

---

### Post by DarkAngel88 on 2009-05-01
> **markbuntu said:**
> Are you using the 2.6.29 kernel with that?
Do you have vlc set to use pulseaudio?
Do you have simultaneous output set or module combine?
Do you have all the xine-xtras. I like vlc too but have not had time to play with it yet with 0.9.15.

Also, I am going to post a pulse0.9.15 guide as soon as I get it fully figured out...maybe this weekend....maybe later, but soon.

Thanks for your reply markbuntu !

I'm currently using kernel 2.6.30-rc2 as I'm also having issues with my intel graphic card.  Tried with 2.6.28 (stock one from jaunty) and I'm still having the issues.  VLC is indeed using pulseaudio output.  About the simultaneous outputs, I haven't played with this so my guess is that it's the default values...

I just wish I haven't upgraded to 9.04 !!  I'm having weird issues that wasn't part of 8.10 !! :(  Do you know what have changed in 0.9.15 exactly ?

---

### Post by ZankerH on 2009-05-02
Is it possible to somehow entirely remove pulse-audio and maintain working sound? I'm asking because wine keeps crashing due to it not supporting pulse audio properly.

---

### Post by gorean on 2009-05-02
> **markbuntu said:**
> There is a tutorial for loading the firmware for a tascam us122 here. You need to do that for it to work.

[http://alsa.opensrc.org/Tascam_US-122http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122http://alsa.opensrc.org/Tascam_US-122)

Your right.  I used a Tascam 122.  That one was easy.  The new one (Tascam 122L) however is proving a more challenging task.
Perhaps I am overlooking something so obvious I can not find it.  This has happened to me before.

---

### Post by alex777 on 2009-05-03
That's a really nice guide, but it didn't help me. I have USB speakers Genius SP-i202U, they are detected by the system as "USB Audio Device", and even volume control buttons on the speaker work (I can see the volume sliders in PulseAudio Volume Control move) - but no sound!

Can anyone help?

---

### Post by markbuntu on 2009-05-03
> **alex777 said:**
> That's a really nice guide, but it didn't help me. I have USB speakers Genius SP-i202U, they are detected by the system as "USB Audio Device", and even volume control buttons on the speaker work (I can see the volume sliders in PulseAudio Volume Control move) - but no sound!

Can anyone help?

Did you try moving the playing streams to the usb device in the pulseaudio volume control?

---

### Post by markbuntu on 2009-05-03
> **ZankerH said:**
> Is it possible to somehow entirely remove pulse-audio and maintain working sound? I'm asking because wine keeps crashing due to it not supporting pulse audio properly.

Have you tried setting wine to use OSS and then changing the wine launcher to padsp wine?

---

### Post by markbuntu on 2009-05-03
> **DarkAngel88 said:**
> Thanks for your reply markbuntu !

I'm currently using kernel 2.6.30-rc2 as I'm also having issues with my intel graphic card.  Tried with 2.6.28 (stock one from jaunty) and I'm still having the issues.  VLC is indeed using pulseaudio output.  About the simultaneous outputs, I haven't played with this so my guess is that it's the default values...

I just wish I haven't upgraded to 9.04 !!  I'm having weird issues that wasn't part of 8.10 !! :(  Do you know what have changed in 0.9.15 exactly ?

A lot has changed in Jaunty. ALSA 1.0.18 and Pulse 0.9.14 which both have a lot of changes since Intrepid. Also changed was a lot of the xine libs which vlc and KDE4/Phonon use and a lot of changes have been implemented in the kernel as well. I have found that changing settings in the xine-ui is necessary to change the xine defaults for amarok so you might want to try that for vlc.

---

### Post by alex777 on 2009-05-04
> **markbuntu said:**
> Did you try moving the playing streams to the usb device in the pulseaudio volume control?

Yes, I did. I have 3 sound devices on my laptop: small built-in HDA speakers, a USB headset VXI and USB speakers Genius. The first two work all-right, but my USB speakers (which I obviously want to make the default sound device) produce no sound, and moving sound streams doesn't help.

---

### Post by markbuntu on 2009-05-04
> **alex777 said:**
> Yes, I did. I have 3 sound devices on my laptop: small built-in HDA speakers, a USB headset VXI and USB speakers Genius. The first two work all-right, but my USB speakers (which I obviously want to make the default sound device) produce no sound, and moving sound streams doesn't help.

I know that some logitech usb speaker sets do not work because they are not usb standard compliant and in windows require a special driver which is not available for linux. Perhaps you have a similar problem since your other devices seem to be working fine.

Do the speakers show up in the volume controls?

---

### Post by alex777 on 2009-05-05
> **markbuntu said:**
> 
Do the speakers show up in the volume controls?

**markbuntu**, thank you for your assistance! My usb speakers suddenly started working and after a while I figured out what they wanted me to do :-) That's a minor problem, and I don't know why, but after each reboot the speakers need to be turned off and then on again (by pressing a button on one of the speakers). They just probably want to draw my attention this way so I don't forget about them :-)

---

### Post by crjackson on 2009-05-05
> **alex777 said:**
> **markbuntu**, thank you for your assistance! My usb speakers suddenly started working and after a while I figured out what they wanted me to do :-) That's a minor problem, and I don't know why, but after each reboot the speakers need to be turned off and then on again (by pressing a button on one of the speakers). They just probably want to draw my attention this way so I don't forget about them :-)

Your speakers sound like a needy girlfriend. :roll:

---

### Post by mozychan on 2009-05-06
> **markbuntu said:**
> There are some patches from the alsa devs making their way into the update pool, when they will be released in updates I do not know. 

That said I think that many machines will still need specific options manually entered in /etc/modprobe.d/alsa-base because of the difficulty in autodetecting the zillion configurations OEMs have used to tweak their hda sound chips. 

Most OEMs are not very forthcoming about this information so if you want to help out please bug your manufacturer to publish the specs or at least send them to the alsa devs so proper drivers can be implemented.

hmm, thanks for the info.  I'll be waiting for implementation of fixes patiently... :-|

-moose

---

### Post by FredBarns on 2009-05-07
Hi everyone,

I just upgraded to Jaunty and have been having a heck of a time making sound work. I have read through these forums and tried to use the guides but with no luck.  Here is what I suspect.  When I click on pulse audio volume control and look at the output devices, I only see "simultaneous output"  That is, no hardware output devices.  I do see things like ALSA firefox plugin and totem in the playback tab, and the bar in moving, so sound is going in. I think the reason it is not getting out is it can't find my hardware sound card.

This is supported to a degree by the fact that I cant find this file.

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

or even the /driver directory.

I can get sound sometime usings HDA... anolog OSS in instead of Pulse audio in the chooser. I can get sound files to play, but not sound from my bowser (Youtube, for example.)

I am at a loss and any kind advice you have would be appreicated.  I am using a Dell latitude D520, and every worked fine before the upgrade.

Thanks so much for the help.

---

### Post by markbuntu on 2009-05-09
> **FredBarns said:**
> Hi everyone,

I just upgraded to Jaunty and have been having a heck of a time making sound work. I have read through these forums and tried to use the guides but with no luck.  Here is what I suspect.  When I click on pulse audio volume control and look at the output devices, I only see "simultaneous output"  That is, no hardware output devices.  I do see things like ALSA firefox plugin and totem in the playback tab, and the bar in moving, so sound is going in. I think the reason it is not getting out is it can't find my hardware sound card.

This is supported to a degree by the fact that I cant find this file.

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

or even the /driver directory.

I can get sound sometime usings HDA... anolog OSS in instead of Pulse audio in the chooser. I can get sound files to play, but not sound from my bowser (Youtube, for example.)

I am at a loss and any kind advice you have would be appreicated.  I am using a Dell latitude D520, and every worked fine before the upgrade.

Thanks so much for the help.

This seems to be a problem with some upgrades, not really common but not so rare either. What you should do is to reinstall alsa completely so any leftover configs can also be purged.



(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

If you needed to edit your /etc/modprobe.d/alsa-base file you may not have to with the updated driver but if you still do the file in Jaunty is is /etc/modprobe.d/alsa-base.conf. This is to conform to configuration file naming conventions. 

Then follow the guide. let me know how this works out for you.

---

### Post by FredBarns on 2009-05-09
Dear Markbuntu,

Thanks so much for the response.  I did what you suggest, but no joy.

I have set all my sound preferences under the "device" tab to "pulse audio sever" except default mixer tracks that I have set to "capture:HDA intel - stack92xx analog (PulseAudio Mixer)" which is the closest thing to name of my sound card that I can find her. 

when I hit the test buttons I get silence.  If I change them choices to HDA intel stack92xx Analog (OSS) I do get sound when I click the buttons.  This also makes my MP3's play when loaded in player, but I stil do not get any sound from Firefox.

Should I be seeing a hardway output devices at all in pulse audio  volume control?  I only see "simultanious output"

could it just be that my flash plugin is broken, I wonder?  Settin my prefereces to OSS does not follow the guides, so it seems something else must be wrong.

What do you think?

---

### Post by markbuntu on 2009-05-09
Try turning off the simultaneous output and any rtp settings in the Configure Local Sound Server from the padevchooser and logout and login.

---

### Post by FredBarns on 2009-05-09
I did as you suggested, but nothing changed.

---

### Post by markbuntu on 2009-05-09
Ok, stop pulseaudio and run it from a terminal so we can see what is going on

killall pulseaudio

pulseaudio -vvv

Most likely what we want to see is as pulse starts up. It should be finding alsa sinks and sources, those are the messages we need to see.

You can also try reinstalling pulseaudio. That might fix whatever weirdness is going on.

---

### Post by FredBarns on 2009-05-09
Thanks for your help.  I killed pulseaudio and here is what I got:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 78e82c71622faf1b78f21e00489212ff.
I: main.c: Using runtime directory /home/jpconley/.pulse/78e82c71622faf1b78f21e00489212ff:runtime.
I: main.c: Using state directory /home/jpconley/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

I am happy to try reinstalling but I hesitated because when I started to do so it would also have uninstalled quite a few other packages.

---

### Post by markbuntu on 2009-05-10
Remove or rename the /home/jpconley/.pulse directory and restart pulse. That directory is left over from before the upgrade and the files are most likely wrong and are not necessary for pulse to run.

---

### Post by FredBarns on 2009-05-10
Hi Again,

did that, rebooted, but no change.  Should I reinstall Pulse audio?

---

### Post by markbuntu on 2009-05-10
What does aplay -l tell you

---

### Post by FredBarns on 2009-05-10
I'm not sure I understand the question. Nothing plays (not system sounds, MP3's or sound in FF.

---

### Post by FredBarns on 2009-05-10
Sorry to be such a noob. Okay, aplay, a command line audio player.  I tried it with an MP3, no sound, but here is what I got at the command line:

Playing raw data '/home/jpconley/9-archive/Prime.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
^CAborted by signal Interrupt...

---

### Post by markbuntu on 2009-05-10
OK, go here and follow the directions


[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

---

### Post by FredBarns on 2009-05-10
Okay, did it.  I have a lot of data.  I don't have the expertise to detect what might be wrong.  Nothing is obiously an error to me:

jpconley@jpconley-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
jpconley@jpconley-laptop:~$ lsusb
Bus 001 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jpconley@jpconley-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 21
jpconley@jpconley-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
jpconley@jpconley-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jpconley@jpconley-laptop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jpconley@jpconley-laptop:~$ 
jpconley@jpconley-laptop:~$

---

### Post by raptor2552 on 2009-05-11
I am having this exact problem in Ubuntu 9.04 amd64. I can record the output of rhythmbox (with sound recorder AND audacity) when connecting to the monitor BUT nothing when using the mic even though _the mic plays through the speakers_.

When I kill pulseaudio and then start it up I see three errors:
```
E: module-rtp-send.c: Source does not exist.
E: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_SOURCE@ loop=0"): initialization failed.
E: module-gconf.c: pa_module_load() failed
```
Is there a package I need?

output of arecord -l:
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

output of arecord -L
```
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

my sound card
cat /proc/asound/cards
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe7f8000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe8fc000 irq 17


```

output of lspci
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
[COLOR="Red"]00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
[COLOR="Red"]01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device[/COLOR] **Note: This is my video??**
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```

---

### Post by Sxeptomaniac on 2009-05-11
I've also been stuck on this one.  I've got an HP DV6z (an HD ATI SB), and every fix I've tried so far has had absolutely no effect.  I've tried editing /etc/modprobe.d/alsa-base.conf a couple of different ways, uninstalling ALSA and replacing it with OSS, upgrading ALSA to 1.0.20, and downgrading my Kubuntu install to 8.04.  

I haven't tried [the fix listed here yet]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870"), but that's next, when I have some time.  I haven't been stumped on a problem like this before.  Usually a quick couple of searches comes up with a fix, but this time there are people all over trying things that don't work for me.

I've been reduced to using Windows on my own equipment again.

---

### Post by markbuntu on 2009-05-11
> **raptor2552 said:**
> I am having this exact problem in Ubuntu 9.04 amd64. I can record the output of rhythmbox (with sound recorder AND audacity) when connecting to the monitor BUT nothing when using the mic even though _the mic plays through the speakers_.


Try playing around with the capture devices in one of the the alsa mixers, either the one on the panel or the gnome-alsa mixer. You may need to enable them in the edit/preferences tab. It is the capture settings that are for recording. At least you know your mic can work which is a big problem for a lot of people. Also, be sure to follow the OP exactly.

---

### Post by markbuntu on 2009-05-11
> **FredBarns said:**
> Okay, did it.  I have a lot of data.  I don't have the expertise to detect what might be wrong.  Nothing is obiously an error to me:


What model is your dell?

---

### Post by markbuntu on 2009-05-11
> **Sxeptomaniac said:**
> I've also been stuck on this one.  I've got an HP DV6z (an HD ATI SB), and every fix I've tried so far has had absolutely no effect.  I've tried editing /etc/modprobe.d/alsa-base.conf a couple of different ways, uninstalling ALSA and replacing it with OSS, upgrading ALSA to 1.0.20, and downgrading my Kubuntu install to 8.04.  

I haven't tried [the fix listed here yet]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870"), but that's next, when I have some time.  I haven't been stumped on a problem like this before.  Usually a quick couple of searches comes up with a fix, but this time there are people all over trying things that don't work for me.

I've been reduced to using Windows on my own equipment again.

It looks like that may be the way to go since you have pretty much tried everything else.

---

### Post by raptor2552 on 2009-05-11
Why does this have to be so hard? I got it working for anyone interested. You'll have to discover your own hardware ( I have the HDA Intel AD198x) setup but basically:

System > Preferences > Sound
set Sound Events, Music and Movies, Audio Conferencing.Sound > Playback to: PulseAudio Sound Server
set Audio Conferencing.Sound > Capture to:Hardware device, e.g., HDA Intel AD198x Analog ALSA
set Default Mixer Tracks to: Hardware device e.g., Playback: HDA Intel - AD198x (PulseAudio)
	
Volume Control (click on speaker icon in panel)
click on Device: and select your hardware device that most closely matches your Capture Hardware selected above (for example HDA Intel (ALSA Mixer)
click on the Preferences button to make sure all your devices are selected. In the case of my Intel card: 
Under playback: Master, PCM, Line-in, CD, microphone, Mic boost, Analog mix
Under recording: capture
under options: input source

click on the Options tab, select mic for input source
click on the Recording tab be sure capture volume is up and the speaker icon is enabled (don't fret over the mic icon)
click on the Playback tab make sure the volumes are turned up and enabled. Note that the microphone only needs to be unmuted if you want to monitor what is coming thru the mic, otherwise leave it muted as it will only introduce noise and most likely feedback into your recording


Start Sound recorder and enjoy (not my favorite app)

Prefered app - Audacity
With this you may easily select between a mic and other input devices be sure the Device Toolbar is visible
Next to the speaker icon (Playback) select ALSA: pulse
	
To use the mic:
Next to the mic icon (Input) select the hardware device in my case: ALSA: HDA Intel: AD198x Analog (hw:0,0)
Record from the mic and enjoy. Remeber, to monitor your mic session you'll need to unmute the mic in the volume control.
	
To record from say Rhythmbox:
Next to the mic icon (input) select the hardware device select ALSA: pulse, and in your System > Preferences > Sound set Audio ConFerencing > Sound Capture to: PulseAudio Sound Server, you can now record from Pulses Monitor using this guide, [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by FredBarns on 2009-05-11
Hi Markbuntu,

Thanks again for your help. It is a latitude d520  I attach a screen shot that shows my current settings.  Perhaps I am doing something really stupid.

---

### Post by markbuntu on 2009-05-12
If you turn off the service discovery in the device chooser and turn off the rtp sender and receiver stuff and simultaneous output what happens?

---

### Post by markbuntu on 2009-05-12
If you turn off all the notifications and uncheck any boxes in Multicast RTP and turn off simultaneous output what do you get in output devices?

---

### Post by FredBarns on 2009-05-12
Still no luck.  Is reinstalling pulse audio likely to help.  I am about at the edge of doing a clean install, but that would require quite a bit of effort to get everything back the way it was.  I do get login sounds up until the desktop comes up.  I had a look at pulse audio manager.  I wonder if it is meaningful that default sink is "auto_null"

---

### Post by markbuntu on 2009-05-12
Try this, make a new user and log in with that.

---

### Post by FredBarns on 2009-05-12
Good thought, but still no sound with a new user.

---

### Post by johnaaronrose on 2009-05-13
Raptor3552,

I've followed your instructions for a laptop & a desktop. Both now work OK for Sound Recording. For Audacity on both desktop & laptop, the devices toolbar is not shown for a user with administrative privileges but is shown for a user without administrative privileges! However, you can get to it (for a user with administrative privileges) by bringing up the Edit/Preferences window using the appropriate top menu selection.

In the gnome volume control after unmuting the microphone icon (in the Recording tab's Capture column), it becomes mute again after the window is closed and opened! This is already posted on Launchpad as bug 299642.

I still have a problem with Skype recording (checked by using its Options window to make a test call and then listening to the call being played back). Sometimes it works OK. I thought it might be to do with the 'Allow Skype to adjust my mixer levels' (in the Skype Options window). But clearing or setting that check box has no effect on the test call success. I'd previously set this to pulse for each of Sound In, Sound Out & Ringing, as recommended by another thread/posting (whose details I forget). What do you recommend as settings here? 

However, I then thought of the PulseAudio Volume Control. The Input Devices tab was showing the volume as 0% and the speaker icon as mute. I don't know what caused this to happen as it was previously at 100%. Unmuting it and settng it back to 100% didn't result in Skype test call success! The Show list box is currently at 'All except monitors'. Any recommendation for the Show list box?

---

### Post by Pitboss on 2009-05-13
Hey, man now I have fully working audio thanks very much for your advice. However I have trouble when talking over skype. People from the other side report that they hear themselves rather than hear me, and hear some noise. If anyone has gone through this please let me know.

Thanks, in advance.

EDIT: I understood what the problem is, but I don't know how to fix it. It seems that for some reason, when there is output sound it goes in the input channel, that is that when I'm playing mp3, and trying to record my voice, I hear the mp3 so loud and I almost can't hear my voice.

Pitboss

---

### Post by peternz on 2009-05-13
I tried a LOT of things to fix my sound.  Uninstalled pulse, ALSA, reinstall alsa, try adding various lines to config files, etc.

So I've no idea if it was really the last step I tried that fixed it, or a combination of a lot of things.

But I did eventually notice a sneaky little config that I don't think was on my 8.10 setup.

System > Preferences > Default Sound Card.

The default was blank.  So I simply chose my sound card. Instant sound.

Long may it last.

I do find it unfortunate that one of the most basic functions of my desktop computer (audio) causes me the biggest trouble in Ubuntu.

Peter

---

### Post by gewitty on 2009-05-13
Can anyone tell me why in 64bit Jaunty the lib32asound-plugins file is deleted whenever Skype, Picasa, or any Wine-based app is installed. Or why Skype, Picasa and any Wine-based app is deleted when lib32asound-plugins are re-installed. Which means you can have one or the other, but not both.

lib32asound-plugins seem to be crucial for many multimedia apps to work (Audacity, Amarok, VLC, etc).

System sounds and Skype sound are unaffected by the problem.

There is a discussion about this on the 64bit forum, but so far it has not provided any solution.

---

### Post by fifth on 2009-05-13
Many thanks for your post markbuntu.

I did have sound on Jaunty but silence in Karmic. I never thought to check the user groups, but reading your post I found I was not a member of any of the Pulse groups.

All working now :D

---

### Post by l-x-l on 2009-05-13
> **markbuntu said:**
> **Jaunty 9.04 Sound Solutions**
** Necessary Packages**
As with Hardy and Intrepid, some important packages necessary for optimal sound set up are missing. Open System/Adminstration/Synaptic package manager and search pulse. This is the easiest way to find and install all  the packages we need. Select the following packages 

padevchooser  -this will pull in all the pulseaudio guis and their dependencies

if you plan on using vlc or xmms2 or 32 bit or libao apps etc, you can get those packages now too. If you are not constrained on disk space it is a good idea to get all of the following

vlc-plugin-pulse          -this also pulls in a lot of libs that vlc will need
xmms2-plugin-pulse   -this also pulls in the xmms2 core
pulseaudio-module-lirc - this is to use lirc and your infrared remote with pulse
libsdl1.2debian-all -this wil replace the alsa version with all available drivers
lib32asound2-plugins -this is the 32 bit plugins for 32 bit apps
libao2 - you need this for apps using the libao cross platform library
asoundconf-gtk -applet for default alsa sound card
audacious-plugins-extra -plugins for audacious for many codecs like MP3, aac, FLAC, WMA, etc

Hi Mark.. when I attempt to install these I get the following msg:
```

The following packages will be REMOVED:
  flashplugin-installer ia32-libs libsdl1.2debian-alsa nspluginwrapper
```

Will I miss these packages? Particularly the flashplugin & nspluginwrapper?

---

### Post by gewitty on 2009-05-14
> **l-x-l said:**
> Hi Mark.. when I attempt to install these I get the following msg:
```

The following packages will be REMOVED:
  flashplugin-installer ia32-libs libsdl1.2debian-alsa nspluginwrapper
```

Will I miss these packages? Particularly the flashplugin & nspluginwrapper?

I also found that when installing lib32asound2-plugins, this removes both Skype and any Wine-based apps, such as Picasa. However, I since got my machine working OK without this package. Sound works fine if I follow all of the How To guide, but substitute lib32asound2 for the lib32asound2-plugins. This also leaves Skype and Wine apps installed.

I can't say why this works, as I'm not sufficiently experienced to understand what these two packages are doing exactly. But it solved my problem.

---

### Post by Pitboss on 2009-05-17
> **Pitboss said:**
> Hey, man now I have fully working audio thanks very much for your advice. However I have trouble when talking over skype. People from the other side report that they hear themselves rather than hear me, and hear some noise. If anyone has gone through this please let me know.

Thanks, in advance.

EDIT: I understood what the problem is, but I don't know how to fix it. It seems that for some reason, when there is output sound it goes in the input channel, that is that when I'm playing mp3, and trying to record my voice, I hear the mp3 so loud and I almost can't hear my voice.

Pitboss

Hey I still have this problem and it's seriously pissing me off. So if anyone can help I'd appreciate it.

---

### Post by markbuntu on 2009-05-17
Do you have pcm capture selected?

---

### Post by Pitboss on 2009-05-17
> **markbuntu said:**
> Do you have pcm capture selected?

Well I don't know how to check this. :blush

EDIT: I found this:

```
pitboss@swamp:~$ cat /proc/asound/pcm 
00-00: VT1708B Analog : VT1708B Analog : playback 2 : capture 2
00-01: VT1708B Digital : VT1708B Digital : playback 1
01-03: ATI HDMI : ATI HDMI : playback 1

```

---

### Post by markbuntu on 2009-05-17
Look in the alsa volume controls. If you have the gnome-alsamixer that is the best place to look. make sure the record box in not checked under PCM.

---

### Post by harveygfl on 2009-05-17
I am glad that you got your Audio working. I am having similar audio problems... 
I would like to know your hardware Configuration, I Am using .. 
-Intel BOXDX58SO LGA 1366 Intel X58 ATX Intel Motherboard 
-&#65279;Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor
-CORSAIR DOMINATOR 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Triple Channel Kit Desktop Memory
-POWERCOLOR AX4870 1GBD5-PPH Radeon HD 4870 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card 
-Pioneer 20X DVD±R DVD Burner Black SATA Model DVR-216DBK
-Hauppauge WinTV-Nova-S-Plus Video Device 790 PCI Interface

I tried ALSA, OSS, and Pulse as audio drivers and tried various combinations.. I was not able to successfully get my sound working. ..   as you know its fustrating.  ( I also tried to disable the  HDA in the BIOS.. No Luck)  I am thinkging the IRQ the sytemboard uses for onboard audio  does not match the some setting in my alsa-config... but that is a guess.    Any Suggestions would be helpful.

Thanks

---

### Post by Pitboss on 2009-05-18
> **markbuntu said:**
> Look in the alsa volume controls. If you have the gnome-alsamixer that is the best place to look. make sure the record box in not checked under PCM.

I don't have a record box under the PCM. I notice the same thing I noticed before: I have two Capture controls in the gnome-alsamixer under which I have two Rec checkboxes and if I mute one of them, it stops recording the music so loudly it records it as if I were montiring it. If I check or unckeck the Rec checkbox under this capture it mutes or unmutes the Input device in the Pulseaudio Volume Control.

---

### Post by 101011010010 on 2009-05-18
*Thankyou for your excellent post. I had no sound in Firefox (Flash 10), Rhythmbox, etc. Installing Padevchooser & pointing it to my usb speakers, as suggested & viola, sound sweet sound. Once again THANKYOU.*  :grin:

---

### Post by markbuntu on 2009-05-18
> **harveygfl said:**
> I am glad that you got your Audio working. I am having similar audio problems... 
I would like to know your hardware Configuration, I Am using .. 
-Intel BOXDX58SO LGA 1366 Intel X58 ATX Intel Motherboard 
-&#65279;Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor
-CORSAIR DOMINATOR 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Triple Channel Kit Desktop Memory
-POWERCOLOR AX4870 1GBD5-PPH Radeon HD 4870 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card 
-Pioneer 20X DVD±R DVD Burner Black SATA Model DVR-216DBK
-Hauppauge WinTV-Nova-S-Plus Video Device 790 PCI Interface

I tried ALSA, OSS, and Pulse as audio drivers and tried various combinations.. I was not able to successfully get my sound working. ..   as you know its fustrating.  ( I also tried to disable the  HDA in the BIOS.. No Luck)  I am thinkging the IRQ the sytemboard uses for onboard audio  does not match the some setting in my alsa-config... but that is a guess.    Any Suggestions would be helpful.

Thanks

You should read this, it is about getting sound working with multiple hardware devices. You have three devices, on-board sound, HDMI sound from the 4870, and tv card sound.


[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by Pitboss on 2009-05-19
Hi, I still haven't resolved the mic problem, but now I'm writing to ask if anyone else experiences this: Amarok and Vlc can't play sound when they are both on. Why does this happen?

---

### Post by markbuntu on 2009-05-19
If VLC is not set to use pulseaudio that can happen.

For the mic problem, open the gnome-alsa mixer and edit/sound card properties and check to see if there are other options that are unchecked. If you check them they will show up in the volume control and you can turn them off. I have some Input Source boxes that I had to reveal that way so I could turn them off.

---

### Post by Pitboss on 2009-05-20
All right, thanks man :) now I have a working mic at last. In the volume control I had to select preferences and then Input Source and then in the newly appeared Input Source tab select mic. 

However the problem with vlc and amarok doesn't resolve. I have selected the audio output of vlc to be pulse but when I play a movie I can't play songs and vice versa. And it's not only that. Skype is acting the same way. Once I read somewhere that pulse can't support more than one application. Is that right?

EDIT: And maybe it's amarok's audio output that causes this problem, but I can't find any option where I can select it.

---

### Post by malathion on 2009-05-20
Installing the packages in the OP uninstalled wine and skype without notifying me. They had to be reinstalled.

That is not cool.

---

### Post by markbuntu on 2009-05-20
> **malathion said:**
> Installing the packages in the OP uninstalled wine and skype without notifying me. They had to be reinstalled.

That is not cool.

Well, I do not use wine or skype so I was unaware of this until recently. lib32asound2-plugins is needed for vlc, audacity, amarok and other applications to work. Skype and wine remove this lib when they are installed. 

This is something that should be taken up with the wine and skype developers since the problem clearly lies with them. Applications should not be removing standard libraries. You should file bug reports.

I have edited the OP to add a note about this problem.

---

### Post by malathion on 2009-05-20
Ah, looks like someone has already rooted this bug out: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/305860](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/305860)

---

### Post by mr_raider on 2009-05-20
I'm trying to get HDMI output in Jaunty 32 bit. Using An Asus m3n78-vm with nvidia 8200 chipset and HDMI out.

My HDMI is recognized as an output. If manually set all the sound preferences to HDA Nvidia HDMI (ALSA), I can play sound via HDMI. But if I set pulseaudio as the default, no sound is produced. In pulseaudio device chooser, volume control, playback, I only have the analog audio output as an option. In Intrepid, I also had HDMI as option in pulse audio.

Any ideas?

---

### Post by d4x2hhhy on 2009-05-21
Hi Guys and girls,
Ive been struggling for some time now with sound issues in Jaunty.  I had a good working system and then bought an HP pavillion DV4 and tried to use Jaunty, when I log in I get a drum type beat which sounds like an error then  eventually fades.  Ive read a lot of stuff and tried changing to OSS or ALSA etc but am now very confused and still no sound.  I think its an integrated Sound Blaster Pro.  Also I managed to get flash working but then no sound, now its died completely.  Maybe I need to start again?

---

### Post by dabdiputs on 2009-05-21
> **mr_raider said:**
> I'm trying to get HDMI output in Jaunty 32 bit. Using An Asus m3n78-vm with nvidia 8200 chipset and HDMI out.

My HDMI is recognized as an output. If manually set all the sound preferences to HDA Nvidia HDMI (ALSA), I can play sound via HDMI. But if I set pulseaudio as the default, no sound is produced. In pulseaudio device chooser, volume control, playback, I only have the analog audio output as an option. In Intrepid, I also had HDMI as option in pulse audio.

Any ideas?

I have the exact same problem with my m3a78-emh with HDMI out on a fresh install of Jaunty. When I choose HDMI in the sound preferences I can hear the test tones, and sound works in some applications (not firefox/flash), but pulse doesn't seem to recognize the HDMI output. I can see the sound playing in pulse's control panel, but the HDMI output is not available and I can't hear anything.

---

### Post by mr_raider on 2009-05-22
I added the following line:

load-module module-alsa-sink device=hw:0,3

To /etc/pulse/defaul.pa

It seems to help as now HDMi is an option in pa device chooser. It still sets the analog as default on log in though.

---

### Post by dabdiputs on 2009-05-22
> **mr_raider said:**
> I added the following line:

load-module module-alsa-sink device=hw:0,3

To /etc/pulse/defaul.pa

It seems to help as now HDMi is an option in pa device chooser. It still sets the analog as default on log in though.

Thanks for the advice, but that doesn't seem to work either. Does it matter where you add this; did you just add this to the end of the file? How did you find the "hw:0,3" part? Is there somewhere I can go to check if that's the right code for my setup?

---

### Post by mr_raider on 2009-05-22
I just added it at the end.

hw 0,3 is determined from the  aplay -l command which lists my HDMI as device 0,3

Yours may be different.

---

### Post by VampiricPadraig on 2009-05-25
Hello, I'm new to Ubuntu. I got a magazine today which contained Ubuntu 9.04 and a guide to installion. I followed everything that was in the magazine, but I seem to have a problem with the sound. On startup (after putting in the username and password) that jingle/startup song always skips...As in a badly scratched CD in a CD player. It would skip constant that I either have to mute the volume via the top of the screen or by going to the Terminal and going "*killall pulseaudio*" and then it would stop but obviously with no sound. When I go to re-enable the sound ("*pulseaudio -vvv*") it would contine.. Is there anyway around this??

My Specs:
Toshiba Satellite Notebook
Ubuntu 9.04 (32-bit) Jaunty Jackalope
Intel Celeron M
ATI GFX Card (Don't know the model number) 
512MB RAM (I think, I know it only needs approx. 380MB RAM)

If you need anymore infomation, I will be more than happy to provide it.

VP

---

### Post by ashtone on 2009-05-25
Hi everyone, im having issues with sound, I have a Gigabyte mainboard GA-MA790FX-DQ6 with an integrated sound card Realtek ALC889a 

I cant hear sound correctly, when I play a mp3 file or a video file it seems to be ok, but instead the normal sound I hear like a noise, like sound going too fast or too slow

I ve donde several things, and have read (and followed) 3 posts in this forums (about sound issues), and other forums where people talk about solutions to sound problems, but no one worked for me, also I have checked combinations in sound configuration, I mean selecting OSS, Alsa, autodetect, pulse audio...

Someone could give some advice please ?

---

### Post by Flag on 2009-05-26
I'm running 9.04 fresh install, tried all tricks but to no avail. Skype is important for me, so not being able to use it makes this distro suck.
Having said this, I've the same problems with arch-2009, which uses kernel 2.29.x and alsa 0.20 by default.
The last one which worked flawless was 8.04.

---

### Post by karenk on 2009-05-27
Sxeptomaniac, Have you found any solution yet?  I too have an HP dv6z.
Thanks.



> **Sxeptomaniac said:**
> I've also been stuck on this one.  I've got an HP DV6z (an HD ATI SB), and every fix I've tried so far has had absolutely no effect.  I've tried editing /etc/modprobe.d/alsa-base.conf a couple of different ways, uninstalling ALSA and replacing it with OSS, upgrading ALSA to 1.0.20, and downgrading my Kubuntu install to 8.04.  

I haven't tried [the fix listed here yet]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870"), but that's next, when I have some time.  I haven't been stumped on a problem like this before.  Usually a quick couple of searches comes up with a fix, but this time there are people all over trying things that don't work for me.

I've been reduced to using Windows on my own equipment again.

---

### Post by charlesall on 2009-05-27
Hi

I have also had issues with sound. I am running 9.04 64bit on Intel MB DP45SG which has following sound specs:
Chipset: ICH10 - 82801JI
Codec:   IDT 92HD73E1X5

From clean Jaunty install - no sound at all!

Sound device recognized....

```

charles@linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

More info on hardware:

```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Intel Corporation Device 5001
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

Upgraded to ALSA 1.0.20 got sound working perfectly except for the mic and this driving me crazy.

The only way I do get the mic to capture, in a very round about way, is go to the gnome gui to /preferences/sound etc, - down to the capture drop down, select the hda ALSA capture device and click "test". Very far from ideal.

Any help would be appreciated but I fear as Markbutu said,

> There are some problems with the snd-hda-intel driver in the 2.6.28 kernel and updates are coming very soon to fix those issues so please be patient.

I will have to wait for the kernel updates.:)

---

### Post by Enter t'Ibex on 2009-05-27
I had sound everywhere but not in flash.  Firefox was suggesting this install, but for some reason jaunty hangs constantly running synaptic.  doing this in terminal fixed it for me.

sudo apt-get install gstreamer0.10.plugins.bad

now my kid can watch talking cats again (oh joy)

---

### Post by polauster on 2009-05-28
Can anybody tell me wich program should I use to masterize what I produce on Ardour, there's any program that able me to export and process audio Ardour projects??

---

### Post by jama999 on 2009-05-28
> **markbuntu said:**
> Do you have pcm capture selected?

markbuntu,

Great Guide - it has brought me a long way to understanding audio on Ubuntu.

Per this, I have a strange problem for you - I have been through this guide ad nauseum, pages and pages and I managed to get the following working:

1.  Default audio (non surround) works ONLY through HDMI - in the GUI sound preferences, the only option which yields the test tone is HDMI.  This is actually OK with me and I can live with it.  If I fire up any video file using totem-gstreamer, it works fine but only stereo and only through the HDMI.
2.  I can play surround sound (DD, DTS, etc.) through VLC ONLY - sounds beautiful - but VLC will NOT play regular 2 channel sources at all.  Anything I do in VLC except select spdif does not work.  When playing, VLC states that its putting out audio through "A/52 on Spdif"- so theres evidently some special sauce in VLC that dosent exist anywhere else.

This is through an HDA Intel chipset with integrated HDMI and spdif outputs and aplay-l and aplay-L both show the hardware recognized and working perfectly.

So what I would like to do but can't quite figure out how to do is either:
- Get VLC to *default* to the HDMI when the content is not decoded as surround, then I will just fire up VLC all the time and abandon totem-gstreamer
- Somehow get surround encoded information to default out the fiber port (I have been able to figure out no way to do this, though there is a "surround51" parameter which shows up in aplay-L which is clearly pointing to the Analog out.

Any ideas - direction in which to point me?

If you need me to run anything on the machine and post here, let me know - happy to do it.

cheers

J

---

### Post by markbuntu on 2009-05-28
> **jama999 said:**
> markbuntu,

Great Guide - it has brought me a long way to understanding audio on Ubuntu.

Per this, I have a strange problem for you - I have been through this guide ad nauseum, pages and pages and I managed to get the following working:

1.  Default audio (non surround) works ONLY through HDMI - in the GUI sound preferences, the only option which yields the test tone is HDMI.  This is actually OK with me and I can live with it.  If I fire up any video file using totem-gstreamer, it works fine but only stereo and only through the HDMI.
2.  I can play surround sound (DD, DTS, etc.) through VLC ONLY - sounds beautiful - but VLC will NOT play regular 2 channel sources at all.  Anything I do in VLC except select spdif does not work.  When playing, VLC states that its putting out audio through "A/52 on Spdif"- so theres evidently some special sauce in VLC that dosent exist anywhere else.

This is through an HDA Intel chipset with integrated HDMI and spdif outputs and aplay-l and aplay-L both show the hardware recognized and working perfectly.

So what I would like to do but can't quite figure out how to do is either:
- Get VLC to *default* to the HDMI when the content is not decoded as surround, then I will just fire up VLC all the time and abandon totem-gstreamer
- Somehow get surround encoded information to default out the fiber port (I have been able to figure out no way to do this, though there is a "surround51" parameter which shows up in aplay-L which is clearly pointing to the Analog out.

Any ideas - direction in which to point me?

If you need me to run anything on the machine and post here, let me know - happy to do it.

cheers

J

Are you using a nvidia driver?
I have seen a few scattered reports about HDMI and nvidia where installing the nvidia driver only allows HDMI and disables the on-board sound. It seems to happen with just a few cards and certain drivers. You might want to do a  search for HDMI nvidia in the forums here. I am sure someone has found a solution for that. I don't use nvidia myself so I can't really help you with that.

fyi, the gpu driver has a lot to do with the hdmi audio since hdmi audio passes through the gpu.

---

### Post by jama999 on 2009-05-28
> **markbuntu said:**
> Are you using a nvidia driver?
I have seen a few scattered reports about HDMI and nvidia where installing the nvidia driver only allows HDMI and disables the on-board sound. It seems to happen with just a few cards and certain drivers. You might want to do a  search for HDMI nvidia in the forums here. I am sure someone has found a solution for that. I don't use nvidia myself so I can't really help you with that.

fyi, the gpu driver has a lot to do with the hdmi audio since hdmi audio passes through the gpu.

Interesting - I am Intel GMA not nVidia, but I just also went through the "HOWTO: Jaunty Intel Graphics Performance Guide" on the stickies in this section to fix video flicker, etc.  so I will buy that - Intel drivers also fixed other HDMI issues.

---

### Post by jtomast on 2009-05-28
For Intel Soundcards laptop users:

In terminal type this code:

-------------------------------
sudo apt-get install alsa
-------------------------------

If you allready have ALSA, Skip
the step 1 and type:

-------------------------------
gedit /etc/modprob.d/alsa-base
-------------------------------

Copy and paste this line to alsa base

-----------------------------------
options snd-hda-intel model=mobile
-------------------------------------

Restart.
This helped me with Hp 6730s laptop Intel Core2 Duo.
It's still buggy, but sound's great.

---

### Post by victor.cighir on 2009-05-29
> **markbuntu said:**
> **Jaunty 9.04 Sound Solutions**


In System/Adminstration/Users and Groups check that your users and root are members of the following groups. (This is supposed to be taken care of by Policykit and hal but users have reported messages in their logs relating to lack of permission for pulse to gain rt priority so.....)
pulse
pulse-access
pulse-rt

Reboot 
mark

I've been tryin to make sound work with Asus M2N-e SLI and pulseaudio for 2 days... I even considered buying a new sound card.

My problem was that pulseaudio showed that it receives input from Rhythmbox or Gnome Mplayer but it did not output anything to my speakers. On the other hand TvTime worked and I could hear sound. 

No mic yet in skype, but I hope I will make that work as well!

---

### Post by Ariccanfly on 2009-05-29
Install ALSA? is that really the solution to get skype working again? smf custom open solaris(ie not getting increasingly laggy)

Pulse and skype worked in 8.04 and 8.10

---

### Post by Sxeptomaniac on 2009-05-29
OK.  I just had an odd breakthrough.  I found that if I connect my laptop to my monitor using an HDMI cable, I can get test sounds out of the monitor's built-in speakers using the Multimedia settings in System Settings.  Anyone have some ideas?

It's an HP DV6z laptop.  Info from the terminal is below:

~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2400000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2310000 irq 2298

---

### Post by redenex on 2009-05-30
> **jtomast said:**
> For Intel Soundcards laptop users:


If you allready have ALSA, Skip
the step 1 and type:

-------------------------------
gedit /etc/modprob.d/alsa-base
-------------------------------

Copy and paste this line to alsa base


But do we have modprobe.d in Jaunty?

---

### Post by hacker_at_linux on 2009-05-31
I think I found out the problem but I am unable to solve it
I am posting a screenshot of ALSA Mixer which has my Headphone volume to none. but when I try to increase it nothing happens it stays at 0. So I think this is the problem. But is any one can tell ho to resolve it?????
[IMG]http://www.newtrojansblog.com/S.png[/IMG]

---

### Post by redenex on 2009-05-31
For me sound works, but stops after some time, any clue what is happenning?

---

### Post by hacker_at_linux on 2009-05-31
Did any one have seen the same problem as i hav in my uppre post

---

### Post by redenex on 2009-05-31
Plays for 5 seconds before it dies!!!! well.

---

### Post by debiant on 2009-06-02
Thank you Markbuntu!

---

### Post by markbuntu on 2009-06-04
> **hacker_at_linux said:**
> I think I found out the problem but I am unable to solve it
I am posting a screenshot of ALSA Mixer which has my Headphone volume to none. but when I try to increase it nothing happens it stays at 0. So I think this is the problem. But is any one can tell ho to resolve it?????


There are lots of problems like this with laptops and the alsa driver. There is some help for that here:


[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by dakinibilyana on 2009-06-05
**ubuntu 9.04 sound problems HP compaq 6720s**

                                                                                                                      Hello all,
I installed ubuntu 9.04 recently and as much as i want to make it work, i'm still having problems with the sound on my laptop HP Compaq 6720s.
I managed to get Skype working but then at some the sound from internal speakers stopped and i could only listen to it through headphones. then i started twicking it, and i had a variety of problems with it - headphones worked, microphones stopped, both worked but with bad quality. sound worked through headphones for all programs but skype, etc.
i've read so many posts and forums and i tried so many solutions and configuration that i think i managed to make it even worse - no at times i can't get any sound at all, sometimes it stops in the middle of a skype call without me touching anything.
 i don't know what else to do.
there is some info about my system that i got with one of the commands:
[http://www.alsa-project.org/db/?f=9d46f040e06a0b1d875febe4cc1c1bf38cb08108](http://www.alsa-project.org/db/?f=9d46f040e06a0b1d875febe4cc1c1bf38cb08108)
 i will really appreciate any help as i really want to get ubuntu working nicely and i still haven't quite given up yet. :)
many thanks
dakini

---

### Post by PR_FM on 2009-06-06
Hi,
I have hp pavilion dv4 1070 & i've got sound problem (I don't have any :( ),but when i want log in there is some noise & it continues after 2 or 3 min after logged in but but it's going to lower noise till it stops, 
PLEASE HELP ME

---

### Post by logan85 on 2009-06-06
hi, i have ubuntu 9.04, for 2-3 months, and now appeared a problem, if i play music with amarok, and start vlc, there is no sound in vlc. if i log out and log in, and start vlc first, works fine. I tried to switch vlc sound output to alsa output, but is not working. the problem appeared this week. any suggestion? thanks anticipated.

---

### Post by hmjbarbosa on 2009-06-08
Hi All,

For those of you with sound working but no Mic, just though you'd like to know there is a possible solution. Follow this [guide]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/#comment-191")guide and switch from pulse to good old ALSA. I just did it and now sound recorder and skype work perfectly. 

BTW, My system is a desktop with i920 on a intel DX58S0 running a fresh install of Jaunty with Kernel is 2.6.28-11-server. The sound card info is below. 

Hope that it helps,
Henrique

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

$ cat /proc/asound/card0/codec#2 | grep Codec
Codec: Realtek ALC889

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0000000 irq 22

$ cat /proc/asound/pcm
00-00: ALC889 Analog : ALC889 Analog : playback 1 : capture 1
00-01: ALC889 Digital : ALC889 Digital : playback 1
00-02: ALC889 Analog : ALC889 Analog : capture 1

---

### Post by ratcheer on 2009-06-09
I am having partial sound problems.

If I select my sound card in Sound Preferences, the tests work. I can play DVD movies with sound in Totem but not in VLC. I get no sound in Flash videos (the videos do play). I can listen to Internet Radio and get sound.

If I set the preferences to Pulse Server, as suggested in this topic, I get no sound from anything. I have checked and verified that my username and root are in the three Pulse user groups.

I am on 9.04 and my device is an Audigy ZS. I have the latest Flash Player installed.

What to do, next?

Thanks,
Tim

---

### Post by cougs_83 on 2009-06-10
I was turned onto this thread in another post and followed the instructions my problem is that the pulse audio applet in not detecting my hardware audion device.  I am trying to run the audio through my HIS HD 4650 video card.  Everywhere else the audio device is detected and set up except for the pulse audio applet.  Does this post only refer to the onboard analog audio.  Is there a setting I should change?

---

### Post by markbuntu on 2009-06-10
> **PR_FM said:**
> Hi,
I have hp pavilion dv4 1070 & i've got sound problem (I don't have any :( ),but when i want log in there is some noise & it continues after 2 or 3 min after logged in but but it's going to lower noise till it stops, 
PLEASE HELP ME

There are some solutions for sound problems with the dv4 here. I am not sue if your particular model is listed but it is worth a try. Let me know what works for you or not...

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by ratcheer on 2009-06-10
> **ratcheer said:**
> I am having partial sound problems. ....



Thanks to psyke83's tutorial on Pulse Audio fixes, I am now in business. The problem was, indeed, the group permissions. I thought I had checked them, but I did not understand what I was seeing. Fixing them fixed everything.

Tim

---

### Post by chimericidol on 2009-06-13
I cannot launch padevchooser, it gives me this error:
[HTML]** (padevchooser:4376): WARNING **: pa_browser_new() failed.[/HTML]

And now I also have this very strange beep from the computer when I press backspace in terminal :(

---

### Post by stefpeter on 2009-06-14
Hello,

I have a SoundBlaster Live! 5.1 Running in stereo mode on kubuntu Jaunty Jackalope . This card has the emu10k1 chip on board. I have tried everything that was posted in this thread as well as many other things to get the plugins for firefox like flashplayer or gstreamer working, but none of that stuff is working. 
Neither pulseaudio nor raw alsa-devices are working with the firefox a plugins. I have sound with raw alsa using the SPDIF digital output jack of this card,  so I can play amarok or system-sounds, but thats it.  I'm coming from a Gentoo distribution, frustrated about all the configuration stuff, and hoped things will be easier using a binary distro, but I'm completely disappointed. PulsAudio seems to be in a beta state, also within 0.9.14 no SPDIF is working. Even with 0.9.14 no PCM output (analog-output) of my soundcard is working. Do anybody has probaly the same configuration? Is Ubuntu better supported than Kubuntu? Does it make sense to switch over?

Thanks in advance.

---

### Post by crjackson on 2009-06-15
> **stefpeter said:**
> Hello,

I have a SoundBlaster Live! 5.1 Running in stereo mode on kubuntu Jaunty Jackalope . This card has the emu10k1 chip on board. I have tried everything that was posted in this thread as well as many other things to get the plugins for firefox like flashplayer or gstreamer working, but none of that stuff is working. 
Neither pulseaudio nor raw alsa-devices are working with the firefox a plugins. I have sound with raw alsa using the SPDIF digital output jack of this card,  so I can play amarok or system-sounds, but thats it.  I'm coming from a Gentoo distribution, frustrated about all the configuration stuff, and hoped things will be easier using a binary distro, but I'm completely disappointed. PulsAudio seems to be in a beta state, also within 0.9.14 no SPDIF is working. Even with 0.9.14 no PCM output (analog-output) of my soundcard is working. Do anybody has probaly the same configuration? Is Ubuntu better supported than Kubuntu? Does it make sense to switch over?

Thanks in advance.

I'm afraid I can't offer much help, but I will say this. I too have the SoundBlaster Live! 5.1 in my system and it works out of the box. It could be a different revision I suppose.

---

### Post by Sxeptomaniac on 2009-06-15
I was testing out combinations of answers, and stumbled on to a partial solution for my HP DV6z.  Speakers now work, but the headphones still don't, and the slider for them has disappeared.  Anyone have an idea how to fix that?

Below is what I did:

I added the following line to the end of /etc/modprobe.d/alsa-base.conf:

> options snd-hda-intel model=hp-m4 enable_msi=1

I then upgraded ALSA to the newest version, 1.0.20, using the automated script at:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

After a restart, I checked my mixer panel, and there was a new slider labelled "Speaker."  It seems to have replaced my headphones slider (which did not work before anyway).  It started out all the way down, but sliding it up got sound out of my speakers.

---

### Post by nineowls on 2009-06-18
i am so tired of these sound issues...my Thinkpad A31 sound goes away last two updates. 
just started going through this thread doing whatever anyone else had tried
this apparently worked

try 
[B]       sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
       sudo apt-get install linux-sound-base alsa-base alsa-utils
       sudo apt-get install gdm ubuntu-desktop[/B]
then
[B]       sudo apt-get install gnome-alsamixer
       gnome-alsamixer[/B]
look at all the settings
play with the settings
maybe you'll find something that will work for you? (I did)

---

### Post by johnaaronrose on 2009-06-18
When I try "sudo apt-get install --reinstall pulseaudio-module-hal ":
Reinstallation of pulseaudio-module-hal is not possible, it cannot be downloaded

Help please!

---

### Post by matashi on 2009-06-19
This worked out well. Thanks for the post.

:D

---

### Post by Th3_uN1Qu3 on 2009-06-21
Really nice guide, and it works... Mostly.

I have a HP DV5 laptop, and previously configured sound to work with ALSA, everything was fine and dandy except that i couldn't have sound in multiple apps at once. So i followed your guide and installed pulseaudio. For some reasons it removed Wine, i reinstalled it. I checked the boxes for pulse, pulse-access and pulse-rt in Users and Groups. Here are my issues:

The PulseAudio volume control crashes exactly like described here: [http://ubuntuforums.org/showpost.php?p=7108833&postcount=7](http://ubuntuforums.org/showpost.php?p=7108833&postcount=7)

Recording does not work (crashes when i try to record).

When playing music and opening a site with Flash content at the same time, sound starts to crackle and pop. I know flash is a CPU hog, but we're talking about a dual core here. There must be something to make it run with lower priority and not mess up my sounds anymore.

Also, sound in Wine is all crackly, and VirtualBox doesn't seem to work with PulseAudio. I want to run FL Studio, either via Wine or VirtualBox XP. Before installing PulseAudio, FL Studio used to work very well in VirtualBox with the OSS driver selected, but it would lock out all other sound sources. Now selecting OSS in VirtualBox does not work at all (says device cannot be accessed or something like that), and with PulseAudio i just get no sound.

Edit: Ticking "Driver Emulation" in Wine's audio options enabled FL Studio to run with a half-decent latency. I still need to fix the Flash issues though.

---

### Post by markbuntu on 2009-06-21
Crackly sound can usually be fixed by turning up the PCM volume in the alsa sound mixer. You should start wine with padsp wine and set it to use oss. I am not sure about virtual box, I have not played with it too much but maybe try setting it to use alsa.

---

### Post by Th3_uN1Qu3 on 2009-06-21
The volume was all the way up. I ran PulseAudio -vvv in the terminal and it was reporting lots and lots of underruns. I have removed PulseAudio, then removed and reinstalled ALSA, which configured with Dmix by itself. So now i have working software mixing AND no more underruns. I can open as many Youtube vids as i like. :D

Previously FL Studio would crash VirtualBox if i tried to use ALSA, now it works, and it has fairly good performance.

It seems PulseAudio has still a long long way to go till becoming useful.

---

### Post by davidmigl on 2009-06-24
The OP's post resolved my issue. Jaunty 64 Soundblaster Live! 5.1. Many thanks!

---

### Post by ForgivenByJC on 2009-06-24
This guide is good with the following caveat.

If you are having issues with no flash player streams (Pandora.com) within pavucontrol--
The problem may be that you are running amd64 architecture and flash (Ubuntu Repo's) are all 32-bit.
I did this with only needing to reboot...
[http://simos.info/blog/archives/804](http://simos.info/blog/archives/804) (check: flashplugin-nonfree has become flashplugin-installer, so uninstall both and possibly nspluginwrapper if you don't need it anymore)

I now have it streaming through Pulse Audio (server or whatever it is referred to as).  I am quite certain I also did this on my amd64 architecture with the 32-bit package from Adobe before I had to rebuild my computer for an unrelated issue.
Good luck!

---

### Post by dld on 2009-06-29
There are 3 or 4 threads like this one that promise to get audio working
under Ubuntu 9.04.  I tried several, with mixed results.  Now I try this
one, and am stopped at the same place where I encountered a problem before.
When running PulseAudio DeviceChooser, an entry appears on the task 
bar saying "starting ...", holds there for a short time and then is
removed.  No new icon appears where I can find it.  I tried running
padevchooser from the command line.  Nothing happens! any ideas or
suggestions?

My read problem is not addressed by threads like this one.  I can get
more or less playback (less at the moment:  frozen bubble is without
sound).  But I have never been able to capture sound when running
Linux.  Dell XPS410 with Intel HDA and STAC 9227 codec.  So I am
forced to reboot to XP more often than I like, and can't run one
application on this machine under Linux that I really would like 
to run.   Again,  ideas, facts, suggestions??

---

### Post by Elgin on 2009-06-29
Hello

I recently did a clean install of Jaunty 9.04 (was using Intrepid) and now I have no audio. Pulseaudio volume meter and control both show strong audio levels, but there is not a sound. 

However, alsamixer -Dhw shows the levels there (in the little box at the bottom of the window) at 00. I am unable to change that because there are no controls in the alsamixer window, nor do any appear in Gnome alsamixer.

Also, when I click on Pulseaudio device chooser it does not load, all it does is install an extra icon beside the other in the top panel.        
                       [LEFT][SIZE=1][SIZE=2]I[/SIZE][SIZE=2] have added user to pulse, pulse-access and pulse-rt.[/SIZE][/SIZE][SIZE=1]

[/SIZE]   [SIZE=1]Can you help me correct the problem?

[/SIZE]   [SIZE=1]Thanks for your attention.


[/SIZE]  
[SIZE=1]Below are the results of aplay -l and lspci -v[/SIZE]

[/LEFT]
                                  [SIZE=1]**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0[/SIZE]
[SIZE=1]Ispci-v[/SIZE]

                                  [size=1]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64
Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fdd00000-fddfffff
Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
I/O ports at ff00 [size=8]
I/O ports at fe00 [size=4]
I/O ports at fd00 [size=8]
I/O ports at fc00 [size=4]
I/O ports at fb00 [size=16]
Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
Expansion ROM at fdf80000 [disabled] [size=512K]
Capabilities: <access denied>
Kernel driver in use: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: 66MHz, medium devsel
I/O ports at 0b00 [size=16]
Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: piix4_smbus
Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at f900 [size=16]
Capabilities: <access denied>
Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: fdc00000-fdcfffff
Prefetchable memory behind bridge: fde00000-fdefffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Flags: fast devsel
Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
Flags: fast devsel
Kernel driver in use: k8temp
Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
Subsystem: ASUSTeK Computer Inc. Device 0296
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at d0000000 (64-bit, prefetchable) [size=256M]
Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at ee00 [size=256]
Expansion ROM at fddc0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: fglrx_pci
Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
Subsystem: ASUSTeK Computer Inc. Device aa28
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, medium devsel, latency 64, IRQ 21
I/O ports at dc00 [size=256]
Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: 8139too
Kernel modules: 8139too, 8139cp

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
Subsystem: Hewlett-Packard Company Device 2a26
Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
Memory at fdcfe000 (32-bit, non-prefetchable) [size=2K]
I/O ports at df00 [SIZE=128]
[SIZE=1]Capabilities: <access denied>
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394







[/SIZE]        
[/SIZE] 
 [LEFT][SIZE=1]

[/SIZE] [/LEFT]
 
[SIZE=1]
[/SIZE] 
 [LEFT][SIZE=1]
[/SIZE][/LEFT]
 [LEFT][SIZE=1]
[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]
[/SIZE][/LEFT]

---

### Post by rajintha131 on 2009-07-07
t

---

### Post by rajintha131 on 2009-07-07
Thank you and may God bless you

---

### Post by akqj10 on 2009-07-11
Many of us have tried to solve the sound problem in 9.04.  I myself have tried dozens of configurations and nothing has worked until today.   All you have to do is go into your BIOS and turn off the motherboard sound, reboot into Ubuntu and voila, sound is working.   I opened Firefox and went to CNN and CNET and played videos and the sound works!

---

### Post by rtalcott on 2009-07-11
FWIW....nothing worked until I tried 9.10 Alpha2...then...everything worked.
rt

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by PR_FM on 2009-07-29
Hi Guys, I Still Have problem
I have ubuntu 9.04 on my laptop ( HP DV4 1070 ) & I have this problem : when a sound finished (either music, logging in sound, ...) it hanged & repeated forever till I start to play a sound again,
I used some solution like add something in the alsa base file ( I don't remember ) but I still have the same problem ,
please help me.

---

### Post by mattlach on 2009-07-29
Thank you.

This solved my nagging sound issues.  (Though I still don't understand why my ALC888 only seems to work when set to OSS, and not when set to ALSA...)

---

### Post by KingNeil on 2009-07-29
This is a very good thread. The thing about Dell laptops having low microphone volume is very true. If you install padevchooser, turn up the volume to about 150% or so, and recording works flawlessly.

In order to make sure your applications take this into account, choose Pulse whenever you have an option for sound. For example, in Skype, go to Options > Sound Devices, and choose Pulse for all three options.

Here's another tip for recording. Using Audacity, you can use the "Noise Removal" tool to get rid of background noise. Highlight some empty space, with only the background noise, select Effects > Noise Removal, click "Get profile", then select the whole recording, select Effects > Noise Removal again, and click OK.

Also, you can increase the volume of your recording in Audacity by selecting your recording and using Effects > Amplify.

---

### Post by trinacriax on 2009-07-30
Hi to all,
I've a strange problem...
I heard audio from both headphone and internal speaker of my desktop.
why??
I've Ubuntu 9.04 on 64-bit pc (amd64).
I searched in the forum, but I didn't find any thread close to my problem.
Any idea??

thx

---

### Post by mattlach on 2009-07-30
> **trinacriax said:**
> Hi to all,
I've a strange problem...
I heard audio from both headphone and internal speaker of my desktop.
why??
I've Ubuntu 9.04 on 64-bit pc (amd64).
I searched in the forum, but I didn't find any thread close to my problem.
Any idea??

thx

Does [this](http://ubuntuforums.org/showthread.php?t=806620) help?

Personally I'm not bothering to install this tweak, because I always turn my speakers off when I'm not using them, and unplug my headphones when I'm not using them.

---

### Post by HarryBhat on 2009-07-31
Hey guys! Could someone please help me with this?
> 
[http://ubuntuforums.org/showthread.php?t=1226899](http://ubuntuforums.org/showthread.php?t=1226899)

P.S.: Sorry about making a different thread, but I saw this thread after I had already created that.

---

### Post by elenssar on 2009-07-31
hello,
i am trying to setup a system with 2 sundcards. I have successfully setup ubuntu (i think) and i have sound from both of them. The only think i cant do is that wine does not recognize them. I find this link [http://ubuntuforums.org/archive/index.php/t-895009.html](http://ubuntuforums.org/archive/index.php/t-895009.html) but since i am new to linux i dont understand what i have to do. above step3 he says that i need to change some bold letters with my soundcard but there are no bold letters. 
my aplay -l output is this ```
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
can some one help

---

### Post by trinacriax on 2009-07-31
> **mattlach said:**
> Does [this](http://ubuntuforums.org/showthread.php?t=806620) help?

Personally I'm not bothering to install this tweak, because I always turn my speakers off when I'm not using them, and unplug my headphones when I'm not using them.

Hi have tried to add

```

options snd-hda-intel probe_mask=1

```

in /etc/modprobe.d/alsa-base.conf
rebooted my pc BUT I still hear sound from both headphone and itnernal speacker of my pc. Why???????
I've also disabled "Speaker" in Volume Control.
Please let me give you more information about my card:

```

$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

$ head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC1200

```
any idea??
I have already searched in the forum but without success.

---

### Post by babygenius55 on 2009-08-01
I love you guys to death. finally able to record. Great, now to get started with some freestuff.

---

### Post by trinacriax on 2009-08-03
> **trinacriax said:**
> Hi have tried to add

```

options snd-hda-intel probe_mask=1

```

in /etc/modprobe.d/alsa-base.conf
rebooted my pc BUT I still hear sound from both headphone and itnernal speacker of my pc. Why???????
I've also disabled "Speaker" in Volume Control.
Please let me give you more information about my card:

```

$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

$ head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC1200

```
any idea??
I have already searched in the forum but without success.

I have solved my problem simply disabling the internal speaker in the BIOS.
thx

---

### Post by Wlo on 2009-08-04
Hiya.  I wonder if someone can help me?  I'm running Jaunty 64bit with an Edirol UA25 external soundcard.  I can get sound to play in some apps (Banshee, Totem) when I point the settings in System>Pregerences>Sound to OSS, but then sound doesn't work in other apps (VLC, Flash).  I tried using PulseAudio and followed the guide at the start of this thread to the letter, and have tried various other guides, but with PulseAudio selected I get no sound from anything.  If I set it to ALSA and try and run the test the sound applet crashes.

Other telling sign perhaps is that if I try and access sound card properties in gnome-alsa-mixer it crashed with:

(gnome-alsamixer:8734): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

Any ideas?

Thanks.

Wlo.

---

### Post by Wlo on 2009-08-05
Known bug, this workaround worked for me:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/366708](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/366708)

Wlo.

---

### Post by bayesianlogic on 2009-08-07
Anyone know how, after following instructions above, to get stereo working again?  I see only a "Mono" option for "Playback" in the padevchooser Volume Control window.:confused:

---

### Post by mlnease on 2009-08-14
Mark,

WOW.  I've been a devoted Ubuntu user since Dapper was new and have always found sound configuration challenging.  This is the best tutorial I can recall seeing (on any subject) in these years of troubleshooting.  Thanks a million.

mike

---

### Post by ChrisMoss on 2009-08-18
I'm still having trouble with my Dell Inspiron 1735 laptop. I followed the guide in the sound solutions and got:

For  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and for  lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
    Subsystem: Dell Device 0256
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f6dfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

but I can't find anything in the alsa database correspobnding to STACK92xx Analog or Intel HDMI or even ICH8.

The sound system works perfectly well under Windows Vista so what am I missing? I'm running Jaunty.

Chris

---

### Post by Cavsfan on 2009-08-21
Thank you so much Mark!!! 
I finally was able to record sounds coming from my speaker! I had been trying to do this for days and thanks to you I can now do this.
Rock On! :guitar:

I have been wanting to make a youtube video and show off how cool Ubuntu is to my family and I am a whole lot closer to that goal.
I recorded the sound in ogg format and the video is in ogv format and if I can find a way to edit them and merge them I will be there (where I want to be :))

Thanks for making this great tutorial!

---

### Post by kemedo on 2009-08-28
thanks a lot mark, this problem was driving me crazy.
I was for several days searching everywhere, and didn't found anything, until i arrived to your HOW TO.
Now my Logitech Speaker plays well in java apps, but now i have another problem, VERY choppy sound, and if for example im using a lot the scrollbar in Opera, the sound just stops until i finished to move the scrollbar, any idea?
i hope someone has a clue.
thanks once more!

---

### Post by harveygfl on 2009-08-29
FYI...  The Sound header on the System board  was shorted out.
I figured this out by loading different operating systems (Current versions of Fedora, Suse, OpenSolaris and Windows) when none of them recoognised the onboard sound, i new it was hardware related.  I RMA'd the system board and got a new one. I connected everything (At the Time i was playing with Windows 7, and It Worked!    BTW...  from my experiences Ubuntu is the only Linux distro that supported my hardware straight out of the box.

if you like i can post the settings that are being used (All Defaults from Juanty X64) 
Also,  from my experience, make sure you don't connect a AC97 internal Cable on the Intel HDA header,  It may have caused the short but I am not sure.

---

### Post by awe on 2009-08-30
> **markbuntu said:**
> In System/Adminstration/Users and Groups check that your users and root are members of the following groups. (This is supposed to be taken care of by Policykit and hal but users have reported messages in their logs relating to lack of permission for pulse to gain rt priority so.....)
pulse
pulse-access
pulse-rt
I definetely should do that, but how do I give an additional group to users that are on al LDAP tree?

---

### Post by LinuxBob on 2009-08-30
> **nineowls said:**
> i am so tired of these sound issues...my Thinkpad A31 sound goes away last two updates. 
just started going through this thread doing whatever anyone else had tried
this apparently worked

try 
[B]       sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
       sudo apt-get install linux-sound-base alsa-base alsa-utils
       sudo apt-get install gdm ubuntu-desktop[/B]
then
[B]       sudo apt-get install gnome-alsamixer
       gnome-alsamixer[/B]
look at all the settings
play with the settings
maybe you'll find something that will work for you? (I did)

NOt hardly

$ gnome-alsamixer

(gnome-alsamixer:8481): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault


Not much help obviously

---

### Post by LinuxBob on 2009-08-30
Insult to injury

now not even local files play any more, not rythmbox or anything

---

### Post by LinuxBob on 2009-08-30
> **LinuxBob said:**
> Insult to injury

now not even local files play any more, not rythmbox or anything

Got sound for local files and rythmbox back after reboot.  Still no pandora or youttube sound from firefox

---

### Post by xycris on 2009-08-31
Don't mind this, I followed the steps on this thread thus uninstalling the default sound driver and controller in Jaunty Jackalope. It took sometime for me to really figure it out in PulseAudio, then, when I unlocked the "Lock channels together" and adjusted the "Front Left" slider to 0%, the sound then included the voice!

I really didn't know why this was not available in the default of Jaunty but I am glad this tutorial exists. Thank you very much!

Hi, I have upgraded to Jaunty Jackalope and now I have problems with the front panel audio output connection. The sound is having no voice at all just instruments. I guess this is because the surround sound setting is enabled.

How can I make the front panel for earphones or headphones?

Thank you in advance I highly appreciate any help.

---

### Post by gognos on 2009-09-02
Hi guys i was wondering if maybe someone could possibly help.

Firstly im new to linux so lamo terms if possible :) 

 im using a m2n-mx motherboard amdx2 

logitech 5.1

Moving from winxp pro where 5.1 surround sound worked flawlessly 

front speakers and sub woofer worked out of the box on ubuntu 9.04 

however the center and 2 rear fail to work no matter what i try 

tried 
sudo gedit /etc/pulse/daemon.conf

Uncommented and changed this
;default-sample-channels=2

to 

default-sample-channels=6 

Reboot

no change


i went to the asus website and they had the old alsa .11 drivers/libs/tools/utilities found for my motherboard

installed still center and rear speakers fail 

came here followed purge apt-get instructions to update alsa drivers 

installed

reboot

no change still no center rear speakers working

went into HDA Nvida alsa mixer changed to 6 channels 

tried everything in that mixer 

still no rear center speakers working 


did a sound test earlier, forgot how where it plays a chime through every speaker to test if they worked they did however playing music or dvd's it doesn't 

i am  at a loss 

installed alsa mixer gui still no help

installed gnome alsa mixer still the same and couldn't work out how to change channel mode to 6 with that mixer anyway.

flash sound works i have every codec needed all files play i just cant get surround sound to work.

Is there a fix to my solution? 

Thanks in advance all help greatly appreciated

---

### Post by gognos on 2009-09-04
after a clean install and changing this first 

default-sample-channels=6  

i am now able to get the center speaker working  yet still no REAR speakers.despite tuts all over the net stating this will improve the situation. so now i have a 3.1 instead of 5.1 sound system,which is ok but far from perfect. Is this a problem in all flavours of linux or only ubuntuZ??

Is this thread now dead?? Can no one help ? Is there no chance of getting all speakers to work with ubuntu 9.04 .

Everything mentioned has been done, what a waste of time it was since it hasnt corrected my problem. its 2009 ALL speakers should simply plug in and work. Windows can do why cant linux/ubuntu?  You would think at the very least default-sample-channels=2 would be set to 6 when you install, since it stll gave me sound to my 2 speaker system on that setting. instead thousands of people  spend how many hours searching the net just to get something so  basic to work. Then still doesnt, with the addition of limited help from people directing you to the same old info that you try and  doesnt work or change anything. 

So is there anyone that can tell me if i can get 2 front 2 rear sub and center speakers working with ubuntu 9.04 or any flavour of linux.Or am i simply waisting more time trying?

---

### Post by TheGreenStump on 2009-09-05
MarkBuntu! Thank you so much for your post! I've been having a nightmare trying to fix Flash audio. I just installed Ubuntu, and I'm new to most Linux stuff.

Everyone keeps referring to /etc/firefox/firefoxrc, but that's nonexistent for me.

I really appreciate your help! I'm one step closer to getting my system the way I want it.

Thanks again!

-The Green Stump-

---

### Post by Qassis on 2009-09-06
Sound wouldn't work on a W4620 emachine with an
ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02).

The situation and fix (not my own):

Running Ubuntu 9.04 desktop (Jaunty Jackalope) on a
eMachine W4620 laptop (made by gateway) with:
ATI IXP SB400 AC'97 Audio Controller (rev 02)
Subsystem: Gateway 2000 Device 0301

From lspci -v
Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Gateway 2000 Device 0301
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at d0503400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

**To fix my sound had to:**
edit blacklist file (like this):
         sudo gedit /etc/modprobe.d/blacklist

Then added the following line to the bottom:
         blacklist snd-atiixp-modem

Then I had to reboot - and "I had sound!".
Don't forget the reboot.

I found this solution in an archive on ubuntuforums.org for another version, 
but it worked!  This forum has helped me get my wireless card and sound going - thanks!

---

### Post by ken78724 on 2009-09-06
pardon the dual post [re post 7908967] but perhaps this forewarns those like me who ignore forewarnings when they dump ALSA for OSS4. I presumed that essencialy involved a quick remove and replace but that is not so. The following test report reveal my situation: 

take note of this response in terminal
k78724@Kproductions:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
k78724@Kproductions:~$ OSSR4mixer
bash: OSSR4mixer: command not found
k78724@Kproductions:~$ 

Why did I try OSSR4mixer? Because I followed advice in another thread recommending the latest in 9.04 jaunty 64 bit sound ... Question is: has anyone else gone this route and how did you solve it? [you go to open source when one chooses the OSS4 option; alsa sound is removed or held in abeyance] 

Before going this route I did not have audio or mic in skype; but now I have no sound as well. It is feasible I didn't conclude the build around recommended. but, I'm challenged by this and now am chumping at the bit. 

Any recovery help will be appreciated.

---

### Post by ken78724 on 2009-09-07
Though I must fine tune Ubuntu Studio which I installed as noted in post 1258885, another thread. But so far I have no sound. 

Yes I removed ALSA and made an incomplete OSS4 install. this has forced a lot of study, all to no avail so far. 

Kindly point me to a solution.

---

### Post by ken78724 on 2009-09-08
though system>sound>test chirps on four tests, nothing kicks sound when I do a YouTube or other content. Meanwhile for those who willing to go into the unknown, here's the route to suffering with OSS4,,,, to have benefit of OSS4 sound & open source performance aka &#8220;oss-linux-4.1-1052_amd64.deb&#8221; click on: 
[http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb](http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb)

be forewarned, in three/four days I've been in the woods and can't get home... :confused:

---

### Post by ken78724 on 2009-09-09
your help accepted to light up sound when tests show sys, preferences and settings are allegedly a okay

And, TheGreenStump where do you input "/etc/firefox/firefoxrc" ?

---

### Post by JOshea on 2009-09-14
I know this thread came out awhile ago but for AMD64 users with jaunty

one very important thing that is not covered here is using 
audacity to record whats coming through the speakers ie 
how to record songs playing on the web or wherever if you are using amd64 
jaunty - including flash files that are encoded ...

I switched everything to pulse audio from preferences on the main menu 
the "sound" selection on the main menu - sound preferences - except the main mixer - leave as is ...then 

use the pulse audio device chooser - go under the volume control 
and fire up audacity ...go under preferences there and choose pulse for audacity under both playback and record 

under the device chooser/ volume control -  go to recording tab - 
and hit record on audacity ...my card does not have a mix setting - but you can move the stream to the simultaneous from both playback and record tabs setting - and then you will see Audacity recording whats playing 

this took me way too long to figure out and you don't have to do any fancy work arounds or scripts to get it to work - I followed the link for jaunty but did not get rid of flash by adding the extra 32bit plugs to replace them but the others don't hurt to have - jack audio is not necessary and you can still save and load the wav files into something like Ardour 

cheers

---

### Post by eltucaso on 2009-09-15
Hi all,

   I didn't read the 22 pages of replies to this thread, but thought it worth mentioning;

 I have a Creatvie Labs Audiology sound card with surround sound; On a clean install of 9.04 I followed all the directions and still had NO sound.  I went into Alsamixer and had to un-mute the volume for the audiology bar.  Once that was done; presto chango sound all better, at least for 2 speakers.  To get the surround sound working I had to go into the daemon.conf file and do some changing.  To do this  hit alt+F2 and type gksudo nautilus, then go to /etc/pulse, copy and paste daemon.conf, then enter daemon.conf, change the last line to look like this: default-sample-channels = 6  (making sure to un-comment it) ...and now thanks to the original poster I have some nice software to use with it.  Thanks.

---

### Post by Axess_Denied on 2009-09-18
Markbuntu, I have read your guide and have seen some of the things you have suggested in other posts regarding HDMI audio playback and 9.04. 

Here is output for my system:

```
jim@Furthur:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
[COLOR="Red"]card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]
card 2: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I would like my audio output to solely come from the HDMI out (hdw1,3 I believe). Right now in System > Preferences > Sound I have selected "HDA ATI HDMI ATI HDMI (ALSA)" for each output option.

Problems I run into:
1. No audio from system sounds - login screen, window actions, etc.
2. No audio from flash player (using Adobe Flash 10 plugin in Mozilla and no audio in stand-alone)
3. No audio from Youtube
4. No audio from VLC (even when selescting ALSA mixer for audio source)


Curious if anyone may be able to help. Thanks

---

### Post by markbuntu on 2009-09-18
Try adding this line to etc/pulse/default.pa

load-module module-alsa-sink device=hw1:3

There may be more to this, it has been a while since i messed around with this so I may be missing something.

If you get pulse 0.9.15 from here, it has easily selectable options for HDMI output in the new volume control. It will be included in Koala.

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

### Post by Struki on 2009-09-18
Ok so I've got some sound issues. My hardware specs are in my sig, but here is my problem. I' ve activated sound on my first Jaunty install by adding the line:

*options snd-hda-intel model=laptop *

at the and of the alsa.base.conf file. It worked, but every now and the when I get a random sound (eg. pidgin sound incoming msg alert ) i hear this loud cracking noise instead of the apropriate sound. I've tried fixing this the by adding:

[I]alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel[/I]

also in the alsa-base file

Then I tried to install EVE online with wine and I did it, but everytime I tried to use in-game voice chat, the whole system crashes (I'll post my eve problem on the different forum I'm just stating this here as a point of reference). I've tried to fix that by following the "how to" guide from this link: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)  
As I can see now is the same thing as the guide at the begining of this thread. The result was, I did get the correct sounds, but every time I reboot at startup the PCM volume control would automaticly be set to 0 and mute. So baiscly every time I start ubuntu I have to manualy turn the sounds on.

So is there a way to set the pulseaudio and to set it so that its automaticly turned on. Or how can I fix the alsa-base file so that I stop getting the cracking noise.

Also I know this is not the subject but if some1 knows how can I fix my EVE online issue or point me in the right direction I would be greatfull. 

Thanks guys!

---

### Post by Axess_Denied on 2009-09-19
Markbuntu, thanks for the advice - 

That said, downloading PulseAudio is a not working out right now. I am told that my system does not satisfy the dependencies. Where can I find which dependencies I need to utilize PulseAudio?

Here is what I see in my /etc/pulse/default.pa file - 

```


### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

```

Am I to modify the existing

```


#load-module module-alsa-sink

```

Or am I to create a new line in this that includes > device=hw1:3

---

### Post by TheStroj on 2009-09-20
Thank you soooooo muuuuuch for all your instructions on how to make microphone working. I made it work in 15 minutes and before that i spent 2 weeks to make it work but nothing helped!

Thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by FirstByté on 2009-10-01
Pardon me if this aint the appropriate thread to ask this...

I've surfed a while now hoping to solve the issue of **muting my laptop speakers when a jack plug is plugged** in to my **Dell Studio 14's** audio jack.

While I've never had Sound issues; not even on Intrepid nor on this Jaunty, on Jaunty sound comes out of both my headphone and laptop speakers which gets me switching to Windows to use my SIP calls.

info:
> 
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3. 

~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Silicon Image SiI1392 HDMI



---

### Post by markbuntu on 2009-10-01
> **FirstByté said:**
> Pardon me if this aint the appropriate thread to ask this...

I've surfed a while now hoping to solve the issue of **muting my laptop speakers when a jack plug is plugged** in to my **Dell Studio 14's** audio jack.

While I've never had Sound issues; not even on Intrepid nor on this Jaunty, on Jaunty sound comes out of both my headphone and laptop speakers which gets me switching to Windows to use my SIP calls.

info:

This sort of problem is very hardware specific so you can look here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Your machine may not be listed but you can try the solutions for similar machines

---

### Post by FirstByté on 2009-10-01
> **markbuntu said:**
> This sort of problem is very hardware specific so you can look here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Your machine may not be listed but you can try the solutions for similar machines

Sorry If I sound like a jerk! I've read through that thread before coming here. Nice to note, my **/etc/modprobe.d/alsa-base.conf** already has 
> # Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell-m6
Appended to it.

I tried playing around with a couple 'model=dell-xxx' but no go. Like I said I don't have any problem with getting sound at all. I listen to music right from day one, and I do that at any volume :D

The problem is getting to mute the Laptop speakers with a jack plug.

While I post this, I'll keep trying other configs.



BTW:

I get this warning/errors when I try
```

~$ killall alsaaudio
~$ sudo alsa force-reload
~$ pulseaudio -D

```

> 
~$ sudo alsa force-reload
[COLOR="Red"]**lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon** file system /home/john/.gvfs
      Output information may be incomplete.
Terminating processes: **30925 30932 31175lsof**: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
**lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon** file system /home/john/.gvfs
      Output information may be incomplete.
.
**lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon** file system /home/john/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-allocUsage: /sbin/modprobe [-v] [-V] [-C config-file] [-d <dirname> ] [-n] [-i] [-q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
/sbin/modprobe -r [-n] [-i] [-v] <modulename> ...
/sbin/modprobe -l -t <dirname> [ -a <modulename> ...]
**WARNING: Error running install command for snd**
.
[/COLOR]
~$ pulseaudio -D
[COLOR="Red"]
**E: main.c: Daemon startup failed.**
[/COLOR]
~$ 

Am I doing something wrong somewhere? :confused:


Thanks in advance

---

### Post by Thorndog on 2009-10-12
OK, I have 9.04 amd64 installed with intel mother. My problem is I cannot seem to get the mic working on Dell SP2208WFP. The webcam is also sporadic and requires several removes and reinstalls to get it going on every boot, topic for different forum. The mic...
I tried the sound preferences and it sees the "Mic-Omnivision Technologies, Inc.538-2640-07.08.09.6 Monitor Webcam (SP2208WFP)" with two options; OSS control device or USB Audio ALSA. On select and then test, the OSS option tests but it doesn't seem to give output from mic and the ALSA option barfs out the following "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource."
A test call on Skype doesn't pick up sound for either choice.
possibly relevant bits from dmesg:

[   15.369060] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)                                                                           
[   15.369425] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   15.369668] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   15.369670] uvcvideo: Failed to initialize the device (-5).                  
[   15.369726] usbcore: registered new interface driver uvcvideo                
[   15.369729] USB Video Class driver (v0.1.0)   

Only video related I think or perhaps:
[ 6472.831774] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
might have some (I doubt) bearing.
I don't see anything in dmesg re mic and don't want to post the whole lot
The fact that the system is obviously seeing the mic since it is listed in the audio conferencing options list makes me think that this can be fixed but it is way beyond my limited capabilities.
I don't see anything in dmesg that looks like it relates to the mic and don't want to post the whole massive spew of it.
 Any help would be appreciated.

---

### Post by harrykar on 2009-10-12
Ok i have not read all that posts(only the first) and if duplicate another one i apologise.
Here's the hint to resolve(Sound recorder mishaps) for whom has had the outputs below:
```


$ lspci
...
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
...

$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcfff0000 irq 23

$ cat /proc/asound/modules
 0 snd_hda_intel

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```all that output it is syntheses in : I have a on board *High Definition Audio NVIDIA chip* that's a *nVidia Corporation MCP55 High Definition Audio (rev a2)* on irq 23. It has a analog output at hw0,0  and a digital output at hw0,1. Instead has only an analog input at hw0,2. MCP55 use the *snd_hda_intel* module.(tnx markbuntu)

more precisely mishaps here regard "Volume Control" (left clik on volume applet in up panel-> *Volume Control*) after a new Ubuntu install you must enable (clik on "preferences" button) in function of your sound card or onboard sound chip (in my specific case see below in your case if you don't know what you are doing possibly enable all mic fields and after clik the unmute button) 

front mic
front mic boost
and (**the most important**) the 2 inputs
(see screenshots)

Then goin on to *Options* tab and select your mic position (in my case i set *front mic* )
Now run *sound recorder* and you must certainly record with your mic

Hope this help :)

PS:
1 Certainly that's not the right way to go for the average user. That setting would have had to be automatic. In spite of the hint above i'm sure that most users will have difficulty to resolve 
2 Master, PCM, Front, Linein was just automatically enabled in my case (Im in Ubuntu Jaunty AMD64)

---

### Post by markbuntu on 2009-10-12
> **FirstByté said:**
> Sorry If I sound like a jerk! I've read through that thread before coming here. Nice to note, my **/etc/modprobe.d/alsa-base.conf** already has 

Appended to it.

I tried playing around with a couple 'model=dell-xxx' but no go. Like I said I don't have any problem with getting sound at all. I listen to music right from day one, and I do that at any volume :D

The problem is getting to mute the Laptop speakers with a jack plug.

While I post this, I'll keep trying other configs.



BTW:

I get this warning/errors when I try
```

~$ killall alsaaudio
~$ sudo alsa force-reload
~$ pulseaudio -D

```


Am I doing something wrong somewhere? :confused:


Thanks in advance

A lot of the switch sensors do not work with the alsa version in Jaunty. You might try a newer alsa. There is a thread around here with scripts for installing the latest alsa version. 

Or you just might want to wait a few weeks for Karmic. A lot of long running sound issues have finally been fixed and it is much easier to use soundwise.

---

### Post by Thorndog on 2009-10-12
I tried Harrykar suggestions and found mic volume adjust etc.
output from arecord -l is
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SP2208WFP [Monitor Webcam (SP2208WFP)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
so apparently my system sees the microphone but it just doesn't work!!!!
I have used it in XP today so def not hardware problem.
any ideas?

---

### Post by harrykar on 2009-10-13
> **Thorndog said:**
> I tried Harrykar suggestions and found mic volume adjust etc.
output from arecord -l is
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SP2208WFP [Monitor Webcam (SP2208WFP)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
so apparently my system sees the microphone but it just doesn't work!!!!
I have used it in XP today so def not hardware problem.
any ideas?

Hi Thorndog. Above all i suggest you** don't fear to play around.** Here's the rule:(. So confirm that you have just enabled all fields below  in *volume control preferences *window?:

front mic
front mic boost(optionally)
and (**the most important**) the 2 inputs
(see screenshots)

If yes moreover play(i say *play* here because e.g. my motherboard has 2 positions to connect the mic one in front and another one behind. I have had connected mic in front position) to set mic position in *input source* field in *Options* tab (see screenshots).That was an important point in my case

Hope this help you

---

### Post by Thorndog on 2009-10-13
Harrykar,
thanks for the input.
I have been playing with all the settings. Below is a screenshot of all the menus I have available. I have no problem getting a plug in mic (in my case only 1 input on the rear), in fact I cannot seem to shut it off even when i CHANGE AROUND THE alsa TO oss etc.
It seems that the rear jack has got the input capture locked down and won't give it up, even when I turn on the mic in volume control and using gamix which at least shows controls for everything.
My menus don't include all the options you have, not sure why, different boards I would guess. See attachment.
My sound is all working fine so I am hesitant to install other programs to manage the audio. I went to synaptic package manager to try and follow the install sequence laid out by markbuntu at the beginning of this thread and it seems that it was mostly already installed and also since I have had some problems because of my 64 bit quad proc I would just as soon leave well enough alone.
I think what I need is a command line fix to force the system to use the webcam mic tat the system sees:
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Red"]card 1: SP2208WFP [Monitor Webcam (SP2208WFP)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]
here. If that is not possible then I would look for further enlightenment from the gurus of Ubuntu who are out there in their thousands and probably in the meantime I will just use an external mic.
Thanks for your help

---

### Post by harrykar on 2009-10-13
> **Thorndog said:**
> 
I have been playing with all the settings. Below is a screenshot of all the menus I have available. I have no problem getting a plug in mic (in my case only 1 input on the rear), in fact I cannot seem to shut it off even when i CHANGE AROUND THE alsa TO oss etc.
It seems that the rear jack has got the input capture locked down and won't give it up, even when I turn on the mic in volume control and using gamix which at least shows controls for everything.


Firstmost post a sreenshot of your *Options *tab(i don't see it yet in your screenshot) like my here:
[http://ubuntuforums.org/attachment.php?attachmentid=131737&d=1255383426](http://ubuntuforums.org/attachment.php?attachmentid=131737&d=1255383426) 
As i say there you can set the mic position like *front mic, mic,  line* in my case (depend of your hardware) and it's a very important (for mic functioning) set. I remember in my case was per default  in *mic* position instead of *front mic* and my mic was mute(on purpose "It seems that the rear jack has got the input capture locked down and won't give it up, even when I turn on the mic in volume control" that behavior suggest  an improper setting or hardware.I guess the earlier). After i set it to *front mic* my mic wake up like a charm.
(I use a planctronics like mic&headphone with 2 jacks one for mic and another one for headphone)

> **Thorndog said:**
> 
My menus don't include all the options you have, not sure why, different boards I would guess. See attachment.


I agree with you

> **Thorndog said:**
> 
My sound is all working fine so I am hesitant to install other programs to manage the audio. I went to synaptic package manager to try and follow the install sequence laid out by markbuntu at the beginning of this thread and it seems that it was mostly already installed and also since I have had some problems because of my 64 bit quad proc I would just as soon leave well enough alone.

I'm sure it's not a lack of software problem but an inappropriate set instead 

> **Thorndog said:**
> I think what I need is a command line fix to force the system to use the webcam mic tat the system sees:


I don't know magic commands:P once again post a sreenshot of your *Options* tab

> **Thorndog said:**
> 
If that is not possible then I would look for further enlightenment from the gurus of Ubuntu who are out there in their thousands and probably in the meantime I will just use an external mic.


OT: Hehe the real gurus have been in the past and now are in embeeded systems or maybe in *bsd (if you ignore about take a glance here:  [http://harrykar.blogspot.com/2009/10/freebsd.html](http://harrykar.blogspot.com/2009/10/freebsd.html)) world.  Here we're just normal users more or less informed(geeks?) but certainly not gurus

If your options tab is well set and webcam's mic is ever death then you can probe an external mic in the rear 

> **Thorndog said:**
> 
Thanks for your help


My pleasure. Also I have been helped elsewhere:). That's the strength of a good community:wink:

Harry

PS: Also notice the difference between your *sound capture *field set and my & others(that's moreover the default) in the sreenshot below. Moreover if you clik the next test button and mic is working you must hear your voice with a reverb(little delay) & probably a little noise

---

### Post by Thorndog on 2009-10-14
Harrykar,
I didn't explain but the one window on the screenshot on the right was your volume control window for comparison. Mine does not even have an options tab!! I set up my netbook with 9.10 'netbook remix', which incidentally is a great package, last night for Skype and it has more or less exactly the settings windows that you show in you screenshots. Like, hey this looks familiar sais I. Absolutely flawless setup, webcam and mic both work.
I already have rear mic going on my 'main machine'. I'm guessing that my next system update will magically 'fix' this problem like all the other problems that got fixed updating from 8.04 to 9.04 meanwhile I will keep poking no doubt since it is bothering me. When it's fixed, I'll post.
Regards

---

### Post by harrykar on 2009-10-14
> **Thorndog said:**
> Harrykar,
I didn't explain but the one window on the screenshot on the right was your volume control window for comparison. Mine does not even have an options tab!! 


Sorry too little my time for help > much speed > much bugs(miss in my case: i not have observed well because half window was hidden from another one) 

> **Thorndog said:**
> Harrykar,
I set up my netbook with 9.10 'netbook remix', which incidentally is a great package, last night for Skype and it has more or less exactly the settings windows that you show in you screenshots. Like, hey this looks familiar sais I. Absolutely flawless setup, webcam and mic both work.


If i think my first Slakware in first '90s LOL I "blush". Well done

> **Thorndog said:**
> Harrykar,
I already have rear mic going on my 'main machine'. I'm guessing that my next system update will magically 'fix' this problem like all the other problems that got fixed updating from 8.04 to 9.04 meanwhile I will keep poking no doubt since it is bothering me. When it's fixed, I'll post.


So you have an alternative way; you're working(if I have understood well). Regard fixes: That's sure. The only problem is if someone hasn't alternative (you have fortunately rear mic possibility ); because Bazzaar (see Stallman's cathedral Vs bazaar )  world is a little to very chaotic & therefore the bugfix shedule is mostly time-depended

PS: I just run 9.10 beta release on a virtual machine and i notice that my sound problem (not more ..but was a problem in the past) as i described it in my earlier post is still not fixed(it still needs manual work otherwise don't work "out of the box"). Maybe in 10.4 release ("The hope is the last to die")


Regards
Harry Kar

---

### Post by simsimt on 2009-10-21
Hello all,

I'm running Ubuntu Jaunty 9.04 on laptop and sound is working perfectly except on headphones where no sound plays at all. I googled the problem and many resources suggested turning off "Surround" in Volume Control > Preferences. However, there is not any listing of "surround" in the preferences list.  Of course the device is HDA Intel (Alsa Mixer).

Any other possible way to get headphones to work?

Thanks in advance.

---

### Post by harrykar on 2009-10-22
> **simsimt said:**
> Hello all,

I'm running Ubuntu Jaunty 9.04 on laptop and sound is working perfectly except on headphones where no sound plays at all. I googled the problem and many resources suggested turning off "Surround" in Volume Control > Preferences. However, there is not any listing of "surround" in the preferences list.  Of course the device is HDA Intel (Alsa Mixer).

Any other possible way to get headphones to work?

Thanks in advance.

Take a glance in my posts from #229 till here(if you have that hw). Unfortunately all this are problems strictly hardware(that's fastly varying in time) depended (precisely motherboard's/PCI soundcard chipset). So hardware coincidence  is difficult/improbable and consequently every answer refer to a particular (not all) hardware. My hw (look in my earlier posts) permits a *Swich tab* (look in sreenshot) that matter headphones. All i have to do is tic the field

Hope this help you

---

### Post by abhiroopb on 2009-10-25
I made a mess of things. Basically, I added some repo's that totally destroyed my dependencies and I had to re-install a lot of packages (including alsa and pulse). I also had to re-install my kernel and numerous other things.

In between doing all this my configuration got messed up. Before adding the repo everything was fine. So, I assume if I were to re-install jaunty at this point everything would work fine. But, of course I'd rather not re-install everything.

What the basic commands show me:

```

$ aplay -l
aplay: device_list:217: no soundcards found...

```

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

[code]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[code]

I've done everything in these guides: 
http://ubuntuforums.org/showthread.php?t=205449
http://ubuntuforums.org/showthread.php?t=1130384
http://ubuntuforums.org/showthread.php?t=1043568
http://ubuntuforums.org/showthread.php?t=843012

Nothing has worked for me. In fact I've done everything twice I think!

Please help!!

---

### Post by vexorian on 2009-10-26
I had issues with front headphones jack not working after I changed my motherboard to an ASUS P5K/1600 one.

I kinda fixed it (I think have a problem with totem not using pulseaudio but something else)

First, I did aplay -l
```

vx@vx:~$ LANG=EN aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```
so it had 2 "subdevices" this is apparently very rare. My guess was that subdevice #1 was the front headphone jack. None of my programs was using that subdevice.

So I did:
```

aplay -Dhw:0,0,1 somewavfile.wav

```
And headphones were working, problem was getting to make pulseaudio use them which I eventually did by :
```

sudo gedit /etc/pulse/default.pa

```
I added:
```

load-module module-alsa-sink device=hw:0,0,1

```
Just before the:
```
### Automatically load driver modules for Bluetooth hardware

```

Line, restarted and a new device was appearing in pulseaudio. I used pulseaudio manager's "configure local sound server" to create a virtual device that sent input to both devices. I made this new virtual device the default. headphones work in Rhythmbox but not in totem for some reason.

I also have another problem with PCM mixer getting muted whenever I log-in, this seems to get fixed temporarily by removing ~/.pulse and ~/.pulse-cookie, but it gets ruined again eventually.

Edit: I deleted ~/.pulse and ~/.pulse-cookie again then rebooted, and now everything seems to work 100%, headphones work in totem and there is no PCM muting on init.

---

### Post by nooblot on 2009-10-26
this is where I start to hate Linux and am thinking of "going back"

sigh
don't have time to drop another x hours try to search out a fix


Browser sound coming out of laptop , not nice USB speaker :(

---

### Post by vexorian on 2009-10-27
Didn't pulse audio device chooser work? It should allow you to pick what device to send the stream, or you could make your life easier and make a combined virtual device.

Reality is that your hatred is being misdirected, this would be far easier if hardware companies would actually decide on standards, instead they just design towards making it easy only for the users of a single platform.

---

### Post by nooblot on 2009-10-27
> **vexorian said:**
> Didn't pulse audio device chooser work?...

well I did not install pavucontrol because [this "freaks" me out]("http://i.imgur.com/LZI87.jpg")....ALL that is going to be gone ??!!

I thought "forgetit"

---

### Post by vexorian on 2009-10-28
I checked pavucontrol's dependency list and it doesn't have conflicts with any package.

Are you sure you didn't have a failed package installation? Does that list appear when you try to install any other package?

---

### Post by nooblot on 2009-10-28
> **vexorian said:**
> 

Are you sure you didn't have a failed package installation? Does that list appear when you try to install any other package?

no I have no package failure
and that list is definitely "unique", never seen it before

---

### Post by karimruan on 2009-10-28
Thanks for this, it got my mic working, and sound is flawless now! I have been searching the web for just this kind of how to! Thanks again!

---

### Post by m0nstersnatch on 2010-01-04
> **markbuntu said:**
> This seems to be a problem with some upgrades, not really common but not so rare either. What you should do is to reinstall alsa completely so any leftover configs can also be purged.

(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

If you needed to edit your /etc/modprobe.d/alsa-base file you may not have to with the updated driver but if you still do the file in Jaunty is /etc/modprobe.d/alsa-base.conf. This is to conform to configuration file naming conventions. 

Then follow the guide. let me know how this works out for you.
Nope, this did not help.
I had sound after the installation of Jaunty but weeks later after a reboot caused by an Amarok crash my sound diasappeared completly! I tested the hardware by using a 9.10 LiveCD and there was sound, so now i want my sound back on Jaunty! ;)
Here the logs of alsa-info.sh on 9.04 w/o sound:
[http://www.alsa-project.org/db/?f=54f1e63412030f07118f12ed6f364a3f94bc5047](http://www.alsa-project.org/db/?f=54f1e63412030f07118f12ed6f364a3f94bc5047)

using the liveCD from 9.10 i have sound again:
[http://www.alsa-project.org/db/?f=a5f966ba7ca83c6998578f11c1ad0d40dad85858](http://www.alsa-project.org/db/?f=a5f966ba7ca83c6998578f11c1ad0d40dad85858)

```
$ sudo lspci -vvnn
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
   Subsystem: IBM Device [1014:02c7]
   Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   Latency: 0
   Interrupt: pin B routed to IRQ 17
   Region 0: I/O ports at 1c00 [size=256]
   Region 1: I/O ports at 18c0 [size=64]
   Region 2: Memory at e0000c00 (32-bit, non-prefetchable) [size=512]
   Region 3: Memory at e0000800 (32-bit, non-prefetchable) [size=256]
   Capabilities: [50] Power Management version 2
      Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
      Status: D0 PME-Enable- DSel=0 DScale=0 PME-
   Kernel driver in use: Intel ICH
   Kernel modules: snd-intel8x0
```
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

