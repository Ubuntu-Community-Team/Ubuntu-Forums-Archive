---
title: "Problems with Mplayer and VLC"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by crazydiver on 2007-05-30
Hello All,

   For some reason I am having problems playing both VLC and Mplayer. VLC worked out well for me when I was using my XP operating system but after making my transfer to Ubuntu my VLC player doesn't show any video, just audio. I click on the screen just to see what's up and parts of the video flashes out for a second and then blacks out. 
   Thereafter, I made the assumption that Ubuntu and VLC don't mix, so I went on to install and play MPlayer (Totem). 
  This time, for some reason the video plays well but with a slight overexposure... THe whiteness is pretty out there when I watch action movies full of explosions, my screen becomes a full white screen every time soemthing blows up. I go back to XP and VLC works perfectly. hmmm

Any suggestions?

---

### Post by crazydiver on 2007-05-31
haha... found the culprit...Apparently the desktop effects was interfering with the video players.

I disabled desktop effects by going to preferences...

After doing this everything is just the way I like it!:p

---

### Post by cvmostert on 2007-06-15
but what do you do to have desktop effects AND watch videos normally.. that would be a golden thread...

---

### Post by jatilq on 2007-06-16
just change the video output to x11 and you can do both. SMPlayer seems to work right out the box.

---

### Post by Hachi-Roku on 2007-07-26
cheers. turned off D/E and my vlc probs went away!!!

In which vlc config file to we change the output to X11?? i assume its something like /.vlc/something.conf??

cheers
J

---

### Post by RomeReactor on 2007-07-26
Hi. [This section of UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback") will help you set up VLC to avoid the black screen issue while having Desktop Effects (Compiz) or Beryl enabled.

---

### Post by Hachi-Roku on 2007-07-27
Thanks dude! Worked briliiantly. now i have videos AND cool cube desktops!!!

hi 5!

J

---

