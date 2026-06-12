---
title: "Amarok wont update tags for files in collection"
date: 2010-02-09
forum: Multimedia Software
---

### Post by damnated on 2010-02-09
I have most of my music on my hard drive in one big "Music" folder, and in Amarok this is seen as the collection. Everything is imported, works fine.

Until i change the ID3 tags of a file/album. Amarok refuses to load the new tags, and keeps displaying the old tags. 

I have over 200 GB of music in that folder, some of it is badly tagged. When i realize that, i retag the files with Musicbrainz. And unless i scan the entire collection again, the new tags wont be loaded. Needless to say i can't listen to the respective album/file for hours, as the rescanning of that whole folder takes at least one hour.

Any ideas?

---

### Post by b9k9kiwi on 2010-02-09
It would be helpful to say which version of Amarok you are using.

I am using 2.2.0 and I can have Amarok rescan my library and continue to listen to music at the same time.

---

### Post by damnated on 2010-02-09
I'm using the latest build.

Please read what i wrote and don't start talking about the weather. 

My problem is that if i change the tag of a file, amarok will use the old tag unless i rescan the whole collection.

---

### Post by Ronin_301 on 2010-02-10
> **damnated said:**
> I'm using the latest build.

Please read what i wrote and don't start talking about the weather. 

My problem is that if i change the tag of a file, amarok will use the old tag unless i rescan the whole collection.

Wouldn't that be because the one program you used to change the tag changed the tag associated with the file, but amarok doesn't "know" that it's been changed until it rescans the file?

What if you change the tag, then restart amarok? Does it still not update the tag?

---

### Post by damnated on 2010-02-10
> **Ronin_301 said:**
> but amarok doesn't "know" that it's been changed until it rescans the file?

Exactly. But i could never rescan just one file/folder, hence the problem. 

Restarting amarok doesn't solve anything.

---

### Post by sjonniemac on 2010-03-14
Hi there, 
I'm having the exact same problem - files wont update properly unless re-scanned, (artist showing as UNKNOWN) even though ID3 tag is just fine.. using amarok 1.4.1

Found any solutions yet?
Thanks

---

### Post by damnated on 2010-03-14
Actually, I've switched back to 1.4 and got rid of this issue, as 1.4 updates everything almost instantly. For me at least.

---

### Post by kelt65 on 2012-10-06
Same problem here with 12.04 LTS / Amarok 2.5.0

---

### Post by wildmanne39 on 2012-10-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

