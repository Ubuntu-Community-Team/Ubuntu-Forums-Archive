---
title: "MythTV &amp; AIMS Video Highway Xtreme"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by PaganHippie on 2006-07-08
I got the VHX card in a trade from a friend, and I'm interested in building a MythTV box around it.  Has anyone tried it?  Are there any particular hardware, software, and/or driver issues I should know about, or does it 'just work?'

Thanks in advance....

---

### Post by brandon_r87 on 2006-08-13
From what I've been reading, it works with MythTV, although I don't quite have it going yet.  You use the bttv drivers which are either built into the kernel or set up as modules.  Otherwise you can download them.  

I used these commands...

```
rmmod bttv 
rmmod tuner
modprobe bttv card=14 tuner=2
```

and then dmesg and got this output...

```
[   54.022448] bttv0: using: Aimslab Video Highway Xtreme (VHX) [card=14,insmod option]
```

Showing that the drivers work.  I can also get video within VLC (VideoLAN Client) and XawTV from the the cable and composite inputs, s-video not tested yet.  No audio though.  But in MythTV, I can scan the channels and it picks them up, but upon loading up the frontend and going to Watch TV, I get a black screen that hangs for a while and then goes back to the main menu.  So it works, it just takes a little work.  

Besides that, any help regarding not getting video in MythTV or why I'm not getting audio in other programs?  BTW, it took me hours to figure MythTV out.  I probably could've read the manuals, but it's so much easier to spend hours frustrated and thinking mySQL is the problem when you just need the load the friggin backend. ](*,)

---

