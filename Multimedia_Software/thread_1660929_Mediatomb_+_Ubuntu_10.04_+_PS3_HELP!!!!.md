---
title: "Mediatomb + Ubuntu 10.04 + PS3 HELP!!!!"
date: 2011-01-06
forum: Multimedia Software
---

### Post by tku703 on 2011-01-06
Hi all,
I'm having trouble setting up my PS3 media server.  I have Mediatomb installed and I'm running Ubuntu 10.04 Lucid.

I've install ffmpeg, vlc, and many other dependencies via apt-get.

I've updated the ~/.mediatomb/config.xml file with the following:

<protocolInfo extend="yes"/>
<map from="avi" to="video/divx"/>

I've opened a browser ([http://MyServer:49152](http://MyServer:49152)) and added the directory where all my movies are.

Now my PS3 see the new Mediatomb server but when I navigate to the directory, I can't see any files, its says "There are no tracks".  I have both .avi and .mp4 files and none are shown.  Can anyone please, please help and point me in the right direction?  Thanks.

---

### Post by Blues- on 2011-01-06
Drop the database and rescan the directories.
Changes made with the mapping only work with new items being added.

---

