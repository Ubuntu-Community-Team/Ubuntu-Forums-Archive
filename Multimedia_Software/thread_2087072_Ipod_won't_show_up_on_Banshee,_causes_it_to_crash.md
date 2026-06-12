---
title: "Ipod won't show up on Banshee, causes it to crash"
date: 2012-11-22
forum: Multimedia Software
---

### Post by Maverick Mungbean on 2012-11-22
Since updating to Ubuntu 12.10 I can't put Music on my iPod anymore, Banshee does not recognize it and crashes after about 10 seconds.

Also, my iPod won't mount at all after I unplug it.

I have tried the upairing and pairing commands, none of which seem to make any sort of difference.

I was going to post the output of 'banshee' in the Terminal, but my whole Laptop is messing up, it is reluctant to open any application right now.

Anyway, my iPod is running ios 4.2 and it has been like that for quite some time. Never been a problem before.

I could really use some advice here.

---

### Post by Maverick Mungbean on 2012-11-26
This is driving me insane, any help please?

---

### Post by Shuudoushi on 2012-11-26
Do to 12.10 being a "dev" build atm it is rather buggy with some already installed software. 12.04's CompizConfig for example does NOT like working in 12.10 (I found this out the hard way when i gone to update; I went back to 12.04 just FYI). I would suggest backing up your data and trying to reinstall your software. If that doesn't work you may need to downgrade or rollback to 12.04.

---

### Post by Maverick Mungbean on 2012-11-26
When I try to load Banshee into memory at boot and then plug in the iPod the Terminal gives me this

> Failed to load media-player-info file for 1


---

### Post by Maverick Mungbean on 2012-11-26
> **Shuudoushi said:**
> Do to 12.10 being a "dev" build atm it is rather buggy with some already installed software. 12.04's CompizConfig for example does NOT like working in 12.10 (I found this out the hard way when i gone to update; I went back to 12.04 just FYI). I would suggest backing up your data and trying to reinstall your software. If that doesn't work you may need to downgrade or rollback to 12.04.


ah right. Would be the second time I would have to do a clean install..

---

### Post by Shuudoushi on 2012-11-26
> **Maverick Mungbean said:**
> ah right. Would be the second time I would have to do a clean install..

Yeah sorry ^^; I wish 12.10 wasn't so buggy myself. I love a lot of the new stuff from 12.10 but a lot of my stuff simply will not work on 12.10 ATM.

---

### Post by Maverick Mungbean on 2012-11-26
> **Shuudoushi said:**
> Yeah sorry ^^; I wish 12.10 wasn't so buggy myself. I love a lot of the new stuff from 12.10 but a lot of my stuff simply will not work on 12.10 ATM.
So I just uninstalled and installed Banshee, without backing up my music files because, frankly, I don't need them that much.
But my stuff is still there and it gets the same errors over and OVER again. Gonna downgrade back to 12.04 I think.

---

### Post by Shuudoushi on 2012-11-26
> **Maverick Mungbean said:**
> So I just uninstalled and installed Banshee, without backing up my music files because, frankly, I don't need them that much.
But my stuff is still there and it gets the same errors over and OVER again. Gonna downgrade back to 12.04 I think.

Sounds like the best thing to do i think. As it stands i don't think Apple has given Ubuntu permission to use there drivers with Ubuntu 12.10 yet so it may be a bit before you see support for ipod....

---

