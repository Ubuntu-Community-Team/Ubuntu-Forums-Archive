---
title: "skype no microphone in jaunty"
date: 2009-09-01
forum: Multimedia Software
---

### Post by dgdriscoll on 2009-09-01
Has anyone made Skype work in Jaunty?
Specifically, The microphone.
I've tried everything suggested here:
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
here:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
and here:
[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)
If anyone has actually gotten a microphone to work with Skype in Jaunty, I would really like to hear from you. 
Right now, sound works, the microphone works, skype works except it can't see the microphone.

For anyone who cares all the details are below:

os version:
2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

Skype (Beta) Version 2.1.0.47
Downloaded from the skype.com site

System/Preferences/Sound: Sound capture:  C-Media Electronics Inc. USB PnP Audio Device USB Audio (ALSA)
Default Mixer Tracks Device: Playback: VIA 8235-VIA 8235(PulseAudio Mixer)

everything else set to PulseAudio Sound Server

Applications Sound & Video Gnome ALSA Mixer
Realtek ALC650E tab:Mic slider set to max Rec. box checked
USB Mixer tab: mic slider set to max Rec. box checked

PulseAudio applet 
Default Server  & Sink  set to Default
Default Source set to Other

PulseAudio Manager Server info
server name pulseaudio 0.9.14
Default Source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0
Devices lists 3 sources
monitor of VIA 8235-VIA 8235
VIA 8235-VIA 8235
and USB PnP Audio Device-USB Audio
Clients
lists Skype driver pulsecore/protocol-native.c
Modules lists 2 module-alsa-source entries:
alsa_input.pci... and alsa_input.usb_device...
Sample cache
various ogg files when I click on "Play" nothing happens

Pulseaudio volume control
Recording tab shows skype as an application when I make a test call.
Input Devices Tab VIA 8235 muted
USB PnP Audio Device is on monitor bar show activity when making skype test call.
Output Device shows VIA 8235 unmuted 100%

PulseAudio configure local sound server
Network Access tab
Enable network access to local sound devices checked/unchecked
Multicast/RTP Enable Multicast/rtp sender/disabled
send audio from local microphone checked/unchecked 
no joy

Preferences show notifications for discovered sources

Applications sound & video sound recorder app the microphone works fine.

---

### Post by Chronon on 2009-09-01
In Skype set "Sound in" to your sound card.  Set "Sound Out" and "Ringing" to pulse.

---

### Post by dgdriscoll on 2009-09-01
Okay,
I click the skype icon and I get a window with a skype logo at the bottom tagged "main menu". I click that, then click "options" then "sound devices". That gives me choice boxes for "Microphone", "Speakers" and "Ringing". The only option inside the boxes in all three cases is "Pulse Audio server (local)" & it won't let me enter anything else. I do have a device entry for the mic but I haven't been able to figure out how to tell Skype to use it.
Is there somewhere else to set sound in in Skype?
Thanks,
Dave

---

### Post by Chronon on 2009-09-02
There's a new beta version of Skype available from their site.  It's supposed to support pulse properly, though I have read some reports of headsets not working.

I have to set the correct hardware option in Skype in order to have it get any sound from my microphone.  As far as I have read, the new beta version works with all settings set to pulse.  Maybe give that a try, especially if you don't need it to work with a headset.

---

### Post by dgdriscoll on 2009-09-02
I'm using 
Skype (Beta) Version 2.1.0.47 which I downloaded from the skype site less than one week ago. Are you referring to that or is there something else? Also you say you have to set the correct hardware option in Skype for the mic. The only option Skype gives me is "PulseAudio server (local)".  Do you know any way for me to force it to change this setting?
Thanks,
Dave

---

### Post by ChrisWebb on 2009-09-02
Yep, have the same problem here. Skype 2.1.0.47 on Jaunty 64 bit (2.6.28-15-generic). Only audio device that shows is Pulseaudio (local). I'm already considering a regression to a previous version of Skype.

---

### Post by ChrisWebb on 2009-09-02
Regressed to 2.0.0.72. Now have all the options again. Guess I'll have to wait a while for a later version to become available in the repos...

---

### Post by HyperHacker on 2009-09-02
Same problem, thinking same solution, but where do I get version 2.0.0.72? Their website is useless (closest I get is a page saying there is no beta for Linux, which still takes me to the 2.1 beta page), all other websites just redirect to their download page, and apt-get says it has no installation candidate. :?


