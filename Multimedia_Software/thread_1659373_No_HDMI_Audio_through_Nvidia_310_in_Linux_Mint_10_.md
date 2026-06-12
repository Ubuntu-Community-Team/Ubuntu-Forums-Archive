---
title: "No HDMI Audio through Nvidia 310 in Linux Mint 10 Julia"
date: 2011-01-03
forum: Multimedia Software
---

### Post by Jags_FL on 2011-01-03
I've gone through countless threads in Ubuntu & other forums and have spent more than 15+ hours but still couldn't get HDMI audio working through Nvidia 310. Though video is playing fine on 2nd monitor _Samsung TV_ which is connected thru HDMI.

PC: Dell Vostro 430, Core i5-760, Nvidia G310
OS: Linux Mint 10 Julia 64bit
Nvidia Driver: 260.19.06
Nvidia X server display configuration: TwinView (clones)
Monitors: (1) Dell 1080p 23" (2) Samsung 1080p LCD HDTV

Gnome-Alsamixer and Sound Preferences screenshots are attached.

Any help is greatly appreciated.

---

### Post by Jags_FL on 2011-01-03
Attaching two more screenshots of Sound Preferences...

Thanks a million in advance!

---

### Post by lidex on 2011-01-04
I'm thinking you want to select high definition audio on the hardware tab as well as the output and select the correct profile.
These are two very useful links:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by Jags_FL on 2011-01-04
@ lidex

many thanks for the reply. In Sound Preferences > Hardware > When I select "High Defination Audio Controller (Digital Stereo HDMI Output)" > Under the Profile > I get 2 options (1) Digital Stereo (HDMI) Output or (2) Off. Right now "Digital Stereo (HDMI) Output" option is selected. And that's the one is selected under "Output" tab too.


Now under the Input tab (in Sound Preferences) I get only one option of "Internal Audio Analog Stereo".

From the link you provided, [http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250) , I've got this far:

-- since mine is Linux Mint 10 / Ubuntu 10.10, Alsa is already 1.0.23

cat /proc/asound/version

jags@mint ~ $ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23. 

-- aplay -l
jags@mint ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-- when I enter: cd /proc/asound/card1 : all I get is:

jags@mint ~ $ cd /proc/asound/card1
jags@mint /proc/asound/card1 $ 

I don't get following as described in [post#8 of the above thread]("http://ubuntuforums.org/showpost.php?p=9732345&postcount=8"):

```
cd /proc/asound/card1
cat eld#0.0
cat eld#1.0
cat eld#2.0
cat eld#3.0
```

so as mentioned in the same post:

```
If you have no eld data for any device you're in the same boat that I was at the start of this thread 
```

Now I'm trying to figure out what do I have to follow from that thread besides Alsa 1.0.23 (as it's there in Ubuntu 10.10 already)...

---

### Post by Jags_FL on 2011-01-04
when I enter cat eld* or cat eld, I get:

jags@mint /proc/asound/card1 $ cat eld*
cat: eld*: No such file or directory

---

### Post by Jags_FL on 2011-01-04
ok, I just installed Alsa 1.0.23 from ubuntu backports:

```
jags@mint /proc/asound/card0 $ uname -r
2.6.35-22-generic

apt-cache search linux-backports-modules-alsa-2.6.35.22

jags@mint /proc/asound/card0 $ apt-cache search linux-backports-modules-alsa-2.6.35.22
linux-backports-modules-alsa-2.6.35-22-generic - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-alsa-2.6.35-22-server - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.

```

installed :
```
sudo apt-get install linux-backports-modules-alsa-2.6.35-22-generic alsa-utils
```

Reboot.

to discover all devices aplay -l

```
jags@mint /proc/asound/card0 $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and now I'm also getting following for cat eld*

```
jags@mint /proc/asound/card0 $ cat eld*
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		1
eld_valid		1
monitor_name		SAMSUNG
    
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x2d4c
product_id		0x667
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

