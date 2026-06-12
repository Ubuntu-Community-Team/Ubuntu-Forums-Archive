---
title: "Lossless H264 Transcode from within Myth GUI??"
date: 2009-12-26
forum: Mythbuntu
---

### Post by SiHa on 2009-12-26
I would like to keep some BBC-HD recordings from Christmas (like The Grufallo), but remove the leading and trailing rubbish.

Unfortunately, using the standard transcode jobs, but set to 'Lossless' reports an error, and from the backend log, it seems to be that H264 is an unsupported codec.

Is there an easy way I can do this as a user job? I really don't want to be messing around with the command line, I'd like something that I can use by just setting the cutpoints with the edit function then running the userjob.

TIA,

Simon

---

### Post by nickrout on 2009-12-26
> **SiHa said:**
> I would like to keep some BBC-HD recordings from Christmas (like The Grufallo), but remove the leading and trailing rubbish.

Unfortunately, using the standard transcode jobs, but set to 'Lossless' reports an error, and from the backend log, it seems to be that H264 is an unsupported codec.

Is there an easy way I can do this as a user job? I really don't want to be messing around with the command line, I'd like something that I can use by just setting the cutpoints with the edit function then running the userjob.

TIA,

Simon

Try this script:

[http://monopedilos.com/dokuwiki/doku.php?id=hdpvrcutter.pl](http://monopedilos.com/dokuwiki/doku.php?id=hdpvrcutter.pl)

or read this thread

[http://www.gossamer-threads.com/lists/mythtv/users/400227](http://www.gossamer-threads.com/lists/mythtv/users/400227)

---

### Post by SiHa on 2009-12-26
Now *that* looks promising, thanks!

---

### Post by nickrout on 2009-12-26
please note I edited the above post to link to another thread in the mailing list.

Also this is the thread I saw the hdpvr-cutter mentioned in:

[http://www.gossamer-threads.com/lists/mythtv/users/412997](http://www.gossamer-threads.com/lists/mythtv/users/412997)

---

