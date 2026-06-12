---
title: "Internet crashes"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by owy on 2009-05-05
Thought I would let the community know about this one. 
Have a macbook pro. The whole disc is dedicated to ubuntu 9.04 which I like. Especially now that i config the background the splash page. 
I was terribly confused about the internet crashes on 8.04, 8.10, and 9.04 particularly when I added wireless, or added the network manager  to the mix. I have found (dont know if others have) that the best way is to keep the original network manager without update and not to add on any additional wireless. That way my internet etho does not crash or drop at all. 

Thats my 2 cents for the community. Was not a hardware bug at all.

owy:lolflag:

---

### Post by trentscott4 on 2009-05-05
Agreed, I had a similar problem and solved it through the following steps:

This is for Ubuntu 8.10 Desktop, simply skip steps 1-2 if
you're running Ubuntu 8.10 Server.

Steps:

  1. Open a console (Alt+F2) and type:
     ```
gnome-terminal
```
  2. Remove 'Network Manager'.
```
sudo apt-get remove --purge network-manager
```
  3. Modify the /etc/network/interfaces file.
     ```
sudo vi /etc/network/interfaces
```
  4. Press 'Insert' to edit the file and enter the following
(customized to your network):
    ```
 # The primary network interface
     auto eth0
     iface eth0 inet static
     address 192.168.1.115
     netmask 255.255.255.0
     gateway 192.168.1.1
```
  5. Hit 'Esc' and type ':wq' to save the file and quit.
  6. Modify your DNS servers.
     ```
sudo vi /etc/resolv.conf
```
  7. Delete any existing lines and replace with your router's IP:
     nameserver xxx.xxx.x.x
  8. Hit 'Esc' and type ':wq' to save the file and quit.
  9. Restart your networking.
     ```
sudo /etc/init.d/networking restart
```
 10. Test your new settings:
    ```
sudo ifconfig
```

The output should reflect the changes you just made
(proper IP, gateway, etc.)

---

