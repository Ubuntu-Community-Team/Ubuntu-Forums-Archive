---
title: "mythfilldatabase question"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by sephirothsigep on 2008-03-12
so up until the lates update of mythtv everything was working great. but now the command that i use to fill my listing with is not working. 

i use to use mythfilldatabase --file 1 -1 /home/me/xmltv.xml

now the only command that i can find that is simular is mythfilldatabase --dd-file <sourceid> <offset> <lineupid> <xmlfile>

now i am guessing that inorder to do what i want i need to use this new command but what is the lineupid.


   <sourceid> = number of the video source to use with this file
   <offset>   = days from today that xmlfile defines
                (-1 means to replace all data, up to 10 days)
   <lineupid> = the lineup id
   <xmlfile>  = file to read

---

### Post by sephirothsigep on 2008-03-27
I have the same problem... you can you the --file <sourceid> <xml-file> command to place your data into the database but this does not allow you to remove old guide data you just have to wait the 7 days for the data to be removed by mythtv on its own. so this willl work but not as nicely as before.

---

### Post by maieutike on 2008-04-29
mythfilldatabase >= 0.21 does not reqiure the offset parameter when called with --file, it now determines the target date from the xml file.

---

