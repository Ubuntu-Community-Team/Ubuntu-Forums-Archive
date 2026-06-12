---
title: "A work-around for usb wifi/3G adapters without Linux drivers"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by JJSkoli on 2012-05-14
I have found a work-around for using dongles without Linux support, like the Linksys AE2500, or telephone company dongles for 3G connectivity. The work-around uses Oracle VirtualBox, with Windows as a guest system, and herein lies the rub: it may look like an overkill if you install VirtualBox for this sole purpose. But in my case I already have it installed (my thesis advisor bought a Windows-license software package which the whole lab uses), and it's a snap to setup. 

The work-around involves getting the adapter to work on Windows, and then making it accessible to all users of the Host-only network. I will assume that you already have Windows installed as a guest OS on Oracle's VirtualBox running under Ubuntu (11.10, in my case). If you don't, I am not sure it's worth the hassle just for this. 

1) Start-up Oracle VirtualBox, on the top bar of the screen, NOT of the Oracle GUI that's just appeared, check 
File->Preferences; then click on Network. Add a Host-only network
by clicking on the plus sign (a new network called vbox0net will appear), then click on settings (the screwdriver);

2) now configure the Host-only network as follows:

adapter 192.168.137.101

Now go to the DHCP server page and change the following settings:

Server 192.168.137.100
Lower Bound 192.168.137.1
Upper Bound 192.168.137.99

[This choice of network, 192.168.137.xxx, may appear arbitrary, but it isn't: when you share your connection within Windows, the OS automatically sets up a 192.168.137.xxx network, warning you of possible connectivity losses with other PCs. By choosing the IP range as 192.168.137.xxx you void this danger, but you must also allow for the fact that Windows will take for itself the IP 192.168.137.1, which voboxnet0 would like to reserve for the Ubuntu machine. The choice suggested above takes into account all of this.]

3) Now you can start your Windows virtual machine. At this point you can check, by using ipconfig/ifconfig and ping, that host and guest can talk to each other.

4) You may now connect the Windows machine by means of the USB adapter, be it a wifi or 3G antenna.

5) When this is done, in Windows, open Connection Center, click on Modify NIC properties, select the card thru which you are connected to the Internet, click on it with the right button, select Properties, then Sharing. Select the top choice (Share connection with other computers), and then, in the drop-down menu, select LAN network. Then click on Settings, and select all boxes that appear. Save and leave Windows. 

6) In Ubuntu, since the connection has not been set up thru Network-Manager, we need to tell the machine how to reach the Internet. First, add a static route thru your Windows guest,

sudo route add -net 0.0.0.0/0 gw 192.168.137.1

and then add DNS servers by editing /etc/resolv.conf

sudo vi /etc/resolv.conf

and adding these two lines at the bottom of a (presumably empty) file:
nameserver 8.8.4.4
nameserver 8.8.8.8

7) restart networking
sudo /etc/init.d/networking restart

and you're good to go. Hope this is useful to someone.

---

