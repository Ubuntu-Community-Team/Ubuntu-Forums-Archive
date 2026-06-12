---
title: "Flash video gets stuck in full screen"
date: 2010-11-22
forum: Multimedia Software
---

### Post by vikyjain on 2010-11-22
I have a very weird problem with Flash videos in youtube and hulu. the first time when i go full screen i could hear the audio moving forward but the video freezes. however the second time press escape and then do full screen (sometimes i repeat this more than once) it works completely fine. I am moving to ubuntu from windows vista. i never will have enough money to go back to vista and buy expensive software. Ubuntu is my only hope.. please help me fix this :p

---

### Post by big_bum on 2010-11-23
I have the same problem.

---

### Post by vikyjain on 2010-11-23
I have a Quad PRo 2 GHZ processor with 2 Gigs of memory. I suspected that it may have been due to Ubuntu being bloated with lot of pre-loaded stuff these days and my computer being low on resources. So i tried loading XFCE Desktop environment (XUBUNTU) and i dont see the problem occuring there. I miss the fancy GNOME desktop, but i think i have to give it up and just use XUBUNTU (relatively a boring looking desktop).

---

### Post by gs17 on 2010-11-23
Same problem. But I dont think it is hardware dependent.
But it does not always happen. 

Also, this workaround works *most* of the time:

If it gets stuck - 
 1. Undo fullscreen (Esc)
 2. Pause the video
 3. Go Fullscreen
 4. Play the video

---

### Post by vikyjain on 2010-11-23
WEll, if it works after the work around, then this should be a defect for sure. Is this reported?

---

### Post by vikyjain on 2010-11-23
I saw a lot of posts that mentioned if we remove Compiz, we could get rid of this problem. however i had no compiz in my machine. I was experimenting with XFCE. Since the look of XFCE was so dull i installed a theme package called MacBuntu 10.10 xfce-look.org. However after playing with it, i decided to uninstall it. Point to note here is, while i installed this package, it installed Compiz as well. and when i removed it, it removed along with it a whole lot of packages that i did not know about. 
Now after i restarted i went back to my GNOME environment and tried out youtube in mozilla... and guess what? it works just fine, no work arounds needed. 
however i noticed that my ubuntu maximise minimise animations are now gone. they are just doing the very basic thing after the macbuntu install. 
My guess is, there is some package that interferes with the flash video but i dont know what. i posted this just so that if someone researching this issue may get a hint on what exactly happened here.

---

### Post by tommcd on 2010-11-23
> **vikyjain said:**
> I suspected that it may have been due to Ubuntu being bloated with lot of pre-loaded stuff these days and my computer being low on resources. So i tried loading XFCE Desktop environment (XUBUNTU) and i dont see the problem occuring there....
If you want a *buntu that is really light on resources you could try **Lubuntu**:
[http://lubuntu.net/](http://lubuntu.net/)
I am running Lubuntu on the desktop in my sig and I have been happy with it. Lubuntu is fast and light, just like Ubuntu was back in the days of Warty and Hoary. Also, there is no pulseaudio on Lubuntu.
Speaking of pulseaudio, if you want to save a lot of CPU cycles on X/Ubuntu, just get rid of it:
```

sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio

```
Then run "*gstreamer-properties*" and set everything to alsa.

---

### Post by vikyjain on 2010-12-22
Thanks Tom! but what is a Pulse Audio?

---

### Post by tommcd on 2010-12-22
> **vikyjain said:**
> Thanks Tom! but what is a Pulse Audio?
Pulseaudio is the new sound server for Ubuntu as well as some other distros that use it like Fedora. See these:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)

---

### Post by vikyjain on 2010-12-25
Also! this forum helped me out on a fresh install on the same PC. 
Watch out 
[http://art.ubuntuforums.org/showthread.php?t=1593274&page=2](http://art.ubuntuforums.org/showthread.php?t=1593274&page=2)

---

### Post by vikyjain on 2010-12-27
These threads also helped a few others
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1193567[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1193567")
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=766683[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by arpad9 on 2010-12-27
I used to have the same problem.

I went into Flash settings (by right clicking on the flash video) and disabled hardware acceleration.

---

### Post by arpad9 on 2010-12-27
But of course, now, I have Flash 10.2 64-bit Square Preview ([http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)) AND 64-bit Firefox 4b9pre ([http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)) and I have been able to re-enable hardware acceleration without issue.

---

### Post by asheeshs on 2011-02-06
It fixed my Flash Full Screen problem - [http://www.youtube.com/watch?v=SeO8YytqEKE](http://www.youtube.com/watch?v=SeO8YytqEKE)

---

### Post by anshulfy on 2011-08-26
[http://www.youtube.com/watch?v=SeO8YytqEKE](http://www.youtube.com/watch?v=SeO8YytqEKE)  

This fixed my problem too :). Thanks

---

