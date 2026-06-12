---
title: "Pls Help Me !!Sapphire hd2600xt&amp;Ubuntu 7.10 64 bits"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by Dezinteres on 2008-01-02
Hello , 
I have a "little"problem that i cant seem to figure out.I have a sapphire hd2600xt and i am trying to install it under ubuntu 7.10 64 bits .So far i tryed envy ( with envy the direct rendering is always NO )and also i tryed with the driver from ati`s website.( who doesnt seem to work at all ).I am new to linux .. but i really want to give it a try,tho it is kinda hard to do this without a proper install of my graphic card.. so any help is welcome.


Ps : sorry for my english .

LE :I just reinstalled ubuntu .. and if i install envy and the ati driver before the updates from ubuntu .. everything is working ok.I have direct rendering enabled and also desktop efects )If .. i install the updates from ubuntu .. i have direct rendering enabled .. but the desktop efects are gone.Any help on how to have both enabled ? Thank u

adi@ubuntu:~$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7170 Release


adi@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes

adi@ubuntu:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

i have no clue why i cant enable compiz... pls help !

---

### Post by Yellow Pasque on 2008-01-02
```
sudo gedit /usr/bin/compiz
```

Put fglrx in the line that says WHITELIST=" "

---

### Post by Dezinteres on 2008-01-02
Problem solved thanks to Temüjin ! Thank u ;)

---

