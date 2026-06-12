---
title: "is it possible to make an mp3 audio server?"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by Stochastic on 2007-01-15
Hi, I'm just curious if anyone knows a way of setting up my Ubuntu Dapper Server so that I can play the mp3s on it, out of its soundcard from any computer in the house (an Ubuntu laptop and a Windows XP laptop)?
It's currently setup with a PHP and Apache web server - I'm thinking the easiest way would be to look into a web interface? (just a thought, any other ideas/advice?)

---

### Post by NeoLithium on 2007-01-15
I think that [http://www.ubuntuguide.org](http://www.ubuntuguide.org) had a walkthrough for that.

---

### Post by Stochastic on 2007-01-15
which section is that?  I'm not sure what type of service I need to run, I'm relatively new to ubuntu.

---

### Post by NeoLithium on 2007-01-15
Well, there's the streaming info:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Streaming_Media_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Streaming_Media_Server)

There was another mysql way I think; but I'm not familiar with that...

---

### Post by Stochastic on 2007-01-15
But a streaming server will play the music on the user's soundcard not the server's soundcard.  Won't it?  Or can you configure GNUMP3d to play music on the server?

---

### Post by NeoLithium on 2007-01-15
The streaming should work over the server, I would imagine, because it also would go over the internet....

---

### Post by Stochastic on 2007-01-15
just to be clear:

-mp3 files exist on my server's harddrive
-I can play them through my server's soundcard through a web control on my laptop's windows machine if my server installs GNUMP3d?

---

### Post by NeoLithium on 2007-01-15
If your server installs the streaming server, you can just use any media player from the other laptop to connect to the streaming address you set up for your server, and it'll recieve the playlist you set.

I guess you can think of it as your own small-scale shoutcast.

---

### Post by Stochastic on 2007-01-15
I thought you played shoutcast's through your laptops soundcard? from your laptop's media player accessing a shoutcast from files on the servers computer?  I don't want to do that.  I want to play the files out my server's soundcard.

---

### Post by Stochastic on 2007-01-16
So just to let you know, this: [http://kde-apps.org/content/show.php?content=23630](http://kde-apps.org/content/show.php?content=23630) is how I solved my problem.  It was the easiest solution with the least configuration needed and works across Windows and Ubuntu because it's a firefox extension.

---

### Post by ianmac on 2007-01-16
> **Stochastic said:**
> So just to let you know, this: [http://kde-apps.org/content/show.php?content=23630](http://kde-apps.org/content/show.php?content=23630) is how I solved my problem.  It was the easiest solution with the least configuration needed and works across Windows and Ubuntu because it's a firefox extension.

You could also check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Playing_Server_.28MPD.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Playing_Server_.28MPD.29)

Seems to be closer to what you want to do...  as an alternative solution.

Ian

---

### Post by Stochastic on 2007-01-17
Hmm, but can this easily interact with a windows client machine?  I need it to work from both a windows xp machine and an ubuntu dapper machine.  The Amarok-Firefox app is nice because it's requirements are very minimal.  Though it is a little on the buggy side.

---

### Post by Stochastic on 2007-01-17
just to try the MPD method out I went through the installation steps but when I got to the ```
/etc/init.d/mpd restart
``` I was greeted with the following error: ```
Stopping Music Player Daemon: not running or no pid_file set.
Starting Music Player Daemon: Error reading db, fgets
failed.
```
Also I'm running Dapper not Edgy, is this where the error is coming from?

---

### Post by Antonlacon on 2007-01-18
[http://ubuntuforums.org/showthread.php?t=320469](http://ubuntuforums.org/showthread.php?t=320469)

MPD howto.

---

