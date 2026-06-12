---
title: "Media Sharing to DirecTV DVR"
date: 2009-02-01
forum: Multimedia Software
---

### Post by kooseefoo on 2009-02-01
Hey,


I'm trying to figure out how to share the media on my linux box to a directv dvr that i have. They are all networked together, I just don't know of what I would need to install and configure. Bascially, from what I've read, with a program like Windows Media Player 11 you can share music and video from a computer to the DVR.

The DVR box I have is a DirecTV HR20, and my linux box is running ubuntu hardy server edition. It does not have X11 or a desktop environment installed.



Thanks,
Chris


Also, is there anything to do this on mac? iTunes?

---

### Post by Zero Prime on 2009-03-10
Bump, cause I have the same problem with Ubuntu 8.10

---

### Post by Joshua on 2009-11-08
Wow.  I'm surprised there wasn't a response to this.  I haven't been able to figure this out either, but it seemed like there should be a pretty straightforward way to do it - maybe with MythTV or something.  DirecTV wouldn't have set these DVRs up to only work with Windows Media Centers would they?

---

### Post by peepingtom on 2009-11-08
It probably follows the DLNA or UPNP standards for media streaming. Google around, you'll know for sure! You'll need a media server ps3mediaserver, mediatomb, ushare and moovida are all pretty cool in their own ways. You'll need to transcode, I bet that DVR doesn't have great codec support.

---

### Post by Joshua on 2009-11-12
Just to update.  I got it to work.

- Install Ubuntu 9.10
- Install mediatomb (it should be version 0.12)
- Run "mediatomb" in the terminal
- Copy the DirecTV HR2x sections from [http://mediatomb.cc/dokuwiki/transcoding:transcoding#directv_hr2x_transcoding]("http://mediatomb.cc/dokuwiki/transcoding:transcoding#directv_hr2x_transcoding") into the appropriate files.  (for the scripts, that should be in /usr/bin, and you need to make the files executable in the file properties - I think you will also need to be root to do this stuff)
- Hit ctrl-c in the terminal to stop mediatomb and then re-run it
- (After this step, I got an error for a section of the config file that I didn't care about, so I went back into the config file, deleted the section, and then restarted mediatomb again.)
- Ctrl-Click the link that it gives you in the terminal
- Use the web interface to share media

I'm using a DirecTV HR23 and things work pretty well.  MP3s, jpeg pictures, and mpeg videos work, but I haven't played around with it much yet.

---

### Post by bioborg on 2010-01-15
The above post worked for me with my HR22
Everything seems to work, music, video, photos.

---

### Post by rickyble on 2010-01-26
Just a note and a quick question.   I have just gotten a hr20 and I have connected it to my home network also.  I can scan see all my movies and recordings and they play back fine on my directv ...which is actually wild.  They are recorded on an older hacked hr10-250 and then transferred to my mythtv box.  However I can see my music and its all listed but they are all X-de out and when I select one of the songs it comes back no files in this folder.  I have Samba running also and they are accessible to other Windoze boxes in the house and of course to my Linux boxes ;-).  Any ideas?  I didnt want to put media tomb on the box.  The tunes play everywhere else.

---

### Post by izaakrach on 2010-05-02
> **Joshua said:**
> Just to update.  I got it to work.

- Install Ubuntu 9.10
- Install mediatomb (it should be version 0.12)
- Run "mediatomb" in the terminal
- Copy the DirecTV HR2x sections from [http://mediatomb.cc/dokuwiki/transcoding:transcoding#directv_hr2x_transcoding](http://mediatomb.cc/dokuwiki/transcoding:transcoding#directv_hr2x_transcoding) into the appropriate files.  (for the scripts, that should be in /usr/bin, and you need to make the files executable in the file properties - I think you will also need to be root to do this stuff)
- Hit ctrl-c in the terminal to stop mediatomb and then re-run it
- (After this step, I got an error for a section of the config file that I didn't care about, so I went back into the config file, deleted the section, and then restarted mediatomb again.)
- Ctrl-Click the link that it gives you in the terminal
- Use the web interface to share media

I'm using a DirecTV HR23 and things work pretty well.  MP3s, jpeg pictures, and mpeg videos work, but I haven't played around with it much yet.


This worked perfectly for me on Karmic but after I upgraded to Lucid it stopped.  I reinstalled mediatomb following these instructions and my movies still show up on the DVR with x's next to each one.  Has anyone gotten this to work after the upgrade?  Granted I did run the upgrade and I plan to do a fresh install of Lucid tomorrow so I'll let you know how that goes.

---

### Post by izaakrach on 2010-05-03
OK without doing a fresh install I figured out that the above was working as long as I started mediatomb manually in a terminal.  The instance that was starting automatically was using the wrong config.xml.  I later figured out that it was trying to use one in the /etc/mediatomb/ directory. I tried to overwrite that one but then it would never start on boot.  So now the quick and dirty solution based on my super limited knowledge which will crack most of you up was to ignore the fact that the first instance is simply failing and write a simple shell script and have cron run it at start.  I will look into learning how mediatomb actually works later this week when I have more time. In the mean time the kids now can watch their movies.

---

