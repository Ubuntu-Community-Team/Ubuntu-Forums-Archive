---
title: "iPod Nano Artcover + Amarok"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by hanexar on 2007-04-16
Hiya, 
   I just upgrade to feisty fawn to get the latest Amarok version. I hoped I could transfer the art cover on my 2nd gen nano ipod. But when I'm trying to do so, I only get the text aligned to the left on my ipod, as if I had a blank artcover loaded. I check my configuration on Amarok, and it is pointing to the good ipod models. Gtkpod is not a solution because first it is trying to mount my ipod where it is not (do not why) and second, I want to transfer amarok cover that I have downloaded with the amarok library.

Any Idea?

---

### Post by pingpongboss on 2007-04-16
I don't really like how amarok manages artwork, it's really unpredictable soemtimes. Sometimes, the entire album will be assigned a certain picture, while files that belong to the album have different pictures. I tend to get alot of that, especially with multi-artist albums. That might be a reason why ur artwork doesnt get transfered to ur ipod.

A clumsy way to get all the files tagged with the same artwork is to use another program, easytag.  There's also  the "refresh cover images" option if u right click inside the sidebar where it shows u all the songs that it detects on the connected ipod.

---

### Post by hanexar on 2007-04-17
> **pingpongboss said:**
> I don't really like how amarok manages artwork, it's really unpredictable soemtimes. Sometimes, the entire album will be assigned a certain picture, while files that belong to the album have different pictures. I tend to get alot of that, especially with multi-artist albums. That might be a reason why ur artwork doesnt get transfered to ur ipod.

A clumsy way to get all the files tagged with the same artwork is to use another program, easytag.  There's also  the "refresh cover images" option if u right click inside the sidebar where it shows u all the songs that it detects on the connected ipod.

Thanx for your reply,

All my tag are already in perfect condition. I only have one cover per album. I don't think that's the problems.

What I do get, is no album artwork on my ipod at all, but the text aligned on left as if there was one... It seems more like a transfer glitch or something like that.

---

### Post by ronocdh on 2007-04-17
> **hanexar said:**
> Thanx for your reply,

All my tag are already in perfect condition. I only have one cover per album. I don't think that's the problems.

What I do get, is no album artwork on my ipod at all, but the text aligned on left as if there was one... It seems more like a transfer glitch or something like that.

I believe this is because Amarok is just indexing artwork, not attaching it to the actually song file. iTunes (on OS X and Windows) actually binds the artwork to the song file, which can be verified by checking the filesize before and after adding the artwork. Amarok remains more hands off and just creates an index overlay for your songs. Try backing up your music and then deleting all Amarok config files; upon reinstallation, Amarok will have to find the artwork again, because it is not present on the individual files.

---

### Post by hanexar on 2007-04-17
ohhhhh :(

---

### Post by pingpongboss on 2007-04-17
would using easytag fix that?

---

### Post by hanexar on 2007-04-18
Unless easytag can attach on the file the indexed artwork I downloaded with amarok, no, it won't help.

---

### Post by hanexar on 2007-04-20
Ok, some new data: I just successfully transfered artwork on a nano first gen. So it is not an indexing problem, but a transfer problems with the 2nd gen nano.

Any insight on this?

---

### Post by wallacetheweasel on 2007-06-07
Sorry to revive the thread, but I came here by Google with the same problem, and I thought that the answers contained at the Amarok wiki might be relevant to other people who come here looking for answers:

[http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working](http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working)

---

### Post by hanexar on 2007-06-07
Thanx for the info, I'll look into this.

---

