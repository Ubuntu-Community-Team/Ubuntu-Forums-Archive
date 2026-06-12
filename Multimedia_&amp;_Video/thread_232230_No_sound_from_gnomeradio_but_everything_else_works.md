---
title: "No sound from gnomeradio but everything else works fine"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by whein on 2006-08-08
I have a Hauppauge PVR-350 installed.  I know the card is good because I had it running under Windows2000 and had both FM radio and TV working.  After a few tries on Ubuntu 6.06 I got the ivtv drivers installed and got video and audio from the tv tuner playing through mplayer.  I also have sound working through all the rest of the programs I've tried to run on Ubunutu so far (before, after, and during gnomeradio being open.)
When gnomeradio is open, I can tune it to the different frequencies and the little signal strength indicator seems to be strong (three green bars) when tuned to stations I know exist in my area and weak/nothing when tuned to frequencies I know do not reach my house.  So I'm pretty sure the tuner part is working.  I have the radio device set to /dev/radio0 (which is what the ivtv page indicated it used) and I've tried setting the mixer to just about every option on there.  I have the volume turned up in the gnomeradio main window.  I don't have the mute turned on.  My speakers are on and turned up.  The system sound is unmuted and turned up.  And yet silence from gnomeradio.  I even tried recording the channel to an MP3 file and to a WAV file and then opening that with XMMS but they were dead silence as well.  What am I missing?
-Will

---

### Post by whein on 2006-08-09
Ok, another data point.  Using the
```
ivtv-radio -f 94.5
```
command I got (good) sound out of my speakers.  Startled the heck out of me because I thought it would be similar to the ivtv-tune command where you had to open an external viewer to use it...  So I tried to open up gnomeradio to use this feed and it said that /dev/radio0 was already in use by another program so it could not function, etc.  Even stranger, and I wish I had copied the output to my usb drive so I could quote it here, the ivtv-radio command said something about /dev/video24.  I thought it should have been going through /dev/radio0 especially since it blocked gnomeradio from using it.  I even tried shutting down the ivtv-radio command and then opening /dev/video24 using gnomeradio, but it did not indicate any signal present and did not put out any sound.  Anyone know what the heck is going on?
-Will
:confused:

---

### Post by Bseater on 2006-08-14
I'm having the exact same problem with a PVR-500. Anyone have any ideas?

---

### Post by whein on 2006-09-01
/bump

:(  Still nothing.  I tried installing gradio, and still no sound.  I *know* the card works because ```
ivtv-radio -f 105.9
``` works great.  I double checked the permissions on /dev/radio and /dev/radio0 using nautilus and everybody has read permission.  As before, the little signal strength icon seems to indicate a signal, but nothing comes out.  Is there something to do with ALSA vs OSS that I can mess with?  If so, I'll need detailed instructions, I'm still learning my way around the box.  Should I uninstall and reinstall?  Compile from source?  Sacrifice a small child?  Help!
-Will

---

### Post by xinix on 2006-10-06
Bump, same as above.  Everything seems to work fine.  Except sound output.  I'm on a Hauppauge PVR-150.

Edit:
The CLI command gives me no sound.  I get this output when I try it:
```
Running: aplay -f dat < /dev/video24
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
```

---

### Post by the_mechanical on 2007-05-03
I have a Terratec Cinergy HT PCI.
It's also everything except radio working fine. I tried gnomeradio but it says:
```
could not open "/dev/mixer"!
```
So i can't switch anything in the mixer-source in the preferences.
Is gnomeradio working with OSS? I only use ALSA.

Anny suggestions?

---

### Post by Krikke_wl on 2007-07-25
I stumbled upon this problem, but nobody seems to have a solution for this?? Got the same problem at home, Hauppauge PVR-500, Ubutu Feisty...

Thanks in advance,
Kriikke

---

### Post by genti on 2007-11-16
Check the sound for Analog Mix, It seems it is muted by default.
Go to Volume Control (double click the sound icon) Edit > Preferences and add all the channels that you think should be included.
Try playing with them.

---

### Post by ariel on 2007-12-08
Same problem here. SAA7134-based card, working fine, gnomeradio fires up, and when configured to point to /dev/radio0 it scans and finds the channels and all.

Activated all output and input channels in the audio panel / alsamixer, and still no joy. anyone has got this to work?

ps. I don't see any 'analog mix' though.

---

### Post by brainformat on 2007-12-12
i have saa7134 and it workes fine to me...
what you need is to make a file named, for example, [COLOR="DarkRed"]radio.sh[/COLOR]
paste this text in it:
```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/audio1 -t ossdsp -w -r 32000 /dev/dsp &
gnomeradio --mixer=/dev/mixer:pcm
wait gnomeradio
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80% unmute
```

save it where ever you want and close. after that you can start it from terminal using command
```
sh radio.sh
```
if it shows error, look into [COLOR="DarkRed"]/dev[/COLOR] directory. maybe you don't have [COLOR="DarkRed"][COLOR="DarkRed"]audio1[/COLOR][/COLOR] file in it. if it is so, look for some other [COLOR="DarkRed"]audio[/COLOR] file in the same folder (audio2, audio3...) if you find it change the path in the script's second line to that file....

if you what, you may create a desktop louncher. the path must leed to [COLOR="DarkRed"]radio.sh[/COLOR] and not to [COLOR="DarkRed"]gnomeradio...[/COLOR] but first do this:
```
 sudo chmod 755 radio.sh
```
the same thing works with [COLOR="DarkRed"]tvtime,[/COLOR] only, you must write tvtime instead of [COLOR="DarkRed"]gnomeradio[/COLOR] in script...

---

### Post by ariel on 2007-12-12
that was awesome, thanks brainformat!

Now the curious thing is, the script activated the radio output, ... even if sox is not installed in my system (I could install it... but now i don't need to :))

Looks like the trick was the /dev/mixer parameter in gnomeradio...

Question: now... how do I turn the radio off :) sounds funny but I can't stop it. Gnomeradio doesn't have a stop button, and when I close it, the audio from the tuned radio stays on, very funny :)

thanks!

---

### Post by brainformat on 2007-12-14
you have that option at gnomeradio's preferences.

---

