---
title: "Need help with audio and video using ubuntu 11.04 (pursuing k3b as soln)"
date: 2011-04-07
forum: Multimedia Software
---

### Post by ClientAlive on 2011-04-07
Hello,

I have a couple things I need to do and I have spent some hours googling  and on the forum here to get to the point I am at. I hope this will not  prove to be too broad for a single thread but I was concerned about  breaking it up and ending up with tthings being too disconnected for me  to follow. I'll go ahead and break things down into a couple sections  ok? If there is any part of these things that anyone can direct me on I  would surely appreciate it. If this is just too much, I certainly  understand. I am researching and learning about these things through the  Internet right now but would also like to be able to do some of them  right away - should this learning process prove to be lengthy. (I'm really not sure what I'm facing here).

First: I'm using what I believe to be beta 1 of Ubuntu 11.04. I say  "believe to be" because I started with alpha 3 a few weeks back and have  been updating almost daily (yesterday being the most recent time); and,  last I checked, 11.04 was at the beta 1 stage. This makes me assume  that this is what I now have on my machine via updating.

Now for my questions:

**A) Want to be able to rip**** (1)****, ****copy ****(2)**** and ****burn ****(3)**** audio to CD (or to hard drive as the case may be with ripping)**

**A3.1)** What I'm working on right now (preface):

I have an audio book in the form of eight mp3 files that I would like to  put onto cd. I have learned that I can burn mp3 files to a cd by  burning as data. Now I would like to find out about converting to wav  and burning as an audio project. This is where I have run into some  difficulty with k3b.

**A3.2)** What I've tried so far to accomplish this (I will describe this part in a more chronological fashion):

I have k3b installed on my system. I have tried to run k3b (with a blank  cd inserted into the drive) and clicked, "New Audio CD Project". When I  try to add my mp3 files to the project I get an error message telling  me the file type is not supported and that I can convert the files to  wave using another app first.

I did some research on burning mp3 with k3b (thought to talk about  burning mp3 in the context of burning audio seems a bit misleading) and  found some talk about a library called libmad0. When I looked in my  installed apps I found that this library was already installed (but the  error message had still been generated). This information came from an  older post on this forum (roughly 6 years ago).

I also found a more recent post here:  [http://ubuntuforums.org/showthread.php?t=1454537&highlight=mp3+k3b](http://ubuntuforums.org/showthread.php?t=1454537&highlight=mp3+k3b)  and have followed the instruction given in post #3. What I found was  that K3b MAD decoder is not listed under Settings > Configure k3b > Plugins. (Yet, as mentioned before, libmad0 is installed on my machine - unless these are two different things).
[B]
Note)[/B] I should also mention, for what it's worth, that I do have ubuntu-restricted-extras installed on this machine.

** Now for the other (audio) stuff. The follow (audio) subsections are  not projects I am working on right now but would like to get set up for  so that I can when the time comes.*

**A1)** I have noticed that under Settings > Configure k3b  > Plugins there are sections for encoding and decoding and I am not  quite familiar enough with how things work to understand the difference  or know which (if not 'both' or even 'neither') apply to ripping.

**A2)** Just wondering if there are any particular/ specific issues I should be aware of when attempting this with k3b.

**B) Want to be able to ****rip**** (1)****, ****copy ****(2)**** and ****burn ****(3)**** video to DVD (or to hard drive as the case may be with ripping)**

**(B1 and B2)** Just wondering if there are any particular/ specific issues I should be aware of when attempting this with k3b.

**(B3)** Most of the movies I'll be burning to dvd are avi files to  begin with. What I would want to end up with is a dvd that will play in  most any standard dvd player and on a computer (given the right player  on the computer). *Actually, I do have several avi video files I hope to burn to dvd later this evening*.

Thanks in advance. Any/ all help greatly appreciated.

Jake

---

### Post by ron999 on 2011-04-07
> **ClientAlive said:**
> 
I also found a more recent post here:  [http://ubuntuforums.org/showthread.php?t=1454537&highlight=mp3+k3b](http://ubuntuforums.org/showthread.php?t=1454537&highlight=mp3+k3b)  and have followed the instruction given in post #3. 
Read the whole thread.:D

---

### Post by ClientAlive on 2011-04-07
Ok. libk3b6-extracodecs fixes that. I can convert from mp3 to wav or ogg now.

Now I wonder if I even need to have libmad0? Should I uninstall it? Also trying to keep my system relatively tidy here too.

As far as the other stuff: I see that k3b has options for ripping and copying but have not delved into any of them specifically yet. I imagine I'll have to deal with each thing as it comes up/ as I go?

Are there any pitfalls and/ or suggestions for any of the other stuff I mentioned in my initial post? Anything that seems to come up a lot for people when they try to do those tasks?

Thx.
Jake

---

