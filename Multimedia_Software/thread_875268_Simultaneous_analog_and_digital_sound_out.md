---
title: "Simultaneous analog and digital sound out"
date: 2008-07-30
forum: Multimedia Software
---

### Post by jlindbergh on 2008-07-30
Hi!
I have sound working on my Asus P5B-Deluxe with the Intel AD198x chip. My question is if I can have the sound played back on the analog and digital device at the same time (if not playing a movie using passthrough AC3 or something like that - in that case I'm fine with digital only). 

My "aplay -l" looks like this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And when in System->Preferences->Sound I can choose either 
[LIST]
[*]Autodetect
[*]AD198x Digital
[*]AD198x Analog
[*]ALSA
[*]OSS
[*]PulseAudio
[/LIST]
Autodetect, OSS and PulseAudio all give the same errors:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
The AD198x ones outputs sound exactly where one might expect: Receiver (digital) and Headphones (analog) respectively. And if I chose ALSA i get analog sound only.

What I want is to select ALSA or PulseAudio and get output on both the analog and digital devices. Is this possible? 

Grateful for any help!
/jlindbergh

---

### Post by jlindbergh on 2008-08-08
I feel it's time to continue this thread.

I've been doing fine with having my sound settings set to ALSA (not AD198x Analog/Digital) for around a week now. Somehow I got sound in both my headphones and digitally to my receiver, just the way I wanted. Don't ask me how that happened. I've even been playing an occasional video using (s)mplayer with AC3 S/PDIF pass-through. Worked great!

Today I was listening to music as usual through my receiver, watching a movie (non-passthrough). Everything was ok until I played a video sample that used AC3 passthrough. After closing smplayer and trying to play some music through amarok I could no longer get regular audio to the receiver! I couldn't get audio to the receiver playing a regular (non-passthrough) movie either! I now have sound in my headphones only :(

I tried re-opening smplayer, fiddling with enabling-disabling S/PDIF passthrough but no luck. I also tried the old Ctrl-Alt-BkSpace, but no difference. Same result after restarting the whole system..!
I've went through and experimented with both the gnome volume control and alsamixer settings, but everything seems to be as it was earlier. I also went to System->Preferences->Sound and saw that all comboboxes were set to ALSA. I tried changing to AD198x Digital but I didn't even get a test beep to the receiver! Now when I just tried that again I actually got a beep in the receiver, but I still can't get sound from amarok or smplayer through. Well I can if I play pass-through material, but I'd like to have sound in my livingroom when playing regular music too!

Long post, but I'm troubled and confused. Can anybody please shed some light on what it is that controls where (ALSA) sound gets output? Right now I feel like there's some kind of midget (or gnome?) in the computer that arbitrarily chooses where it likes to send my sound...

Please help.

regards
/jlindbergh

---

### Post by jlindbergh on 2008-08-10
Is there some way to duplicate my audio using something flashy in ~/.asoundrc 
> copy hw:0,0 -> hw:0,1
Perhaps..?

---

### Post by Oswald1 on 2008-09-15
Hiyah,

Not an expert on any of this, but I've been struggling with very much similar problems as you.

First of all, I believe you've run into this bug when playing ac3 content:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632)

Somehow in certain circumstances (playing ac3 and then trying to play something 'regular' through spdif locks the spdif eternally to passthrough). The bug was reported already years ago, but not fixed yet.


Anyways I needed simultaneous playback through analog and digital as well and after some hours of asoundrc tweaking and occasional swearing I ended up with this kind of a file:

```

pcm.!default {
	type plug
	slave.pcm ttable

}

pcm.ana {
        type hw
        card 0
        device 0
}

pcm.digi {
        type hw
        card 0
        device 1
        format S16_LE
        rate 48000
}

pcm.both {
        type multi
        slaves {
                a {
                        pcm "digi"
                        channels 2
                }
                b {
                        pcm "ana"
                        channels 2
                }
        }
        bindings {
                0 {
                        slave a
                        channel 0
                }
                1 {
                        slave a
                        channel 1
                }
                2 {
                        slave b
                        channel 0
                }
                3 {
                        slave b
                        channel 1
                }
        }
}

pcm.ttable {
  type route
  slave.pcm "both"
  ttable.0.0 1
  ttable.1.1 1
  ttable.0.2 1
  ttable.1.3 1
}


```

I'm pretty convinced this could be done much more elegantly, but at least it works for me :)

Hope this is of some help.

---

### Post by Oswald1 on 2008-09-16
Like I suspected, something simpler can be used to achieve the same effect, namely:

```

pcm.!default {
	type plug
	slave.pcm "copper"
}

pcm.copper {
	type copy
	slave.pcm "hw:0,0"
	slave.pcm "hw:0,1"
	slave.pcm "hw:0,0"
}

```

Not sure why I need the third slave.pcm line in the copper part, but I'm suspecting it's got something to do with copying the first slave to the next ones. I'm figuring this out pretty much through trial and error here, as I'm having hard time finding any proper description of these asoundrc types etc.

---

### Post by Oswald1 on 2008-09-20
Dang, this introduces a new problem. Apparently only on program can access this new 'device' at time. So if for example I'm surfing the net and something like youtube is accessing the audio device, I cannot start a music player. Actually I need to close the whole browser before I get sound from Rhythmbox even if the browser isn't playing any sounds at the moment.

I'm guessing this has something to do with software/hardware mixing. I suppose if you directly play through hw:0,0 or something like that, some hardware mixing takes place. Further on, perhaps something built around dmix might be helpful here, but haven't figured out yet how to make it work.

Any clues?

---

### Post by Oswald1 on 2008-09-27
From the alsa-wiki:

> A very interesting and potentially extremely useful aspect of this plugin is using it combined with the default plugin name. In theory this means all applications that have native ALSA support will share the sound device. In practice not many applications are able to take advantage of this functionality yet.

Is this up to date information? At times I get things working nicely, especially when simply testing with aplay on many consoles and so on, but for example starting up rhythmbox changes things so that sound disappears from the digital amp.

Anyone reading these posts? :)

