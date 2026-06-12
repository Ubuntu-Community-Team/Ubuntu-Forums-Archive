---
title: "Use ndiswrapper on xubuntu live-CD"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by schulwitz on 2012-11-24
I've written a shell script for those who are looking for a way to use **ndiswrapper** successfully running the **xubuntu 12.04 live-cd**.

Note: this script has been_ specifically tailored to those using the **WNA3100 Netgear**_ wireless card and will have to be modified slightly for those with other wireless cards (see the bottom of my post for further instructions on this matter).

[I]Steps:
1.  Download &#8220;ndiswrapper_xubuntu_WNA3100.tar.gz&#8221; here:   [/I][https://sites.google.com/site/schulwitz/ndiswrapper_xubuntu_WNA3100.tar.gz](https://sites.google.com/site/schulwitz/ndiswrapper_xubuntu_WNA3100.tar.gz)[I]
(md5sum = f5ac854cad6aa5e93eb1bf3236197030)
2.  Right click -> Extract Here
3.  cd to directory &#8220;ndiswrapper_xubuntu_WNA3100&#8221;
4.  Give execute permissions by typing "chmod a+x install.sh"
5.  Run script by typing "./install.sh"
6.  Once the script finishes, click the wireless icon in the upper left hand corner, the WNA3100 should be working![/I]


If this script doesn&#8217;t work, verify that you have the WNA3100 Netgear wireless card by typing: &#8216;lsusb&#8217;.  You should see a line similar to this:
```
&#8220;Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]&#8221;
```If you do not see this line, you have a different wireless card.  Follow these steps:
[I]1.  Find the appropriate Windows .inf driver file and place it in a directory on your xubuntu system.  
2.  Open up &#8220;install.sh&#8221; and modify the line that reads &#8220;sudo ndiswrapper -i Netgear/bcmwlhigh5.inf&#8221; and change &#8220;Netgear/bcmwlhigh5.inf&#8221; to a path that points to your windows .inf driver file.
3.  Save install.sh
4.  Run steps 4-6 listed above.[/I]

---

