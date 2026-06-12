---
title: "Weird! Can't Change Tags of 9/10 Songs of 1 Album, no matter what I try! Very Strange"
date: 2009-02-03
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-02-03
OK, the scenario is this: an album I downloaded "Dahlia" by X Japan is split up under 2 bands in Rhythmbox: track 9 is under "X Japan" and Tracks 1-8, 10 are under "X JAPAN", with the album being "Dahlia" and "DAHLIA" respectively.

Now, I am aware that unlike in Windows, case can make all the difference in Linux. I am also aware that, unlike in Windows, in Linux I can change the tags to the correct case if needed. I am also aware that if something is refusing to be renamed or whatever (in this case, the change of tags holding), I can change permissions of files to allow me the read/write.

What I don't understand is why in blazes I just can't successfully edit the tags using either Rhythmbox or EasyTag! When I do so in Rhythmbox (let's call it RB for short), the X JAPAN vanishes and the 9 tracks go into X Japan (and under Dahlia instead of DAHLIA), but within 2 seconds those 9 tracks are no longer there, but back under X JAPAN! In EasyTag (ET), I can change the case and apparently it is saved, as when I go back and forward between folders, the changes seem to stick. But this I think is only while I am still in that ET session, as when I restart it, the tags of 9/10 tracks are back to uppercase.

I've checked permissions of the files, and all is fine of course, as I wouldn't have been able to "edit" the tags in the first place. I've never seen anything like this before, and I have edited plenty of tags. I've edited plenty where the author left the caps lock on, and no worries about changing to title case. Except for this album, or at least 90% of the songs.

One interesting note is that when I open that folder in ET, the offending tracks are red, while track 9 is white. As I've said, ET fools me into thinking I've successfully edited and saved the tags, but RB confirms I haven't, and reopening ET shows the same. Actually, don't quote me on that, as sometimes it is a mish-mash of some seeming to have the correct case, and others not. For example, right now I opened ET and every track has X Japan as the band (so all seem to have the correct case), and every other song has the correct case for the album, while others have DAHLIA.

But in RB, it's the same as before, with only one track having the correct case for the artist and album. Oh, and 3 tracks have their tag for the song name in uppercase too, and this can't be changed either. So ET doesn't know what the heck is going on, and RB shows the tags as they are - which I can confirm by right-clicking each file in the residing folder, and choosing Properties > Audio.

Can anybody explain what is going on, and/or tell me how to get out of this loop of unsuccessfully editing the tags? (Please don't reply "Oh, sounds like a permissions issue..." hehe, as I've not only checked that, but tried all sorts of whacky things I've never had to do with other albums, like changing groups and everything). Hope someone can help, as this is driving me nuts! Cheers.

---

### Post by OzzyFrank on 2009-02-03
OK, sort of found a solution, at least for how to get them to show properly in Rhythmbox: I manually edited **rhythmdb.xml** in **~/.gnome2/rhythmbox** and it worked. While that gets the songs in the right place in RB, I still can't figure out why the tags aren't really changed, which I can confirm by viewing the Properties of each file. And of course also by opening **Amarok** - in my Collection there is both X Japan and X JAPAN. This will of course happen with any other program than RB, as I've only edited the xml file for that program.

EDIT: I just had a closer look in Amarok, and this just gets weirder! Only one of the tracks is under X JAPAN/DAHLIA, while the rest are under X Japan/Dahlia. I editing the tag for that one song in Amarok, and at least in that program too there is now only X Japan/Dahlia, with all tracks together. Still hasn't changed a thing in reality, as in Nautilus the Properties > Audio for all but track 9 still show uppercase info.

---

