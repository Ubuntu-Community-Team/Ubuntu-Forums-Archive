---
title: "Mythbuntu DVD wont start"
date: 2008-09-22
forum: Mythbuntu
---

### Post by MartinusEx on 2008-09-22
Hi.

I'm working on Mythbuntu 8.04.1. on FE/BE machine

Currently Mythbuntu Frontend refuses to play a DVD which is a bought one and known good.

I have already seen a DVD so I know that it worked.
I ran an update recently but didn't check all the corners.

Any idea around?
Thx a lot in advance

Martinus

---

### Post by SiHa on 2008-09-22
What command do you have setup in the setup for playing DVD? I found 'internal' just did nothing, I'm using xine now with no probs - mplayer doesn't really do DVD menus.

---

### Post by MartinusEx on 2008-09-22
H SiHa,

yep, it was set to internal.
I changed to xine and to vlc, both breaking off.
With vlc I found that it couldn't open dev/dvd.
I even tried vlc from the application menu, but it doesn't start the dvd

I can see dev/dvd and dev/dvdrw  

This looks like a problem deeper in the system.
I'm not linux enough to hack that myself.

Any ideas on this are very appreciated

OK:
now I found that the very first dvd i played is still played.
some others are played wit internal and vlc, other aren't playd.
looks like a problem with dvd's which have a ripping protection.
I saw this in another thread right in this forum, I'll have a look around if there's any solution.

how about that? 

thx a lot in advance

Martinus

---

### Post by ian dobson on 2008-09-22
Hi,

On my frontend my DVD-RW drive seems to exist as /dev/dvdrw4 and as /dev/sr0. Maybe the device name needs to be changed on your box.

Regards
Ian Dobson

---

### Post by MartinusEx on 2008-09-22
Hi Ian,

i'm totally confused by now.

I edited the posting above and didn't see yours.
well as i said in the edit, the dvd works despite of all what i said above.

true is, that the internal player and vlc and probably xine as well don't play dvd's with a certain copy protection.
 do you have any information on that issue?

rgds
Martinus :confused::confused:

---

### Post by ian dobson on 2008-09-22
Hi,

Maybe you just need to install libdvdcss2.
 
```
dpkg --get-selections | grep css 
```
Will show if it's installed and if not just do a 
```
apt-get install libdvdcss2
```

Or you can go into the control center and add the non-free codecs.

Regards
Ian Dobson

---

### Post by MartinusEx on 2008-09-22
All right Ian,


:popcorn:

that is it.

thanx a lot
hope I can pay back later

rgds

Martin

---

