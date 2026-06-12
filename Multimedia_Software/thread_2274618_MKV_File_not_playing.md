---
title: "MKV File not playing"
date: 2015-04-21
forum: Multimedia Software
---

### Post by chandan-rattan-k on 2015-04-21
I am trying to run MKV video file, but its not playing. I have used the smplayer,GNOME player and VLC Player but none of them playing it. I am getting error with VLC player 

[COLOR=#ff0000]No suitable decoder module:[/COLOR]
[COLOR=#000000]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.

Sound is playing. Other players are not showing any error.

Kindly note that i am newbie in Ubuntu 12.04.

System : i5 processor, 3 GB RAM.[/COLOR]

---

### Post by dino99 on 2015-04-21
Glance at an app called 'pacpl' into 'synaptic'

---

### Post by Vladlenin5000 on 2015-04-21
> **9d9 said:**
> Glance at an app called 'pacpl' into 'synaptic'

Here we go again... Synaptic, like Ubuntu Software Centre, GDebi and dozens of others are just frontends for the exact same commands. Why add a difficulty layer of installing a software just to install another? There's a reason why Synaptic is no longer included: It isn't needed for regular users and certainly NOT needed for installing other software. 
If you like Synaptic just use it. Please keep the fetish for yourself ;)

@OP: No, you probably don't need a conversion tool either (pacpl) because if you don't have the necessary codecs to play you won't have it either for conversion. **So, for now, you need to find out what codec is required for the video streaming inside (MKV is just a container)**.

---

### Post by VMC on 2015-04-21
It would help to find out what's inside the 'mkv' file or if its damaged.
 'mediainfo' will display what's inside the 'mkv' file:

```
sudo apt-get install mediainfo
```

You should update first.

---

### Post by chandan-rattan-k on 2015-04-22
Installed the media GUI. Below is the screenshot.


[ATTACH=CONFIG]261462[/ATTACH]

---

### Post by mc4man on 2015-04-22
Read here, your options for hevc in 12.04 are a bit limited - 
[http://ubuntuforums.org/showthread.php?t=2272576](http://ubuntuforums.org/showthread.php?t=2272576)
Best bet is to install the plugins for gstreamer (totem) or vlc from the strukturag ppa. As far as mplayer, the ppa build is a year old though still superior to repo version, I may update, may not as it would require I test first on 12.04 which I don't have & would be difficult to have with current hw set up.

Or just don't get hevc files in the first place or if your hardware is good enough use 14.04 (trusty) instead of 12.04

---

### Post by Vladlenin5000 on 2015-04-22
> **mc4man said:**
> Or just don't get hevc files in the first place or if your hardware is good enough use 14.04 (trusty) instead of 12.04

^^^^
This. HEVC is a b***. 


PS - Nice episode.

---

### Post by chandan-rattan-k on 2015-04-23
Thanks lot. It worked.Followed the steps mentioned in link


[COLOR=#000000]You can add his PPA, then install mplayer and smplayer, a full-featured GUI interface for mplayer.[/COLOR]
[COLOR=#000000]Code:
sudo add-apt-repository ppa:mc3man/mplayer-test
sudo apt-get update
sudo apt-get install mplayer smplayer[/COLOR]

---

### Post by VMC on 2015-04-23
I quit using **vlc** after reading a discussion about **mpv**. **mpv** plays anything I throw at it. There's a lot of options for mpv's config file. Now I just click on any mkv file and it starts playing.

---

