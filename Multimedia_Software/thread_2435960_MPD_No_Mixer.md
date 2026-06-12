---
title: "MPD: No Mixer"
date: 2020-01-29
forum: Multimedia Software
---

### Post by Furycd001 on 2020-01-29
HI.. I cannot adjust the volume of any playing audio in ncmpcpp. Whenever I press the volume up or down buttons, all I see is **"MPD: No Mixer"** appear at the bottom of the screen. I would like to use hardware over software if possible. Below is a copy of my mpd.conf. Many thanks....


```

music_directory "/home/furycd001/Music/"
playlist_directory "/home/furycd001/Music/Playlists/"
db_file "/home/furycd001/.mpd/mpd.db"
log_file "/home/furycd001/.mpd/mpd.log"
pid_file "/home/furycd001/.mpd/mpd.pid"
file "/home/furycd001/.mpd/mpdstate"
sticker_file "/var/lib/mpd/sticker.sql"
user "furycd001"
# group "audio"
bind_to_address "localhost"
port "6600"
#log_level "default"
#gapless_mp3_playback "yes"

audio_output {
    type "alsa"
    name "ALSA MPD"
    device "hw:0,0"
    mixer_type "hardware"
    mixer_device "default"
    mixer_control    "PCM"
    mixer_index    "0"
}

audio_output {
    type "pulse"
    name "PULSE MPD"
    server "localhost"
}

audio_output {
    type "fifo"
    name "FIFO MPD"
    path "/home/furycd001/.mpd/mpd.fifo"
    format "44100:16:2"
}

```

---

### Post by Furycd001 on 2020-01-30
Anyone able to help :?

---

### Post by Yellow Pasque on 2020-01-30
I notice you have options for 3 audio outputs in your .conf file. Which one are you using(/trying to use)?

---

### Post by Furycd001 on 2020-01-31
> **Yellow Pasque said:**
> I notice you have options for 3 audio outputs in your .conf file. Which one are you using(/trying to use)?

I'd like to use alsa if possible and have pulse as a backup.I don't know why the fifo part is there, but I've removed it....

---

### Post by Furycd001 on 2020-02-03
Anyone :?

---

### Post by Yellow Pasque on 2020-02-03
So are you trying to use this on a system with or without pulseaudio? I think all Ubuntu flavors come with pulseaudio, so that's the output you want to use to make things easy. mpd should automatically detect and use that if it's enabled.
Can you look at the mpd log and verify which sound output is used?

If you are trying to use the ALSA hardware device directly, that gets more complicated.

---

### Post by Furycd001 on 2020-02-03
Can confirm that pulseaudio is installed. In the log file for mpd I can see the following....

> 
Feb 02 22:44 : exception: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM


---

### Post by Furycd001 on 2020-02-06
So.. I've tried a bunch of things from around the web, but none of them have worked. Below is what my config currently looks like. Any help appreciated....

> **FYI:** Audio plays just fine. I just cannot adjust the volume without getting the error mentioned previously..

```

music_directory "/home/furycd001/Music/"
playlist_directory "/home/furycd001/Music/Playlists/"
db_file "/home/furycd001/.mpd/mpd.db"
log_file "/home/furycd001/.mpd/mpd.log"
pid_file "/home/furycd001/.mpd/mpd.pid"
file "/home/furycd001/.mpd/mpdstate"
sticker_file "/var/lib/mpd/sticker.sql"
user "furycd001"
# group "audio"
bind_to_address "localhost"
port "6600"
#log_level "default"
#gapless_mp3_playback "yes"audio_output {
	type "alsa"
	name "ALSA MPD"
	device "hw:0,0"
	mixer_type "hardware"
	mixer_device "default"
	mixer_control	"PCM"
	mixer_index	"0"
}

#audio_output {
#	type "pulse"
#	name "PULSE MPD"
#	server "localhost"
#}

```

---

### Post by Yellow Pasque on 2020-02-06
> **jonny6 said:**
> So.. I've tried a bunch of things from around the web, but none of them have worked. Below is what my config currently looks like.

