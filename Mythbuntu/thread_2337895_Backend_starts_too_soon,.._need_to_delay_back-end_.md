---
title: "Backend starts too soon,.. need to delay back-end service start"
date: 2016-09-22
forum: Mythbuntu
---

### Post by diyhouse on 2016-09-22
As per Title,... I have found many articles on the net in different forums,.. but I am still lacking some key information,... which I would greatly appreciate some clarification on.

I have Clean build 16.04 Mythbuntu system,.. with an imported Dbase from 0.27,... ( Quad TBS FreeView, and Dual Satellite tuners ).

I have found the following code to create some rules for udev..... 

Now my first question,.... if ( as this script will do ) I change the tuner device file names,... I assume I will then have to re-map them in Myth-backend,.. and perform a retune ( a pain yes,.. but I don't really want to second guess this as it takes a long time to perform a retune ),.. but why do I need to change the device names, what is wrong with /dev/dvb/adaptor[0-5].... that the TBS driver creates by default.

And the next question is how does this script help me?,... does the creation of this script mean the boot process waits for the devices to be created before continuing to boot... or do I then have to create some additional stanza stuff in the back-end init process.... (as I believe I did with 14.04 ).

Thanks for reading and any pointers you can give me....


> [COLOR=#000000][FONT=&amp]# Create a symlinks for both [/FONT][/COLOR][COLOR=#417394][FONT=&amp]tuners[/FONT][/COLOR][COLOR=#000000][FONT=&amp] of TBS device[/FONT][/COLOR]SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}!="two", ENV{tbs}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}=="two", ENV{tbs}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs2/%%s $${K#*.}'", SYMLINK+="%c"




---

### Post by yonkiman on 2016-09-28
I had a similar problem - see if this helps:
[https://ubuntuforums.org/showthread.php?t=2320224&p=13472538#post13472538](https://ubuntuforums.org/showthread.php?t=2320224&p=13472538#post13472538)

---

### Post by diyhouse on 2016-09-29
Many thanks Yonkiman,..  I have followed the thread you comment about,.. and this has given me some more ideas/questions..... My network comes up fine,...even with my SSD system,.. it the TBS tuner  cards that fail to load before the backend starts,... So basically the udev stuff ( as far as I can see ), is a red herring... the true solution lies with one of the statements I see in the myth-backend.service file,..   

After=mysqld.service network.target

Is there an equivalent command I can call upon to wait for the TBS cards to load.

ie something like 

After=TBS-Tuner.service    ( I have no idea what the actual command is ) can anyone help, or is this wishful thinking..

As "I assume",.. the myth-backend service waits for mysql.service and network.target to start before initiating a Myth-backend start-up...

---

### Post by diyhouse on 2016-10-03
Finally found the answer,.. ( to the ultimate question),.. here:-

[https://forum.mythtv.org/viewtopic.php?f=29&t=1148&start=15](https://forum.mythtv.org/viewtopic.php?f=29&t=1148&start=15)

But basically two steps,...  a udev statement

> ## Create systemd device units for capture devices
#
SUBSYSTEM=="video4linux", TAG+="systemd"
SUBSYSTEM=="dvb", TAG+="systemd"
SUBSYSTEM=="firewire", TAG+="systemd"


and adding to the myth system service rule.. 

> [Unit]Description=MythTV backend service
Wants=mysql.service dev-dvb-adapter0-frontend0.device dev-dvb-adapter1-frontend0.device dev-dvb-adapter2-frontend0.device
Wants=mysql.service dev-dvb-adapter3-frontend0.device dev-dvb-adapter4-frontend0.device dev-dvb-adapter5-frontend0.device
After=mysql.service dev-dvb-adapter0-frontend0.device dev-dvb-adapter1-frontend0.device dev-dvb-adapter2-frontend0.device
After=mysql.service dev-dvb-adapter3-frontend0.device dev-dvb-adapter4-frontend0.device dev-dvb-adapter5-frontend0.device




---

