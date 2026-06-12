---
title: "Ipod and Amarok connection Problems"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by FearBefore28 on 2008-03-22
Well with the help of these forums I finally got Amarok up and running but when I plug my ipod in to the computer it doesn't recognize it, amarok doesn't recognize it, rhytmbox or whatever doesn't recognize it, and it doesn't show up on the desktop, though the ipod switches to the connected screen so it knows its connected to something. i am using an old 3rd generation ipod and it used to be a little flaky connecting to itunes in windows but it usually worked. Can anyone help me get at least something to realize my ipod is connected?

---

### Post by ubuntu27 on 2008-03-22
I don't own an ipod so I will just make a recommendation.  Try out gtkpod. gtkpod is an ipod's playlists manager.

```
sudo apt-get install gtkpod
```

Maybe it won't work since Amarok didn't recognize it, but it is worth a try. 
Hope someone will jump-in and tell your a way to fix it.

---

### Post by lukem on 2008-03-25
Sounds like your main problem is that your IPOD doesn't mount when you connect it.  Try this thread [http://ubuntuforums.org/showthread.php?t=691704&highlight=usb+drive](http://ubuntuforums.org/showthread.php?t=691704&highlight=usb+drive) for some help on that.
Good Luck

---

### Post by hendersoneg on 2008-04-07
I just went through this yesterday with my Ipod.  I've now got it working and here's what I did.  

Plug in your Ipod
Open a terminal window. 
Type df (this will give you a list of devices connected)
Find the line that has your Ipod and see what it is being recognized as. (Mine was /dev/sdd1)
Note the location. 
Go into Amarok devices configuration and give the location as the mount point

Mine then found my Ipod and sync'd all my music.  Now my only problem is I have all my music twice.  Once from Itunes and once from Amarok, but I'll figure that out too.  

I'm a newbie at this Linux stuff and just about the time I think I'm beginning to understand a little of how things work, the Penguin reaches up with his little wing and gives me a cuff along side the ear just to remind me I don't.  :)

Thank god for the user forums.

---

