---
title: "DVD Playing Problem"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by stereofreak69 on 2007-09-20
Ok, i will explain this:

I put in ladder 49 DVD, into a dvd drive. and the player pops up. Good so far, right?

I installed a GStreamer media plugin or something. But after that, it says it cant read from source.

On the desktop, it says LADDER_49, so the dvd drive itself has the plugins, right?

Im fixing it for someone, and convinced them Ubuntu was all the best. I personally was taking a leap, because i had just gotten the CD's a few weeks prior. I can tell you this:

The DVD-ROM drive is a Toshiba "DVD-ROM SD-M1502".
I installed Ubuntu successfully yesterday, and ran the update wizard thing. It took like 20 minutes.

Im fixing it for someone, so i cant tell you the previous OS or anything. We assume it was windows 2000, but a slim chance of 98.

Any help? Im new to ubuntu, to linux OS that is...

Thank you!

Stereofreak69

---

### Post by yabbadabbadont on 2007-09-20
Have you seen this yet?

[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd)

---

### Post by stereofreak69 on 2007-09-20
No i have not. Thank you.

I will now attempt that.

Ill keep this community updated. Thank you.

Stereofreak69

---

### Post by stereofreak69 on 2007-09-20
Ok, when i go to Add/Remove programs, i only find the first one. gxine. I installed it, and went to the system preferences and stuff like the post said. I couldnt find the pther ones in the programs. But i think gxine installed it.

I put the dvd in, it (gxine) came up. It quided me through a like 2 page wizard. Then said this:

"The xine engine failed to start"
"no demuxer found - stream format recognized"

Im sorry, i must be doing something wrong. Please, any idea why?

All the thanks in the world.

Stereofreak69

P.S. I can feel that were almost there. lol. Again, new to ubuntu.

---

### Post by yabbadabbadont on 2007-09-20
Did you follow *all* the instructions?  Specifically ```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by stereofreak69 on 2007-09-20
I did that. It said something about downloading libdvdcss and unzipping the package. Then it said done, and gave me another prompt line.

And another odd thing. I plugged my Seagate 160GB External HHD in a USB port in the back. Its not in computer. How do i fix that?

Sorry about so many questions.
Do you have gmail? Maybe chat in gmail from the web so i dont have to download anything?

Thanks a lot!

Stereofreak69

---

### Post by yabbadabbadont on 2007-09-20
Sorry, out of ideas.  :(

---

### Post by RomeReactor on 2007-09-20
Hi. Maybe using the Medibuntu version of libdvdcss can help you; but first, read the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page for more information about patent issues with some codecs and libraries. If you agree to that, enter the following commands in the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the Medibuntu repositories; then:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to get the gpg key for authentication and update the repository information on your package managers; and lastly:

```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs w32codecs mplayer libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
After the packages finish their installation, Totem should be able to play DVDs. The change from totem-gstreamer to totem-xine is to enable totem to display DVD menus and its subtitles.

Hope this helps.

---

### Post by kevdog on 2007-09-21
Your second set of instructions need to be prefaced with sudo wget -- Please make the correction.  Otherwise good instructions.

---

### Post by RomeReactor on 2007-09-21
> **kevdog said:**
> Your second set of instructions need to be prefaced with sudo wget -- Please make the correction.  Otherwise good instructions.

Now corrected; thanks.

---

