---
title: "Cannot play DVD"
date: 2012-12-01
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2012-12-01
Just got a DVD, put into the player, it mounts and vlc started and then crashed.

I started vlc in the terminal and here is what I got

```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x9a5f908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: WAIT_TIL_YOU_ARE_OLDER
libdvdnav: DVD Serial Number: 438392D3________
libdvdnav: DVD Title (Alternative): WAIT_TIL_YOU_ARE_OLDER
libdvdnav: Unable to find map file '/home/monkeybrain/.dvdnav/WAIT_TIL_YOU_ARE_OLDER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdread: Invalid IFO for title 8 (VTS_08_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdread: Invalid IFO for title 5 (VTS_05_0.BU).
libdvdread: Invalid IFO for title 6 (VTS_06_0.BU).
libdvdread: Invalid IFO for title 7 (VTS_07_0.BU).
libdvdread: Invalid IFO for title 8 (VTS_08_0.BU).
libdvdread: Invalid IFO for title 9 (VTS_09_0.BU).
Segmentation fault

```

I got 3 dvds in the same place, two of them has this issue, third one is ok. Any idea what may have been the problem?

Thanks.

---

### Post by Greggi on 2012-12-01
Maybe a problem with copyright?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by SeijiSensei on 2012-12-01
Where did you buy this?  Did you buy it from a vendor in the same country in which you live?

According to the logs the DVD claims to be "Region 0" which usually means it's a bootleg.  The problem may have to do with region codings; your DVD player may be set to a legitimate region and will refuse to play something with a different region code.  There are ways to change the DVD player's region coding, but you can only do it five times total in the lifespan of the player.  I don't know how to do this in Linux though I'm sure it is possible; in Windows, you can change a setting in a dialog box to change the region coding.

---

### Post by andrew.46 on 2012-12-01
Does seem a little odd, have you tried with SMPlayer?

---

### Post by monkeybrain2012 on 2012-12-03
> **andrew.46 said:**
> Does seem a little odd, have you tried with SMPlayer?

Yeah, it is very odd. I think basically my dvd drive is toasted, sort of. 

After trying a few more times with the same result I could't even open my dvd drive any more even with no disc inside (have to stick a pin into the hole to open it) Tried fixing it a whole night with no avail (using a screw driver) then this afternoon somehow it works again. Put the same dvd in and it now plays in both vlc and Smplayer??!! (One of them, The other one also plays for about a minute with Smplayer and then stuck, Vlc crashed like yesterday, I think this one may be damaged)

I will mark this thread as solved (sort of) since it is likely some electronic-mechanical problems in the hardware which has nothing to do with the OS.

(From this little exercise I made a discovery! Smplayer now appears to support DVD menu, it used not to, but now it does,tried with both mplayer and mplayer2 as backends)

---

### Post by carrdeavelon on 2013-03-25
I found this forum searching after I got this strange problem that the first 2 of 4 programs on a DVD were OK, but mplayer refused to show the others.
In the end it seemed to be because I'd had another disk mounded from that drive. As soon as I gave the umount command I could see all the programs on the DVD again.
Yours
Ian

---

