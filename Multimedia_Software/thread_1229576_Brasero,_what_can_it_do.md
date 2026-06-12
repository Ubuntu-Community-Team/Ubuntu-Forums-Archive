---
title: "Brasero, what can it do?"
date: 2009-08-02
forum: Multimedia Software
---

### Post by Howard Kaikow on 2009-08-02
A few daze ago, I created what was alleged to be an ISO 9660 conforming CD-RW.

I used the default CD/DVD writer that popped up when inserting blank media.

Today, I decided to try to create media using the UDF format. The Brasero web site states that it "can burn data CD/DVD on the fly", which means that it is either using UDF, or multisession.

So, I selected a few files, then told Brasero to burn.
I then re-inserted the media  hoping to learn whether it would use UDF or multisession.

First problem was that as soon as system recognized the media, a pop up asked me whether  I wished to import the 1st session. Of course, this gave me my answer, Brasero was using multisession, not UDF.

Unfortunately, the pop up did not stay long enough for me to respond.

So I added a directory, call it A, then I added another directory, call it B, within each directory, I plopped a file.

I then told Brasero to burn.

Then I re-inserted the media.
Brasero could not mount the media.
I moved the media to a CD-ROM drive.
Brasero still could not mount the media.

I said, Oh well, that will teach to not uncheck the box that forces Windows compatability, whatever that means.

I then rebooted my system to Windows. Windows also could not mount the media, but I was able to use [ISO Buster]("http://www.smart-projects.net/isobuster/") to examine the media.

The 1st session was present and I could view the files.

The 2nd session was present, but not correctly recorded. There was a 0 length garbage file, that's all. So session 2 was never completed making the media unmountable.

Is there a document that shows how to use Brasero, and states whether "drag to disk" can be used.

If Brasero will not do this, does Gnomebaker?

I am interested only in a GUI, not a command line way to accomplish this.

I suffered enough developing [High Sierra]("http://www.standards.com/StandardsDownloads/hs.txt"), [ISO 9660]("http://www.standards.com/index.html?HowardKaikow"), and [ISO/IEC 13346]("http://www.standards.com/indes.html#Standards") (on whuch UDF is based), do I really need to suffer more?

---