You commented out the pulseaudio output. It seems like you keep trying to do this the hard way (or maybe I don't understand mpd enough). What happens when you comment out the ALSA output and force pulseaudio output to be used? Anyway, if you insist on using ALSA output:

> Failed to read mixer for 'My ALSA Device': no such mixer control: PCM 

This means that you need to change these lines:
```
	mixer_control	"PCM"
	mixer_index	"0"
```

To see what controls you have for your card:
```
aplay -l
amixer scontrols
```

---

### Post by TheFu on 2020-02-06
I know nothing, but thought mpd was the server and needed a client to actually playback any audio. That would mean the client would be responsible for volume, mixing, etc.
[https://www.musicpd.org/clients/](https://www.musicpd.org/clients/) seems to confirm my guess about the client/server nature.

The client can be on the same machine or over a network.

---

### Post by Yellow Pasque on 2020-02-06
> **TheFu said:**
> I know nothing, but thought mpd was the server and needed a client to actually playback any audio. That would mean the client would be responsible for volume, mixing, etc.
The client can be on the same machine or over a network.

OP already stated s/he was using ncmpcpp. I'm assuming it's on the same machine.

---

### Post by Furycd001 on 2020-02-07
> **Yellow Pasque said:**
> OP already stated s/he was using ncmpcpp. I'm assuming it's on the same machine.

Yes I am using ncmpcpp with mpd & they are both on the same machine. When I was setting up mpd for the first time I followed the section at the bottom of [**"this"**]("https://help.ubuntu.com/community/MPD") page for setting up mpd as a user service.. Btw if using pulse would be easier than alsa then I don't mind switching, but I do get the same problem when using pulse. Anyway here's the outputs of those two commands & many many thanks for all of the help so far....[B]


aplay -l[/B]

```

furycd001 > aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20753/4 Analog [CX20753/4 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


**amixer scontrols**

```

furycd001 > amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'Headphone',0
Simple mixer control 'Speaker',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958',1
Simple mixer control 'IEC958',2
Simple mixer control 'IEC958',3
Simple mixer control 'IEC958',4
Simple mixer control 'Beep',0
Simple mixer control 'Capture',0
Simple mixer control 'Auto-Mute Mode',0
Simple mixer control 'Internal Mic Boost',0

```

---

### Post by Yellow Pasque on 2020-02-07
Can you describe a little more about what you are trying to do with mpd? Do you want it to be the only program that can access the sound card and play sound? If so, you'll have to do some extra configuration (making sure your user is in the audio group and tha pulseaudio has not grabbed the hardware device (hw:0,0).

---

### Post by Furycd001 on 2020-02-07
> **Yellow Pasque said:**
> Can you describe a little more about what you are trying to do with mpd? Do you want it to be the only program that can access the sound card and play sound? If so, you'll have to do some extra configuration (making sure your user is in the audio group and tha pulseaudio has not grabbed the hardware device (hw:0,0).

Just want to play some music in ncmpcpp & be able to adjust the volume when necessary. Hmmm no I don't want that.. I just want playback without any stutter, interruptions or high cpu usage. Sometimes I need to close waterfox, before ncmpcpp / mpd will open, but that doesn't bother me really....

---

### Post by Yellow Pasque on 2020-02-07
> Just want to play some music in ncmpcpp & be able to adjust the volume when necessary. Hmmm no I don't want that.. I just want playback without any stutter, interruptions or high cpu usage.
Theoretically, that shouldn't happen with pulseaudio, but bugs do exist and sometimes it's easier to work around them. 
So, if you want to try using the hw:0,0 device directly
1. Check if your user is in the audio group:
```
groups
```
If not, add it:
```
sudo usermod -a -G audio furycd001
```

2. Make sure you uncomment this line in your mpd.conf
```
 group "audio"
```

3. Stop all programs playing audio (like waterfox)

4. Try starting ncmpcpp with pasuspender:
```
pasuspender ncmpcpp
```

I'm not sure about these lines in mpd.conf
```
mixer_type "hardware"
mixer_device "default"
mixer_control	"PCM"
```
If you're using onboard audio, you won't have a hardware mixer (that's why only one program can play sound at a time if you don't use a software mixer like pulseaudio).

---

### Post by Furycd001 on 2020-02-09
> **Yellow Pasque said:**
> Theoretically, that shouldn't happen with pulseaudio, but bugs do exist and sometimes it's easier to work around them. 
So, if you want to try using the hw:0,0 device directly
1. Check if your user is in the audio group:
```
groups
```
If not, add it:
```
sudo usermod -a -G audio furycd001
```

2. Make sure you uncomment this line in your mpd.conf
```
 group "audio"
```

3. Stop all programs playing audio (like waterfox)

4. Try starting ncmpcpp with pasuspender:
```
pasuspender ncmpcpp
```

I'm not sure about these lines in mpd.conf
```
mixer_type "hardware"
mixer_device "default"
mixer_control    "PCM"
```
If you're using onboard audio, you won't have a hardware mixer (that's why only one program can play sound at a time if you don't use a software mixer like pulseaudio).

Thank you for the detailed reply. Checked and my user is already in the audio group & uncommented that line in my .conf. Tried launching ncmpcpp with that command, but the same thing still happened. I tried also commenting out the alsa_output part of my config & then uncommenting the pulse_output to use that instead, but again got the same message along the bottom. Completely stumped. If I was to switch to a software mixer in my config, would I notice any performance issues or cpu increase ??

---

### Post by Yellow Pasque on 2020-02-09
> **jonny6 said:**
> If I was to switch to a software mixer in my config, would I notice any performance issues or cpu increase ??

You shouldn't, because you probably don't have a hardware mixer if using onboard Conexant CX2075x audio. Maybe look at alsa info to see some of the more advanced settings for your card: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Furycd001 on 2020-02-10
> **Yellow Pasque said:**
> You shouldn't, because you probably don't have a hardware mixer if using onboard Conexant CX2075x audio. Maybe look at alsa info to see some of the more advanced settings for your card: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Just ran **"alsa-info"** & here's the [output..]("http://alsa-project.org/db/?f=9253099d4d6ba207205d2d082a6a64e7bc88f0d8") Also ran **"amixer"** & here's it's [output..]("https://termbin.com/55gg") Read through it both, but don't know what to take from either or what to put in my audio_output section. I feel like a complete noob....

---

