---
title: "what program does myth tv use to play avi files?"
date: 2008-01-18
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-18
what is the default program mythtv uses to play avi files?

---

### Post by racmar on 2008-01-18
It uses an internal player based off mplayer.  However, what I think you are asking is how do you play avi files using mythtv.  So, you'd need to install mythvideo and add the videos to the correct directory.

```
sudo apt-get install mythvideo
```

next, copy your avi files to:  /var/lib/mythtv/videos

finally, restart the frontend and find the new mythvideo section.

---

### Post by tgm4883 on 2008-01-19
You can also have mythtv use an external player such as VLC or XINE.

[http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration](http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration)

---

### Post by onesojourner on 2008-01-20
actually I need mythtv or mplayer to load more of a video before it starts playing. the playback is sketchy when I try to stream stuff over the network. I can stream the same video on my xbox though with out a problem.

I think I have the answer:

If either of those help, then change the mplayer.conf file. look at your mplayer.conf file and look for these lines:

Quote:
# cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50

---

### Post by racmar on 2008-01-20
I use several separate frontends on my network, and one is wireless.  I have not had any streaming problems /w either the frontend or playing videos with mythvideo.  Also, we do have HD content and no problems there either. 

Are you using wireless?  Is the content HD?

---

### Post by onesojourner on 2008-01-21
The machine that is hosting the content is wireless but the myth box is not. It is not hd.

---

### Post by racmar on 2008-01-22
Oh, what kind of wireless are you using?  I am using 802.11g, I'm not sure if 802.11b is fast enough to stream uncompressed mpeg2 video reliably.  Then again, you said earlier that your xbox works reliably with the same setup.  It's a strange problem.

Perhaps you could try to have all computers wired and do a test to see what happens when you remove the wireless bottleneck.

---

### Post by onesojourner on 2008-01-23
yep its G so that is not the issue.

---

