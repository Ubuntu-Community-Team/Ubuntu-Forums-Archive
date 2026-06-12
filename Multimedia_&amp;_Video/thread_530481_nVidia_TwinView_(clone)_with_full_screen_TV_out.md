---
title: "nVidia TwinView (clone) with full screen TV out"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by Hercynium on 2007-08-20
**Here's what I want:** 

**[SIZE="3"][COLOR="DarkRed"]I want to play videos full-screen on the television while keeping the desktop on the CRT/VGA. Furthermore, I'd like to keep the video player's interface on the desktop, or at least have some way to manipulate the playback and play list from the desktop.[/COLOR][/SIZE]**

**Here's where I'm at:** 

I've recently purchased an MSI video card with an nVidia 7300LE GPU. This card has VGA, DVI, and SVIDEO/COMPOSITE/HD TV outputs.

The proprietary nvidia driver worked right out-of-the-box for just about everything - DRI 3D acceleration, TwinView (clone *and* separate modes) Xinerama, you name it. The nvidia-settings app did everything it was designed to do.

I got this working on Windows XP, but I needed to downgrade my driver from version 100.xx to version 87.xx (or something like that... I don't remember off the top of my head) 

My config in a nutshell on Windows is that I enabled TwinView in clone mode so the desktop displays on both the VGA and the TV. I then configured the nvidia control panel to display fullscreen video on the TV. 

Since my VGA resolution is greater than 1024x768, the desktop on the TV uses 'panning'. However, when videos play, the TV does not pan, everything displays perfectly. 


[CENTER][I]I simply minimize the media player window on my VGA monitor and the video continues to play full-screen on the TV.
[/I]
**[SIZE="3"][COLOR="DarkOrchid"]That is the type of experience I want to get working in Ubuntu.[/COLOR][/SIZE][/CENTER]**

[CENTER]:popcorn: :popcorn: :popcorn:[/CENTER]

I've spent the past couple of days reading up on overlays, XVideo, SDL, TwinView, nVidia configs, VLC, Totem, GStreamer, etc, etc, etc... I believe this can work, it's just a matter of time...

[COLOR="Red"]I haven't yet seen any solutions to this that fit my preferences, so I'm creating this post to try to gather more info and share my (hopefully successful) results![/COLOR]

**Right now, the closest thing I've found is this:** 
[LIST][http://en.wikibooks.org/wiki/NVidia/TV-OUT]("http://en.wikibooks.org/wiki/NVidia/TV-OUT")
[/LIST]

Perhaps I can play with it later tonight or tomorrow and see if it can't be modified to fit my needs.


**SO...** 

[SIZE="3"][COLOR="DeepSkyBlue"]Has anyone else out there gotten their system to work like I want mine to work? Are other people interesting in doing this with their systems? Please post with your ideas and advice and perhaps we'll figure out the magic config that makes this work![/COLOR][/SIZE]

[INDENT] [SIZE="3"]**[COLOR="Blue"][COLOR="Navy"]~Hercynium[/COLOR][/COLOR]**[/SIZE] :KS[/INDENT]

---

### Post by belacs1 on 2007-10-24
Have you been able to get your system setup the way you want? Your situation is EXACTLY like mine. I have twin view set right now but i still want to be able to have movies running full screen on my tv and be able to control or minimize  the player on my desktop so i can do other tasks. In totem : edit>prefrences their is a full screen tv-out option but it is grayed out and nothing i have done with my display setting has allowed me to select that option. 

 If you find/found a solution that allows you to play movies in full screen on your tv, as you described in your post, let me know please

---

### Post by mikko.ohtamaa on 2008-05-10
> **Hercynium said:**
> **Here's what I want:** 

[SIZE="3"][COLOR="DeepSkyBlue"]Has anyone else out there gotten their system to work like I want mine to work? Are other people interesting in doing this with their systems? Please post with your ideas and advice and perhaps we'll figure out the magic config that makes this work![/COLOR][/SIZE]

[INDENT] [SIZE="3"]**[COLOR="Blue"][COLOR="Navy"]~Hercynium[/COLOR][/COLOR]**[/SIZE] :KS[/INDENT]

I am! :guitar: (playing Judas Priest - Breaking the law)

On Ubuntu 8.04 Hardy Heron.

With a lot of sweat and curses. The year 2008 is not yet the year of Desktop Linux.

1. Use nvidia-settings to enable your TV-out as "Separate X Screen", This way TV doesn't interference the normal computer usage. Save config file. Restart X (press CTRL-ALT-BACKSPACE).

Installing and using nvidia-settings: [http://ubuntuforums.org/showthread.php?t=735986](http://ubuntuforums.org/showthread.php?t=735986)

Do not use System menu shortcut: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/229090](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/229090)

Launching another X screen will break Compiz and you need a workaround:
[http://ubuntuforums.org/showthread.php?t=536045&page=5](http://ubuntuforums.org/showthread.php?t=536045&page=5)  (I reported this bug also in Launchpad)

2. Install VLC video player (Totem support does not work)

[https://answers.launchpad.net/ubuntu/+source/totem/+question/8391](https://answers.launchpad.net/ubuntu/+source/totem/+question/8391)

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/218454](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/218454)

3. Start VLC with special command line switch, or it will crash

```

vlc --no-wx-embed 

```

Bug: [http://forum.videolan.org/viewtopic.php?f=13&t=40278](http://forum.videolan.org/viewtopic.php?f=13&t=40278)

4. Edit VLC settings. Enable "Advanced options" bottom right checkbox in VLC Setting dialog. For Video > Output > XVideo modules type following text to "X11 display" option 

```

:0.1

```

Screen for fullscreen mode setting seems to be ineffective:

[http://209.85.129.104/search?q=cache:IQqy6pqi6NMJ:https://trac.videolan.org/vlc/ticket/1420+vlc+%22screen+for+fullscreen+mode%22&hl=fi&ct=clnk&cd=1&gl=fi&client=firefox-a](http://209.85.129.104/search?q=cache:IQqy6pqi6NMJ:https://trac.videolan.org/vlc/ticket/1420+vlc+%22screen+for+fullscreen+mode%22&hl=fi&ct=clnk&cd=1&gl=fi&client=firefox-a)

5. Play video. Output should go to TV now. 

Please vote/comment mentioned bugs so that developers will look the issues and we might get them solved before 2015.

Cheers,
Mikko

---

### Post by mikko.ohtamaa on 2008-05-10
To get video back to your primary display, you need to clear "X11 video display" settings in Video > Output modules > XVideo and stop/restart video. This is PITA.

---

### Post by mikko.ohtamaa on 2008-05-10
Also if you have widescreen TV (which you probably have) you can enter value 16:9 in Video > Monitor pixel aspect ration. Advanced options checkbox must be toggled and you need to scroll down settings a bit.

---

### Post by mikko.ohtamaa on 2008-05-10
Also see:

[http://brainstorm.ubuntu.com/idea/206/](http://brainstorm.ubuntu.com/idea/206/)

---

