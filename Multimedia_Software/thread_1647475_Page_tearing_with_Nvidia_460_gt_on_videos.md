---
title: "Page tearing with Nvidia 460 gt on videos"
date: 2010-12-17
forum: Multimedia Software
---

### Post by thisisjay on 2010-12-17
I got rid of the page tearing issue on my old video card (240 gt), but no luck with this one. The strange thing is that the page tearing in videos only happens on my 1080p projector and not an LCD monitor. What I have tried:

Enabling Vsync in the Nvidia control panel

Enabling Vsync in Compiz

Installing the latest driver

turning off all vistual effects

trying multiple players(vlc, movie player, gnome mplayer)

Still ugly page tearing on all large movements in movies.

I'm in Ubuntu 10.04

---

### Post by efflandt on 2010-12-17
Which nvidia drivers are you using?  If you are using drivers activated with Hardware Drivers, you can get newer nvidia  (currently 2.60.19.29) by adding x-swat repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then Quick search nvidia in Synaptic, update nvidia-current, nvidia-settings, and nvidia-current-modaliases, and reboot.

---

### Post by thisisjay on 2010-12-18
What you suggested did fix the page tearing.....but the video is still not watchable for 2 reasons:

1. The video is shaky. It is most noticeable when the camera pans quickly from left to right, up to down etc. It is livable, but not optimal.

2. After a few minutes of playback the video starts to glitch. Just small pauses and then stop go, stop go, stop go.


Just started with this new video card.

---

