---
title: "new wifi trouble in previously stable ubuntu 12.04"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by Hodor on 2013-07-16
I'm having a new trouble with wifi in previously stable ubuntu 12.04 on a Dell inspiron n5010:
the connection drops out, and then a window prompting for authentication password appears -> click ok (details previously saved) -> keeps re-prompting.

Device connects ok via ethernet cable (i've just tried sudo apt-get update), doesn't seem to have helped.
I've tried fiddling with power management (as suggested here for a 13.04 user: [http://askubuntu.com/questions/295035/wifi-keeps-disconnecting-and-extremely-slow-at-low-signal-ubuntu-13-04](http://askubuntu.com/questions/295035/wifi-keeps-disconnecting-and-extremely-slow-at-low-signal-ubuntu-13-04));
I've tried the following suggestions (from here [http://askubuntu.com/questions/263529/wifi-keeps-prompting-for-password](http://askubuntu.com/questions/263529/wifi-keeps-prompting-for-password)), no joy:
[COLOR=#333333][FONT=UbuntuRegular]echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo modprobe -rfv ath9k[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo modprobe -v ath9k

My windows computers are working fine, so this is nothing to do with the modem or router.

Any advice much appreciated (no wifi is a deal breaker for me).

Thanks[/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-07-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

