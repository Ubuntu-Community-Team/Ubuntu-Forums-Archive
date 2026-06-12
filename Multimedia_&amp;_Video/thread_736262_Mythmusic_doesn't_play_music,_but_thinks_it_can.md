---
title: "Mythmusic doesn't play music, but thinks it can"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by aseriesoftubes on 2008-03-26
Hi,

I am running Mythbuntu 7.10 with a dedicated backend server and a separate frontend machine. All of my media--recordings, music, videos--is stored on the backend and shared via NFS. Recordings and videos both play as expected, but I'm having trouble playing music on the frontend. 

If I quit mythfrontend and navigate to the mount point for my music, all of my music files appear correctly, and I can play them in my media player of choice just fine, so I know that the share is set up correctly. But when I attempt to play those same files through MythMusic, I get nothing. The Scan for New Music tool detects all of the files, but when I play an album or playlist, nothing happens. No sound, no visualizations, nothing. 

Here's the really weird part: MythMusic *thinks *it's playing something, because when I exit out of MythMusic, it gives me the "Do you want to keep playing the music or stop it?" dialog.

I've double-, triple- and quadruple-checked the path of the music folder in Music Settings, and have confirmed that all of my sound output settings are correct, which they are (I'm running SPDIF out to an AV receiver BTW). I'm stumped. Any ideas out there? Thanks!

Brent

---

### Post by aseriesoftubes on 2008-03-27
Gah, I figured it out. Turns out it *was *a configuration issue. I had to change the audio output setting for MythMusic from 'default' to 'ALSA:default'. Everything works perfectly now.

---

