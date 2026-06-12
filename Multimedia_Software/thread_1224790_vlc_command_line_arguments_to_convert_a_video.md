---
title: "vlc command line arguments to convert a video"
date: 2009-07-27
forum: Multimedia Software
---

### Post by pythonscript on 2009-07-27
What command line arguments would I use to convert a video (format might vary) to, say, and avi file? I'm looking to script this, and this is the main command I'm missing (and also the meat of the script). Thanks!

---

### Post by pythonscript on 2009-09-05
Anyone have any ideas?

---

### Post by Gen2ly on 2009-09-05
Most people either use mencoder (part of mplayer) or ffmpeg to do this.  Though vlc can probably do this I haven't seen anything written on it.

---

### Post by andrew.46 on 2009-09-05
Hi pythonscript,

> **pythonscript said:**
> What command line arguments would I use to convert a video (format might vary) to, say, and avi file?

As Gen2ly has mentioned documentation for the commandline vlc is more than a little scanty and I will confess that I am myself more accustomed to MEncoder and FFmpeg. But perhaps a good start might be:

VLC-0-9-x command-line help
[http://wiki.videolan.org/VLC-0-9-x_command-line_help](http://wiki.videolan.org/VLC-0-9-x_command-line_help)

and this page has links to other versions and a little bit of general information on the commandline vlc. An even more useful page that I note contains a bash script for conversion is here:

Transcode
[http://wiki.videolan.org/Transcode](http://wiki.videolan.org/Transcode)

Perhaps mc4man might have a bit more information?

Andrew

---

### Post by michael37 on 2009-09-05
As was mentioned before, there are probably BETTER and MORE APPROPRIATE tools to convert file than VLC. 

Is there a reason why you need to use VLC?

---

### Post by pythonscript on 2009-09-06
> **michael37 said:**
> As was mentioned before, there are probably BETTER and MORE APPROPRIATE tools to convert file than VLC. 

Is there a reason why you need to use VLC?

Not particularly, no, but in my experience, it's been the most stable graphical player, and I'm hoping for a cross platform solution.

---

### Post by michael37 on 2009-09-07
> **pythonscript said:**
> Not particularly, no, but in my experience, it's been the most stable graphical player, and I'm hoping for a cross platform solution.

Here is what works for me.

**[SIZE="4"]Avidemux[/SIZE]** 
[IMG]http://fixounet.free.fr/avidemux/index_files/screenshot1.png[/IMG]

[General information and Windows download]("http://fixounet.free.fr/avidemux/")
[Linux download]("http://www.getdeb.net/app/Avidemux")

**[SIZE="4"]Handbrake[/SIZE]** 
[IMG]http://trac.handbrake.fr/raw-attachment/wiki/LinGuiScreenshots/HandBrake-Pic.jpeg[/IMG]

[General information, Windows, Linux and Mac]("http://handbrake.fr/")
[Ubuntu repository]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")

---

