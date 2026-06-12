---
title: "Linksys 802.11g wireless USB hub - not connecting to Eth0"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by makoto149 on 2006-02-27
I have a PC that I've installed Breezy on, and have a Linksys 802.11g USB access point installed on. Device manager recognizes the device, but I still can't connect to the network (I'm running a wireless network).

A "route -n" command shows that I have nothing going on. Sad... :-(

How do I tell Breezy that my USB device is the "network" device? Am I going to have to edit a file? Because I will! Somebody please help me!

Thanks.

---

### Post by super on 2006-02-28
you need to have it set up to use wlan0 not eth0. use the gnome networking tool to do it. it's fairly staight forward.

---

### Post by makoto149 on 2006-02-28
I see no way to add a new connection. Supposedly, there is an "Add" button, but one doesn't show up on the dialog box. I've tried running network-admin as root, but this doesn't work either. Am I running the right version of breezy? Is there some kind of patch I need? I hate it when the doc doesn't match the app!

---

### Post by super on 2006-02-28
there should not be an 'add' button. all usable network interfaces should be already displayed. if there is no wlan0 that means your hardware is not being detected correctly.

you most likely need to install ndiswrapper and install your device manually. basically the process goes like this:

1. uue synaptic to get ndiswrapper-tools

2. get the windows drivers for your card from the linksys site, and copy the .sys and .inf to somewhere (eg: /home/<yourusername>/Linksys/)

3. open terminal, and enter the following commands:
```
cd Linksys
sudo ndiswrapper -i <*thenameofyourdriver*>.inf
cd /etc/ndiswrapper/
```
some people have mentioned that for some linksys recivers you must edit all the .conf files in /etc/ndiswrapper. use gedit to open the *.conf files and look for the line [FONT="Courier New"]RadioState|1[/FONT] and change it to [FONT="Courier New"]RadioState|0[/FONT]

now back to the terminal:

```
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules
sudo iwlist wlan0 scan
```
make a note of your access point in the list, then
```
sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed
``` (the X and ESSID are the values from the iwlist scan
```
sudo ifup wlan0
```

or you could try using dapper rather than breezy. my linksys usb reciever worked out of the box with no need for drivers in dapper.

---

### Post by makoto149 on 2006-03-04
Thanks for the very detailed help. I definitely appreciate it. I've wrestled with this all day, following your instructions, but to no avail. I think it's a problem with the particular driver I'm using (which I downloaded from linksys' website).

There is a Wiki page with very similar information to what you provided at [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto.]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto.") that mentions grabbing the latest ndiswrapper source, compiling it and replacing the version of ndiswrapper that came with the Breezy distro. I think I'm gonna try that, and if that doesn't work, I'm upgrading to Dapper.

Thanks again!!!

---

### Post by makoto149 on 2006-03-05
Thanks, super, for the replies! The best advice super gave me was to upgrade to Dapper. I installed the Daily Build for 3-4-06, and my Linksys WUSB54G (version 4) USB Wireless Adapter was recognized right away. All I had to do was go to System > Administration > Networking and enable the device (with the correct SSID, etc., of course). I am writing this post from my newly connected computer.

The device iface is "rausb0" and works like a charm (or you wouldn't be reading this post!).

---

