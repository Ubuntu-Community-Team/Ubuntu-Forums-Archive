---
title: "MPD crashing due to corrupted file"
date: 2011-04-19
forum: Multimedia Software
---

### Post by iconoclast hero on 2011-04-19
I saw [this]("http://ubuntuforums.org/showthread.php?t=1666781&highlight=mpd+crashing+song"), it isn't the problem, I didn't install mpd until last month.

Yesterday, I downloaded and compiled rubyripper and it was working fine so far as I know.  I ripped a couple of CDs and moved them down to my mpd music server.  It kept crashing at 3:37 on the same song.  I basically had to ssh into the server, and kill the process.  ```
sudo /etc/init.d/mpd restart 
``` would show that it the service was stopped, but then when it went to restart, it said port 6600 was still in use and could not restart.  I was had to find the process and kill it.  

I tried to bring the file back to the desktop to try and play it here and it was a corrupted file.  According to rubyripper, it checked out twice, so it might be a bad sector or it  might be an error transferring over to the server...

Just in case anyone goes looking, that would be something to check.

---

