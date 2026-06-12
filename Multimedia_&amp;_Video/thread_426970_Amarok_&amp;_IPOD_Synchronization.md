---
title: "Amarok &amp; IPOD Synchronization"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by jose_ramirez on 2007-04-29
Hi,

I'm able to open my 80 GB IPOD with Amarok, no problems. My question is the following: how do I sync Amarok & my IPOD? All my music files are on /home/jose/my_music. What I'm looking is to automatically update my IPOD every time I add a new file to my music folder (just like iTunes). Is this possible?

Regards,

Jose

---

### Post by ratbagradio on 2007-04-29
I'm not sure what you are after...but if you want to automatically import your music files into Amarok use the "files" left panel window and import your folder that way:
<i>/home/jose/my_music</i>.
You can do it that way or import the music files by making your folder a bookmark address.Either method works for my podcast downloads which update daily. I find "playlists"  won't  handle  changes to the folder, so I never use them on any music manager.

Then it's a simple drag and drop to pull your music into the sync window. and then proceed from there. Since I had trouble sync-ing to my iRiver I cannot advise you there on in but one day I'll get Amarok to sync.

If your files appear as file names in the left panel, if you "load" the lot(either as "load" or drag and drop) the ID tags will be displayed in the right column.

The good thing about Amarok's file handling is that you can manipulate and delete files from within these panels rather than simply play around with playlistsas other media players I've used do.

---

### Post by jose_ramirez on 2007-04-29
Ummm, well, let me explain with an example:  let's assume that I just have two songs in my IPOD: song1.mp3 and song2.mp3. In my /home/jose/my_music I also have song1.mp3 and song2.mp3. Now I add song3.mp3 to my /home/jose/my_music folder and then connect my IPOD. I want Amarok to automatically import song3.mp3 to my IPOD... is this possible?

Thanks in advance...

---

### Post by aroch1 on 2007-04-29
I don't believe so...I think that you just have to transfer new files manually.  I've been using AmaroK+iPod for quite some time, and I haven't been able to find that feature either.

---

### Post by Ephry on 2007-05-02
I have been playing around with Amorok and Rhythim box for the past week, and I quite like Amorok better. Rhythim box seems to be more Itunes oriented though, and I am able to connect to my Ipod right away. 

Like Jose, I am interested in finding a way to sync or transfer files from my laptop to the Ipod. I have almost 14g of music files, and well, you know how that goes. I don't mean to hijack the tread, but I wanted to know which music formats work better for this, and also how to transfer the files to the Ipod from my laptop's music folder. Any inputs? 

Thanks in advance.

E

---

### Post by Ephry on 2007-06-08
Anyone?


E

---

### Post by L1vingd3ad on 2007-06-09
Have you tried gtkpod yet??

> What can gtkpod do?

gtkpod allows you to

    * Read your existing iTunesDB (i.e. import the existing contents of your iPod including playcounts, ratings and on-the-go playlists).
    * Add MP3, WAV, M4A (non-protected AAC), M4B (audio book), podcasts, and various video files (single files, directories or existing playlists) to the iPod. You need a third party product to download podcasts, like 'bashpodder' or 'gpodder'
    * View, add and modify Cover Art
    * Browse the contents of your local harddisk by album/artist/genre by adding all your songs to the 'local' database. From there the tracks can be dragged over to the iPod/Shuffle easily.
    * Create and modify playlists, including smart playlists.
    * You can choose the charset the ID3 tags are encoded in from within gtkpod. The default is the charset currently used by your locale setting.
    * Extract tag information (artist, album, title...) from the filename if you supply a template.
    * Detect duplicates when adding songs (optional).
    * Remove and export tracks from your iPod.
    * Modify ID3 tags -- changes are also updated in the original file (optional).
    * Refresh ID3 tags from file (if you have changed the tags in the original file).
    * Sync directories.
    * Normalize the volume of your tracks (uses mp3gain or the replay-gain tag)
    * Write the updated iTunesDB and added songs to your iPod.
    * Work offline and synchronize your new playlists / songs with the iPod at a later time.
    * Export your korganizer/kaddressbook/thunderbird/evocalendar/evolution/webcalendar... data to the iPod (scripts for other programs can be added).

Should be able to using synaptic.

---

### Post by complexgeek on 2007-06-21
So Amarok can't automatically sync my music library on my PC to my iPod? That's annoying. So if I use gtkpod, does that mean I then have to export any playlists I create in Amarok, export them to gtkpod, then sync the iPod?

---

### Post by wild_oscar on 2007-06-21
> **complexgeek said:**
> So Amarok can't automatically sync my music library on my PC to my iPod? That's annoying. So if I use gtkpod, does that mean I then have to export any playlists I create in Amarok, export them to gtkpod, then sync the iPod?

I have also the same problem. One interesting feature of Amarok is to filter the collection to "Added today" or "Added this week".

I believe you can click on that filter and then just drag all the contents to the "devices" (bottom left corner) and click "transfer".

It is close to auto sync. Only problem I have is that updated files are already present in my Ipod and I cant update them (e.g, files with updated id3 tags).

Help on the latter issue would be greatly appreciated!

---

### Post by wild_oscar on 2007-06-26
Basically, Amarok is good to send music to the ipod but simply does not work if we want it to manage our music library in ipod...

---

### Post by Do0odz on 2007-07-04
Can anyone please tell me how to transfer music from an ipod to amarok ?

---

### Post by abhiroopb on 2008-03-08
easiest thing to do:

1. Turn on Amarok
2. Connect iPod to computer.
3. Look for a "Devices" tab on the left pane.
4. Click "Connect" which is on the top left corner (just under Engage, Playlist, etc.)
5. the iPod should connect in a couple of seconds.
6. Then go to "Collection"
7. Right click on any song that you would like to transfer and click "Transfer to Media Device"
8. Then go to the Devices tab and select the files that you would like to transfer (a pane just below your iPod's contents should have opened up)
9. right-click and click start transfer

Let me know if that works (has worked for me Ubuntu 7.10, iPod classic 80gb, Amarok 1.4.8)

---

