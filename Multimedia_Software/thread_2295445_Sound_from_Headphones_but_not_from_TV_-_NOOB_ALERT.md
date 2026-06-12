---
title: "Sound from Headphones but not from TV - NOOB ALERT :)"
date: 2015-09-18
forum: Multimedia Software
---

### Post by Mitchell_Reed on 2015-09-18
Hi Everyone,

I recently started using Lubuntu 15.04 and my only regret is that I didn't start using it sooner.  I built an HTPC using a Dell Minitower with integrated video and audio.  I am using a DVI to HDMI cable to connect the video and a 3.5mm to RCA for Audio.  My problem is that while I can hear the sound if I plug in headphones I can't hear it on the TV.  I had this TV hooked up to another computer previously and it worked fine, so I know it's not the TV.

I came across this thread which seems to be the same issue:
[http://ubuntuforums.org/showthread.php?t=2233149](http://ubuntuforums.org/showthread.php?t=2233149)

I went to Intel's website and ran their installer to update my video drivers.  It installed drivers, but still no luck.  I installed and can see the sound playing in Pavucontrol but no settings changes seem to make any difference.

I attempted to run the code Papibe suggested:
[COLOR=#000000]Code:[/COLOR]
/var/log/Xorg.0.log
but received a permission denied error, and I admit I have absolutely no clue about EDID.  Any help with this issue would be greatly appreciated.  Thank You!

Mitch

---

### Post by Bucky Ball on 2015-09-18
I know you've looked in PAVControl, but have you checked you have the right device chosen in 'Playback' tab? There could be one hiding further down the window. Also check the 'Output tab'.

---

### Post by Mitchell_Reed on 2015-09-18
The Playback tab doesn't appear to have any choices.  Just list Systems Sounds - Mono with a slider set at 100.  Below that is Mplayer2 with sliders and the sound bar.

Output has speakers (unavailable) Line Out (Plugged In) and Headphones (unplugged).  I have it set at Line out, the other two didn't make a difference although I didn't expect them to.

Thanks!

---

### Post by Bucky Ball on 2015-09-19
You need to get an audio stream going to have a stream in Playback or an active stream in Output. 

Play a song (or vid with sound), open PAVC, check what we've mentioned. 

You will only have system sounds in Playback if you don't have anything else running. Playback shows active streams. You currently don't have any. :)

---

### Post by Mitchell_Reed on 2015-09-19
I appreciate your help.  I had a video with sound running in the background when I checked previously.  I just tried again and Mplayer2 (Gnome Media Player) is the audio stream and I can "see" the sound in the sound bar in the playback tab.  I still couldn't see any choices per se, just the System sounds on top with the MPlayer2 on bottom.  I can post a screenshot of what I'm seeing if that helps?  Maybe I'm missing something obvious...

Thanks!

---

### Post by Bucky Ball on 2015-09-19
Well if you have sound routed to the MPlayer, then that needs to be output to the correct device. Check in Outputs and Playback again and change the 'Port' settings to something else. You should be routing mplayer to a hardware device using the 'Port' dropdown menu.

---

### Post by Mitchell_Reed on 2015-09-19
Here is what I am seeing.  Changing the ports on the output tab didn't help.  I can still hear the audio if I plug in headphones, but the TV won't pick it up for whatever reason, even though it's the same jack and it should work, ya know in theory anyway.

[ATTACH=CONFIG]264509[/ATTACH][ATTACH=CONFIG]264510[/ATTACH]

---

### Post by Bucky Ball on 2015-09-19
Ok. If you can plug the headphones in, sound is coming out, unplug headphones and plug in TV to the same socket and no sound is coming out the TV, this has nothing to do with Ubuntu and you already have it set up correctly. 

Look to issues with the TV setup. You may need to set the audio input to the RCAs and the video input to HDMI, *_on the TV_*. :)

---

### Post by Mitchell_Reed on 2015-09-19
That's what I initially figured too.  But here's the weird part.  I have another computer with Windows that has the same outputs, that I was able to hookup to this TV with these exact cables without issue, I tried another TV in my house with the same results.  The Windows computer worked with both, the Ubuntu computer only had video on both

When I was initially researching this, I came across the thread referenced in my first post which mentioned that the TV might be seeing a dummy sound signal coming from the video card that it believes is the sound and is automatically turning off the RCA audio, because it believes it's not necessary.  He had some instructions on how to check for this, and create a custom EDID that fixed the issue for him, but the code he provided only returned permission denied for me and I'm not exactly sure how to go about it.  Any thoughts?

Thanks again for all your help.

---

### Post by Mitchell_Reed on 2015-09-22
Ok, so after a lot more messing around, I wiped the drive and installed windows XP and once I installed the integrated sound card drivers, it immediately started playing sound on the TV.  So I am now certain it isn't an issue with the TV setup, but I am completely stumped here as to what could cause this.  Obviously, using Windows XP is an option, but I'd consider it an "if all else fails" option.  Any thoughts would be appreciated.  Thanks!

---

