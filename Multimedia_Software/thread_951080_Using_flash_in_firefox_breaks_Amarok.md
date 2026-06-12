---
title: "Using flash in firefox breaks Amarok"
date: 2008-10-17
forum: Multimedia Software
---

### Post by kayvee on 2008-10-17
This is something I observed with my installation. I am just a simple linux 'user'; may be somebody more knowledgeable can reproduce it on their systems and better yet, come up with a solution!

I use Amarok to listen to music. I start Amarok, and play music. It works fine without any issues. I start firefox and start browsing while listening to music. Then I come across a video or audio clip that uses flash somewhere on the web so I stop Amarok music and watch/listen to the clip in firefox. That part also works fine. After I am done with the clip in firefox, I get back to Amarok and hit the 'Play' button, I see that the track is not being played and Amarok hangs throwing 'Force Quit' dialog box on me. 

I figured out the way to get back to my Amarok music. I 'Force Quit' Amarok and then close Firefox completely. I start Amarok and it works fine. I do not know if this is an issue with firefox, flash or Amarok...

Ubuntu Hardy with all updates as of today
Firefox 3.0.3
Amarok 1.4.9.1 using KDE 3.5.10
Flash 10.0 r12 (same behavior with older Flash too)

---

### Post by orthod0ks on 2008-11-05
I have the same problem in both Hardy and 8.10

---

### Post by terrygr on 2008-11-07
I am experiencing a similar problem where I will use Firefox 3.0 to watch Youtube or something similar and then none of my audio or video applications work (Audacious mplayer totem xmms etc.)

---

### Post by s13g3 on 2009-12-19
I am still experiencing just this problem in 9.10 using a reverted version of Amarok 1.4.10 (the new Amarok is *terrible*). As long as any flash is running in Firefox (currently 3.5.6, updated < 15m ago as of this posting), Amarok simply will not play at best, and more or less locks up until closing the offending page containing allowed flash object (though in testing this does not guarantee the program will recover) or the process is terminated manually (via the process explorer or kill -9). 

Any chance of a fix?

---

### Post by Chronon on 2009-12-19
It appears most people have Intrepid or Hardy.  I had a similar issue before I got pulseaudio working.  I don't have a problem currently with getting audio simultaneously from Amarok (2) and flash in Karmic (both running through pulse).

---

