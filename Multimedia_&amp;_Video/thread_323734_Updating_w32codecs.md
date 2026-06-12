---
title: "Updating w32codecs"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by Yleeyas on 2006-12-22
Hi all,

I just noticed that I've got an older version of the w32codecs (20050412-1plf4?) while the 'restricted formats' page shows a more recent v. 20061022.
So, should I upgrade and how?:confused: 

Thanx
Yleeyas

---

### Post by Dr. Nick on 2006-12-22
probably only need to update if you have problems with a particular file, if you want just search google for the new version and install just like the old, most likely just double-clicking or by using 

sudo dpkg -i *packagename*

---

### Post by Yleeyas on 2006-12-22
Dr. Nick,

Thanx for the reply. So your saying that by following the instructions in the 'restricted formats' wiki this will upgrade the w32codecs, not just install a newer version along side the old?? (Anyone?)

edit: OOPS, :oops:  I just did a 'man dpkg' and sure enough it does handle remove old / install new. 

I'm looking to upgrade because, as you suggest, I'm having trouble with my mplayer plugin for FF. Once in a while it hangs the system when playing a wmv file, and I have to powerdown reboot to get my system back. I haven't found anyone with same problem in here, so I thought I'd try solving that problem stepwise, starting with codecs updates.

edit: Now to see if the new w32codecs solves the mplayer-plug crashes [-o< 

Thanks again,

Yleeyas

---

### Post by Dr. Nick on 2006-12-22
Must have missed your posts about the mplayer hang, I had that same problem too before I trashed the install beyond repair ;)

Yes, dpkg handles updates itself, also I imagine that the filenames between w32versions are the same in which case installing a new version would inherently overwrite the old versions.

Let me know if the crashes go away, I never thought to update my codecs to troubleshoot, Its a pain to trouble shoot problems that force you to restart like that.

---

### Post by Yleeyas on 2006-12-22
Hi Dr. Nick,

Well the crashes didn't do away, so it ain't the codecs. ](*,) 
I'm guessing at this point that I'll need to update the mplayer-plugins for FF, or just wait for the repos to update. :rolleyes: 

Ofcourse, it might be the wmv files are boinked, cuz it happens very rarely. I'll have to start keeping track of which sites cause the problem.

Good thing I'm in this for the long haul :-D 

Thanx again
Yleeyas

---

