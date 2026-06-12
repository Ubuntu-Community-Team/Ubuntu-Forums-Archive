---
title: "Streaming Media Server"
date: 2009-01-20
forum: Multimedia Software
---

### Post by f37u5g0d on 2009-01-20
I have a large music collection on my server and I have a netbook that I want to stream the music too over my school's wireless LAN.  I have tried simply using rhythmbox's DAAP sharing but for some reason it continually drops the share while I am listening to it.  The share doesn't find it again until I restart rhythmbox.  Is there a good streaming server that I can use to stream my music collection?  They are all .ogg files and I would like to access them via a client app not a browser.  I have heard about gnump3d and I wanted to try that because it can browse my folders but it isn't in the repos anymore?  What gives?  Thanks for any help!

---

### Post by mcduck on 2009-01-21
You could try Edna: [http://edna.sourceforge.net/]("http://edna.sourceforge.net/")

While the site only says it's MP3 streaming server that supports "certain other types of music and video files", OGG should be supported.

---

### Post by f37u5g0d on 2009-01-21
I solved my own problem.  Thanks for your help though!  I firstly made my Music on my server a samba share accessible by guests (although not writeable by anybody).  I then mounted it to a file on the filesystem of my client with smbmount //"server-ip"/"share" /"the directory on my client's filesystem" (without the quotes.  Then I created an entry in my fstab for the samba share to be mounted everytime the computer is booted.  Then i installed exaile music player from the repos and I told it that my collection is located in /"the directory on my client's filesystem" and viola!  I am streaming :)

---

