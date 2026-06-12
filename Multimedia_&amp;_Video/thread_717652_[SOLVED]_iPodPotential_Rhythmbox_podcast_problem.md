---
title: "[SOLVED] iPod/Potential Rhythmbox podcast problem"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Arituay on 2008-03-07
Hello all,

I am able to use Rhythmbox to download podcasts and then drag them into my iPod.  The problem is that when I eject my iPod and try to play the podcasts it doesn't work.  

Specifically when I try to enter the Podcasts menu from the iPod main menu by clicking the center button nothing happens.  To the right it shows that there are 27 podcasts so I don't know why it doesn't respond.

Has anyone had this problem?  How can I fix this?

---

### Post by Arituay on 2008-03-08
Ok, I fixed this.  For anyone that has a similar problem this is how I did it.

1. Plug in ipod (ensure it is mounted)
2. Install Amarok via Synaptic
3. Install libgpod-0.6.0 (had to google it, download, and build since that version isn't in the repos yet)
4. Opened the following Ubuntu menu item System>Administation>System Monitor, go to the File Systems tab and note the DEVICE and DIRECTORY for your ipod (these will be needed for step 5)
5. Ran the following command in a terminal:
    sudo ipod-read-sysinfo-extended DEVICE DIRECTORY


That is what I did and it enabled me to add podcasts to my ipod via Amarok that would actually play.

Now I just need to search for how to make Rhythmbox stop opening automatically when I plug in my ipod.

---

