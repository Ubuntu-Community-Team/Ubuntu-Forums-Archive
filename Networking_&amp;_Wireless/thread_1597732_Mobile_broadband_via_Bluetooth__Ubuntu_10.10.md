---
title: "Mobile broadband via Bluetooth / Ubuntu 10.10"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by yelvington on 2010-10-15
Is there a known way to get mobile broadband working through Bluetooth on Ubuntu 10.10?

Previously I've used Blueman to get this done. However, Blueman expects to notify Network-Manager of the connection's availability via HAL.

HAL has been removed from Ubuntu.

Ubuntu's standard (nameless) Bluetooth configurator does not appear to have any idea that mobile broadband exists.

[https://bugs.launchpad.net/blueman/+bug/660373](https://bugs.launchpad.net/blueman/+bug/660373)

---

### Post by yelvington on 2010-10-15
Following up my own post:

It appears that the 10.10 upgrade clobbered a previous configuration, couldn't properly read a previous configuration and/or simply broke Blueman.

However, the following steps got things working again. The key is to delete all configurations and get completely away from Blueman, using the native stack. Once you do that, the device should show up in the Network Manager applet.

* Completely remove Blueman, using Synaptic.
* Reboot to delete any processes that were holding open the file handles. (How very Windows-like. Not good.)
* Delete the Bluetooth device pairing left over from Blueman. Click the Indicator Applet's Bluetooth icon. Choose "Preferences." Find the device and delete it.
* "Set up new device," find the device, and re-pair.

That last step should offer to configure dial-up networking (DUN). Walk through the wizard, selecting your mobile broadband provider. 

Now the bluetooth device should show up in the network manager applet, just like "Wired Networks" and "Wireless Networks." Connect and you're good to go.

This enabled me to use my Verizon Blackberry 8330.

---

### Post by physio_amer on 2010-10-16
[size="5"]*Thanks a lot yelvington. :)*[/size]

---

### Post by kvmill on 2010-10-20
That worked. Thanks!!

---

### Post by ammostro on 2010-10-22
I've created a new mobile broadband connection in this way to use my nokia E72 as a mobile broadband modem in Ubuntu 10.10 Netbook Edition. Unluckily i'm not able to find this connection into the 'Network Connection' system panel, anybody knows how to change its properties so i can avoid connection while my mobile is roaming on other GSM networks?

---

### Post by ammostro on 2010-10-23
Found how to modify this configuration, had to add proper keys via gconf-editor.

---

### Post by singletrackmind on 2010-11-02
This did the trick for me as well. Thank you, that was an annoyance. 

Just like he said, delete it, remove blueman and just set it up using the native blutooth tool. Then you will have a connection available under network manager under the name of your provider. 

Thanks again

---

### Post by jtpoole99 on 2010-11-16
Does anyone know how to complete this setup through Kubuntu?  I've seen the notification box telling me that my blackberry's dun will be added to network manager, but when I click on the network manager icon, the only thing listed is my WLAN device and my Wired device.

Any help on this matter would be very much appreciated...

---

### Post by jfleming9232 on 2010-11-17
This method worked for my Blackberry Storm 2 from Verizon......for about three days.  Then suddenly, it just will not connect.  The network manager still shows my DUN connection and it will still pair with my Storm but when it tries to make an internet connection all I get is the "Disconnected-You are now offline" message.  I have tried removing, reinstalling, etc.  No go.  The set up still goes through like it should it just will not connect.  Any thoughts?

---

### Post by demonboy on 2010-11-24
> 
That last step should offer to configure dial-up networking (DUN). Walk  through the wizard, selecting your mobile broadband provider. 



I don't see this option. The devices are paired up but there is nothing about setting up a DUN between the two devices.

---

### Post by pikamoku on 2010-11-26
thanks

removed blueman from synaptic, reboot, and then used the default bluetooth manager to Search, Pair, select DUN connection and configure it.

now Mobile Phone DUN connection is available on Network Manager tray icon.

it worked fine for me.

---

