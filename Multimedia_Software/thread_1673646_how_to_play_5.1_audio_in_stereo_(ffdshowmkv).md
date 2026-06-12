---
title: "how to play 5.1 audio in stereo (ffdshow/mkv)?"
date: 2011-01-22
forum: Multimedia Software
---

### Post by pickarooney on 2011-01-22
I have an issue with the voice channel on certain MKV fikles being really low compared to the music and sound effects. I've found an explanation and solution for Windows for this, but nothing for linux. 

[http://www.codecguide.com/faq_playback_issues.htm](http://www.codecguide.com/faq_playback_issues.htm)
[http://forums.anandtech.com/showthread.php?t=254724](http://forums.anandtech.com/showthread.php?t=254724)
[http://shark007.net/forum/Thread-5-1-no-voices-low-volume-MKV](http://shark007.net/forum/Thread-5-1-no-voices-low-volume-MKV)

Does anyone know how to get the same kind of result in smplayer or xine or VLC?

For info, playback is fine through headphones - no channel imbalance.

---

### Post by BicyclerBoy on 2011-01-22
This solution may not be applicable to you.
The nicest solution is external down-mix in a HT amp/AVR because it works properly.
This output to AVR could be AC3 S/PDIF or 5.1 LPCM HDMI.

The down-mix 5.1 to 2ch stereo is bugged/broken/not-implemented in ffmpeg thus it is not right for VLC in 2ch mode.

With windoze play 5.1 audio (analogue 2 ch headphones) with VLC by starting playback & then selecting the 5.1 audio device. This works correctly.

In linux the 5.1 audio device must exist for the above VLC trick to work.
There is someway to down-mix the 5.1 surround audio device to output on the 2 ch stereo device.
 (alsa does the down-mix correctly)
[http://www.spinics.net/linux/fedora/alsa-user/msg09154.html](http://www.spinics.net/linux/fedora/alsa-user/msg09154.html)
this may break pulse-audio.

So I do not play 5.1 audio in Linux (unless DTS/AC3) because I have no solution to down-mix. (do not want 5.1 analogue output)

It is possible that players based on xine engine may down-mix correctly.
10.10 Totem is based on xine again..

---

### Post by pickarooney on 2011-01-23
I didn't understand much of that, unfortunately. I gather it's pretty complicated for something that should eb very straightforward though!

---

### Post by BicyclerBoy on 2011-01-23
Sorry for the confusion..
The whole linux audio scene is confusion...

For an application to play 5.1 audio (because its own down-mix is broken) there must be an audio 5.1 device real or virtual.

So you need a media player with correct down-mix, maybe the xine engine works because ffmpeg does not. 
Or..
The alsa plugins package libasound2-plugins can provide a52 (encoder) & vdownmix (down mixer).

So (in theory) you should be able to install the alsa plugins & setup vdownmix.

/usr/share/doc/libasound2-plugins/vdownmix.txt
This has an example of how to edit the /etc/asound.conf

Edit1:
I can report NO success in making a52 or vdownmix work with any media player..
aplay -D a52:0 11k16bitpcm.wav   This actually works...

Edit2:
VLC will play multi-channel into the digital 5.1 IEC958/AC3 a52 plug-in device.
The channel ordering of the a52 plug-in is wrong C & FR & LFE are mixed up..(another ffmpeg bug)

---

### Post by BicyclerBoy on 2011-01-24
For completeness & to correct errors.

VLC does do a some down-mix of 5.1 to 2.0. Confirmed with an AC3 audio test sample.
Centre front seemed loud enough.
My impressions of the VLC down-mix is that it does sound quite right (live music) compared to a good Marantz AVR down-mix.

You can down-mix (crude) using alsa plug (no extra software needed)
[http://www.volkerschatz.com/noise/alsa.html](http://www.volkerschatz.com/noise/alsa.html)
/etc/asound.conf
```

pcm.51to2 {
  @args.0 SLAVE
  @args.SLAVE { type string default "plughw:0,0" }
  type route
  slave {
    pcm $SLAVE
    channels 2
  }
  ttable {
    0.0= 0.3
    2.0= 0.3
    4.0= 0.18
    5.0= 0.21
    1.1= 0.3
    3.1= 0.3
    4.1= 0.18
    5.1= 0.21
  }
}

```
This allows you to adjust the individual levels..(sum=1)

Alsa plug-in vdownmix could be option if you can make it work.

Note: the channel orders for alsa, AC3 & SMPTE (& FLAC) are all different.

---

### Post by pickarooney on 2011-01-24
So basically I ned to edit/create this asound.conf file and I should then get an extra volume option for 5.1 in VLC? Sorry if I seem a bti obtuse; I've always been very confused by sound in linux.

---

### Post by BicyclerBoy on 2011-01-24
I think every one is confused by Linux audio..
A basic understanding is probably required before trying anything.

Editing asound.conf is one way.
I think if you use this as default audio output device you can use the pulse audio mixer (or similar) to get an easy GUI multi-channel volume control.

Is there a plug-in/filter/module for VLC that gives you multi-channel volume control ?
VLC will only play to default pulse or alsa device.

AFAIK Mplayer lets you adjust the multi-channel volume balance from the cmd line.
Mplayer lets you easily play to any audio device/sub device.

If it all goes wrong you can just delete the asound.conf file..

It is a shame that pulse audio does not provide virtual multi-channel down-mix & AC3 encoding etc because this would be more usable.

---

