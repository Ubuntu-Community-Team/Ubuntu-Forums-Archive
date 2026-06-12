---
title: "XMMS Memory Leak?"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by marx2k on 2006-12-11
I go to sleep at night listening to music.  I load up XMMS and begin streaming a shoutcast server @ 128kbps.

Original footprint when just loaded is 1.6MB

8 hours later, XMMS memory footprint is at 460M and growing.

It reverts back to original footprint size when I reload the program.

I'm not sure if the same behavior is seen when playing local files.  I will make an 8 hour playlist tonight of local files and test it out.

Has anyone else seen this behavior before?

---

### Post by Frem on 2006-12-11
I dunno. Does Beep Media Player have the same problem?

---

### Post by marx2k on 2006-12-11
> **Frem said:**
> I dunno. Does Beep Media Player have the same problem?

Unsure. I would have to set up Beep to stream from a shoutcast server overnight.  I can try that after a day or two after I test long-term streaming on XMMS via SAMBA to see if it displays the same problem as via Shoutcast

---

### Post by marx2k on 2006-12-12
After 6  hours streaming over a SAMBA connection, XMMS has a memory footprint of 2.2M

I will try streaming shoutcast with Beep tomorrow night but it does look as though there is a memory issue when streaming Shoutcast with XMMS.

The memory is released immediately when XMMS is reloaded.

---

