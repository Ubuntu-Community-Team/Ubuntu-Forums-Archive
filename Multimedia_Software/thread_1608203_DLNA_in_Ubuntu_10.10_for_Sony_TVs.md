---
title: "DLNA in Ubuntu 10.10 for Sony TVs"
date: 2010-10-28
forum: Multimedia Software
---

### Post by mikehicks on 2010-10-28
Hi.
I've seen a lot of threads about DLNA and how to get it working with Samsung TVs, but I have a Sony net-enabled TV. Having tried many different DLNA servers I've finally found one that works.

I know how frustrating an experience this has been for me so Im posting this for anyone who has a Sony net-enabled TV and wants to stream their music, video or pictures from their Ubuntu machine.

Im running Ubuntu 10.10.
The only DLNA server that seems to work with a Sony TV in my experience is "miniDLNA".
It doesnt seem to be in the Ubuntu repositories.
I had to Google for it and download the tar GZ from sourceforge.

Its so simple its untrue.
I accidentally unpacked the tar GZ into my Downloads folder so I had to manually "mv" the bits into /usr/sbin and /etc.

I edited the minidlna.conf file in /etc to point at my music,video and jpeg folders.
Then I ran this simple command at the Ubuntu command prompt: "minidlna".
Yes thats it, thats all I had to do.

Went to my TV, hit the Home button, went to Music and my DLNA server was in the list.
I navigated through the music, it plays fine and it even displays the album art!!

In the past Ive tried mediatomb. It doesn't work at all with a Sony TV.
Ive tried various dlna servers.
Trust me, minidlna is the only one that works with a Sony (that ive tried myself anyway).

My TV is a Sony KDL40EX403.

Best regards
Mike
UK

---

### Post by bilbo1234 on 2010-11-26
Hey Mike,

I have a Sony bluray player and it also gave me a lot of trouble recognizing "DLNA compatible" servers. I did get minidlna to work, but also Rygel, so you may want to check it out as well. Minidlna gave me some trouble with audio playback. Good luck!

---

### Post by theboydidgood on 2011-01-20
@mikehicks - great work. I've just set up my 37ex503 and I'm ready to tackle DLNA. I already have a Sumvision Cyclone streaming my music and videos so I'm sceptical if this is going to just be an experiment more than useful. My thinking was that it would be quicker and easier to be able to this through the TV so I don't have to have switch on the cyclone, I can just use the TV. The question of course is about file types. Do you know if it will play avi and flash video for example?

Also, what success have you had in relation to ff and rw?

---

