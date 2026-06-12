---
title: "Bluetooth Headset default audio device"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by superdexter on 2006-08-05
I am using Kubuntu Drapper.  Blutooth headset is working for skype and any other program I set manually.

I'm looking for a way to make the headset the systemwide alsa default device.  I cannot find the setting in the Control Center.  My goal is that any program trying to use the alsa default device would use the bluetooth headset without any additional per program config change.

I am using ALSA exclusively without any issues and I would prefer not to use any other sound system as that could cause problems for the bluetooth/skype config.

Can anyone tell me either of a GUI tool setting or of a command line option that would change the entire system to defult sound to the bluetooth headset (once paired)?

---

### Post by superdexter on 2006-08-11
I'm a little surprised that I have received NO response to this post.  I should take this to mean that no one else is interested in such a function?  Or that I posted this in the wrong place.  

If this is the wrong place to post this question, or the question is badly phased, could someone offer some advise on what to change about my post to get a reply?

---

### Post by Concrete on 2006-08-11
Hi there!
If someone can tell me how to configure a Bluetooth (MSI) and connect my phone (Nokia 6680) via that bluetooth, and copy files, picture from phone to PC.

Thakns and sorry for off-topic question! ;)

---

### Post by superdexter on 2006-08-11
[This thread ]("http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset")got me up 100%.  I have completed that and now I am looking for a system wide setting to use the sync'd bluetooth headset.

Good luck!

---

### Post by zzarr on 2007-06-12
I'm running fiesty fawn (ubuntu/gnome) and I'm having the same kind of question as superdexter.

Concrete, have you tested obexftp? (or obexfs?)

If not, you should have a look at it.

---

### Post by davidgro on 2007-11-22
Solution found!

In my .asoundrc I set up my headset with the Bluetooth device as suggested elsewhere:

```
pcm.bluetooth {
   type bluetooth
   device 00:11:22:33:44:55 #Headset
}
```

and got that working in xmms directly.

Then I found the advice in [http://alsa.opensrc.org/index.php?title=FAQ026]("http://alsa.opensrc.org/index.php?title=FAQ026")

and added this to make bluetooth the default:

```
pcm.!default {
   type plug
   slave.pcm "bluetooth"
}
```

after testing it I discovered that the left and right channels were swapped, so I found a solution here: 
[http://www.volkerschatz.com/noise/alsa.html]("http://www.volkerschatz.com/noise/alsa.html")

and re-wrote it a bit to match the style of the above block (which I figure must be more recent syntax)

So I commented out the above block and added this one:

```
pcm.!default {
   type route
   slave.pcm "bluetooth"
   ttable {
      0.1 = 1
      1.0 = 1
   }
}
```

Now (after restarting "the sound system" in the KDE control panel - Gnome probably can do similar) I get full A2DP stereo sound from at least mplayer. (Note that I had to mess around a lot with its settings to make it work right) and I am working on other apps (no luck yet with xine).

My full ~/.asoundrc is (roughly) as follows:

```
pcm.bluetooth {
   type bluetooth
   device 00:11:22:33:44:55 #Headset
}

#pcm.!default {
#   type plug
#   slave.pcm "bluetooth"
#}

pcm.!default {
   type route
   slave.pcm "bluetooth"
   ttable {
      0.1 = 1
      1.0 = 1
   }
}
```

---

### Post by Bossieman on 2007-11-24
Davidgro, thanks, i finally got my Sony Ericsson HBH-DS970 working (kind of).
The problem is that when i play a movie in mplayer or use Amarok it lags heavy.


Mplayer gives:

AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1035.8 kbps (126.4 kbyte/s)
Clip info:
 Software: transcode-1.0.2
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12  [fs] [zoom]
[AO_ALSA] Write error: Broken pipe-0.046  26/ 26 13%  0%  2.9% 0 0 
[AO_ALSA] Trying to reset soundcard.
[AO_ALSA] Write error: Broken pipe-0.029  50/ 50  8%  0%  2.5% 0 0 
[AO_ALSA] Trying to reset soundcard.
[AO_ALSA] Write error: Broken pipe-0.040  70/ 70  6%  0%  2.5% 0 0 
[AO_ALSA] Trying to reset soundcard.
[AO_ALSA] Write error: Broken pipe-0.030  73/ 73  8%  0%  2.7% 0 0 
[AO_ALSA] Trying to reset soundcard.
[AO_ALSA] Write error: Broken pipe-0.027  92/ 92  7%  0%  3.0% 0 0 
[AO_ALSA] Trying to reset soundcard.
gnome_screensaver_control()31 ct: -0.031  98/ 98  7%  0%  2.9% 0 0 

Does anyone know what I should try next?
my soundcard is 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by Bossieman on 2008-01-11
BUMP

No solutions for streaming sound with no lag to BT-device?

---

### Post by davidgro on 2008-01-14
Eventually, in an effort to solve all the compatibility issues I tried PulseAudio, and that was a complicated mess which I don't want to type out here, but in the end resulted in most everything working... at a lag of about 200ms. (which any media player I used was able to correct for pretty easily)
I then determined that I got a lag of about 100ms with this: 

[http://store.kyocera-wireless.com/product_detail.aspx?productID=5065]("http://store.kyocera-wireless.com/product_detail.aspx?productID=5065")
(A 'Bluetooth® Black 3.5mm Audio Adapter' - plugs into a regular headphone jack)

and I decided that it is simply the easiest solution at the moment.  (If the buttons on the headset worked with the direct connection, that would be a different matter, but for now I am not losing any functionality using the dongle)

---

### Post by learnerofskills on 2008-07-14
this solution to make my bluetooth headset the default audio device seems to work great for me but...

It seems that no more than one application can access my bluetooth headset at the same time. Is there a way to allow audio mixing for this device?

Also it would be nice to be able to toggle the default audio device back and forth between my speakers and my bluetooth headset without having to reboot. Can someone please tell me how this can be done?

---

### Post by learnerofskills on 2008-07-16
I have found out that I can switch back and forth between my laptop and bluetooth headset as the default device by commenting out the lines
```
#pcm.!default {
#   type plug
#   slave.pcm "bluetooth"
#}
```
and then running as root
```
/etc/init.d/alsa-utils restart
```
to switch back I just uncomment the lines and restart the alsa-utils daemon again.

---

