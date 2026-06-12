---
title: "Problem loading songs to ipod from Amarok"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Elotero on 2007-11-29
I get this error when i try and transfer the Queue:

Media Device: Copying file:///path/to/my/music/song.mp3 to 
file:///media/My iPod/iPod_Control/Music/F03/kpod0730089.mp3 failed


I read the other post that sais that the guy solved the problem his self by using Windows and ITunes to retore the ipod to factory settings... what does that mean? Clear out the songs? Because thats what it sounds like.. i wouldnt think that "restore to factory settings" would do anything other than clear everything out... 


Anyone else have this problem? 

All of your help is always appreciated!

---

### Post by Elotero on 2007-11-29
Bumpster... 

Im sure someones had this happen before that can help

---

### Post by abhiroopb on 2008-03-27
don't know if you're problem is solved but you can do the following:

1. connect iPod.
2. Open nautilus (file browser)
3. Click on the iPod icon on the left.
4. Click on iPod_Control
5. Delete the iTunes folder.

What this does is deletes all the database information (NB: NOT THE SONGS THEMSELVES).

6. Disconnect the iPod (properly).
7. Reconnect.
8. Go into Amarok.
9. Go to Devices.
10. Click on connect (like normal, if you have the iPod set up for usage in amarok).
11. An option should appear to rebuild the iPod database.

This should reset everything nicely.

Let me know if this helps!

---

### Post by bfkeats on 2008-04-26
I'm having the same problem. Removing the database didn't help. Anyone?

edit: This problem started after upgrading. Amarok also doesn't autodetect my ipod, I have to add it manually.

---

### Post by abhiroopb on 2008-04-27
If you are using ubuntu and you update kde apps can cause problems. So you should remove them and then upgrade and then re-install.

---

### Post by bfkeats on 2008-04-27
I actually did a clean ubuntu install, then installed amarok so that's likely not it.

---

### Post by bfkeats on 2008-04-28
If I run amarok in a terminal I get:
> kio_file: WARNING: Couldn't write[2]. Error:Input/output error
HELP! I'M CONSIDERING WINDOWS!

edit: similar error in gtkpod,

Transfer of 'Bitter Green' failed. Error while writing to '/media/KEATS'S IPO/iPod_Control/Music/F05/gtkpod569763.mp3' (Input/output error).

---

### Post by abhiroopb on 2008-04-29
That error I have gotten if I did not actually have the song.

---

### Post by gedzilla on 2008-04-29
i had a whole load of problems with my ipod until i found this (can't remember which thread it was posted on, but remembered to bookmark it);

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)


certainly worked with gutsy - not sure about hardy

---

### Post by bfkeats on 2008-04-29
I followed a similar procedure for Gutsy. It seems to be broken in Hardy. I suspect an apple update broke libgpod.

---

