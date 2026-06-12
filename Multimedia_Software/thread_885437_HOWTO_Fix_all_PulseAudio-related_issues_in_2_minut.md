---
title: "HOWTO: Fix all PulseAudio-related issues in 2 minutes"
date: 2008-08-10
forum: Multimedia Software
---

### Post by eye208 on 2008-08-10
**What you will get:**
[list][*]Fully functional audio in all applications, including those currently incompatible with PulseAudio (e.g. Audacity, Blender, Skype, Second Life + voice chat, Flash)
[*]The ability to use these applications side by side (using software sound mixing provided by ALSA or ESD)[/list]
**What you will lose:**
[list][*]Ubuntu's login and logout sounds (and any other system sounds you may have added to the default set)[/list]

**To implement the fix, perform the following steps:**
[list=1][*]Open the sound configuration panel (System > Preferences > Sound).
On the "devices" tab, set all devices to "ALSA".
On the "sounds" tab, disable "play system sounds".
Leave "software sound mixing (ESD)" enabled.
Close the panel.
(See the attached picture for details.)
[*]Open a terminal window (Applications > Accessories > Terminal).
Enter the following commands:
```
sudo apt-get remove pulseaudio
sudo apt-get install esound
exit
```
**-- or --**
Open Synaptic (System > Administration > Synaptic Package Manager).
Search for the package "pulseaudio" and mark it for removal.
Search for the package "esound" and mark it for installation.
Apply the changes, then quit Synaptic.
[*]Restart the computer.[/list]

**Remarks:**

This will remove PulseAudio and replace it with ESD. The resulting sound setup will be similar to Ubuntu 7.10 and previous versions. Any issues unrelated to PulseAudio will not be affected in any way.

To restore the original setup, install the packages "pulseaudio" and "pulseaudio-esound-compat", then re-enable system sounds. Or just install the "ubuntu-desktop" metapackage. The latter is recommended anyway before doing a full system upgrade.

**Reminder:**

If you configure ALSA for the PulseAudio sink and then apply this guide, don't be surprised about ALSA not working properly. This should be a no-brainer. Remove /etc/asound.conf and ~/.asoundrc to restore ALSA's default configuration.

**April 2009 Update:**

The latest version of the Second Life client has proper ALSA support. It no longer requires ESD to work with voice chat. Unless you still need ESD for something else, I recommend uninstalling the "esound" package and going for a pure ALSA setup.

---

### Post by T_W on 2008-08-10
Just FMI, why the need to disable system sounds?

They wont play without pulseaudio installed?

---

### Post by eye208 on 2008-08-10
> **T_W said:**
> Just FMI, why the need to disable system sounds?

They wont play without pulseaudio installed?
Even after choosing ALSA as the default device, Gnome will still try to play system sounds through PulseAudio. This will cause freezes on login and/or logout when the sounds are about to be played, so you have to disable them during the absence of PulseAudio.

There may be a way to fix this and keep the system sounds, but I didn't bother looking for it. Don't apply these changes if you cannot live without system sounds.

I've been using this setup for several weeks now, and it's the only side effect I found. Everything else works.

---

### Post by Scottmoelker on 2008-08-11
Thank you very much. I've been incredibly frustrated trying to get my songs to play in media players, all other sounds were working fine. This fixed my problem, although I only followed the first steps, changing the devices to ALSA. I didn't need to uninstall PulseAudio.

---

### Post by Jeenyus on 2008-08-16
beautiful, i dont know why my sound magically stopped working, but this fixed everything.

Thank you

---

### Post by Irihapeti on 2008-08-17
If you really want the login sound, you can do this:

Create a script file with the following lines:

```
#!/bin/bash
aplay /usr/share/sounds/login.wav
```

Name it anything you like (within reason :) ). Make it executable.

Open Sessions Preferences (System -> Preferences -> Sessions)

Under Startup Programs you can add your script file to the list of additional startup programs.

Not sure what to do about logout sound. It hasn't been working on my Hardy install, anyway.


I have been having problems with Thunderbird locking up if I have the Gizmo client and Firefox running, I download a new message and new mail notification sound is on. I'm wondering if removing Pulseaudio will fix this also...

Edit: I think it has fixed this last problem :)

Irihapeti

---

### Post by jvincent08 on 2008-08-17
Thank you for this! I couldn't get Banshee to play nicely with other programs that tried to use the sound device, but this did the trick. I didn't know it had anything to do with PulseAudio, though.

---

### Post by charles_parker on 2008-08-17
I followed your steps, but I still cannot get flash sound. I'm sure it relates to my USB sound card. My system board sound doesn't work; so, I bought a small USB sound card which works fine under Windows. I get no sound at all with ALSA set in my sound preferences as described. When I switch back to USB sound, my sound works again except for flash sound in Firefox. I did complete the pulseaudio removal and esound installation.

