---
title: "gtkpod &amp; iPod"
date: 2008-07-03
forum: Multimedia Software
---

### Post by cjnkns on 2008-07-03
Hi all - 

I typically use my iPod on Windows and iTunes, but recently ventured to try it with gtkpod/banshee. I have succesfully been able to add songs and artwork to the iPod.

The problem is now I get absolutely now sound from the iPod at all. It's like the volume is off or on mute (which it is not). 

Anyone else have issues like this or know if I missed a step during sync with gtkpod?

Thanks!

---

### Post by cjnkns on 2008-07-03
I did notice the files I copied from my cd to linux have different permissions than the ones brought over from iTunes. So I changed them to be the same as the existing file permissions. Then I copied the changed files back over to the iPod and still nothing....

When I go to cover flow and try to play the album it quickly runs through each song and then stops. Doesn't play any of them. In order to get sound working again i have to resent the iPod (hold down Menu and the center button for a few seconds)

This is goofy - life was much easier on iTunes :(

---

### Post by uterrorista on 2008-07-03
it works for me. never had problems.
try also amarok.

---

### Post by cjnkns on 2008-07-03
I have seen some articles talking about re-formatting the ipod. Is this somethign that "needs" to be done? The iPod already works on a windows system so it must be fat32 which is what linux expects correct?

---

### Post by cjnkns on 2008-07-03
I get this message - not sure what it means?


> iTunesDB '/media/CARL'S IPOD/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/CARL'S IPOD/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using SHA1 checksums. This may take a long time.

---

### Post by cooltd825 on 2008-07-03
> **uterrorista said:**
> it works for me. never had problems.
try also amarok.

I'll second that.  Amarok is the best media player out there.  And that's coming from a kid who grew up on Windows :P

I would just suggest you reset your ipod and try transferring a few songs through Amarok.  If it works, then just transfer all the music you had before on.  If it doesn't, then there might be a problem with the ipod itself.  Unlikely, but still.............  Apple's been known to play mean tricks.

---

### Post by cjnkns on 2008-07-04
Hmm Amarok huh... The last time I tried Amarok on Gnome it looked horrible. I really didn't want to pollute my Gnome environment with kde apps, but I guess I'll try it.

Does anyone here use KDE in gnome? Or are you just using kde?

---

### Post by cjnkns on 2008-07-04
well it seems amarok doesn't work so well for me either.

I can get my collection imported into amarok and my ipod displays also.
But, when I transfer a couple albums I ripped on linux to the ipod. They just will not play. Looks like it is back to windows for the ipod... kind of a bummer really..

---

### Post by tijmz on 2008-07-04
I have never heard of this particular problem, but maybe this helps:

Was the iPod empty when you transferred files onto it using Banshee? If not, try reformatting your iPod using iTunes and then adding the files with Banshee to a 'clean' player.

Also, make sure you use software that is compiled against the latest version of **libgpod** if you're using a newer model iPod.

---

### Post by adouglasmhor on 2008-07-04
I use Hippo on my GF's Ipod if that helps anyone.

[http://www.gnome.org/projects/hipo/](http://www.gnome.org/projects/hipo/)

---

### Post by cjnkns on 2008-07-04
> Was the iPod empty when you transferred files onto it using Banshee? If not, try reformatting your iPod using iTunes and then adding the files with Banshee to a 'clean' player.

Also, make sure you use software that is compiled against the latest version of gtkpod if you're using a newer model iPod.

Thanks I'll give it a shot. I appreciate the help and suggestions!

---

### Post by cjnkns on 2008-07-05
Ok - so I finally figured out why I couldn't get my collection built in amarok.
It didn't want me to use MySql so I switched to SQLLite and it worked fine.

I am still not sure why my iPod would not play the cd's I ripped using banshee. They were ripped into the .m4a format which my ipod is alredy using anyway.

So I ripped the cd again using sound juicer into mp3 format and now it works fine.

Thanks for all the help and suggestions!

---

