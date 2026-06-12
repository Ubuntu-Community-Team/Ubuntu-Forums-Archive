---
title: "Scanner not being detected by ubuntu 11.04"
date: 2011-06-01
forum: Multimedia Software
---

### Post by young hastings on 2011-06-01
I have an epson stylus sx425w which is a printer/scanner. ubuntu found and installed a driver for me and im able to use the printer fine but for some reason the scanner just isnt working. if i use the simple scan software it says connect a printer and if i press the scan button on the printer and select usb it says connection problem.

i saw a post about this already for ubuntu 10 or 9 and they provided a link for a newly released driver which turned out to be the drive ubuntu installed automatically and that hasnt fixed my problem.

anyone know what the cause could be and how to fix it? 


also just incase it matters ubuntu installed 2 drivers for the printer dunno why and what the difference is but it installed 2

---

### Post by demonipuch on 2011-06-02
Hello

Avasys provides Linux drivers for your printer/scanner.

There are 3 packages you might need to install in order to use your scanner. Here are the links :

for Ubuntu 32 bits :

[http://linux.avasys.jp/drivers/iscan-data/1.8.1/iscan-data_1.8.1-1_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.8.1/iscan-data_1.8.1-1_all.deb)
[http://linux.avasys.jp/drivers/iscan/2.26.3/iscan_2.26.3-1.ltdl7_i386.deb](http://linux.avasys.jp/drivers/iscan/2.26.3/iscan_2.26.3-1.ltdl7_i386.deb)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb)

for Ubuntu 64 bits :

[http://linux.avasys.jp/drivers/iscan-data/1.8.1/iscan-data_1.8.1-1_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.8.1/iscan-data_1.8.1-1_all.deb)
[http://linux.avasys.jp/drivers/iscan/2.26.3/iscan_2.26.3-1.ltdl7_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.26.3/iscan_2.26.3-1.ltdl7_amd64.deb)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb)

Install first iscan-data.deb, then iscan-ltdl7.deb and iscan-network.deb

---

