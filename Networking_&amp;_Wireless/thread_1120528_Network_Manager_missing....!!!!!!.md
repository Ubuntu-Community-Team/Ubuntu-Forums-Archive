---
title: "Network Manager missing....!!!!!!"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2009-04-09
Plz see the thread below...... 

[http://ubuntuforums.org/showthread.php?t=1105963](http://ubuntuforums.org/showthread.php?t=1105963)

Is there any possibity to getback my Network Manager from live cd or are there any available .deb packages for Network Manager....!!:(

---

### Post by t0mppa on 2009-04-09
If I understood correctly and you just closed it, see this thread [http://ubuntuforums.org/showthread.php?t=1117735]("http://ubuntuforums.org/showthread.php?t=1117735") for instructions on how to get it back.

---

### Post by chinmaya_n on 2009-04-09
Not exactly...... b'se in the  thread u suggested, he missed the panel but here i missed Network Manager Itself... When i tried to run the command "nm-applet" it is showing "no such file found".

Then i tried to run it in terminal then it is showing as follows:

The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>

I cant get any internet connection with out the Network Manager....then how can i use apt-get to install is from the web. So i asked for any debian package or to get from any livecd.

Plz any one help me!!:-(

---

### Post by khelben1979 on 2009-04-09
Network Manager can be found [here]("http://rpmfind.net/linux/rpm2html/search.php?query=NetworkManager&submit=Search+...&system=&arch=") (contains packages in rpm format which easily can be converted to the .deb format by using [the alien tool]("http://en.wikipedia.org/wiki/Alien_(software)")).

Or download it from [the Network Manager homepage]("http://projects.gnome.org/NetworkManager/").

And.. ask someone to download it for you or from a library somewhere, or something.

---

### Post by abn91c on 2009-04-09
here is the deb

---

### Post by chinmaya_n on 2009-04-09
Thanks everyone......... i got everything back by using the following command :
```
sudo dhclient eth0
```
again Thank u verymuch for ur help..!!

Now i would like to know what exactly happend to my system.... and what has the above command done?? plz explain me!:p

---

### Post by coutts99 on 2009-04-09
> **chinmaya_n said:**
> Thanks everyone......... i got everything back by using the following command :
```
sudo dhclient eth0
```
again Thank u verymuch for ur help..!!

Now i would like to know what exactly happend to my system.... and what has the above command done?? plz explain me!:p

[http://www.linuxcommand.org/man_pages/dhclient8.html]("http://www.linuxcommand.org/man_pages/dhclient8.html")

---