Thanx - Charlie

---

### Post by Kristian9K on 2008-08-19
This is what I'm looking to do - simply go back to 7.10 sound. When I try this fix, I get error messages in sound setup saying that the device is already being used. Example:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

I was toying around with the settings before, so that could be the cause of this problem. Is there a way to remove ALL sound handling and then install the things that were in 7.10?

Thanks,
Kristian

PS: I'm on Mint Elyssa now which should be the same as 8.4...right?

---

### Post by suprakid24 on 2008-08-20
Thanks! After a quick reboot the sound is good

---

### Post by bdoe on 2008-08-22
> **Kristian9K said:**
> This is what I'm looking to do - simply go back to 7.10 sound. When I try this fix, I get error messages in sound setup saying that the device is already being used. Example:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

I was toying around with the settings before, so that could be the cause of this problem. Is there a way to remove ALL sound handling and then install the things that were in 7.10?

Thanks,
Kristian

PS: I'm on Mint Elyssa now which should be the same as 8.4...right?
Kristian: I used to get that a lot because of some sort of limitation with Pulseaudio and system sounds that lasted longer than 20 seconds... In short, if I logged in while the "login ready" sound I had was still playing, it would crash the audio server and result in me getting that error within the sound control panel.

If you go ahead and change everything to ALSA and disable system sounds, and then reboot before doing the rest, all should be well.

Edit:  Dammit, I just figured out what you were talking about. I followed the steps, removing pulseaudio and installing esound, and now my audio doesn't work at all with all the sound control dropdowns set to "ALSA". I get the same errors you do. I have to set them all to "Autodetect" for sound to work...

I wonder if somehow pulseaudio is still installed...

2nd Edit: I found a configuration file, /etc/asound.conf in my system. I renamed it to something else, and all is well.

---

### Post by rizitis on 2008-08-22
I have[COLOR="Navy"] ubuntu studio[/COLOR] 2.6.24-19-rt
and I have problem with Audacity, but if I try to disable from synaptic pulseaudio,
then ubuntustudio desktop will be removed too...
what can I do?  

@ &#960;&#961;&#959;&#962; &#945;&#960;&#959;&#956;&#940;&#954;&#961;&#965;&#957;&#963;&#951; = will be removed

---

### Post by Eck on 2008-08-22
Just browsing around here and noticed this.

Related to the Gnome system sounds, on Debian at least this is what got them going:

By default libesd0-dev and libesd0 are installed with the taskel desktop and gnome-desktop tasks.

However, if one installs libesd-alsa0, aptitude will remove libesd0, leave libesd0-dev and the Gnome system sounds then play normally.

Perhaps the sounds for you guys were playing through PulseAudio but when that's removed there's nothing to play it like in my case on Debian with PulseAudio never installed.

Check out Synaptic to see what Ubuntu sets up for esd.  That's esound, but the specific library files for the normal libesd0 I think are set to play through OSS (alsa-oss I guess).  But since we all set everything to Alsa, one needs the alternative libesd-alsa0 to actually hear the sounds.

---

### Post by BrendanM on 2008-08-22
Thank you very much, this fixed my sound problems. Bizzarely, I still have system startup sounds, even though I followed all of the steps in the guide. I just checked and the box for system sounds is unchecked in the config panel, but it plays anyway. *shrug* I'm pleased.

---

### Post by Kristian9K on 2008-08-23
Thanks to those who read my post and gave it thought. I got tired of messing around with the settings, then reinstalled and followed this howto... Now all is fine.

Multimedia handling in Linux - will it ever be as good as in the unnamaeble OS?

---

### Post by eye208 on 2008-08-23
> **rizitis said:**
> if I try to disable from synaptic pulseaudio,
then ubuntustudio desktop will be removed too...
what can I do?
*ubuntustudio-desktop* is a metapackage. Metapackages do not contain any software but depend on other packages. When you install a metapackage, all the other packages it depends on will automatically be installed too. However if you remove a metapackage, by default all the packages it depends on will _not_ be removed.

This means you can safely remove *ubuntustudio-desktop* without losing the actual content of Ubuntu Studio. The software itself will remain installed because it is contained in separate packages which do not depend on *ubuntustudio-desktop*.

When Ubuntu 8.10 is released and you want to upgrade, remember to re-install *ubuntustudio-desktop* before performing the upgrade. This will restore the default configuration and ensure a trouble-free upgrade.

---

### Post by flashbackk on 2008-08-23
This saved me a lot of grief. Thanks a lot. My laptop was gagging on my usb sound cards,for one thing.

---

### Post by Neil_J on 2008-08-23
> **bdoe said:**
> 2nd Edit: I found a configuration file, /etc/asound.conf in my system. I renamed it to something else, and all is well.

I had the same problems until I renamed my /etc/asound.conf ..  This should probably be mentioned in the GP post as part of the instructions.

