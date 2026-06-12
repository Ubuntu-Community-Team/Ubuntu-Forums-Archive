---
title: "Network Manager Disabled"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by Ske7ch on 2011-01-08
Ive had 10.10 since it's stable version was available with no problems. The past couple of days my newtwork manager hasen't been able to connect to any wi-fi network. Last night after trying to figure out a solution it randomly connected to a wi-fi network, but after turning the laptop off and on again the same problem resumed.

Today after reading a couple of solutions I came across one right here in the ubuntu forums that suggested removing the network manager and installing a wicd? not sure what it was called. I removed the network manager but I can't install anything else since I don't have any internet connection lol

Then I read another solution about a bug and to open a Terminal and type sudo aptitude remove connman, and it did something but I still can't check if I solved to problem because my Network Manager is still not running from the previous solution.

Is there anything I could do to get the Network Manager running again and see if I can find a solution to this problem?

Thanks.

---

### Post by PatchesTheCaveman on 2011-01-08
Go to Applications > Accessories > Terminal and run this command:
```
sudo apt-get --no-download install network-manager-gnome
```
If you're lucky, APT has NetworkManager cached on your hard drive and it will install.  

If you're not so lucky, you'll need your Ubuntu install or live DVD/USB to reinstall the packages from.  Put it in, and double-click on its icon on the desktop or in the Places menu to mount it.  Then, go back in a terminal and run this command:
```
sudo apt-cdrom add
```
For more information on this process see [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

Once you've done that, you can run
```
sudo apt-get install network-manager-gnome
```
to reinstall NetworkManager.

(Note:  If you use Kubuntu change -gnome to -kde above.)

---

