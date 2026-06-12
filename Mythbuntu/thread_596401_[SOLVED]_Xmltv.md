---
title: "[SOLVED] Xmltv"
date: 2007-10-29
forum: Mythbuntu
---

### Post by weiser on 2007-10-29
Hey,

I have now for some days, being figthing with Mythbuntu. Trying to get myth to work with XMLTV.

I live in Sweden and need XMLTV to get the EPG down. But I can't seem to get it to work.

I have tryed to install Mythbuntu with XMLTV under the installation. Not working!
I have tryed to reinstall XMLTV right after. Not working!
And last I have tryed to install it without XMLTV, and install it after. Not working!

I can find all the tv_grap_* in /usr/bin/ but not in Mythtv backend under Video source setup.

What am I doing worng?

Pease help,

Best regards,

Kim

---

### Post by faffaz on 2007-10-29
Same problem here! What is up with that?

---

### Post by axelsvag on 2007-10-30
I also live in sweden and I got almost everyting working. First I must ask you if you use the final release?

---

### Post by weiser on 2007-10-30
Hey,

I have now checket it out. And it is the final release. So I don't know what to do.


Kim

---

### Post by axelsvag on 2007-10-31
That was strange. In the RC the xmltv did work in the installatuion but in the FR it was perfect. 
OK you say it doesn´t work what do mean? Do you see that it is installed in the synaptic? 
Do you see it show up in the mythtv backend videosource/grabber? And if it works so far you should be able to go back to the terminal after have been choosen the right grabber with Alt+Tab. In the terminal you should be able to define what channels you want to choose. please report how far you have come.

---

### Post by weiser on 2007-10-31
I have just downloadet the md5sum from mythbuntu.org to check it up against my .iso file, it says it is the right one. So it is to FR i'am running.

And I can see in Synaptic that XMLTV is installet. 

I can't chose it under the Mythbackend setup under "Video sources", I can chose:
North America (SchedulesDirect.org) (Internal), Transmitted guide only (EIT) and No grabber.

Furter more kan I see in the terminal running behind the Backend setup:

tv_find_grabbers exited early or we timed out waiting.

If I run tv_find_grabbers it finds the grabbers, but I don't know if it is too slow. It takes about 35 sek to find them all. 
I have just tryed it on my running mythtv, that one is not faster to find them!

:confused:
-- 
Kim

---

### Post by axelsvag on 2007-10-31
This is very mysterious. If you just see what you see all signs indicates that  XMLTV is not installed. 
Maybe someone else here on the forum have seen this anomali. Mythtv should get the xmltv info automatic. The last way out is to reinstall the final release but wait  a few days maybe someone have seen this before. You don´t do anything wrong as far as I know and I mean that the new combinergrabber  is wonderful to work with especially since swedb is missing a lot channels in my cable net so you have really something to look forward too.

---

### Post by superm1 on 2007-10-31
For posterities sake you can go out and reinstall xmltv
```
sudo apt-get install --reinstall xtmlv
```

But i would be leaning to issues with that time it's taking.

Also remove ~/.xmltv and /home/mythtv/.xmtlv if they exist before starting.  

Lastly look at logs from mythbackend as well as mythtv-setup when you are running through.

---

### Post by weiser on 2007-10-31
Hey

First of all axelsvag, thanks for trying.


And now for Superm1


~/.xmltv did exist so I have removed it, there was no /home/mythtv/.xmltv

And then I reinstallet xmltv, but no different. 


I have looked into the log for mythbackend, nothing about xmltv or tv_grab*

Here is the output of the terminal when running mythsetup:

[I]2007-10-31 20:37:27.154 Using runtime prefix = /usr
2007-10-31 20:37:27.186 DPMS is active.
2007-10-31 20:37:27.241 New DB connection, total: 1
2007-10-31 20:37:27.267 Connected to database 'mythconverg' at host:
localhost
2007-10-31 20:37:27.271 Total desktop dim: 800x600, with 1 screen[s].
2007-10-31 20:37:27.290 Using screen 0, 800x600 at 0,0
2007-10-31 20:37:27.324 Current Schema Version: 1160
2007-10-31 20:37:27.394 Total desktop dim: 800x600, with 1 screen[s].
2007-10-31 20:37:27.400 Using screen 0, 800x600 at 0,0
2007-10-31 20:37:27.405 Switching to square mode (Mythbuntu)
2007-10-31 20:37:27.471 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
lirc_init failed for mythtv, see preceding messages
2007-10-31 20:37:27.868 Joystick disabled.
2007-10-31 20:37:28.284 Loading from:
/usr/share/mythtv/themes/Mythbuntu/base.xml
2007-10-31 20:37:28.391 Loading from:
/usr/share/mythtv/themes/default/base.xml
2007-10-31 20:37:38.282 New DB connection, total: 2
2007-10-31 20:37:38.284 Connected to database 'mythconverg' at host:
localhost
2007-10-31 20:37:38.291 New DB connection, total: 3
2007-10-31 20:37:38.294 Connected to database 'mythconverg' at host:
localhost
2007-10-31 20:37:38.480 New DB connection, total: 4
2007-10-31 20:37:38.482 Connected to database 'mythconverg' at host:
localhost
2007-10-31 20:37:38.489 New DB connection, total: 5
2007-10-31 20:37:38.490 Connected to database 'mythconverg' at host:
localhost
2007-10-31 20:38:07.375 tv_find_grabbers exited early or we timed out waiting[/I]

