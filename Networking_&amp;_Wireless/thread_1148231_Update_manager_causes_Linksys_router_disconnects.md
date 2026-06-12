---
title: "Update manager causes Linksys router disconnects"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by IainStrachan on 2009-05-04
Hi, 

I tried this in the "absolute beginner talk" forum as I'm a newbie but got no response; perhaps this is the correct forum.

I installed Ubuntu 9.04 successfully on my Dell Dimension 310.  I used the "install within windows" option because there were problems in the partitioning of the disk.

Everything works fine with the irritating exception that the update manager seems to cause my Linksys WAG 200G router to disconnect regularly.  I am using a wired connection to the router as this is the main computer.

The problem seems to occur when update manager or the apt-get command has to download multiple files.  During these downloads, my router frequently indicates that it has disconnected from the ADSL broadband (the "Internet" light on top of the router goes red).  It reconnects after a minute or so, but the download remains stalled; I have to exit and restart.

I think it seems to occur when it's finished downloading one file and is about to start on the next.  This will happen about once a minute during an update download.

By contrast, single file downloads are showing no problems, and no such problems occur on XP (for example I downloaded the entire 9.04 ISO image of 700 Mbytes without problems.

Can anyone help?

---

### Post by IainStrachan on 2009-06-10
Still looking for a solution to this problem.

Hope it's not a breach of etiquette on this forum to bump a thread up to most recent.

Iain

---

### Post by thanhngo on 2009-12-21
I've got the same problem. I'm using Ubuntu 9.10. The problem also happens when I open many tabs in the browser.

---

### Post by kevin_hill on 2010-04-02
Hi,

Did either of you find a solution to this problem. I seem to be facing the same problem.

Any download and the router disconnects in under a minute. I  practically cannot download anything from the Ubuntu 9.1 setup. :(

I find this totally strange. Why should my Linksys router behave erratically just because a Ubuntu 9.1 OS is connecting to it ? Does anyone have any ideas ?

regards,
Kevin

---

### Post by thanhngo on 2010-04-02
I use ndiswrapper instead of the default driver and it works just fine.

---

### Post by kevin_hill on 2010-04-04
Hi,

Thanks, Is there some place I can get a step by step on how to follow that route ?

regards,
Kevin

---

### Post by thanhngo on 2010-04-04
google for "install ndiswrapper ubuntu" then you can go to the first result. You need the Windows driver of your wireless card to use with ndiswrapper.

---

