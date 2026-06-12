---
title: "About the xVid codec??"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by billdotson on 2007-02-26
I hear the xVid codec is illegal.. is that true?  Also how do I use the xVid 4 in avidemux to make a really compressed video (ex: 8GB to 700MB file)?

---

### Post by shirilover on 2007-02-26
I don't believe it is illegal.

[QUOTE=Xvid.org]Xvid is an open-source research project focusing on video compression and is a collaborative development effort. All code is released under the terms of the GNU GPL license.

The Xvid video codec implements MPEG-4 Simple Profile and Advanced Simple Profile standards. It permits compressing and decompressing digital video in order to reduce the required bandwidth of video data for transmission over computer networks or efficient storage on CDs or DVDs. Due to its unrivalled quality Xvid has gained great popularity and is used in many other GPLed applications, like e.g. Transcode, MEncoder, MPlayer, Xine and many more.[/QUOTE]

---

### Post by jocheem67 on 2007-02-28
No it's not illegal, it's a derivate from the divx codec.

In avidemux, you can use the xvid4 codec. You should install xvid4conf for some detailed settings though. Also ffmpeg in avidemux is possible, also creates a .avi and is maybe a bit quicker.

---

### Post by (4M)Stephen on 2007-04-12
I googled many things, and I found that if you run the following scripts, and run the video with VLC Player, it works. 

*sudo gedit /etc/apt/sources.list*

add the following lines to it (replace VERSION with dapper, edgy, or feisty)
[I]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) VERSION universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) VERSION universe multiverse[/I]

then install mplayer
*sudo apt-get install mplayer*

get the codecs
*sudo apt-get install avidemux xvid4conf ffmpeg*

refer to [http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html")
for more info on mplayer and w32codecs libdvdcss2 apps.

remember to install VLC Player and you should be good...

note you can visit [http://lunapark6.com/?p=2501]("http://lunapark6.com/?p=2501") for info on installing VLC and other useful programs

---

### Post by devout on 2008-07-10
None of the above has worked for me.
These are the steps I've done... reading from varius forums and how to's

Using synaptic, checked totem-xine for instalation, totem-gstreamer is automaticly removed.
From [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#CD.2FDVD](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#CD.2FDVD)
	sudo apt-get install libdvdread3
	sudo /usr/share/doc/libdvdread3/install-css.sh
	Then in the Multimedia Players section, has a link "Mplayer with Multimedia Codecs Installation Tutorials". Follow instructions there.
	
	sudo apt-get upgrade
	sudo apt-get dist-upgrade
	install avifile-xvid-plugin using Synaptic.
	As per [http://ubuntuforums.org/archive/index.php/t-371196.html](http://ubuntuforums.org/archive/index.php/t-371196.html)	sudo apt-get install avidemux xvid4conf ffmpeg
	Look at [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) for how to install vlc.
		sudo apt-get update
		sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

		echo "deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe" > /etc/apt/sources.list.d/vlc.list ##although permission denied on this for some reason.
      sudo apt-get update
      sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2

My .avi will not play on:
   Totem using gstreamer or xine.
   MPlayer.
   VLC.

The .avi plays on windows boxes fine...
I'm running out of ideas.
Any one got any more?

---

