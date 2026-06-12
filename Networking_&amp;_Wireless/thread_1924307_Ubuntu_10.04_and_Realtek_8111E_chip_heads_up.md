---
title: "Ubuntu 10.04 and Realtek 8111E chip heads up"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by Zaaark on 2012-02-12
Just wanted to share this information.

I have Asus P8H61 USB3 motherboard with that gigabyte capable realtek chip and the driver that comes with Ubuntu 10.04 that chip doesn't work as it should. Connection is dropping, download and upload speeds are low, there is lot's of packet loss.

Problem is solved by downloading new driver from realteks website. Install it and reboot. Problems are gone!

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)    8.028.00    2012/2/3    61k

This problem is not only Ubuntus problem, but with Fedora, Debian and Centos too.

---

### Post by Ramblin on 2012-04-11
When you say install it and reboot, can you expand a bit please?

I have the same board as you and apparently the same problem.

Did you have to uninstall the original driver and then install new?
Did you have to add the new driver to the rc.local file or was it automatically added?

The ReadMe that came with the driver from the Realtek site had instructions for installation that had sections to it.

The first section:
<Quick install with proper kernel settings>     
Unpack the tarball :         # tar vjxf r8168-8.aaa.bb.tar.bz2      
Change to the directory:         # cd r8168-8.aaa.bb      
If you are running the target kernel, then you should be able to do :          # ./autorun.sh    (as root or with sudo)      
You can check whether the driver is loaded by using following commands.          # lsmod | grep r8168         # ifconfig -a      
If there is a device name, ethX, shown on the monitor, the linux      driver is loaded. 
Then, you can use the following command to activate      the ethX.          # ifconfig ethX up          ,where X=0,1,2,...

After that, it LOOKED like the remaining sections were optional, but I wanted to check with you first, before doing anything.

Thanks for your posting - it was precisely my situation (with CentOS)

Ramblin

---

