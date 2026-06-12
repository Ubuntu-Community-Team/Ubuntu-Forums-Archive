---
title: "Media/Bittorrent Server Help!!!"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by jbillzz on 2007-12-27
So I might be in a little over my head here.

I got my grandma's old 733mhz celeron 64 mb ram computer, and I wanna turn it into a headless music/video/bittorrent server.

Basically, I'm looking to be able to start bittorrents on it remotely, play music off it at home, and ideally, access its contents over the interwebs.

I just installed ubuntu server, which is command line only thus far, and have successfully accessed it over my router w/ putty.

Now i don't know what to do to make this happen. 

I have no experience w/ ubuntu/linux/commandline only os, I don't know if I should install the gui on such a low memory cpu, how any of this stuff might work...

---

### Post by icheyne on 2007-12-27
Don't bother with installing X - it'll be too slow.

Read any of the hundreds of introductions to the command line. You won't regret it.
Check out these excellent [command line programs.]("http://users.skynet.be/six/gpure/tech/linux/apps.html")
sudo aptitude install cplay
sudo aptitude install rtorrent

Also check out:
[http://edtechdev.blogspot.com/2007/11/quickly-setting-up-and-securing-ubuntu.html](http://edtechdev.blogspot.com/2007/11/quickly-setting-up-and-securing-ubuntu.html)

---

