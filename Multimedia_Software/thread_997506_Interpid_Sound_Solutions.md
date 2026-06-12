---
title: "Interpid Sound Solutions"
date: 2008-11-29
forum: Multimedia Software
---

### Post by markbuntu on 2008-11-29
** Intrepid 8.10 Sound Solution**
**also works with Hardy Heron 8.04**
** with multimedia support**

If you are using Jaunty Jackalope 9.04 go here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

If you have just upgraded to or installed Intrepid or Hardy or Jaunty and you have some sound somewhere, but not everywhere for everything, this is a fast way to get all the missing stuff you need and give you some tools to figure out what is going on. If you hear the startup sound but nothing else, or if some applications work and others don't, this is for you. If you have no sound at all, there is a link at the end of this post for more extensive troubleshooting help but you should try this first anyway as it may solve your problem and will not make matters worse.

Make sure that your system is fully updated. (Jaunty is still somewhat of a mess with pulseaudio so if something is weird wait for an update or file a bug report)

** Essential Packages**
First you need to get some missing packages with Synaptic. These packages were not installed by default but are important for getting your sound working properly:

asoundconf-gtk

This is a little Default Sound Card application for choosing the default sound card for alsa. (This may not be necessary anymore with Jaunty)

gnome-alsamixer

This is a gui mixer, far easier to use than the command line alsamixer.

alsa-oss

This is the wrapper for oss applications so they will use alsa instead of grabbing the sound card all for themselves

libasound2
libasound2-plugins

These are the plugins for alsa

padevchooser

This is the Pulse Audio device chooser and will pull in the pavucontrol which is the Pulse Audio Volume Control and papref which is the Pulse Audio Preferences along with the Pulse Audio Volume Meters. (This is now included with Jaunty)

gstreamer0.10-pulseaudio

This is the gstreamer plugin for pulseaudio

ubuntu-restricted-extras

This is the package with all the restricted codecs and java and flashplayer so you can watch youtube and play your mp3s,etc..

If you have other applications like mplayer, vlc, amarok, or audacious be sure to get any extra packages available for them also.

**Setting things up**
Once you have all these packages installed, close any application that may be trying to use sound  and go to System/Preferences/Sound and set all the preferences from automatic to PulseAudio except Default Mixer Tracks which you should set to your sound card. Go to System/Preferences/Default Sound Card and choose pulseaudio. 

Next, right click on the little speaker on the top panel, that is the Panel Volume Control. Click Open Volume Control and make sure it is set to the same thing as the Default Mixer Tracks. Click on Preferences and make sure that Master and PCM and whatever else you want to control are selected. Make sure that any boxes labeled SPDIF or IEC958 are not checked. Close the Preferences box. Push up the sliders in the volume control and make sure the little speakers do not have little red mute marks on them. Go to Applications/Sound and Video/GNOME ALSA Mixer and see if there is anything you missed because sometimes, for some cards, not all the options are in the Panel Volume Control.

Go to Applications/Sound and Video and select Pulse Audio Device Chooser. This will put a little icon on the panel near the Panel Volume Control. Click on the new icon and choose Volume Control.  This will open the Pulse Audio Volume Control. Go to Output Devices and see if your sound card is there, it will be listed as ALSA PCM on front:...(ALC88) via DMA or whatever your sound card is.  If you have a usb device it will be listed as ALSA PCM on front:...(USB Audio) via DMA or something like that. Make sure the sliders are up and the device is not muted.

If any of the above is giving you problems, try rebooting.

Now, open Rythmbox and play something. If you have nothing handy just play one of the radio stations, you should hear something. In the Pulse Audio Volume Control/Playback you should see something like this
Rythmbox: Playback Stream 
and some Volume sliders that you can adjust. 

**More than one Device**
If you have more than one device listed in Output Devices, Rythmbox may be playing in the wrong one if you do not hear anything so right click on the stream and choose move stream and move it to another device.

If you have more than one device and you want to use them all, like a usb headset and your speakers, go back to the Pulse Audio Device chooser on the panel and select Configure Local Sound Server/Simultaneous Output and click the box:
"Add virtual output device for simultaneous output on all local sound cards"

Now you can right click on the stream and move it to your new device. You should have sound from all your sound devices now or at least a clue about how it is supposed to work.

**Other stuff**
Another thing you may need to do, Check in System/Administration/Users and Groups that your users and root are enabled as members of the following groups:
pulse
pulse-access
pulse-rt
This seems to be a particular problem for some people after getting recent updates.

**Extras**
I usually do this right after every install/upgrade.It is updated for Intrepid now and will really get you dialed in for sound and video (not updated for jaunty yet):

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

**KDE4 Phonon and Pulseaudio**
If you are using Intrepid or Jaunty with KDE4.1 or KDE4.2/Kubuntu you should read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

(If you are using KDE4.2 see post #9 in that thread.)

If this did not work for you, or you want to get your digital output or surround sound working, or you are using UbuntuStudio or jack, or you just need more information, you can go to my 10,000 page guide here, it was written for Hardy but also works for Intrepid, Jaunty testing is ongoing but the basic troubleshooting should help:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

An Italian language version of this post is here. Many thanks to caracuri for the translation.

[http://caracuri.altervista.org/blog/?p=129](http://caracuri.altervista.org/blog/?p=129)

---

### Post by agwblack on 2008-11-30
Great!! I was having real trouble with my sound, but following this has fixed it up perfectly! Ta v much.

---

### Post by GuitarStv on 2008-12-01
Thanks very much, I've been going nuts trying to figure out how to get audio working properly, this did it!

---

### Post by spandanj on 2008-12-01
> **markbuntu said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

ok. I did what it said in your post. It worked!!!. Now flash 10 in firefox IS USING pulse as evidenced by a stream in pavucontrol:

ALSA plug-in [firefox]: ALSA playback.

THank you!!! (I don't know how this works, but followed your steps and it works now)


However, I have two questions:

1) the flash player in firefox has a very low volume even though it's (stream) volume is set too 100% in pavucontrol. While, simultaneously the banshee stream gives me a good volume at 100% in pavucontrol. I have set my sound card volume to max using the volume applet in gnome bar
2) WHY do I (...the user) have to take so just to set up audio properly????? It's annoying have to configure so many things in my fresh install. Sound is just one of them. Why can't the ubuntu devs just make it work??? I am on ubuntu 8.04. 


I hope this configuration will last a few months without breaking...although even as right now, its not perfect, because my overall volume in my headphones has reduced very much even after setting all volume settings to max and configuring the system as your post suggests.

---

### Post by Zarok on 2008-12-02
Sadly didn't help with my issue with S/PDIF. even when I switch everything to pulseaudio and install all the packages you have listed, it only plays AC3/DTS audio through it, and those only when mplayer or VLC uses the force AC3/DTS through spdif-option. All OS sounds etc still go through analog. Audio chip is ALC883 on a Intel ICH8 chipset. Annoys the crap out of me when I had this working like 3 months ago perfect and then some kernel update(I think) broke it :/

---

### Post by markbuntu on 2008-12-02
> **spandanj said:**
> ok. I did what it said in your post. It worked!!!. Now flash 10 in firefox IS USING pulse as evidenced by a stream in pavucontrol:

ALSA plug-in [firefox]: ALSA playback.

THank you!!! (I don't know how this works, but followed your steps and it works now)


However, I have two questions:

1) the flash player in firefox has a very low volume even though it's (stream) volume is set too 100% in pavucontrol. While, simultaneously the banshee stream gives me a good volume at 100% in pavucontrol. I have set my sound card volume to max using the volume applet in gnome bar
2) WHY do I (...the user) have to take so just to set up audio properly????? It's annoying have to configure so many things in my fresh install. Sound is just one of them. Why can't the ubuntu devs just make it work??? I am on ubuntu 8.04. 


I hope this configuration will last a few months without breaking...although even as right now, its not perfect, because my overall volume in my headphones has reduced very much even after setting all volume settings to max and configuring the system as your post suggests.

There is a tiny volume control in the flashplayer applet. Make sure it is turned up all the way.

As far as your second question goes, the Ubuntu audio team seems to be asleep at the wheel for the last few distros, switching to pulseaudio and leaving out the pulseaudio tools.....

---

### Post by markbuntu on 2008-12-02
> **Zarok said:**
> Sadly didn't help with my issue with S/PDIF. even when I switch everything to pulseaudio and install all the packages you have listed, it only plays AC3/DTS audio through it, and those only when mplayer or VLC uses the force AC3/DTS through spdif-option. All OS sounds etc still go through analog. Audio chip is ALC883 on a Intel ICH8 chipset. Annoys the crap out of me when I had this working like 3 months ago perfect and then some kernel update(I think) broke it :/

There are a number of issues with digital output depending on which card/driver you are using and I did not want to get into all that since this is meant to be a quick start guide.

Due to the inconsistent way that the alsa driver writers deal with secondary devices it is difficult for the pulseaudio devs to come up with some way to consistently detect digital inputs and outputs. They are trying and so are the alsa people.

Nevertheless, for now you can make a sink for digital output that will appear in pavucontrol and can be used like any other sink. 

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

This is the original ticket at pulseaudio where Lennart explains the problem.

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

You can also read this from alsa:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

---

### Post by Norman Thom on 2008-12-02
Thank you markbuntu:

I tried what you suggested. Unfortunately I was not able to find assoundcof-GTK, libsound2 or libsound2 - plugins in synaptic. any ideas where I might get them

---

### Post by markbuntu on 2008-12-02
Did you misspell these in your search with Synaptic?

It is a common thing to do, I do it all the time. In fact I just discovered I misspelled libasound in the OP (I wrote Libasound). But anyway that is fixed.

asoundconf-gtk
libasound2
libasound2-plugins

---

### Post by sdowney717 on 2008-12-05
so far I have not lost any sound since following along with this.
Solid 3 days with not losing sound is really impressive. I used to have to reboot twice a day due to sound shutting down.

---

### Post by lister171254 on 2008-12-06
First of all thanks markbuntu for well written instructions and your time and effort. 
Unfortunately I have similar problems to Zarok with getting Digital output to work. I also share his sentiments as I have been using Ubuntu as my music player for a pretty expensive stereo for over two years without any sound problems only to have this latest release screwing everything up.

I have followed markbuntu's (and others) instructions and have sound via my PC speakers, but cannot get digital output to work. I have attached a few screen shots and config files; maybe I'm missing something obvious.

I do get digital output after the system rebooted (i.e. the drums) and I guess that this is before pulseaudio starts. I can also get digital output (the test tone) when I set the output to ALSA in the Sound Preferences.

Thanks

---

### Post by shanse2 on 2008-12-06
I appreciate all the help this forum provides.  I recently installed Ubuntu 8.1 on a Dell Inspiron 9100 laptop, but am having sound problems.

When I first installed Ubuntu, I could not control the sound with either the volume controls on the laptop or with the volume control in the top task bar.  The sound was extremely loud, and I couldn't do anything about it.  

I followed all of the instructions in this post, and now I have the opposite problem.  I still can't control my sound, but now it is very quiet.  

Does anyone know how to fix this problem?

---

### Post by markbuntu on 2008-12-07
> **lister171254 said:**
> First of all thanks markbuntu for well written instructions and your time and effort. 
Unfortunately I have similar problems to Zarok with getting Digital output to work. I also share his sentiments as I have been using Ubuntu as my music player for a pretty expensive stereo for over two years without any sound problems only to have this latest release screwing everything up.

I have followed markbuntu's (and others) instructions and have sound via my PC speakers, but cannot get digital output to work. I have attached a few screen shots and config files; maybe I'm missing something obvious.

I do get digital output after the system rebooted (i.e. the drums) and I guess that this is before pulseaudio starts. I can also get digital output (the test tone) when I set the output to ALSA in the Sound Preferences.

Thanks

If you follow the link in the OP to my 10,000 page guide, there is a link there with directions for adding a device for getting your digital output into the pulseaudio volume control. That should fix you up.

---

### Post by markbuntu on 2008-12-07
> **shanse2 said:**
> I appreciate all the help this forum provides.  I recently installed Ubuntu 8.1 on a Dell Inspiron 9100 laptop, but am having sound problems.

When I first installed Ubuntu, I could not control the sound with either the volume controls on the laptop or with the volume control in the top task bar.  The sound was extremely loud, and I couldn't do anything about it.  