```

I think now I need to "set up a proper pcm alias for a device(HDMI?)

any help is greatly appreciated...

---

### Post by lidex on 2011-01-04
I think you need to try the eld info for card 0 then once we find which device has the monitor info it should be easy.
```
cd /proc/asound/card0
cat eld#0.0
cat eld#1.0
cat eld#2.0
cat eld#3.0
```

---

### Post by Jags_FL on 2011-01-04
@ 
thanks again for the reply...


```
jags@mint /proc/asound/card0 $ cat eld#0.0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
jags@mint /proc/asound/card0 $ cat eld#1.0
monitor_present		1
eld_valid		1
monitor_name		SAMSUNG
    
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x2d4c
product_id		0x667
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24
jags@mint /proc/asound/card0 $ cat eld#2.0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
jags@mint /proc/asound/card0 $ cat eld#3.0
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0
jags@mint /proc/asound/card0 $ 
```

---

### Post by lidex on 2011-01-04
So the correct device is 0,7. Try this:
```
gksu gedit /etc/asound.conf
```
Now paste in this text:
```
pcm.hdmi07 {
    type hw
    card 0
    device 7
}
pcm.!default hdmi07
```
Save. Close. Reboot.

---

### Post by Jags_FL on 2011-01-04
> **lidex said:**
> So the correct device is 0,7. Try this:
```
gksu gedit /etc/asound.conf
```
Now paste in this text:
```
pcm.hdmi07 {
    type hw
    card 0
    device 7
}
pcm.!default hdmi07
```
Save. Close. Reboot.

Thanks again but there's still no audio in TV :(

---

### Post by lidex on 2011-01-04
Have a go at this.

> If you have eld data for a device first unmute the device in alsamixer then test the device.

alsamixer

Select a device/channel and press m to unmute the devices/channels .MM denotes muted 00 is unmuted.

Test the audio with aplay *,* denotes whatever device you're testing eg 1,9 = plughw:1,9. hdmi:NVidia is a pcm alias used by the system

aplay -Dplughw:*,* /path/to/file.wav
aplay -Dhw:*,* /path/to/file.wav
aplay -Dhdmi:NVidia /path/to/file.wav

**/usr/share/sounds/alsa has some .wav files you can test

Once unmuted make sure you have an hdmi profile selected in sound preferences.


---

### Post by tjones00 on 2011-01-04
I got him routed to [http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926) it should resolve the pcm alias dmix/hw setup that's incomplete on the ion2 hdmi audio thread.

Edit: also fixed the pcm alias example in the ion2 hdmi audio thread post #8 it should now be "complete".

---

### Post by lidex on 2011-01-04
> **tjones00 said:**
> I got him routed to [http://ubuntuforums.org/showthread.php?t=1620926](http://ubuntuforums.org/showthread.php?t=1620926) it should resolve the pcm alias dmix/hw setup that's incomplete on the ion2 hdmi audio thread.

Edit: also fixed the pcm alias example in the ion2 hdmi audio thread post #8 it should now be "complete".

Thank You sir!

---

### Post by Jags_FL on 2011-01-06
@ tjones00, zAPPzAPP & lidex    

Thanks a million guys... =D>

Finally HDMI Audio is working on Samsung TV through Nvidia G310.

To sum it up for anyone who come across this thread:

(1) As described in [here by tjones00]("http://ubuntuforums.org/showpost.php?p=9732345&postcount=8"), I installed Alsa 1.0.23 from ubuntu backports(even though my OS was Linux Mint 10/Ubuntu 10.10):

```
jags@mint /proc/asound/card0 $ uname -r
2.6.35-22-generic

apt-cache search linux-backports-modules-alsa-2.6.35.22

jags@mint /proc/asound/card0 $ apt-cache search linux-backports-modules-alsa-2.6.35.22
linux-backports-modules-alsa-2.6.35-22-generic - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-alsa-2.6.35-22-server - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
```

```
sudo apt-get install linux-backports-modules-alsa-2.6.35-22-generic alsa-utils
```

(2) Then as described in [here by zAPPzAPP]("http://ubuntuforums.org/showpost.php?p=10121401&postcount=3"), I created/edited asound.conf

```
sudo gedit /etc/asound.conf
```

and entered the following:

```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm dmixer
}
```

Reboot and voila HDMI audio was working just fine on Samsung TV. 

To avoid the issue of low quality sound as mentioned by zAPPzAPP, I did make one change in VLC Media Player: VLC > Tools > Preferences > Audio > Output Module > **ALSA audio output** > Save.

The only question I still have... **is it possible to have audio through computer headphones/speakers too along with HDMI?** 'coz otherwise whenever you wanna listen to anything in headphones/speakers you've to change "Output" in Sound Preferences...

---

### Post by tjones00 on 2011-01-06
So you want to have your hdmi digital and analog cards active at the same time?

It seems more and more people want this setup. It is possible but it will require some work to create a combined card and is specific to each system. It should involve tweaking alsa and possibly pulseaudio with custom configurations.

If you visit the xbmc forums I believe there are a couple posts in the HOWTO section about creating a combined card. The alsa wiki and the arch wiki should also have information on this as well.

 eg. [http://alsa.opensrc.org/index.php/TwoCardsAsOne](http://alsa.opensrc.org/index.php/TwoCardsAsOne)

[http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)

from the mythtv link

> It is possible to configure ALSA to output PCM audio simultaneously on  both the analog and the digital outputs.  This means that any 2-channel  audio MythTV decodes will be sent to both outputs.  It does not mean  that you will get AC-3 or DTS through the digital output and analog  audio through the analog output.  To configure ALSA this way, add the  following at the end of the above /etc/asound.conf or .asoundrc file: 

---

### Post by lidex on 2011-01-06
Using pulseaudio for simultaneous output an option here? Perhaps you can try it. Using paprefs (pulseaudio preferences), check the option in the last tab. To quote markbuntu:
> Simultaneous Output

In the PA Device Chooser/Configure Local Sound Server/Simultaneous Output there is a check box for Simultaneous Output to all local sound cards. If you select it this will add a new Output Device in the PA Volume Control listings
Simultaneous output to ALSA PCM.......(all your sound hardware devices).......
You can select this device in the PA Volume Control just like any other and it will direct streams to all your sound devices simultaneously so you can have sound in your speakers and usb headset etc at the same time.

---

### Post by tjones00 on 2011-01-07
I think I've read about some people doing it with pulseaudio. It'd be worth a shot.

---

### Post by Jags_FL on 2011-01-09
tjones00 & lidex

Many thanks, first I tried the MythTV link, then paprefs (to get Simultaneous output to High Defination Audio Controller Digital Stereo (HDMI), Internal Audio Analog Stereo), and finally tried both together. Rebooted the PC after each option. But there's still no audio in PC headphones/speakers.

Another thing I noticed is that no matter what I choose in Sound Preferences > Output tab _out of 3 possible options_ there is still no audio in PC headphones/speakers. I guess I need to change/edit /etc/asound.conf or something. This is how my /etc/asound.conf now:

```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

