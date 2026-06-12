---
title: "Amazon Instant Video no longer works in 12.04?"
date: 2012-08-04
forum: Multimedia Software
---

### Post by SeijiSensei on 2012-08-04
I have been an Amazon Prime member for quite some time and was pleased when they made a bunch of their streaming media available for free to Prime members.  I've watched a number of movies there over the past few months, until the other night.

Now I get a error message saying that I need to upgrade my version of Flash.  Of course as we all know, there are no later versions of Flash for Linux besides 11.2 r202 that is in the partner repository packaged as "adobe-flashplugin".  That's because Adobe has discontinued its support of Flash on the Linux platform.

I tried installing the version of libflashplayer.so that's available on Adobe's site.  The version I downloaded (in the tar.gz package) was **10**.2, a full version behind the one in the repositories.  Nevertheless I soldiered onward and tried to watch a movie with that version of Flash.  This time Amazon tells me I need to upgrade my version of Flash and my browser!  

While I await a constructive reply from Amazon support (the last one was largely boilerplate), I thought I'd ask whether anyone else here has tried to watch an Instant Video from Amazon lately?  Am I alone in having this problem?

---

### Post by SeijiSensei on 2012-08-04
Amazon reports they now requires Flash 11.3 which is a version we will never see.  They sent me some alternatives which I'll try in the next day or two.

---

### Post by papibe on 2012-08-04
:(

I'm looking forward to hear from you on how those alternatives work.

Regards.

---

### Post by ufugu on 2012-08-06
I haven't had a chance to try it yet, but [here is a possible solution.]("http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=1&cdSort=newest&cdThread=TxFTGOK5LRL3JM")

---

### Post by SeijiSensei on 2012-08-06
Yes, the solution is to install the deprecated hal and libhal1 packages.  It apparently has something to do with DRM.  After "sudo install hal libhal1" I can now watch Instant Videos again.

That said, what will happen when sites require future versions of Flash (11.4, 12.x, etc., etc.), and we're still left with 11.2 as the final (and broken) Flash version?  This is a solution, but not one that makes sense in the long term.

The realistic long-term solution is to continue to pressure content providers to adopt HTML5-based video streaming.  Flash should die.

---

### Post by ufugu on 2012-08-07
Yep, tried it last night on a few machines and it worked.

> **SeijiSensei said:**
> 
The realistic long-term solution is to continue to pressure content providers to adopt HTML5-based video streaming.  Flash should die.

Agreed.  And meanwhile, companies like Amazon should at the very least put hack solutions like this in an FAQ.

---