I followed all of the instructions in this post, and now I have the opposite problem.  I still can't control my sound, but now it is very quiet.  

Does anyone know how to fix this problem?

The pulseaudio volume control is probably controlling your sound now along with the panel volume control so you probably need to adjust them both. To get your media keys to control the sound you need to use System/Preferences/Sound and select your sound card for the default mixer.

---

### Post by lister171254 on 2008-12-08
> **markbuntu said:**
> If you follow the link in the OP to my 10,000 page guide, there is a link there with directions for adding a device for getting your digital output into the pulseaudio volume control. That should fix you up.

The digital output is already displayed in the pulseaudion volume control (see attached). I seem to recall that ALSA has a problem with multiple output devices on the same card. If this is correct, I would like to change the order of the devices when loaded (see attached) by pulse so the optical is loaded first. Tried to do this, but am unsuccessful so far.

I may of course be totally off the mark.

Thanks.

---

### Post by markbuntu on 2008-12-09
What you can do is go to the pulseaudio device chooser and select Configure Local Sound Server/Simultaneous Output and enable the box

Add virtual output device for simultaneous output on all local sound cards

This will create a virtual simultaneous output device in the pulseaudio volume control that you can use like any other device.

---

### Post by Robbyx on 2008-12-10
I started out with no sound and before reading this thread installed oss 4. This gave me sound but also crackling, especially when there is no playback.

I have tried to follow you solution but can not get pulse audio to work because the device is not being found.

Pref-- default sound card does not bring up any options. The waiting cursor fades away.

In sound prefs devices
If I choose sound playback and set it to pulse audio sound server and test it this is the result:


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

ie no test sound is produced. It does test if I set it to oss 4.

Can you help me?

---

### Post by lister171254 on 2008-12-10
> **markbuntu said:**
> What you can do is go to the pulseaudio device chooser and select Configure Local Sound Server/Simultaneous Output and enable the box

Add virtual output device for simultaneous output on all local sound cards

This will create a virtual simultaneous output device in the pulseaudio volume control that you can use like any other device.

Tried you suggestion, but couldn't get it to work.

I found a way of making my optical output the default and now have sound (again) via optical out. I used the Pulseaudio applet to set the default sink to the second sink as per attached screenshots. 

Thanks

---

### Post by markbuntu on 2008-12-10
> **Robbyx said:**
> I started out with no sound and before reading this thread installed oss 4. This gave me sound but also crackling, especially when there is no playback.

I have tried to follow you solution but can not get pulse audio to work because the device is not being found.

Pref-- default sound card does not bring up any options. The waiting cursor fades away.

In sound prefs devices
If I choose sound playback and set it to pulse audio sound server and test it this is the result:


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

ie no test sound is produced. It does test if I set it to oss 4.

Can you help me?

This does not work with OSS4. I think there may be OSS4 support for pulseaudio in OSS4.1 but you would need to find that out from the OSS devs.

---

### Post by Robbyx on 2008-12-10
> **markbuntu said:**
> This does not work with OSS4. I think there may be OSS4 support for pulseaudio in OSS4.1 but you would need to find that out from the OSS devs.

I now realise that the sound has ceased working. In order to get the sound to work properly I don't mind going back to pulseaudio and to remove oss4.  I do not know how to do that successfully.

---

### Post by markbuntu on 2008-12-10
> **Robbyx said:**
> I now realise that the sound has ceased working. In order to get the sound to work properly I don't mind going back to pulseaudio and to remove oss4.  I do not know how to do that successfully.

There are some directions for doing that in the OSS4 thread.

---

### Post by Robbyx on 2008-12-11
> **markbuntu said:**
> There are some directions for doing that in the OSS4 thread.

Do you have a link?

---

### Post by nightcrawl on 2008-12-11
I had a sound problem in my Vaio... both speakers&headphones worked simultaneously. I've resolved my problem as I tell here:

[http://ubuntuforums.org/showthread.php?p=6343772](http://ubuntuforums.org/showthread.php?p=6343772)

But when resolving, I might have made something wrong because I've lost the Output volume control keys (Fn+F2; Fn+F3; Fn+4;) for the Input. 

I mean... Watching the alsa mixer gui and operating the control keys, i can see the "In-gain" moving instead "Master Volume".

Anyone knows what might be? :confused:

I've only edited the /etc/modprobe.d/alsa-base file. Is it possible that I've made something wrong in that file?

---

### Post by sv1cdn on 2008-12-13
Hi all!
After upgrading to 8.10 from 8.04 started having sound problems. Dig a lot in forums and found this help (great!) followed everything but the problem still remains.
At log in prompt I get no sound. When I log in I get the usual first sound of Ubuntu. Then when I try to play a simple .mp3 it works fine. After a random time (even when I leave my pc doing nothing) and I try to play again the same .mp3 with the same player I get NO sound at all! Using Volume control -> Playback I can see the application there and it is not muted or anything, yet no sound comes out!
If I do sudo alsa force-reload it works 90% otherwise I have to hard reset - restart the whole Ubuntu!
Doing a lot of dig in forums I discovered that for what I am saying above, alsa libs have a bug and will be corrected, any idea?
FYI, never had a problem with sound since Ubuntu 7.04
Could there be an issue with ATI Radeon HD 3450 vga that I have also installed?
Thank you for your kind help!
Take care.

Dennis.

[UPDATE] I realized that if I leave one audio application playing an audio file (in pause) then volume control of Pulse server shows it in Playback (as expected) and my sound 99% never stops! Even after hibernate!

---

### Post by markbuntu on 2008-12-14
It could be that in the PA Volume Control/Output Devices there is the wrong device selected for default. You can fix this by right clicking on the correct device.

The HD 3450 card has its own HDMI audio device and sometimes that can become the default for alsa when the system starts or restarts.

---

### Post by sefs on 2008-12-14
> 
Setting things up
Once you have all these packages installed, close any application that may be trying to use sound and go to System/Preferences/Sound and set all the preferences from automatic to PulseAudio except Default Mixer Tracks which you should set to your sound card. Go to System/Preferences/Default Sound Card and choose pulseaudio.


Am i seeing things or there is no such thing as "System/Preferences/Default Sound Card"

I can't find that anywhere...where is it?

Update: Never mind it appeared after installing said packages.

---

### Post by sefs on 2008-12-14
Hi again,

I've had to switch to my built in soundcard from a soundblaster LIVE i was using as the mic input did not work with that.

But now the volume from the built in soundcard is very very low.  The LIVE card was much louder.  

Is there any way to pump up the volume?

Thanks.

---

### Post by jis on 2008-12-15
I have Creative Labs Soundblaster Live! (value) soundcard
> $ lspci | grep audio
02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)


It has two analog line outs: green and black one. I can get sound of only the green one in Gnome session. In Xfce4 session I get sound from both; the black one is controlled by Wave Surround mixer setting.

I wonder how can you enable the black output (together with the green one) in Gnome/Pulseaudio?

---

### Post by sv1cdn on 2008-12-15
Thought so, but not this case markbuntu! Anybody saw a bug report in launchpad?

---

### Post by markbuntu on 2008-12-15
> **sv1cdn said:**
> Thought so, but not this case markbuntu! Anybody saw a bug report in launchpad?

Are you using alsa 1.0.17 or 1.0.18?
There may be a problem in the alsa libs. Alsa is a mess. Intrepid is still using pulseaudio 0.9.10 which is old but has very few bugs left if any but is missing some features that are in the newer versions. the pa devs are up to 0.9.13.

---

### Post by Roger Allott on 2008-12-15
Hi Markbuntu,

I thought I had cracked the problem yesterday after following your guide, but today I've been trying a few different applications and it seems that my sound is only OK for certain ones and not others. Rhythmbox, Banshee and Audacious are happy playing mp3 and/or wmv files, but I can't get any sound at all out of Aoleus or Alsa Modular Synth, and I can't find any app at all that recognises sound recording through my laptop's internal microphone.

Something from your initial post in this thread looks suspiciously like it might be on the right track:-

> **markbuntu said:**
> 
Next, right click on the little speaker on the top panel, that is the Panel Volume Control. Click Open Volume Control and make sure it is set to the same thing as the Default Mixer Tracks. Click on Preferences and make sure that Master and PCM and whatever else you want to control are selected. Make sure that any boxes labeled SPDIF or IEC958 are not checked. Close the Preferences box. Push up the sliders in the volume control and make sure the little speakers do not have little red mute marks on them. Go to Applications/Sound and Video/GNOME ALSA Mixer and see if there is anything you missed because sometimes, for some cards, not all the options are in the Panel Volume Control.

When I do those steps I leave both of the IEC958 boxes unchecked in Panel Volume Control > Preferences (screenshot below):

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-VolumeControlPreferences.png[/IMG]

but then when I go to GNOME ALSA Mixer I see that for some reason that looks odd to me, the IEC958 Default PCM box is checked (screenshot below):

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-GNOMEALSAMixer.png[/IMG]

Might this be what's causing my problem, or does that look OK to you? Should I simply uncheck that box in ALSA Mixer and reboot?

---

### Post by markbuntu on 2008-12-15
You can try that. You should also try turning up the mic boost. Also, in the pulseaudio volume control you should make sure your default input device is the ALC 883. You can check that by right clicking on it.

In the Preferences box I see the Input Source options are unchecked. You should check those boxes and then look in the options section of the panel volume control to see what they do. They may have something to do with which mic gets captured.

---

### Post by sv1cdn on 2008-12-16
> **markbuntu said:**
> Are you using alsa 1.0.17 or 1.0.18?
There may be a problem in the alsa libs. Alsa is a mess. Intrepid is still using pulseaudio 0.9.10 which is old but has very few bugs left if any but is missing some features that are in the newer versions. the pa devs are up to 0.9.13.

I am using 0.9.10 PA any idea how to install 0.9.13? As for the alsa, how can I be sure which one I have?
Dennis.

---

### Post by PlatoDan on 2008-12-18
Hi, I tried this on my laptop and so far so good. So thanks! 

The only issue I have is that my volume switch no longer adjusts the volume. As I move it up and down, the animation on the screen appears but no matter how high or low I adjust it, the volume remains constant. Is there a way to make my volume buttons function again? Thanks!

---

### Post by markbuntu on 2008-12-18
You need to select what is controlled in the panel volume control/preferences, usually Master or PCM by clicking on it.

---

### Post by PlatoDan on 2008-12-18
lol worked like a charm. I knew it would be something totally simple. Thanks. :)

---

### Post by theteju on 2008-12-22
Hello Sir, 

I am new bee to Ubuntu. here is my situition. I had 8.04 before and in which somehow everything worked just fine.

NOw I got 8.10 (fresh install)
I followed your instructions. and pretty much sound is working out of the box except I have two issue.

1. I need SPDIF digital sound out.
2. second headphone jack on front is not working.

I have dell inspiron 1420. I tried a lot before posting But finally I lost patience and now need some help

I hope somebody will reply.

Thank you.

---

### Post by markbuntu on 2008-12-23
There is help for those problems here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You can look in the digital section about adding control of the digital output to pulseaudio and for didgital help in general.

For help with the headphone jack you can look in the Drivers/HDA section. OEMs did a lot of tweaking to the HDA firmware to fit their particular needs and it is difficult for the ALSA driver to detect which is which so you may need to adjust the option for the hda driver. There are links so you can find out how to do that. 

There is also a whole sub-forum for dell machines here that may be helpful.

---

### Post by anne_maree on 2008-12-25
Thanks heaps markbuntu. I was on the verge of going back to Gutsy due to no sound, but your guide worked like a charm :)

---

### Post by unknown011 on 2008-12-28
I have tried all the guides that I could find on the internet and nothing has worked yet.
I was using 7.10 which worked fine, then about a month ago I updated to 8.04 and then up to 8.10. Since then (and in 8.04) I have not had any sound at all!

I have followed your guide, and also read your other thread (the 10,000 one) and followed numerous guides, please help me out! I also created a bug in launchpad over 3 weeks ago and no-one has helped :( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304888](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/304888)

Any ideas what I can do?

---

### Post by markbuntu on 2008-12-28
From the bug report it looks like your AC'97 sound chip is beong properly detected so it should work. 

It looks like there are a lot of switches available in the sound mixer so you should check and make sure the master and pcm and other switches are on. Use the gnome-alsamixer, it is easier to use and should show all the options. You should also check that System/Preferences/Sound is set to pulseaudio and in the pulseaudio volume control/output devices that the AC'97 is selected as the default device (right click on it.)

