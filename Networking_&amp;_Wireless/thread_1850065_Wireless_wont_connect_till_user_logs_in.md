---
title: "Wireless wont connect till user logs in"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by oneadvent on 2011-09-25
Is there anyway to make it connect on power up? I cannot remote in if I reboot it. I have to have someone log in there then I can.

Thanks!

---

### Post by praseodym on 2011-09-25
You can try:

```
echo "auto wlan0" | sudo tee -a /etc/network/interfaces
sudo /etc/init.d/networking restart
```
if wlan0 is the name of your interface. Do you use the network-manager? Which Ubuntu-version is that?

Check:
```
uname -a
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by oneadvent on 2011-09-25
```
oneadvent@oneadvent-desktop:~$ uname -a
Linux oneadvent-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
oneadvent@oneadvent-desktop:~$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory
oneadvent@oneadvent-desktop:~$

```

I did what you suggested and it did not work.

---

### Post by praseodym on 2011-09-26
Ok, the file doesnt exist in Natty anymore. Try Wicd instead of the NM:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **wlan0** (or whatever) as interface name and **wext** as driver. Now you can add additionally the following line (if you added "auto wlan0"):
```
echo "iface wlan0 inet dhcp" | sudo tee -a /etc/network/interfaces
sudo /etc/init.d/networking restart
```
Deactivate the NM in "Autostart" or uninstall it completely:
```
sudo apt-get remove --purge network-manager plasma-widget-networkmanagement
```. For wired connection you can add similar lines with "eth0" and/or configure a manual config.

---

