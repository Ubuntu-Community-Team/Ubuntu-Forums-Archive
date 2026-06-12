---
title: "upnp server to dsm 320"
date: 2007-12-01
forum: Mythbuntu
---

### Post by angelsneverdie on 2007-12-01
i've seen other posts that say i can stream music with mythtv to my dlink dms 320 - i've installed mythtv and can't figure **** out.  i don't know how to tell it where my music files are, or how to tell it to serve them or anything.

as you can tell, i'm a huge noob 
can anyone tell me what i have to do to get this to work?
i'm running gutsy

---

### Post by superm1 on 2007-12-01
By default mythmusic uses /var/lib/mythtv/music.

Put your music in there, and then go into the musicbrowser for mythmusic make sure it works.

As for getting it going with UPNP, I want to say it will automatically export from the backend, but don't know for sure.

---

### Post by angelsneverdie on 2007-12-01
what do you mean by export?

---

### Post by angelsneverdie on 2007-12-01
also, i transfered a folder of some music into the directory you specified, but it doesn't show up when i start the mythtv frontend

---

### Post by superm1 on 2007-12-02
Go into the settings menu and choose the music related option and with any luck it should generate a playlist based upon your selection.

---

### Post by angelsneverdie on 2007-12-02
no such luck.  :-(

are there any other options that mythtv for streaming music via upnp?

---

### Post by superm1 on 2007-12-02
Are any things being exported?  Like your recordings?

---

### Post by angelsneverdie on 2007-12-02
i still don't know what you mean by exported.  i don't have any recordings. . . i don't even have a tv tuner, i just want to stream my mp3's so that my d-link media player can play them

---

### Post by superm1 on 2007-12-02
Take a look here:

[http://www.mythtv.org/wiki/index.php/UPnP](http://www.mythtv.org/wiki/index.php/UPnP)

and 

[http://www.mythtv.org/wiki/index.php/DLinkDSM520-UPnP](http://www.mythtv.org/wiki/index.php/DLinkDSM520-UPnP)

particularly.

You need to make sure you have setup an external IP address in mythtv-setup if things are to be exported.

> 
[LIST]
[*] Make sure you set the proper external IP in mythtv-setup, otherwise you will be able to see your server via UPnP, but the file location urls will contain the default 127.0.0.1 IP address.
[*] Make sure you have a value for MusicLocation set for your backend hostname if your frontend and backend are on different machines[/LIST]

Exporting means "showing up" on the other machines such as your dsm-320.

---

### Post by angelsneverdie on 2007-12-02
alright, i set the ip address and still nothing shows up either on this computer or on the dlink thing.  i think i'm just going to uninstall everything and buy a wireless adapter for my speakers.

thanks for trying to help me

---

### Post by viper4 on 2007-12-23
Hey. Try installing gmediaserver. That's what I use and it works, same model - DSM 320. The way you use it is by doing Alt+F2 and then type 'gmediaserver /path/to/your/music' - without the quotes.

Hope this works for you.

---

### Post by mechgt on 2007-12-23
I installed MythTV, MythVideo, & MythMusic on a Gutsy machine, and am able to watch all of my movies & music on my D-Link DSM-520.  I added a link to my music folder (on another HDD) under the /var/lib/mythtv/music folder... same for my videos.  Probably the main thing that I did was to change the backend IP from 127.0.0.1 to 192.168.0.x (backend server's IP address).

Functionally everything works fine, however the sorting is quite lacking.  On the D-Link go to 'Music' and my options are 'All Music' & 'By Album'; either of which would take a week to scroll through to find the music I want to listen to.  Same goes for Videos... 'Genre', 'Country' & 'All Videos' are the options.  

I need a better way to find the music and movies I want... like a folder structure.

---

