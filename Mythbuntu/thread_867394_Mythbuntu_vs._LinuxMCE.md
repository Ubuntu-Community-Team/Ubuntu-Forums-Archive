---
title: "Mythbuntu vs. LinuxMCE?"
date: 2008-07-22
forum: Mythbuntu
---

### Post by bmwman on 2008-07-22
I have a Mythbuntu 8.04 for couple of months. I'm still tweaking the system. My biggest problem is watching LiveTV, the picture is very choppy, especially with the HD channels. I have HD Homerun dual network tuner which has a built in hardware MPEG2 encoder so it shouldn't load the PC too much. Anyway, i just watched this video on YouTube and I was really impressed.
[http://youtube.com/watch?v=QcNwnANrCpw&feature=related](http://youtube.com/watch?v=QcNwnANrCpw&feature=related)

Has anyone tried LinuxMCE and is it any better (mostly lightweight) than Mythbuntu?

---

### Post by tgm4883 on 2008-07-22
It's much heavier.  LinuxMCE is supposed to be a home automation setup that controls your lights and everything.  In my experience from testing and from what I've read, it is a serious pain to setup, and it doesn't work as designed when it is setup.  YMMV though, and like most things OSS, it's free to try.

About your tuner, it has hardware encoding, but that doesn't decode the video.  What are your system specs?

---

### Post by bmwman on 2008-07-22
I use IBM ThinkCenter P4 3Ghz, RAM 2GB- PC5300 667Mhz, 500GB sata HDD, built in video Intel965 128MB. It's not top of the line but it should be fine. Most everything works fine, except LiveTV. I don't know if it's the video drivers, i tried reinstalling but it got worse, then i reverted back to the original.

---

### Post by freymann on 2008-07-22
> **bmwman said:**
> Anyway, i just watched this video on YouTube and I was really impressed.
[http://youtube.com/watch?v=QcNwnANrCpw&feature=related](http://youtube.com/watch?v=QcNwnANrCpw&feature=related)

Has anyone tried LinuxMCE and is it any better (mostly lightweight) than Mythbuntu?

 LMCE is a very different beast than MythBuntu.

 The people that put MythBuntu together have done an excellent job! Support here is super and for the most part, I would say MythBuntu "just works"

 LMCE, as one of the previous posters has said, can be a real pain to get working properly. You should be prepared to tinker, tinker and tinker some more. You might even have to keep putting out cash trying to find that magic combination of hardware that works under LMCE.

 That being said, I'm quite pleased to be using both :-)

 It wasn't an easy road and it's not for the faint of heart.

 LMCE is a complete home automation system that includes media. Media is likely 20% of what LMCE actually does.

 If you're after media, stick with MythBuntu... it does a great job.

 If you want to "play" with media AND a host of other things, then by all means give Linux MCE a try. 

 The video is what got me hooked. But you don't get all those neat bells and whistles as easily as you would think, and it will cost you a fortune to assemble all the equipment to duplicate what you saw. Be warned.

 Oh yeah, LMCE prefers nVidia video chips. Your intel (and ati) are already show stoppers.

---

### Post by nickrout on 2008-07-23
> **bmwman said:**
> I use IBM ThinkCenter P4 3Ghz, RAM 2GB- PC5300 667Mhz, 500GB sata HDD, built in video Intel965 128MB. It's not top of the line but it should be fine. Most everything works fine, except LiveTV. I don't know if it's the video drivers, i tried reinstalling but it got worse, then i reverted back to the original.

Some people seem to specify a minimum of a dual core cpu to do justice to HiDef streams. depends on whether your video card is doing any hardware assistance on the decoding though.

---

### Post by laga on 2008-07-23
If it only happens in LiveTV, you're probably affected by [http://svn.mythtv.org/trac/ticket/5025](http://svn.mythtv.org/trac/ticket/5025)

For testing purposes, try turning off the deinterlacer.

---

### Post by bmwman on 2008-07-23
> **laga said:**
> If it only happens in LiveTV, you're probably affected by [http://svn.mythtv.org/trac/ticket/5025](http://svn.mythtv.org/trac/ticket/5025)

For testing purposes, try turning off the deinterlacer.

Yes, it only happens during LiveTV. If I watch a recording or any of my movies with VLC as a player, it works fine. The mplayer as a default player in MythTV is choppy most of the times too.

---

### Post by nickrout on 2008-07-23
do you mean mplayer as default player in mythvideo?

What is it trying to play? codec? frame size? format?

---

### Post by bmwman on 2008-07-23
Yea. Normally mythvideo uses mplayer but it can be changed with VLC indtead. About codecs and formats - whatever the default recording format is and my movies are in .avi

---

### Post by nickrout on 2008-07-23
well your answer is unhelpful. I asked for specifics of what you are trying to play in mplayer, and you say .avi. Well thats not going to help. I need to know what codec, what frame size. ```
ffmpeg -i filename.avi
``` will give you the answer.

I don't think you have a powerful enough machine to play HD material. However you also say mplayer is choppy. I am trying to determine what sort of material you are trying to play in mplayer. If it is also quite processor hungry hi def material then, again, it may be lack of processor power. If it is lower definition stuff that should play OK on your machine, then there is a more deep seated problem.

Now how about [LIST=1]
[*]looking at the log files for mythfrontend and posting what you find during stuttery playback; and
[*]running mplayer from the command line and reporting back what it says.
[/LIST]

That is, if you really want help.

---

