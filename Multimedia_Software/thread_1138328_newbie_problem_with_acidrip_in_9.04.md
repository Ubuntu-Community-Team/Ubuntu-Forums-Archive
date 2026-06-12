---
title: "newbie problem with acidrip in 9.04"
date: 2009-04-26
forum: Multimedia Software
---

### Post by tommyjw on 2009-04-26
I'm new to linux so some of the folder structures and mounting concepts are new to me.  

I'm trying to use acidrip in 9.04 and when using the default video source path of /dev/dvd,  I get error "Can't read DVD track" when I hit Load.  Tried another disc, same problem.   I right clicked on the DVD mount on my desktop and enter what its properties indicated was the mount location of /media/cdrom0, "No valid file found".  Added VIDEO_TS to the end and it only finds the VIDEO_TS.VOB file.  Looked at other posts for similar problems and in my filename, replace my %T with "mydvd" according to another post, still no luck.

A google search found something from 2 years ago and indicated this problem was fixed with an upgrade.  I'm working with the version I found on Add/Remove Manager which is 0.14.

Any help would be appreciated.

---

### Post by EndersJ on 2010-01-29
> I'm new to linux so some of the folder structures and mounting concepts are new to me. 

I'm trying to use acidrip in 9.04 and when using the default video source path of /dev/dvd, I get error "Can't read DVD track" when I hit Load. Tried another disc, same problem. I right clicked on the DVD mount on my desktop and enter what its properties indicated was the mount location of /media/cdrom0, "No valid file found". Added VIDEO_TS to the end and it only finds the VIDEO_TS.VOB file. Looked at other posts for similar problems and in my filename, replace my %T with "mydvd" according to another post, still no luck.

A google search found something from 2 years ago and indicated this problem was fixed with an upgrade. I'm working with the version I found on Add/Remove Manager which is 0.14.

Any help would be appreciated.

So being new to linux, i ran into this problem as well. Acidrip defaults to /dev/dvd which is not necessarily what your DVD drive is termed. I was unable to find what my DVD was really called and thought for a while that "/media/cdrom0" was the path since that was what appeared at the top of the nautilus window. But this is not the case. I grabbed 'device manager' from the package manager and found my DVD drive through it and learned that its true path was actually  

```
/dev/sr0
```

which seems completely non-intuitive but who am i to say. You can also link your DVD drive to another path using the "ln" command. So that way when Acidrip opens you and reads "/dev/dvd" it will actually re-route to "/dev/sr0" and you dont have to manually enter it in every time. Hope this helps as this confused me at first as well.

---

### Post by amsterdamharu on 2010-04-30
I had a problem with this as well, first made the /dev/dvd link so it'll pick it up:

[sudo]
sudo ln -s /dev/sr0 /dev/dvd
[/sudo]

It keeps giving me the same grief though, then followed some other tip and use the mount point for it which is mounted at: /media/ME_KIO_blablabla and get an error: "no valid files found"

Installed restricted extras but that just removed libavcodec-unstripped-52 and that will crap all over ffmpeg not supporting mp3 anymore (since that was the fix I used to make that work).

Finally I went to nautilus and unmounted the dvd then started acidrip and let it read /dev/dvd and everything is ok. Not sure what was going on there but it's working fine now.

---

### Post by mamakubwa on 2010-06-09
[HTML]'device manager'[/HTML]

where is the application device manager? sounds dreamy. yes this is really amazing. we are on Ubu 10 and you can rip mix make move copy music 1000000 ways, you can see exactly where the music is.. but if you right click on it does it show you the path? of course not! why would anyone want a quick lookup of the path! 

come on guys, really.

---

### Post by embain14 on 2011-05-15
> **EndersJ said:**
> So being new to linux, i ran into this problem as well. Acidrip defaults to /dev/dvd which is not necessarily what your DVD drive is termed. I was unable to find what my DVD was really called and thought for a while that "/media/cdrom0" was the path since that was what appeared at the top of the nautilus window. But this is not the case. I grabbed 'device manager' from the package manager and found my DVD drive through it and learned that its true path was actually  

```
/dev/sr0
```which seems completely non-intuitive but who am i to say. You can also link your DVD drive to another path using the "ln" command. So that way when Acidrip opens you and reads "/dev/dvd" it will actually re-route to "/dev/sr0" and you dont have to manually enter it in every time. Hope this helps as this confused me at first as well.

Thank you that was very helpful!!

---

