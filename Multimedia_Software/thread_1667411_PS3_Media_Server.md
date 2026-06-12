---
title: "PS3 Media Server"
date: 2011-01-14
forum: Multimedia Software
---

### Post by alohanate on 2011-01-14
How do I set up a PS3 Media Server?  I've been trying all day.  Thanks!

---

### Post by HankB on 2011-01-14
> **alohanate said:**
> How do I set up a PS3 Media Server?  I've been trying all day.  Thanks!

Are you talking about "PS3 Media Server" as in the one described at [http://ps3mediaserver.blogspot.com/?](http://ps3mediaserver.blogspot.com/?) I have no knowledge, but I suggest you post additional information like what you've tried and what didn't seem to work.

At the moment, I'm watching a copy of Shrek ripped form my DVD via Media Tomb. Start with:
```
sudo apt-get install mediatomb
```

I also needed to make an entry in /etc/mediatomb/config.xml to get .m4v files to work. (I think.) ([http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html](http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html))

hank

---

### Post by alohanate on 2011-01-14
Hank,

So I scrapped my attempt at installing the PS3 server that you provided a link for (I was unable to execute PMS.sh, when I attempt to open it, nothing happens) and installed MediaTomb but when I attempt to use it, it sends me to a page on my browser that reads, 
**"MediaTomb UI is disabled. Check your configuration."**


How do I configure MediaTomb?

---

### Post by alohanate on 2011-01-14
How do I give mediatomb permission to access my Music and Video folder?

---

### Post by HankB on 2011-01-14
The Mediatomb web site is at [http://mediatomb.cc/](http://mediatomb.cc/)

The configuration file is in [FONT="Courier New"]/etc/mediatomb/config.xml[/FONT]. You can edit it with ```
sudo gedit /etc/mediatomb/config.xml
```

Look for:
```
    <**ui enabled**="yes" show-tooltips="yes">
```
and if it says 'no' change it to yes.

I'm not sure what you mean about permission to access your music and video files. Is it a file permission problem? 

-hank

---

### Post by alohanate on 2011-01-15
So I figured out how to configure mediatomb, so that's good.

But I can't seem to access my music or video folder. This is the error I get:

**"Error: could not list directory /home/samwise : Permission denied"**

---

### Post by HankB on 2011-01-15
That sounds like a file permission problem. The best I can think to solve that is to make the necessary files readable by the group 'mediatomb'. When you install mediatomb, it creates both a user and group named 'mediatomb'.

One way to do this is to add the user 'mediatomb' user to the group with your login name. In [FONT="Courier New"]/etc/group[/FONT] you will find an entry that *starts* with your login name. Mine looks like:
```
hbarta@toonsinator:~$ grep ^hbarta /etc/group
hbarta:x:1000:
hbarta@toonsinator:~$
``` 

You want to (make a backup copy and) edit that with:
```
sudo cp /etc/group /etc/group.bak
sudo gedit /etc/group
``` and add 'mediatomb' to the end of your group entry 'mediatomb' so it looks like:
```
hbarta@toonsinator:~$ grep ^hbarta /etc/group
hbarta:x:1000:mediatomb
hbarta@toonsinator:~$
``` (substitute your user name, of course!)

I think you will need to restart mediatomb for it to gain your group permissions:
```
sudo /etc/init.d/mediatomb restart
```

That may be sufficient if your files are group readable. 

If this doesn't work, please post the output of:
```
ls -ld ~/
ls -lR /path/to/my/music/or/video
``` (For the second command, please post only enough to show some representative files. We don't need to see your entire music and video collection. ;) )

My installation is ancient and my home directory dates back to a previous age. And in any case, I store music, videos pictures and so on stored outside of my home directory and have explicitly made them world readable and writable to share with other members of our household. My description above assumes that you have music and videos in your home directory. Maybe this is time to reconsider that as keeping stuff like that separate makes managing file permissions without compromising security easier. A better solution (w/out making your home directory any more open) is just move all music and video files outside your directory and make that world readable. (Might be a good time to google "unix file permissions" to learn a little more about that.

HTH,
hank

---

