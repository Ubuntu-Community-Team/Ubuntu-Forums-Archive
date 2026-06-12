---
title: "CMI8770 Surround Sound"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by KyRo1989 on 2007-12-29
I know there are many threads about this, but none of them could help me.
I am running the latest ALSA version (.15) with a Theatron Agrippa 7.1 (CMI8770) sound card. I can't get the card to play 5.1 surround sound.

First of all some information -

amixer:
> Simple mixer control 'Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 24 [77%]
  Front Right: Playback 24 [77%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%] [0.00dB] [on] Capture [off]
  Front Right: Playback 255 [100%] [0.00dB] [on] Capture [off]
Simple mixer control 'Synth',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line-In Mode',0
  Capabilities: enum
  Items: 'Line-In' 'Rear Output' 'Bass Output'
  Item0: 'Line-In'
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 31 Capture 0 - 7
  Mono: Playback 0 [0%] [off] Capture 0 [0%] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'Mic-In Mode',0
  Capabilities: enum
  Items: 'Mic-In' 'Center/LFE Output'
  Item0: 'Mic-In'
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [off]
Simple mixer control 'IEC958 5V',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Copyright',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Phase Inverse',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Select',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Valid',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Loop',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Four Channel Mode',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Software Master',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 255
  Front Left: 255 [100%]
  Front Right: 255 [100%]


Without a .asoundrc file, amarok (speaker arr. 5.1) and speaker-test (-c 6 surround51) play only on FR/FL. One special thing: if I run speaker-test this way > speaker-test -Dplug:surround51 -c 6  instead of > speaker-test surround51 -c 6, I get output on center and sub, but nothing on FR/FL. I never heard RR/RL with any setting.

So next try with this .asoundrc file:
```

# 6 channel dmix:
pcm.dmix6 {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 5120
    }
}

# upmixing: 
pcm.ch51dup {
    type route
    slave.pcm dmix6
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "ch51dup" # upmix first
    capture.pcm "hw:0"
}

# change default device:
pcm.!default {
    type softvol 
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"
```

Now I hear FR/FL and C/SUB ind xine and amarok, but once more no rear. I also have to plug Front to Side, which could be because this file is originally for CMI8738-MC6, not CMI8738-MC8, which is my one. xines output does not seem to be 5.1 but stereo. speaker-test without -Dplug remains as before, with the only difference that there is also output on center and sub while FR and FL output comes, but they both remain silent when their channel is tested.

I hope that is enough information for you to tell me whats wrong :)
I'm also playing around with OSS 4.0, but have problems too ([http://4front-tech.com/forum/viewtopic.php?t=2400]("http://4front-tech.com/forum/viewtopic.php?t=2400")). 

In the end I don't care if I have ALSA or OSS, if one of both works, so I'm also pleased if I get help for OSS :)

greets

---

### Post by mohbana on 2008-02-10
hey is this relevant to a auzen 7.1 x-plosion, the sound i am getting on linux is so lame comapred to windows, its so tempting for me just to move back to it because of that.

---

### Post by Dandeloreon on 2008-02-10
I had mixing issues with this, however i don't always use sorround sound, but i do have a working dmixing with this now, but i can't get the audio recording to always work as expected.
Command output: aplay -l
```

card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

It's worth noting that i use a string to detect my sound card, so i don't haft to reconfigure it if alsa decides to load it up funky... for mine, which is an Auzentech Xplosion the string turned out to be:

CMI8738MC8

with this, i'll now show you the system config file for alsa, namely,  /etc/asound.conf
```

#----------------------------------------------------------
#   Set Default Sound Card.
#----------------------------------------------------------


pcm.!default {
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
}

pcm.dsp {
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
}


pcm.dsp0 { 
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
} 

pcm.default { 
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
} 


#----------------------------------------------------------
#   Define Sound Cards.
#----------------------------------------------------------


#----------------------------------------------------------
# Main Card:  C-Media PCI CMI8738-MC8
#----------------------------------------------------------

# actual hardware device.
pcm.Cmedia_Dev{
    type hw
    card CMI8738MC8
}
pcm.Cmedia_Dev0{
    type hw
    card CMI8738MC8
	device 0
}

pcm.Cmedia_Dev1{
    type hw
    card CMI8738MC8
	device 1
}

