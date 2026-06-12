---
title: "skype mic not working on Ubuntu 9.10 netbook"
date: 2009-10-30
forum: Multimedia Software
---

### Post by cipicip on 2009-10-30
Hi guys,

After installing skype 2.1 on ubuntu netbook remix 9.10, the mic stopped working. The output sound is good but no input. With the static version of skype there is no sound however - input or output. Only with the deb packages.

There is only one option I can select in skype's autio properties: "pulse audio server". Nothing else. Until now I was using "HDA Intel hd:0" option which was working.

In the same time the audio recording app is working properly - I can record the mic output.

Any ideas on what I should do? Suggestions?

Thanks.

---

### Post by cipicip on 2009-10-30
Solved. Installed skype version 2.0 and selected "HD Intel (hw:0)" option.
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)

---

### Post by B Crowther on 2009-10-31
Thank you, good tip, it worked for me.

Just one quick point to help others, if you have already installed Skype 2.1 from Medibuntu Repos, you will have to uninstall skype-common via synaptic, as well as skype, or else the Skype 2.0 package will not install via GDebi.

---

### Post by joshzam on 2009-11-05
Make sure you have 'padevchooser' installed to help configure your PulseAudio and select the proper Mic input.

---

### Post by cristian.vrabie on 2009-11-06
thanks @joshzam ! this saved my day! praise the day savers!

---

### Post by mantd on 2009-11-07
Hi,

I am running Ubuntu Network Remix 9.10 on Acer Aspire One D150.

Installing the 2.1 skype version gives me no input (mic), tried adjusting the volume to the max to no avail, sound recording is possible though.

With version 2.0 most of the time i can't hear anysound it stutters with audio playback device error. Whenever i can hear the sound (which is shortlived) I can hear my voice (in skype test call)

On terminal this two error message keeps coming out and skype v2.0 maxed out my cpu  

- RtApiAlsa: underrun detected.

- bt_audio_service_open: connect() failed: Connection refused (111)

Any ideas ?

---

### Post by chrisblack on 2009-11-11
As above -uninstalled 2.1 and installed 2.0 from link above - mike now working fine on my Aspire One with full 9.10 (not netbook remix).

Chris

---

### Post by The End of The World on 2009-11-11
Just putting this out there...

Have you tried updating it?  

You would be suprsied - some people forget. Or they just cant. Meh...It works on my acer aspire one a150l, and thats what i did ;), so Good Luck

---

### Post by andrius7 on 2009-11-24
What soud divice setting i should choose, coz on default ones i even cant make a test call , on Beta2

---

### Post by cipicip on 2009-11-24
> **andrius7 said:**
> What soud divice setting i should choose, coz on default ones i even cant make a test call , on Beta2

Use this from the dropdown: "HD Intel (hw:0)"

---

### Post by tr1gg3r on 2009-11-24
I'm running skype 2.1 beta from Medibuntu, and have installed padevchooser. Still no joy with the mic under skype though. What settings for the mic did you choose, and what version of skype ?

Thanks.

---

### Post by cipicip on 2009-11-24
> **tr1gg3r said:**
> I'm running skype 2.1 beta from Medibuntu, and have installed padevchooser. Still no joy with the mic under skype though. What settings for the mic did you choose, and what version of skype ?

Thanks.

Just like it says above [http://ubuntuforums.org/showpost.php?p=8200725&postcount=2](http://ubuntuforums.org/showpost.php?p=8200725&postcount=2)
uninstall the skype 2.1, install instead 2.0 and select "HD Intel (hw:0)" in Skype's audio settings.

---

### Post by Renzo4 on 2009-12-03
> **cipicip said:**
> Solved. Installed skype version 2.0 and selected "HD Intel (hw:0)" option.
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)
hola gracias me ayudate muchome sirvio la version 2.0 del skype solo que no la encontre por ningun lado 

hello thanks a lot to me served me get hold of version 2.0 of skype which not only find him anywhere

---

### Post by cipicip on 2009-12-04
> **Renzo4 said:**
> hola gracias me ayudate muchome sirvio la version 2.0 del skype solo que no la encontre por ningun lado 

hello thanks a lot to me served me get hold of version 2.0 of skype which not only find him anywhere

De nada. Me alegro que te pudo ayudar.

---