Many thanks, I've had skipping problems since I installed 8.04, and spent the last four months off and on trying to fix it... Now completely gone.

---

### Post by ashmew2 on 2008-08-24
> **Irihapeti said:**
> If you really want the login sound, you can do this:

Create a script file with the following lines:

```
#!/bin/bash
aplay /usr/share/sounds/login.wav
```

Name it anything you like (within reason :) ). Make it executable.

Open Sessions Preferences (System -> Preferences -> Sessions)

Under Startup Programs you can add your script file to the list of additional startup programs.
Irihapeti

Genius !

---

### Post by Irihapeti on 2008-08-24
> **ashmew2 said:**
> Genius !

Hardly a genius. I just enjoy tinkering with things.

Irihapeti

---

### Post by MemoryDump on 2008-08-27
I tried this and removed all pulse related packages. I set all my gnome sound settings to use ALSA. After setting everything to ALSA and I hit the TEST button I get no sound. So I tried using "Multichannel Playback" and when I click on the TEST button I hear sound. This leads me to believe that ALSA is working, however it's not working properly when I simply select ALSA. So now this is causing my grief with all my applications which require sound. I've set their output to ALSA and I get no sound. 

I have 2 soundcards and they both show up:
```
cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xe400, irq 21
 1 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at irq 23

```
I've set my default sound card to the Audigy2.
```
asoundconf set-default-card Audigy2
```

```
cat /proc/asound/modules 
 0 snd_emu10k1
 1 snd_intel8x0
```
in my /etc/modprobe.d/alsa-base I have:
```
options snd_emu10k1 index=0
options snd_intel8x0 index=1
```

any ideas?

---

### Post by ashmew2 on 2008-08-31
> **Irihapeti said:**
> Hardly a genius. I just enjoy tinkering with things.

Irihapeti

You're Just being modest..Good job though..

---

### Post by grashdur on 2008-09-23
This fix is great. I followed the instructions, rebooted, and now Skype sound is no longer disabled while playing Totem, and Audacity now wonderfully makes use of my USB headset! :)

The only problems remaining: 

Skype sound is still disabled if I've routed music output (from Rhythmbox) to my headset and I get an incoming call. Not a big problem, as I'd likely only use my headset for music late at night when I don't want to receive calls.

But a somewhat bigger issue: This still doesn't work for Flash (for playing videos on YouTube with Firefox) -- it would be nice if there's a solution to this, since my lady sometimes likes to watch YouTube videos while I'm sleeping.

---

### Post by eye208 on 2008-09-23
> **grashdur said:**
> Skype sound is still disabled if I've routed music output (from Rhythmbox) to my headset and I get an incoming call.
> This still doesn't work for Flash (for playing videos on YouTube with Firefox) -- it would be nice if there's a solution to this, since my lady sometimes likes to watch YouTube videos while I'm sleeping.
This can be fixed too.

The problem is that ALSA defines its default device as a dmix-ed version of the system's first soundcard (hw:0) but doesn't automatically do the same thing for any other card that may be present. However, you can do that yourself, and it's not too difficult.

I assume the USB headset appears as device hw:1 in the system. Open a text editor and enter or paste the following:
```
pcm.usbmix {
    type dmix
    ipc_key 1024 # must be unique!
    slave {
        pcm "hw:1,0"
        period_time 0
        period_size 1024
        buffer_size 8192
    }
}

pcm.usb {
    type plug
    slave.pcm "usbmix"
}
```
Save this as ".asoundrc" in your home folder. Now you have a new PCM device called "usb" which should be capable of handling multiple audio streams simultaneously. Use it instead of hw:1,0.

---

### Post by grashdur on 2008-09-25
It didn't seem to work: I made that file .asoundrc and I don't see a new device listed in Sound Preferences. I have "USB Audio", which is what I have always selected whenever I want to switch sound output to the headset -- but with YouTube the sound is still going to my speakers. I tried rebooting but it's still the same.

---

### Post by zamujilo on 2008-09-26
> **eye208 said:**
> **What you will get:**
[list][*]Fully functional audio in all applications, including those currently incompatible with PulseAudio (e.g. Audacity, Blender, Skype, Second Life + voice chat, Flash)
[*]The ability to use these applications side by side (using software sound mixing provided by ALSA or ESD)[/list]
**What you will lose:**
[list][*]Ubuntu's login and logout sounds (and any other system sounds you may have added to the default set)[/list]

**To implement the fix, perform the following steps:**
[list=1][*]Open the sound configuration panel (System > Preferences > Sound).
On the "devices" tab, set all devices to "ALSA".
On the "sounds" tab, disable "play system sounds".
Leave "software sound mixing (ESD)" enabled.
Close the panel.
(See the attached picture for details.)
[*]Open a terminal window (Applications > Accessories > Terminal).
Enter the following commands:
```
sudo apt-get remove pulseaudio
sudo apt-get install esound
exit
```
**-- or --**
Open Synaptic (System > Administration > Synaptic Package Manager).
Search for the package "pulseaudio" and mark it for removal.
Search for the package "esound" and mark it for installation.
Apply the changes, then quit Synaptic.
[*]Restart the computer.[/list]

