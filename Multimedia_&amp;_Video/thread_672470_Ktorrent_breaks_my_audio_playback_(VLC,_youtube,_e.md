---
title: "Ktorrent breaks my audio playback (VLC, youtube, etc.)"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by loweb1 on 2008-01-19
It took me a while to figure out that it happened whenever I open up Ktorrent. But it's happened reliably many times now. Once I start Ktorrent audio playback doesn't work for anything in Firefox. And when I try totem, it gives an error saying that the audio device is busy.  I was able to find a similar problem on a fedora forum here:

[http://forums.fedoraforum.org/archive/index.php/t-165504.html](http://forums.fedoraforum.org/archive/index.php/t-165504.html)

They fixed it by setting the audio system to suspend if idle for more than 5 seconds. But I don't know how to do that in Ubuntu. 

I'd rather not have to switch torrent programs but if no one has any idea's I may just start looking for a different one. I suppose I should mention that I'm using gnome and not KDE even though I am using Ktorrent. Would that matter though?

---

### Post by jaimekristene on 2008-02-26
Hi,

I did apt-get install kcontrol  then in kcontrol I followed the same instructions as the fedora link.

Go to 
Sound & Multimedia-> Sound System-> Auto-suspen if idle after [x]5 second

then after it restarted the sound system I could use my other sound applications straight away with ktorrent still running.

hope this helps someone,
Jaime Schmidt.

---