### Post by mcb CH on 2009-12-07
Running skype on 9.04 (Jaunty) on a Dell Desktop with a USB headset. No problem until yesterday, when medibuntu upgraded to skype 2.1. Lost mic out, all capability to adjust skype audio devices (stuck on 'pulse audio'). Following advice and link from cipicip above, I re-installed skype 2.0 - everything works again.
I had the same problem (and a few others) when upgrading from 9.04 to 9.10 on this machine and decided to roll back to 9.04. On a Samsung netbook, I run skype with 9.10 Netbook remix, no problems.
Thanks cipicip

---

### Post by leorolla on 2009-12-08
I also have Acer Aspire One D-150.

Can't get microphone on skype either.

2.1 not a chance... does not recognise any "device"
2.0 displays sound for a second and then totally mutes my computer

---

### Post by leorolla on 2009-12-09
@The End of The World
@rodrick

How do you update?

---

### Post by leorolla on 2009-12-09
@mantd

Try this:

```
sudo apt-get install libqt4-assistant libqt4-core libqt4-gui libqt4-test skype-common- skype- padevchooser
wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb
sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb
rm skype-debian_2.0.0.72-1_i386.deb

```
Reboot
```
alsamixer

```
F3
set all to maximum, and unmute all (pressing m)
F4
set all to maximum, choose one of the options if you are given options (probably built-in or external)
ESC
```
skype

```
Options -> Sound Devices
Choose the 2nd option for the three choices (in your case should be "HD Intel (hw:0)")
Uncheck "Allow Skype..."
Apply
Make a test sound
If so sound, sorry.
If sound, make a test call.

I am a newbie and I don't know exacly why  padevchooser is important... It worked for my AAO-D150.

For my MIM-2310 it worked after installing padevchooser, though I didn't try hard before installing it... afterwards I removed padevchooser and all the packages it had brought with it, and still it works...

---

### Post by revanb on 2009-12-09
The following works for me in 9.10

If, in Skype, the audio options are set to PulseAudio with no other options you need to do the following:

* Open your sound setting (Right clicking speaker icon top right will do)

* In sound settings go to input tab and choose your microphone/source there.

---

### Post by Richardthe675th on 2009-12-10
Thanks Revanb - that worked for me. I have just down loaded Skype 2.1.0.47, no mic on the test call, followed your instructions on setting levels, all ok now.

thanks again,

Richard

---

### Post by brianfriedkin on 2009-12-14
When I installed Karmic K the Skype mike quit working and I was only able to get it working by upgrading to Skype 2.1. It worked fine for a month then the mike quit working again. I reinstalled Skype 2.0 but it didn't work--too many choices in sound device options all of which failed to work. So I then reinstalled 2.1 and it worked again. My guess is that Skype or something is resetting something on reboots. What is a pain in the *** about this is that reinstalling 2.1 didn't work. I had to install 2.0 then 2.1 to get it to work. Are they neglecting Linux by not fixing cheesy stuff like this? I would quit using Skype if it weren't for friends in foreign countries who use it.

---

### Post by brianfriedkin on 2009-12-16
I did all the things recommended above such as installing padevchooser and messing around with alsamixer settings. Neither Skype 2.0 nor 2.1 works for me. Or, this is how I can get it to work: I have to uninstall 2.1, install 2.0 and then I need to reinstall 2.1. If I only put my computer into suspend Skype, or something, resets everything and the mic will not work and I need to repeat the process. So if you need to waste 2 hours putting on your shoes for a one hour walk you will just not bother anymore. 

Does anyone have a solution for this? Is this my computer set up? I have an Audigy 2 sound card. Or is Skype deteriorating and going the way of Netscape?

---

### Post by iceman85 on 2009-12-19
> **revanb said:**
> The following works for me in 9.10

If, in Skype, the audio options are set to PulseAudio with no other options you need to do the following:

* Open your sound setting (Right clicking speaker icon top right will do)

* In sound settings go to input tab and choose your microphone/source there.

thanks!

---

### Post by joeljoseph999 on 2009-12-30
> **cipicip said:**
> Use this from the dropdown: "HD Intel (hw:0)"

Hi I tried ur method of reinstalling skype with version 2.0.Jus for the sake of clarification did u select HDA Intel(hw;Intel,0) for all 3 cases viz Sound in Sound out and ringing?

---

### Post by leorolla on 2009-12-31
Yes

---

### Post by cipicip on 2009-12-31
> **joeljoseph999 said:**
> Hi I tried ur method of reinstalling skype with version 2.0.Jus for the sake of clarification did u select HDA Intel(hw;Intel,0) for all 3 cases viz Sound in Sound out and ringing?

Yes. But feel free to experiment with them. I know that in one case only one speaker was working (mono instead of stereo sound out).

