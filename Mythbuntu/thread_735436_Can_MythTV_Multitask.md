---
title: "Can MythTV Multitask?"
date: 2008-03-25
forum: Mythbuntu
---

### Post by colinpollock on 2008-03-25
Hey all you wonderfully helpful Linux/Ubuntu/MythTV gurus...

So I've recently installed Ubuntu (7.10), and MythTV to my HP laptop.  I installed it to learn about the OS and MythTV, as I am considering building a HTPC later this summer, using MythTV as my interface.  Before I spend my hard earned money on hardware, I want to understand the software as best I can on the paid-for hardware I already have.    My observations thus far are that this is pretty impressive stuff.  However, I can't seem to get MythTV to multitask.

Is it possible to "listen to music" from your audio library (mp3's or ogg's on the hard drive) while at the same time look at photos in the image gallery?  I can't seem to figure out how to leave the "listen to music" screen so I can navigate to my "image gallery" without causing the music to stop.

Is this possible?

---

### Post by .nedberg on 2008-03-25
Have you upgraded to MythTV 0.21 yet? I _think_ you can continue playing music with that version.

0.21 is in the backports repositories for Gutsy, default in Hardy.

Also I would recommend you use a Mythbuntu install rather that Ubuntu+MythTV. Mythbuntu is a lot easier that setting up MythTV yourself.

---

### Post by colinpollock on 2008-03-25
Huh.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

I went to "Applications....Add/Remove and installed what I would would have been the latest versions of MythTV Frontend, Backend and Mythbuntu Control Center. The version installed is 0.20.20070821-1.  The install went very smooth, but again, I'm surprised I installed an older version.

I'm not too familiar yet with working in the Terminal screen.  Is there a good (aka simple) way to go about installing 0.21?

CP

---

### Post by .nedberg on 2008-03-25
I am using Kubuntu so I am not sure how it is with Ubuntu. But I believe

System->Software sources, select the "updates" tab and mark everything there. Update your comuter and you will have 0.21.

0.20 is the version supported with Gutsy, 0.21 will be supported with Hardy. It is _not_ recommended to do this, but a lot of people do anyway. But be prepared to break something once in a while, and these packages don't get security updates that fast.

---

### Post by volkswagner on 2008-03-25
> **colinpollock said:**
> Huh.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

I went to "Applications....Add/Remove and installed what I would would have been the latest versions of MythTV Frontend, Backend and Mythbuntu Control Center. The version installed is 0.20.20070821-1.  The install went very smooth, but again, I'm surprised I installed an older version.

I'm not too familiar yet with working in the Terminal screen.  Is there a good (aka simple) way to go about installing 0.21?

CP

You will need to add the backports to your sources.lst.

This can be done within synaptic.
Applications>system>Synaptic Package Manager> Settings> Repositories >Updates, check the box for backports

This is also an easy place to browse and install all your software.  To find a particular name, select any package to get focus then start typing the name you are looking for.

---