What applications are you trying to use?

---

### Post by unknown011 on 2008-12-28
All the switches are on in alsamixer.

PulseAudio seems to be set up fine too, as per the guide.

I have tried to play mp3's in both vlc and rhythmbox. Rhythmbox has issues though and frequently freezes and I don't think it's actually playing it anyway. It all seems to work fine in vlc though but no sound.

---

### Post by jaydoc on 2008-12-29
Hi

I am running Kubuntu Ibex. and having trouble with flash audio in firefox. if i play flash on firefox then there is no audio available to amarok, or any other application, unless I close firefox and restart the other app. sometimes i need to rebbot before being able to play anything.

All this is so frustrating. 

My question is - can I use this guide here to solve this issue...? it seems to be written for Ubuntu, but i would like to try it on Kubuntu.

---

### Post by markbuntu on 2008-12-29
Yes, it works fine for me with KDE4 on Intrepid. I installed KDE over gnome so I am not sure if the pulseaudio packages are included in kubuntu but it is easy enough to get them from the repos.

---

### Post by Old Jimma on 2008-12-31
Hi:

When I went to Applications/Sound and Video and select Pulse Audio Device Chooser. T and choose Volume Control the sliders were up and the device were muted.

I could not unmute them.

What should I do?

THanks,
Phil Smith
Duluth, GA

---

### Post by markbuntu on 2008-12-31
> **Phil Smith said:**
> Hi:

When I went to Applications/Sound and Video and select Pulse Audio Device Chooser. T and choose Volume Control the sliders were up and the device were muted.

I could not unmute them.

What should I do?

THanks,
Phil Smith
Duluth, GA

Are they muted in the volume control in your top panel or in the gnome-alsa mixer?

You need to click on the little speaker to mute and un-mute and when muted there is a box around the speaker and the other thing is greyed out. The little red x is always there.

---

### Post by Old Jimma on 2009-01-01
Markbuntu:

When I use gnome alsa mixer, they are not muted. 

However, (Appendix A, item 2) say: Open the "PulseAudio Device Chooser" from Applications/Sound & Video. Click on the applet icon, and click "Volume Control...". Click on the "Playback" tab.

When I do that the speakers are muted.

What should I do next?

THanks,
Phil

---

### Post by Old Jimma on 2009-01-01
Hi Mark:

When I click on those muted speakers they do not "unmute."

Phil

---

### Post by AmadeusOK on 2009-01-03
A complete noob here. Two days ago, I upgraded from Hardy Heron to Intrepid Ibex and after rebooting the sound icon showed a red X over it and since then there is no sound. When I click on it, I get the following message:

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

And also this one:

```
No volume control GStreamer plugins and/or devices found.
```

When I enter aplay -l on the terminal I get:

```
aplay: device_list:215: no soundcards found...
```

Entering lspci -v gives me:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fc000000-feffffff
	Prefetchable memory behind bridge: f9000000-f9ffffff
	Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at dce0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9
	Kernel modules: i2c-piix4

00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
	Subsystem: Dell Device 0082
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at dc00 [size=128]
	Memory at ff000000 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
	Subsystem: Dell Device 4082
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=256]
	Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: atyfb
```

For almost three days, I've been doing nothing except looking for a solution to my problem. I followed ever possible lead and wasted hours and hours but still no sound on this old computer. This is so frustrating! I faced the same situation when I upgraded from Ubuntu 7.10 to Ubuntu 8.04. Surfing the net I found something that worked out well but I just can't remember what I did.

Please, any help would be greatly appreciated. Thank you very much.

:(

---

### Post by sendblink23 on 2009-01-03
Markbuntu:

Lets see if you could help me out...

I'm not going to randomly install any of the things you have in your Thread .. since I have all my Sounds Working Perfectly(Natural Ubuntu sounds, VLC, MoviePlayer, RhythmBox, Flash: Youtube, Myspace & all websites), from simply installing fresh Ubuntu 8.10 ... ofcourse and installing any applications from *Add/Remove.. They all work 100%

**The only issue Application, that I do have perfect Picture, but NO SOUND is: TVtime**

[COLOR="Red"]Any[/COLOR] specific thing you can think off that I will need to execute?

I have a thread up of my issue: [http://ubuntuforums.org/showthread.php?t=1029078](http://ubuntuforums.org/showthread.php?t=1029078)
Some have tried to help, but still no success.

---

### Post by L8erG8er on 2009-01-04
Thanks, Markbuntu, I've been following your guides for a while now, and this one is just the right length and detail for us poor novices.

---

### Post by mahmater on 2009-01-05
Markubuntu! I really need your help.over a month now since I installed 8.10 everything is fine except for the microphone.It just drove me and many others crazy.

1. I cannot record anything in applications_sound and video_sound recorder.
2. I followed all of your instruction here:
      [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
3. whenever I UN-mute the mic in the volume control_recording,it becomes muted again (a little red sign).
4. in the pulse audio applet_volume control_input and output devices everything is muted and cannot be unmuted (the red little sign cannot be removed).

many thanks in advance for all the great effort you invested for the benefit of the ubuntu community.

---

### Post by markbuntu on 2009-01-05
There is a more comprehensive guide here that includes help for getting recording working. Also, there seems to be problems with some of the drivers in ALSA 1.0.17 for microphones.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If this does not help you should file a bug report at Launchpad or at alsa.org.

---

### Post by mahmater on 2009-01-07
thanx for replying. indeed I tried the tutorial about recording too.May be I should file abug.I never filed one,but I will learn how to.

---

### Post by markbuntu on 2009-01-07
The lttle red x is always there in front of the little speaker in the PA volume control. If you click on it a little box appears around it and the box above fades, that is when the mute is active.

I think this is a problem with alsa since it happens in the alsa mixer. I have seen others complaining about this in the forums so a bug report in either launchpad or alsa.org would probably be warranted.

---

### Post by hoboboot on 2009-01-07
THIS WORKED FOR ME, AMAZING! THANKS ALOT, WITHOUT THIS, PEOPLE WOULD HAVE NO CLUE HOW TO DO THAT ****, WITH HALF THE MIXERS /CONTROLS I NEEDED WERENT EVEN INSTALLED. WHY WERENT THEY... THATS LAME FRESH INSTALL, DETECTS CARD, AND THEN I GOTTA SET IT UP MYSELF? OH WELL ITS WORKING NOW SO YOU'RE DOPE MAN YOU ROCK. im gonna link this in my other threads as a solution.

---

### Post by Roasted on 2009-01-09
Can anybody tell me if they have Skype working with this? I cannot get my microphone to work to save my life and I really need Skype to get working. Any input?

---

### Post by markbuntu on 2009-01-09
Can you use your microphone at all?

What hardware do you have?

---

### Post by Roasted on 2009-01-09
I'm running a relatively new computer (about 2-3 months old) with a Turtle Beach Montego DDL 7.1 PCI sound card. My headset is a 15 dollar headphone/microphone combo set from Target, made by Logitech. I'm running Ubuntu Intrepid 8.10 64 bit. I did not alter my sound after installing, so whatever I have (pulse, alsa, whatever) from the get-go is what I have now. The only thing I've tinkered with is the settings.

Under sound preferences the top 3 lines are Autodetect, with Sound Capture being ALSA. My device is CMI8768, which is the chipset my Turtle Beach sound card uses.

When I open my volume control, I have Master/PCM/Line-in/Microphone/Phone listed. They are not muted and the levels are up.

Within volume control, if I go to the recording tab, I see microphone capture. It has 2 icons below it, one looking like a speaker for volume level and the other on the right is a microphone. It has a red X on it. If I click the red X to remove it, close volume control, and go back in, the red X reappears.

I'm not sure what else I can do.

EDIT - I have no idea what I did. I didn't make any changes. But suddenly my microphone decided to work. I mean, I shut my computer off last night, so maybe the "reboot" helped? Nonetheless, I hear my voice in my microphone in sound recorder. Now I just gotta get skype to work because it still won't work right.

EDIT AGAIN - Again, I made no changes to the system, only to skype to try and get it to work, and now my microphone does not work AT ALL.

This is by far the most inconsistent problem I've ever had in Ubuntu. It seriously makes me consider switching back over.

---

### Post by markbuntu on 2009-01-09
I have a SIIG sound card with that same chipset and it works just fine for me on Hardy and Intrepid. I assume you have followed the OP and got the packages, If so you can try some things.

Try setting System/Preferences/Sound/Sound Capture to pulseaudio and then in the Pulseaudio Volume Control/Input Devices right click on the ALSA PCM.... (C-Media... to make it the default. Open the gnome-alsamixer and make sure the mic is not muted and the rec box is checked along with the mic boost box. Make sure the Mic-in Mode box is not checked because that will redirect the Center/LFE output to the mic jack. Open the volume control from the top panel amd make sure that in Switches the mic boost capture box is checked. The volume control in the panel and the gnome-alsa mixer do the saem thing but they do not each have everything, weird. I could not get my mic to record until I turned on the mic boost capture switch. It was driving me crazy for a while.

Push up the sliders and see if you can hear the mic. Try to record something. In Skype set the input and output to pulse. I have not used skype on Intrepid but I see here in the forums that many people have got it working and many have not.

Your on board sound card could also be causing some of this but you have the pulseaudio volume control now so you can control that. The kernel could be changing the order of the sound cards each time you reboot which it will do since it arbitrarily assigns the interrupts on each boot.

I have a more involved guide with many links here. There is a link for Multiple Sound Cards that explains that problem and how to fix it.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Roasted on 2009-01-09
I checked the switch for mic boost and mic boost capture. But still I didn't hear anything. Under "options" where Mic-In Mode is, I do not have a switch to turn it on/off. Any ideas on that?

Now, when I go to sound recorder and record myself talking, it just comes through with 100% static. It did this after I changed my sound capture to pulseaudio sound server, along with the switches I added under options (mic boost + mic boost capture). I don't have a clue what else to do.

So, you're running Intrepid... with the same chipset sound card... and your's is working... what in the world does your setup have that mine doesn't??

EDIT - I just disabled my onboard sound card in BIOS and rebooted. So now I'm working ONLY with my PCI sound card. I set my sound capture in my sound preferences to ALSA as well as pulseaudio sound server. The first time I went into "sound recorder" I could record myself just fine. Then, I opened Skype. Skype yielded no difference, even with all of my sound input/output settings to "pulse." Then, I went back to "sound recorder" to record myself again... and it didn't work.

That's strange to me. 1 Sound card, not two like before. Sound recorder works, Skype doesn't, back to sound recorder and it doesn't work.

Gahhhh!

---

### Post by Despot Despondency on 2009-01-12
Hey, I've got a problem with my laptop, I've tried directions from this post but to no avail. When I do system-> preferences -> default sound card nothing seems to happen.

It's strange, sound seemed to be working fine the other day and then I updateded my laptop and now it has a red arrow over the speaker symbol in the system tray. When I click on the speaker symbol I get the message

```

The volume control did not find any elements and/or devices to control. 
This means either that you don't have the right GStreamer plugins installed, 
or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the 
speaker icon on the panel and selecting "Remove From Panel" from the menu.

