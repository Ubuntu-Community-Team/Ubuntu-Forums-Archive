---
title: "Gnash unable to play youtube HD"
date: 2013-02-23
forum: Multimedia Software
---

### Post by BKDW34 on 2013-02-23
Greetings community--

I am a hardcore Ubuntu user and have been for years. This is my first post.

I am tired of Flash for videos. The HW acceleration just isn't happening without me changing the adobe mms file. However, this is extremely unstable and it crashed.

I have a basic Nvidia GT610 card. 

So I have switched to Gnash hoping that it would help me. The 480p is fine. But when I want to go to HD 720 or 1080, it simply won't do it. It just won't load. 

**Question: Is gnash capable of playing HD and if so: what can I do to make this happen? **

I installed it (0.8.10) from the repository. I am being driven insane by this--I have searched endlessly for an answer.

Thanks for your help.

---

### Post by shantiq on 2013-02-24
hi BK 

HD is generally still a problem on Ubuntu in my personal experience
Yesterday i even tried 13.04 to see if it was better there



but same as it ever was

480p fine 720p slight lag 1080p virtually does not move
i do not think gnash cn improve on flash  [tried it a while back and for me it was worse than flash]


went to a friend's house a while back and he has a basic mac laptop
was amazed to see it handled YT 1080p without any problem whatsoever

mind you even downloading a 1080p only leaves the option of playing it with smplayer nothing else ever has worked for me [also [**XBMC **]("http://en.wikipedia.org/wiki/XBMC_Media_Center")but for me [navigating]("http://wiki.xbmc.org/index.php?title=Keyboard") it was never intuitive or pleasant]  cannot remember if umplayer handles hd [um just tested it and slight lag i think even with vdpau]


edit:   aving had a further play around Xmbc is really good [some of u might want to try]as it is the 

&#9679;only video player which plays 1080p OOTB on Ubuntu [smplayer requires changing video setting to vdpau whereas it is on vdpau by default on xbmc]
&#9679;also the quality of the picture seems superior on xbmc in relation to smplayer
&#9679;it has the most unintuitive minimize/fullscreen i have ever seen  you have to hit ```
\
```
&#9679;for continuous play videos right-click on folder then press play
&#9679;it installs from the repo  ```
sudo apt-get install xbmc
```

[B]
So[/B] sometimes i too get frustrated with HD on Buntu; surely all the clever guys who program and use Linux could fix that [or maybe it is really complicated] but then i look at all the good things Ubuntu-Linux offer and i get a sense of perspective

But let us say it once more: HD on Ubuntu is still a problem in early 2013 and it needs addressing positively and fixing :KS

---

### Post by evilsoup on 2013-02-24
You can play youtube videos in VLC. From the command-line, you can simply 

```

vlc http://youtube.com/blahblah

```

For integration with firefox, look up the add-on 'Open With'.

Obviously, not an ideal solution, but it's a workaround.

---

### Post by shantiq on 2013-02-24
> **evilsoup said:**
> You can play youtube videos in VLC. From the command-line, you can simply 

```

vlc http://youtube.com/blahblah

```

For integration with firefox, look up the add-on 'Open With'.

Obviously, not an ideal solution, but it's a workaround.


are you getting 1080p to play fine through vlc?    never has that happened to me      they just choke:KS

---

### Post by evilsoup on 2013-02-24
I have to admit I've never tried; my netbook is unable to play 1080p *anything*, though it just about manages with 720p (even streaming youtube videos), albeit with occasional tearing.

---

### Post by BKDW34 on 2013-02-28
Thanks for the responses....  I don't mean to be a pain, but I really want to get gnash working. I know about the VLC work-arounds.    This has been driving me crazy. It's like it wants to play the HD, but it simply freezes--the picture contacts then doesn't play.     I was hoping that some brilliant person figured out how to do it.     Gnash is a great project--with all of the flash issues, I personally think gnash development should be a priority of our community.  I think the project has lots of potential.   I think we really need our own primetime flash/swf player.  If I had the programming expertise, I would work on this, but unfortunately, I don't :(

---

### Post by evilsoup on 2013-03-01
You could maybe try out Shumway, if you're using firefox.

---

### Post by joe4ska on 2013-07-13
VLC, plays the highest version available in my test. You can check in the stream codec info.

I tried Fedora 19 recently and Gnash worked in Firefox on YouTube in HD 720p and 1080p and played well so It should be possible for them to fix it in the next release.

---

### Post by Claus7 on 2013-07-13
Hello,

I had an old graphics card (>10 years), which was unable to support HD from firefox, yet with the advice from *lovinglinux* I was able to get the most from my system:
[http://ubuntuforums.org/showthread.php?t=1455335&p=9132571#post9132571](http://ubuntuforums.org/showthread.php?t=1455335&p=9132571#post9132571)

Now, things are more than ok. I would advice you to use his guidelines, since it fixes not only FF, but also other browsers. 

Regards!

---

