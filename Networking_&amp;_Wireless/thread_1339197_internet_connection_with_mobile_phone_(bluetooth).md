---
title: "internet connection with mobile phone (bluetooth)"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by jpgeerets on 2009-11-27
hi folks,

i have my ubuntu910 laptop connect to my mobile phone with bluetooth.
this all works easy and great.
on my mobile phone i have mobile internet. this works too.

at this moment i want to connect my laptop to my mobile phone (with bluetooth) and use this as my internet provider.
but, how can i tell to ubuntu to NOT use wireless or ethernet BUT the bluetooth connection as the internet connection?

someone has done this before?

thanks in advancced!!

Jean-Paul

---

### Post by sakisds on 2009-11-27
I am not sure if you can get it work with bluetooth, but its tested to work if you use your phone cable in modem/pc studio/or whatever mode(Not mass storage or media player). Usually ubuntu will detect it and ask some info from you.

---

### Post by jpgeerets on 2010-01-11
well,

on windows7 this is no problem.
just plug and play.
on ubuntu this is little harder....
somehow ubuntu doesnt know he can access the internet on the cable connection on the mobile phone...

---

### Post by changingstate on 2010-01-11
I have this up and working with my n95.

First, I'm using blueman rather than the default bluetooth stuff, so grab that. :

sudo apt-get install blueman

Once blueman is installed, assuming you've got your bluetooth device setup correctly, the notification area (where network manager lives ) should have a bluetooth icon in it. Left click it to bring up the device list and scan for new devices. You should see you phone listed.

Pair the phone and the computer, just like you would on windows. I suggest getting them to trust each other, too ( entering PIN's just annoys me ). Once this is done, right click on the phone's icon in the blueman window, and select refresh services. Right click on the phone again, and select 'Serial Port', then 'Dial Up Networking'. The bluetooth icon should get a little green spot on it and you phone's bluetooth should show busy.

Next, right click the network manager icon and go to 'Edit Connections'. Go to the mobile broadband tab and add a connection for your mobile service provider. Then close the window. Left click on network manager icon *and assuming that blueman is still connected to the phone ( it'll be showing the little green spot )* your new mobile broadband connection will be shown. Click it to connect. 

If everything is set up correctly, after a brief pause, you will see network managers icon turn into a little mast to show you are connected. You should now be able to surf to your hearts content.

---

