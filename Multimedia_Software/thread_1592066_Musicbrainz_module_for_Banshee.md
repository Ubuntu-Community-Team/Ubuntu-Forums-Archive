---
title: "Musicbrainz module for Banshee"
date: 2010-10-10
forum: Multimedia Software
---

### Post by lduperval on 2010-10-10
Hi,

Is there a musicbrainz module available for Banshee? If so, what is it and how can it be installed? I'm on Lynx.

Thanks,

L

---

### Post by lduperval on 2010-10-10
FWIW, I just installed Banshee 1.8 from launchpad, since the Webpage says it supports Musicbrainz. However, I inserted a CD which is found by SoundJuicer but not banshee. I check the Musicbrainz database to make sure, and the content is there.

Any ideas?

L

---

### Post by rwigle on 2010-11-11
I am anxious to hear of progress on this question.

I have a large number of older Naxos CDs and do not look forward to manually entering that much metadata.

I am running Banshee 1.6.1 (from the ubuntu repos) under Lucid, but would upgrade if there was a fix for this issue.

---

### Post by murdos on 2010-11-12
> **lduperval said:**
> However, I inserted a CD which is found by SoundJuicer but not banshee. I check the Musicbrainz database to make sure, and the content is there.

Any ideas?


MusicBrainz may know the contents, but still misses the "DiscId" (a sort of "fingerprint") for the CD, that is used to link contents and CD.
But it's really easy to add it to MusicBrainz from your CD.

SoundJuicer is using both MusicBrainz and FreeDB (by order of preference), that's why SoundJuicer may find it. SoundJuicer should however let you know that it's missing from MusicBrainz, and encourage you to contribute there.

---

