---
title: "How To: Capture video from a DV camcorder with dvconnect Ubuntu 7.10 Gutsy"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Sabot on 2007-11-04
For some reason my laptop just would not allow me to use raw1394 and Kino to capture video from my firewire PC Card.  It would just freeze.  I had to find another way.  I found a command line program called dvconnect that allows me to capture without any problems. It uses video1394 to do this.

What you need to install:

```
sudo apt-get install libdv-bin
```

Then add video1394 to your modules that load at boot time:

```
sudo gedit /etc/modules
```

Type in video1394 at the bottom of the list of modules.

Restart your computer.

Now you can connect your camcorder to your firewire card.

Open a terminal and enter:

```
dvconnect -v myvideo.dv
```

You can press play on your camcorder and the video will be captured to a file called myvideo.dv in your home folder.  You can also capture live video from your camera. dvconnect saves video in raw dv format.

When you are done capturing just press Ctrl-c.  You can then use Kino, Cinelerra,and Live to edit your video.

---

