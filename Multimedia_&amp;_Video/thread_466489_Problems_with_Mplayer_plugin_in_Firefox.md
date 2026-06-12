---
title: "Problems with Mplayer plugin in Firefox"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by skhobotu on 2007-06-06
Hi from Korea!
i am using Linux Feisty Fawn 7.04 and Swiftfox with all the plugins, but when I go to a video site the Mplayer plugin will not load the video or it takes about 10 minutes then it plays poorly with lots of pauses.
i have used Automatix and checked to see if there are any updates and everything appears to be fine.
I have tried reassigning the video to another player (avidemux) in the Firefox preferences, but it makes no difference.
Any suggestions?

---

### Post by bobbybobington on 2007-06-06
I kinda have the same issue. I simply right click and open the video in movie player. It can be annoying sometimes, but at least it gets the job done.

---

### Post by rfurman24 on 2007-06-07
My Mplayer works with the ffplugin from synaptic packages. After installing I had to right click on the video window and play with the settings make sure a video output is selected.

---

### Post by NeoLithium on 2007-06-07
I removed all the plugins for mozilla and just used VLC. It plays everything I want embedded :)  just make sure you remove all the others, or there will be conflicts :)

---

### Post by skhobotu on 2007-06-10
Thanks, I'll try that.
Steve.

---

### Post by battra on 2007-06-12
in /etc/mplayerplug-in.conf, set noembed=1 and set cachesize=1024 or something high for buffering.

---

### Post by skhobotu on 2007-07-29
Still no joy with this problem, especially where the designated website player is Windows Media Player.
I have no problem with Real Player sites or ones like Reuters or BBC.
Any suggestions on how to fool the site into thinking I am running WMP?

---

### Post by logos34 on 2007-07-29
> Still no joy with this problem, especially where the designated website player is Windows Media Player.
I have no problem with Real Player sites or ones like Reuters or BBC.

And my problem is (and always has been) the opposite.

---

### Post by Gremlinzzz on 2007-07-29
i  use mplayer plugin you have to configure it right click on the video  screen and choose configure choose X11 for vidio and alsa for audio do you have codecs these are the ones i use 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
paste the link your trying to watch ill see if i can watch it.

---

### Post by skhobotu on 2007-07-30
The site I am trying to watch is [www.tv3.co.nz](www.tv3.co.nz) ( being as how I am a Kiwi in Korea!).
I will try the link for the codecs. 
Thanks,
Stevo.:)

---

### Post by Gremlinzzz on 2007-07-31
I went to site tried the videos i cant watch them either.Just freezes up so its not just you.

---

