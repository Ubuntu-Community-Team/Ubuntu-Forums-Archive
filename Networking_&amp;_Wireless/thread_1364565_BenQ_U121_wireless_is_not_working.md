---
title: "BenQ U121 wireless is not working"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by narendra.sisodiya on 2009-12-26
my BenQ U121 wireless is not working on karmic ubuntu 9.10.
lsusb -v output says, my chipset, is 
* usb based
* belongs to Ralink
* support 802.11 n Wilreless LAN
* {USB_DEVICE(0x13D3,0x3247)}, /* AzureWave */
Here is my lsusb -v output [http://pastie.org/756546](http://pastie.org/756546)

root@eduvid:/home/narendra# uname -a
Linux eduvid 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

After booting, it show me wireless network at drop down at network manager, but it does not list any wifi network around me, also I tried to created some new wifi network but those new wifi network are not detected in other laptops.



I checked my dmesg and it says

[   16.695958] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.712843] rt2800usb 1-4:1.0: firmware: requesting rt2870.bin
[   17.077265] input: rt2800usb as
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input6


I think it load rt2800usb, I think the correct driver for this should be rt2870usb

i have added following lines in /etc/modprobe.d/blacklist.conf

blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00usb
blacklist rt2x00lib


but applying this does not worked out.

then I tried following command

root@eduvid:/home/narendra# modprobe rt3070usb
FATAL: Module rt3070usb not found.
root@eduvid:/home/narendra# modprobe rt2870usb
FATAL: Module rt2870usb not found.

does it means i need to add these drivers ?? I have rt3070sta on karmic.
So

applying, this

root@eduvid:/home/narendra# modprobe rt3070sta

no error came, but wifi still not working.
So, What driver i need for this ?
also what is the difference between rt3070usb and rt3070sta
also what is the difference between rt2870usb and rt2870sta

---

### Post by narendra.sisodiya on 2009-12-26
Hi, 
My Wifi is working now. I forget to reboot it. 
This is my procedure - [http://lug-iitd.posterous.com/how-to-make-benq-u121-wireless-working-on-kar](http://lug-iitd.posterous.com/how-to-make-benq-u121-wireless-working-on-kar)
Thanks

---

### Post by Speedster on 2009-12-29
I found that the rt3070sta driver allowed my wifi to scan but not to associate with WPA/WPA2 networks. Open and WEP networks were fine.

In the end I had to download the latest driver from RALink Tech to get it to work.

Doc for wireless (and other U121 fixes) here - [http://docs.google.com/Doc?docid=0AfzktdIb2ExcZHJqcTd2bl8zZjY3Mm1iY24](http://docs.google.com/Doc?docid=0AfzktdIb2ExcZHJqcTd2bl8zZjY3Mm1iY24)


Dean

---

### Post by laptopreviewshop on 2010-12-02
We are offering a Benq Joybook U121 netbook for free. All you have to do is take part in our contest on our website. 

[http://laptopreviewshop.com/win-a-benq-joybook-lite-u121-eco-netbook.html](http://laptopreviewshop.com/win-a-benq-joybook-lite-u121-eco-netbook.html)

---

