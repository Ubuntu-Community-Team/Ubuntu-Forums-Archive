---
title: "Banshee wont play, Gstreamer resource error: Openwrite"
date: 2009-02-11
forum: Multimedia Software
---

### Post by kraymore on 2009-02-11
i am getting this error in banshee:

[Error 11:43:01.206] GStreamer resource error: OpenWrite

i don't know what could be wrong, or how to solve it.

i have a bluetooth adaptor but no bluetooth headphones. this has never happened before. i also get a orange icon that happens to have a small in it next to any song i try to play.

anyone have any ideas ?

---

### Post by sgleo87 on 2009-02-14
I have the same problem (using Ubuntu Intrepid and Banshee 1.4.2). Banshee starts fine but when I double click a song it puts an "x" next to it, doesn't play anything, skips to the next song and does the same thing, and repeats this for about 5 songs. 
Here is my output:
```
[Info  13:51:30.643] Running Banshee 1.4.2: [Ubuntu 8.10 (linux-gnu, i486) @ 2009-01-22 07:54:13 UTC]
Mirage - Open DB - URI=file:/home/sandra/.cache/banshee-mirage/mirage.db,version=3
Mirage - Database version 2 is up to date
[Info  13:51:32.200] All services are started 1.41188s
[Info  13:51:33.264] nereid Client Started
[Error 13:51:36.245] GStreamer resource error: OpenWrite
[Error 13:51:36.663] GStreamer resource error: OpenWrite
[Error 13:51:37.050] GStreamer resource error: OpenWrite
[Error 13:51:37.376] GStreamer resource error: OpenWrite
[Error 13:51:37.766] GStreamer resource error: OpenWrite
```
Any ideas what is causing this?

---

### Post by NewJack on 2009-03-01
I am having a similar problem.  I have checked and it looks like I have all of the GStreamer plugins installed.

---

### Post by sgleo87 on 2009-03-02
I have resolved this issue and I think the problem was caused by pulseaudio. Try "killall pulseaudio" and then "pulseaudio" to restart it and see if it helps.

---

### Post by pixies7 on 2009-03-06
apparently my skype was using the same output resource. So i selected another output resource in skype
then did killall pulseaudio
then restarted pulseaudio with "pulseaudio &"

---

### Post by leonardosalinas on 2009-11-03
Hey
I think I managed to solve it. First, I removed completely Pulseaudio and [upgraded ALSA]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/"); rebooted and reinstalled Pulseaudio... crossed fingers and Banshee was working once again.
Hope it works for you!

---

### Post by piratemurray on 2009-11-10
These suggestions haven't worked for me. I'm a bit worried about removing pulseaudio since it (package manager) wants me to remove ubuntu-desktop along with it. 

I don't have skype to interfere with Banshee and I've tried killing and restarting pulseaudio. None of which has helped I'm afraid.

Banshee 1.6 Beta 2 (1.5.1)
Karmic AMD64

Please let me know if there is any further information you need to help me with this. Much appreciated!

---

### Post by cnelbuendia on 2009-11-27
Try reseting your GStreamer config to default.
To do so, go to a console a type de following:

```

sudo rm -rf ~/.gconf/system/gstreamer
sudo rm -rf ~/.gstreamer-0.10

```That worked for me, let me know if it does for you.

Cnelbuendia.

---

### Post by sthrudel on 2009-12-13
Are you sure you have *ubuntu-restricted-extras* installed?

---

