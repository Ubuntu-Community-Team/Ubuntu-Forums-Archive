---
title: "KeyHoleTV"
date: 2008-07-24
forum: Multimedia Software
---

### Post by The Pinny Parlour on 2008-07-24
KeyHoleTV

How-To taken from the following thread that I started.  Cleaned up for ease and presented here: [http://ubuntuforums.org/showthread.php?p=5232466#post5232466](http://ubuntuforums.org/showthread.php?p=5232466#post5232466)

1) Download latest version to desktop
   [http://www.v2p.jp/video/Viewer/Linux/ubuntu8.04/LKeyHoleTV1.20-ubuntu.tar.gz]("http://www.v2p.jp/video/Viewer/Linux/ubuntu8.04/LKeyHoleTV1.20-ubuntu.tar.gz")

(Main Site URL: [http://www.v2p.jp/video/Viewer/](http://www.v2p.jp/video/Viewer/) )

2) Extract to desktop.
   Right click>Extract

3) Open Terminal and enter the following:
```
cd /home/YOUR USERNAME HERE/Desktop/KeyHoleTV 
```
then
```
./lkeyholetv
```

You should now be watching Japanese TV, or listening to Japanese Radio.

---

### Post by The Pinny Parlour on 2008-11-22
Unfortunately I haven't been able to get this working on Intrepid 8.10 yet.

Spoke to soon.  I got it working.

---

### Post by mindfall903 on 2008-12-31
uhm... what did you do to get it working?

I downloaded the tar file, decompressed it and installed the software via sudo make install which copied the executable to /usr/bin/local.
However, when I start the software from there, keyholetv starts but it's offline. When I try to go online, it says "cannot login".

The Q&A in Japanese on the homepage says that keyholetv uses UDP for connection and that security software should be configured to allow this. I'm pretty sure that this applies to Windows, not Ubuntu (where the appropriate ports will be opened automatically)

What further steps did you take?

---

### Post by Lostincyberspace on 2009-01-05
I agree I get:
```
lee@lee-desktop ~/Desktop/KeyHoleTV $ sudo ./lkeyholetv 
Can not Use ALSA

```

whether it is run as admin or normal

I can get the esd one to run though, but every 20-30 second I need to mute the sound or it fills with static.

---

### Post by The Pinny Parlour on 2009-01-11
New version.  Original post updated.

---

### Post by senor_smile on 2009-03-03
I have the exact same problem, although I've been using keyholetv successfully for a couple weeks.  I checked the site and I have the newest version.  Every minute or so, it becomes very loud and I have to mute it.  Anyone else able to fix this problem?  I also all of a sudden had to change from alsa to esd as well(as it tells me it can't initialize audio with default alsa selected).

---

### Post by Rujiel on 2009-03-29
I think your problem may be you're copying the executable to bin and not its support (or config) files. I think it needs its directory intact.

Thanks for this topic, I had a brain-explosion of linux understanding on seeing how you call an executable. (./ ohhhhh)

---

### Post by computermacgyver on 2009-03-29
I am running Ubuntu Hardy (8.04) and downloaded [http://www.v2p.jp/video/Viewer/Linux/Ubuntu8.04-32bits/LKeyHoleTV1.23-ubuntu.tar.gz](http://www.v2p.jp/video/Viewer/Linux/Ubuntu8.04-32bits/LKeyHoleTV1.23-ubuntu.tar.gz) which I believe is the most recent version of KeyHoleTV. 

After I install the package (sudo make install), I get the follow error upon running it:

```

$lkeyholetv 

(lkeyholetv:16725): Gdk-CRITICAL **: gdk_colormap_get_screen: assertion `GDK_IS_COLORMAP (cmap)' failed

(lkeyholetv:16725): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault

```

I'm sure one of the static libraries that it was linked against is different, but is there an easy way to tell which one and fix the problem?

&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

Edit: I should say this problem is exactly the same whether I install the software or just execute it from the directory the .tar.gz extracts to.

---

### Post by Rujiel on 2009-03-31
> **computermacgyver said:**
> I am running Ubuntu Hardy (8.04) and downloaded [http://www.v2p.jp/video/Viewer/Linux/Ubuntu8.04-32bits/LKeyHoleTV1.23-ubuntu.tar.gz](http://www.v2p.jp/video/Viewer/Linux/Ubuntu8.04-32bits/LKeyHoleTV1.23-ubuntu.tar.gz) which I believe is the most recent version of KeyHoleTV. 

After I install the package (sudo make install), I get the follow error upon running it:


Make install wasn't necessary for me to make it work. I just ran it from its folder:
./lkeyholetv

---

### Post by computermacgyver on 2009-04-10
Rujiel, may I ask what version of Ubuntu are your running?

I seem to have the same problem if I run it directly from the directory it extracts to or if I "install" it. Perhaps this is b/c I am using Hardy or it's my hardware. Oh well.

Thanks!

---

### Post by guga31bb on 2009-05-23
When I launch the program, it says "Selected Audio Device can not use now."

I have ALSA selected with "plughw:0,0". Nothing else works.

How can I fix this?

---

### Post by saxman66 on 2010-04-18
I am having the same problem. I hate to bring this dead post back but its better than making a whole other one. Any advice?

---

### Post by guga31bb on 2010-06-04
Same problem. Any ideas?

---

### Post by fergal on 2010-07-04
I got it working with this.

~/.asoundrc should have the following (it may not need all of this but now that I have it working I'm not touching it!):

```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

hook_func.pulse_load_if_running {
	lib "libasound_module_conf_pulse.so"
	func "conf_pulse_hook_load_if_running"
}

@hooks [
	{
		func pulse_load_if_running
		files [
			"/usr/share/alsa/pulse-alsa.conf"
			"/etc/asound.conf"
			"~/.asoundrc"
		]
		errors false
	}
]

```

and then you select "pulse" as the alsa device in the keyhole audio prefs.

---

### Post by ronnielsen1 on 2010-07-04
I got it working (Ubuntu 10.04) by right clicking the file, selecting extract here and then double clicking the lkeyholetv file. It worked, sound too

---

### Post by CyborgSmurf on 2010-10-30
I downloaded v 1.23 and extracted it on the desktop. Opened the directory and just clicked on the prog, worked perfectly! :guitar: Thank you for the prog :popcorn: ps. I use Ubuntu 9.10

---

### Post by Swifty31703 on 2010-12-05
Sorry to revive this thread all of the sudden but I have a quick question to ask. I have been using KeyHoleTV on Windows7 for a few months now but recently Windows7 blue screened and destroyed half of the data on the hard drive. I have switched over to Ubuntu which I have never really used as my main operating system. I have KeyHoleTV working now but I can't adjust the screen size like I did in Windows. I use to drag the edge of the program window to enlarge the viewing screen. I have noticed that trick doesn't work here on Ubuntu. Is there a way to enlarge the window and/or screen so I can sit back and watch? I am tired of sitting a foot from the screen to watch things. Thanks for any help!

---

### Post by soracantabile on 2011-04-26
sorry for bringing up this thread..

I just want to share, that I just downloaded KeyHoleTV with this thread as reference, and I also had same problem like (I think) most people have here. The audio didn't work.

Then I tried to install [FONT=Courier New]alsaplayer-alsa[/FONT] package from synaptic, and it's work!!

---

