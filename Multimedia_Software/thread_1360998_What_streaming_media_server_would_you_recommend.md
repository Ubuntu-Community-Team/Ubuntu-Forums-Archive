---
title: "What streaming media server would you recommend?"
date: 2009-12-21
forum: Multimedia Software
---

### Post by BioGeek on 2009-12-21
I have set up an old desktop box as a headless server running Ubuntu Server Edition. Attachted to it is a 1 terabyte external hard drive containing al my music and videos.

What is the best software to stream all of this content to my laptop/stereo/over the internet?

Thanks in advance.

---

### Post by jocampo on 2009-12-21
I just asked a similar questions hours ago and no response... luckily enough, thought out of the box and got some ideas now :-)

I went to a electronic store and found some Wireless Sound system that does not require software at all, just a USB connector; talking about Bose. Not sure if is going to work on Linux but will tell you soon 'cause planning to buy it. This is/will be my setup

1.Ubuntu headless server with a bunch of MP3s files
2.Ubuntu Jaunty (gnome running, of course) on my laptop
3./music folder shared on Server 
4.Exaile music player on laptop (using share folder)

Now, what I'm going to do/test is plug the USB connector on my Ubuntu laptop and stream the music content to the BOSE sound system ...

---

### Post by Fire_Chief on 2009-12-21
What is the laptop running and what do you want to use for your streaming client?
Many people use Mediatomb for streaming but you could use any number of solutions including
Icecast
Twonky
Ushare
MiniDLNA
NFS share

Cheers!

---

### Post by BioGeek on 2009-12-21
@jocampo: sounds interesting. I would be interested to hear if your setup works. Happy Hacking :-)

@Fire_Chief: I know already that there are [a lot of streaming media servers]("http://en.wikipedia.org/wiki/Comparison_of_streaming_media_systems"), so I just wanted to know which ones are considered the "best of breed" and/or have an active developer community.

That said, I have installed Mediatomb. It scans my folders with media files, but haven't got the streaming part working yet.

---

### Post by jocampo on 2009-12-21
> **BioGeek said:**
> @jocampo: sounds interesting. I would be interested to hear if your setup works. Happy Hacking :-)

@Fire_Chief: I know already that there are [a lot of streaming media servers]("http://en.wikipedia.org/wiki/Comparison_of_streaming_media_systems"), so I just wanted to know which ones are considered the "best of breed" and/or have an active developer community.

That said, I have installed Mediatomb. It scans my folders with media files, but haven't got the streaming part working yet.

Like I said before, not sure about the speakers/hw yet, but setup NFS share on server and put automount on your laptop, that's it. You will see all your music and can browse it with your favorite media player. ;-)

---

### Post by Fire_Chief on 2009-12-21
Did you happen to see the Ubuntu Community page on Mediatomb?
[https://help.ubuntu.com/community/MediaTomb]("https://help.ubuntu.com/community/MediaTomb")

---

### Post by jocampo on 2009-12-21
> **Fire_Chief said:**
> Did you happen to see the Ubuntu Community page on Mediatomb?
[https://help.ubuntu.com/community/MediaTomb]("https://help.ubuntu.com/community/MediaTomb")

nice, need to invest sometime and play/learn, but sounds a bit more complex (on my case) than using NFS share for my MP3s. Because any mp3 player is all I need once my laptop can connect and see the music files ... not sure what else MediaTomb can provide

---

### Post by jocampo on 2009-12-21
> **BioGeek said:**
> @jocampo: sounds interesting. I would be interested to hear if your setup works. Happy Hacking :-)


Man, it worked! lol ... sounds awesome! lol ... I think I have a party with wife tonight, at home, hahaha...

Had to change some settings via GUI but I will post configuration tomorrow!

---

### Post by BioGeek on 2009-12-22
Sweet :)

And I have got it working here as well. I installed Firefly Media server. iTunes on my girlfriend her Windows laptop picked it up immediately. And after I configured Rhythembox on my Ubuntu laptop according to [this guide]("http://coherence.beebits.net/wiki/RhythmBox") it works for me too :-D

---

