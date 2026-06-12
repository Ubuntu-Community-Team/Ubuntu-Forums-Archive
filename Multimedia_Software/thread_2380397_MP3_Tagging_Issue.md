---
title: "MP3 Tagging Issue"
date: 2017-12-16
forum: Multimedia Software
---

### Post by Neil_Sherin on 2017-12-16
Hi,

I am having issues with MP3 tags that are driving me to the point of crazy in Linux.

I have a large - around 217,000 track MP3 library. All stored on a Windows 2012R2 server.

Taking one album as an example in Windows - Explorer shows all the tags as there, as does MP3tag. i've run MP3 Diags to remove any other anomalies.

Opening a track in VLC under Windows shows the track with the correct track data if I go into the media information.

Importing said album - along with a number of others into Banshee under Linux simply shows Unknown Artist/Album.

As a test, I even copied my test album onto the drive of the Ubuntu VM as mentioned above that shows up fine under Windows Explorer/VLC with meta data. When I open a track off that album, VLC does not show any ID3 tag data - nor does Banshee. This is despite the same files in Windows showing the tags.

Any help would be much appreciated - I cannot understand at all what is going on here as to why the exact same files should differ on Windows versus Linux.

---

### Post by Yellow Pasque on 2017-12-17
Try this first to see if tags show up in Banshee.
```
sudo apt-get install gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad
```

---

### Post by Neil_Sherin on 2017-12-17
Hi Temüjin. Thanks for your reply. Both of those plugins are already installed on the Ubuntu machine. I have also checked that ubuntu-restricted-extras is installed - which it is.

---

### Post by Neil_Sherin on 2017-12-18
I've checked all of the files using MP3Tag on Windows - they all have an Artist entry in their tags. Album Artist is blank - to remove that confusion, plus i do not wish to use Album Artist. Having left Banshee to import the library overnight again there are still thousands - as in between 5 and 6 thousand files with unknown artist/albums and track names that include the track numbers. This makes no sense, considering they look absolutely fine in MP3Tag!

---

### Post by Yellow Pasque on 2017-12-18
kid3-qt is a friendly GUI. I'm guessing it's equivalent to MP3Tag. Start there.
mp3val is a lower level CLI utlity used to check mp3 integrity.

---

### Post by Neil_Sherin on 2017-12-19
I've since tried the import using Rhythmbox on Ubuntu 17.10 - it worked perfectly - all files imported without issue, whereas even when I tried Rhythmbox on 16.04, I had the Unknown Artist/Album issue. Banshee on 17.10 quits after you browse to the folder to import but that seems to be a known bug.

---

### Post by jee.smith on 2017-12-19
kid3-qt is probably the best solution

---

### Post by Neil_Sherin on 2018-01-04
A further update and good progress made. I removed the 'Album artist' tag from all of the tracks in iTunes. All tracks are now imported perfectly in Rhythmbox tested on:

Ubuntu MATE 16.04
Ubuntu MATE 16.10
Ubuntu MATE 17.04
Ubuntu MATE 17.10
Xubuntu 16.04

So it seemed to be issues with the 'Album Artist' tag that were causing the problems. Thanks for all tips provided though!

---

