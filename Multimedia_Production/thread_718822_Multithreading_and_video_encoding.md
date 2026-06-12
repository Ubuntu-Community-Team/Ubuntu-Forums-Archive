---
title: "Multithreading and video encoding"
date: 2008-03-08
forum: Multimedia Production
---

### Post by Dubbayoo on 2008-03-08
I'm building a new box and I spend a fair amount of time burning video to dvd. Am I better off with a Q6600 quad cpu or an overclocked Core 2 Duo? Will I be able to take advantage of the extra processors? Thanks.

---

### Post by ahaslam on 2008-03-08
Get the quad. I do a lot of xvid & x264 encoding on an OCd C2D, 4 threads would be greatly appreciated. To take advantage of the extra cores you'll need to use mencoder via the cli (far superior to any gui). Lavc & x264 have threaded support & xvidcore has support within cvs.

You'll still end up overclocking the quad (and the Q6600 is a good choice) ;)

---

### Post by Creative2 on 2008-03-08
man mencoder.....**if you enable threads **

for x264(about 90% faster if you have dual core ) and xvid(15% faster if you have dual core)

threads: This option allows to spawn threads to encode in parallel on multiple CPUs. You can manually select the number of threads to be created or, better, set threads=auto and let x264 detect how many CPUs are available and pick an appropriate number of threads. If you have a multi-processor machine, you should really consider using it as it can to increase encoding speed linearly with the number of CPU cores (about 94% per CPU core), with very little quality reduction (about 0.005dB for dual processor, about 0.01dB for a quad processor machine).

---

### Post by Dubbayoo on 2008-03-10
How can I figure out which options the default packages for x264, ffmpeg and mplayer are built with? If I want to recompile I just want to use the default options **plus** threads=auto. 

I have a dual Xeon system with hyperthreading enabled.

---

### Post by Creative2 on 2008-03-10
you don't need to recompile you must only write that option on ffmpeg or mencoder command line...

man ffmpeg 
man mencoder

---

### Post by Dubbayoo on 2008-03-10
> **Creative2 said:**
> you don't need to recompile you must only write that option on ffmpeg or mencoder command line...

man ffmpeg 
man mencoder
I don't run those directly when I convert video. I use tovid or DeVeDe so I want to make sure those apps use threads by default.

---

### Post by ahaslam on 2008-03-13
They don't use them by default, you'll need to use the cli.
I find the html man page easier to search: [http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

PS. Some good info to get you going: [http://gentoo-wiki.com/HOWTO_Create_a_DVD](http://gentoo-wiki.com/HOWTO_Create_a_DVD) ;)

---

### Post by ahaslam on 2008-03-13
An example:
```

mencoder *x264.mkv *-of mpeg -mpegopts format=dvd -srate 48000 -ofps 25 \
-ovc lavc -oac lavc -lavcopts vcodec=mpeg2video:**threads=2**:vrc_buf_size=1835:\
keyint=15:vrc_maxrate=9800:vbitrate=4900:mbd=2:mv0:trell:aspect=16/9:\
acodec=ac3:abitrate=256 -vf expand=aspect=16/9,scale=720:576,harddup -o dvd.mpeg2
# make iso image:
dvdauthor -t dvd.mpeg2 -o dvd/
dvdauthor -o dvd/ -T
mkisofs -dvd-video -v -o dvd.iso dvd

```
This is faster than DeVeDe on a multi-core (& slightly better quality). 

;)

---

### Post by sarman on 2008-04-28
I find this thread across google just now, but it is not good for me too. Why do i need Devede? In Devede i ordinary convert not only one divx, just run, quick select up to 3 avi. Some of than 4:3, some 16:9, larger or smaller, so i ALWAYS quick play with visual size calculator to fast reduce some of them video quality to compromise. If I save videos from my cam, gggrawl, up to 10-15 videos to one dvd... Make some menus, etc... Easier way for me -> Devede. In advanced options adding that string (-lavcopts vcodec=mpeg2video:threads=4) is very painful for every file, so you may hack some python Devede code. Edit /usr/lib/devede/devede_video_convert.py and somewhere after

		command_var.append("-lavcopts")
	
		lavcopts="vcodec="
		if disctype=="vcd":
			lavcopts+="mpeg1video"
		elif disctype=="divx":
			lavcopts+="mpeg4"
		else:
			lavcopts+="mpeg2video"

		#add that string here, choose your thread model (2 or 4 threads)
		lavcopts+=":threads=4"

Dirty, but not so painful later.

---

### Post by sarman on 2008-04-28
p.s.

or threads=auto

---

### Post by HOLLYW00D on 2008-05-03
sorry, i'm new at this.  when i add

[INDENT]*lavcopts+=":threads=auto"*[/INDENT]

after

[INDENT][I]command_var.append("-lavcopts")

lavcopts="vcodec="
if disctype=="vcd":
lavcopts+="mpeg1video"
elif disctype=="divx":
lavcopts+="mpeg4"
else:
lavcopts+="mpeg2video"[/I][/INDENT]

devede doesn't even start.  it doesn't "look" right.  what am i doing wrong?  i have it looking like this:

[INDENT][I]command_var.append("-lavcopts")
	
lavcopts="vcodec="
if disctype=="vcd":
lavcopts+="mpeg1video"
elif disctype=="divx":
lavcopts+="mpeg4"
else:
lavcopts+="mpeg2video"
[COLOR="Red"]**lavcopts+=":threads=auto"**[/COLOR]
	
if videofile["trellis"]:
lavcopts+=":trell"
	
if videofile["mbd"]==0:
lavcopts+=":mbd=0"	
elif videofile["mbd"]==1:
lavcopts+=":mbd=1"
elif videofile["mbd"]==2:
lavcopts+=":mbd=2"[/I][/INDENT]

any help would be greatly appreciated.  thanks in advance.

---

