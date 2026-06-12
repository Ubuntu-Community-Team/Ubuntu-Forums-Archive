---
title: "Ubuntu 8.04 32bit and Intel Wireless WiFi Link 4965AGN card"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by rbaleksandar on 2009-04-20
Hi, guys :)

  First of all I'm a jungle-boy when it comes to Linux and something too complicated like WiFi :D So keep it simple please :D

  I've looked in the forum and as far as I could find any results they were all about having problems like "wlan worked fine for a while and then suddenly stopped after (...)". Couldn't find anything about installing the drivers... :( So sorry if I'm posting something that is already here. Couldn't find it.

 Now the problem: I have a Toshiba Satellite A200-14D (PSAECE) with Intel(R) Wireless WiFi Link 4965AGN. Actually I'm using Ubuntu for quite some time but never used wireless since it was always installed on a virtual machine that connected through the internet via WinXP Pro via Wireless. That's in the past now. This saturday I finally decided to make a dual-boot with Ubuntu 8.04 Hardy Heron and WinXP Pro SP3 (in the future I'll probably wipe Win from my hard drive since under Ubuntu I had almost no problems with updates and drivers! :o ). Well, everything went fine. Now I have them both :) One thing bothers me really though. I can't figure out how to make my WiFi work. Don't know how. :( Read something about Intel wireless drivers already integrated in Ubuntu 8.04. Maybe I'm wrong...Dunno really. I'm a typical win-spoiled human being.

  Before I try downloading anything and installing I would like to know how to determine if there's something that's already there and needs a little push so to say to start working.


Here are some links that I found and that will probably help me in the future:

[http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)
[http://ubuntuforums.org/archive/index.php/t-932275.html](http://ubuntuforums.org/archive/index.php/t-932275.html)
[http://ubuntuforums.org/showthread.php?t=866868](http://ubuntuforums.org/showthread.php?t=866868) (about the same notebook!)


  Sorry again for bothering. Hope someone can help me. LAN's working great so far. Needed less configuring than under XP. :P


Thanks in advance!
rbaleksandar

---

### Post by chili555 on 2009-04-20
First of all, if you are using Network Manager, which is installed by default. it will not allow a wireless connection if you have a wired connection active. Please see: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) especially:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection.I noticed you said, 'LAN's working great so far' so I assume you mean the wired connection is active.

Please unplug the wire. Does the Network Manager icon at the top right now show an available wireless connection? If not, let's give it a poke in the ribs. Open a terminal (Applications -> Accessories -> Terminal, if you are using Gnome) and do:```
sudo ifconfig eth0 down
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Each of these is a separate command followed by 'Enter.' If the command is accepted with no complaint or error, no message will be displayed.

Now does the Network Manager icon at the top right show an available wireless connection? Can you click on it and connect?

---

### Post by rbaleksandar on 2009-04-20
Thanks you for your answer! :)

Forgot to mention something (important) about the LAN (wired connection) - I'm with it at home and I'm using in most of the time Ubuntu. On the campus I'm using WLAN and using WinXP because of this Ubuntu-issue that I'm hoping to resolve with your help guys.



  About the console thingies that you wrote about:

```

sudo modprobe iwlagn
WARNING: Error inserting iwlwif5k_mac80211 (/lib/modules/2.6.24-23-generic/ubuntu/wireless/iwlwifi-5k/net/mac80211/iwlwif5k-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.24-23-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.24-23-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

  I see that it says that the problem is in iwlwif5k_mac80211. Perhaps it is not installed?. I have downloaded iwlwifi-4965-ucode-228.57.2.23 but I see now that I've downloaded the wrong thing).
This dmesg gives me I think more than 100 lines of text in the terminal. :-/
 I typed in the last command too but as I see from these error-messages - no need to do that because it won't work.

---

### Post by chili555 on 2009-04-20
> 2.6.24-23-genericThat's an older kernel. I'd suggest you run Synaptic and get linux-image-2.6.27-11-generic installed, as well as linux-backports-modules-intrepid. Reboot and then please try the commands I suggested once more and let us know the result. Thanks.

---

### Post by rbaleksandar on 2009-04-20
All right :) Didn't know that. Thanks!


EDIT: I seem not to be able to find this image-thing in Synaptics.Used the search function, searched through lots and lots of packages manually.

---

