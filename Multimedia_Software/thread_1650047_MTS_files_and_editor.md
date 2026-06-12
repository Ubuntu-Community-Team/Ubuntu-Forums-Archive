---
title: "MTS files and editor"
date: 2010-12-21
forum: Multimedia Software
---

### Post by Vepar on 2010-12-21
I have a problem playing MTS files... I tried the default movie player and VLC media player, but it's the same thing, video starts normal, but then it starts being choppy and skips frames... Sound's alright though, but video is not watchable.

Those are files from a camera, and i want to edit them.

Can someone recommend what program to use to edit them? Can any program even read mts files, and if not, what and how would i convert them into something (idk, avi maybe) and not loose the quality, so i can edit them and play them...

For editing, i don't mind converting them, but as i have limited disk space so i'd prefer to be able to play and edit MTS files without converting them cause i don't want to delete the original files...

---

### Post by sir_robert007 on 2010-12-21
> **Vepar said:**
> I have a problem playing MTS files... I tried the default movie player and VLC media player, but it's the same thing, video starts normal, but then it starts being choppy and skips frames... Sound's alright though, but video is not watchable.

Those are files from a camera, and i want to edit them.

Can someone recommend what program to use to edit them? Can any program even read mts files, and if not, what and how would i convert them into something (idk, avi maybe) and not loose the quality, so i can edit them and play them...

For editing, i don't mind converting them, but as i have limited disk space so i'd prefer to be able to play and edit MTS files without converting them cause i don't want to delete the original files...

You can use Kdenlive (u can find it in the repositories) to edit MTS video files. When installing Kdenlive make sure u are using version 7.7 or higher as I had major issues using 7.5.

Also are the MTS files of HD quality? Because if they are your CPU may not be powerful enough to play them. I once tried playing HD MTS video files on an old 2ghz dual core machine using VLC and I had the same problem but when I played them on my quad core machine they play just fine

---

### Post by Vepar on 2010-12-21
Thank you i'll try that for editing.

Yes, the MTS files are HD quality... And i do have a single core processor (AMD AMD 3000+ 64 bit with 1.5 GB RAM) but i have Win7 on the same machine and they play fine in Windows Media Player, so if they play in a system that's much more demanding on resources like Win7, why wouldn't they play on Ubuntu too... Maybe i don't have some codecs or something? I'm still new to Linux so i wouldn't know how to check if i'm missing something... 

