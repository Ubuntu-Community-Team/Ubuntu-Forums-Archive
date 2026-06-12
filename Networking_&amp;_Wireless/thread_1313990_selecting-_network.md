---
title: "selecting- network"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by JohnPinto on 2009-11-04
Hi,
am using ubuntu 9.04
want to select the network using command line i
my wireless interface is in 'wlan0'
i used the following commands..
[COLOR=DarkRed]**1)**[/COLOR]
sudo ifconfig wlan0 down                
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 1  
sudo iwconfig wlan0 essid "saveme"
sudo ifconfig wlan0 up


Initially it was connected to ssid "linksys"

when i finished all the above given commands  it connected to the network "saveme", It gave ping results for "saveme" (4 to 8 ping results) and then disconnected it and again got connected to the previous network "linksys"

How to continue with this problem ?
[COLOR=DarkRed]2)[/COLOR]
--i manually deselected the wireless option from network-manager ---ran all the above commands --- and then selected activated the wireless option in the network-manager ---it got connected to "saveme" and started pinging without any problem..

[COLOR=DarkRed]3)[/COLOR]
I also ran the command -[COLOR=Blue]
sudo ifdown wlan0[/COLOR] before all the above commands but of no use..

Can anyone tell me how to proceed ?

Thanks in advance..

-John...#-o

---

### Post by dvlchd3 on 2009-11-04
Network Manager and iwconfig are two seperate wireless tools.  They should be used seperately.  If you disabled NetworkManager, you should be able to connect successfully with ifconfig and iwconfig.  If NetworkManager is not disabled, it will try to interfer with the connection.

---

### Post by JohnPinto on 2009-11-04
Hi,

I used a command before all the above mentioned  commands ie,
 sudo /etc/init.d/NetworkManager stop

So the commands to be followed are


[COLOR=RoyalBlue][B]sudo /etc/init.d/NetworkManager stop
sudo ifconfig wlan0 down                
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 1  
sudo iwconfig wlan0 essid "saveme"
sudo ifconfig wlan0 up
sudo /etc/init.d/NetworkManager start[/B][/COLOR] 


it worked...fine..

---

