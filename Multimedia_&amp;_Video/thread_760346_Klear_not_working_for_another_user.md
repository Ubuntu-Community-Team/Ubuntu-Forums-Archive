---
title: "Klear not working for another user"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Ganymedes on 2008-04-20
I have got Klear to work in my system (AMD 64) for USB DVB-T device (Afatech 9015 based). 

However, it does not work for another user - it just complains that there is not DVB device present (I have copied the channels.conf -file in directory ".klear").

Also Xine Movie Player does not work for another user. It complains that "no plug-in" for displaying the stream. 

Are there any general instructions how to check and configure the usage for another user? I have tried to check the obvious ones under the user - like the directories .klear and .xine in these cases - but it does not help.

---

### Post by xc3RnbFO8P on 2008-04-20
Did compare /home/your folder/.klear/**klear.conf** and the another user **klear.conf**

---

### Post by Ganymedes on 2008-04-20
Thanks! But I am afraid that it just states some obvious differences. The output of "diff" looks like this:

20c20
< ScreenshotDir=/home/john/Desktop/
---
> ScreenshotDir=/home/jane/Desktop/
24c24
< RecordingDir=/home/john/Desktop/
---
> RecordingDir=/home/jane/Desktop/
29,30c29,30
< CurrentChannel=YLE TV1
< CurrentServiceID=17
---
> CurrentChannel=none
> CurrentServiceID=0
33,34c33,34
< WindowWidth=911
< WindowHeight=615
---
> WindowWidth=594
> WindowHeight=338

The differences seem to be only the working directories and the fact that the user "jane" has never been able to use Klear and thus does not have current channel or serviceID.

What else is there to check?

---

### Post by xc3RnbFO8P on 2008-04-20
I can see you also got problem with Kaffeine,
all Xine related.
Bad install I think.

---

### Post by Ganymedes on 2008-04-21
I did a removal and install to Xine and Klear - it did not change anything. (Totem and Kaffeine are gone at the moment).

It works fine when I scan the channels with the "scan" command and copy "channels.conf" to Xine and Klear. But for another user it does not:

Klear gives an error box stating:
- DVB device not found

Xine gives a box:
- -xine engine error - 
There is no input plugin available to handle 'dvb://YLE TV1'.
Maybe MRL syntax is wrong or file/stream source doesn't exist.


It looks simply that for the other user software does not know where to look for the DVB device/source/stream/whatever it is trying to find first. As for the Xine error message - is that kind of syntax right or wrong - I have no idea?

Perhaps you would need to create ENV variables or something for the other user ... just a wild guess?

And yes, I did have, in another thread, another problem with Kaffeine not scanning correctly, but I think that is something else altogether.

---

