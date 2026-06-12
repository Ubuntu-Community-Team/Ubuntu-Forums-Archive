---
title: "Question  about setup of Ubuntu + Kismet + Earthmate LT-40 GPS"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by rustondriv on 2009-09-06
Hello, 
 
I have done some googleing around but havent had much luck so i thought I would ask the experts. I am trying to use my gps with kismet to get a wap layout of my service building.
 
I am running Ubuntu 9 + kismet latest build. 
 
I just purchased a Delorme Earthmate LT-40 usb gps. 
 
I plugged it in to my computer and installed gpsd and gpsd-client. 
 
I enabled GPS in the kismet conf file. 
 
I tried the following commands before starting kismet but none have worked so far. 
gpsd -n -D2 emate 
gpsd Eart Mate 
 
 
I am familiar with linux but not with using a gps. Can anyone lend some advice to make this gps work with kismet. Thanks for your help.

---

### Post by rustondriv on 2009-09-06
I had tried accessing the usb directly before using the following command:


gpsd /dev/ttyUSB0

It did work after rebooting. So for anyonelse trying to get this to work, try the above command. (You may have to sudo as i do to make it work but it does work)

Thanks

---