---

### Post by premamotion on 2010-01-01
[http://ubuntuforums.org/showthread.php?t=1368141&highlight=pulse](http://ubuntuforums.org/showthread.php?t=1368141&highlight=pulse) 

Remove PulseAudio, and it will work.

PulseAudio does not allow you to change anything in the Skype sound configuration.. so choose Alsa.

---

### Post by jesuisbenjamin on 2010-01-04
Hello there,

i would like to be able to make calls from Skype 2.1 on Jaunty. All the above didn't work out for me. 
Skype test-call does not work, input does not work during calls. Please help me fix this i need to use Skype badly.
PulseAudio Volume control does not open and i don't know how to setup PulseAudio Device Chooser.

cheers.
B.

---

### Post by egruber on 2010-01-05
> **cipicip said:**
> Solved. Installed skype version 2.0 and selected "HD Intel (hw:0)" option.
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)

I have similar problems with a thinkpad t40.  I uninstalled the newer version and installed the one with the above link.  But when I open the drop down boxes under sound options, I have a whole slew of option choices, including a bunch starting with Intel 8201DB-ICH4 followed by different codes.  And HDMI and Bluetooth.  But not the one listed above.  With Pulse, I can hear, but the mic will not work.  The other choices don't seem to work.

Update:  I deleted Skype 2.0 and downloaded 2.1 from the Skype website, but picked Ubuntu 8.10 and NOT Ubuntu 8.10 +32.  Now the sound works perfectly.

---

### Post by leorolla on 2010-01-06
@jesuisbenjamin,

why don't you try skype 2.0?

---

### Post by Cotopaxi on 2010-01-07
Ok, I finally got it working with the 2.1 Version. Following the advice of someone of this forum, I just removed all pulseaudio:

> Sudo apt-get remove --purge pulseaudio

After rebooting, and having the USB headset connected, Skype recognized my USB headset. In my case I had to choose:

> Logitech USB Headset, USB Audi Default Audio Device (default:CARD=Headset)

I hope this helps

---

### Post by egruber on 2010-01-08
Well, my audio problems have been resolved with 2.1  Audio-only calls work fine But when I use the video, everything locks up when on a call with another video user.  I thought it might be a network issue, but I did comparison tests with a Windows 7 PC and only Ubuntu locked up.

---

### Post by DeonStr on 2010-01-11
> **leorolla said:**
> @jesuisbenjamin,

why don't you try skype 2.0?

Any link where to get Skype 2.0? The one at the beginning of this thread gave me 2.1, and the mic is not working on my Acer Aspire One , even after I removed pulseaudio. :(

Regards

---

### Post by leorolla on 2010-01-11
Skype 2.0 from Medibuntu repositories:

0. Clean up```

sudo apt-get purge skype skype-static skype-common
sudo apt-get autoremove
```

1. Add Medibunutu repositories

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2. Pin priorities```

sudo gedit /etc/apt/preferences
``````

Package: skype skype-static skype-common
Pin: release a=hardy
Pin-Priority: 990
```3. Add hardy-stage repositories```

sudo gedit /etc/apt/sources.list.d/medibuntu.hardy.list
``````

deb http://packages.medibuntu.org/ hardy free non-free
deb http://packages.medibuntu.org/ hardy-staging free non-free
```4. Install skype```

sudo apt-get install skype
```Normally this should work unless you have other repositories pinned with priority bigger than 990.

Obs.:
Skype will soon be removed from Medibuntu as skype.com shall deploy their own repository.
Anyway, [http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb) and [http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu1.1_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu1.1_i386.deb) should be 2.0.0.72 and I would be surprised otherwise.

---

### Post by alldaylong on 2010-01-16
I was having all of these same problems with my mic and jack logic (plug in headset and speakers don't mute, etc) and with skype and so on - just ditch pulse audio and get ALSA. This fixed everything for me. Here's the thread [http://ubuntuforums.org/showthread.php?p=8675681&posted=1#post8675681](http://ubuntuforums.org/showthread.php?p=8675681&posted=1#post8675681)

---

### Post by Nordstroemen on 2010-01-20
**How it worked out for me**

Finally solved this problem, simply by a lot of trial and error attempts, combined with a lot of forum browsing.. Lets make it straight from the beginning; Im a total dummy at both Ubuntu and computers in general, so perhaps this might help others on the same level or give some ideas:

I had no sound input of any kind, neither when i used pulse or alsamixer.. at first at least.. but this worked:

I have the Skype Linux beta version.. which works perfectly for me, only the sound input was a prob. You can download it from skype.com. It is very easy.

**1)** go to Skype -Options/Sound devices/ --> and remove the: "allow skype to automatically adjust my mixer levels. Most important step!

**2)** if you dont have it, download Alsamixer in Ubuntu sofwarecenter.

**3)** go to Sound preferences (right click the loudspeaker icon on toolbar in top of screen)
go to the hardware tab, and make sure your hardware device, and its profile, give the possibility for sound input. 
(If you, as me, have no idea of what you got and how it should be configured, try to see which choices allows you to mute your sound input volume(next tab), and are still are allowing your computer to make noises/music)

