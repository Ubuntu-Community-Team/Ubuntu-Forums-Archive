---
title: "Did Rhythembox screw up your iphone/ipod touch?"
date: 2010-12-25
forum: Multimedia Software
---

### Post by superyounan1 on 2010-12-25
I'm getting some strange behavior from my iPod touch, and I think it is related to the fact that I tried out the new Rythembox compatibly. Let me know if you've had this happen to you, and if you found a solution.

I tend to buy music on my iPod touch directly, then synchronize it with iTunes later. 

After goofing around with Rythembox by trying (unsuccessfully) to import some mp3s onto my iPod, I noticed that my recently purchased 'Fame Monster' Lady Gaga album would not synchronize with iTunes, although the music was still playable and indexed correctly on the ipod itself. I also noticed that Rhythembox can't seem to find that album either. It is quite strange.

So I browsed around the file structure on the ipod to try to hunt down these m4a files and found them in a folder called 'Purchases' - they were all there along with a few other recent purchases. These m4a files are different though - they don't seem to have any of the audio tracks' meta-data embedded in the files themselves, that info is instead in associated 'plist' files that are just xml files with all the info about the tracks you'd expect.

When you sync an ipod touch with itunes, it copies your 'on-the-go' generated playlists - so I tried to trick itunes into finding these files by adding my gaga album to a playlist, but sure enough after synching, that playlist simply disappeared. I tried it again, but this time also adding other songs that are not having any problems, and sure enough the playlist was successfully copied to itunes... SANS any of the gaga tracks! This is so weird.

So basically I have these tracks that are paid for, not cheap might I add, that are playable on my ipod touch, but simply refuse to synchronize with itunes. Why not just grab it m4a off the ipod directly? Well thats true, they play on my computer just fine that way, but the files don't have any of the album and track information embedded...

What the hell is all this? Has it happened to you? Do you know how to fix it?

---

### Post by superyounan1 on 2010-12-31
Well maybe this thread will help someone. I don't know how the problem started but I suspect it was after trying to use Rhythembox to manage my Ipod's music library. 

I tried updating my iPod touch's OS and iTunes to the latest editions, but this still didin't give me access to the music recently purchased on the iPod directly. Prior to the updates though I took the liberty to back up the music m4a files, used an amazing tool called 'musicbrainz picard' to automatically populate the ID3 tag data, and import the music from scratch into itunes.

If you have this problem, this is probably the best solution. Also it might be wise to avoid jailbreaking the thing, this might have helps screw things up.

---

