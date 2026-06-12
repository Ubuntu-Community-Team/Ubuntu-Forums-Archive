---
title: "[SOLVED] Cover Art on iPod Classic and gtkpod not reading artist tag"
date: 2008-12-08
forum: Multimedia Software
---

### Post by mwsherman on 2008-12-08
Hi.

I've been having problems getting cover art to transfer to my ipod classic. The music transfers fine, but for some reason the cover art doesn't.

Sorry to sort of "double dip" with this post, but I'm just trying to solve my problem, and there are multiple ways to do it. I'm flexible.

My cover art is embedded in the metadata.

I tried using amarok and songbird and rhythmbox. Both transferred the music just fine, but no cover art got transferred.

I tried using gtkpod. It transferred the cover art properly, but it has another extremely strange bug...it will not use my artist ID3 tag. This is confusing me totally!

So I load my files into gtkpod and the artist tags are wrong (I had just changed this whole batch, putting "NEW" in front of the artist name in a bunch of files, to mark my new music). I tagged them in EasyTAG, and all the other programs (amarok, songbird, rhythmbox) read these new tags fine...it is presumably NOT a problem with the tags.

But no matter what I do in gtkpod, it refuses to read my new artist tag. The other fields (song name, album name) it will read if I change them in easy tag. But something about the artist field is not changing.

I tried reinstall gtkpod, as well as killing the contents of the .gtkpod directory. I ran gtkpod both with and without the ipod hooked up. I killed the local directory. I played with the settings...nothing is working. 

So can anyone either

Recommend another program that will transfer my songs and album art?

or

Tell me how to make amarok, rhythmbox, or songbird transfer my album art?

or

Help me solve this incredibly weird problem where gtkpod refuses to read my artist ID3 tags?

Thanks.

---

### Post by rick08 on 2008-12-08
I encountered the same problems with gtkpod.  I changed from gtkpod to floola and I currently do not have any problems.  I have also used floola with my old ipod video and the new ipod nano and have had no problems.  I recommend using floola if you cannot get gtkpod to work because I found floola to be much more superior and I was able to add cover art.

---

### Post by mwsherman on 2008-12-08
Floola is unable to read much of my artwork.

It gets about 10% of it. The rest of it is still visible in Amarok, Songbird, etc, but for some reason most of my artwork isn't being read by Floola, thus it can't even transfer it to the iPod.

I can't figure out why Floola is able to read some of the artwork, but not most of it.

---

### Post by apd on 2008-12-09
Read about troubleshooting on floolas homepage. could be that u need to use Itunes to reinstall the original settings on yr Ipod and that might be the solution.

---

### Post by mwsherman on 2008-12-09
> **apd said:**
> Read about troubleshooting on floolas homepage. could be that u need to use Itunes to reinstall the original settings on yr Ipod and that might be the solution.

The problem isn't with the iPod. It's with Floola. Floola never sees the cover art.

I tried a few times with a freshly restored iPod, since Floola wont even touch your iPod if any program besides iTunes has touched it.



In other news, gtkpod will read tags if I use EasyTAG to save them in version 2.3 instead of 2.4 . But I'm in discussions with both Floola and gtkpod developers, so hopefully I'll soon have solutions to both of these problems to share.

---

### Post by mwsherman on 2008-12-10
After some discussion on a gtkpod mailing list, the source of the gtkpod tagging bug was discovered. gtkpod was reading the "album artist" tag instead of the artist tag.

The fix is in the current build, but has not yet made its way into the most recent packaged version.

I'm writing this for future internet surfers who stumble into this thread.

You can fix this by changing your album artist tag instead of your artist tag. Although I can't tell you how to do that...

---

### Post by Floola on 2008-12-10
Next version of Floola will fix the embedded artwork bug that existed under linux. The problem with PNG embedded artwork.

Just to let you know,
Tomas

---

### Post by mwsherman on 2008-12-11
Whoops. I made this post by mistake.

---

