---
title: "6th generaton Ipod Classic with ubuntu?"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Nante on 2008-05-28
Anyone know if there are any serious problems with getting the 6th gen Ipod classics to connect with ubuntu? I want to get a new one but I have been unable to find anything on google about how they sync with ubuntu. Anyone have any first hand experience to guide me?

---

### Post by briandu on 2008-05-28
install gtkpod using synaptic.

Read all about it from gtkpod.org

to quote:
"
gtkpod is a platform independent Graphical User Interface for Apple's iPod using [GTK2]("http://www.gtk.org/"). It supports the first to fifth Generation including the iPod mini, iPod Photo, iPod Shuffle, iPod nano, and iPod Video..

"

Should work methinks!

---

### Post by Thee_Baron_ on 2008-05-28
I used hipo (you can search in synaptic for it) to transfer a couple of tracks to my Classic 160GB, worked perfect and was fast. I would like it more if it had a sync feature. All you do is select the folder/files you want to transfer.

---

### Post by hellomoto on 2008-05-28
I brought a iPod classic 6G 80gb 3 days ago.

here is what i have found out so far:

Connection: Hardy recognized and mounted my ipod automatically.

Its very important to have the libgpod0.6.0 (Its installed with hardy by default).

WARNING: Ejecting your ipod 6G before saving/ejecting properly from GTKpod will result in GTKpod not writing to the music.db file and you loosing all your music! (it will be on your ipod but wont be able to be played). If this does happen the only way to fix it is using apples restore facility. This can be used through itunes. 


Rhythmbox: Loads my ipod automatically.


GTKpod:
-this works for syncing music to your ipod and is quite easy to use.  
-I havn't been able to sync photos onto the ipod via this program. GTKpod can't access the iPod photo.db file.


Album Art:
-the new iPod relies on album art heavily for its GUI. And such features as "coverflow" require album art.
-album art is a great app for linux & windows that allows you to download album art from the net or browse for images on your HD.
-album art embeds the art into the MP3 (which is required to show on your ipod)

Calender syncing with evolution:
To copy my calender to my iPod i navigated to:
/home/name/.evolution/calendar/local/system
Copy the iCal file and then save it to you ipod in the calenders file.


Functions I haven't been able to enable:

Photo syncing with ipod.
Video syncing with ipod.

Usefull links:

[Rhythmbox]("http://www.gnome.org/projects/rhythmbox/")

[album art]("http://www.unrealvoodoo.org/hiteck/projects/albumart/") 

[GTKpod]("http://www.gtkpod.org/about.html")

[6G help]("http://www.downloadsquad.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/")


Hope this helps :)

---

### Post by Nante on 2008-05-28
Thank you all very much, I'm always wary of hardware compatibility, I wanted a Archos 605, but one of my friends bought one and it broke in less than a week and Archos wouldn't give him the time of day, so it's a Ipod for me )

---

