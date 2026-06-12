---
title: "Flash Video: Sound ok, video speeds up &amp; slows down"
date: 2009-07-16
forum: Multimedia Software
---

### Post by AKADAP on 2009-07-16
For the last several versions of the ATI video driver (currently using ati-driver-installer-9-6-x86.x86_64 on Ubuntu 9.04), I've been having trouble with Flash videos.

For the first two minutes of a video, the video will slow down, then stop for several seconds, then run at extreme speed to catch up with the audio which is playing perfectly the whole time. It will do this over and over for the first two minutes of the video, then everything will sync up and the rest of the video will play fine.

If I start over, it will do the same thing most times, but the slowdowns will occur at different locations. If I start over enough times, it will eventually play through with no problems.

This is not a problem with buffering, the progress bar usually shows plenty of buffered data when this is occurring.

Anyone seen this behavior before? Got a fix for it?

---

### Post by lovinglinux on 2009-07-16
I think removing pulseaudio and installing esound should fix this.

If you don't want that, then try fixing pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Also visit the Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by AKADAP on 2009-07-17
> **lovinglinux said:**
> I think removing pulseaudio and installing esound should fix this.

If you don't want that, then try fixing pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Also visit the Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

Going through the pulseaudio fixes appears to have fixed the problem. I've thought I had fixed this before and been wrong, so I'll give it a few days before I claim success. It is odd though that PulseAudio would cause video problems.

---

### Post by AKADAP on 2009-07-18
A couple of days has gone by with no video problems.
I think I can safely say the problem is fixed. Thanks.

---

### Post by lovinglinux on 2009-07-18
> **AKADAP said:**
> A couple of days has gone by with no video problems.
I think I can safely say the problem is fixed. Thanks.

You are welcome. 

For future reference, I have included this issue in my tutorial. See **Solution** [*[COLOR="Red"]**FOT009**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT009).

---

