---
title: "Getting MP3's onto Sony NWZ-A729"
date: 2009-01-07
forum: Multimedia Software
---

### Post by chazdraves on 2009-01-07
Greetings, all!

I'm afraid I'm having a bit of an issue. After all this reading on this particular model, I finally decided to break down and get one, only to find I've run into a real mess.

For some reason, I thought it supported .ogg, and it doesn't. I wasted a whole hour transferring my entire library onto it only to find none of them play.

With that in mind, I've been re-ripping my CD collection (90+ CDs one at a time) into MP3 format. I just tried copying over the first two albums only to find that album artwork does not work (though it comes up in Rhythmbox), and none of the Genre,Album,Artist information is recognized either... it all says "Unknown Artist, Unknown Album" and groups them all together even though they're in separate labeled files... I never had this issue with my Sansa, that was just drag-and-drop...

Anyone have any ideas?

Thanks, all!
- Chaz

---

### Post by chazdraves on 2009-01-07
Okay, I'll answer one part of my own question, hopefully somebody can help me with the second part as well..

If you go under plugins in Rhythmbox there's one listed for MTP player support. Enabling that will force the Sony (somehow) into MTP mode. From here you can Ctrl+A your entire music library and drag it to the MP3 player in the side pane and Rhythmbox will transfer all the music with artist/album/year information intact, though it seems to lack Genre, which is still fine.

Now the final question... how do I get album art on there as well?

Thanks, all! Hopefully the above helps someone else with this...

- Chaz

---

### Post by robhem on 2009-10-12
Chaz, 

I wonder if you needed to do anything special to get your Sony NWZ-A729 to work in Jaunty? I have the same model and it mounts as a removable drive. But, I can not browse its contents at all. I have the MTP plugin for Rhythmbox. 

Regards, 
Rob

---

### Post by vinutux on 2009-10-13
checkout songbird it support automatic album fetcher and tag editing .....

---

### Post by fleasbaby on 2009-12-06
> **chazdraves said:**
> Okay, I'll answer one part of my own question, hopefully somebody can help me with the second part as well..

If you go under plugins in Rhythmbox there's one listed for MTP player support. Enabling that will force the Sony (somehow) into MTP mode. From here you can Ctrl+A your entire music library and drag it to the MP3 player in the side pane and Rhythmbox will transfer all the music with artist/album/year information intact, though it seems to lack Genre, which is still fine.

Now the final question... how do I get album art on there as well?

Thanks, all! Hopefully the above helps someone else with this...

- Chaz

From what I have seen you need to actually tag the mp3's to get the album art to show (sucks, I know). I still haven't gotten mine to work in Jaunty though...anyone else figured this out yet?

---

### Post by fleasbaby on 2009-12-06
> **robhem said:**
> Chaz, 

I wonder if you needed to do anything special to get your Sony NWZ-A729 to work in Jaunty? I have the same model and it mounts as a removable drive. But, I can not browse its contents at all. I have the MTP plugin for Rhythmbox. 

Regards, 
Rob

Hmmm...okay, not sure why, but a solution (I forget where I saw it on here) that didn't work for me before magically worked now....I opened the player after it had mounted, created a folder (didn't name it anything, just left it unnamed) and in it all of the files added onto the player under Windows were there.

The trick is, now when I try to play the files there are none under the folder on the player...

---

### Post by fleasbaby on 2009-12-06
Okay, so, I gave up on the "create a folder" method and tried another I found bumbling around on the inter-web...

1. Plug in the player.
2. Start up the System Monitor (in Jaunty go "System", "System Administrator" and "System Monitor").
3. Stop the process tagged "gvsf-photo-something or other" (sorry, forgot what the precise name was...)
4. Plug the player in again.

You should then be able to add files.

---

