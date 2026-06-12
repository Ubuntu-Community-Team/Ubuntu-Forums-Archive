---
title: "Epson artisan 835 network printer"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by valtra on 2010-12-30
I have an Epson Artisan 835 network printer hooked up to my desktop. I am running a wubi install of 10.10 and cannot get it to find the printer. 

I previously had an artisan 830 and it worked fine, however, this new printer is not recognized in the add printer application. 

So far I have install LSB 3.2, and then installed the rpm package for the artisan 835 using alien -i. Now I am at a loss for what to do. 

Can anyone help?

Thanks

---

### Post by PatchesTheCaveman on 2010-12-30
Though it is a network printer, it sounds like you have it connected via USB.  Is that correct?

If so, you might have better luck finding help on the Hardware board:  [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by valtra on 2011-01-16
Unfortunately it is not a wired connection. We were recommended to keep it on network for our windows installation and unfortunately I cannot turn it into a wired connection.

---

### Post by synace on 2011-07-30
I figured I'd help anyone else trying to setup this printer/scanner. I just bought it from OfficeMax for $119.99 + tax by using their 'exhange' voucher for $50 off the price by returning an old (really old..) printer for them to recycle. I think it ends today though.

On Ubuntu 11.04 (Natty):

1. set the printer up on your network w/ a static IP or static lease via DHCP on your router. (for purposes of this howto, your target IP would have been set as '192.168.1.222')
2. use the add printer tool in system > printing to add the printer, hit the network down arrow, (open it up and wait about 30 seconds, it will appear in the list), click on Epson Artisan 830
3. searching for drivers comes up.. be patient.
4. install the proprietary driver (1.0.0 the first in the list) (for me this ends up being: epson-inkjet-printer-artisan-725-835-series_1.0.0-1lsb3.2_amd64.deb)

to get the scanner working:
```
sudo apt-get install libltdl7 sane

```

then download iscan, iscan-data and iscan-network-nt (for your architecture.. i'm on amd_64) from: 
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

and install them (adjust based on latest versions/filenames/architecture):

```
sudo dpkg -i iscan_2.26.4-2.ltdl7_amd64.deb iscan-data_1.9.0-1_all.deb iscan-network-nt_1.1.0-2_amd64.deb
```
then, edit this file:

```
sudo nano /etc/sane.d/epkowa.conf
```
and add (and change the IP to the printer's IP): 

```
net 192.168.1.222 1865
```
then, check your main menu and click on Image Scan, or run 'iscan' manually

all set

---

### Post by jefflinux on 2012-01-15
new to ubuntu. Tried following the thread but still get error opening iscan. get
could not send command to scanner
check the scanner's status. works in Windows7 so think I may have missed something. It's a network attached printer and I can ping it from the ubuntu machine

any ideas?

---

### Post by jefflinux on 2012-01-16
nevermind -got it working was just a dhcp reservation issue with my scanner

---

