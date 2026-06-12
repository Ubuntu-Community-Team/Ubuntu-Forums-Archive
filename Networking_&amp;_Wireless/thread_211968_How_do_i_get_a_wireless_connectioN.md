---
title: "How do i get a wireless connectioN?"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by mech7 on 2006-07-09
I have been trying for hours now.. where can I setup a wireless wpa connection I only have a wep setting :mad:

---

### Post by parkash on 2006-07-09
As far as I know there's no WPA support yet.

---

### Post by mech7 on 2006-07-09
No wpa? omg that sucks then.. makes wireless pretty useless as wep is so easy to hack :s

---

### Post by bikeboy on 2006-07-09
> **parkash said:**
> As far as I know there's no WPA support yet.

Not true at all. However wpa is tricker than wep. I suggest looking at [https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)
There is info and wpa as well as instructions for specific cards. Have a look at both.

---

### Post by parkash on 2006-07-09
Hmm...  Perhaps there is... I've read sth about WPA supplicant out there...  But haven't really used it...

-- Edit...  Thanx for the correction... bikeboy

---

### Post by mech7 on 2006-07-09
I have an  	 Acer TravelMate 4102WLMI i believe it has an Intel PRO/Wireless 2200BG... but that card is not in the list on that page ?

---

### Post by mech7 on 2006-07-09
It says..

> you'll need to install network-manager-gnome. After installing the package logout and log back in (or re-start) and network manager should appear. Right click the network manager icon to enable network if necessary. Next, left click on the network manager icon and choose "Connect to other wireless network".

But i only have 2 small screens as an icon.. when i click it it only says wired.. and i cant even select that. My wireless is active. in networking

---

### Post by bikeboy on 2006-07-09
Ok, you're right. The general wpa stuff should help but it looks like this is teh howto you're after [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Parkash, no worries, hope I didn't sound too harsh. I don't actually use wpa but I knew it was possible. I live in a pretty much wifi free area and I use other security measures. So mine isn't under threat for now.

---

### Post by parkash on 2006-07-09
No offense taken ;) Besides it's always good to know.

---

### Post by mech7 on 2006-07-09
isn't there someone who compiled it allready ? as i don't have a internet without my wireless :-s

---

### Post by mech7 on 2006-07-09
Also it says..

Now we have to download and install the wpa_supplicant package:
Code:

sudo apt-get install wpasupplicant

So it was installed allready but then..

Then you have to create a wpa_supplicant.conf in /etc, so:
Code:

sudo gedit /etc/wpa_supplicant.conf

I can't even do that it just gives me an error :confused:

---

### Post by mech7 on 2006-07-09
hmm i followed everything it says.. but i get this error:

Warning PCI Driver IPW2200 has a struct device driver shutdown method please update

Also wanted to post a screenshit print screen does not work.. so i took tha capture thingy.. then half the time i could not save to my usb stick and the other half it did not open in windows :mad:

---

### Post by bikeboy on 2006-07-09
About the screenshot, make sure you save it as a .jpg, I think the default is .png but maybe windows doesn't like them.

---

