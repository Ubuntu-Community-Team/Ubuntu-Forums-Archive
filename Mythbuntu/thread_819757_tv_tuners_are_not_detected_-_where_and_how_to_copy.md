---
title: "tv tuners are not detected - where and how to copy the firmware file"
date: 2008-06-05
forum: Mythbuntu
---

### Post by styrofoam cup on 2008-06-05
I'm trying to install mythbuntu, but upon setup my tv tuners are not detected. I'm guessing that I have to install the firmware file somewhere [http://www.linuxtv.org/downloads/firmware/dvb-usb-vp7045-01.fw]("http://www.linuxtv.org/downloads/firmware/dvb-usb-vp7045-01.fw")
where does it go to on my system, and can I just skip the setup then copy the firmware files the restart the setup, or will this break the install ????

---

### Post by dvbspider on 2008-06-05
i have same problem with skywalker,, I will like to now If I have to do same..

---

### Post by styrofoam cup on 2008-06-06
OK, I think I have mine working (just waiting for the channels to tune in)

What I did was download the firmware from the web site
[http://www.linuxtv.org/downloads/firmware/]("http://www.linuxtv.org/downloads/firmware/")
and copy it to my usb sitck.
I put the usb stick into the mythbuntu computer and copied the file to the home directory.
Next I started a terminal and did a (cant remember the exact location, use you file browser to have a look)
> sudo cp *.fw /lib/firmware/2.24.?????-16-generic
then reboot, exit the mythtv frontend and start the backend-setup.
the tuners were detected, and are currently tuning in stations.
:guitar: rock on!!

---

### Post by novellahub on 2008-06-06
You can copy the firmware right into /lib/firmware

See this wiki page:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)

It shows the location for copying firmware for other cards.  I have sucessfully used this procedure in the past setting up a Kworld 115 card.

---

