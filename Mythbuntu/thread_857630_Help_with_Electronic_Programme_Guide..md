---
title: "Help with Electronic Programme Guide."
date: 2008-07-12
forum: Mythbuntu
---

### Post by Tim L on 2008-07-12
I have found information on how to set up an Electronic Programme Guide for New Zealand. I can follow all the instruction except for the very last line:

Set myth to execute this command as tv guide grabber "sh $HOME\TVNZ\tv_grabber.sh" 

I assume this goes in the Video Sources Setup? But how and where? Under “Listings grabber” I seem to have only three choices 1. No grabber, 2.North America, 3. Transmitted guide only.

---

### Post by nickrout on 2008-07-13
Perhaps if you tell us where to find the instructions you are following someone ,ay be able to help.

I am very familiar with EPG in NZ and have never seen instructions like that. Can you enlighten me?

---

### Post by Tim L on 2008-07-13
Nickrout Thanks, this is where it came from. It is step 4 I am stuck on.

[http://www.reven.co.nz/xmlTVNZ/Guides/LinuxGuide.aspx](http://www.reven.co.nz/xmlTVNZ/Guides/LinuxGuide.aspx)
xmlTVNZ 

NOTE: This guide assumes you already have Myth TV installed. 
1.Install the mono framework 
Download from: Mono-Project.com 
To get the proper libs in ubuntu you may need to install xsp and xsp2 using synaptic 
2.Install xmlTVNZ 
Download from xmlTVNZ Homepage 
Unzip to $HOME\TVNZ 
Run the xmlTVNZ Command Builder to build the command line you need to grab the channels you want 
3.Create a file to grab the data 
Create a new file called $HOME\TVNZ\tv_grabber.sh 
Copy the output genereated by the xmlTVNZ Command Builder with the prefix "mono" and fix the paths 
Example tv_grabber.sh file 
#!/bin/bash
mono $HOME\TVNZ\xmlTVNZ.exe $HOME\TVNZ\tvguide.xml -days 5 xtra_tv1 xtra_tv2 xtra_tv3 xtra_c4 prime
mythfilldatabase --file 1 -1 $HOME\TVNZ\tvguide.xml
4.Set myth to execute this command as tv guide graber "sh $HOME\TVNZ\tv_grabber.sh"

---

### Post by laga on 2008-07-13
I think you can set that somewhere in the frontend.

---

### Post by Tim L on 2008-07-13
Thanks - but where?

---

### Post by nickrout on 2008-07-13
You really need to run mythfilldatabase manually from a cron job if you want to use that EPG source.

But you could try the source suggested here, there is an almost complete howto in this thread.

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/335365](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/335365)

Read the whole thread though. I am in the process of writing up a HOWTO which I wil publish the url of here when I have finished.

You should also join the mythtvnz mailing list:

[http://lists.ourshack.com/mailman/listinfo/mythtvnz](http://lists.ourshack.com/mailman/listinfo/mythtvnz)

---

