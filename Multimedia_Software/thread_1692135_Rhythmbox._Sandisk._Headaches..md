---
title: "Rhythmbox. Sandisk. Headaches."
date: 2011-02-21
forum: Multimedia Software
---

### Post by Roasted on 2011-02-21
I have a Sandisk Sansa Fuze MP3 player. I was trying to work out how to set up playlists so I fired up Rhythmbox. Well, the device acts weird to start off. It won't respond if I have it set up through MSC mode. If I have it set as MTP mode, it won't fly. This began when I formatted the Sansa via the Sandisk "format" option within the MP3 player interface. Okay, whatever. Moving along, I need to use MSC mode for it to work. Well, fine.

I fired it up originally and put all sorts of music on it. Then I added about 100 songs to this playlist. I checked the Sansa and it read the playlist fine. Plug it back in to add a 2nd playlist and I did my thing. I unplug the Sandisk and check it. Of the 80 songs I added to playlsit #2, only TWO showed up. What the? 

So I plug it back in, and Rhythmbox detects the Sandisk player, but it sits at Importing 0/0.

I have the MTP plugin enabled, even though I have to have it on MSC mode for it to work properly in Ubuntu.

Does anybody know what I can do?

---

### Post by Roasted on 2011-02-21
I assume everybody has had flawless results?

---

### Post by Roasted on 2011-02-21
Fixed it. A user in the Ubuntu IRC chat was nice enough to point me in the direction of .local/share/Rhythmbox. I removed that Rhythmbox folder (I guess it's the equivalent of .exaile or .audacious that some other programs have in the home directory) by cutting it and pasting it to my desktop. Once done, Rhythmbox had to COMPLETELY re-vamp my music library, both on the system and on the media player. But that's fine, cause it fixed it. Good to go now!

---

### Post by Roasted on 2011-02-22
New problem. Rhythmbox seems to "forget" some of my music on my Micro SD card within my Sansa. For example, it imported 700 files originally. Eventually I noticed a band was missing. Sure enough, 656 files were imported.

So why is Rhythmbox getting confused so much? It's a little frustrating to see this happening. Besides dumping my Rhythmbox database as described above CONSTANTLY, how can I avoid this problem?

---

