---
title: "Backup and restore Exif data"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by jackyyong on 2007-10-25
Hi all,

I've been a loyal user of Ubuntu since Draper Drake, so I would consider myself a decently experienced Ubuntu-ian.

Here's my question: I take a lot of pictures with my dSLR, and I do a lot of post-processing before finally storing the pictures in CDs. Before I store them, I would want to make sure that the EXIF data of each JPGs are consistent with the original JPGs that came from the camera. So my question is, how do I do this quickly?

I have tried EXIFTool, but its example is not very useful:

*exiftool -tagsfromfile %d%f.CRW -r -ext JPG dir*

This command assumes that I am copying EXIF data from a **RAW** file located in the same folder. I can't have the same JPG files with the same name in the same folder right?

I have also tried *jhead *and others, but none seem to work properly.

Any help is appreciated for this newbie here. Thanks a lot!

My previous workflow in Windows is by backing up the EXIF data from the original JPGs, post-process them, and then restoring them back using [Exifer]("http://www.exifer.friedemann.info/"). Any equivalent steps in Ubuntu?

P/S: Gutsy RAWKSS!!!

---

