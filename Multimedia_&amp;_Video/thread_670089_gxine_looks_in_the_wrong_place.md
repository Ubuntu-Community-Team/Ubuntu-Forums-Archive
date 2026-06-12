---
title: "gxine looks in the wrong place"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by dsimpson on 2008-01-17
I have tried to resolve my cdrw and dvd player issues but with no luck. I am trying through another route. When I try to open my dvd player, it looks for the dvd under  /dev/dvd and according to my computer it gives the logical name as /dev/hdd and the media as cdrom1. How can I go about changing the location that gxine looks for the dvd to fit the location that is given for the drive. I know this sounds confusing but I just don't know how to word it otherwise. I would appreciate any help possible.:confused:

---

### Post by cor2y on 2008-01-17
you can always set gxine as the default dvd movie player if its not set as it.That way anytime you insert a dvd movie gxine will automatically launch.
To do this go to System->Preferences->Removable Drives and Media
Then the multimedia tab and the Video Dvd section and replace whatever is in there with gxine (leave the %m don't remove that) next click close and test it out .
Insert your dvd movie and see if gxine launches and plays it.
On the other hand for in depth config in gxine go to preferences
File->Configure->Preferences
Then to the media tab then the dvd tab and checkout device.
It should correctly point to dvd if it doesn't change it to that (just click and select dvd from the list in dev that pops up) close out and that should do it.

---

### Post by dsimpson on 2008-01-19
I was able to re-configure the setting for my dvd but still nothing. here is the message that appears when it fails. 


The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

Read error from:/dev/cdrom1

---

### Post by RomeReactor on 2008-01-19
Hi. It looks like gXine is trying to read the drive's contents. Does this drive read other DVDs correctly, such as data DVDs? Do you have the necessary libraries to play the DVD?

---

### Post by dsimpson on 2008-01-19
What do you mean by "libraries"? I have installed all the codecs, to play the dvd's but cannot even open the player to play anything. I can play audio files, on cd, both recorded and commercial but no video files are read. I tried to read a dvd with photo's on it and it wasn't detected, so it only will access and play audio.

---

### Post by RomeReactor on 2008-01-19
How old is the drive? does it read other DVDs (containing pictures, text, sound files), or does it only read CDs? By 'libraries' I meant the packages needed to play DVDs:
```
sudo aptitude install libxine1-gnome libxine1-plugins libxine1-ffmpeg libdvdnav4 libdvdread3 libdvdplay0
```
If you have the Medibuntu repository enabled also install:
```
sudo aptitude install libdvdcss2
```
If not, then run the following:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by dsimpson on 2008-01-19
As for the libraries' yes all those are installed and are the latest versions. 
As to the age, the computer is about 8 years old, and it worked good prior to installing Gutsy, previously I had Dapper installed and did a complete install of Gutsy and now my dvd and cdrw both will not access data. I don't know what happened?

---

### Post by RomeReactor on 2008-01-19
If the drive is a couple of years old or more, or as old as the PC, then it would probably be hardware failure; have you tried booting a Live CD to see if it works with it? Have you tried cleaning it?

---

### Post by dsimpson on 2008-01-19
RomeReactor,
Ok, I could understand the age factor, but why would it work with audio and not any video? I haven't tried cleaning yet, could give that a try. Also I am having the exact same issue with my cdrw as is affecting my dvd player, how can that happen? I was trying to open a LinuxMint .iso with CD?DVD Creator and it couldn't find the drive. This is driving me crazy, I was able to install Gutsy and open the .iso for it fine just a few weeks ago. I live in the country so it will be a few days before I can get a can of cleaner to blow out the drive to see if that will fix the problem or improve it. Thank you for answering my post.

---

### Post by dsimpson on 2008-01-22
Ok, update!

I can put in a blank cd and the disc is recognized, but when I try to write to it then it isn't found. As I said earlier when I put in an audio cd it works, on both dvd and cdrw, but data files won't, on my dvd or cdrw it will make the icon under places/computer disappear, and only with rebooting can I get them back. 

Now the really weird thing is, I tried my wife' computer and I get exactly the same thing as far as not being able to write to the disc from the .iso image. Everything else on hers works, it will open the data cd's, play music etc. So, I was thinking that something might be wrong with the .iso image that keeps it from writing to disc. Any thought on that? The other thought was that it was too large to fit on the cd, it has 688.7 mb of data, and the cd is naturally 700 mb but with the file system for CD/DVD Creator plus the 688.7 mb it might exceed the capacity of the cd. That is the only reason that I can think of as to why it won't write on either computer. I would like anyone who has any ideas to help please. Not that its important, but the .iso image that i am trying to write to disc is LinuxMint, which is an Ubuntu derivitive so I don't know why it isn't working, since I did a fresh install of Gutsy.

---

