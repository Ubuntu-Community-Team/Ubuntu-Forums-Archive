---
title: "Export recordings"
date: 2010-08-07
forum: Mythbuntu
---

### Post by itlarson on 2010-08-07
I would like to export recordings so I can play them back on a laptop, but am unsure how to proceed.  I installed the mythexport package in Synaptic, but it doesn't show up in the frontend anywhere, and there doesn't seem to be a way to start it.  On wiki said I should go to  [http://localhost/mythexport](http://localhost/mythexport) to configure it, but this just gives a server error message.  How do I make this work?  Is mythexport even the right tool?  The laptop is too old to play back h264 well, and I will need a higher resolution than most of the media devices it seems to work with.

---

### Post by nickrout on 2010-08-07
According to the wiki > MythExport is a script that can be added to MythTV as a User Job and used to export recordings into a format playable on portable devices such as iPod Video, iPod Touch, and PSP. Besides converting your recordings, this script also grabs data from the MythTV MySQL database and injects it as iTunes data into the exported video so that it will show up correctly on your iPod. Now includes RSS feed and daily cleanup functionality. [http://www.mythtv.org/wiki/Unofficial_Plugins](http://www.mythtv.org/wiki/Unofficial_Plugins)

Frankly if your laptop was capable of playing the recorded file you could just copy it over and play it using mplayer or smplayer or whatever you choose.

---

### Post by nickrout on 2010-08-07
Having read this [http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport) I see what you are after.

Have you started the mythexport service? (/etc/init.d/mythexport start)

Are you pointing your browser at the right machine (it will only be localhost if you are accessing it from sitting in front of your backend)

---

### Post by bb_145 on 2010-08-08
Mythexport's strength is for compressing files- particularly if you'd like to put them on a portable device such as an ipod.

If you don't need to compress the file, I find the easiest way is to use Mythweb:  

[http://www.mythtv.org/wiki/MythWeb]("http://www.mythtv.org/wiki/MythWeb")

Just access Mythweb on the laptop.  If you select the recording, there is an option for direct download.

If you would prefer to stream, mythweb can also be set up to stream flash (the option needs to be turned on before it is used), or I find mythtv player works well:

[http://www.sudu.dk/mythtvplayer/index.php?page=download]("http://www.sudu.dk/mythtvplayer/index.php?page=download")

Hope this helps.

---

### Post by itlarson on 2010-08-08
Thanks for the replies.

I definitly need to compress the files, because at 6gb/hr the laptop's hard drive isn't going to go very far.   I was hoping to transcode down to about 1/2 gb/hr.  My understanding is that you can specify the command line of the encoding tool in mythexport.  I was thinking I could use this to specify a less cpu hungry codec than h264.  

Unfortunatly I haven't been able to connect to mythexport.   I can start it sometimes:

 ~$ sudo /etc/init.d/mythexport start
[sudo] password for itl: 
 * Starting MythExport Daemon: mythexport                                       [ OK ] 
itl@itlmyth:~$ pgrep mythexport 
13140

but it seems to crash as before I can to contact it in Firefox.  Most of the time it crashes immediately, and I don't even get a PID when I pgrep.  Does anyone know what is going on?

---

### Post by nickrout on 2010-08-08
presumably it logs somewhere?

---

### Post by bb_145 on 2010-08-08
Try checking the apache log at /var/log/apache2.  I originally had problems with Mythexport (I kept getting a server error message), and I used the logs to eventually track the problem down to the permissions on the Mythexport config files.  (I can't recall the exact details.)

---

### Post by itlarson on 2010-08-09
Sorry- I got derailed by a graphics meltdown on my mythbox- ended up doing a compleat re-install.  Mythexport logs to /var/log/mythtv/mythexport.  I will take another stab at making it work tomorrow.

---

