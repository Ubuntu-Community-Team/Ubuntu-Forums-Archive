---
title: "rythmbox failing to read in lots of mp3's"
date: 2008-05-24
forum: Multimedia Software
---

### Post by xtang on 2008-05-24
all my music is in one folder. exaile works fine in reading the folder into its library but rythmbox only manages to read in a fraction of them. There are a huge amount of import errors, all of the with "Couldn't access file:///home/...

Please help, it seems only rythmbox is capable of transferring music to my ipod touch.

---

### Post by IHATEDLINK on 2008-05-24
Oh no, you are SO WRONG. I have a Touch to.
The best way to sync it is using Amarok/gtkpod and to jailbrake your touch for WIRELESS SYNCING, sounds cool?
[iPod Touch and Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPhone")

For rythmbox, is all your music in mp3? what about mpeg-2 or AAC? Try installing all the codecs avaible for gstreamer.

---

### Post by xtang on 2008-05-24
i did all that, jailbreaking, wireless synching etc. I CAN transfer music.

I was just hoping to do all this with rythmbox but it wont process all my mp3's. I dont want to use amarok, I havnt tried gtkpod yet. All my music is in mp3. I installed the restricted extras package, what else? I can playback mp3.

Maybe i shouldnt have mentioned the Touch, this is essentially a Rythmbox specific problem

---

### Post by IHATEDLINK on 2008-05-24
Ok, I'm glad I'm the only Amarok hater :). IT'S JUST SO DARN UGLY!
Did you recently moved all your mp3s? Just remove all the files that Rythmbox can't read and add them again. (Or right click the song>Properties>Details and change the location.)
If this doesn't work I advise you to

1 Remove Rythmbox:

```
sudo apt-get remove rhythmbox 
```

2 And install it again:

```
sudo apt-get install rhythmbox 
```

Remember to tell me how it went. If i solved your problem you can thank me by clicking the little star button at the bottom right of the post. ;)

PS: Does your Touch syncs well with Rhytmbox? Does it 'Autosync'? iPod management is one of the main things that are keeping me for removing XP.

---

### Post by xtang on 2008-05-24
I know why now, its because rythmbox cant read in files with spaces in them.

nvm, I will try something else.



The ipod management is still pretty poor, having to type ipod-touch-mount in the terminal and the password (twice!). Amarok automates this but like we said, neither  of use likes amarok. There's no autosyncing like in itunes, its select file and then transfer.

---

### Post by IHATEDLINK on 2008-05-25
> **xtang said:**
> I know why now, its because rythmbox cant read in files with spaces in them.

nvm, I will try something else.



The ipod management is still pretty poor, having to type ipod-touch-mount in the terminal and the password (twice!). Amarok automates this but like we said, neither  of use likes amarok. There's no autosyncing like in itunes, its select file and then transfer.

Really? I didn't thought about that..

For the iPod Touch.... Well, thats why I started the iTunes Linux Project( link on my sign)
I hate that apple forces people to proprietary OS'.
I guess it's still dual-booting for me... :(

---

