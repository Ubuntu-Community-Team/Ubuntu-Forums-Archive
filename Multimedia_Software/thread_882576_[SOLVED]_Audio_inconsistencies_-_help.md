---
title: "[SOLVED] Audio inconsistencies - help"
date: 2008-08-07
forum: Multimedia Software
---

### Post by le singe on 2008-08-07
Hello all,

So I think I've got most things in ubuntu working (well one other problem just came to mind but I'll save that for another post), yet I've had some simple audio trouble from the start.

Basically, if I play audio in one program (rhythmbox, a video file, youtube) it works fine, yet then if I switch to another source, say rhythmbox to youtube, the second audio source will not work.  If I'm playing mp3s in rhythmbox then I go to youtube, even after closing rhythmbox, the youtube video won't play past the first two seconds.  Inversely, if I start by playing a youtube video, I get sound and video fine like I should, then later switching to rhythmbox, my mp3s won't play.  I can remedy this by rebooting, but I am having no luck switching from one audio source to another in the same session.

Rhythmbox is my primary mp3 player, I use totem to play video files, and I've downloaded the recommended codecs to play youtube files and such when I was prompted to do so the first time I ever opened an internet video file.  I'm running a decent laptop, most likely with some generic embedded sound card.

Has anyone else experienced this problem?  Ideally, I'd like to be able to pause an mp3, play a video, stop that video, hit a video link on the internet, and go back to playing mp3s without any problems.  I'm used to this and I don't think it's too much to ask.

Sorry, I cannot remember which exact audio/video codecs I installed, but they seemed to be the recommendations, you know?

I'd appreciate any input.  Bye.

---

### Post by Vivaldi Gloria on 2008-08-07
> **le singe said:**
> ... I'd appreciate any input.  Bye.

Hardy uses the new pulseaudio and it has problems. The following guide fixed all my problems:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by le singe on 2008-08-08
okay thanks vivaldi....

I'm trying to use this guide right now, but I'm encountering another problem.  I can type in or copy the first code into the terminal, then once I am prompted for a password, I cannot type a single letter.  I don't understand... I can type the code, but then I cannot type my password.  Must I reboot in recovery mode, and hence as the root user?

Why can't anything in linux just be f-in' simple?  Anyone else get frustrated from time to time?

---

### Post by Vivaldi Gloria on 2008-08-08
> I can type in or copy the first code into the terminal, then once I am prompted for a password, I cannot type a single letter.

When you type your password it works but it's just invisible. Type your password and it'll work.

> Why can't anything in linux just be f-in' simple?  Anyone else get frustrated from time to time?

It takes a couple of months to get use to it. ;)

---

### Post by le singe on 2008-08-08
so I just rebooted in recovery mode as root, and that did not do the trick.  I can type the code into the terminal, but still cannot type my password.

Has anyone else encountered this problem?  Are there some terminal basics I need to know, like "of course you can't type your password into the terminal," or something else?  This should be less frustrating than this.  How is anyone expected to get anything done in the terminal??

sorry... my frustration is probably showing regardless of my attempts to tone it down for the forum.  And no, not everything in ubuntu is difficult.  I have to say I really enjoy using this OS, and for the most part things are simple.  It's just that sometimes the problems you run into can be real pains, the solutions to which often obscure....

Thanks again ubuntu community.  Bye

---

### Post by le singe on 2008-08-08
oh no, so this is one of those ubuntu basics that I just didn't know??
so when I type the password, no stars or placeholders or dots will show in its place, but it's getting the password just the same?

Aaiiee, okay.... 
this was just a simple thing then, part of the basics of the terminal.  Well, I didn't know.  

I tend to get frustrated pretty quickly.

Thank you very much, vivaldi.

---

### Post by Vivaldi Gloria on 2008-08-08
> so when I type the password, no stars or placeholders or dots will show in its place, but it's getting the password just the same?

Yep. This is more secure. People can't see how long your pwd is.

Here are a couple of links that are useful. Go over them when you have time.


-----------------------------------------

Start with my posts here:

[http://ubuntuforums.org/showthread.php?t=874035](http://ubuntuforums.org/showthread.php?t=874035)

-----------------------------------------

Read the terminal basics from:

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

-----------------------------------------

ubuntu help and wiki:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

-----------------------------------------

aysiu's page (he's a member here):

[http://www.psychocats.net/](http://www.psychocats.net/)

-----------------------------------------

The greatest of all linux sites:

[http://tldp.org/](http://tldp.org/)

Especially read the guides there:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

Start with these

Bash Guide for Beginners
GNU/Linux Command-Line Tools Summary

-----------------------------------------

---

### Post by le singe on 2008-08-08
Hey!!

It worked!  I followed parts A and B of the guide (HOW-TO: Pulse Audio Fixes...) and everything works now (after a reboot).  I can even pause an mp3, play a video, play both at the same time and both give sound!  I am pretty happy.

So thanks for the link, vivaldi.  If anyone else has this same problem I detailed, try this guide and it might fix it.  I only followed the first two parts, A and B.

---