k found it, you need both:
[http://packages.medibuntu.org/intrepid/skype-common.html](http://packages.medibuntu.org/intrepid/skype-common.html)
[http://packages.medibuntu.org/intrepid/skype-static.html](http://packages.medibuntu.org/intrepid/skype-static.html)
And yes, it works. I'm starting to think 2.1 is just plain broken. D:

---

### Post by dgdriscoll on 2009-09-03
OK, I killed 2.1.0.47. I see in synaptic package manager a skype-mid 3.0.0.93-3jaunty1. Is that worth trying? Or is that a Very Bad Idea?
Thanks
Dave

---

### Post by Chronon on 2009-09-03
I am using 2.0.0.72 and don't have problems.  You want "skype-common" and either "skype" or "skype-static" (which is just a statically linked version, if I understand correctly).

I'm pretty sure you can just select "skype" and it pulls in "skype-common" as a dependency.

---

### Post by ChrisWebb on 2009-09-03
dgdriscoll:
As mentioned above, you need the medibuntu repository. Add it to your software sources by going to **System - Administration - Software Sources** and adding it from the Third Party tab.

If you don't see an option for Medibuntu Jaunty, then click "**Add**" and enter the following:

```
Type: **Binary**
URI:** [http://packages.medibuntu.org/](http://packages.medibuntu.org/)**
Distribution: **jaunty**
Components:** free non-free**
Comment: **Mediabuntu - Ubuntu 9.04**
```The comment isn't vital, but it helps when you're fingering through the list in 6 months time!

---

### Post by dgdriscoll on 2009-09-04
Solved: I downloaded the files hyperhacker listed & now life is beautiful. Thanks, dgd

---

### Post by keayz on 2009-09-05
Hi, I've tried all the different types of Skype in this thread and also followed the 'Comprehensive Sound Problems Solutions Guide' but my microphone still does not work, though the speakers are just fine. I have a Sony Vaio NS11J with Intel HDA sound card, Realtek chip ALC 262. Has anybody any other suggestions?

---

### Post by newcolour78 on 2009-09-08
I can get the mic to work with Alsa. 
Kill pulseaudio (for me it's unstable anyway, does not work with boxee). 
When I go to skype audio options my nvidia HD onboard soundcard now shows. I tried first the default analog device but still no mic. I then selected a different interrupt (there are a couple, don't ask me why), and now everything is fine.

I hope it helps in some way (even though configs will probably be different for other computers), but give alsa a shot if pulse does not work for you.

I run Jaunty x64.

---

### Post by Excedio on 2009-09-08
> **dgdriscoll said:**
> Solved: I downloaded the files hyperhacker listed & now life is beautiful. Thanks, dgd
 
Linky?

---

### Post by skwhirl on 2009-09-08
I have the same issues. Only "Pulse Audio" is selectable in the Skype config. I've tried the suggestions here to no avail. One particular hurdle that I can't get around:

[IMG]http://i166.photobucket.com/albums/u111/mypunkyspace/libasound2.png[/IMG]

I've been scratching my head all afternoon on this one... I'm using Hardy Heron 8.04. in this case, with Skype 2.0.0.72. Perhaps if I can get around this, I can get it working?

---

### Post by Chronon on 2009-09-08
I don't use skype-static.  I have skype and skype-common installed.  Try that instead.

---

### Post by torkna on 2009-09-09
I upgraded from skype 2.0 to the new beta version as well with the same issue. Skype would only let me see pulse audio and I could call and use all the sounds, but in a test call I would get silence for when I was speaking. After reading multiple other forums, it occurred to me that maybe it's because I didn't follow advice that I had read before I installed it - which was to uninstall skype before installing the new one. So, I unistalled skype 2.1 in synaptic by marking it for removal, and then reinstalled it from the .deb file I downloaded from skypes website. Worked like a charm. I didn't have to mess with anything after that. Just for backgrounds sake I'm using ubuntu 9.04 with a logitech quickcam pro 9000 on an ibm thinkpad T43. So in summary, I would recommend uninstalling and then trying it again.

---

### Post by jumb4 on 2009-09-12
to ChrisWeb:
I wasn't able to add that component even manually

> **HyperHacker said:**
> Same problem, thinking same solution, but where do I get version 2.0.0.72? Their website is useless (closest I get is a page saying there is no beta for Linux, which still takes me to the 2.1 beta page), all other websites just redirect to their download page, and apt-get says it has no installation candidate. :?


k found it, you need both:
[http://packages.medibuntu.org/intrepid/skype-common.html](http://packages.medibuntu.org/intrepid/skype-common.html)
[http://packages.medibuntu.org/intrepid/skype-static.html](http://packages.medibuntu.org/intrepid/skype-static.html)
And yes, it works. I'm starting to think 2.1 is just plain broken. D:

i tried to instal the first package but it failed and what i got was this (see attachment). any suggestions?

---

### Post by jumb4 on 2009-09-12
ok, now I have removed the 2.1 version of skype and i was able to instal the packages linked by hyperhacker, but now not even the speakers work!!!
in fact i can't even make a test phone call. and attached is a screenshot of the "problem with audio playback" window.
everybody i try to call has the same problem with audio playback

EDIT: PROBLEM SOLVED - It was enough to change some of the sound settings within skype to find the perfect configuration. sorry for wasting time and space! ;)

---

### Post by nortexoid on 2009-09-20
I had the same problem when updating to Skype 2.1 beta and this is what I did.

1. Install paman (pulseaudio manager). It should install pulseaudio preferences, device chooser, etc. (I think it's just the device chooser that's required but it doesn't hurt to install the manager.)

2. Run the pulseaudio device chooser. It should show an applet in your notification bar. Left click it and click on Volume Control. Then click on the Configuration tab. It should show several devices including your mic. My mic is on my external usb cam and my soundcard is an HDA Intel. Under the profile of every device that is NOT the mic device, make sure they are NOT set to input. E.g my HDA Intel device profile was "Output analog stereo + Input analog stereo". I changed it to "Output analog stereo". My USB camera profile was set to "Input analog mono".

Everything works now. I imagine the default input device for pulseaudio was my soundcard's stereo input which I wasn't using. So by disabling it, pulseaudio defaulted to my webcam.

By the way, the quality of Skype 2.1 seems better than 2.0, so I'm glad I'm using it. And it doesn't seem like my mic input drops out every now and then. So it's all good!

---

### Post by sqlpython on 2009-10-23
To get jaunty 9.04 w/PulseAudio to show mic in Skype Options.....
I wrote this script to launch Skype which utilizes the 
PULSE_SERVER  variable
You feed the PULSE_SERVER your IPaddress for your connected device..
As you can see, for me my devices are eth0 and wlan0
Modify the script devices to your needs.
A simple ifconfig <deviceName>   ...i.e.  ifconfig eth0 will give back the info for that device then we just parse it ... 
NOTE: I have installed my Skype in a Particular Dir /home/sqlpython/skype..
......If yours is in a different Dir CHange the Script..
...Also for Notification Sounds Move the /home/sqlpython/skype/sounds     dir to
..../usr/share/skype/ .. You probably will have to create that one in as sudo user of Konqueror or Nautilus 
  Even with all this PulseAudio and SKype work poorly together as they will hog CPU% and result in squashing all other playbacks while Skype is connected to another Skype User VOIP.. like if you are streaming Radio music or just trying to Play a Music CD at the same time..
   To put it in eloquent technical terms  "_PulseAudio Stinks_":P
In the end for my 8.10 and 9.04 installs I will probably uninstall Pulse.
Here You Go... Mic in Skype. :)
> 
#!/bin/bash

ifconfig wlan0 | grep "inet addr" | cut -d: -f2 | cut -d" " -f1 $1
ifconfig eth0 | grep "inet addr" | cut -d: -f2 | cut -d" " -f1  $2
if [ $1 -gt $2 ]
  then
echo $1
PULSE_SERVER=$1 /home/sqlpython/skype/skype
fi
if [ $2 -gt $1 ]
  then
echo $2
PULSE_SERVER=$2 /home/sqlpython/skype/skype
fi

---

### Post by Craig73 on 2009-10-23
> **nortexoid said:**
> 
2. Run the pulseaudio device chooser. It should show an applet in your notification bar. Left click it and click on Volume Control. Then click on the Configuration tab. It should show several devices including your mic. My mic is on my external usb cam and my soundcard is an HDA Intel. Under the profile of every device that is NOT the mic device, make sure they are NOT set to input. E.g my HDA Intel device profile was "Output analog stereo + Input analog stereo". I changed it to "Output analog stereo". My USB camera profile was set to "Input analog mono".


I don't see a configuration tab

---

### Post by funnycat79 on 2009-10-24
1. Choose "Volume Control" and open "Input Devices" tab. Than select your device to default.

2. Go to ~/.pulse/ and find file like "3fc1801253b192fb3a453426489ca151:default-source". Copy content of that file, in my was "alsa_input.usb_device_4f2_a13c_noserial_if2_sound_card_0_alsa_capture_0"

3. Left click on "Device Chooser" and choose "Default Source" and select "Other". Paste content of your file there.

It works good for me

---

### Post by libssd on 2010-05-19
> **dgdriscoll said:**
> OK, I killed 2.1.0.47. I see in synaptic package manager a skype-mid 3.0.0.93-3jaunty1. Is that worth trying? Or is that a Very Bad Idea?
Thanks
Dave

Skype-Mid is the only version I have been able to get running, although it took me a while to figure out how to quit. 

In the leftside Skype-mid panel, click on More. 
Three options are presented: **History**, **Sign Out**, and **Quit**.

---

