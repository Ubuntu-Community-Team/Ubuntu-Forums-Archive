---
title: "How to install Media Device Support in Amarok2"
date: 2008-12-03
forum: Multimedia Software
---

### Post by shizow on 2008-12-03
Hi 
i just installed Amarok2 in Intrepid?
How can i access Media Devices, do i have to install an extra package?

---

### Post by shizow on 2008-12-22
can anyone help?

---

### Post by cameronsstone on 2009-01-18
Just found this. Click on the "+" on the bottom left of the middle panel to "Add Widgets" or just right click on the middle panel and select "Add Applet". Then click on "Media Devices".

As I understand it, only MTP devices are supported at the moment. I don't have one at present, so all I get is a blank panel about the same size as the "current track info" applet.

---

### Post by dakhath on 2009-05-01
From what I can tell, media devices are already supported.  I'm using Slackware (current-version) and I upgraded from KDE3 to KDE4 recently, and Amarok 2 still recognizes my 80GB iPod Classic.  I'm not certain how different the steps to fix this in Ubuntu would be.

The interface simply seems to be different: the Media Devices applet seems currently only to connect and disconnect iPods, while your actual iPod collection should show in the Collection pane on the left.  You can drag and drop from your current local collection to the iPod from that pane.

In response to your original question, I'm assuming the answer would be to get everything working in Amarok 1 first, so my suggestion would be to remove your current Amarok packages, install an earlier version (like 1.4), get it to recognize your iPod, then upgrade and update to 2.  Once you mount your iPod, you should have access to it in Amarok.

---

### Post by Chronon on 2009-05-02
Amarok2 does not currently support UMS devices (MSC mode instead of MTP).

---

