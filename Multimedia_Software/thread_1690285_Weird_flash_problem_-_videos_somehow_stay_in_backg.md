---
title: "Weird flash problem - videos somehow stay in background"
date: 2011-02-18
forum: Multimedia Software
---

### Post by zeta on 2011-02-18
Hi,

after an update on wednesday I got some serious problem with flash. Whenever I watch a video clip on sites like youtube, the video somehow stays in the background and "shines" through any black field in applications. So videos look shattered, but it is even worse for texts - they are almost unreadable on the part of the screen where the video was. This doesn't show on screenshots though. 
I un- and reinstalled flash a couple of times now, tried another video-driver, but it didn't help. 

Any thoughts?

---

### Post by Bucky Ball on 2011-02-18
Tried installing ubuntu-restricted-extras? You will find it in Synaptics Package Manager. That will install latest and appropriate flash if not installed already, some codecs and other things. You might be missing a codec or something may have been killed by your update. This happens with 10.10 and other non-LTS releases from time to time. (Also with LTS releases rarely.)

---

### Post by zeta on 2011-02-18
Thanks, but I got the ubuntu-restricted-extras installed.

---

### Post by andersgr on 2011-02-21
Hi there,

I am experiencing the same issue, and would very much like a solution.

I have ubuntu-restricted-extras installed like OP, and have very much enjoyed the use of flash on my computer, that is up until now. I guess this means I am using the binary blob flash player from adobe installed with flashplugin-installer, but if you need me to verify this somehow I'd be happy do that, I just don't know how.

I tried taking screenshots of the issue but they look normal if I reboot or have someone else look at them, so the corruption of the image does not lie in the browser but rather (I guess) in the video buffer. This makes sense as I seem to be getting traces of the image in other gui apps than the browser, and even some artifacts in gnome itself.

To sum up the issue, basically if I watch a flash video in firefox (like this: [http://vimeo.com/moogaloop.swf?clip_id=18150336](http://vimeo.com/moogaloop.swf?clip_id=18150336)), stop the video and close the tab, the image of that video stays on any part of the screen that is white, for instance the google front page would be covered in it.

---

### Post by simple_impulse on 2011-02-21
I have similar problem. Some Flash surface somehow remains in background. Some icons and applications on desktop show Flash video (still) image after the Flash-using application is closed. For example, black can become transparent in Gimp showing the video image. The "ghost" image stays in the same place it was during video play, so if I move an application over it, if messes up that part which is over this "ghost" image.

I have nVidia GT240 video card, with newest possible drivers for VDPAU.

If someone can tell quick way to reset X/OpenGL/whateverisneeded because now I need to reboot Ubuntu after watching Flash videos?

---

### Post by arrjj on 2011-02-21
Disable hardware acceleration for flash (any flash object right-click-settings, it "fix" background problem) and wait for update of flash player.

---

### Post by simple_impulse on 2011-02-23
arrjj: That seems to solve it. I needed to reboot after disabling hardware acceleration. Happily my i5 750 seems to have enough juice to decode Flash without GPU assistance... Or whatever it now does.

I just hope they fix it properly.

---

### Post by arrjj on 2011-02-27
[http://www.youtube.com/watch?v=zzesO81u-28](http://www.youtube.com/watch?v=zzesO81u-28) solution to rollback to older version of flashplayer.

---

### Post by euclidean on 2011-06-08
> **arrjj said:**
> Disable hardware acceleration for flash (any flash object right-click-settings, it "fix" background problem) and wait for update of flash player.

Superb. I had the same problem (Kubuntu Natty with Flash 10.3.181.22) and that fixed it. Thank-you!

---

### Post by tomochan on 2012-03-28
I'm having this problem too. Is it possible to get rid of the previous flash image from my screen by refreshing the framebuffer or something like this?

---

### Post by tomochan on 2012-03-28
I got rid of the old flash image by restarting gdm.

---

### Post by nv22nv on 2012-05-01
Now that it's more than a year since this thread was started, I'm wondering if someone found a solution other than to disable hardware acceleration or use an old version of flash. Apparently, Adobe has yet to get rid of that bug - I just did an update from the last working version I could get (11.1.102.62) to the latest version (11.2.202.233), and viola - the problem is there again.

Edit: Using Flash-Aid for Firefox and installing any of the version offered there didn't help as well. I'm afraid I'll forever be stuck with version 11.1.102.62.

---

### Post by mayeulk on 2012-05-17
> **arrjj said:**
> Disable hardware acceleration for flash (any flash object right-click-settings, it "fix" background problem) and wait for update of flash player.

Thanks, searched a solution for days ! (Kubuntu 11.10 64 bits, Nvidia GeForce 8500GT  driver 280.13)

Mayeulk

---

### Post by mathx5 on 2012-12-16
> **nv22nv said:**
> Now that it's more than a year since this thread was started, I'm wondering if someone found a solution other than to disable hardware acceleration or use an old version of flash. Apparently, Adobe has yet to get rid of that bug - I just did an update from the last working version I could get (11.1.102.62) to the latest version (11.2.202.233), and viola - the problem is there again.

Edit: Using Flash-Aid for Firefox and installing any of the version offered there didn't help as well. I'm afraid I'll forever be stuck with version 11.1.102.62.

I have the same issue with 11.2 r202. Without HW acceleration, 1080p wont play fullscreen smoothly.

Can I get a copy of your older version? I have a 10.3 something here, but thats too old, has artifacts with some audio codecs :(((

---

### Post by mathx5 on 2012-12-16
> **mathx5 said:**
> I have the same issue with 11.2 r202. Without HW acceleration, 1080p wont play fullscreen smoothly.

Can I get a copy of your older version? I have a 10.3 something here, but thats too old, has artifacts with some audio codecs :(((

Oh there are archives at Adobe. 11.1r102.63 already plays vimeo when 11.2r202 did not. 

Also no more ghosting as we're all discussing. But youtube rewind or ffwd on videos is a bit wonky, sometimes doesnt start playing again :(

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

the older versions are large zips of all files for all platforms. just dip into the zip to find your own desired version.

---