---

### Post by markbuntu on 2008-09-27
You should be able to turn on the Digital Output in your sound mixer by clicking on the SPDIF or IEC958 check box. Some sound cards have a analog/digital check box that can disable your analog sound output so watch out for that.

Anyway, you can look here for more info:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

---

### Post by jlindbergh on 2008-10-18
> **Oswald1 said:**
> From the alsa-wiki:



Is this up to date information? At times I get things working nicely, especially when simply testing with aplay on many consoles and so on, but for example starting up rhythmbox changes things so that sound disappears from the digital amp.

Anyone reading these posts? :)

Yes I'm reading, and I really appreciate you posting here!

But... to be honest I'm in a period where I feel that my time is better spent on my Windows XP partition where I can do what I want without constantly running into situations where I have to spend hours googling, researching and tweaking to be able to accomplish the same things.

---

### Post by markbuntu on 2008-10-19
OK, bye.

---

### Post by Oswald1 on 2009-01-13
Good lord! It happened again!

Once again I made the grave mistake of starting playback of a non ac3-encoded movie clip while watching a dvd passing throught ac3 and boom, no more 'regular' sound through digital output.

To be clear, I've gone through every possible volume slider from 0 to 100 and mute and no mute and still just nothing.

Also to be clear, the only thing I did was to start the 'regular' playback on top of the passthrough stream.

Also I don't seem to get anything out even when trying to use aplay with -D hw:0,1 either.


This thoroughly sucks. Any great hints?

---

### Post by Oswald1 on 2009-01-18
Although, I haven't been able to fix the problem so far even with the new info, this might be useful:

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/95940](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/95940)

At least they claim removing the asound.state file would fix the passthrough problem. Also it sounds like a plausible place for the problem to preside, as it really seems like the state of things gets borked and so on.

But like I said, at least for me only removing the file and rebooting didn't fix anything, but at least the file looks more reasonable now, without entries from long gone sound cards and what not.

Please let me know if this helps you fixing things and how was it done exactly.

---

### Post by Oswald1 on 2009-01-18
And now I have sound! I can't believe how satisfying it is to hear a test beep sound from a speaker...

So it appears the asound.state was corrupted somehow. What I had to do to get things working again, was to first stop alsa with

sudo /etc/init.d/alsa-utils stop

Then edit 

/var/lib/alsa/asound.state

and chage the corresponding parts to these:

```

	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}

```

Then restart alsa with

sudo /etc/init.d/alsa-utils start

And finally make sure that volumes and the iec958 checkboxes are set.

---

### Post by Oswald1 on 2009-11-04
lol

Installed Karmic and simultaneous digital analog audio sweetness is gone again. 

Any quick tips? The whole sound preferences system is different from what it used to be and I'm lost :)

---

### Post by han555 on 2009-11-05
> **Oswald1 said:**
> lol

Installed Karmic and simultaneous digital analog audio sweetness is gone again. 

Any quick tips? The whole sound preferences system is different from what it used to be and I'm lost :)

+1.  I have a PW5 DH motherboard with Intel audio and I want to run the spdif out to my receiver for movies and surround sound and have the analog line out running into a crossfader so I can DJ mp3s with my vinyl.  I can only output to one or the other though.  I have pulseaudio set for simultaneous output but the virtual device it creates is tied to either digital or analog.  Any ideas?

---

### Post by jlindbergh on 2009-11-06
Oswald1, I found the settings after a while.. If you right click on the systray sound icon and select Preferences, or go to System->Preferences->Sound then click the Hardware tab you can experiment with the options in the Profile dropdown list.

I have an Intel AD198x card and it lists about 20-something options there. Some are Analog Surround 2.*, 4.* and 5.* etc, some are Digital only. However, the options that gives me both digital and analog are the three named *Analog Stereo Output*, *Analog Stereo Output + Digital Stereo Input* or *Analog Stereo Duplex*. So, now Im getting simultaneous output to my receiver and my headphones (as I did in Jaunty), yay!

