---
title: "Jellyfin on Ubuntu Server"
date: 2021-12-17
forum: Multimedia Software
---

### Post by mark-rehorst on 2021-12-17
I'm building a Jellyfin server (Plex sucks!) with a Dell Optiplex 3020M that has quad core i5, 4 GB of RAM, and a 4 TB HDD. I have installed ubuntu server 20.04.3 LTS and jellyfin. I created two media folders- one for movies and one for TV in my home folder. I transferred about 60GB of video to the Movie and TV folders with no problems, but additional file transfers to those folders start failing. It's as if I'm running into folder size limits or disc space limit, but when I installed ubuntu server I used the entire HDD and it was formatted ext4 which I don't think should have any limits, at least, not at around 60GB. What am I doing wrong? File sizes are typically 4-5 GB. Should I be putting the video files somewhere else?

I am transferring video files to the server using sftp via filezilla on a windows PC. When the file transfers fail, filezilla doesn't tell me why, it just stops and says transfer failed.

---

### Post by mark-rehorst on 2021-12-18
I believe I got it figured out- the home folder had only about 100GB allocated when I installed ubuntu server.  I reinstalled and allocated the 3.540T of storage which then got mounted in the /home folder.  Thanks!

---

