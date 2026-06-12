---
title: "wpa/wpa2 question"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by kw27 on 2010-04-02
Hello.  Having problems getting qpa/wpa2 personal working (nw111 (0846:9000  chip set) usb wireless card on a Dell C800 latitude laptop) with ubuntu 9.10.  Card works fine (with nisdwrapper) with no authorization/encryption.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

shows that WPA/WPA2 does work

First a naive question.  When WpA/wpa2 selected in network connection on the laptop the only information it asks for is a password.  On the router (buffalo wzr-hp-g300nh) the input is a "pre-shared key"  which can be between 8  and 63 character.  The naive question is: the password asked for on computer is not that preshared key, right?  IF it is not how do I enter a password in on and the "preshared key" in another? 

I did find: [http://ubuntuforums.org/showthread.php?t=263136&highlight=wpa](http://ubuntuforums.org/showthread.php?t=263136&highlight=wpa), which seems to suggest the password on laptop gets converted into a "passphrase" using

wpa_passphrase your_ssid your_pskIs this passphrase the pre-shared key on the router.  Do I enter the password in laptop wpa/wpa2 network configuration window?  It seems each time I do this command (same password and SSID) I get a different passphrase.  I tried doing this but nothing connects.  

maybe if my lack of understanding of passwords/passphrases and preshared keys are the issue.  trying above I did continue with the howto, but I could not follow completely because I get stuck at the part 6 and 7.  in part 6 a section with my wireless card does not exist. only 2 lines relating to  "lo" exits.  and in section 7 I am not sure which driver to use wext or ndiswrapper (neither work, but I may have other problems) and I have no eth0 device (everywhere else wlan0 is appearing.  I tried using both eth0 and wlan0 but nether works.  I had to remove the "w" after the "B" in the line
sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.confand with the wlan0 it stopped giving error meassages when I ran it.

Any help?

---

### Post by kw27 on 2010-04-04
I learned a little.  It seems that the password in Ubuntu and the  pre-shared-key in the router setup are the same thing.  Without  additional changes to ubuntu I did get it to work... briefly.   I tried  different combination of wpa, wpa2 authentication with individual tkip  aes authorization.  It connected with wpa and tkip.  I was very happy.  I  change setting to further test it and it would not connect  with any  other setting.  I went back to wpa and tkip and it would not connect  again.  I changed the password on both computer and router and it  connected again.  I wanted to test one more thing and changed back to  the wpa/wpa2 tkip/aes mixedmode , which did not work, so again went back  the wpa/tkip and the same password and it no longer connected.   I  tried changing password again with no luck.  I can not get it to  reconnect again.   I don't know why it work twice, but not any more.     all I had changed was the password and the mode on the router.  computer  still connect fine with no authentication (obvious I did not leave it  like that for long) but not with encription

Can anyone shed some light on what is happening.

 keith

---

