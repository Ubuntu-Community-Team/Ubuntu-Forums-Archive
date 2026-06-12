---
title: "4965 AG WIFI Card - iwl4965 - connection losts"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by mac-duff on 2013-07-05
Hi there,
After checking this “internet-thing” I found some threads about network issues with the Intel PRO/Wireless 4965 AG WIFI Card, or this is at least what lshw is telling me I have (Lenovi T61). My current driver is iwl4965 and I also have a lot of disconnects when I am in the university and want to connect to the Eduroam network.
Sometimes it works quite well for about 10 min, sometimes the connection is dropped again already after 5min and also sometimes I have to enter my password various times.
All the stuff I found was with old distribution but now I am using Ubuntu 13.04 which should have all the bug fixed which other members describes 4 years ago and said that they were fixed with kernel 2.4... or somehting.
So, the point is, has someone an idea what I can do? Its really annoying :/
Thanks in advance
Stephan

---

### Post by wildmanne39 on 2013-07-05
Hi, please try:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
Thanks

---

### Post by mac-duff on 2013-07-08
Hi,
thanks for the reply.
I tried what u recommanded but after I couldnt connect to the network anymore.

I tried to reverse it with:
```

echo "options iwl4965 11n_disable=0" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965

```

But no luck so far

---

### Post by wildmanne39 on 2013-07-08
Hi, please do not make changing unless we ask you too because it will make it much harder if not impossible to get your wireless working.

Open:
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```
make sure it looks like this:
```
options iwl4965 11n_disable=1
```
Then add swcrypto=1 and it will look like this:
```
options iwl4965 11n_disable=1 swcrypto=1
```
reboot, if it still does not work properly then copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by mac-duff on 2013-07-10
Hi,
I set it and it looks much better at the university but at home (DD-WRT) I am lossing now the connection after some minutes and the AP disappaers... :(

---

### Post by wildmanne39 on 2013-07-10
Hi, run the script in my previous post when you are at home with the connection you are now having trouble with.
Thanks

---

### Post by praseodym on 2013-07-11
Try pure WPA2-AES encryption mode and a fixed channel at home. Bandwidth to 20MHz, not 20/40 MHz.

---

### Post by mac-duff on 2013-07-31
Hi,
ok, here are the log files from the script. I did it one time when I was connected to m-d and one time after it disappeared after a while.

Thanks for your help

---

### Post by wildmanne39 on 2013-07-31
Hi, this network has 100 percent strength   > dd-wrt_vap:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2 can you not use it?

When you are not connected it is at 58 percent and the other one is completely out of range.

When you can not connect did you move further from the router? did you close a door between the router and your computer?
or something else get in the way?
Thanks

---

