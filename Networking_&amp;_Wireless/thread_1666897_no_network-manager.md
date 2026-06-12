---
title: "no network-manager"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by Harley883 on 2011-01-14
Hi all,

I'm running xubuntu 10.04 LTS (upgraded from 8.04 LTS) on an old low power sempron machine as an always on 'internet machine' i.e. it does all my downloading email etc. and up until yesterday it has always performed flawlessly. Yesterday wasn't its fault, it was a BTI network problem that took out my internet service but while talking to tech support I realized that this machine has lost all ways to control the network cards. network-manager and network-manager-gnome are installed according to synaptic but they have no menu or notification appearance. I've tried reinstalling them to no avail, any help in getting some control back would be much appreciated.

---

### Post by dineshs on 2011-01-14
Right click on panel - click add to panel - select "Notification Area" from the list then add
If your icon is not back please post the contents of /etc/network/interfaces```
cat /etc/network/interfaces
```

---

### Post by Harley883 on 2011-01-14
Thanks for the quick reply, 

I already have a notification area on the panel but with no network icon and this is the content of 

cat /etc/network/interfaces 

that you requested

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.76
netmask 255.255.255.0

iface eth1 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

iface eth2 inet static
address 192.168.1.76
netmask 255.255.255.0

auto eth1

auto eth2

the cards are working perfectly, I just have no way of accessing them.

---

### Post by dineshs on 2011-01-14
If you want network manager to manage your devices,edit /etc/network/interfaces using ```
sudo gedit /etc/network/interfaces 
```so that it has only these lines```
auto lo
iface lo inet loopback
```
Restart Machine.Your icon will be back
Configure devices as explained [ here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

---

### Post by dineshs on 2011-01-14
If you want network manager to manage your devices,edit /etc/network/interfaces using ```
sudo gedit /etc/network/interfaces 
```so that it has only these lines```
auto lo
iface lo inet loopback
```
Restart Machine.Your icon will be back
Configure devices as explained [ here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

---

### Post by dineshs on 2011-01-14
If you want network manager to manage your devices,edit /etc/network/interfaces using ```
sudo gedit /etc/network/interfaces 
```so that it has only these lines```
auto lo
iface lo inet loopback
```
Restart Machine.Your icon will be back
Configure devices as explained [ here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

---

### Post by Harley883 on 2011-01-14
Thanks for that dineshs, I now have network manager back in the notification area and an easy/quick way to control my network cards. 

Network still hasn't reappeared in the system menu though, but that doesn't matter, I don't need it twice. 

It's still a mystery why it disappeared though. I've no idea as to when, it just wasn't there when I needed it yesterday.

---

### Post by dineshs on 2011-01-14
> Network still hasn't reappeared in the system menu though, but that doesn't matter, I don't need it twice. 
Dont you have Network connections under system-preferences?
> It's still a mystery why it disappeared though. I've no idea as to when, it just wasn't there when I needed it yesterday. Did you edit /etc/network/interfaces manually before?

---

### Post by Harley883 on 2011-01-15
No, there is no network icon under system, it disappeared just like the network manager icon had leaving me with no easy method of controlling my network cards. Prior to the network trouble I had a couple of days ago (a service outage in the BTI network) I had no need to and consequently never noticed the lack.

I originally set the cards up using network manager and hadn't touched the settings since.

---

### Post by dineshs on 2011-01-16
Older ubuntu versions used network-admin tool for configuring devices
The configurations are stored in /etc/network/interfaces. You can 
1)Go to System->Administration->Network 
or
2)Type network-admin into a terminal
or
3)Edit /etc/network/interfaces using ```
sudo gedit /etc/network/interfaces
```for configuring devices.More info [here]("https://help.ubuntu.com/community/NetworkAdmin")
Newer versions use Network-manager
The configurations are stored in /etc/NetworkManager/system-connections.You can 
1)Go to System->preferences-network connections
or
2)Rightclick NM icon and edit connections
More info [here]("https://help.ubuntu.com/community/NetworkManager0.7")

---

### Post by Harley883 on 2011-01-17
thanks for the additional info dineshs

---

