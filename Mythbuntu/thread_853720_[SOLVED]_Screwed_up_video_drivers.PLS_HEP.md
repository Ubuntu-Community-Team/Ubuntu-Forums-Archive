---
title: "[SOLVED] Screwed up video drivers.PLS HEP"
date: 2008-07-08
forum: Mythbuntu
---

### Post by bmwman on 2008-07-08
I finally was able to fully configure my MythTV. Everything was working. My problem was when watching LiveTV the picture and the sound was very choppy. I thought i would try to install the nvidia drivers and did sudo apt-get install nvidia-settings. That totally screwed up everything after I  rebooted. I was able to set up my resolution again, but don't have the one I had before available so it looks weird. Also when i play video or LiveTV the sounds works fine but there is no video AT ALL or just a blue colored screen, kinda like this one : [http://ubuntuforums.org/showthread.php?t=621983](http://ubuntuforums.org/showthread.php?t=621983)

I have a built in Intel 945 video card on IBM ThinkCenter machine. Please help me fix this.

Thanks.

---

### Post by freymann on 2008-07-09
> **bmwman said:**
> I finally was able to fully configure my MythTV. Everything was working. My problem was when watching LiveTV the picture and the sound was very choppy. I thought i would try to install the nvidia drivers and did sudo apt-get install nvidia-settings. That totally screwed up everything after I  rebooted.

 Editing the xorg.conf file always makes me nervous, so I always make a backup copy somewhere that I can copy back in case of disaster!

 Have you looked inside /etc/X11 for other copies of xorg.conf? I can't remember for sure but doesn't nvidia-settings automatically backup your existing copy for you?

 Take a look in the /etc/X11 directory. You may be pleasantly surprised.

---

### Post by bmwman on 2008-07-09
I have not looked in there yet. I tried multiple changes so hopefully i'll have the very first configuration. I'm not sure if it would make multiple backups every time there is a change.
I kinda fixed the resolution. It's not like the way it was, because i'm not exactly sure what it was. I can live with it, but i need to have my video playback working. I've noticed that is only in Fullscreen. I can play video files not in full screen, but of coarse MythTV is always fullscreened and LiveTV or anything else just gives me a blue colored (sometimes black) screen and i can only hear the sound. The sound work good, before it was choppy with the picture, but i do need to get the video back :)

---

### Post by freymann on 2008-07-09
> **bmwman said:**
> I have not looked in there yet. I tried multiple changes so hopefully i'll have the very first configuration.

You can have a look here:

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

It's full of useful links relating to Video cards and Xorg configs and has links specific to your video chip.

---

### Post by bmwman on 2008-07-09
I was able to restore the back up of xconf.org. Thankfully there were over 10 different backup files, each time i changed to a different resolution. So i'm back to choppy video :)

---

### Post by freymann on 2008-07-09
> **bmwman said:**
> I was able to restore the back up of xconf.org. Thankfully there were over 10 different backup files, each time i changed to a different resolution. So i'm back to choppy video :)

That's great! Well, not the choppy video, but at least you found backups.

Look at that Video link I gave you... it may help with the choppy video.

Choppy video, as far as I know, is usually due to:

-poor hard drive/network through put?
-not enough RAM
-not enough CPU power
-too much heat in the box
-bad video drivers. This one especially.

There should be plenty of threads about choppy video in this forum.

---

