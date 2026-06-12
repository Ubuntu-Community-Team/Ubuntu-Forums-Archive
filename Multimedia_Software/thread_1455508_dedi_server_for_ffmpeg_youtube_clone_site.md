---
title: "dedi server for ffmpeg youtube clone site"
date: 2010-04-16
forum: Multimedia Software
---

### Post by lawstudent on 2010-04-16
Hi,

We are building a website which will show movies, pretty much like youtube. We are using  phpmotion (although open to other scripts)

The thing I need to do, build a server for 1 domain with its sole purpose to display movies. There is no need for users to upload their movies in the beginning, it will just be our own content. 

I have an HP 380G4 server, 1TB of space, 4GB of memory. 
The server is currently on my kitchen table, 

Dynamic IP is being managed by no-IP and my domain is pointing to there, all ports forwarded and working.

OK question time

1) how to setup Ubuntu specifically for my (VIDEO) needs
2) do I use /var/www for the website? (my paid servers I use /home/username
3) I have something "lilo" lights out is it worth the trouble to use it?
4) How can I secure my server
5) I formatted my drives as RAID10 is that the best option?

I guess these are all different topics on their own, but I was hoping someone could talk me through the basics, this is the first time I use my own server (although I use servers in datacenters, I never set them up though)

---

### Post by FakeOutdoorsman on 2010-04-18
> **lawstudent said:**
> OK question time

1) how to setup Ubuntu specifically for my (VIDEO) needs
I currently use a LAMP system to show videos.  My workflow will probably be different than yours because we only show our own content and nothing user submitted.  I convert videos to H.264/AAC MP4 with FFmpeg or x264 on my workstation and then upload to the dedicated server.

We use a mySQL database to deal with the movie information (title, screen shot, description, file location, etc) and then use a custom Flash player to show the movies to the site visitors.  I am currently in the process of dumping the custom player and using JW Player because it isn't too expensive for commercial use (free for personal use). It has more features and works better than our custom player.  You can also try Flowplayer.

Before you start, I recommend reading the [Ubuntu Server Guide](https://help.ubuntu.com/9.10/serverguide/C/index.html).

I recommend paying for hosting if this will be a business critical site.  With a good hosting provider you'll get a fast connection, redundant power systems, and a controlled environment.  If you're on a budget check out this thread: [Ubuntu 9.10 OpenVZ VPS - Starting at $5/month](http://ubuntuforums.org/showthread.php?t=1128094) (this is an offer by the Ubuntu Forums admin.  I'm not affiliated with it and I've never used it but it might be worth looking into).  If it is a personal or hobby project then self-hosting can be fun and a good learning experience.

> **lawstudent said:**
> 2) do I use /var/www for the website? (my paid servers I use /home/username
You can use whatever you want.

> **lawstudent said:**
> 3) I have something "lilo" lights out is it worth the trouble to use it?
I don't know what you're referring to.

> **lawstudent said:**
> 4) How can I secure my server
My favorite resource on this topic is the [Securing Debian Manual](http://www.debian.org/doc/manuals/securing-debian-howto/).

> **lawstudent said:**
> 5) I formatted my drives as RAID10 is that the best option?
I'm not sure.  I don't have any RAID10 experience.  However, if this project is important to you, then *always have a backup*.  RAID doesn't count as a backup.  My server uses [duplicity](http://duplicity.nongnu.org/) for daily incremental and encrypted file and database backups to an offsite third-party "cloud" storage system (Rackspace Cloudfiles) and it has saved me a couple of times (and it's cheap).  You could try [rdiff-backup](http://www.nongnu.org/rdiff-backup/) if you are making backups to a local machine or storage device and don't need encryption to reduce complexity.  Both of these are in the Ubuntu repository.

---