In my case its: Hardware: "Internal audio-1 output/1 input", set to the profile; "analog stereo duplex".

ofc your Input volume should NOT be muted

close sound preferences

**4)** Now open your downloaded Alsamixer application: Applications/sound and video/Gnome Alsa mixer.

Make sure the two "Capture-slides" are set to max, and that the "Rec-options" below the sliders are selected. If in doubt; just put all of it on max, wont harm you, except the Mic Boost, you can play with that later.

**5)** Now its get interesting, open terminal: Applications/Accessories/terminal
(and no, here i have no idea of what Im doing either)

Type in: alsamixer -> then press enter

This window will pop up, except you'll start on the "Playback tab":

[[IMG]http://img211.imageshack.us/img211/1253/alsamixerinterminalh.jpg[/IMG]]("http://img211.imageshack.us/i/alsamixerinterminalh.jpg/")

You start on the "Playback tab" (see the line saying View), and have to go to the "Capture tab". move between them by using the Tab-key.

The thing you want to change is the input sources. mine is set to "input mix" and "line in". if that particular setting doesnt work for you, or you want another setting, try to play around with it. 

**6)**Restart your laptop.

**7)**Check if changes has worked for you, by seeing the input levels in "sound preferences", both when playing music and using your mic. Try recording in "Voice recorder" (Applications/sound and video/Voice recorder).

After this, mine has been working like a charm!

As i said, im certaintly no expert, and have only been able to make this work bcs of the advice from others.. some steps might be unneccesary, to be honest I have no idea, so if others sees some faults or anything please don't refrain from pointing it out.

Btw I'm on an Acer-Aspire 6530

Hope it can help!

---

### Post by andycastille on 2010-01-20
Not working... I tried the last one ( ^ ) and it didn't help. Nothing happened. Still no sound from the mic. The speakers work, but they always did.

---

### Post by egruber on 2010-01-21
Skype just released a new version for Ubuntu.  Try it and see if it works better.

---

### Post by mn_voyageur on 2010-01-21
Finally!  I have been fighting this problem ever since I upgraded.

---

### Post by Peter Wagner on 2010-01-26
Hello,

1) Microphone in general: (Creative Sound Blaster)
in Alsamixer I had to play around, typing and listening. Result for Capture:
Analog Source - Mic,
Digital: "i2s in" (i2s mixe records also system sounds)
Shared Mic: Mic

In Sound Settings (Pulseaudio) I had to play with the "input" settings: lowering to zero and turning back to 100% made sound appearing

2) Skype itself: Sound output (+Ringing) was working generally, but only via ALSA (CA0106). "Pulse" made it stumbling and fading.
With Sound input, again, only Pulse was "working" (I could hear myself during the test call). ALSA set the Mic level to zero. But there was no repeating of my voice, the service continued very fast with "If you can hear your own voice ...". Sometimes I could hear the beginning of the message itself recorded.

Solution: Upgrade to Skype 2.1 (interepid, even if I have Karmic). Download .deb pack, remove skype and skype-common in Synaptic, run .deb file
Still nothing - but just unless I disabled my first input source (sound settings - hardware - internal sound system - chose "turn off" or whatever it is in English)

Now I can hear my own voice!

:D:D:D:D:D:D:D:D

---