-- 
Kim

---

### Post by Notlef on 2007-10-31
First off, I installed on RC so some things might have changed in the final release. These are my notes for getting xmltv to work (in Sweden, comhem), unfortunately my notes are not complete, but they might point you in the right direction.

I found useful information at: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) (section 6.1)
and: 
[http://tv.swedb.se/index.php](http://tv.swedb.se/index.php)

you need to download and configure xmltv-util:
sudo apt-get install xmltv-util

then run:
tv_grab_se_swedb --configure --config-file '/home/yourusername/.mythtv/swedb.xmltv'
say yes to the channels you have

then run:
sudo mythfilldatabase --manual


my list of channels:
E5	1an
E7	2an
E8	4an
E9	3an
E10	24an
E11	Uppsala kanalen
SE10	
SE11	6an
SE13	TV4sport
SE14	MTV
SE15	5an
SE16	barn/kunskap
SE17	TV6(maybe)
SE18	8an
S36	9an
57 	TV4+
66	test kanal e66


as I said, this is NOT an how-to, but could give you some ideas to try!
Good luck!

---

### Post by Nikas on 2007-11-01
Works great for me too. Little time configuring.
I dont use the OTA from "Boxer" (epg här i sverige).
I use only XMLTV. 14 days and more details compared to whats coming in by OTA.

---

### Post by laga on 2007-11-01
If you guys still have problems:

Can you run tv_find_grabbers in a terminal and give us the output?

---

### Post by Nikas on 2007-11-01
I have one small question.
When i run "mythfilldatabase" it does everything for me.
The thing is that it wants to get 15-days of data. The source only has data for 14-days. How can change so that "mythfilldatabase" only requests 14-days by default..  When i dont use --max-days 14 "mythfilldatabase" tries to get 15 days. I dont want to use "--max-days" :)

---

### Post by weiser on 2007-11-02
Hey all,

Sorry for not writing back the last days. But I have being out of house. 

I got a littel tried of my test computer, so I switched the HDD in my main mythtv and installet mythbuntu. 

On this one it just work out of the boks (XMLTV) but here the tv card dosent work. But that is another storey. 

I dont know why xmltv dont work onit I dont know.


Thanks for all the help.


Kim

---

### Post by georg@gac.no on 2007-12-28
>
>Re: Xmltv 
>
>--------------------------------------------------------------------------------
>
>I have one small question.
>When i run "mythfilldatabase" it does everything for me.
>The thing is that it wants to get 15-days of data. The source only has data for 14-days. How can change so that "mythfilldatabase" only requests 14-days by default.. When i dont use --max-days 14 "mythfilldatabase" tries to get 15 days. I dont want to use "--max-days" 
>
>========================================
>

Sorry if this has been answered already, but I had the same problem, and haven't found any smooth solutions. I'm using tv_grab_no_gfeed.

I tried fiddling around with 'MythFillDatabaseArgs', but didn't get mythfilldatabase to work any differently. I probably didn't get it..

I've solved it the cruel way by creating a script '/usr/bin/mythfilldatabase.14' containing the following:

==
#!/bin/sh
/usr/bin/mythfilldatabase $@ --max-days 14
==
(Remember to create it as root and 'chmod 755 mythfilldatabase.14'..)

..and I've set 'MythFillDatabasePath' to '/usr/bin/mythfilldatabase.14'

Regards,
Georg

---

### Post by Nikas on 2007-12-28
> **georg@gac.no said:**
> >
>Re: Xmltv 
>
>--------------------------------------------------------------------------------
>
>I have one small question.
>When i run "mythfilldatabase" it does everything for me.
>The thing is that it wants to get 15-days of data. The source only has data for 14-days. How can change so that "mythfilldatabase" only requests 14-days by default.. When i dont use --max-days 14 "mythfilldatabase" tries to get 15 days. I dont want to use "--max-days" 
>
>========================================
>

Sorry if this has been answered already, but I had the same problem, and haven't found any smooth solutions. I'm using tv_grab_no_gfeed.

I tried fiddling around with 'MythFillDatabaseArgs', but didn't get mythfilldatabase to work any differently. I probably didn't get it..

I've solved it the cruel way by creating a script '/usr/bin/mythfilldatabase.14' containing the following:

==
#!/bin/sh
/usr/bin/mythfilldatabase $@ --max-days 14
==
(Remember to create it as root and 'chmod 755 mythfilldatabase.14'..)

..and I've set 'MythFillDatabasePath' to '/usr/bin/mythfilldatabase.14'

Regards,
Georg

Thank you for your answer.
I did end up with nearly the same solution as you.
I'm running some scripts every night (backups and more).
At the same time i run mythfilldatabase --max-days 14 --refresh-all (refresh-all is allowed for the swedish source)
This brings all my data up to date and even the changes in the program listnings.

---