### Post by KRISHi on 2010-11-28
> **ammostro said:**
> I've created a new mobile broadband connection in this way to use my nokia E72 as a mobile broadband modem in Ubuntu 10.10 Netbook Edition. Unluckily i'm not able to find this connection into the 'Network Connection' system panel, anybody knows how to change its properties so i can avoid connection while my mobile is roaming on other GSM networks?

same problem here buddy. with my nokia 6233

---

### Post by KRISHi on 2010-11-28
its true that native bluetooth tool offers u to connect ur phone through DUN after pairing & makes a connection for u. but... when u restart the pc, it just don't get connected to the mobile phone & keeps displaying network disconnected!! plz help guys. thanks in advance!

---

### Post by Dinesh Babu on 2010-11-30
Thanks a lot..... It works 100%

---

### Post by prat22 on 2011-01-08
> **KRISHi said:**
> its true that native bluetooth tool offers u to connect ur phone through DUN after pairing & makes a connection for u. but... when u restart the pc, it just don't get connected to the mobile phone & keeps displaying network disconnected!! plz help guys. thanks in advance!


It doesnt connect for me too... Did the pairing, and the connection gets listed in the drop-down list of the applet. But it shows mobile broadband "disconnected", and the checkbox too keeps de-selected!! However, when I try my connection, it tries to connect, but fails!

I am using samsung C3010, with Airtel/Docomo... Doesnt connect with either...

Please help!!:confused:

---

### Post by gsedej on 2011-01-14
Hi,

It still does not work for me. I have HP compac nc6000 laptop with internal bluetooth and Nokia E63. USB device:
```
Bus 004 Device 002: ID 049f:0086 Compaq Computer Corp. Bluetooth Device
```
It worked just fine in 10.04.
I updated Ubuntu from 10.04 to 10.10 and I can't make it work. I followed yelvington's instruction and tried it few times, but Mobile Bandbord conncetion just does not appear in Network Manager applet. And I can't see it "ifconfig" command.

> **yelvington said:**
> Following up my own post:

* Completely remove Blueman, using Synaptic.
* Reboot to delete any processes that were holding open the file handles. (How very Windows-like. Not good.)
* Delete the Bluetooth device pairing left over from Blueman. Click the Indicator Applet's Bluetooth icon. Choose "Preferences." Find the device and delete it.
* "Set up new device," find the device, and re-pair.


I don't understand the 3. point. How can you delete device if blueman is not installed? I tried to remove all pair connections before deletion.
Ok, so where is configuration file located?

Do you have any other idea?
*does somone knows if blueman project is still active?*

---

### Post by gsedej on 2011-01-14
I solve it!

You shouldn't use Blueman at all!
I deleted Blueman and installed default bluetooth application.

---

### Post by tlcstat on 2011-02-01
Greetings, Works perfect with Mavrick. Did complete removal of Bluetooth, Blueman, Bluez, etc. Rebooted. Reinstall Bluetooth and Gnome-bluetooth. Search for phone, choose provider from list, provider then shows-up under Network Manager. No problems at all. Thanks for the information.
tlcstat

---

### Post by frekja on 2011-02-05
> **jfleming9232 said:**
> This method worked for my Blackberry Storm 2 from Verizon......for about three days.  Then suddenly, it just will not connect.  The network manager still shows my DUN connection and it will still pair with my Storm but when it tries to make an internet connection all I get is the "Disconnected-You are now offline" message.  I have tried removing, reinstalling, etc.  No go.  The set up still goes through like it should it just will not connect.  Any thoughts?
I have the same problem as jfleming9232 - bluetooth dialup worked for a while, now it doesn't. I've completely removed and reinstalled several times to no avail.

---

### Post by josepgl on 2011-02-06
Thank you!!!

---

### Post by frytek on 2012-03-22
Well, maybe it works, but not for xubuntu. I believe there is no "native" bluetooth manager applet here. I guess, it is available in Gnome? In xubuntu I used blueman, but now it just cannot work if HAL is removed. :( 

Or am I wrong? Any suggestions?

---