```

Has anyone else had this problem?

---

### Post by starscalling on 2009-01-14
> **markbuntu said:**
> ** Intrepid Sound Solution, also works with Hardy Heron 8.04**
** with multimedia support**

If you have just upgraded to or installed Intrepid and you have some sound somewhere, but not everywhere for everything, this is a fast way to get all the missing stuff you need and give you some tools to figure out what is going on. If you hear the startup sound but nothing else, or if some applications work and others don't, this is for you. If you have no sound at all, there is a link at the end of this post for more extensive troubleshooting help but you should try this first anyway as it may solve your problem and will not make matters worse.

** Essential Packages**
First you need to get some missing packages with Synaptic. These packages were not installed by default but are important for getting your sound working properly in Intrepid:

asoundconf-gtk

This is a little Default Sound Card application for choosing the default sound card for alsa.

gnome-alsamixer

This is a gui mixer, far easier to use than the command line alsamixer.

alsa-oss

This is the wrapper for oss applications so they will use alsa instead of grabbing the sound card all for themselves

libasound2
libasound2-plugins

These are the plugins for alsa

padevchooser

This is the Pulse Audio device chooser and will pull in the pavucontrol which is the Pulse Audio Volume Control and papref which is the Pulse Audio Preferences along with the Pulse Audio Volume Meters.

gstreamer0.10-pulseaudio

This is the gstreamer plugin for pulseaudio

ubuntu-restricted-extras

This is the package with all the restricted codecs and java and flashplayer so you can watch youtube and play your mp3s,etc..

If you have other applications like mplayer, vlc, amarok, or audacious be sure to get any extra packages available for them also.

**Setting things up**
Once you have all these packages installed, close any application that may be trying to use sound  and go to System/Preferences/Sound and set all the preferences from automatic to PulseAudio except Default Mixer Tracks which you should set to your sound card. Go to System/Preferences/Default Sound Card and choose pulseaudio. 

Next, right click on the little speaker on the top panel, that is the Panel Volume Control. Click Open Volume Control and make sure it is set to the same thing as the Default Mixer Tracks. Click on Preferences and make sure that Master and PCM and whatever else you want to control are selected. Make sure that any boxes labeled SPDIF or IEC958 are not checked. Close the Preferences box. Push up the sliders in the volume control and make sure the little speakers do not have little red mute marks on them. Go to Applications/Sound and Video/GNOME ALSA Mixer and see if there is anything you missed because sometimes, for some cards, not all the options are in the Panel Volume Control.

Go to Applications/Sound and Video and select Pulse Audio Device Chooser. This will put a little icon on the panel near the Panel Volume Control. Click on the new icon and choose Volume Control.  This will open the Pulse Audio Volume Control. Go to Output Devices and see if your sound card is there, it will be listed as ALSA PCM on front:...(ALC88) via DMA or whatever your sound card is.  If you have a usb device it will be listed as ALSA PCM on front:...(USB Audio) via DMA or something like that. Make sure the sliders are up and the device is not muted.

If any of the above is giving you problems, try rebooting.

Now, open Rythmbox and play something. If you have nothing handy just play one of the radio stations, you should hear something. In the Pulse Audio Volume Control/Playback you should see something like this
Rythmbox: Playback Stream 
and some Volume sliders that you can adjust. 

If you have more than one device listed in Output Devices, Rythmbox may be playing in the wrong one if you do not hear anything so right click on the stream and choose move stream and move it to another device.

If you have more than one device and you want to use them all, like a usb headset and your speakers, go back to the Pulse Audio Device chooser on the panel and select Configure Local Sound Server/Simultaneous Output and click the box:
"Add virtual output device for simultaneous output on all local sound cards"

Now you can right click on the stream and move it to your new device. You should have sound from all your sound devices now or at least a clue about how it is supposed to work.

Another thing you may need to do, Check in System/Administration/Users and Groups that your users and root are enabled as members of the following groups:
pulse
pulse-access
pulse-rt
This seems to be a particular problem for some people after getting recent updates.

**Extras**
I usually do this right after every install/upgrade.It is updated for Intrepid now and will really get you dialed in for sound and video:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


If this did not work for you, or you want to get your digital output or surround sound working, or you are using UbuntuStudio or jack, or you just need more information, you can go to my 10,000 page guide here, it was written for Hardy but also works for Intrepid:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

killer... this plus compiling alsa got me my azalia audio codecs with multiple audio streams in xubuntu 9.04 [alpha2] ):P

---

### Post by hoboboot on 2009-01-16
is there any reason why these packages would not show up in the synaptic package manager?
 
asoundconf-gtk
gnome-alsamixer
alsa-oss
padevchooser
gstreamer0.10-pulseaudio
ubuntu-restricted-extras

they did 2 weeks ago when i followed this guide from hardy, since, i've wiped my drive and installed ibex, and now i cannot get my sound working as i had it in hardy 2 weeks ago, because i cannot get these packs. anyone up to date with this ? feel free to pm me if you know anything about this.

this guide was awesome to follow in hardy. but i am screwed for sound in ibex right now. thanks for any info you might have.

---

### Post by markbuntu on 2009-01-16
Well I just tried that and Synaptic could not find the packages until hit the reload button and updated the package list. That should not happen since the packages have not changed but then again Intrepid is still a work in progress.

---

### Post by AmadeusOK on 2009-01-17
> **Despot Despondency said:**
> Hey, I've got a problem with my laptop, I've tried directions from this post but to no avail. When I do system-> preferences -> default sound card nothing seems to happen.

It's strange, sound seemed to be working fine the other day and then I updateded my laptop and now it has a red arrow over the speaker symbol in the system tray. When I click on the speaker symbol I get the message

```

The volume control did not find any elements and/or devices to control. 
This means either that you don't have the right GStreamer plugins installed, 
or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the 
speaker icon on the panel and selecting "Remove From Panel" from the menu.

```

Has anyone else had this problem?

I'm having exactly the same problem right now. The sound was working just fine before upgrading to Intrepid Ibex. Several months ago, I had to deal with the same issue when going from 7.10 to 8.04. Then I read somewhere that I just needed to change a configuration file. I did it by using copy and paste and it solved my problem. But since I'm a noob (or an idiot :() I forgot the name of that file and the changes I made. 

Any ideas?

:confused:

---

### Post by markbuntu on 2009-01-18
After an update you sometimes need to reconfigure your sound since the settings you made have been replaced by defaults which may not work. If you have edited etc/modprobe.d/alsa-base to add specific options for you sound chip configuration you may need to do so again. You may also need to change the settings in System/Preferences/Sound and System/Preferences/Multimedia System Selector and System/Preferences/Default Sound Card since they may be defaulted to the wrong settings by the update.

You can just follow the directions for settings in the OP again or if you are having more difficulty go here where there is more extensive help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have not experienced this problem myself so the above is just a best guess. If someone who has experienced this problem figures out what happened and/or a way to fix it, please post your findings so we can help others. 

thanks
mark

---

### Post by ngohaibac on 2009-01-18
Thank you so much. Your tutorial really works well for my Ubuntu 8.10.

And I am really happy if I can translate your guide to Vietnamese language to help Vietnamese creative community, especially techical, IT students.

Best regards,

---

### Post by markbuntu on 2009-01-18
> **ngohaibac said:**
> Thank you so much. Your tutorial really works well for my Ubuntu 8.10.

And I am really happy if I can translate your guide to Vietnamese language to help Vietnamese creative community, especially techical, IT students.

Best regards,

I make these things to be shared as widely as possible and anything anyone can do to further that sharing is entirely welcome and does not need any permission from me or anyone else. So feel free to translate this or anything else I post into Vietnamese or any other language.

There is a much more extensive guide to troubleshooting and setting up sound in Ubuntu here, including UbuntuStudio which may be of especial interest for the creative community

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

There is also an overview of the Ubuntu sound system here that may be of interest to the technical community. It explains how all the different parts of the sound system operate and interact together


[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

Once again, feel free to translate these.

regards,
mark

---

### Post by kenworth on 2009-01-18
I'm a bit of a noob and avoid compiling in case things don't go well.

I had similar problem upgrading to 8.10 from 8.04 on my dell laptop using the alternate CD. Sound disappeared and I had no soundcard detected.The kernel that came with the alternate CD was 2.6.25-2-386.

I used some of the information in this thread but the process that got me working was to install the latest kernel (2.6.27-9-generic). It seems the alternate CD kernel was missing startup processes that identify and initialize the soundcard.

I was able to use synaptic to install the kernel.

Once I upgraded the kernel I got the startup bongos and was able to get things working.

Hope this helps someone out there.

Still have issues with my USB wireless, but everything else now working. I am disappointed that 8.10 upgrade has been such a mission.

---

### Post by markbuntu on 2009-01-18
It is good practice to get all the updates before doing anything else after an initial install because the iso was frozen before release and many critial problems were not discovered and fixed until after.

Your post is a good reminder that shows why updates are necessary and I have added a note in the OP about updates.

thanks,
mark

---

### Post by AmadeusOK on 2009-01-19
> **markbuntu said:**
> After an update you sometimes need to reconfigure your sound since the settings you made have been replaced by defaults which may not work. If you have edited etc/modprobe.d/alsa-base to add specific options for you sound chip configuration you may need to do so again. You may also need to change the settings in System/Preferences/Sound and System/Preferences/Multimedia System Selector and System/Preferences/Default Sound Card since they may be defaulted to the wrong settings by the update.

You can just follow the directions for settings in the OP again or if you are having more difficulty go here where there is more extensive help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have not experienced this problem myself so the above is just a best guess. If someone who has experienced this problem figures out what happened and/or a way to fix it, please post your findings so we can help others. 

thanks
mark

Mark: 

I'm still looking for a solution to my problem to no avail. I've tried many different things but nothing seems to work in my case. :(

Anyway thanks a lot for all the useful information you're posting on a regular basis. You're helping many people with their sound issues. :)

---

### Post by Anthony T. on 2009-01-19
you are my god, thank you very much i can talk on skype right now.

---

### Post by Roasted on 2009-01-19
> **Anthony T. said:**
> you are my god, thank you very much i can talk on skype right now.

What helped? The first post of this thread? Or something else along the way? I need to figure out my skype mic issue too... What did you do to fix it?

---

### Post by davidself1001 on 2009-01-21
I have system sounds and I can hear audio from amorak, mplayer, etc but I cannot get sound from my youtube or any other firefox video (only tried youtube and dailymotion).  I went thru the full re-install in this guide as well as the Comp mm/video thread as recommended but still no audio in firefox.  Any ideas on that one?

---

### Post by Roasted on 2009-01-22
What codecs did you install, exactly? Can you remember?

---

### Post by davidself1001 on 2009-01-22
I followed the procedure specified at the beginning of this thread.  And also I followed the MM and Video procedure for Intreped as well.  I used the second option for player install.  Actually I installed option 1 and then option 2 from that how to (ie MM and Video).  I have playback on Amorak and I have system sounds just no sound on FF when viewing youtube, etc.  I have tried to set the app for flashvideo in FF to both mplayer and the flashplayer that is listed in the Applications tab under preferences.

---

### Post by markbuntu on 2009-01-22
On way to check and application is to open the pulseaudio volume control (pavucontrol) and then open the application and see if it appears in playback. If it does, make sure the volume sliders are turned up and it is not muted. You can click on the mute icon to see how it works. If the application seems to be playing but you cannt hear anything right click on the stream and see if it is using the correct device, If not choose move stream and select the correct device.

If the application does not appear in pavucontrol then it is trying to use a different sound server like alsa or oss and you have a configuration problem. If the application has the option, choose pulseaudio or alsa for sound output. You can also go back to the OP and make sure you followed all the steps and installed all the packages.

---

### Post by pushin50 on 2009-01-22
Great post! One of the most useful I've seen. Tickety-boo thanks to you. If the forum had a "thank you" tool going right now, I'd give you one.

---

### Post by pushin50 on 2009-01-22
I'm referring to markbuntu's initial post in this thread. Excellent.

---

### Post by davidself1001 on 2009-01-22
No satisfaction.  When I open the speaker volume panel I don't see FF or any other app running.  There aren't any options that I know of in FF for change from oss to alsa.  Other ideas?

---

### Post by davidself1001 on 2009-01-22
I just figured out that my speaker in the task bar is for the ALSA mixer.  I brought up the PA mixer and I still don't see an app when playing a youtube video but I do see an app if i play an mp3 in Amorak.

---

### Post by markbuntu on 2009-01-22
What do you have set in System/Preferences/Sound?

---

### Post by davidself1001 on 2009-01-22
I have auto in all but sound capture which is set to pulse audio.  I have my soundcard in default mixer tracks.  I have also tried settin all to pulse audio (other than default mixer tracks).  I use swiftfox but have the same issue in firefox as well.

---

### Post by davidself1001 on 2009-01-22
I did a pulseaudio -vv and get this error

W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Is that my issue?  If so, what do I need to do?

---

### Post by davidself1001 on 2009-01-22
Got audio in FF finally.  I had to set the PA sound prefs default mixer tracks to Cirrus Logic (OSS mixer) instead of my SB Live (Alsa mixer).  Not sure why that is?

---

### Post by umechanism on 2009-01-23
I have followed all the steps you suggested in this thread.  However, when I select the Pulseaudio icon then pick "Volume Control" the  "Output" tab shows "No Output Devices Available".  There is nothing to select.  What does this mean?

Here is my sound card.
```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, I tried killing PulseAudio (per the 10,000 page guide) and got this as a message:

