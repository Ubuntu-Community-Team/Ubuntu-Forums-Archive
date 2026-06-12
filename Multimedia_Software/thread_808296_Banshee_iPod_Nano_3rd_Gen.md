---
title: "Banshee iPod Nano 3rd Gen"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Houli on 2008-05-26
How do I get a 3rd generation iPod Nano to work with Banshee or are there any other music players that work with this version of iPod? It comes up with a unable to launch DBUS. Help!

---

### Post by hellomoto on 2008-05-26
rhythmbox will detect and load your ipod. :)

also GTKpod will allow you to import/export music/pictures etc to your ipod.

both of these can be found in synaptic package manager.

go to:

system>administration>sysnaptic package manager

open a search box and type:

rhythmbox

then after installing that:

GTKpod

enjoy :)

---

### Post by Houli on 2008-05-28
Now Rythmbox messed up my iPod none of the songs apppear anymore. I tried reinstalling it but that didn't work. When I was transferring songs onto it one of them failed and my iPod became unmounted. I had to pull out the cable even though it said do not disconnect. This might have messed it up. This is different iPod FYI it's a 2nd Gen Nano.

---

### Post by Kazuki Mishima on 2010-09-23
I also use a 8GB third-generation iPod Nano, and Rhythmbox seems to have destroyed its database. I used to use gtkpod and it did the trick, but I didn't like the way it handled cover art and metadata editing, and loading the same device in both gtkpod and iTunes caused some weird glitches, so I switched over to using only iTunes on Windows Vista. This meant loading new music from my Ubuntu system onto a flash drive anytime I wanted to add something to my iPod, but it worked well enough - until iTunes started crashing on every startup, despite repeated updates, uninstallations, and re-installations. Then I tried Rhythmbox back on my Ubuntu system, which seemed to work well until I ejected my iPod, turned it on, and saw "No Music" displayed on the screen.

Later tonight I'll try Banshee on for size, and I'll post the results.

A side note: gtkpod asked me not only for the model, generation, and capacity of my iPod, but also for its color, which apparently makes a difference in terms of the database structure. Mine's black, in case that matters.

---

### Post by Kazuki Mishima on 2010-09-23
Well, I've just tried Banshee. It imported all my music from Rhythmbox for me. Before syncing all my music to my iPod (again the 8GB 3rd generation Nano), I went into the iPod_Control directory on the iPod and deleted all the music. I also rooted through the subdirectories and deleted anything that might be databases for music or album art. After that the syncing was incredibly smooth. Banshee took care of all the album art for me and even converted a few Vorbis files to MP3 format for me. (I had changed the settings; the default is to convert to PCM.) I'm impressed. I may even ditch Rhythmbox.

---