**Remarks:**

This will remove PulseAudio and replace it with ESD. The resulting sound setup will be similar to Ubuntu 7.10 and previous versions. Any issues unrelated to PulseAudio will not be affected in any way.

To restore the original setup, install the packages "pulseaudio" and "pulseaudio-esound-compat", then re-enable system sounds.
Hi,

I did all you suggested but the micro still doesn't work in skype....they can't hear me. all the rest seems to be working smoothly....any other hint? I'm getting desperate....

---

### Post by cotcot on 2008-09-26
It is a no go for me. sudo apt-get remove pulseaudio wants to remove ubuntu-desktop as well.

---

### Post by treris on 2008-09-26
> **cotcot said:**
> It is a no go for me. sudo apt-get remove pulseaudio wants to remove ubuntu-desktop as well.

The ubuntu-desktop package is a meta package meaning that it is used to install the total ubuntu desktop, removing it, however, does not remove the ubuntu (gnome) packages from your system. It is in actual fact quite harmless to do so.

Just make sure that all it is removing is the ubuntu-desktop meta package and nothing else. You can also find this information in the package description within synaptic.

I for one don't have it on my system anymore, I think I removed it along with Evolution or some other part of the basic ubuntu install.

---

### Post by treris on 2008-09-26
> **zamujilo said:**
> Hi,

I did all you suggested but the micro still doesn't work in skype....they can't hear me. all the rest seems to be working smoothly....any other hint? I'm getting desperate....

Have you clicked on the 'mic boost' button in volume control? This is something that is often forgotten, but which really is vital!

Right click on the sound applet in the panel, open volume management or whatever it's called (i'm working in a Dutch version of ubuntu so I couldn't tell you what it's really called, but it's right above 'preferences')

When the volume management window opens, go into 'edit' and 'preferences'. Select Mic Boost to be visible and then go back and mark it as active in the switches tab of the volume management window.

Hope that helps! If you've already done all this, than I'm sorry but then I won't be able to help you and I've just wasted your time, sorry about that.

---

### Post by harusp3x on 2008-09-26
I followed the steps, but ALSA cannot play audio.

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


asoundconf list displays: 
> Names of available sound cards:
default
Webcam
Intel
HDMI


I set asoundconfig set-default-card to "Intel", which I would assume is my mobo's on-board sound.

---

### Post by eye208 on 2008-09-26
> **harusp3x said:**
> I set asoundconfig set-default-card to "Intel", which I would assume is my mobo's on-board sound.
Set it to "default" instead.

ALSA's default configuration defines "default" as a software stream mixer connected to the first hardware sound device in your system. All the other devices in the list do not include the stream mixer by default, so they can be used by only one application at a time.

If you need shared access to the other sound devices in the list as well, use a customized ".asoundrc" configuration file in your home folder to assign stream mixers to those devices. There's an example in post [#24](http://ubuntuforums.org/showpost.php?p=5839531&postcount=24).

---

### Post by cotcot on 2008-09-27
> **treris said:**
> The ubuntu-desktop package is a meta package meaning that it is used to install the total ubuntu desktop, removing it, however, does not remove the ubuntu (gnome) packages from your system. It is in actual fact quite harmless to do so.

Just make sure that all it is removing is the ubuntu-desktop meta package and nothing else. You can also find this information in the package description within synaptic.

I for one don't have it on my system anymore, I think I removed it along with Evolution or some other part of the basic ubuntu install.
Thanks a lot. It works.

---

### Post by Bakon Jarser on 2008-09-27
Your way to fix pulseaudio is to get rid of it?  There are better ways of solving the problem.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by andras artois on 2008-09-27
Aha, works fine. System start up sounds still play sometimes :) thank you very much.

---

### Post by T_W on 2008-09-28
> **Bakon Jarser said:**
> Your way to fix pulseaudio is to get rid of it?  There are better ways of solving the problem.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Man, there are a heck of a lot of steps in that solution.  

I think that this all makes it obvious that PulseAudio should not have shipped in Hardy in its current form.

---

### Post by Bakon Jarser on 2008-09-28
> **T_W said:**
> Man, there are a heck of a lot of steps in that solution.  

I think that this all makes it obvious that PulseAudio should not have shipped in Hardy in its current form.

Yeah, his configuration is going to be the default in intrepid.  But if you follow the link on the top of the page to one of his later posts he automates most of the process.

---

### Post by eye208 on 2008-09-29
> **Bakon Jarser said:**
> Your way to fix pulseaudio is to get rid of it?
No. This guide doesn't fix PulseAudio but the issues caused by it.

