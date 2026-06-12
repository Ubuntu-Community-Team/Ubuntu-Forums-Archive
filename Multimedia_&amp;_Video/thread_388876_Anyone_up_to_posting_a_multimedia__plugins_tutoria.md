---
title: "Anyone up to posting a multimedia / plugins tutorial for newbies to make Firefox work"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by brjoon1021 on 2007-03-20
Hi,

As a recent convert to Linux I can say that webiste embedded streaming audio and video is a downer. I am accustomed to watching and listening to A/V streams in Windows that do not work in Linux. This is one of the most gleaming disparities between the OS's. I bet that some of you experienced users have found many fixes.

I have heard rumors that with the right editing of config files and the right plugins: Flash, gxine, Mplayer, VLC, Real/Helix one can play almost everything that Firefox in Windows can play. Yahoo.com videos, BBC videos and radio, some Fox sports video and many others just open a dead Mplayer page or a dead Flash window in Linux. The problem seems to be that the plugins overwrite eachother and squabble over formats.

Have any of you figured out how to make Firofox in Linux as handy as it or Internet Explorer is in Windows? Care to share, if so? In fact, a tutorial like that deserves a sticky. Users of every distribution would be indebted to you.

Thanks,

B.

---

### Post by Bloch on 2007-03-21
I had much the same ide some time ago - see my thread
Looking out for a streaming video guru
[http://www.ubuntuforums.org/showthread.php?t=363806&highlight=guru](http://www.ubuntuforums.org/showthread.php?t=363806&highlight=guru)

since I wrote that BBC clips have stopped playing nicely with my realplayer plugin, though paradoxically the realplayer plugin now works very well on the RTE (Irish national tv/radio) website.

Apart from specific techie solutions, I am curious as to why streaming video is so hiss and miss and whether the future looks brighter.

---

### Post by 8oluf7 on 2007-03-26
Not a tutorial - more a case of 'How I got RealPlayer  to play BBC streams in Firefox without crippling Firefox'.

If you are using the latest version of Ubuntu (6.10, otherwise known as Edgy Eft) the first place to look for advice on installing the extra stuff you will need for playing audio and video streams is the Unofficial Edgy User Guide:

[INDENT][http://ubuntuguide.org/wiki/Ubuntu_Edgy#Unofficial_Ubuntu_6.10_.28Edgy_Eft.29_Starter_Guide](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Unofficial_Ubuntu_6.10_.28Edgy_Eft.29_Starter_Guide)[/INDENT]
This document has sections on all of the stuff you will need. I used it to install Flash, Java, RealPlayer ... 

However, whenever I used RealPlayer to play the BBC streams, Firefox slowed to a crawl. I eventually found help on the Forums and followed the instructions to install gxine one evening. 
Firefox behaved normally while it played the BBC streams and I thought I had a result. Unfortunately, the next morning, gxine would lose the stream every couple of minutes. I've no idea what causes this, but I thought I would try the alternative (thanks Red Knuckles), described here:

[INDENT][http://www.ubuntuforums.org/showthread.php?t=356903&highlight=realplayer+gxine](http://www.ubuntuforums.org/showthread.php?t=356903&highlight=realplayer+gxine)[/INDENT]

Install alsa-oss using Synaptic or, in a terminal:
```
sudo aptitude install alsa-oss
```
Install realplay (if it isn't there already) using Synaptic (NB not realplayer – which installs an older version)

Open the realplay file in a text editor (I use Gedit, but any text editor will do e.g. Kwrite for KDE users) :
```
sudo gedit /usr/lib/realplay-10.0.8/realplay
```
Edit this line [it's line 73]
[INDENT]$REALPLAYBIN "$@"[/INDENT]
to read:
[INDENT]aoss $REALPLAYBIN "$@"[/INDENT]

Save and exit text editor.

**NB** – this fix is now in the Unofficial Guide!

**NB2** – The RealPlayer site also recommends aoss but has an alternative edit – AFAICT it has the same effect.

**[SIZE="4"]In Firefox[/SIZE]**

Tools > Add-ons

Click 'Get Extensions'

Search for 'MediaPlayerConnectivity'

Install this extension.

When asked to set up media players for the different streams, ensure realplayer is selected for RealMedia (/usr/bin/realplay)

Now – when you pull up the BBC Radio Player, there will be a MediaPlayerConnectivity thumbnail in the top left corner of the window. Select the programme you want to listen to and click on the thumbnail. 

I've found that, using RealPlayer, I don't suffer the dropout problems I was experiencing with gxine. And it works equally well with the BBC's video clips.

MediaPlayerConnectivity is a real boon, as it enables you to experiment to see which player gives the best results for each type of stream. It prevents the frustrating confusion which otherwise occurs when you expect to be using one player, say gxine, and Firefox insists on using another, say mplayer (or both at once, which is worse).

BTW – RealPlayer has some test streams here (but, apparently, the video ones don't work with Firefox!):

[INDENT][http://service.real.com/test/](http://service.real.com/test/)[/INDENT]

If your problem may be hardware related, this looks like a good place to go:

[INDENT][http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)[/INDENT]

---

### Post by brjoon1021 on 2007-03-29
Cool, thanks guys.

I also decided to post the same question at Linuxquestions.org under the same user name. Maybe we can all find help in those answers, as well.

Thanks again.

---

