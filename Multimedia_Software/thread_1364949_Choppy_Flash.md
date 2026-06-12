---
title: "Choppy Flash"
date: 2009-12-26
forum: Multimedia Software
---

### Post by Holograph on 2009-12-26
Hello all!

Windows crashed for the 3th time this week, so I decided to install Ubuntu, after that I patched it to Kubuntu. I also installed Adobe Flash 10 (what wasn't very easy) but after 30 minutes the install had succeed. So the first thing I did was going to youtube to test if I was still able to watch HD movies properly (I was able to do that on Windows). But it was awfull (in fullscreen), the frames were choppy, but when I went back in 'minimized' youtube I was able to see it without lagg. So I went searching, but I didn't make it. It was still choppy as hell. So now I am here: how can I 'repair' the choppy flash files? I'm using Ubuntu x64

System specs:
Intel Core 2 Duo 3.1 GHz (6MB L2)
ATI Radeon HD4670
4GB Ram

I hope anyone can help me out :)

Regards,

---

### Post by HappyFeet on 2009-12-26
First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

---

