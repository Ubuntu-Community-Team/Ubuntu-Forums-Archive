---
title: "Understanding Multimedia in Ubuntu"
date: 2009-11-12
forum: Multimedia Software
---

### Post by deamon_knight on 2009-11-12
I'm setting up a new system, and I'm trying to settle on a good media player for use in ubuntu/xubuntu. However, I'm sure I understand enough to even ask the right questions. I followed the instructions here and appear to have all media types working [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

However, before that I would get odd situations where one player would play one type of media but not another properly. Since I'm not sure why that is, I'm afraid to make any changes. I'm looking to have one players run everything, but if I have to settle on Totem for everything but DVDs (as VLC has worked best for me in the past). Key features are to rotate the video during playback, playback incomplete files and integrate well with the file manager (Thunar as I'm trying Xubuntu, but if nautilus is needed I can switch.) so I can step through a number of files one at a time in a directory without having to configure playlists.

I don't understan dthe relationship from backend to frontend so its not clear to me what is Just a GUI for a set of tools and what is a separate program whos selection of supported media types needs to be considered.

This is all functionality I found available on my Windows system in the K M player [http://download.pandora.tv/]("http://download.pandora.tv/") However there is no linux version. 

Can anyone suggest some options?

Thanks

---

### Post by HappyFeet on 2009-11-12
Even when I used windows in the past, I always used VLC for everything. I still do. 

[Here]("http://en.wikipedia.org/wiki/Category:Linux_media_players") is a list of linux media players. Install some of them and try them out. It won't hurt anything to install/uninstall a bunch of apps.

---

### Post by deamon_knight on 2009-11-13
I really appreciate the reply HappyFeet, and I do use VLC on my windows box, and its my choice for playing DVDs in Ubuntu, but it has never been my experience that I could just install VLC from the repos and then could play everything. I know that is not the case for me here. I downloaded the video trailer for the new Mechwarrior:
[http://www.techpowerup.com/downloads/1457/Mechwarrior_5_Trailer_HD.html]("http://www.techpowerup.com/downloads/1457/Mechwarrior_5_Trailer_HD.html")

And had the amusing situation of Mplayer able to play the audio (but not video), Movie Player could play the video and identified that needed to install an audio codec, but was unable to locate one, and VLC told me it could not play the audio in this file and there was nothing I could do to fix this.

Following the instructions listed in ther fourmsI was able to get this file to play properly in Mplayer (Great!), but now I'm not sure if addition players will try to makes changes and foul things up!

---

### Post by VertexPusher on 2009-11-13
> **deamon_knight said:**
> I don't understan dthe relationship from backend to frontend so its not clear to me what is Just a GUI for a set of tools and what is a separate program whos selection of supported media types needs to be considered.
The most important difference between Totem and the other players is that Totem uses the GStreamer framework. GStreamer is quite similar to DirectShow on Windows. A GStreamer plugin is equivalent to a DirectShow filter. If you install new GStreamer plugins, they will be available to all GStreamer-based multimedia applications.

Totem, VLC and MPlayer all have their specific strengths and weaknesses, so it's always a good idea to install all three. Totem is extensible through GStreamer. VLC is optimized for streaming, on-the-fly transcoding and screen capturing. MPlayer has very good support of SSA/*** subtitles, DVD menus and a large set of video filters.

Edit: *** means _A_dvanced _S_ub_S_tation Alpha. Stupid censorship.

---

