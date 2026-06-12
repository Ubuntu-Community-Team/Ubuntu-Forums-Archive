---
title: "Watching AVI movies with mplayer on my Hitachi 42&quot; HDTV... how to?"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by konungursvia on 2007-01-15
I have a question about this. The native resolution of my HDTV is 1024X1024 actually. Do I need to edit xorg.conf to allow for that resolution, and that's it? I found the cable to connect my laptop to it through a regular old serial port. Will it work and allow me to play my lovely hi-dev movie (720p) on the Hitachi? hope-hope...

---

### Post by Shay Stephens on 2007-01-15
I have hooked my computer up to my widescreen via the monitor cable.  All I had to do was edit xorg.conf to add the resolution of the TV and away I went.

---

### Post by konungursvia on 2007-01-15
> **Shay Stephens said:**
> I have hooked my computer up to my widescreen via the monitor cable.  All I had to do was edit xorg.conf to add the resolution of the TV and away I went.

Yes, I thought that might work, thankyou. But, my tv is 1024x1024, whereas its manual lists "suggested resolutions" along the more normal lines such as 1024x768, never with x and y equal in pixels. Should I tell X the native resolution of the tv or let the tv work with 1024x768 and bend it?

---

### Post by Shay Stephens on 2007-01-15
> **konungursvia said:**
> Yes, I thought that might work, thankyou. But, my tv is 1024x1024, whereas its manual lists "suggested resolutions" along the more normal lines such as 1024x768, never with x and y equal in pixels. Should I tell X the native resolution of the tv or let the tv work with 1024x768 and bend it?

I am assuming that the TV does not sport square pixels, and in that case, I have no idea what the final result will look like, but my initial thoughts would be to feed it with native resolution and let the tv work out what to do from there.  My guess is that the image would look distorted due to the presumably non-square pixels.  I don't know how one would compensate for that on the PC side of things.  So if it does look weird, then I would next feed it what I think it might be expecting, i.e. 4x3 aspect ratio.

Whatever happens, please report back, I am rather interested to see how this works out :-)

---

### Post by konungursvia on 2007-01-16
> **Shay Stephens said:**
> I am assuming that the TV does not sport square pixels, and in that case, I have no idea what the final result will look like, but my initial thoughts would be to feed it with native resolution and let the tv work out what to do from there.  My guess is that the image would look distorted due to the presumably non-square pixels.  I don't know how one would compensate for that on the PC side of things.  So if it does look weird, then I would next feed it what I think it might be expecting, i.e. 4x3 aspect ratio.

Whatever happens, please report back, I am rather interested to see how this works out :-)

Thanks for the ideas, I will report back. I'll buy the cable today and hook it up this evening, if all goes well.

---

### Post by konungursvia on 2007-01-17
> **konungursvia said:**
> Thanks for the ideas, I will report back. I'll buy the cable today and hook it up this evening, if all goes well.

Well that Hitachi could probably play an extraterrestrial signal! It seems the NVidia driver doesn't output anything perfectly square, and so X kept itself in 1280X1024 while talking to the plasma TV, which re-interpreted it in five ways simultaneously which I could cycle through to choose a zoom mode.

Not that I was able to figure anything out about how this should be done, but it worked. I watched Shrek last night in lovely hi-def. The HDTV simply interpreted the sync and adjusted itself. I had four zooom and screen size and shape options and cycled through them until I had the screen filled with good video.

The only glitch was that Mplayer won't keep audio and video in sync unless you enable frame dropping. And, you can't push the progress bar ahead to jump to later parts of the video, it seems, as you can in Windows media player etc.

All in all, a great experience, and I learned a lot.

---

### Post by curuxz on 2007-02-01
for my HDTV, which I use as my main pc monitor for design and cad reasons, it recomends 1024x768, however it runs very very well at 1920 x 1200 :)

Hope that helps

---

