---
title: "livesteam buffer problems with totem-plugin"
date: 2011-07-07
forum: Multimedia Software
---

### Post by groundnut on 2011-07-07
I am trying to watch several video channels. These are available in the wmv format. This is being handled by the Totem-plugin in both Firefox and Chromium. Many times excessive buffering takes place.

What can I do to eliminate this buffering?

---

### Post by beew on 2011-07-07
Can you give a link?

---

### Post by groundnut on 2011-07-07
I mainly have problems with 

[http://nos.nl/sport/](http://nos.nl/sport/)

Probably this is not available outside the Netherlands.

At the moment I follow 2 streams / programs at this site.
In the afternoon I watch the livestream of the Tour de France (link top right corner of the site).
In the evening, after 23:00 I watch the livestream of a program called De Avondetappe (also, link top right corner of the site).

Now I am watching the Tour de France. At the moment there are no buffering problems (for the first time).

---

### Post by groundnut on 2011-07-07
Now the buffering is there again.
Probably there are more viewers now closer to the finish.
I have to use the lower quality stream now.

On my Windows machine I always can view the higher quality (both in wmv and in Silverlight).

---

### Post by beew on 2011-07-07
I watched the video with no problem, playback started almost immediately (see last screenshot). Maybe you should use gecko-mediaplayer as your plugin for watching this kind of movie instead of Totem. In my experience the Totem plugin is excellent for quicktime streaming and pretty useless for everything else.

So install the gecko-mediaplayer. Then in FF go to Tools > Add-ons > plugins to disable conflicting plugins (use only the Totem plugin for quicktime, disable the gecko-mediaplayer quicktime plugin, disable totem and use only gecko for everything else), see first two screenshots.

---

### Post by groundnut on 2011-07-08
Thank you very much beew.

I installed the Gecko Media Player.
I tried it yesterday evening and today.

I think it gives a slight improvement over Totem, but the problem has not been solved. Still to much buffering.

The Tour de France is also available in a (slightly) lower image quality. This works without buffering (also with Totem).

However the program the avond etappe (evening stage) is only available in higher quality. This program is often impossible to watch on my Ubuntu computer.

---

