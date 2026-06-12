---
title: "Flash really slow in Karmic"
date: 2009-11-15
forum: Multimedia Software
---

### Post by damnated on 2009-11-15
I have a 4000+ AMD X2 CPU, Nvidia 8600GT video card and 3 gigs of ddr2 ram, with the video driver and flash installed, yet flash runs like a turtle in firefox. 

Every site that has flash to some extent is slow, even youtube, but sites that are entirely flash based, like my brute run as if i had a pentium 2. And it's not a browser based issue: same thing is true for Konqueror. Slow as a fat, old hog.

Also, it's not just the site i'm browsing. My cpu use is up every time to 50-60%.

Any ideas?

---

### Post by lovinglinux on 2009-11-15
See Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). But don't expect miracles.

---

### Post by damnated on 2009-11-15
No change :(

---

### Post by masux594 on 2009-11-15
what kind of flash plugin are u currently using? See in your about:plugins and paste the lines below "Shockwave Flash"..

Sysc, A

---

### Post by damnated on 2009-11-15
Shockwave Flash 10.0 r32

---

### Post by masux594 on 2009-11-16
Oki, and under that? Please, post the entire paragraph.. 

Sysc, A

---

### Post by Iteria on 2009-11-16
I'm having the same problems as this guy. This is what I have under shockwave flash:

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Hope it helps you find a solution to this problem. It's really bad. The internet is almost unusable sometimes for me.

---

### Post by masux594 on 2009-11-17
> **Iteria said:**
> File name: libflashplayer.so
    Shockwave Flash 10.0 r32

Oki, so, you have the "adobe-flashplugin" currently installed.. well, uninstall it using ```
sudo apt-get remove adobe-flashplugin
```.. now, if u restart your browser, you will see [an about:plugins] that the plugin disappeared[try it].. right? if not, post a message.. Then, now install the flashplugin-nonfree using ```
sudo apt-get install flashplugin-nonfree
``` and the new plugin are now installed, restart firefox and then try it in youtube or something else..

Sysc, A

---

### Post by Iteria on 2009-11-17
Wow, there was a huge improvement. Thank you.

---

### Post by nunovi on 2009-11-21
Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

---

### Post by alexfish on 2009-11-21
removed

---

### Post by alexfish on 2009-11-21
got flash player 10 from

 [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

  re :bbc iplayer no sound 
  
   only tried firefox  do know about chrome/chromium 

  read first / 

   you also have to config the files in pulse and also from the pulse jack / pulseaudio device  chooser 


/etc/pulse/daemon.conf file 

  you can tweak the system ie speakers ect/ect

---

### Post by shpansk on 2009-11-27
Hey guys, 

All I really use flash for is videos, so this trick is only really useful if you want to watch fullscreen videos.

I just now discovered a little trick that will enable you to play the videos as if they were directly on your hardisk without having to use the flash plugin directly.

The trick isn't a trick so to speak, its just merely taking advantage of the buffered content that streaming technology utilises to appear to play files without load times.

 Everytime you stream a video, ubuntu creates a new file with a corresponding title like 'FlashOCNZcD' in your '/tmp' folder. If you watch the folder, the filesize of the FlashOCNZcD file grows as the buffering bar on the website nears completion. This FlashOCNZcD is your video stream.

The trick is to pause the stream (which still lets the video buffer) and instead of playing the stream in firefox, open the FlashOCNZcD file in vlc!

BINGO !!!

I cant believe I never thought of this before...

Tested on Ubuntu 9.04 Jaunty, flash10, firefox 3.0 and VLC .9.9a

---

### Post by lovinglinux on 2009-11-27
> **shpansk said:**
> Hey guys, 

All I really use flash for is videos, so this trick is only really useful if you want to watch fullscreen videos.

I just now discovered a little trick that will enable you to play the videos as if they were directly on your hardisk without having to use the flash plugin directly.

The trick isn't a trick so to speak, its just merely taking advantage of the buffered content that streaming technology utilises to appear to play files without load times.

 Everytime you stream a video, ubuntu creates a new file with a corresponding title like 'FlashOCNZcD' in your '/tmp' folder. If you watch the folder, the filesize of the FlashOCNZcD file grows as the buffering bar on the website nears completion. This FlashOCNZcD is your video stream.

The trick is to pause the stream (which still lets the video buffer) and instead of playing the stream in firefox, open the FlashOCNZcD file in vlc!

BINGO !!!

I cant believe I never thought of this before...

Tested on Ubuntu 9.04 Jaunty, flash10, firefox 3.0 and VLC .9.9a

Or you can simply download it with [Video Download Helper](https://addons.mozilla.org/en-US/firefox/addon/3006). Much easier.

This is problematic when the original video has several parts. For example a TV channel here publishes some programming without commercials, so they cut the video in pieces and the player joins them while watching. In this case, you would have to look for each part of the video in the tmp folder. But with Video Download Helper is pretty easy, since it adds each new part automatically. All you have to do is advance the flash player to each part and download. Then close the flash player and watch all videos from a local folder.

I use mkvtoolnix to join them on a single video, without the hassle of re-encoding.

---

