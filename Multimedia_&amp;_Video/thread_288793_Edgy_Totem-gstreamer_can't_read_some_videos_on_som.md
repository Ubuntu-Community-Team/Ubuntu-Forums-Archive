---
title: "Edgy: Totem-gstreamer can't read some videos on some partitions"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by ara qui rit on 2006-10-30
Hello everyone

I have just installed Edgy and I'm facing some quite strange problem with Totem-gstreamer. Basically, it doesn't read some videos (in fact it can somehow, but you'll see, it's really wierd).

I think the context have some importance so here it is : Before having Edgy, I had Dapper installed. I didn't want to do upgrade it because I've done some mess on it, so I deleted it and put Edgy in place of it, but I had to keep some data partitions intact so I did the following : 

/dev/sda1, ext3 : / (Edgy)
/dev/sda2, swap (Edgy)
/dev/sda3, ext3 : /home (Edgy)
/dev/sda4, ext3 : data from Dapper : haven't been formatted

/dev/sdb1, ext3 : data from Dapper : haven't been formatted either

/dev/hda1, ntfs : Win 2000
/dev/hda2, fat32 : data

So right after installing Edgy, I get my data partitions back :

# chown -R 1000:1000 /media/sda4
# chown -R 1000:1000 /media/sdb1

... and to be 100% sure I won't have access issues on them : 

# chmod -R 755 /media/sda4
# chmod -R 755 /media/sdb1

So now, I think I do have a total access to theses partitions. But I still have issues with them. When I try to read some videos with Totem-gstreamer (by double-click on the video in Nautilus), Totem gives me an error message "flux error" ). 

I don't think it's a plugin issue because when I copy the video in my /home, Totem reads it! 

Also, I have installed every gstreamer0.10 package I found with the default repositories (plus universe/multiverse). Speaking about that, I should add that I'm using a ALSA sound output and X Window System (NO Xv) video output. 

Ok, I hope I've been clear enought (btw, since English isn't my native language, sorry for the possible spelling / grammar faults).

Anyway. Is somebody can help me ?

---

