---
title: "deleted channels return"
date: 2010-10-10
forum: Mythbuntu
---

### Post by mookie60 on 2010-10-10
mythbuntu 9.04, up to date
hvr 1600 & pchdtv 5500


I have a couple of analog channels my cable company has moved to its qam channels.   The analog tuner still finds these channels even though they're just static.

When I delete these channels, using either mythweb or the main backend setup, they only stay deleted for about a day - then they reappear.   I think this is happening when it does its nightly mythfilldatabase.

Any suggestions how to correct this?

Thanks

---

### Post by ian dobson on 2010-10-10
Hi,

What grabber were you using for the EPG on the deleted channels? It could well be that the grabber is still being run every 2nd day and thats adding the deleted channels.

Regards
Ian Dobson

---

### Post by mookie60 on 2010-10-11
I'm using Schedule's Direct.   I'll try deleting the channels on SD and see how that works.   

But if the channels are determined by SD, what does it mean when a channel is deleted using Mythweb or Mythtv channel editor; does this have another purpose? 

Thanks

---

### Post by ian dobson on 2010-10-11
Hi,

If you delete a channel with mythweb or what ever,  whenever you run Schedule's Direct it'll see that the channels are deleted and re-add them.

So you need to delete them from Schedule's Direct as well.

Regards
Ian Dobson

---

### Post by mookie60 on 2010-10-11
Thanks so much Ian

---

### Post by jlagrone on 2010-10-11
There's a place in the general backend setup with options for mythfilldatabase. One of the fields is for mythfilldatabase arguments. you can put ```
--remove-new-channels
``` and it will delete any channels that aren't in your database

---

