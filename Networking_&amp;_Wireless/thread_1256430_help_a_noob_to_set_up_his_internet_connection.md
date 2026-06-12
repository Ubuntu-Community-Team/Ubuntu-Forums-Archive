---
title: "help a noob to set up his internet connection"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by DnGrS on 2009-09-02
I tried the following in order to set up my connection:

I edited etc/network/interface to 
if eth0 inet static
address xx.xx.x.x
network xxx.xxx.xxx.xxx
gateway xx.xx.x.x

then I edited /etc/resolv.conf adding nameserver *dns1* and nameserver *dns2*
then i typed this in the terminal -> sudo /etc/init.d/networking restart and it failed.. it said it couldn't read the interface file or something like that

A friend of mine said doing this would fix my internet but it didnt't work. Neither does he or I know what to do further.. so any help? By the way I'm using ubuntu 9.04 desktop i386 if that helps. Oh, and I saw that I have 3 network interfaces: 1) Wired network (asus blabla ethernet controller), Auto Ethernet(it's the only one i can enable out of the 3), 3)Wired networks (realtek blabla)- this is my network board but it's kinda broken so I use the motherboard's onboard one(this should be the nr1 interface which I can't select).
So.. what now?

---

### Post by diafanos on 2009-09-02
Why do you have to edit so many files? There is a gui network manager.
Just go:  System -> Preferences -> Network Connections.

Select the Auto eth -> edit -> IPv4 settings 

Do you really need to set a static ip? 
If you don't, then

-> Method: Automatic (DHCP).

else 

-> Method (Manual)
And complete the appropriate address, netmask, gateway and dns server

---

### Post by Iowan on 2009-09-02
If it will work for you, Network Manager is pretty painless for either DHCP or static address. Manual configuration via */etc/network/interfaces* adds the "inconvenience" of configuring */etc/resolv.conf*, but should work (it bypasses Network Manager - which may complain about "unmanaged" interface).

---

### Post by DnGrS on 2009-09-02
I did it lol.
I set it up Manually and it worked..
THANKS A LOT!

1 tiny question
Can I import bookmarks from windows's mozilla to this one?

---

### Post by diafanos on 2009-09-03
Of cource you can.

(export bookmarks)
In firefox select: Bookmarks -> Organize bookmarks...
then in the toolbar select: Import and backup -> Backup and save the .json file.

(import bookmarks)
Do the other way round: Import and backup -> Restore -> Choose file, and select the previous saved .json file

---

### Post by DnGrS on 2009-09-03
Thanks again

---

