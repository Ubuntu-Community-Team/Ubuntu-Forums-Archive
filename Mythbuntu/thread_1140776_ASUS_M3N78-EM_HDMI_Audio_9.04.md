---
title: "ASUS M3N78-EM HDMI Audio 9.04"
date: 2009-04-27
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-04-27
Just installed a fresh copy of 9.04 on my ASUS M3N78-EM. There are a couple of recurring problems from 8.10; one is the very soft analog audio output and lack of HDMI audio. I haven't yet tried the SPDIF.

The symptom, which has always been present on this board, is audio that's about half the volume of a cable box input (granted, that one is via HDMI); but even at 100% on the TV, the Asus audio is just not even at a "normal" listening level, and there is a strong background noise undertone from the TV, i.e. the TV amp gain is set too high. Not the case at all with the cable box. Same problem with headphones or external amplified speakers -- the mobo just isn't putting out enough mV.

Yes, the master and PCM and all other volumes are dialed up to 11 (so to speak). Updated to latest BIOS -- no difference. Only the "ALSA-Default" setting in Myth's config produces any audio output at all. All others are silent (after restarting the frontend); SPDIF passthrough passes the digital feed right into the analog out, with less than pleasing results.

ALSA finds the HDMI output for the built-in NVidia 8300, but I can't get it to show up in the Myth front end audio configurations.

Here's the output of aplay -L :

```
M3n78em:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

and here's the (default) xorg.conf:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

Looking for a louder experience....

---

### Post by phroman on 2009-04-28
Hey DrJohn999, I have an Asus P5Q and had trouble getting the audio out of the SPDIF also.  I think they're the same audio chipset.  I found 3 posts that helped me out, they're not exactly what you are describing but maybe can give you *some* help.

[http://ubuntuforums.org/showthread.php?t=1100747](http://ubuntuforums.org/showthread.php?t=1100747)  I did Add the line "options snd-hda-intel model=6stack-dig" at bottom of /etc/modprobe.d/alsa-base.conf

[http://ubuntuforums.org/showthread.php?t=1100747](http://ubuntuforums.org/showthread.php?t=1100747)

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)   Where it says "Check Your Mixer", I followed the instructions and everything is working now.  

Good luck.

---

### Post by DrJohn999 on 2009-04-29
Thanks, phroman, that got it 95% of the way there. Here's what I had to do. The following is a combination of what I found in the links above, and what I determined experimentally. Note that this only applies to Jaunty with the released and updated drivers as of today. One can hope this will stick but who knows...

1) in alsamixer, set the front channel volume up high: this is the default (lime-colored) jack on the board. It was down low and I'd never changed it. This has increased the basic analog output level sufficiently that its now within a 'normal' range of the cable box (still slightly softer, though).

2) in alsamixer, unmute all IEC958 playback channels.

In this system, I can't find enumerations on the IEC958 channels to set them to "PCM", contrary to what's said on the [Alsa wiki]("http://alsa.opensrc.org/index.php/DigitalOut").

I also added the suggested line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=6stack-dig
```

but I haven't gone back and removed it to verify if it actually does anything.

Finally, the MythTV front end audio settings under General... Well, I find that I have to leave the output device at Alsa:Default to get any sound, and I do now get output from both the rear panel audio and SPDIF. With the "Max Channels" setting at stereo the analog output is now fine, and the SPDIF works well, although it's not getting a 5.1 feed.

Setting "Max Channels" to 5.1 introduces some artifacts into the SPDIF playback but not an actual 5.1 feed: it sounds as if companding has gone amuck. At this setting the overall volume level of both analog and SPDIF are also reduced. 

I can get 5.1 sound, but to do so I have to enable the AC3 and/or DTS passthrough checkboxes. Now, however, and watch out for this, the digital 5.1 stream is passed not only to SPDIF but it pipes out through the analog as well, which can damage a high-powered analog amp if connected. I don't yet know (will try another time) if the 5.1 feeds through when "stereo" is selected in Max Channels.

Thanks,

DrJ

---

### Post by Chuckels550 on 2009-04-30
HDMI is tricky even if you are using regular electronic components.  Most receivers only pass through the digital audio signal carried by HDMI.  If you are using analog speakers, that means that if you connect your DVD player and LCD TV to the receiver using HDMI, then no sound will come out of the speakers unless your TV can handle digital sound.  That's why receivers advocate both a composite and digital connection along with HDMI from the DVD player to the receiver.  

The audio digital to analog or analog to digital conversion only occurs when fed by the non-HDMI connections.  That means that if you are using a HDMI connection between your PC and receiver or speaker set, unless the audio can accept digital passed through, you won't hear anything; however, you can display an up to 1080p picture if your TV is capable.

