---
title: "via rhine 82XX_S3_Unichrome"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by cyfer on 2005-10-13
is there any support for this integrated graphics board "MSI" to enable
the 3d thing 

all help and tutorials goes to ATI & Nvidia ....
what about that unichrome ???

i can't get the blues here ...#3Ddesk#

P.S i know about the flg thing ..but it doesn't work

---

### Post by kakashi on 2005-10-14
here is a part a of what lspci says when i put it in my computer 
> 0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

so i figure i have the same thing as you 
i do have a MSI KM3M-V mainboard with onbaord sound and video 
i do run linux on it but i have never tried to play games using linux 
i don't think 3d acceleration works cuz when it goes to screen saver it starts consuming 100% processing power

also off topic but did you get onboard sound working.

---

### Post by tecantonio on 2005-10-14
yea i agree, i have the same video card, but my mother board is p4vm800 or something like that, and i try to install the driver that is on the page:

[http://www.viaarena.com]("http://www.viaarena.com")

but i can make it work, that is sow bad

---

### Post by cyfer on 2005-10-14
guys ...you should not agree...
i don't know about the sound problem ...cause i never had that before 

look at this to enable the 3d shit on your machines 
it works for me now 

[http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393)

you should look at that part ..about all chips 


```


sudo apt-get install build-essential 
wget [http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2)

wget [http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2)

 tar -xjf common-20050707-linux.i386.tar.bz2 

 tar -xjf savage-20050707-linux.i386.tar.bz2 

 cd dripkg 

 sudo ./install.sh

```
but you should change these to get via drivers like that 


```

sudo apt-get install build-essential 
wget http://dri.freedesktop.org/snapshots/common-20050718-linux.i386.tar.bz2

wget http://dri.freedesktop.org/snapshots/via-20050718-linux.i386.tar.bz2
 
tar -xjf common-20050718-linux.i386.tar.bz2 

tar -xjf via-20050718-linux.i386.tar.bz2 

cd dripkg 

sudo ./install.sh

```
please look at the link i gave you ....i posted you the part you need to get the right driver ..only 

regards

---

