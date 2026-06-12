---
title: "Ipod With Amarok"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by SRGT. DeGreene on 2008-03-01
Ok, so i got my ipod to work and everything and add all my music then I unmount my Ipod and all my album art is gone and amarok doesn't have anything to fix that that I know of. If any knows different or can help that would be sweet.

---

### Post by motoperpetuo on 2008-03-31
since there's another unanswered post that asks essentially the same question, i'm going to guess that amarok doesn't support album art. someone please correct me if i'm wrong, but it seems that there's no application in linux that will allow you to get album art on an ipod or manage playlists on an ipod like iTunes does.

i just had a crazy idea...why not try to run iTunes on wine? it's probably wouldn't work, but it might be worth a shot.

---

### Post by Matthewslf on 2008-03-31
I think I remember getting iTunes to work in wine. I'll try again to make sure. Even if it does work, I have doubts about it handling the usb/firewire very well. As for Amarok, it has a great album art feature, it must just not work with ipods.

---

### Post by Matthewslf on 2008-03-31
Well, no luck with iTunes in wine. I admit I am not the expert when it comes to wine, but it will take some doing to get working.

---

### Post by motoperpetuo on 2008-04-06
> **motoperpetuo said:**
> since there's another unanswered post that asks essentially the same question, i'm going to guess that amarok doesn't support album art. someone please correct me if i'm wrong, but it seems that there's no application in linux that will allow you to get album art on an ipod or manage playlists on an ipod like iTunes does.

i just had a crazy idea...why not try to run iTunes on wine? it's probably wouldn't work, but it might be worth a shot.

i proved myself wrong. amarok does support album art and can transfer it to an ipod. i've been fiddling with it off and on for days now and finally got it to (mostly) work. i'm not sure, but i think i had identified my ipod model incorrectly. it seems like when i identified the device correctly and added one more track to the ipod, it brought the album art over too. (i had to add one more track because, as near as i can see, there's no "synch ipod now" function in amarok like there is in itunes. it seems like you have to add or remove at least one track to make the "transfer" button available.)

the only thing i haven't figured out is how to add album art for albums that i've purchased recently and never had uploaded to my ipod through itunes in windows. i can add a cover for these albums within amarok by doing this:

1) tools|cover manager
2) click on the artist in the list on the left.
3) right-click on the empty album icon, choose "set custom cover" and browse to the .jpg for the album cover

after doing this, i can see the album cover in amarok, but the cover won't upload to my ipod. if anyone has any suggestions, please let me know.

also, i still haven't figured out how to upload custom playlists to my ipod, but maybe that's supported too. i'll try to figure it out another day.

---

### Post by motoperpetuo on 2008-04-16
i figured this problem out, too. if the art for a particular album doesn't appear on your ipod, you need to:

1) delete the album from the ipod.
2) go into cover manager (tools|cover manager) and add the art as a custom cover.
3) transfer the album to the ipod again.

i think there is supposed to be some way to get album art automatically, but i was never able to get that to work in itunes either, so i'm not too worried about it.

---