> There are better ways of solving the problem.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Sorry, but that guide, despite being much longer, addresses only a few of the issues.

---

### Post by Cresho on 2008-09-30
I fixed my audio issues with this method

sudo apt-get install asoundconf-gtk

in terminal I launch asoundconf-gtk and select my audio card.

so i created a script to load at startup in sessions.  This is to make sure it loads up by force!  Not sure how it will work for everybody here but it works just fine for me.  all audio recording through any means works.

#!/bin/bash
sleep 10 && asoundconf set-default-card Audigy2;

---

### Post by applecookie on 2008-10-01
Have someone fixed the system-sound problem till today?

When you deinstall, pulseaudio and install esound, you can't play the systems sounds, as the thread opener already wrote. (When a system sound should be played, gnome freezes, till you "kill" the esd process).
There is another libesd in the repos ("libesd"), which can be used instead of libesd-alsa0. With this lib, the system sound works with esound without any freeze. But... You do not have any sound in games anymore (don't know, why).

The problem is, that the newer alsa (> 1.15) does not work with esound anymore. I tried the same issue in gutsy (where all works perfect except of the headphone jack on my hp) and when I install a newer alsa system there, the same freezes with esound occurs.

---

### Post by eye208 on 2008-10-01
esound is required to make Second Life sound work properly (including voice chat).

If you don't use Second Life, there's probably no need to install esound at all. I'm not aware of any other application that uses it.

I guess the difference between libesd and libesd-alsa is that the former uses OSS. This would explain why you had no sound in other applications while ESD was running. With libesd-alsa, ESD uses ALSA's default device. This enables ESD to work side by side with other ALSA clients.

---

### Post by rousselm on 2008-10-01
Hello,

I've tried this tutorial and many others ([https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel") or [http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739"))but can't get my microphone working since I installed ubuntu hardy. Well, actually it was working with "sound recorder" before following this but now it's not even... In "sound preferences" when I test the sound they all work except sound capture where I hear only a short static sound and then nothing. All my devices in "sound preference" are on "alsa" and the default mixer is on "HDA Intel" which is my sound card as far as I know.... Also, when I play music in "rythmbox" I can't even try to make a skype test call, I get the following message "problem with audio playback".
I don't know if I messed to much around or what.... I can't find anything helping on internet... I'm really hoping someone here could help me in some ways or send me links to look somewhere else...
Thanks in advance!

Marie

---

### Post by eye208 on 2008-10-04
> **rousselm said:**
> I've tried this tutorial and many others ([https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel") or [http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739"))but can't get my microphone working since I installed ubuntu hardy. Well, actually it was working with "sound recorder" before following this but now it's not even...
Make sure to undo all the changes of the other tutorials. For example, the second guide you mentioned advised you to create an /etc/asound.conf file which doesn't exist in the default setup that my guide is referring to. Some people have reported that my solution didn't work for them until they removed that file.

---

### Post by rousselm on 2008-10-08
Hello eye2008,
Well; I tried as far as I could to undo all the other tutorials and I removed the file asound.conf but it still doesn't work; it's actually even worse, I can't even make a test call as I get "problem with audio playback" although I have ONLY skype and firefox open....
Is there a way to redo a clean installation of all the audio things in hardy so I can try to find a solution on "clean" audio files?
Thanks for the help though...

Marie

---

### Post by christianj on 2008-10-18
I have a similar problem using aa Logitech USB headset. Works fine with Rhythmbox and work with youtube for about 5 minutes and then mutes.

I am running it on OSS4 and set all sound options as that.

I have uninstalled and reinstalled several of the different sound programs and this seems to be work as test tones register.

Still have that problem with Youtube cutting out.

Where can I look next ?

I am running Ubuntu 8.10 on a PC.

---

### Post by Darth Buh on 2008-10-20
Thank you so much.

I'm a new Linux user on Hardy 8.04, and I've spent the last 5 days trying to figure out why I couldn't record any sound when jacked directly into my microphone port on the PC.  As the post says, it took 2 minutes to fix.

If only Bluetooth setup were this easy...

DB

---

### Post by maphilli14 on 2008-11-05
Great guide.  I too am growing tired of pulseaudio related issues.  Anyone get cheese webcam video with audio or recordmydesktop audio to work after this guide?

---

### Post by hibi on 2008-11-07
> **MemoryDump said:**
> 

```
cat /proc/asound/modules 
 0 snd_emu10k1
 1 snd_intel8x0
```
in my /etc/modprobe.d/alsa-base I have:
```
options snd_emu10k1 index=0
options snd_intel8x0 index=1
```

any ideas?

options snd**-**emu10k1 index=0
options snd**-**intel8x0 index=1

use "-" not "_"

---

### Post by sirebral on 2008-11-07
Not everyone might want to get rid of Pulse Audio.  If you are like me and you don't want to get rid of Pulse Audio you can keep it.  My only problem is that sometimes when I run multiple sound programs the sound stops working for one or more of them.  I found this to work.

Open a terminal and type this.
```

pulseaudio --kill

```

This kills the Pulse Audio process, which is probably frozen somewhere.

Then restart Pulse Audio with this

```

pulseaudio -D --log-target=syslog

```

Pulse Audio appears to not have been ready for wide distribution.  Also, the version that came with 8.10 is older then the newest, but compiling the newest version of Pulse Audio requires a grip of DEV Libraries.  And then I couldn't even 'make' the install. :-s

But I don't think I want to remove it yet, so I looked for another work around and found this works.

---

### Post by Teclas5 on 2008-11-07
Great post eye208, this worked for me as well.  :guitar:

---

### Post by Ascenti0n on 2008-11-08
I was hoping this fix would sort out my issues with recording, ie I couldn't capture any sound, regardless of which options/settings I chose.

After following the OP's original instructions and restarted my system, I entered my details to login and was confronted by an xserv error stating it couldn't locate a pulseaudio file.

I had to restart my system and choose the 'safe gnome' option from the options panel. I then re-installed pulsaudio from sytem>administration>synaptic package manage, then choose pulseaudio, which selected dependencies too. I restarted my system and all was well again.

I'm not a linux techie, but I think pulseaudio has dependencies running deeper and wider than the toplevel desktop.

I'm running Ubuntu 8.10 - [COLOR="Red"]**proceed with this fix WITH CAUTION.**[/COLOR]

---

### Post by psyke83 on 2008-11-10
I've gotta say, this guide is overkill (at least for Intrepid).

As far as I know, Intrepid's version of GNOME no longer requires ESD (or PulseAudio) for system sound notifications at all - it uses the "libcanberra" library.

99% of users can get PulseAudio working if they take two minutes to ensure PulseAudio is configured properly, rather than ripping it out. All you need to do is follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") post, and PulseAudio will work correctly for virtually everyone.

For the 1% that either don't want PulseAudio, or genuinely can't get it working, there is a much simpler solution:

Go to System/Preferences/Sessions. Create a new entry and fill in the following details:
```
Name: Disable PulseAudio
Command: pkill pulseaudio
Comment: This will prevent PulseAudio from launching at startup.
```

With this startup entry enabled, PulseAudio will no longer run at startup, and all applications will revert to ALSA output automatically. System sounds should also work (ESD is not required).

Although I don't recommend disabling PulseAudio **unless absolutely necessary**, the above is a much better solution because:
[LIST]
[*]ESD is obsolete and unnecessary; and
[*]PulseAudio is now a part of Ubuntu; removing the packages will cause you headaches when you perform distribution upgrades.
[/LIST]

---

### Post by Fhernd on 2008-11-18
Hi!

Thanks **eye08**. Now I'm playing YouTube's videos without problems. The steps worked on Ubuntu ver. 8.10, and Firefox ver. 3.0.3.

Bye!

---

### Post by eye208 on 2008-12-13
> **psyke83 said:**
> Although I don't recommend disabling PulseAudio **unless absolutely necessary**, the above is a much better solution because:
[LIST]
[*]ESD is obsolete and unnecessary; and
[*]PulseAudio is now a part of Ubuntu; removing the packages will cause you headaches when you perform distribution upgrades.[/LIST]
Here's why your solution doesn't work:
[list][*]You won't be able to use voice chat in Second Life for Linux unless ESD is installed.[*]You can't install ESD without removing PulseAudio.[/list]
Keep in mind, my solution was supposed to work with _all_ applications. That includes Second Life, whether you like it or not.

The system upgrade trouble argument is FUD because all the changes proposed in my guide can be reverted simply by reinstalling the "ubuntu-desktop" metapackage. In fact this is the most upgrade-friendly solution you can possibly imagine.

---

### Post by 2hot6ft2 on 2008-12-13
Interesting thread but although I don't claim to know the intricacies of ubuntu or linux in general there are those who do and I would suggest heeding their advise on this one. Before removing pulse audio take a moment to read this post by TheeMahn here. [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179)

I'll even make it easy for you since it's so short here it is.
> I have posted this in Ultimate Edition 2.0 thread, yet it is ignored, I felt a sticky would help curve problems that admin have to repost over and over.

people with sound issues... I personally hate pulse audio as well, but it is tightly integrated into the O/S, I tried to completely remove it and replace it with alsa, once pulse is removed from the system it no longer allowed me to enter the GUI. I have found a [non-destructive solution]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/"), please let me know if this helps.

TheeMahn
Personally I'll take the word of TheeMahn anyday.

---

### Post by eye208 on 2008-12-15
> **2hot6ft2 said:**
> Personally I'll take the word of TheeMahn anyday.
TheeMahn's problem is that he didn't read my guide. Neither did you. I addressed the system sound lockup issue in step #1.

---

### Post by 4partee on 2008-12-15
eye208;

I was 'this close' to dropping 8.04 and reverting back to 7.04 when I found your sound solution.  

You are TheeeeeeeeeeeeeeeeeeeeeeeeeMaaaaaaaaaaaaaaaaaaaaaaahn!

---

### Post by Plan B on 2008-12-17
> **bdoe said:**
> Kristian: I used to get that a lot because of some sort of limitation with Pulseaudio and system sounds that lasted longer than 20 seconds... In short, if I logged in while the "login ready" sound I had was still playing, it would crash the audio server and result in me getting that error within the sound control panel.


This was the cause of my problems.  After I enabled startup sounds pulseaudio broke.  I disabled startup sounds (for some reason they still play?!?!?) and no more problems.

System > administration > Login Window > accessibilty tab > uncheck sounds.

---

### Post by 4partee on 2008-12-18
eye208;

After following your solution; I had sound problems with SKYPE and a game I run in WINE.

I reinstalled pulseaudio.  Now, before running either of the above, I run 'asoundconf unset pulseaudio'.  

After that, sound works just fine in all other apps as well!!!!!

HTH;
John

---

### Post by eye208 on 2008-12-19
> **4partee said:**
> After following your solution; I had sound problems with SKYPE and a game I run in WINE.
If you customize ALSA to use the PulseAudio sink, of course there will be issues after removing PulseAudio.

If you experience problems like these, remove /etc/asound.conf and ~/.asoundrc to make sure that ALSA's configuration is in its default state.

---

### Post by SlugSlug on 2008-12-24
Thank you so much!!!

---

### Post by eudemonis on 2009-01-02
woow this fixed all my sound problems thanks!!!

---

### Post by PimPamPum on 2009-01-30
hello, i'm using Intrepid, i follow this tutorial and i got no MIC at all the rest was fine. But before it was working fine with the sound recorder, so it's worst.
I tried to undo things but nothing, now all the sound is working but my MIC is completely dead.    :(

---

### Post by Zhatan on 2009-01-31
Hi, I just wanted to say thanks. This solution fixed the problems I was having with my sound.

[http://ubuntuforums.org/showthread.php?p=6650105#post6650105](http://ubuntuforums.org/showthread.php?p=6650105#post6650105)

---

### Post by togo59 on 2009-02-12
Just one correction: it took about 30 seconds not 2 minutes to fix all my sound problems. Thank you!

I have spent many, many hours following advice on forums, loading stuff, configuring stuff, god knows what esle and all I had to do was uninstall pulseaudio! I was even contemplating loading another distro.

Previously ZynAddSubFX synth and a few other synthesizers worked perfectly but rhythmbox and totem didn't. Now they all do! I even have my login sounds (again, in contradiction to the great eye).:)

I have a Terratec DMX 6Fire sound card and it works just great.

I am using Ubuntu Studio. For all such users, just remove pulseaudio and ignore what it says about removing ubuntu studio -- everything will be fine. Don't remove anything else. And I didn't even install esounds, I just removed pulseaudio -- that's it!

Bye-bye pulse audio! :P

Now I can rock and roll at last with Intrepid!:guitar:

---

### Post by ridgeland on 2009-03-31
Here is another idea:
[http://tycheent.wordpress.com/2009/03/31/to-pulseaudio-or-not-to-pulseaudio/](http://tycheent.wordpress.com/2009/03/31/to-pulseaudio-or-not-to-pulseaudio/)

tycheent created a session startup that does
killall -9 pulseaudio

That's what I'm using now.  A couple of minutes to reboot though.

---

### Post by whazooo on 2009-04-08
> **Bakon Jarser said:**
> Your way to fix pulseaudio is to get rid of it?  There are better ways of solving the problem.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

> Q. PulseAudio? Bleh! I don't want it on my system.
A. Well... tough! PulseAudio is already installed and active on Hardy

Hardly the spirit of open source, I quit reading after this.

---

### Post by labou on 2009-04-08
thanks... this worked for me.

---

### Post by KhaaL on 2009-04-23
Does this work for jaunty? because there is no box for ESD in the sound properties here...

---

### Post by barisurum on 2009-04-23
> Does this work for jaunty? because there is no box for ESD in the sound properties here...

Yes I can't see it too! darn! Pulseaudio infected jaunty like a win32 virus...

---

### Post by psyke83 on 2009-04-23
> **KhaaL said:**
> Does this work for jaunty? because there is no box for ESD in the sound properties here...

No, ESD is obsolete software - don't follow this guide for Jaunty.

If you performed a fresh install of Jaunty, everything should work automatically. If you upgraded from an older release, you may need to delete any custom configuration that may cause problems.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by KhaaL on 2009-04-23
> **psyke83 said:**
> No, ESD is obsolete software - don't follow this guide for Jaunty.

If you performed a fresh install of Jaunty, everything should work automatically. If you upgraded from an older release, you may need to delete any custom configuration that may cause problems.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I've done a fresh install of jaunty beta and upgraded to RC, does that count? :P I actually followed your tips in your mentioned post earlier and it didn't help me much. what truly helps is killing PA, but then flash hogs the soundcard. I've seen a blogpost about removing PA from jaunty [here]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") - would you recommend following the steps suggested there in order to remove PA?

---

### Post by psyke83 on 2009-04-23
> **KhaaL said:**
> I've done a fresh install of jaunty beta and upgraded to RC, does that count? :P I actually followed your tips in your mentioned post earlier and it didn't help me much. what truly helps is killing PA, but then flash hogs the soundcard. I've seen a blogpost about removing PA from jaunty [here]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") - would you recommend following the steps suggested there in order to remove PA?

Killing PulseAudio doesn't help very much, because each time an ALSA client tries to open the sound card, PulseAudio is restarted (Ubuntu's libasound2 libraries have been patched to do this - it doesn't occur for other distributions).

You can do whatever you like with your system, but I would recommend against removing PulseAudio. You're better off diagnosing PulseAudio, and if necessary, filing a bug to address the issue. My guide provides a start with regards to troubleshooting.

---

### Post by ssivil on 2009-04-23
I just did a clean install of 9.04; however, everything is dimmed (not selectable) on the "Sounds" tab on the Sound Preferences dialog panel (System, Preferences, Sound).  Everything else on my computer plays fine: videos, music etc.

I'd like to play sound effects when buttons are pressed, but noting on this panel is selectable.

Does anyone have a solution, or any other advice?

Thanks!

---

### Post by markbuntu on 2009-04-23
Read this

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by KhaaL on 2009-04-23
> **psyke83 said:**
> Killing PulseAudio doesn't help very much, because each time an ALSA client tries to open the sound card, PulseAudio is restarted (Ubuntu's libasound2 libraries have been patched to do this - it doesn't occur for other distributions).

You can do whatever you like with your system, but I would recommend against removing PulseAudio. You're better off diagnosing PulseAudio, and if necessary, filing a bug to address the issue. My guide provides a start with regards to troubleshooting.

I've put autospawn to no, and PA dosen't show when i grep ps output - so it does help in my case. I'be put a bug against PA but I'll try troubleshoot PA afterwards, right now I'm very depandent on a working sound from skype (which PA prevents) in order to collect data for my thesis. 

Thanks for the help!

---

### Post by psyke83 on 2009-04-23
> **KhaaL said:**
> I've put autospawn to no, and PA dosen't show when i grep ps output - so it does help in my case. I'be put a bug against PA but I'll try troubleshoot PA afterwards, right now I'm very depandent on a working sound from skype (which PA prevents) in order to collect data for my thesis. 

Thanks for the help!

Well if you disabled the autospan, that's fine.

Just a note: Skype and PulseAudio can get along fine, you just need to change Skype's configuration. See Appendix C of my guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by eye208 on 2009-04-24
Update:

Second Life finally works with ALSA. ESD is no longer required.

---

### Post by KhaaL on 2009-04-24
> **psyke83 said:**
> Well if you disabled the autospan, that's fine.

Just a note: Skype and PulseAudio can get along fine, you just need to change Skype's configuration. See Appendix C of my guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I have tried to set to PA, and i got horrible, barely audible audio quality. well written guide by the way!

@eye208
Huh, they took their time...

---

### Post by eye208 on 2009-04-24
> **psyke83 said:**
> Ubuntu's libasound2 libraries have been patched to do this - it doesn't occur for other distributions
That's one of the reasons why I switched to Debian.

---

### Post by go_lanche on 2009-04-29
Thanks for the help, this really fixed all my issues.

---

### Post by KhaaL on 2009-04-30
I used this guide and some of the steps here:
[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

My sound is working better than ever now :)

---

### Post by agmcclard on 2009-04-30
I did a fresh install of Jaunty since my sound would not work when just doing an upgrade. After install checked firefox to see if I had any sound/video of course that was a no I had to install adobe flashplaer to view youtube videos.  After install of flashplayer I checked on youtube and everything good I had sound and video.  Then the upgrades pop up and firefox 3.0.10 was among them, installed updates, and now I have video but no sound.  Looks like the newer version of firefox caused me to lose sound.  Anyone else had this problem.  Should I just uninstall the newer version and go back to the original version that was included before the update.

Thanks

---

### Post by n2000 on 2009-11-11
I had the same problem in Ubuntu 9.04 - it' solved now.
Thanks for your help.

Even system sounds are working in 9.04 this way.

---