#---------------------------------------------------------------------------------------------

pcm.!default {
  type plug
  slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
}

pcm.stereo {
  type plug
  slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
}

ctl.stereo {
  type hw
  card 0
}

pcm.multi {
  type multi
  slaves.a.pcm "analog-hw"
  slaves.a.channels 2
  slaves.b.pcm "digital-hw"
  slaves.b.channels 2
  bindings.0.slave a
  bindings.0.channel 0
  bindings.1.slave a
  bindings.1.channel 1
  bindings.2.slave b
  bindings.2.channel 0
  bindings.3.slave b
  bindings.3.channel 1
}

ctl.multi {
  type hw
  card 0
}

```

-- Sound Preferences screeshot attached.

---

### Post by tjones00 on 2011-01-09
You're missing the big custom .asoundrc/asound.conf posted above the mixed card call that defines analog-hw and digital-hw plus the controls. You're calling upon multi analog-hw + digital-hw yet they haven't been defined.

Read it very carefully and try to understand whats going on even take notes on the side for yourself.

Start reading at.
**Setting up ALSA's .asoundrc, Properly **

---

### Post by lidex on 2011-01-09
Seem to be getting into the twilight zone here but have you got pavucontrol installed? It may be a simple levels issue. Also alsamixer settings for internal card - use F6 to select it.

---

### Post by tjones00 on 2011-01-11
Have you made any headway Jags_FL? I know people have asked about this topic in the past it would be good to have a reference post :)

---

### Post by Jags_FL on 2011-01-12
tjones00 & lidex

guys very sorry for the delayed reply as I was travelling...

(1) > **lidex said:**
> Seem to be getting into the twilight zone here but have you got pavucontrol installed? It may be a simple levels issue. Also alsamixer settings for internal card - use F6 to select it.

yes, pavucontrol was there by default and I tried mute/unmute from there but it didn't help (I've attached 2 screenshots).

(2) > **tjones00 said:**
> You're missing the big custom .asoundrc/asound.conf posted above the mixed card call that defines analog-hw and digital-hw plus the controls. You're calling upon multi analog-hw + digital-hw yet they haven't been defined.

Read it very carefully and try to understand whats going on even take notes on the side for yourself.

Start reading at.
**Setting up ALSA's .asoundrc, Properly **

I'm getting more confuse the more I did read this page:
[http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly](http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly)

I obviously need help to "define analog-hw and digital-hw plus the controls" please... thanks again

---

### Post by Jags_FL on 2011-01-12
forgot to attach 3 screenshots in earlier post...

---

### Post by Jags_FL on 2011-01-12
As per the MythTV wiki page, do I need to define following in order "*to configure ALSA to output PCM audio simultaneously on both the analog and the digital outputs*" ??

-- pcm.!default
-- pcm.stereo
-- ctl.stereo
-- pcm.multi
-- ctl.multi

---

### Post by tjones00 on 2011-01-13
##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".It's a pretty generic template just make sure you fill in the blanks properly. 

Each of these needs a definition. Just substitute your numbers into the template. If you are unsure what any of this stuff is read the comments in the template and consult the alsa wiki .asoundrc page. [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

Take your time to figure it out there is no rush. If you're unclear about what you're doing stop and recap then make sure you understand what you're doing before pushing forward.

If you just push forward without understanding any of it and it doesn't work you will be stuck because you will not know how to go about troubleshooting the error in a logical stepwise approach. Remember computers are all about algorithms if one step is incorrect or misconfigured you will not receive the expected result. 

pcm.!default
ctl.!default

pcm.analog
ctl.analog

pcm.mixed-analog
ctl.mixed-analog

pcm.digital
ctl.digital

pcm.mixed-digital
ctl.mixed-digital

pcm.analog-hw
ctl.analog-hw

pcm.digital-hw
ctl.digital-hw

pcm.dmix-analog
ctl.dmix-analog

pcm.dmix-digital
ctl.dmix-digital

Then the multi audio combo part with a new default pcm. The stereo and multi definitions are added at this point and call upon the earlier definitions. The entire asound.conf/.asoundrc is read from top to bottom so all of these definitions are required in the proper order.
 
pcm.!default

pcm.stereo
ctl.stereo

pcm.multi[FONT=monospace]
[/FONT]ctl.multi

---