---

### Post by DrJohn999 on 2009-04-30
I'm simply trying to route audio via HDMI directly to the TV itself, not thru the receiver which does not have HDMI capability. Normally this receiver sits with the large-screen TV, 5.1 speakers, etc in another room. The TV I'm running with Mythbuntu is HDMI capable and does fine with the cable box feed. I suspect that I need to update the NVidia driver (now at 180) in order to get HDMI audio to pass through the graphics chip and on to the TV.

-- DJ

---

### Post by kxmas on 2009-05-01
I went through this hell last week.  I survived :)  You don't need new nvidia drivers.  

I have the exact same mobo, so this is what works....
I did go into the bios and set the sound option to "internal only."

Make sure that you have module-assistant installed.

I posted how I did it here, [http://ubuntuforums.org/showthread.php?p=7152783#post7152783]("http://ubuntuforums.org/showthread.php?p=7152783#post7152783")

---

### Post by tobiz on 2009-05-01
> **kxmas said:**
> I went through this hell last week.  I survived :)  You don't need new nvidia drivers.  

I have the exact same mobo, so this is what works....
I did go into the bios and set the sound option to "internal only."

Make sure that you have module-assistant installed.

I posted how I did it here, [http://ubuntuforums.org/showthread.php?p=7152783#post7152783]("http://ubuntuforums.org/showthread.php?p=7152783#post7152783")
I got this m/b working for HDMI, see post as above. Not tried it with 9.04 yet.

---

### Post by DrJohn999 on 2009-05-02
HDMI now works on this board with 9.04, upgraded to latest as of today. I also did flash the BIOS last week to ASUS' latest release version 0520 but don't know if that made any difference.

It's not necessary to update alsa as kxmas did -- Version 1.0.18rc3 is loaded with Jaunty. Just set the BIOS for internal codec only, find the identity of the HDMI device using aplay -L and create /etc/asound.conf, i.e. follow [http://ubuntuforums.org/showthread.php?p=7152783#post7152783](http://ubuntuforums.org/showthread.php?p=7152783#post7152783) but start at step 3:

```
M3n78em:~$ aplay -L
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

M3n78em:~$ cat /etc/asound.conf
pcm.!default hdmi:NVidia
pcm.iec958 hdmi:NVidia


```

I note, however, that this configuration simply passes the digital audio stream thru to the HDMI output. No mixer functions are available. Also, I have found at least one digital channel (a shopping channel so no great loss) that has four sub-channels in standard definition but doesn't get the digital audio quite right, or just leaves it out entirely, so the audio is silent, out of sync, or crosses over from another channel. 

Using the analog outputs works these channels correctly. Didn't try them with SPDIF.

Thanks to all for the help -- as far as I'm concerned the issue is solved.

--DJ

---

### Post by Dewey_Oxberger on 2009-05-02
Alsa is one cool can of code.

Your PC has several hardware audio devices.  The analog stuff, SPDIF, and now HDMI all are supported in your PC's hardware.

To see your PC's hardware just:

```
aplay -l
```

That will show what hardware you actually have.

Alsa lets programs get to this hardware by defining virtual devices.  By default it created several virtual devices for you.  All you have to do is tell a program to use that virtual device and it'll work.

See the virtual devices with:

```
aplay -L
```

In mythtv, if you want to use one of those devices (like say the hdmi device) you would need to go to the audio configuration tab (Utilities/Setup, Setup, General, Next until you see the Audio Tab).  Then fill in the audio info.  It's case sensitive:

```
Audio output device: ALSA:hdmi     <-- you have to type it in

```

If you find the hdmi device doesn't have all the features you need (I don't think it converts other sample rates or channels to it's format) ALSA lets you make your own virtual devices that do whatever you need.

Here is an example of a asound.conf that makes an hdmi device, then a "fix the rate and channels on hdmi" device, then adds a volume control to hdmi so the pc can control the volume.  There are some instructions in the file.  With a little luck it'll fill in the missing parts of the puzzle for you.

---

### Post by DrJohn999 on 2009-05-03
Thanks, that setup works well. 

There's a more complex situation, though. No one here but myself knows how to operate all this stuff, and normally its set to just play HDMI (or analog) through the TV: the A/V receiver is off. The SO can make this work, but nothing else. When we want to watch live TV with Dolby, or a DVD, then I turn on the receiver and change the settings accordingly. This works fine with the cable box, TV, and DVD player.

With this Myth box, however, I don't yet understand how to get  HDMI to the TV and, or without changes to asound.conf and rebooting anyway, get SPDIF into the receiver.

As shown above, SPDIF will work at the same time as analog output, but only in stereo. Enabling the -->SPDIF passthroughs in Myth seems also to send the digital stream to the analog outputs, rendering them useless.

I think that its necessary to enable both the internal and external codecs in the board's BIOS nVidia chipset configuration in order to get anything on SPDIF, but then the HDMI setup in the previous post doesn't work, even though the HDMI output remains on card#0:device#3.

Here's aplay -l with the internal/external codec setting enabled:
```
M3n78em:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
(aplay -L is in the first post in this thread).

So, any advice on proceeding from here? How might I get HDMI working in the above situation? Maybe I can define another alsa virtual device based on card#0:device#1, but how then to pass this through to the SPDIF output? Or maybe enable the IEC958?

Even better, where is a good tutorial on ALSA that discusses its capabilities on a technical level?

Thanks!

---

### Post by DrJohn999 on 2009-05-03
With a little more fiddling I got the HDMI working with the internal/external codecs enabled in the BIOS. Adding the external setting there brought up the other items in alsamixer again. Some of them, line-out and 2 of 3 iec958's were muted, and some of the volumes had been dropped to zero. Unmuting and setting reasonable volume levels solved this one.

So, now I get HDMI while having enabled both the analog and spdif devices, as follows for the Myth audio configuration:

output device: ALSA:hdmi_complete
passthrough output device: ALSA:iec958 {AES0:0x2}
max audio channels: stereo
upmix: passive
(not checked) enable AC3 to SPDIF passthrough
(not checked) enable DTS to SPDIF passthrough
mixer device: ALSA:default
mixer controls: hdmi_volume

If I check "enable AC3 to SPDIF passthrough" the spdif becomes active with stereo or Dolby/5.1, depending on the source. I haven't dug up a DTS DVD yet, so I don't know about that one.

However, selecting "enable AC3 to SPDIF passthrough" mutes the HDMI audio. Not too shabby, though, since now I only have to change the one setting to switch from HDMI to SPDIF.

One curiosity: selecting "5.1" for max audio channels disables Dolby (at least on live TV) and reduces the volume on HDMI by about 50%....

Found AlsoProject.org and am reading up on it.

--DJ

---

### Post by Dewey_Oxberger on 2009-05-03
Ooooh, Now you get a chance to "level up" on your ALSA coding skills.

Poke around the ALSA website documentation and learn about things like "plug," "multi," and "slave."

You go to your asound.conf and define a virtual device that takes in the auto stream and sends it to any or all the hardware you want.  A multi that sends out hdmi and spdif should be no problem.  Then just point your apps to that device name (or make it default).

---

### Post by phroman on 2009-05-04
Just out of curiosity, why don't you use the SPDIF out to go into your  stereo receiver for all situations?  You can turn off the TV speakers entirely.

> There's a more complex situation, though. No one here but myself knows how to operate all this stuff, and normally its set to just play HDMI (or analog) through the TV: the A/V receiver is off.

It seems easier just to turn on the receiver and the TV and go.  Obviously you have to change the inputs on the receiver to whatever device your using, ie cable box or dvr, but that's not too bad.  Just a thought...

---

### Post by kilowhisky on 2009-05-15
> **Dewey_Oxberger said:**
> Alsa is one cool can of code.

Your PC has several hardware audio devices.  The analog stuff, SPDIF, and now HDMI all are supported in your PC's hardware.

To see your PC's hardware just:

```
aplay -l
```

That will show what hardware you actually have.

Alsa lets programs get to this hardware by defining virtual devices.  By default it created several virtual devices for you.  All you have to do is tell a program to use that virtual device and it'll work.

See the virtual devices with:

```
aplay -L
```

In mythtv, if you want to use one of those devices (like say the hdmi device) you would need to go to the audio configuration tab (Utilities/Setup, Setup, General, Next until you see the Audio Tab).  Then fill in the audio info.  It's case sensitive:

```
Audio output device: ALSA:hdmi     <-- you have to type it in

```

If you find the hdmi device doesn't have all the features you need (I don't think it converts other sample rates or channels to it's format) ALSA lets you make your own virtual devices that do whatever you need.

Here is an example of a asound.conf that makes an hdmi device, then a "fix the rate and channels on hdmi" device, then adds a volume control to hdmi so the pc can control the volume.  There are some instructions in the file.  With a little luck it'll fill in the missing parts of the puzzle for you.

Thank you so much. I have M3n78-Pro and it works almost perfectly. This allows mythtv to work perfectly the only problem is that I can not change the volume via mythtv with this.   Is there any way to fix this?

---

### Post by shae marks on 2009-05-16
hi    Just installed a fresh copy of 9.04 on my ASUS M3N78-EM. There are a couple of recurring problems from 8.10; one is the very soft analog audio output and lack of HDMI audio. I haven't yet tried the SPDIF.

The symptom, which has always been present on this board, is audio that's about half the volume of a cable box input (granted, that one is via HDMI); but even at 100% on the TV, the Asus audio is just not even at a "normal" listening level, and there is a strong background noise undertone from the TV, i.e. the TV amp gain is set too high. Not the case at all with the cable box. Same problem with headphones or external amplified speakers -- the mobo just isn't putting out enough mV.

Yes, the master and PCM and all other volumes are dialed up to 11 (so to speak). Updated to latest BIOS -- no difference. Only the "ALSA-Default" setting in Myth's config produces any audio output at all. All others are silent (after restarting the frontend); SPDIF passthrough passes the digital feed right into the analog out, with less than pleasing results.

ALSA finds the HDMI output for the built-in NVidia 8300, but I can't get it to show up in the Myth front end audio configurations.

[[URL=http://mielofon.com/model/shae_marks]shae marks]("http://ubuntu-virginia.ubuntuforums.org/%5BURL=http://mielofon.com/model/shae_marks%5Dshae%20marks%5B/URL%5D")[/URL]

---

### Post by Dewey_Oxberger on 2009-05-16
How do you change the volume?

Go back a page in this thread and download the asound.conf that I attached to an earlier post.  It has the instructions in it.

---

### Post by DrJohn999 on 2009-05-17
> **shae marks said:**
> ...audio that's about half the volume of a cable box input (granted, that one is via HDMI); but even at 100% on the TV, the Asus audio is just not even at a "normal" listening level, and there is a strong background noise undertone from the TV

Close the Myth Frontend, start a terminal session, and run alsamixer. Here you'll find the "Front" channel, which is probably set to less than 100% volume. Set it to 100%. This solved the low volume situation for me on this board.

You can leave a mixer running, start the frontend, and then use alt-tab to switch to the mixer and experiment with changes there, without having to navigate down Myth's configs to get the the audio page.

See the earlier posts in this thread for more info on SPDIF, HDMI, etc. with this board.

---

### Post by jjstiff on 2010-05-07
[http://forums.boxee.tv/showthread.php?t=9617](http://forums.boxee.tv/showthread.php?t=9617)

I'm running 9.10 and I've got this Motherboard
M3N78-EM

It's not really the motherboard... : The problem is that Ubuntu is using Pulse Audio and not ALSA by default

The link above tells you to add an ALSA sink to Pulse in the config file /etc/pulse/default.pa
Add one line of code after the commented line.

```
#load-module module-pipe-sink
load-module module-alsa-sink device=hw:0,3
```

Put the second line only. then re-login or Restart the computer.
My HDMI device was hw:0,3 as I figured from the first response on this topic [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)
With a different MOBO/GFX Config your card,device may be different.

Then, set up ALSA more correctly:
```
cat /proc/asound/devices
mplayer file.wav -ao alsa:device=hw=0.0
```
try hw=0,1 hw=0,2 ... whatever the cat shows for audio playback.. to decide which devices you will manage. For me, I am choosing hw=0.0 (analog) and hw=0,3 (hdmi).

edit .asoundrc or /etc/asound.rc to include
```
pcm.my_hdmi_device
{
    type hw
    card 0                #<first number>
    device 3              #<second number>
}

pcm.my_analog_device
{
    type hw
    card 0
    device 0
}

pcm.my_sound_out my_hdmi_device

pcm.!default my_sound_out
```
now
```
sudo /etc/init.d/alsa-utils restart
mplayer file.wav -ao alsa:device=my_hdmi_device
mplayer file.wav -ao alsa:device=my_analog_device
mplayer file.wav -ao alsa:device=my_sound_out
mplayer file.wav -ao alsa:device=default
mplayer file.wav -ao alsa
```

So I have two output devices, but I can access five different ways.
ALSA is all set.


Then setup PulseAudio: see top of this reply but change the line to
```
load-module module-alsa-sink device=my_sound_out
```

Now when I move my computer from my HDMI to my VGA/analog I edit .asoundrc
```
pcm.my_sound_out my_analog_device
```
And finally run again:
```
sudo /etc/init.d/alsa-utils restart
```

So I have an easier way to switch audio sinks without re-login.

I wish this were all part of the Notification Area in the Panel.

Good Luck, -JJ

Need a wav? Goto: [http://www.eventsounds.com/startup.htm](http://www.eventsounds.com/startup.htm)

---