### Post by leorolla on 2010-01-27
I got PulseAudio working:
[http://ubuntuforums.org/showpost.php?p=8732052&postcount=65](http://ubuntuforums.org/showpost.php?p=8732052&postcount=65)

Now I use Skype 2.1!

---

### Post by xavierzhao on 2010-02-03
You solved my problem, thank you very much. Now I use Skype 2.0
:popcorn:

---

### Post by Spellinator on 2010-02-19
> **Cotopaxi said:**
> Ok, I finally got it working with the 2.1 Version. Following the advice of someone of this forum, I just removed all pulseaudio:



After rebooting, and having the USB headset connected, Skype recognized my USB headset. In my case I had to choose:



I hope this helps

This did the trick for me! Thanks!!!! Skype 2.1 was not the problem.

---

### Post by pldaniels on 2010-03-19
Fixed easy here...

 Go into the Pulse Audio volume control, select the "input device" (for me, Microphone one), unbind both Left & right controls and put the RIGHT control to 0% and the LEFT control to 100%.

 This is for an Acer Aspire One D250.

Hope that helps some.

 It doesn't seem to matter which way you go with the 0% and 100% but it's essential that left and right are at opposites.  Not sure why this is the case but it works great here - as soon as you make the change you can see the 'VU' meter suddenly pick up an work :)

---

### Post by kapcom01 on 2010-03-24
where can i find skype 2.0?

---

### Post by geneluck on 2010-03-24
This sound problems seem to be common. I cannot use skype with ubuntu 9.10 on my DELL desktop. I use an externel microsoft webcam.
The speakers funtion perfectly but I cannot get the mic to work. The only option available for sound input in SKYPE is pulseaudio. Someone on this thread suggested using skype v2.0, but the link given in this thread is not working any longer. There must be many people like me out there and without skype ,linux is not an option for me .

---

### Post by kapcom01 on 2010-03-24
> **kapcom01 said:**
> where can i find skype 2.0?

OK I found it and it works! Here is the link [http://dl.dropbox.com/u/3429388/skype-debian_2.0.0.72-1_i386.deb](http://dl.dropbox.com/u/3429388/skype-debian_2.0.0.72-1_i386.deb)

---

### Post by jithukseb on 2010-04-02
[SIZE=3]I have Samsung N150
[/SIZE]
[SIZE=2]
 first install pulseaudio & its volume Control

apt-get install pavucontrol (for Volume control)

then  go to

application > Sound-Video > pulseAudio Volume Control 

then click on  "input Devices" >"Port"   

 then  select  Microphone2 

that's All     


may this will help u[/SIZE]

[SIZE=6]JITHU[/SIZE]

---

### Post by voscom on 2010-04-02
I think you should install the new version SKYPE, and check it again, good luck to you.

---

### Post by grandmaster on 2010-04-26
Acer aspire one A0A150-ab
Very low mic on skype 2.1.0.81

I fixed this by going to the terminal

sudo apt-get install sudo apt-get install pavucontrol

I then went to applications,sound & video,pulse audio volume control.

I turned down input front left to 0% and front right to 100%

This worked for me.

---

### Post by aveeshkumar on 2010-05-13
skype 2.1 - always had sound but no mic (not even in sound recorder app)
for ubuntu 10.04 (or 9.10)

the only choice was pulseserver

going to system - administration - sound - hardware

and choosing the corrrect mic device did it for me
- my mic was muted
- volume was low
- disabled the skype option to "auto adjust mic level"

HTH some others...cheers
:guitar:

---

### Post by viulian on 2010-05-18
I also had this problem.

My problem was that in Sound preferences / Hardware, the card (SBLive EMU10k1) was set to Analog Stereo Output - so no input was available.

After this, I switched to Analog Surround 5+1 + Analog Stereo Input. Still no luck!

But then I thought maybe the microphone should not be stereo anyway, so I found the other option - Analog Surround 5+1 + Analog Mono Input. Now everything works, Skype 2.1 beta + Ubuntu 9.10 (and Skype is controlling the volume correctly).

---

### Post by danarch on 2010-05-28
> **grandmaster said:**
> Acer aspire one A0A150-ab
Very low mic on skype 2.1.0.81

I fixed this by going to the terminal

sudo apt-get install sudo apt-get install pavucontrol

I then went to applications,sound & video,pulse audio volume control.

I turned down input front left to 0% and front right to 100%

This worked for me.

That worked for me as well on an Aspire One with 10.04.  This is the strangest workaround I've ever seen.  Thank you.

---

### Post by blackest_knight on 2010-06-26
setting the volume high and low on the mic works on 10.04 aspire 110L linux 
guess it sets the 2 channels in opposite phase to each other canceling each other out. 

I used to use a local server to force skype to use alsa but this is more like it.

---

### Post by barna10 on 2010-07-03
I'm using an Acer Aspire one with Ubuntu 10.04. Removed pulseaudio and installed Alsamixer. Skype now works great.

---

### Post by MrJason005 on 2012-05-18
Omfg that guy is a life saver.
He must be on the front page. Thank you grandmaster soooo much. 
God bless you.

---

