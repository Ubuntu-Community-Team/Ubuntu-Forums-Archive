---
title: "VLC: Audio/Video Unsynchronised"
date: 2011-08-05
forum: Multimedia Software
---

### Post by Chriske on 2011-08-05
Hi,

I'm having a problem with the audio/video being unsynchronised when I play videos (any format) in VLC in Ubuntu 11.04.

I have tested this in Puppy Linux and the problem does not occur there. It also did not occur for me in Ubuntu 10.04.

Googling, I see this is not necessarily an unknown problem. The oft-mentioned solution to Tools -> Track Synchronisation does not work for me.

I also noted a possible solution quoted in the VLC FAQs:[INDENT][COLOR=Purple]Try using another audio output plugin and, under Unix, kill esd, artsd or pulseaudio if they are running. If the problem is due to the input file, have a look at the "Audio desynchronisation compensation" option. [/COLOR]
[/INDENT][INDENT][COLOR=Purple]**Oops, there is an information missing:**[/COLOR]
[COLOR=Purple]Audio desynchronisation compensation is limited by the cache size  depending to the selected access module. This can be altered in the  configuration panel. [/COLOR]

[COLOR=Purple] Please, for the clueless people arguing that it doesn't work, include the information mentioned in the second post of [this thread]("http://forum.videolan.org/viewtopic.php?f=12&t=19456&p=61156&hilit=desync#p61156")  in The VideoLAN Forums exhaustingly, as by my nearly ever-lasting  research on the same issue there are a lot of locations here and there  where it isn't being mentioned unfortunately. Best if it was mentioned  in the tooltip as well.  Please do put this tag into the appropiate location or remove it once it is a documented feature inside the software, agreed?[/COLOR]
[/INDENT]But, I'm not really sure how to progress with this.

Can anyone help please?

Many thanks.

---

### Post by TopEnder on 2011-08-05
Chriske,  They way I got around the same problem was to tweak the setting in Tools/Track Synchronization you may have to use a minus value e.g. -0.025. By trying different values both + & - in small steps, it works for me. [[COLOR="Blue"]QUOTE=Chriske;11120556]Hi,

I'm having a problem with the audio/video being unsynchronised when I play videos (any format) in VLC in Ubuntu 11.04.

I have tested this in Puppy Linux and the problem does not occur there. It also did not occur for me in Ubuntu 10.04.

Googling, I see this is not necessarily an unknown problem. The oft-mentioned solution to Tools -> Track Synchronisation does not work for me.

I also noted a possible solution quoted in the VLC FAQs:[INDENT][COLOR=Purple]Try using another audio output plugin and, under Unix, kill esd, artsd or pulseaudio if they are running. If the problem is due to the input file, have a look at the "Audio desynchronisation compensation" option. [/COLOR]
[/INDENT][INDENT][COLOR=Purple]**Oops, there is an information missing:**[/COLOR]
[COLOR=Purple]Audio desynchronisation compensation is limited by the cache size  depending to the selected access module. This can be altered in the  configuration panel. [/COLOR]

[COLOR=Purple] Please, for the clueless people arguing that it doesn't work, include the information mentioned in the second post of [this thread]("http://forum.videolan.org/viewtopic.php?f=12&t=19456&p=61156&hilit=desync#p61156")  in The VideoLAN Forums exhaustingly, as by my nearly ever-lasting  research on the same issue there are a lot of locations here and there  where it isn't being mentioned unfortunately. Best if it was mentioned  in the tooltip as well.  Please do put this tag into the appropiate location or remove it once it is a documented feature inside the software, agreed?[/COLOR]
[/INDENT]But, I'm not really sure how to progress with this.

Can anyone help please?

Many thanks.[/QUOTE]

[/COLOR]

---

### Post by Chriske on 2011-08-05
Thanks TopEnder.

I did try that solution, but unfortunately it does not seem to work.

It's quite difficult to achieve the right offset I find, but also the asynchrony does not seem to be constant, i.e. it seems to grow as the video plays, so that towards the end of the video it is quite large indeed.

But, thanks again for the suggestion anyway.

---

### Post by beew on 2011-08-05
Hi,

There are a few solutions on this thread. My favourite is my post #18. :)

[http://ubuntuforums.org/showthread.php?t=1769271&page=2](http://ubuntuforums.org/showthread.php?t=1769271&page=2)

---

### Post by Chriske on 2011-08-05
Thank you beew! 

#18 is now my favourite post too because it fixed the problem with pure elegance and simplicity. Brilliant! :)

Thanks again and have a great weekend.

---

