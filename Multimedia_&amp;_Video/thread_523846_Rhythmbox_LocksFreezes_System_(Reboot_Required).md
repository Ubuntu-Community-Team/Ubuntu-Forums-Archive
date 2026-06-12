---
title: "Rhythmbox Locks/Freezes System (Reboot Required)"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by linque on 2007-08-12
I just started using Rhythmbox 0.10.0 on Ubuntu 7.04 (32-bit) to manage my iPod (4th Gen/40 GB). I was transferring my music onto it last night when it locked my system up. I had to reboot to be able to use Ubuntu. I believe it's caused when the iPod is full, and you try to put more songs onto it. There were four or five warning boxes that popped up, but they tiled over each other so I couldn't read them all. The one I did see said that the iPod was full. At this point you can't click anything, or use a terminal to kill the process. CTRL+ALT+DEL, or CTRL+ALT+BACKSPACE does not work, and you have to hold down the power button to force a shutdown.

My setup may differ from the norm in that I have my music stored on an external USB drive. I set Rhythmbox up to monitor that drive for changes, and when I transfer music to the iPod through Rhythmbox (drag and drop) it comes directly from the external drive.

I was able to reproduce the issue the next morning, so I did a quick search in the forums and Google, but didn't find anything. I like Rhythmbox, and would like to use it, so I hope to find a solution.

Here are my specs:

Ubuntu 7.04 32-bit (thanks to Microsoft Vista)
HP Pavillion a1730n / Athlon 4600 dual-core
2 GB RAM
eVGA 7600GT (256MB)

---

### Post by Alexander2007 on 2007-08-12
Sounds like a bug. Try reporting it to: [http://bugs.launchpad.net]("http://bugs.launchpad.net")
You should try Banshee. In my opinion its much better than Rhythmbox.
Its available via "Add/Remove" and "Synaptic".

---

### Post by linque on 2007-08-13
Well, I tried Banshee (version 0.12.1). It looked promising at first, but it won't play podcasts. It will let me subscribe to them (twit, Buzz Out Loud), but when I click them to play, nothing happens. It could be user error, as I've only given it ten minutes or so, but they appear in the list as if I should be able to play them. I also can't drag them to my iPod.

Banshee is also missing the "Browse" feature which iTunes and Rhythmbox have. It's the part at the top that lists Genre, Artist, and Album. It makes it much easier for me to find music.

Thanks for the recommendation, but I think I'll stick with Rhythmbox for now. 

I do have another issue regarding podcasts in Rhythmbox. When I drag them to my iPod they do not show up under the Podcast main directory. I have to go to Music>Genres>Podcasts to find them. Anyone else find a fix for this?

---

### Post by doclivingston on 2007-08-14
> **linque said:**
> I do have another issue regarding podcasts in Rhythmbox. When I drag them to my iPod they do not show up under the Podcast main directory. I have to go to Music>Genres>Podcasts to find them. Anyone else find a fix for this?

It's been fixed in the 0.11.x series, but Rhythmbox 0.10.x doesn't mark them as podcasts correctly.

---

### Post by linque on 2007-08-14
Nice! Thank you!

What's the best way to upgrade Rhythmbox? Is there a .deb package to download, or can I use the Synaptic Package Manager?

---

### Post by doclivingston on 2007-08-15
> **linque said:**
> What's the best way to upgrade Rhythmbox? Is there a .deb package to download, or can I use the Synaptic Package Manager?

The 0.11 series won't be in the official Feisty repositories (it's already in Gutsy). You can probably find a variety of .deb packages by searching the forum.

---

