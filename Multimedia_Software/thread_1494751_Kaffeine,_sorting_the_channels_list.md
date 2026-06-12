---
title: "Kaffeine, sorting the channels list"
date: 2010-05-27
forum: Multimedia Software
---

### Post by photoao on 2010-05-27
I am using Kaffeine with a dvb-s card to receive astra and hotbird channels. There are about 900 free channels available. New channels are regularly appearing and old channels are disappearing. Thus we need to re-scan the satellite channels quite often.

After each scan, the numbers attributed to the channels are modified. This is annoying, since you will need to learn new numbers very often. To eliminate this problem, I wrote a little perl script that sorts the first 50 or 60 channels in the same way, according to a model list I define. Thus the small channel numbers, i.e. the most used channels are always the same.

My personal solution did work with Kaffeine version 0.8 which did store the channels in a text file at .kde/share/apps/kaffeine/channels.dvb . It was easy to sort this text file with a perl script.

Now Kaffeine version 1.0 does not save the channels in a text file anymore, but probably in a db, may be the file is named sqlite.db, but not sure.

How can I visualise the content of this db file and finally sort it to my liking with a perl script or another script ?
Thank you

---

### Post by speedbaron on 2010-07-12
The quickest way is to rename the sqlite.db file in the location '~/.kde/share/apps/kaffeine'.  Also rename the scanfile.dvb file.  
Close Kaffeine before to rename the files.  After renaming the file, restart Kaffeine and rescan the channels.

---

