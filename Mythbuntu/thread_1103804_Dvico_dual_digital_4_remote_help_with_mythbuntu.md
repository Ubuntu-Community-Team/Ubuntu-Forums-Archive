---
title: "Dvico dual digital 4 remote help with mythbuntu"
date: 2009-03-23
forum: Mythbuntu
---

### Post by spleblem on 2009-03-23
hey guys, im new here
i have just finished building and still trying to set up my new media pc running mythbunutu 9.04, with a dvico dual digital 4 rev2 non-MCE remote.
looks like this
[http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg](http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg)
i have got the tuner to work, but can't get the remote to work.

when i run
dmesg|grep DVB
i get the line like 
"input: IR-receiver inside an USB DVB receiver as /class/input/input6"

any help would be great
thanks

---

### Post by enchesss on 2009-03-23
have a look here:

[http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation#Remote_Control_.28Lircd.29](http://www.mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation#Remote_Control_.28Lircd.29)


good luck

---

### Post by spleblem on 2009-03-23
Hi thanks that got the remote working
though not every button is working
volume start and the number buttons are.
can find where to change how the other buttons work.
its using linux input device at the moment and i tried editing the .lircr file but that didn't change anything. 
any help would be great
thanks

---

### Post by enchesss on 2009-03-24
Sorry.

Cant help with those specifics.

As a further guide though - what may help is if you use the buttons that do work and then go to the myth setup for your remote and assign the buttons the important commands such as channel up and down.

It is a dirty hack but you usually do not need too many buttons.

Hope it helped.


further reading:

[http://ubuntuforums.org/showpost.php?p=6941074&postcount=115](http://ubuntuforums.org/showpost.php?p=6941074&postcount=115)

---

