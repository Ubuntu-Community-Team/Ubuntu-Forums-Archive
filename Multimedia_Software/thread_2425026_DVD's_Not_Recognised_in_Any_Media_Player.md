---
title: "DVD's Not Recognised in Any Media Player"
date: 2019-08-19
forum: Multimedia Software
---

### Post by Daveski17 on 2019-08-19
Hello,

I upgraded to Ubuntu 16.04 LTS from 14.04 LTS a few months ago and added the  libdvd package

sudo apt-get install libdvd-pkg

sudo dpkg-reconfigure libdvd-pkg

[[img]http://i.imgur.com/4LxL1bX.jpg[/img]](https://imgur.com/4LxL1bX)

I&#8217;d not attempted to play a DVD (with VLC) until last night when I discovered it wouldn&#8217;t recognise or run the DVD (it used to with 14.04). It won&#8217;t run in SMPlayer or Videos either.
What do I need to do to convince it to play DVD&#8217;s?

[[img]http://i.imgur.com/yVW3CHd.jpg[/img]](https://imgur.com/yVW3CHd)

The packages are definitely installed.

[[img]http://i.imgur.com/9rq2A5z.png[/img]](https://imgur.com/9rq2A5z)

Thanks.

---

### Post by crip720 on 2019-08-19
It could be the DVD player or even the disk itself.  Can you check with windows or maybe an external DVD player? Do you have another DVD disk that is known to be good(just played on another machine)?

---

### Post by Daveski17 on 2019-08-19
> **crip720 said:**
> It could be the DVD player or even the disk itself.  Can you check with windows or maybe an external DVD player? Do you have another DVD disk that is known to be good(just played on another machine)?

I've tried different DVD's. They play in other machines. I could play them in 14.04. I'm guessing this is a software problem.

---

### Post by crip720 on 2019-08-19
Can try the last post idea in this.  [https://askubuntu.com/questions/889642/ubuntu-16-04-cant-play-commercial-dvd](https://askubuntu.com/questions/889642/ubuntu-16-04-cant-play-commercial-dvd).  Or you can check out this [https://linuxforums.org.uk/index.php?topic=13309.0](https://linuxforums.org.uk/index.php?topic=13309.0).

---

### Post by mc4man on 2019-08-19
Put a dvd in the drive..
Does it show up in the launcher or in the file manager?
Run this (with a dvd in), what's reported for that drive, look in the *-cdrom section
```
sudo lshw -c disk
```

---

### Post by Daveski17 on 2019-08-20
> **crip720 said:**
> Can try the last post idea in this.  [https://askubuntu.com/questions/889642/ubuntu-16-04-cant-play-commercial-dvd](https://askubuntu.com/questions/889642/ubuntu-16-04-cant-play-commercial-dvd).  Or you can check out this [https://linuxforums.org.uk/index.php?topic=13309.0](https://linuxforums.org.uk/index.php?topic=13309.0).

OK thanks.

---

### Post by Daveski17 on 2019-08-20
> **mc4man said:**
> Put a dvd in the drive..
Does it show up in the launcher or in the file manager?
Run this (with a dvd in), what's reported for that drive, look in the *-cdrom section
```
sudo lshw -c disk
```

I've just tried to run a DVD and now, for some inexplicable reason,it not only recognises the disc but plays it.

[[img]http://i.imgur.com/KdzBbt0.jpg[/img]](https://imgur.com/KdzBbt0) 

I ran the Terminal command with the disc running.

[[img]http://i.imgur.com/r9BGD7V.jpg[/img]](https://imgur.com/r9BGD7V)

I have no explanation for this, but thanks for the help. Is this a known bug on 16.04? Because I've read of similar weird things happening with running DVD's on 16.04.

---

### Post by mc4man on 2019-08-20
> **Daveski17 said:**
> I've just tried to run a DVD and now, for some inexplicable reason,it not only recognises the disc but plays it.

I have no explanation for this, but thanks for the help. Is this a known bug on 16.04? Because I've read of similar weird things happening with running DVD's on 16.04.
Most unlikely to be a bug..
The detection of the media and mounting of the filesystem of DVD_VIDEO is seperate from the reading,navigation, playback of that media/filesystem..
In your case it was most likely the media/filesystem wasn't detected. In that case no player can playback what's 'not there'.

Generally detection/and subsequent mounting are hardware issues, not software though there have been some software issues concerning UDF in the past.
The most common hardware cause is a dirty lens from dust or environment like nicotine.

Also possible is lens tracking problems. When you insert the dvd the lens needs to move over the very inner band area to read disk info, if it can't then nothing will happen.
As drives get older they may have issues getting there, not uncommon with older laptop drives which generally are junk to begin with. 
Desktop drives can have a better lifetime though OEM drives aren't usually very good either.

---

### Post by Daveski17 on 2019-08-20
> **mc4man said:**
> Most unlikely to be a bug..
The detection of the media and mounting of the filesystem of DVD_VIDEO is seperate from the reading,navigation, playback of that media/filesystem..
In your case it was most likely the media/filesystem wasn't detected. In that case no player can playback what's 'not there'.

Generally detection/and subsequent mounting are hardware issues, not software though there have been some software issues concerning UDF in the past.
The most common hardware cause is a dirty lens from dust or environment like nicotine.

Also possible is lens tracking problems. When you insert the dvd the lens needs to move over the very inner band area to read disk info, if it can't then nothing will happen.
As drives get older they may have issues getting there, not uncommon with older laptop drives which generally are junk to begin with. 
Desktop drives can have a better lifetime though OEM drives aren't usually very good either.

Thanks for the reply. It's a distinct possibility that it actually was hardware related. I've never really rated laptop optical drives anyway. My Lenovo isn't that old though and doesn't get used every day. I rarely use the DVD player. I did try a photographic rocket blower to blow any dust out of the optical drive yesterday. Today, before I decided to attempt to run the DVD, I gave the drive a gentle once over with a micro fibre cloth. So I think you're right and the odds are it was dust in the lens.

---

