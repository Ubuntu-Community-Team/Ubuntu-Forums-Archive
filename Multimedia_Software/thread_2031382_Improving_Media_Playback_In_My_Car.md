---
title: "Improving Media Playback In My Car"
date: 2012-07-21
forum: Multimedia Software
---

### Post by Dulleo on 2012-07-21
Hi,

My car allows for an ipod, MTP device, or an external hard drive to be used for media playback.  I decided to go with the external hard drive for $80 bucks, USB 3, and 500 GB rather than using something else.  However, when I plug my hard drive into the car, it only gives me the folder structure I have set up on the hard drive, which is Artist->Album.  The car only plays songs from one folder at a time. This is okay, but I'd like to have more filtering abilities, like by Genre, all songs by an artist, time periods, certain tempos, etc..   My car also supports playlists.  

I've come up with some ideas to make this work. 

1) Copy the songs into multiple places on the hard drive.  This is the 'dumb' approach, but something that I know will work.  I have about 50 GB of Music on a big drive, so I can copy any given song into ten places.  It would be an ugly mess to deal with this way - unless I had a database managing the directory structure.  It only takes FAT format so no symbolic links.  Unless symbolic links can be faked some way.

2) Generate a group of playlists for each category.  I think the limit is something like 200 playlists, internally the car lists these all separately in a group.  A drawback is that this may not be enough playlists, but I wouldn't need one for each album since my directory structure is already setup that way. You also wouldn't be able to filter by other categories within a playlists.  You couldn't have all your rock songs, and then a second playlist within that first playlist with each artist. (At least I don't think so.)

3) Build a little box to read a database from the hard drive, and present it to the car as an ipod, mtp device, or hard drive.  The car thinks it's seeing the directory of a regular hard drive but what it's really seeing is made up on the fly.  

Anyone know which of these is possible, any tools I can use on ubuntu, or have any better ideas?(besides buying an ipod.) Also I'm not sure if this is the exact right category for this question - it's the closest I could find.

---