A problem with it that I didn't have in Jaunty though: If I have the volume calibrated for the headphones, I hardly get any sound from the receiver (this made me think it didn't work for a while). And vice versa when I get ok volume from the receiver, my headphones almost blows up..
I can compensate for this by tweaking in the alsamixer, but as soon as I touch the pulse/ubuntu-volume settings it ruins my alsamixer "compensation".

---

### Post by han555 on 2009-11-06
I don't have any options for both digital and analog outputs there.  Does this mean my soundcard can't support that or is there a config file where I can define new combinations?

---

### Post by jlindbergh on 2009-11-06
> **han555 said:**
> I don't have any options for both digital and analog outputs there.  Does this mean my soundcard can't support that or is there a config file where I can define new combinations?I have no idea, but I noticed I wrote it down wrong the first time. I've changed it now, cause none of my outputs say Analog & Digital out. (Duplex means in/out)

---

### Post by han555 on 2009-11-06
Right, I have the same thing.  Analog out with digital in or vice versa, but no analog and digital out.

---

### Post by bbobbo on 2010-04-02
i'm experiencing the same problem in lucid beta1.

i'm using onboard sound (analog devices ad1985) with the s/pdif connected to my receiver and the line out connected to my monitor which has built-in speakers.

i started with a completely fresh install.

under sound preferences, i chose 'analog stereo duplex' like so:

[IMG]http://img144.imageshack.us/img144/1548/screenshotsoundpreferen.png[/IMG]

i'm using vlc as the media player. i have alsa audio output selected like so:

[IMG]http://img576.imageshack.us/img576/9028/screenshotpreferences.png[/IMG]

i played a non-ac3 video file, and i got sound simultaneously via s/pdif and line out. after playing an ac3-encoded video file (which came through the s/pdif output fine), i tried to play another non-ac3 encoded video. but this time sound only came out of the monitor speakers.

unfortunately, i only seem to have two analog options--i'm missing the 'analog stereo output + digital stereo input':

[IMG]http://img576.imageshack.us/img576/1548/screenshotsoundpreferen.png[/IMG]

i can get non-ac3 videos to play either via s/pdif (by choosing one of the digital stereo options) or via line out (by choosing an analog option) but not both at once.

---

### Post by akg4y on 2010-07-11
Has anyone been successful with this?  I am running Ubuntu 8.0.4 via a bootable USB drive on my Apple TV from this thread:
[http://forum.xbmc.org/showthread.php?t=74992](http://forum.xbmc.org/showthread.php?t=74992)

I have the Apple TV as part of a video distribution system in my house and so am trying to do the same thing because some of my video endpoints have surround sound while others do not.  The ALSA version is 1.0.19 on my system.  I tried to update using the update script on these forums but it fails at some point along the way.  


Is it possible to use the asoundrc file to duplicate the audio from any given source.
If the source is digital/5.1 then the first copy would either passthrough SPDIF or would be sent channel by channel to the correct speakers, and the second copy would be downmixed to analog and sent to all available speakers.

If the source is analog then the first copy gets sent to each available speaker via SPDIF, and the second copy gets sent out the analog out.

Is that even possible, or is this all a pipe dream?

---

### Post by ikiller on 2010-12-18
After a lot of trying I got this working on Lucid on my zotac ion box, I use this for xbmc.

Here goes, I wanted iec598 (spdif) and simultaneous on board analog.

I finally found this website:
[http://www.randomwalking.com/project.php?project=mediapc](http://www.randomwalking.com/project.php?project=mediapc)

Step 1 - Sudo Edit:  /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf
I just had to uncomment the bottom example definition

[Profile output:analog-stereo+output:iec958-stereo+input:analog-stereo]
description = Foobar
output-mappings = analog-stereo iec958-stereo
input-mappings = analog-stereo

I didn't even change the description even though it would probably be a good idea.

Step 2 - install paprefs using apt-get or whatever you like (this is a pulse audio pref gui)

I then rebooted (may not be necessary)

Step 3 - I opened the paprefs System > Preferences > Pulse Audio Preferences
 Navigate to the "Simultaneous Output" tab and select "Add virtual output...".
reboot machine again (this time very necessary)

Step 4 - open normal sound preferences: System > Preferences > Sound
In the "Hardware" tab select the Profile named "Foobar" or whatever you used for your description in step 1.   
Then select the "Output" tab and choose the device labeled  "Simultaneous output to Internal Audio Digital Stereo (IEC985), Internal  Audio Analog Stereo" or whatever matches what you are trying to do.

Step 5 - I went back to xbmc and the correct output option then was available in the sound settings.

Worked great, and didn't have to muck about with those unintelligible asound files.  I have heard a bunch of people complain about pulse audio, but this was way easier than making a new asound file.

---