I did install restricted extras and all other video plays fine (didn't test mkv yet), so i don't know why MTS is so slow...

---

### Post by sir_robert007 on 2010-12-21
> **Vepar said:**
> Thank you i'll try that for editing.

Yes, the MTS files are HD quality... And i do have a single core processor (AMD AMD 3000+ 64 bit with 1.5 GB RAM) but i have Win7 on the same machine and they play fine in Windows Media Player, so if they play in a system that's much more demanding on resources like Win7, why wouldn't they play on Ubuntu too... Maybe i don't have some codecs or something? I'm still new to Linux so i wouldn't know how to check if i'm missing something... 

I did install restricted extras and all other video plays fine (didn't test mkv yet), so i don't know why MTS is so slow...

Hmmmm thats new to me. I always though that u had to have a quad core cpu to play HD quality mts videos unless windows media player 12 is optimized to play HD videos on a single core machine much like HD videos that you buy from iTunes are optimized to play on a 1ghz Apple TV

Oh hey if you installed all the restricted extras then mkv video files should play

---

### Post by Vepar on 2010-12-21
> **sir_robert007 said:**
> Hmmmm thats new to me. I always though that u had to have a quad core cpu to play HD quality mts videos unless windows media player 12 is optimized to play HD videos on a single core machine much like HD videos that you buy from iTunes are optimized to play on a 1ghz Apple TV

Oh hey if you installed all the restricted extras then mkv video files should play

Well, they do play, it's just that they're unwatchable... :sad:
I don't get it, Windows media plays them just fine... I mean, they're not like on a quad core obviously, but i can watch them with minimal stuttering (almost none). In Ubuntu however, the video drops to like 2 FPS (slideshow lol) after a second or two...

Also, i've been observing the differences lately, and i've noticed that in Linux, there's screen tearing (like without Vsync in games, idk how to explain it), and lower quality image than in Win7. Doesn't really bother me, but still... There's definately something either wrong or different at least...

I mean i have a GeForce 9600 GT with 512 MB ram, HQ should work, even on a single core (they do in Win7)...

Also, there are horizontal lines on Win7 when i watch MTS files but i'm assuming that's because of my lousy computer. Even though, i can watch them, and in Ubuntu i cannot...

Any ideas, suggestions? :D

---

### Post by Vepar on 2010-12-22
K, just an update, i tried making something in Kdenlive with those MTS files, and when i play it in Kdenlive's player, it's the same thing, barely plays, so i can't even edit them (since i can't play the video to see where to cut etc.)...

Is it really my computer or is there something other wrong with my Ubuntu system...

Btw, i upgraded to 10.10, but no change (don't know if that could actually change anything at all, but just an information if someone finds it useful).

---

### Post by sir_robert007 on 2010-12-23
> **Vepar said:**
> K, just an update, i tried making something in Kdenlive with those MTS files, and when i play it in Kdenlive's player, it's the same thing, barely plays, so i can't even edit them (since i can't play the video to see where to cut etc.)...

Is it really my computer or is there something other wrong with my Ubuntu system...

Btw, i upgraded to 10.10, but no change (don't know if that could actually change anything at all, but just an information if someone finds it useful).

yeah i had the same problem in Kdenlive when i tried to play them in that dual core machine

Oh hey is ur video card PureVideo enabled? From what ive heard Nvidia cards that are pure video enabled offload some of the HD video decoding from ur cpu. Its designed to work with media player software like Windows Media player with would explain why ur videos play better in windows.

I just happened to research this now as I was remembering off  the top of my head that Nvidia cards had a feature that offloaded HD video decoding but i couldnt remember what it was called.

Wikipedia
[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)


EDIT: you might also want to try the latest version of VLC as hardware acceleration s supported. U will have to install it from the VLC PPA archive. U can find the instructions here.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Scroll down to the bottom of the page and u will find the instructions for adding the ppa archive.

U may also want to to check in Ubuntu Software Centre before u do this as VLC 1.1.0 may already be in the Maverick repositories though I wouldnt know as I am still using Lucid

EDIT2: Ok apparently i scrolled down a bit to fast on the second web page. VLC 1.1.0 is indeed in the Maverick repos  as there are install options for 10.10. Hope this helps. 

Im gonna be out of town for the next 4 days so i may or may not be able to respond during that time. Let me know if u get it working.

---

### Post by Vepar on 2010-12-23
> **sir_robert007 said:**
> yeah i had the same problem in Kdenlive when i tried to play them in that dual core machine

Oh hey is ur video card PureVideo enabled? From what ive heard Nvidia cards that are pure video enabled offload some of the HD video decoding from ur cpu. Its designed to work with media player software like Windows Media player with would explain why ur videos play better in windows.

I just happened to research this now as I was remembering off  the top of my head that Nvidia cards had a feature that offloaded HD video decoding but i couldnt remember what it was called.

Wikipedia
[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)


EDIT: you might also want to try the latest version of VLC as hardware acceleration s supported.

[http://forums.nvidia.com/index.php?showtopic=172492](http://forums.nvidia.com/index.php?showtopic=172492)

Hmmm, now that you mention it, that could be it, it's a GeForce 9600 GT (some pumped up edition) with 512 MB RAM, so it would explain why it works with on Windows...

I have VLC 1.1.4. so it should work but it doesn't. I enabled it in preferences, but nothing changed...

I searched google a bit and found this:

[http://wiki.videolan.org/VLC_GPU_Decoding](http://wiki.videolan.org/VLC_GPU_Decoding)
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)
[http://strangestone.livejournal.com/107092.html](http://strangestone.livejournal.com/107092.html)

which should enable GPU decoding, but i'm a bit lost...

I'm still very new to linux and don't quite understand how this is done...

I got the "libva" package downloaded, but i don't know how to install it (don't know how to install anything in linux for that matter, except for the stuff in synaptic where you just click on a button lol).

Can anyone make a newbie version out of [this]("http://wiki.videolan.org/VLC_VAAPI")? :D
If not (or that IS the newbie version) then it's ok, i'll just watch MTS files on windows...

---

### Post by sir_robert007 on 2010-12-23
> **Vepar said:**
> Hmmm, now that you mention it, that could be it, it's a GeForce 9600 GT (some pumped up edition) with 512 MB RAM, so it would explain why it works with on Windows...

I have VLC 1.1.4. so it should work but it doesn't. I enabled it in preferences, but nothing changed...

I searched google a bit and found this:

[http://wiki.videolan.org/VLC_GPU_Decoding](http://wiki.videolan.org/VLC_GPU_Decoding)
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)
[http://strangestone.livejournal.com/107092.html](http://strangestone.livejournal.com/107092.html)

which should enable GPU decoding, but i'm a bit lost...

I'm still very new to linux and don't quite understand how this is done...

I got the "libva" package downloaded, but i don't know how to install it (don't know how to install anything in linux for that matter, except for the stuff in synaptic where you just click on a button lol).

Can anyone make a newbie version out of [this]("http://wiki.videolan.org/VLC_VAAPI")? :D
If not (or that IS the newbie version) then it's ok, i'll just watch MTS files on windows...

Ok the libva and Nvidia drivers appear to be in source code so you will need to compile that source code, then install it. Basically its a three step process... 

sudo .configure 
sudo make
sudo make install

that you execute in a terminal window. At this point im gonna have to leave the explaining to someone else with more experience in this as i have only compiled source code only once before and not nearly as complicated as this.

---

### Post by datlink on 2011-05-18
Also Ubuntu 11.4 same thing. 

the video glitch and when played on pc even my windows xp old crap, .mts plays well with no glitch. I think Ubuntu the OS has the issue. My windows 7 DELL STUDIO 1735 mts play perfect when switch to ubuntu 11.4 on the same unit the mts glitch the eff all thru.

> **Vepar said:**
> K, just an update, i tried making something in Kdenlive with those MTS files, and when i play it in Kdenlive's player, it's the same thing, barely plays, so i can't even edit them (since i can't play the video to see where to cut etc.)...

Is it really my computer or is there something other wrong with my Ubuntu system...

Btw, i upgraded to 10.10, but no change (don't know if that could actually change anything at all, but just an information if someone finds it useful).

---

