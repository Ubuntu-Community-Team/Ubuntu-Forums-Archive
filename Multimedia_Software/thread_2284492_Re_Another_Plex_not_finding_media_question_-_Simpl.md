---
title: "Re: Another Plex not finding media question - Simple setup."
date: 2015-06-29
forum: Multimedia Software
---

### Post by 77_GCSX on 2015-06-29
I recently acquired a slightly older PC that I am trying to use as a media server. I have a fresh Ubuntu 14.04 LTS install with no other modifications to it except for installing Plex.

Now, my problem is this: I have the same set up on my home PC, same version of Plex but using Ubuntu 14.04 LTS 64 bit. 

I moved 3 movies from my home PC to the new PC. Plex found them and I can watch them on 2 different DVD players. I went ahead and moved another movie, Jaws, from the home PC to the newer PC but for the life of me Plex will not acknowledge that there is a new movie there, same folder as the other 3.

I did nothing to Jaws except for copying it from my home PC to a USB stick, then from the stick to the new PC. The naming scheme stayed the same so it should have been seen and updated, but it wasn't.

I have seen a few posts about using the gpasswd command and I have tried these (with reboots) with no luck.

So, what did I do wrong?

On the home PC I did follow a "10 things to install" tip for Ubuntu which I believe included some codecs. But why will only 3 out of the 22+ movies I have total be acknowledged.

Any help is GREATLY appreciated. If anyone responding needs more info just ask.

Thanks, Paul

NEVER MIND.....I had a DUH! moment. I figured it out. The permissions of each movie file I moved were set to read = No.

My Bad!!

---

### Post by TheFu on 2015-06-29
A home network only needs 1 Plex Server - any other devices can see the Plex server and stream over wifi or wired ethernet or power-line ethernet. No need to physically move files around. Use the network. If the main PC has enough CPU, it can transcode the videos on-the-fly based on profiles for each device.  Every DLNA client I've used has worked.  Roku has a Plex client, smart TVs, BluRay players, and PCs running Kodi/XBMC can all access media from a Plex Server - that's video, movies, tv, music, photos.

Plex uses ffmpeg or avconv to transcode, so whatever codecs those support are supported. At least that's how I think it works.  Each client has a profile that clearly says which codec it supports - so the plex server will transcode into that format on-the-fly. This transcoding will also modify the resolution and quality (bitrate), if necessary. The clients don't need to have any special codecs loaded - all the transcoding happens on the server.

For the last 4 yrs, I've been very careful to only have mkv/h.264/ac3/DTS/DD or AAC media. Makes life easy. Older formats like mp4/xvid are trivially transcoded for the client requirements.

Don't know if any of this will be helpful or not. Hope it is.

---

### Post by 77_GCSX on 2015-06-29
Don't worry about being confused. I live it everyday! lol!

My end product of all this moving of files around was to have 1 dedicated Plex server.

Anyways, I did figure out what the problem was - Each of the movies needed their permissions changed. I did this and now all is good.

Thanks!
Paul

---

