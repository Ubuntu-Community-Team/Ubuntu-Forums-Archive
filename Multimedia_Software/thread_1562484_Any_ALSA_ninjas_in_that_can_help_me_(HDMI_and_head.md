---
title: "Any ALSA ninjas in that can help me? (HDMI and headphone)"
date: 2010-08-27
forum: Multimedia Software
---

### Post by geekyhawkes on 2010-08-27
Hey,

I am trying to get audio from both HDMI and my line out (headphone) connections on my ubuntu machine.  

I have a recent version of ALSA (using the update script posted here, thanks), and my asound.conf is below (as I am guessing this is the solution but cause of my problem currently).

```
#new section

pcm.analog {
	type plug
	slave.pcm "analog-hw"
	hint {
	show on
	description "analog output"
	}
}

ctrl.analog {
	type hw
	card 0
	device 0
}

#################
#################

# pcm.mixed-analog [
#	type plug
#	slave.pcm "dmix-analog"
#	hint {
#	show on
#	description " Mixed analog output"
#	}
#}

#ctrl.mixed-analog {
#	type hw
#	card 0
#}

###########SECTION ABOVE DISABLED######

# ctl.optical {
#        type hw
#        card 0
#        device 1
# }

########### Section above disabled, no pcm optical defined#######

pcm.hdmiout {
        type hw
        card 0
        device 3
}


ctl.hdmiout {
        type hw
        card 0
        device 3
}


pcm.analog-hw {
	type hw
	card 0
	device 0
}

ctrl.analog-hw {
	type hw
	card 0
}
# MIGHT NEED A DEVICE ADDING IN HERE ABOVE


pcm.dmix-analog {
	type dmix
	ipc_key 1234
	slave {
	pcm "analog-hw"
	period_time 0
	period_size 1024
	buffer_size 4096
	rate 48000
	}
}

ctrl.dmixanalog {
	type hw
	card 0
}


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

ctrl.!default {
	type hw
	card 0
}

pcm.myth {
	type plug
	slave {
		pcm multi
		rate 48000
		channels 4
	}
	ttable.0.0 1.0
	ttable.1.1 1.0
	ttable.0.2 1.0
	ttable.1.3 1.0
}

ctrl.myth{
	type hw
	card 0
}	

######Probably in the wrong place#####


# pcm.optical {
#        type hw
#        card 0
#        device 1
#}


pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
	slaves.b.pcm "analog-hw"
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

Any help on where i have gone wrong?  

Thanks

---

### Post by AlphaLexman on 2010-08-27
You should take a look at 'alsactl'
```
man alsactl
```

---

### Post by geekyhawkes on 2010-08-27
I must be dumb, i looked but couldnt really work out how it would take me forward

---

### Post by geekyhawkes on 2010-08-28
So with a bit more investigation, it appears that i dont really have any anaolgue output at all, when i connnect anything to the line out i dont really get static or anything.

I have checked aplay -l and the anaolgue device is listed there (as 0).  I think the issue must be in my asound.conf but i cannot work out what i need to do.

Can anyone offer me some help?

Thanks

---

### Post by AlphaLexman on 2010-08-28
> **geekyhawkes said:**
> I am trying to get audio from both HDMI and my line out (headphone) connections on my ubuntu machine.  
What do the physical audio connections look like?

[LIST]
[*]'3.5 mm' is a standard analog headphone plug
[*]'hdmi' is a 19 pin connector 13.9 mm x 4.45 mm
[*]'optical digital" plugs are more square-like with a fiber-optic cable in the middle
[/LIST]
 Both Alsa and PulseAudio treat each option differently, and require different settings.

---

### Post by geekyhawkes on 2010-08-30
Ok, should have been more clear, i want audio from HDMI and analog headphone plugs via ALSA.  

I dont appear to have any output at the moment from either the 5.1 outputs or the headphone connectors, but do have hdmi audio.  

Currently HDMI feeds my tv for audio, but i also want the headphone output so i can feed my wireless speakers with music (for around the house etc). 

Thanks for any help, heres hoping!

---

### Post by geekyhawkes on 2010-08-31
Anyone see what im doing wrong with this? Im going no where fast at the moment!

---

### Post by tripmix on 2010-08-31
I don't think you can output to both devices simultaneously. If the HDMI goes to your tv or a amplifier there is usually a minijack audio-out plug in those and plugging the headphones in there should work. Otherwise the only solution I can think of would be to get a script or something that detects the minijack being plugged inn and switches output device automatically similar to how windows sometimes act. Pulse is fairly new and I don't know much about it so it might be possible to do something with that but chances are if you manage to get it to output from both devices simultaneously you'll get sound from both your hdmi device and you pc speakers when the headphones are unplugged. Also sound will be coming from you hdmi device even if you use the headphones so make sure you turn off the amplifier before watching pron :D

EDIT: I take back "it's not possible" I just ran these command to test
```
mplayer -fs -zoom -ao alsa:device=hw=0.0 file.mp3 &
mplayer -fs -zoom -ao alsa:device=hw=0.3 file.mp3
```
and I'm getting sound in both simultaneously, I have no idea how to start configuring it system wide though, sorry.

EDIT2: Not very familiar asound.conf but would it be possible to add multiple devices 
to the same option maybe? Like so
```
pcm.hdmiout {
        type hw
        card 0
        device 3
        device 0
}
```
or would that just mess things up?

---

### Post by geekyhawkes on 2010-09-01
No problem, i kind of assumed it would be fine so its good to hear the test prooved it.

I am not sure about running 2 devices in asound.conf, anyone any thoughts on this?  This would be a very simple solution to the problem!

---

### Post by lidex on 2010-09-03
Perhaps a simpler solution is using paprefs (pulse audio preferences). On the 'Simultaneous output' tab, enable the option 'Add virtual...'

---

### Post by geekyhawkes on 2010-09-04
Sounds good, i thought i wouldnt be using pulse as i use alsa?  do they run at the same time, or are they exclusive?  I dont overly want to mess around getting pulse in as alsa has been pretty bomb proof until now.

---

### Post by lidex on 2010-09-04
Pulse directs traffic and allows multiple outputs from alsa - sounds like just what you need.

---

### Post by geekyhawkes on 2010-09-07
Ok thanks, so im guessing then i dont need to do anything more than enable the virtual output as you directed in the previous post (as im running 10.04 mythbuntu on the system in question).

Thanks

---

### Post by geekyhawkes on 2010-09-09
Installing paprefs as we speak (had to go down the route of synaptic package manager to find it, some reason sudo apt-get install paprefs didnt work).  I will report back on it goes. Thanks for the help so far

---

### Post by Vigh on 2010-09-09
Hi, I have perfect audio, I use pulseaudio and alsa together. All sound is working on my Toshiba Laptop, including HDMI. I don't use asound.conf at all though. I just edit alsa-base.conf when I need to customize settings. Make sure you have linux-backports installed and the correct sound-card selected, it can be a bit tricky to set-up. I found using alsa-lucid-generic with pulseaudio works best, also make sure you have linux alsa backports installed. If you need help still just PM me and I will explain step by step.

---

### Post by geekyhawkes on 2010-09-09
Thanks, it isnt quite as easy as adding a simul output in pulse.  So i want this working on my mythbuntu setup with myth tv, what i have so far is the asound.conf as stated at the start of this thread.  I have installed paprefs and selected simul outputs with virtual device.  

If i go into mythtv and select pulse audio as the output device then i get nothing over HDMI or out of the 3.5 headphones.  I if select alsa:default in mythtv then i get audio from hdmi but nothing out of the 3.5 headphone (which was as my setup was behaving before the paprefs was installed).  

Thoughts?

---

### Post by geekyhawkes on 2010-09-26
Is anyone able to help me get this up and running?  I have selected simul output as detailed above but with no luck.  Google isnt giving me many clues on setting up pulse in this way and all of the asound.conf files i can find around the place dont quite give me the solution im after.  

Thanks in advance if anyone can help;

Andy

---

### Post by lidex on 2010-09-26
You may find useful info here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by geekyhawkes on 2010-09-28
Its a good guide thanks but doesnt really offer much to the solution i need.  The guide seems to suggest that i cannot have HDMI and analogue audio at the same time but I have found Nvidea forums that seem to suggest otherwise.  

I guess it might be worth a register there and see if someone can offer me a solution (sadly the asound.conf i found there doesnt give me the solution either)

---

### Post by ktbos on 2010-11-08
geekyhawkes, I'm exactly where you are: Ubuntu (10.10) with either HDMI or analog headphone jack working in MythTV but not both at the same time.  And I need both so I can send the HDMI stream to a remote room and still use the audio to speakers/headphones in the local room.  So I'm hoping you've got it worked out in the time since your last post?  Can you post again with update progress?  Thanks!!

---

### Post by ktbos on 2010-11-08
FYI, I've got mine working.  I followed instructions [at the KnoppMythWiki DigitalAudioHowTo]("http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo").  There's a sample asound.conf file in the section "Using asound.conf" which I copied into my asound.conf (replacing all of my previous failed attempts).  The only edits I needed to make were to change "analog-hw" to "front" and to change "digital-hw" to "hdmi" to match the existing values for my setup.  (Which I was able to find using 'aplay -L').  
With that setup, I was able to test with 'speaker-test -c 2 -P 2' and I got sound on both hdmi feed and on the analog output from the green mini-jack (rear panel and headphones).  Then, back into MythTV and switched the frontend audio to "ALSA:default" and confirmed that MythTV plays over both audio feeds now.  Done!

---

### Post by geekyhawkes on 2010-11-09
Thanks for this, i had never got it working before.  Hopefully this will work for me, I will give it a go at the weekend and report back!

---

### Post by geekyhawkes on 2010-11-14
Right, im getting confused now.  Does this need to go in .asoundrc or asound.conf?

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


I have tried it in asound.conf and when i select alsa:digital i get no audio out of hdmi or anaolgue.  When i go back to alsa:default then i get hdmi but no analoge.  

As an aside, when i go into aslamixer the headfone volume is at 00 but i cannot make it any louder, this could clearly be part of the problem.  

How do i go about getting the volume of the headfone louder?

---