michael@ubuntu-dell:~$ killall pulseaudio
michael@ubuntu-dell:~$ sudo killall pulseaudio
[sudo] password for michael: 
pulseaudio: no process killed
michael@ubuntu-dell:~$ 

This can't be good.


 Thanks!

---

### Post by markbuntu on 2009-01-23
> **davidself1001 said:**
> I have auto in all but sound capture which is set to pulse audio.  I have my soundcard in default mixer tracks.  I have also tried settin all to pulse audio (other than default mixer tracks).  I use swiftfox but have the same issue in firefox as well.

You need to set system/Preferences/Sound to pulseaudio or alsa instead of automatic. You also need to set the System/Preferences/Default Sound Card to pulse. That is why ff is using oss. It is all in the OP.

---

### Post by markbuntu on 2009-01-23
> **umechanism said:**
> I have followed all the steps you suggested in this thread.  However, when I select the Pulseaudio icon then pick "Volume Control" the  "Output" tab shows "No Output Devices Available".  There is nothing to select.  What does this mean?

Here is my sound card.
```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, I tried killing PulseAudio (per the 10,000 page guide) and got this as a message:

michael@ubuntu-dell:~$ killall pulseaudio
michael@ubuntu-dell:~$ sudo killall pulseaudio
[sudo] password for michael: 
pulseaudio: no process killed
michael@ubuntu-dell:~$ 

This can't be good.


 Thanks!

Are you using KDE by any chance?

---

### Post by umechanism on 2009-01-23
> **markbuntu said:**
> Are you using KDE by any chance?

No.  I am using Ubuntu 8.10.  Sorry - should have told you my specs in the first place.  I looked in the ALSA Wiki for supported cards and did not see my Realtec ALC888 (Intel).  Does this mean that I'll never get sound to work?

I'll switch to Kubuntu if that is what it takes.

---

### Post by markbuntu on 2009-01-23
I have an ALC888 on my machine and it works just fine for me on Intrepid and Hardy, I didn't have to do anything. I also have an ati hdmi device on my gpu like you do.

That message means that pulseaudio has crashed which is weird becase the pavucontrol should have given you an unable to connect error when you opened it.
Did you reboot after folowing the guide?
That is sometimes necessary but not always which is also sort of weird.

What is your machine?

---

### Post by umechanism on 2009-01-23
> **markbuntu said:**
> I have an ALC888 on my machine and it works just fine for me on Intrepid and Hardy, I didn't have to do anything. I also have an ati hdmi device on my gpu like you do.

That message means that pulseaudio has crashed which is weird becase the pavucontrol should have given you an unable to connect error when you opened it.
Did you reboot after folowing the guide?
That is sometimes necessary but not always which is also sort of weird.

What is your machine?

I am so glad to hear that someone has this chip working in Ubuntu!  Whew!

Ok, My computer is a Dell Studio SMT-116B like this one  [http://www.bestbuy.com/site/olspage.jsp?skuId=9016986&type=product&id=1218008593628](http://www.bestbuy.com/site/olspage.jsp?skuId=9016986&type=product&id=1218008593628)

Would you mind telling me how you have all of your sound preferences configured?

Thank you!

---

### Post by wyrless2002 on 2009-01-24
Thank You for Your Time! This was the soulution to my problem as well!

-Aaron

---

### Post by umechanism on 2009-01-24
> **markbuntu said:**
> I have an ALC888 on my machine and it works just fine for me on Intrepid and Hardy, I didn't have to do anything. I also have an ati hdmi device on my gpu like you do.

That message means that pulseaudio has crashed which is weird becase the pavucontrol should have given you an unable to connect error when you opened it.
Did you reboot after folowing the guide?
That is sometimes necessary but not always which is also sort of weird.

What is your machine?

Oh, and yes I did reboot.  Several times but it did not help.

Thank you.

---

### Post by umechanism on 2009-01-25
Bumping - out of desperation.

---

### Post by umechanism on 2009-01-25
> **markbuntu said:**
> I have an ALC888 on my machine and it works just fine for me on Intrepid and Hardy, I didn't have to do anything. I also have an ati hdmi device on my gpu like you do.

That message means that pulseaudio has crashed which is weird becase the pavucontrol should have given you an unable to connect error when you opened it.
Did you reboot after folowing the guide?
That is sometimes necessary but not always which is also sort of weird.

What is your machine?

I've discovered an oddity.  Typing "dmseg" after bootup displays a long list of "events" that happen during bootup.  I found this message regarding my soundcard:
```
[   13.049258] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.083143] hda_codec: Unknown model for **ALC883**, trying auto-probe from BIOS.
```

Why does list it an ALC883 when I have an ALC888?  Maybe this is part of my problem?

---

### Post by markbuntu on 2009-01-25
There are some threads around here about the dell studio. You should do a search for them. Dell does a lot of tweaking to the hardware so most likely you need to add some option in your etc/modprobe.d/alsa-base file to get it working.

---

### Post by umechanism on 2009-01-25
> **markbuntu said:**
> There are some threads around here about the dell studio. You should do a search for them. Dell does a lot of tweaking to the hardware so most likely you need to add some option in your etc/modprobe.d/alsa-base file to get it working.


:popcorn::popcorn::popcorn::popcorn:

Yes!!!  I searched for "Dell Studio" (duh) and found this thread:
[http://ubuntuforums.org/showthread.php?t=969611](http://ubuntuforums.org/showthread.php?t=969611)

I install the suggested code and rebooted.  I heard a "Pop" in my speakers but still no sound so I knew I was getting somewhere.  I then followed your suggestions at the beginning of this thread (tweaking Pulse Audio).  I got all the way down to the part where you suggested to open the pulse audio volume manager and verify the audio stream is playing through the correct device.  I switched the steams and BAM!!!!  Music is now playing through my speakers as I type this!

Woot! Woot! :popcorn:

Thank you for the effort and time you put into making your knowledge available to all!

---

### Post by davidself1001 on 2009-01-26
> **davidself1001 said:**
> Got audio in FF finally.  I had to set the PA sound prefs default mixer tracks to Cirrus Logic (OSS mixer) instead of my SB Live (Alsa mixer).  Not sure why that is?
I just thought I had this resolved.  today without changing anything I am back to having no audio in FF but have it everywhere else.  This is getting old.  I have tried changing settings in pref sounds, in the PA volume control and the Cirrius Volume panel.  Any other suggestions?

---

### Post by umechanism on 2009-01-26
> **davidself1001 said:**
> I just thought I had this resolved.  today without changing anything I am back to having no audio in FF but have it everywhere else.  This is getting old.  I have tried changing settings in pref sounds, in the PA volume control and the Cirrius Volume panel.  Any other suggestions?

Well, I still have no sound in Firefox but I'm picking my battles one at a time.  I have sound streaming from last.fm and can play music from CD's whereas I could not before.  I call that a victory but not the end of the battle.

I will attack Firefox next.

---

### Post by markbuntu on 2009-01-27
Which flash version are you guys using, is it the one you get with the ubuntu-restricted-extras package?

---

### Post by davidself1001 on 2009-01-27
I followed the instructions provided at the beginning of this thread as a first pass fix.  I had Flashwave 10 prior to doing that but it wasn't working then either.  As said earlier I managed to get it working for one day by changing the playback to an OSS Cirrus mixer but now that stopped working.

---

### Post by umechanism on 2009-01-27
> **markbuntu said:**
> Which flash version are you guys using, is it the one you get with the ubuntu-restricted-extras package?

I'm using "flashplugin-nonfree   10.0.15.3ubuntu1~intrepid1", "adobe-flashplugin  10.0.15.3-1intrepid2" and "flashplugin-nonfree-extrasound  0.0.svn2431-3".  This is according to what Synaptic says I have installed.  Is this correct?

Thanks.

---

### Post by davidself1001 on 2009-01-27
That matches what I had but I have since removed pulseaudio and now my youtube audio is working again.  based on all the pulseaudio issues i see on this board i assume there must be a systemic problem with it.  i'll wait and try it again in 9.04 hopeing something gets fixed.  Assuming i need it at all.

---

### Post by Roasted on 2009-01-27
Is pulse projected to be a POS in Jaunty too? Or is there hope?

---

### Post by umechanism on 2009-01-27
> **davidself1001 said:**
> That matches what I had but I have since removed pulseaudio and now my youtube audio is working again.  based on all the pulseaudio issues i see on this board i assume there must be a systemic problem with it.  i'll wait and try it again in 9.04 hopeing something gets fixed.  Assuming i need it at all.

Ahh crap.  Don't tell me that I have to uninstall Pulseaudio to get Youtube audio working.  I just got Pulse playing cd's and last.fm.  Tell me it is not so!](*,)

---

### Post by markbuntu on 2009-01-28
Well, I am using the flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1 on Intrepid amd64 and have no problems at all with it and pulseaudio on youtube or anywhere else.

The most likely problem that you people are having is that you did not follow all the directions in the OP or are using a bad flashplayer. 

It is critical to set System/Preferences/Sound to Pulseaudio Sound Server and not to automatic. It is also critical to set the System/Preferences/Default Sound Card to PulseAudio. You also need all the packages in the lists and need to be fully updated.

Failure to follow these steps will result in exactly the problems you are having.

And yes, PulseAudio is in Jaunty. Right now it is pulseaudio 0.9.13 but will most likely be 0.9.15 which is the next stable release.

---

### Post by stwschool on 2009-02-03
Thank you for this thread, it made my life so much easier :)

---

### Post by skootar on 2009-02-08
I make it as far as this line of the instructions:

"If any of the above is giving you problems, try rebooting."

Using 8.10, I followed the instructions line for line. I rebooted, and there are still no devices listed in the sound chooser. My card is detected, I have the login drum sound, and had oss sound in the xmms program before I started with these instructions. No sound in flash 10 however.

Since I had the drum sound I reasonably assumed it was a software problem.

There are 12 choices for output device in sound preferences. Only oss sound plays the test tone.

I have a turtle beach santa cruz sound card on an abit kr7a motherboard.


00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0d.0 SCSI storage controller: Adaptec AHA-2940U/UW/D / AIC-7881U
00:0f.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:13.0 RAID bus controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

---

### Post by Sprax on 2009-02-10
Thank you! Works great!

---

### Post by satx on 2009-02-19
Many thanks! I installed USB speakers and webcam w/mic and was having fits after every reboot. All is well now thanks to your most excellent post.

SATX

---

### Post by RavanH on 2009-02-22
Excellent how-to ! Thanks :)

Small suggestion to make it even easier: maybe provide one single copy-paste command to get all packages in one go?

```
sudo apt-get install asoundconf-gtk gnome-alsamixer alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras
```

---

### Post by yaz360 on 2009-02-22
plz people HELP!!! im going nuts here. i have tried everything im not sure even if im doing it right.. i just installed ubuntu on my hp touchsmart... tried everything nothing worked for me !! i reached till the end in your tutorial but unfortunately but it did not work!! 





plzzzzzzzzzzz help !!!

---

### Post by markbuntu on 2009-02-22
> **RavanH said:**
> Excellent how-to ! Thanks :)

Small suggestion to make it even easier: maybe provide one single copy-paste command to get all packages in one go?

```
sudo apt-get install asoundconf-gtk gnome-alsamixer alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras
```

Well, that might make things a little faster and easier for experienced users but may be a little daunting to new users. That is why I recommend using Synaptic and doing one step at a time and explaining what each package is for. 

It is my opinion that more is learned by taking one step at a time and explaining things. People get a deeper understanding and need less help.

---

### Post by stoneage on 2009-02-22
Hi, markbuntu, I don't suppose you know anything about Totem do you?

I just did a clean install of 8.10 and I get no sound from Totem, though VLC, Mplayer and SMPlayer are all fine. 

Totem has plugins, like the one for the BBC, and firefox uses Totem to stream video, so I'd like to fix it. 

I did copy some .dirs from the Hardy home directory to Intrepid, but the only Totem .dir I can find is .gstreamer-0.10 and that one isn't the problem, so I'm wondering if it is a codec thing.

Any ideas ?

---

### Post by markbuntu on 2009-02-22
You probably just need the rest of the gstreamer packages and need to set up gstreamer in System/Preferences/Multimedia Systems Selector which is the gstreamer settings app.

---

### Post by stoneage on 2009-02-22
I have these gstreamer packages:-
> 
gstreamer0.10   -alsa
gstreamer0.10	-ffmpeg
gstreamer0.10	-gnomevfs
gstreamer0.10	-plugins-bad
gstreamer0.10	-plugins-bad-multiverse
gstreamer0.10	-plugins-base
gstreamer0.10	-plugins-base-apps
gstreamer0.10	-plugins-good
gstreamer0.10	-plugins-ugly
gstreamer0.10	-pulseaudio
gstreamer0.10	-schroedinger
gstreamer0.10	-tools
gstreamer0.10	-x
gstreamer0.10	-0
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-base0.10-dev

I have tried some other settings for System/Preferences/Multimedia Systems Selector but it is still silent. Currently it is on Autodetect but I have tried Pulseaudio and ALSA (Similar to the way it was set up for Hardy) but to no avail. All other sounds are working.

The volume icon on Totem is greyed out and unselectable. 

I don't know if it is related, but when I open Gnome Alsamixer I get this error:-
> Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'There don't seem to be any directories of that name so maybe it is safe to ignore it ?

There are so many sound related functions, I'm not sure where to look:
Multimedia Systems Selector
Sound
Pulseaudio Device Chooser
Pulseaudio Manager
Pulseaudio Volume Control
Volume Control

Forgive my ignorance, it probably seems easy when you know how.

---

### Post by saygin on 2009-02-22
thank you! that was all I need for ubuntu!

---

### Post by markbuntu on 2009-02-22
> **yaz360 said:**
> plz people HELP!!! im going nuts here. i have tried everything im not sure even if im doing it right.. i just installed ubuntu on my hp touchsmart... tried everything nothing worked for me !! i reached till the end in your tutorial but unfortunately but it did not work!! 





plzzzzzzzzzzz help !!!

At the end of the OP there is a link to a very comprehensive troubleshooting guide. You should maybe try that.

---

### Post by markbuntu on 2009-02-22
> **stoneage said:**
> I have these gstreamer packages:-


I have tried some other settings for System/Preferences/Multimedia Systems Selector but it is still silent. Currently it is on Autodetect but I have tried Pulseaudio and ALSA (Similar to the way it was set up for Hardy) but to no avail. All other sounds are working.

The volume icon on Totem is greyed out and unselectable. 

I don't know if it is related, but when I open Gnome Alsamixer I get this error:-
There don't seem to be any directories of that name so maybe it is safe to ignore it ?

There are so many sound related functions, I'm not sure where to look:
Multimedia Systems Selector
Sound
Pulseaudio Device Chooser
Pulseaudio Manager
Pulseaudio Volume Control
Volume Control

Forgive my ignorance, it probably seems easy when you know how.

You should get rid of those ~/.dirs from Hardy.

---

### Post by stoneage on 2009-02-22
Well, do I look like an idiot now.......

I thought I had been careful, but I take them all out and it works. I think I found the culprit though - .config/totem

Thanks again for your time and patience.

---

### Post by rahunar on 2009-02-24
Hi markbuntu,

Thanks very much. Your sound installation steps solved everything and I am able to hear everything in my usb headphones. I have searched many threads but no one seems to have formulated such a nice set of instructions. The *pulseaudio device chooser* did the trick. Thanks a lot..............

---

### Post by id3379 on 2009-02-27
This was just what i needed, had it fixed in 3 minutes, thanks!

---

### Post by toejamfootball on 2009-03-01
I have installed all the packages but get stuck when it comes to opening volume control in PulseAudio. It comes up saying, Error, connection Faile: Connection Refused. I am running Xubuntu, and am having trouble getting 5.1 surround sound. I had a Realtek audio driver for my onboard sound when running Windows.

Thanks.

---

### Post by whitewraith on 2009-03-01
:confused:

Ok i have ubuntu 8.10 and i have the latest of wine and all that stuff. I am new to ubuntu so im not well educated in it but want to. I have a 5.1 speaker sistem and my dound card is Dynex. yeah i know its a poor card but hey. Anyway the problem is this, I have sound on all speakers but the center. I have to turn all cvalumes up to hear the sound. I know if the center one is working right there is no need to turn everything up so loud. 


Please help me get the full system working

---

### Post by markbuntu on 2009-03-01
There is a section on surround sound here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by terminous on 2009-03-06
Not exactly sure but I had to do the same with Debian 5 i386, bigmem & amd64. Works fine now.

---

### Post by jocheem67 on 2009-03-07
I'm trying by no means here to be negative, to rant or anything.....but....

I've been trying to get my hercules RMX dj-console to work in Intrepid, to no avail, until I uninstalled Pulse.

Using just alsa lets me select my RMX now through 'asoundconf set-default-card RMX'

In 'system-preferences-sound' I select alsa as backend and got it to work after a lot of trying with pulse installed and enabled...

I'm not trying to start a endless discussion here by the way, but I do feel that uninstalling pulse can also be a solution to soundproblems.

JFYI;)

---

### Post by markbuntu on 2009-03-07
> **jocheem67 said:**
> I'm trying by no means here to be negative, to rant or anything.....but....

I've been trying to get my hercules RMX dj-console to work in Intrepid, to no avail, until I uninstalled Pulse.

Using just alsa lets me select my RMX now through 'asoundconf set-default-card RMX'

In 'system-preferences-sound' I select alsa as backend and got it to work after a lot of trying with pulse installed and enabled...

I'm not trying to start a endless discussion here by the way, but I do feel that uninstalling pulse can also be a solution to soundproblems.

JFYI;)

Are you using jack?

---

### Post by Jim.uff on 2009-03-08
I will ask my question and hope for the best. I have spent a lot of time chasing around the various details of fixes and feel close....... yet the cigar is elusive. 

I have zero sound with Intel HDA and Realtek ALC 268. I have read through and tried to get all the packages but cannot find non-free-codecs so don't have that. Not sure how to enable mediubuntu which may lead to the codecs not being found. Got in all the other 'good' packages and punted the bad. 

I am to the point where streaming radio in rhythmbox if I go to the pulse audio icon for the applet I see input coming through on the pulse audio volume meter. However on the pulse audio volume control under playback, input devices and output devices I have red x's on the speakers. If I click the speakers the text fades as if that is when it should be muted. When I click again the text comes bold again but the red x remains. 

Anyone who could help that would be much appreciated. 


ps sound is fine in XP and the laptop is a Dell Vostro 2510.

Thanks

---

### Post by umechanism on 2009-03-08
> **Jim.uff said:**
> I will ask my question and hope for the best. I have spent a lot of time chasing around the various details of fixes and feel close....... yet the cigar is elusive. 

I have zero sound with Intel HDA and Realtek ALC 268. I have read through and tried to get all the packages but cannot find non-free-codecs so don't have that. Not sure how to enable mediubuntu which may lead to the codecs not being found. Got in all the other 'good' packages and punted the bad. 

I am to the point where streaming radio in rhythmbox if I go to the pulse audio icon for the applet I see input coming through on the pulse audio volume meter. However on the pulse audio volume control under playback, input devices and output devices I have red x's on the speakers. If I click the speakers the text fades as if that is when it should be muted. When I click again the text comes bold again but the red x remains. 

Anyone who could help that would be much appreciated. 


ps sound is fine in XP and the laptop is a Dell Vostro 2510.

Thanks

Under the playback tab, right click on the stream that is playing and select "change stream" which allows you to pick different devices to direct the sound through.  Once set, it stays set.

---

### Post by osarusan on 2009-03-09
Hey! Thanks for this thread! You got my USB headset to work just the way I wanted. Now I can use Skype and other audio through my headset at the same time. A million kudos to you!

---

### Post by zevans on 2009-03-09
> **toejamfootball said:**
> I have installed all the packages but get stuck when it comes to opening volume control in PulseAudio. It comes up saying, Error, connection Faile: Connection Refused. I am running Xubuntu, and am having trouble getting 5.1 surround sound. I had a Realtek audio driver for my onboard sound when running Windows.


Pulseaudio relies on a daemon/server in the background, and this must be started for audio to work. Xubuntu may be broken in the same way that my KDE installs are - Pulseaudio doesn't start automatically.

Can someone advise where this "should" be started from - I noticed a script 70pulseaudio in /etc/X11/Xsession.d which I suppose gets started automatically from somewhere, but the script appears to check for Gnome, and if you don't have Gnome, it won't do anything. Seems a bit unfair on us KDE types!

---

### Post by markbuntu on 2009-03-09
If you are using KDE4 you should read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by dougcumiskey123 on 2009-03-09
What does this mean.

doug@doug-laptop:~$ "lspci -v | less
>

At his point the terminal has crashed..

---

### Post by Jim.uff on 2009-03-10
> **umechanism said:**
> Under the playback tab, right click on the stream that is playing and select "change stream" which allows you to pick different devices to direct the sound through.  Once set, it stays set.

In volume control under the playback tab I have '**show**' and choices like 'all streams', 'applications' and 'virtual streams'. Don't get anything right clicking. Am I in the wrong place?

---

### Post by zevans on 2009-03-10
> **markbuntu said:**
> If you are using KDE4 you should read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

...which says

[QUOTE=syniurge]As of KDE 4.2 (available in the backports), the only thing needed to get PulseAudio working within KDE is making "pulse-session" run before KDE launches using the following command in a terminal:
Code:

```
cp /usr/bin/pulse-session ~/.kde/env/pulse-session.sh
```

Then after restarting KDE, Phonon devices(not just the "PulseAudio" device) will map to PulseAudio devices instead of ALSA devices.[/quote]

That's the missing info I was looking for, thanks. Like they say in that thread, starting pulseaudio -D from somewhere in the autostart directories is TOO LATE, and Phonon will complain and fall back to ALSA before pulseaudio gets a chance to start. This way kde kicks it off nice and early.

Does Jaunty include an init.d script for a system-wide pulseaudio startup?

---

### Post by markbuntu on 2009-03-10
> **zevans said:**
> ....

Does Jaunty include an init.d script for a system-wide pulseaudio startup?

Pulse is still not very finalized in Jaunty yet but it does start automatically with gnome, I am not sure about kubuntu jaunty, I would imagine not though.

---

### Post by hoboken on 2009-03-12
Saved this tutorial somewhere I'll never lose it. 

Thanks very much.

---

### Post by SyberKowboy on 2009-03-12
Is anyone having issues with pulse or alsa after resume from suspend. For some reason ALSA goes dead after I resume from a suspend. So far the only I've found that works is sudo alsa force-reload and I get a couple errors but the audio comes back. It is bugging me and I'd like to fix it.

---

### Post by zevans on 2009-03-13
> **SyberKowboy said:**
> Is anyone having issues with pulse or alsa after resume from suspend. For some reason ALSA goes dead after I resume from a suspend. So far the only I've found that works is sudo alsa force-reload and I get a couple errors but the audio comes back. It is bugging me and I'd like to fix it.

Lots of audio chipsets seem to struggle with ACPI, seen this on dozens of Windows laptops. Luckily linux has a method to force whatever is needed to reinit sound on a "resume."

Scripts in /etc/acpi/resume.d run on resume, kinda like /etc/init.d works for startup. Mine looks like this:

```