ctl.Cmedia_Mixer0 { 
    type hw 
    card CMI8738MC8
}

# Asymetric audio mixing.
pcm.CMediaCard
{
	type			asym;
	capture.pcm		"CMediaCard_dsnoop";
	playback.pcm	"CMediaCard_dmixer";
}
# single channel mixer.
pcm.CMediaCardA{
     type plug
     slave.pcm CMediaCard_dmixer
}

pcm.CMediaCard_dsnoop {
	type      dsnoop;
	ipc_key   10092
	slave.pcm "Cmedia_Dev"; }

# Software playback mixing.
pcm.CMediaCard_dmixer {
	type                  dmix;
	ipc_key               10191;
	slave.pcm             "Cmedia_Dev1";
	slave.rate            48000;
	slave.channels        6;
	bindings {
		0 0
		1 1
		2 2
		3 3
		4 4
		5 5
		}
}


pcm.CMediaCard_dmixerA {
    type dmix
	ipc_key 10091
	slave {
        pcm         "Cmedia_Dev1"
#		period_time 0
#		period_size 1024
#		buffer_size 8192

		rate 48000
		channels 6
		}
	bindings {
		0 0
		1 1
		2 2
		3 3
		4 4
		5 5
		}
}



#----------------------------------------------------------
# Secondary Card:  NVidia CK804 ( Onboard )
#----------------------------------------------------------
pcm.Nvidia_HW{
    type hw
    card CK804
}
pcm.Nvidia_Dev0{
    type hw
    card CK804
	device 0
}

```

---

### Post by mohbana on 2008-02-12
I have a similar setup, auzen x-plosion 7.1.  I emailed them they said we should be expecting a linux driver in q4 2008, thats long!!!

**aplay -l**

> mohamed@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8770 [C-Media CMI8770], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8770 [C-Media CMI8770], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8770 [C-Media CMI8770], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**cat /proc/asound/modules**

>  0 snd_cmipci
 1 snd_usb_audio
 2 snd_hda_intel


**cat /proc/asound/cards**

> 
 0 [CMI8770        ]: CMI8738-MC8 - C-Media CMI8770
                      C-Media CMI8770 at 0xce00, irq 23
 1 [SP2208WFP      ]: USB-Audio - Monitor Webcam (SP2208WFP)
                      Mic-OmniVision Technologies, Inc.538-2640-07.08.09.6 Monitor Webcam (SP2208WFP)
 2 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 22
mohamed@ubuntu:~$ 


here is mine, this sort of works,  Note; flash doesn't work unless you comment/disable it, really strange.

You need to change the following according to what number is assigned to your sound card, where n is the card number mine was 0.

-card n
-hw:n,1 in pcm.!surround51
-hw:n in pcm.duplex

**cat .asoundrc**

> # ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/mohamed/.asoundrc.asoundconf>

# 6 channel dmix:
pcm.!surround51 {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 5120
    }
}

# upmixing: 
pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "ch51dup" # upmix first
    capture.pcm "hw:0"
}

# change default device:
pcm.!default {
    type softvol 
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

# <.asoundrc6.1>

---

### Post by ihorner on 2008-03-01
Brilliant stuff.  I just had to change the hardware locations to get it working on my machine.  I've been fighting with this for a couple of days.  My question of course, is if there has been any luck in finding a solution to the flash issue?

---

### Post by jai_mantravadi on 2008-03-16
I have an Auzentech X-plosion, and I was struggling to get Optical out enabled on it under Kubuntu (Currently running Hardy Alpha 5, but this should be more than version specific). Someone was struggling to get the Optical out using a turtle beach card (using the same chipset I believe), and all they had to do was unmute the "IEC958 output" which seems to enable stereo PCM. I'm not sure about the details of Passthrough, but at least I've got a digital optical connection to my stereo (and I just bought a cheap stereo capable of DPL2 and DTS Neo6, so I'll use that for multichannel upmixing). 
More on this discussion: [http://ubuntuforums.org/showthread.php?t=493887]("http://ubuntuforums.org/showthread.php?t=493887").
I just thought I'd post it since it seemed relevant to the discussion (and I was on this thread looking for the same info).
Cheers!
Jai

---

