---
title: "DVD Playback issue"
date: 2010-08-07
forum: Multimedia Software
---

### Post by saitoh on 2010-08-07
Ok, I have a mostly fresh install of Ubuntu 10.04 on my computer. I was planning on using this computer as a video sever with XBMC and FUPPES, but I'm experiencing some problems.

Right after installing Ubuntu and fully updating it, I checked to make sure the Universe, Multiverse, and Medibuntu repositories added. I then insalled libdvdread4 and libdvdcss2 (I used the script in /usr/share/doc/libdvdread4 even though I had the medibuntu repo). After doing this I still had no video from output from my dvds, so I installed all of the gstreamer libs(gross) and then I got totem to play back dvds. However, it's super choppy (because it's using gstreamer).

Mplayer, XBMC, and everything other than totem w/gstreamer still cannot play DVDs. I suspected that maybe there was an issue with my drive as it's a blu-ray drive. However a) the output of lshw -C disk looks fine and I ripped a movie to an iso and still encountered the same problems.

```
*-cdrom                 
       description: DVD reader
       product: BR-04B2T
       vendor: ASUS
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/ANCHORMAN
       version: 1.01
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/ANCHORMAN
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

```

Please do not bother replying if your going to post links to the generic libdvdcss install guides.

Otherwise any suggestions would be very much appreciated.

Thanks in advance.

---

### Post by Nick_Jinn on 2010-08-07
Have you tried updating and rebooting? I would install the entire medibuntu repository rather than just those two packages. 

When I use Mint I never have to worry about messing around with this stuff. It just works the first time out. I use the DVD version with Flash and extras installed.

---

### Post by saitoh on 2010-08-07
I have rebooted the computer since I did the install. I haven't looked at how many packages are in the medibuntu repo, but I'm not sure if I want to just install all of them blindly when supposedly the only two required to enable DVD playback are libdvdread4 and libdvdcss2.

I also installed ubuntu-restricted extras and the win32codecs from the medibuntu repo. But they shouldn't be required for dvd decoding.

---

### Post by Nick_Jinn on 2010-08-07
Are you hard up for space on your disk? It might be a good experiment to see if it works after adding the whole repository.

Also, did you add the medibuntu repository to your software sources? Try it and then use aptitude to update.

---

### Post by saitoh on 2010-08-07
I added the repo to /etc/apt/sources.list right after installing Ubuntu. So yes, I have updated all packages that might have newer versions from the Medibuntu repo.

---

### Post by Nick_Jinn on 2010-08-08
If it were me I would try to install the whole thing. It doesnt take up much room and it shouldnt slow down your machine.

---

### Post by lidex on 2010-08-08
What do you have your video output configured as in Mplayer? Does the audio play? Post this output please:
```
sudo lshw -C display
```

---

### Post by mc4man on 2010-08-08
> then I got totem to play back dvds. However, it's super choppy (because it's using gstreamer).
As was just mentioned by lidex your issue very well may be the video output being used, the default would be Xv. 

While totem is and most likely will remain an awful dvd video player it's not because of gstreamer per se.
More from a half-baked resindvd and possible issues with the pulseaudio gstreamer plugin in some instances.

An output of x11 would be something to try with any player.

---

