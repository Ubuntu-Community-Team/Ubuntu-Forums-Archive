---
title: "Is there software to download a podcast."
date: 2012-03-27
forum: Multimedia Software
---

### Post by gardengxc on 2012-03-27
Is there software that can download a podcast after it was removed from itunes but still archived on the mane site? I can play the podcast via the web just fine but the download links and the RSS don't work anymore.

---

### Post by ron999 on 2012-03-27
> **gardengxc said:**
> I can play the podcast via the web just fine...
Hi
If you can play the podcast in your browser then there probably is software able to download it.
:p

---

### Post by ajgreeny on 2012-03-27
If you can play it or stream it, you can record it with **sound-recorder**, **audacity** or even **arecord**, but you may also like to try the firefox add-on download-helper, which camn probably download the mp3 (or whatever it is) direct.

For arecord use command ```
arecord -t wav -f cd -d 600 $(date +%F_%H-%M)-podcast.wav
``` where 
**-t wav** is output filetype, 
**-f cd** is a shortcut for CD quality recording, 
**-d 600** is duration in seconds (10 mins in this case) and [B]
$(date +%F_%H-%M)-podcast.wav[/B] is the filename with date variable added to show as *2012-03-27_21-11-podcast.wav* (todays date and current UK time)

---

### Post by gardengxc on 2012-03-28
download-helper works, thanks. I'm going to leave this thread up in case someone knows a different option like that that doesn't require Firefox.

---

### Post by sillygolem on 2012-04-01
Most podcasts not on iTunes will have RSS feeds, which you can copy and past into the "Add Podcast Feed" on Rhythmbox.

---

### Post by shantiq on 2012-04-02
my favourite piece of kit for downloading itunes podcasts is Tunesviewer which is in synaptic then you play the file in vlc or movie player smplayer etc...   if that answer your question


[ATTACH]215333[/ATTACH]

---

### Post by ufugu on 2012-04-02
Gpodder (in the repos) is a great podcasting tool.  Better than iTunes.  Works best if you have the feed URL, but a couple of times it has even figured out the correct rss or xml for me with just the main site address.

---

