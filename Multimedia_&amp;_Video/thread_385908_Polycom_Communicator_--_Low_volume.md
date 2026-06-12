---
title: "Polycom Communicator -- Low volume"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by T_W on 2007-03-16
Anyone have any exerience running the USB Polycom Communicator with Skype under Edgy?

The [Polycom Communicator]("http://www.polycom.com/products_services/1,1443,pw-34-14992-14993,00.html") is a USB-based teleconferencing solution for Skype.  

I plugged the Communicator into my laptop running Edgy.  It was immediatley recognized and configured as an Alsa Sound Device.  I was able to easily reconfigure Skpe to use the communicator and was able to place a call to the "Skype Test Call" service.

The only problem is that the Mic volume was very low.  I tried bumping things up in the "Volume Control" panel as well as via alsamixer.  Unfortunatley nothing seemed to effect the call volume.

Anyone tried this out or have any ideas?

---

### Post by dhubler on 2008-03-20
I can confirm that issue on Gutsy Gibbon as well.  Speaker worked great, mic nothing.  Volume buttons didn't work on device, nor did volume settings in "Volume Control" control panel in ubuntu desktop work either

---

### Post by jonobacon on 2008-06-17
Also having the same problem - anyone figured out a fix for this yet?

---

### Post by Tom Mann on 2008-06-17
Hi Guys,

This may or may not work - as this is a solution to the eeePC's microphone volume problem, but may be worth a shot...

(Taken from [http://wiki.eeeuser.com/ubuntu]("http://wiki.eeeuser.com/ubuntu")

Open a terminal (Applications > Accessories > Terminal) and type the following:

  sudo alsactl store
  sudo cp /var/lib/alsa/asound.state /var/lib/alsa/asound.state.old
  sudo nano /var/lib/alsa/asound.state

Editing /var/lib/alsa/asound.state: find "Capture Switch" and change the two &#8220;false&#8221; statements to &#8220;true&#8221;.

Exit nano (CTRL-X, Y, Enter)

In the terminal type the following:

sudo alsactl restore


Again, this is in the wiki for the eeePC, so may not be relevant, but worth a try.

---

### Post by jonobacon on 2008-06-17
Hi Tom - great stuff - it now works! I fiddled with your recommendation and adjusted a few things to make it work. I updated my blog entry with the details:

  [http://www.jonobacon.org/?p=1199](http://www.jonobacon.org/?p=1199)

Thanks! :)

  Jono

---

