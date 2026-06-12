---
title: "Suggestion for using MCE Remote on Ubuntu"
date: 2009-11-29
forum: Multimedia Software
---

### Post by Dearhell on 2009-11-29
So in Windows I used media portal wich worked pretty fine with my MCE remote.

[IMG]http://www.multimediapc.nl/images/MCE%20remote.jpg[/IMG]

What I want now it's to use a similar program to view the videos stored in my computer using my MCE remote to control the interface. 

I don't mind using mplayer directly with the MCE remote if that's possible. 

I've tried MythTV but it seems to much oriented to TV control than to play videos already in the computer, and also I couldn't figure it out how to make it work with my videos. 

Any suggestions?

---

### Post by rsay on 2009-11-29
Lirc is the linux program that interprets button presses from infrared remote controls. Lirc supports the MCE remote completely. On many computers, the MCE remote will even wake the computer from S3 suspend. There are several places on the internet that explain how to configure lirc with an MCE remote. I went the easy route and installed the mythbuntu control centre, which has a "Remote" section that will launch a script to set up an MCE remote automatically.

I am not familiar with media portal, but there are lots of video players in linux. Mplayer, xine, vlc and totem are all popular. A mythfrontend only install with mythvideo would probably be the best to use from a remote control. It can get video covers, movie descriptions, actors, year of release, etc. from imdb. Then you can browse through a gallery of movie covers instead of trying to pull up a video from a file list. If you really don't want any of the other myth functionality, you can comment out the other menu entries so you only have the video section. I will warn you that myth is pretty addicting. First you only want videos, then you think maybe it would be good to navigate your music collection, then you think how nice it would be to pull up a weather report, or your photo gallery, or a movie preview.

p.s. Myth can launch an external video player (like mplayer) if the internal player is having problems with your video collection.  Setup>Setup>Media settings>Video settings>Player settings

---

### Post by Dearhell on 2009-11-29
Thanks, that was very useful. I've been able to get my mce remote working with the mplayer. 

But I've not been able to set the video folders. I went to mythtv-setup and select "Storage directories" and added the desktop folder and other folders but none of them appeared when I went again into aplications -> sound video -> mythtv-frontend -> media librarie

---