#!/bin/sh

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
  /etc/init.d/alsa-utils start
fi

```

If yours is missing, that may the problem, or if "alsa-utils start" isn't enough you could always edit in your "alsa force-reload" instead.

---

### Post by RichardCain on 2009-03-14
Thanks a lot for this tutorial.  My sound's working a treat now!!

---

### Post by Teabicky on 2009-03-19
Thanks!!! Every thing's fixed.  Must be witch craft.

---

### Post by wbee on 2009-03-19
Mark,

I see your private messages ignored disclaimer,so here is the thank you note.:-)

I will read this and the other guide referred to and hope it solves my tv tuner card's lack of audio---which is the only issue unresolved before I clean install and say goodbye to Windows.

Thank you.

-----------

Woody

---

### Post by ksamualtolch on 2009-03-23
Your tutorial is much appreciated, but unfortunately i still have no sound.  Everything appears to be working properly, my soundcard is present and drivers are compatible.  The playback tab in the pulseaudio volume control applet indicates that Amarok is playing.  Am I missing something?  

//many thanks

---

### Post by ksamualtolch on 2009-03-23
Ok, here's an update.  I got my sound working, everything was fine.  When I rebooted there was no sound.

Here's my system info:

System Info

lspci:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
04:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

lsusb:

Bus 003 Device 002: ID 0d49:7250 Maxtor 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards:

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with unknown codec at 0xc0503400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0503800, irq 17

cat /proc/asound/modules:

0 snd_atiixp
 1 snd_atiixp_modem

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l:

**** List of CAPTURE Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



thnx

---

### Post by orethrius on 2009-03-23
I might've guessed that it'd be the atiixp.  I'm running one myself, hence why I'm trying to consolidate new postings regarding it into the ALSA workaround listed below.  Perhaps I should add it to my sig?

[http://ubuntuforums.org/showthread.php?t=826941](http://ubuntuforums.org/showthread.php?t=826941)

---

### Post by markbuntu on 2009-03-23
I wrote that quite a while ago and have since had success with the attixp with Hardy and Intrepid using pulseaudio. I also upgraded my entire system so that mobo is hardly ever used anymore.

I seem to remember having to add this line to the end of my /etc/modprobe.d/alsa-base file.

options snd-atiixp ac97_quirk

These are the notes on the ac97_quirk option from the /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz file that is on your computer.


AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

---

### Post by redenex on 2009-03-25
> **yaz360 said:**
> plz people HELP!!! im going nuts here. i have tried everything im not sure even if im doing it right.. i just installed ubuntu on my hp touchsmart... tried everything nothing worked for me !! i reached till the end in your tutorial but unfortunately but it did not work!! 





plzzzzzzzzzzz help !!!

That is where I am too. HP TouchSmart, but no sound!!! Just came across this thread, let me see if this can guide me. :confused:

---

### Post by umechanism on 2009-03-25
I highly recommend this link as well.  It tells how to install everything you need to fix Pulse Audio some of which are covered in MarkBuntu's tutorial.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by zabudarda on 2009-03-25
Great, got it working. thanks buddy

---

### Post by thatsmyboy on 2009-03-26
Thanks for all your help in this. In my opinion GNU/linux really struggles with audio so any help you provide is golden!

---

### Post by Yeti can't ski on 2009-03-26
Hello all,

I have a Dell XPS M1330 with HDA Intel. I was using Hardy for a while and then it went completely mute. Not sure if it was after using skype use or doing an update. I struggled with all kinds of threads, guides, updates and so on. No result. I also excluded hardware problems using a GNewSense livedisk. 

I then decided to anticipate the upgrade to Jaunty to solve the problem. I did it and, frustratingly enough, still had no sound. 

When I was already certain that I had to do a reinstall (it would be a disaster for me ](*,)), it just started to work.  

I did so many things to address the problem that it is hard to tell precisely what finally sorted out the issue, but I think it was either one of these two things: 

(i) the installation of this package with Synaptic: 

asoundconf-gtk

(ii) some tweaking with gnome-alsamixer, which is indeed much better than regular alsamixer. 

gnome-alsamixer

Anyway, I am tired and greatly relieved and now I going to listen to some music. :P

Sorry for the useless post and thanks to everyone, in particular to Markubuntu.

---

### Post by sphynx_25 on 2009-03-28
I think something might be really wrong here. I've been following your guide when I got up to this part in the third paragraph of the Getting Started section:

> This will open the Pulse Audio Volume Control. Go to Output Devices and see if your sound card is there, it will be listed as ALSA PCM on front:...(ALC8 via DMA or whatever your sound card is.

Unfortunately, instead of seeing my sound card listed there's "no output devices available" appearing there. I've tried rebooting but it made no difference.

Also, if I try to play music or videos in a media player (I've tried rhythmbox, totem, dragon player, elisa media centre) the slider does not move at all and the program will then invariably stop responding. Are these problems connected at all?

Any advice?

---

### Post by markbuntu on 2009-03-29
> **sphynx_25 said:**
> I think something might be really wrong here. I've been following your guide when I got up to this part in the third paragraph of the Getting Started section:



Unfortunately, instead of seeing my sound card listed there's "no output devices available" appearing there. I've tried rebooting but it made no difference.

Also, if I try to play music or videos in a media player (I've tried rhythmbox, totem, dragon player, elisa media centre) the slider does not move at all and the program will then invariably stop responding. Are these problems connected at all?

Any advice?

Was you sound working at all when you started?
You can go here which has more extensive troubleshooting help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sphynx_25 on 2009-03-29
I bought this new pc about two weeks ago now and installed intrepid then. Unfortunately, I have still never heard any sound on it. Thanks for the link, I'll give it a go.

---

### Post by James1375 on 2009-03-29
[QUOTE=markbuntu;6278623]** Intrepid 8.10 Sound Solution**
**also works with Hardy Heron 8.04 and Jaunty Jackalope 9.04**
** with multimedia support**

If you have just upgraded to or installed Intrepid or Hardy or Jaunty and you have some sound somewhere, but not everywhere for everything, this is a fast way..................

After Upgrading to Intrepid I lost all streaming Mozilla sound!!!!

After walking through the above thread????:
:lolflag: I can't get over how easy it is to manage my linix box.

Thanks for all your help.  And thank you Markbuntu!!! I've never had to query you directly for following your thread posts have helped me twice now!

---

### Post by Robert Leithe on 2009-03-30
I haven't had sound under Ubuntu since I bought my new laptop (HP Pavillion HDX) in May 2008. I was running Ubuntu 8.04 at the time, but was forced back to Windows in order to get sound working :(
Tried 8.10 when it was released, and then every alpha of 9.04 but still no sound.
When 9.04 hit beta, I gave it another shot. And to my indescribible joy there were sound when running the Live CD, through the headphones (not internal speakers, though). I decided to install, only to find out there was no sound after installation, either through headphones or internal speakers :confused:

After a little fiddling around I was able to get sound through headphones again, and then a little later, through the internal speakers. Oh joy :)
Unfortunately it was a short lived joy. I shut down my PC after a couple of days, and when I turned it back on today, there was no sound. Again :confused:

I followed the how-to in this forum thread, but am still not getting sound. I have captured various screen shots, in case anyone would like to see them. But the one that puzzles me is the Alsa Mixer (when I open a Terminal window, type "alsamixer" and press Enter). It shows only one column (whereas it showed several when the sound was working yesterday)... This column is labelled "Master".

Does anyone have any help to offer on this?

Sincerely
Robert Leithe

---

### Post by markbuntu on 2009-03-30
Well, sound on 9.04 is still an iffy proposition. It has been coming and going with updates now for months and there were some unfixed items before the beta freeze so.....updates are coming...and going and coming back.

In the past a lot of people who had sound with the live cd but not after install were able to get their sound back by making a new user and logging in with that. Something about initial user configs that was never really tracked down. You can also try making root and users memebers of the groups

pulse
pulse-rt
pulse-access

---

### Post by Robert Leithe on 2009-03-31
That wasn't too good news...

I made root and my user a memeber of the suggtested groups, but still no sound. However, the PulseAudio Volume Meter now indicates sound being played. It didn't yesterday...

Robert

---

### Post by markbuntu on 2009-03-31
If the volume meter is working then that means the driver is working etc. Now you need to open the pulseaudio volume control and see which output device the application stream is playing to. If you right click on the stream you can see this and change it. If you are using the correct output device check your speaker connections or try your headphones.

---

### Post by Robert Leithe on 2009-03-31
In the Volume Control, when I right click the picture under the tab "Playback" I have only one alternative under the menu item "Move Stream...", and that's "HDA Intel - STAC92xx Analog", and it's selected. This stream is the same as displayed in the PulseAudio Volume Meter. It says "Showing signal levles of HDA Intel - STAC92xx Analog". Everywhere I can think of looking, I find all sliders are set to around 90 % volume. None are muted...

---

### Post by markbuntu on 2009-03-31
Well, you are not the only one having that particular problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960)

---

### Post by supertappy on 2009-03-31
I have been following this excellent tutorial and get this far

> Go to Applications/Sound and Video and select Pulse Audio Device Chooser. This will put a little icon on the panel near the Panel Volume Control. Click on the new icon and choose Volume Control. This will open the Pulse Audio Volume Control. Go to Output Devices and see if your sound card is there, it will be listed as ALSA PCM on front:...(ALC8 via DMA or whatever your sound card is. If you have a usb device it will be listed as ALSA PCM on front:...(USB Audio) via DMA or something like that. **Make sure the sliders are up and the device is not muted**.

My device is muted, it has a red cross on the speaker icon if the button is selected or not

[http://www.adam.com.au/nickstacey/VolumeControl.png]("http://www.adam.com.au/nickstacey/VolumeControl.png")

It's an on board sound card, and works ok in xp. It has never worked in ubuntu.

these are the playback devices, version 8.10

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

I an post pictures of all steps of the tutorial up to this point if it is of help

---

### Post by Robert Leithe on 2009-04-01
I have sound again :)

Under Volume Control and the tab called "Switches", I had to check "Line In as Output"...

---

### Post by markbuntu on 2009-04-01
> **supertappy said:**
> I have been following this excellent tutorial and get this far



My device is muted, it has a red cross on the speaker icon if the button is selected or not

[http://www.adam.com.au/nickstacey/VolumeControl.png]("http://www.adam.com.au/nickstacey/VolumeControl.png")

It's an on board sound card, and works ok in xp. It has never worked in ubuntu.

these are the playback devices, version 8.10

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

I an post pictures of all steps of the tutorial up to this point if it is of help

That is the normal appearance of the volume control and it looks like the sound is not muted. Have you treid playing anything?

---

### Post by markbuntu on 2009-04-01
> **Robert Leithe said:**
> I have sound again :)

Under Volume Control and the tab called "Switches", I had to check "Line In as Output"...

Well that is sort of strange but it does not really surprise me that a laptop manufacturer would use that switch. Many surround sound cards have a similar switch for side or rear outputs.

But why it is default to line out, that is the mystery. Maybe you could make a comment at the bug report so the devs can see what you have found and maybe fix it.

Anyway, It is good to see you have got your sound back.

---

### Post by supertappy on 2009-04-02
> **markbuntu said:**
> That is the normal appearance of the volume control and **it looks like the sound is not muted**. Have you treid playing anything?

Yes I tried an mp3 without any sound. I think it is muted though. It has the red circle with the line through it. If you go to volume control say for playback on the speaker icon on the top right of the desktop if you click the speaker button it mutes like that, if you un click it the red cross disappears. It does not dissapear in the pulse audio applet.

---

### Post by markbuntu on 2009-04-02
What version of ubuntu are you using?

---

### Post by supertappy on 2009-04-02
> **markbuntu said:**
> What version of ubuntu are you using?

8.10 with a fairly new motherboard GA-MA790X-DS4 and cpu, a phenom, six months old.

I can post pics of all the steps so far in the tutorial if it's helpfull

---

### Post by markbuntu on 2009-04-02
You need to go here. There is better basic troubleshooting help. Also, there was some problems with GA boards that were fixed with a bios update so you might want to consider that as a last resort.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by adamthorne on 2009-04-04
I am interested to know if anyone has had problems persist with USB after this process. My sound output and input is now working fine from the soundcard and I can select USB as a stream in Pulse audio but it's just silent :( I have tested the headset on a Windows machine and no problem there. 

I'm running 8.10 on a  laptop with onboard soundcard SIS SI7012. The usb plantronics headset is recognised as C-USB. 

The only potential anomaly I have identified is that in Sound Preferences and Volume Control Panel I have SiS SI7012 however in GNOME ALSA Mixer it recognizes the soundcard as Realtek ALC203. I can nominate that in Sound Preferences but only as Realtek ALC203 (OSS).

Any ideas?

---

### Post by BangorOrBust on 2009-04-04
Quick question,
I've installed the packages and when you say "Go to System/Preferences/Default Sound Card and choose pulseaudio." I don't see Default Sound Card there, maybe I did something wrong or maybe its not important.  I'm not sure, but being a new user I want to make sure I do it right.  Is there another way to set the default sound card?

---

### Post by markbuntu on 2009-04-05
> **adamthorne said:**
> I am interested to know if anyone has had problems persist with USB after this process. My sound output and input is now working fine from the soundcard and I can select USB as a stream in Pulse audio but it's just silent :( I have tested the headset on a Windows machine and no problem there. 

I'm running 8.10 on a  laptop with onboard soundcard SIS SI7012. The usb plantronics headset is recognised as C-USB. 

The only potential anomaly I have identified is that in Sound Preferences and Volume Control Panel I have SiS SI7012 however in GNOME ALSA Mixer it recognizes the soundcard as Realtek ALC203. I can nominate that in Sound Preferences but only as Realtek ALC203 (OSS).

Any ideas?

Well, I have a plantronics usb headset and it works fine for me except for a little  glitchy volume control which is a common usb driver issue. Did you check the levels in the pavucontrol and on the headset?

---

### Post by markbuntu on 2009-04-05
> **BangorOrBust said:**
> Quick question,
I've installed the packages and when you say "Go to System/Preferences/Default Sound Card and choose pulseaudio." I don't see Default Sound Card there, maybe I did something wrong or maybe its not important.  I'm not sure, but being a new user I want to make sure I do it right.  Is there another way to set the default sound card?

If you are using Intrepid or Jaunty the default is already set so asoundconf-gtk is sort of redundant. Did you reboot?

---

### Post by Dillio187 on 2009-04-07
has anyone gotten the audio output on the Dell E Series docking ports to work right?

I've followed the instructions at the beginning of this thread (which resolved most of my sound issues), but I still have to plug my speakers into the headphone output instead of the output on the dock.  The sound IS playing very faintly to the dock output, but I can barely hear it even with all audio levels all the way up, however, it is playing through the front speakers on the laptop at the same time very loudly.  On the headphone output, everything is very loud and just fine, and the front laptop speakers auto-disable.

Any thoughts?

---

### Post by redenex on 2009-04-07
> **markbuntu said:**
> ** Intrepid 8.10 Sound Solution**

Go to Applications/Sound and Video and select Pulse Audio Device Chooser. This will put a little icon on the panel near the Panel Volume Control. Click on the new icon and choose Volume Control.  This will open the Pulse Audio Volume Control. Go to Output Devices and see if your sound card is there, it will be listed as ALSA PCM on front:...(ALC88) via DMA or whatever your sound card is.  If you have a usb device it will be listed as ALSA PCM on front:...(USB Audio) via DMA or something like that. Make sure the sliders are up and the device is not muted.


For me it displays **HDA ATI SB - ALC268 ANALOG**

Is this a problem?

---

### Post by redenex on 2009-04-07
Okay, when I play a song and open the Pulse Audio Volume Metre, it displays the songs being played, but still no sound in the speakers!

---

### Post by Dillio187 on 2009-04-07
> **redenex said:**
> Okay, when I play a song and open the Pulse Audio Volume Metre, it displays the songs being played, but still no sound in the speakers!

mine did this, and worked once I rebooted.

---

### Post by redenex on 2009-04-07
I rebooted,  but still no luck - yet!

---

### Post by markbuntu on 2009-04-07
In the pulse vlume control make sure that the application is playing to the correct output device. You can do this by right clicking on the stream and choosing move stream to move it to the correct output device.

If you have the right output device selected and it is turned up then check your speaker connections. If you still have problems go here for more basic troubleshooting help.

 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by redenex on 2009-04-08
> **markbuntu said:**
> In the pulse vlume control make sure that the application is playing to the correct output device. You can do this by right clicking on the stream and choosing move stream to move it to the correct output device.

If you have the right output device selected and it is turned up then check your speaker connections. If you still have problems go here for more basic troubleshooting help.

 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


:) nothing seems to help at this point of time. But then, I may need to change my tactics. Just dunno how.

---

### Post by redenex on 2009-04-08
Okay, when I just opened my myspace page, I heard the song for about 5-10 seconds and then it died out. It was on my laptop speakers, and when I connected the main speakers, there was no sound. Perplexing nevertheless.

---

### Post by Dillio187 on 2009-04-08
My sound was working fine yesterday and this morning until it glitched out (repeated note over and over and over until reboot).  I don't remember how to restart the sound engine now to reset everything, restarting pulse audio did not help, in fact, I dropped to a terminal and the sound was still glitching.

I ran pulseaudio -k to try to kill stuff and got this error:
W: ltdl-bind-now.c: Failed to find original dlopen loader.

Is pulseaudio just not quite ready for the masses or what?

---

### Post by markbuntu on 2009-04-08
This is not so much a pulseaudio problem as a problem with pulseaudio implementation in ubuntu. Users of other distros have far fewer problems with pulseaudio. 
Run 

pulseaudio -vvv

and see if you can reproduce the problem. The terminal messages will tell you what is going on and wether it is a pulseaudio problem or a kernel driver problem which would be something for the alsa devs since they write the drivers.

---

### Post by Tiddo on 2009-04-14
When I click on Default Sound Card under system>preferences nothing happens. Does anyone knows how to solve this?

---

### Post by tuique on 2009-04-14
Thank you very much Mark!

---

### Post by digitalramble on 2009-04-15
Trying to follow original instructions (I have Jaunty installed) and am stalled on padevchooser, something is down , or moved around:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pavucontrol/pavucontrol_0.9.7-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pavucontrol/pavucontrol_0.9.7-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


??  Maybe I'll try again tomorrow, but was trying to listen to Susan Boyle :-P

---

### Post by markbuntu on 2009-04-15
> **Tiddo said:**
> When I click on Default Sound Card under system>preferences nothing happens. Does anyone knows how to solve this?

From a terminal run

asoundconf-gtk

What happens?

---

### Post by Dillio187 on 2009-04-15
I decided to give this another go, and was getting the 'connection refused' message.  I ended up changing ownership of the /home/user/.pulse-cookie file to my local user after seeing the below error message.


E: authkey.c: Failed to open cookie file '/home/ptc/.pulse-cookie': Permission denied
E: authkey.c: Failed to load authorization key '/home/ptc/.pulse-cookie': Permission denied
E: module.c: Failed to load  module "module-native-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

---

### Post by jaykemper on 2009-04-16
My problem was embedded in the GNOME alsa mixer control.  There were two sliders at the very end, both labeled "Internal", but one could be muted.  Those referred to the internal speaker and microphone.  I pumped those and voila!

Argh, such a pain...:-x

---

### Post by jamesisin on 2009-04-18
Just here to subscribe.

---

### Post by TH3TH1NG on 2009-04-21
When I am listening to music with Rhythmbox, it crashes after a couple of minutes and makes my computer very laggy. When it works, it slows down a lot my computer. I am running on a dell inspiron 1720 so I guess it's not the computer that is the problem. I have tried all the steps described at the beginning of this topic but it didn't worked. What could be the problem?

---

### Post by markbuntu on 2009-04-22
It could be a problem with rythmbox. Have you tried removing and reinstalling it?
Have you looked in your logs for messages about rythmbox crashing?

Another thing you can try
In a terminal stop pulseaudio and then restart it with

pulseaudio -vvv

Then start rythmbox and see what messages you get.

---

### Post by bo01 on 2009-05-01
I had problems playings two sounds simultaneously. Now with Rythmbox and flash (eg Youtube) I managed to hear from both sources.

The only thing is that I want to use vlc and I can't set it to use pulseaudio. In the preferences menu of vlc, all it has is setting for every module the correct device; not choosing the module you want.

Can someone help me with this?

---

### Post by bo01 on 2009-05-01
I think I found it. I had to check advanced options in the output modules. Although it doesn't say anything about pulseaudio, I clicked ESD and it worked. 

Thanks again!:)

---

### Post by jamesisin on 2009-05-01
In my VLC under Preferences --> Audio --> Output --> Type I see "Pulseaudio audio output".  You don't have that option listed?

(Mine is actually set to Default, by the way.)

---

### Post by bo01 on 2009-05-02
No, I don't have it. You probably have install the vlc-plugins-pulseaudio package, which I cannot find in my synaptics (I use Debian 5.0 Lenny)

---

### Post by jamesisin on 2009-05-02
I have vlc-plugin-pulse which must cover what you are discussing.

---

### Post by bo01 on 2009-05-02
Yes, but there is no package vlc-plugin-pulse for Lenny. :(

---

### Post by lgfish on 2009-05-17
Hello, 

This guide is really helpful, thanks so much.  I have one question, though, so far.  I downloaded all the suggested packages, and then went about configuring settings as instructed.  When it comes to this part, though, I am perplexed: 

> Once you have all these packages installed, close any application that may be trying to use sound and go to System/Preferences/Sound and set all the preferences from automatic to PulseAudio *except Default Mixer Tracks which you should set to your sound card.*   

How do i figure out which sound card to select?  when I run ```
aplay -l 
``` I get 

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The options over at system > prefs > Sound Preferences are in the attached screen shot.  

Sorry if this is a naive question, i've read a ton of threads and forum posts but none seemed to shed much light.  

many thanks in advance :)

---

### Post by markbuntu on 2009-05-17
In System/Preferences/Sound/Default Mixer Tracks you should select the

Playback: ALSA PCM on front:0...

This is not that critical since it just sets the control for your multimedia keys. You can control the other volumes by opening the volume control on the panel.

---

### Post by lgfish on 2009-05-17
thanks markbuntu! 

i had tried HDA intel (AlSA mixer) before, and it seemed to work as well, but i've now changed it to Playback: ALSA PCM on front:0...  

I was mainly struggling with audio capture in skype, and now the onboard mic is working (though it's a bit quiet), so that's progress! :)

thanks again, 
L.

---

### Post by redredrex on 2009-06-08
my computer is a 1.8 ghz hardline t01b pc(brand new and stuff) and i have Ubuntu 9.04 juanty(real trouble maker as read all the treads) and the only thing i can hear is the login screen sounds and nothing els! some of the treads workt but next day,gues what?!!!!! NO FREAKING SOUND!!!!!!!!!!!!!!!!!!!](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by Wondermash on 2009-06-21
Excellent! Sound in Intrepid at last.

Thanks very much for the post! :-)

---

### Post by markbuntu on 2009-06-21
> **redredrex said:**
> my computer is a 1.8 ghz hardline t01b pc(brand new and stuff) and i have Ubuntu 9.04 juanty(real trouble maker as read all the treads) and the only thing i can hear is the login screen sounds and nothing els! some of the treads workt but next day,gues what?!!!!! NO FREAKING SOUND!!!!!!!!!!!!!!!!!!!](*,)](*,)](*,)](*,)](*,)](*,)

This thread is for Hardy8.04  and Intrepid8.10, not for Jaunty9.04. That thread is here.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Do not expect the latest greatest hardware to work very good. It takes time to write new drivers and get the bugs out of them.

---

### Post by chrisgaffrey on 2009-06-22
Thanks so much. That helped out a ton.

---

### Post by mulluysavage on 2009-06-25
Why don't I have System>Preferences>Sound? I don't even have system>preferences. Running Hardy.

---

### Post by markbuntu on 2009-06-26
> **mulluysavage said:**
> Why don't I have System>Preferences>Sound? I don't even have system>preferences. Running Hardy.

If you are not using gnome, these menus may not be available, like with KDE (Kubuntu) which has a completely different menu structure.

---

### Post by goatroapr on 2009-07-15
That was BEAU-TI-FUL.  Thanks

---

### Post by shmish on 2009-07-30
I have a laptop with a cheapo built-in audio card.  It worked fine when I installed ubuntu 8.10.  Last week I tried to get a pcmcia audio card working - an Echo Indigo DJ.  I managed to have some success, but no stereo playback.  Anyways, I have since rebooted my laptop without the pcmcia card and now Ubuntu tells me there isn't any audio device present.

"No volume control GStreamer plugins and/or devices found"

system -> preferences -> sound  there aren't any devices listed.

Unfortunately I have no idea on how to rediscover a sound device, and I'm pretty much lost on what to do at this point.  Any suggestions?

thanks

---

### Post by Norwal on 2009-08-13
Thanks for this thread markbuntu. Your "how to" worked great and I can now game and listen to music.  I did get an error message from GNOME ALSA Mixer. 

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

The mixer opens and I can make changes.  Being a seminoob, I was hoping someone could get me started on the fix.

Thanks:P

---

### Post by cortocircuito on 2009-10-20
Thanks !!! :guitar:

---

### Post by sallymc on 2010-01-13
I am a real newbie and have a 'no sound' problem with Audacity.  I use Hardy and would love to try this thread, but it was written in Nov 2008.  Will it be outdated, or should  I go for it?  Thanks for any advice

---

### Post by markbuntu on 2010-01-13
Hardy has not changed much at all in the last year or so so this thread is still good. As far as audacity goes there is a note about that and hardy in the OP of this thread which you might want to look at if the OP here does not fix your problems.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Lakeside on 2010-01-14
I will add my thanks here, followed your guide for Intrepid and I now have sound (after putting up with no sound for months!!)  Thanks to you        :)

---

