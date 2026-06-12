---
title: "Atheros 5007 in Ubuntu 8.10"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by Oram on 2009-03-16
Hey I have tried everything I could find to get my Atheros 5007 to work with Ubuntu 8.10 and nothing has worked. :(
I have tried
```
sudo apt-get install linux-backports-modules-intrepid

```

I also tried ```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
```
```
sudo ./madwifi.sh
```

These were suggested here: [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937)

Also I tried ```
sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules
```

When I first used ```
sudo apt-get install linux-backports-modules-intrepid

``` it worked then after I installed my video card drivers it stopped working.  After that I had tried all 3 and still no luck.   Does anyone know any other way of getting my card to work?

EDIT:After trying everything I could I installed Vista again wondering if it was my internet card.  Sure enough my internet card didn't work in vista eiter. I found out that my switch to turn my wifi on was turn off.  Time to reinstall Ubuntu tomarrow(this time I wont turn the switch off)

---

