---
title: "Avi playback"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by Jawshie on 2007-10-30
Hey guys. I'm having a problem :(    I searched Google and Ubuntuforums.org but failed to find what I needed. The other day AVI files ran fine. Now when I try to play them with any media player they show up with green squiggles and no possible recognition of the picture, however there is sound. I dont know what to do. I tried reinstalling the Ubuntu restricted extras package and stuff. I think it started happening after I used ManDVD... but I love ManDVD cause its the only thing that will make making dvds from my anime avis so easy :(

---

### Post by mythik on 2007-10-30
I'm getting the same problem.  Except for me, it's all mpgs.  Mplayer gmplayer, totem-xine, totem-gstreamer,kaffeine noatun - all have this problem.

---

### Post by mythik on 2007-10-30
You know what, I just crashed X server (ctrl+alt+backspace) - logged back and tried to watch movies again and it worked.

Kinda pisses my off though.

---

### Post by coreyva on 2007-10-30
Same thing here. All players, originally noticed in mythfrontend. Restarting X is the only, however brief, solution. I've tried various nvidia drivers, using the beta 100.14.23, without change. I've tried KDE, GNOME, and XFCE, same thing. Fiesty had no issues, ugrading to gutsy is when it started. Did a fresh install with no change. Just glad I'm not the only one seeing this. Running 32bit 2.6.22-14-generic with an nvidia GeForce 7200GS.

---

### Post by Jawshie on 2007-10-30
Haha good news. A simple reboot (well.... restart of X) fixed the problem. How silly is that?!

CTRL + ALT + BKSPC
or 
Just reboot.

---

### Post by bconverse on 2007-10-30
I am also having this issue, though it appears to only be "every now and then".  It also appears to be with other filetypes besides .avi as well, even with the reliable VLC player.

---

### Post by coreyva on 2007-10-30
> **Jawshie said:**
> Haha good news. A simple reboot (well.... restart of X) fixed the problem. How silly is that?!

CTRL + ALT + BKSPC
or 
Just reboot.

It will be back.

---

### Post by spacepirates on 2007-10-31
I've got the same issue on 64bit Kubuntu with an NVIDIA 6800GS.

all movie players don't work, the funny thing sometimes my screensaver (electricsheep) will still work even though it shouldn't because electricsheep just plays fullscreen avi movies...

oh, and i haven't used manDVD, so that i don't believe that is tied in with this problem

---

### Post by dward526 on 2007-10-31
have you tried re-installing the 'restricted' and DivX/AVI codecs...it is worth a shot.  When I was having other problems with playback, this helped resolve them.

---

### Post by bingoUV on 2007-10-31
can you guys try changing video output : like do 
```

mplayer -vo help

```

It will list a bunch of video outs mplayer supports. Just try some of these like 
```

mplayer -vo x11
mplayer -vo xv

```

I used to get strange video with default video output, but -vo x11 fixed it for me.

---

### Post by ohzopants on 2007-10-31
That's spot on bingo! "mplayer -vo x11" works fine, but with xv I still get the issue.

If you have any other brilliant insights (like how to make this the default for all players perhaps), I'd be very grategul.

---

### Post by ohzopants on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just did some digging over at launchpad and there is a bug reported for this.  Apparently it's an nvidia driver issue.

---

### Post by spartan777 on 2007-10-31
I'm having the exact same issue everyone else is having. it was fine when I first installed gutsy, but just started happening yesterday. here's what mine looks like. same thing happens with avi, xvid, mpg, divx, ogm and under all video players.

[IMG]http://farm3.static.flickr.com/2150/1810397182_9b4c29ffb1_b.jpg[/IMG]

---

### Post by coreyva on 2007-10-31
It's an [nvidia bug]("http://www.nvnews.net/vbulletin/showthread.php?t=98852"). I tried downgrading with envy, but had lockup issues. I grabbed 100.14.11 from the nvidia website and all is well now.

---

### Post by williammanda on 2007-10-31
Please post how you downgraded.
Thanks

---

### Post by coreyva on 2007-10-31
1. Remove your current nvidia driver
    aptitude remove nvidia-glx-new
2. download the [nvidia driver]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")
3. logoff of your session
4. switch to a different console ctrl-alt-f1
5. login and quit X
    sudo /etc/init.d/(k|g)kdm stop
6. run the nvidia installer
    sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run
7. answer a few questions and you should be set.
8. either reboot or restart X
     sudo /etc/init.d/(k|g)kdm stop
9. voila

---

### Post by ohzopants on 2007-10-31
Please, please, please don't use the word **viola** anymore.  It's spelled voila.

Viola means raped.

Sorry, it's just a pet-peeve of mine.  That and "deja vu all over again"...

---

### Post by bingoUV on 2007-10-31
> **ohzopants said:**
> That's spot on bingo! "mplayer -vo x11" works fine, but with xv I still get the issue.

If you have any other brilliant insights (like how to make this the default for all players perhaps), I'd be very grategul.

I think you have to tell this to each player separately.
for mplayer, put the following in your ~/.mplayer/config(create this file if it is not there)
```

vo=x11
zoom=yes

```

For vlc, settings -> preferences -> output modules -> X11

---

### Post by coreyva on 2007-11-01
> **ohzopants said:**
> Please, please, please don't use the word **viola** anymore.  It's spelled voila.

Viola means raped.

Sorry, it's just a pet-peeve of mine.  That and "deja vu all over again"...
Ah, sounds like a pet peeve my grandmother had, no offense. Her's was the pronounciation of forte. It should be pronounced as fort vs for-tay.

Lesson learned.

---

### Post by Jawshie on 2007-11-01
Ahh it comes and goes now. It comes, I restart X... it comes again after a day or so of being logged in. After a while it seems to offset the audio and I have to pause the video for it to catch up and play it again.

I'm sad :(

---

### Post by williammanda on 2007-11-02
> **coreyva said:**
> 1. Remove your current nvidia driver
    aptitude remove nvidia-glx-new
2. download the [nvidia driver]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")
3. logoff of your session
4. switch to a different console ctrl-alt-f1
5. login and quit X
    sudo /etc/init.d/(k|g)kdm stop
6. run the nvidia installer
    sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run
7. answer a few questions and you should be set.
8. either reboot or restart X
     sudo /etc/init.d/(k|g)kdm stop
9. voila

I downgraded to 100.14.11 64 bit. I'll post any problems through the weekend.
Thanks

---

### Post by williammanda on 2007-11-05
It seems that reverting back is not any better. I have not had any occurrences of the inital problem but have had some other video issues. It seems that I have gained nothing. Hopefully the new driver will be out soon.
Thanks

---

