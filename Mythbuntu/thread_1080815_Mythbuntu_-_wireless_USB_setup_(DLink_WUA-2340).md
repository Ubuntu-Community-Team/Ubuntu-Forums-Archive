---
title: "Mythbuntu - wireless USB setup (DLink WUA-2340)"
date: 2009-02-25
forum: Mythbuntu
---

### Post by vuroth on 2009-02-25
Ok, so I'm trying to follow these instructions here:  [http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html)

I have the driver installed, and ndiswrapper'd.  Now, the instructions say:
> 
* Open System->Administration->Network
* You should see your wireless connection in the list, click the Unlock button to make changes.
* Select your wireless connection and hit the properties button.
* Deselect 'Roaming'
* Select your wireless network from the list and enter in your WPA/WEP information for the card.
* Click ok, and now you have a working wireless connection. Congrats!

Of course, I don't have System->Administration on Mythbuntu.

So now that the driver is set up, how do I get my wlan configured?

---

### Post by vuroth on 2009-02-25
When I tried to run iwconfig, I had to apt-get it (terminal told me how to get it).

iwconfig shows no wireless extensions, but ndiswrapper -l shows the device present.

I thought I had some ndiswrapper errors (in dmesg), but I'm not sure since I have since rebooted.

---

### Post by vuroth on 2009-02-25
Ok, I had some driver issues, I had to install on a 32 bit windows machine and copy the files over - the .ini and .sys from the install CD/zip were insufficient - ndiswrapper did not like them.

Now to figure out how to enter my WPA information.  Any ideas?

---

