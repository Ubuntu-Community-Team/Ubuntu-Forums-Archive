---
title: "[SOLVED] Firefox, flash and bluetooth headset"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by LilYoda on 2008-02-10
Hey y'all

I have a Motorola stereo headset, working fine and all, I have a "a2dpd" alsa device I use to send the sound to it, it works in most applications, but not in firefox and flash applets.

I read somewhere that flash writes blindly to /dev/dsp.  Is there a workaround so that I could listen to youtube videos using my a2dpd alsa device?

Lemme know

---

### Post by redman5087 on 2008-03-29
I have the same problem
please help

---

### Post by kwilliam on 2008-04-06
Add me to the list of users wanting a workaround. I'm using a bluetooth headset with:
```

pcm.bluetooth {
   type bluetooth
   device 00:13:1B:XX:XX:XX
   profile "hifi"
}
```
in my .asoundrc.

I set the default ALSA device to "bluetooth" in the KControlCenter. [Xine seems to crash occasionally using the Bluetooth but] essentially it WORKS, in Amarok, Kaffeine, VLC [as long as xine doesn't crash.]

But Flash simply hangs (tested in Konqueror or Opera, I don't have Firefox installed). In YouTube, for instance, the progress bar will stop moving shortly after I hit the play button, as if it's waiting for the sound to get sent so the video stays syncronized. The sound doesn't come out the PC speakers, which is good, but it doesn't come out the bluetooth headset either. I was under the impression that Flash used ALSA, but obviously something is amiss!

**If anyone knows how to get Flash to work with a bluetooth headset, that would be greatly appreciated. **Would that "newfangled" PulseAudio help? I saw it has a plugin for Flash, but I didn't know if it could output to bluetooth. ([This page](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Tryingpulse) made it sound like Pulse+bluetooth was untested.)

---

### Post by kenelbow on 2008-04-23
Add me to the list of people looking for a solution.  I followed the guide at [http://fosswire.com/2008/01/11/a2dp-stereo-linux/#comment-32989](http://fosswire.com/2008/01/11/a2dp-stereo-linux/#comment-32989) and had great results with most applications, but still have not sound for firefox+flash with my bluetooth headphones.  It just uses my laptop's Intel soundcard instead.

---

### Post by varunbhatbm on 2008-04-25
> **kenelbow said:**
> Add me to the list of people looking for a solution.  I followed the guide at [http://fosswire.com/2008/01/11/a2dp-stereo-linux/#comment-32989](http://fosswire.com/2008/01/11/a2dp-stereo-linux/#comment-32989) and had great results with most applications, but still have not sound for firefox+flash with my bluetooth headphones.  It just uses my laptop's Intel soundcard instead.

Thanks a lot man!!!
The link you provided, solved my problem which was bugging me from 1.5 months..
This brings my last dependency with vista to end.. :)

---

### Post by kwilliam on 2008-04-29
I guess varunbhatbm didn't need sound in Flash then? I want the bluetooth PRIMARILY for flash - watching YouTube, Colbert, imeem.com... sigh.

---

### Post by strudlez on 2008-05-07
I got it working by installing libflashsupport (pulseaudio support for flash), then following the steps here:
[http://ubuntuforums.org/showthread.php?t=757436](http://ubuntuforums.org/showthread.php?t=757436)

Also, to make it the overall default device, change your sound settings to use pulseaudio, and in Pulse Audio Device Chooser (padevchooser), set the default sink to alsa_output.bluetooth (or whatever you set your blueooth device name to).

---

### Post by LilYoda on 2008-05-11
I followed the message threads above, and managed to get pulseaudio to work

My headset's device is detected in pulseaudio, and I see firefox using pulseaudio, so in theory it should work.  But the thing I haven't found yet is how to redisrect an audio stream from one device to another???

---

### Post by strudlez on 2008-05-11
You can change the stream device by right-clicking the stream in the playback tab of pulseaudio volume control.

---

### Post by LilYoda on 2008-05-13
Wow, I confirm it seems to work

Quick summary (more info in all the links listed above

If like me, you were using the old bluetooth daemons (a2dpd, headsetd), remove them from startup.
Make sure you install pulseaudio, libflashsupport, and basically all the pulseaudio related modules (paman, padsp, etc...)

change /etc/firefox/firefoxrc
```
# which /dev/dsp wrapper to use
FIREFOX_DSP="esd"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```

Change /etc/asound.conf
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
pcm.bluetooth {
type bluetooth
device 00:07:A4:B7:4D:24
profile "auto"
}
```
In the above, the line "device" should have your bluetooth's headset's MAC address

in /etc/pulse/default.pa, add
```
load-module module-alsa-sink device=bluetooth
load-module module-alsa-source device=bluetooth
```

Don't forget to add your users to the groups pulse, pulse-access and pulse-rt.  I also had to re-enable avahi-daemon and dbus daemon.  Not sure why I had them removed from startup in the past.

Launch padevchooser, and check the box that makes sure it's launched at every session startup.

Reboot, to make sure all daemons are started with the correct options, etc...

With this, when you open a youtube video in FF, you should still hear the sound in your normal speakers.  Then, click on the padevchooser tray icon, launch the volume control, you should see the audio stream coming from FF.  right click on it, and send it to bluetooth.  Now all audio coming from FF will be send to the bluetooth sink.

---

