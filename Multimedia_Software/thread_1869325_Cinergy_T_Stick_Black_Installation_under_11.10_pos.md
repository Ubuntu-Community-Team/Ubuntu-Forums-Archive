---
title: "Cinergy T Stick Black Installation under 11.10 possible kernel issue with 32-bit setu"
date: 2011-10-25
forum: Multimedia Software
---

### Post by ezilg on 2011-10-25
I want to install a Cinergy T Stick Black USB DVB-T Receiver under Ubuntu 11.10
Based on the driver installation described under : [http://xgazza.altervista.org/Linux/DVB/rtl2832u.html](http://xgazza.altervista.org/Linux/DVB/rtl2832u.html)
I encountered error- and warning messages.
## --
                                 ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ make  
 make -C /usr/src/linux-headers-`uname -r` SUBDIRS=/home/ubuntu/rtl2832u-new-3.0 modules  
 make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.0.0-12-generic'  
   Building modules, stage 2.  
   MODPOST 1 modules  
 WARNING: "__udivdi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!  
 WARNING: "__umoddi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!  
 WARNING: "__divdi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!  
 make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.0.0-12-generic'  
 ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ sudo make install  
 cp dvb-usb-rtl2832u.ko /lib/modules/`uname -r`/kernel/drivers/media/dvb/dvb-usb/  
 depmod -a  
 

                                  ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ dmesg | tail -n 30  
 
                                  .
.
                                  [22954.109240] usb 1-4: USB disconnect, device number 3  
 [23156.272071] usb 1-4: new high speed USB device number 5 using ehci_hcd  
 [23157.163377] dvb_usb_rtl2832u: Unknown symbol __divdi3 (err 0)  
 [23157.163443] dvb_usb_rtl2832u: Unknown symbol __umoddi3 (err 0)  
 [23157.163474] dvb_usb_rtl2832u: Unknown symbol __udivdi3 (err 0)  
 [23157.171572] dvb_usb_rtl2832u: Unknown symbol __divdi3 (err 0)  
 [23157.171638] dvb_usb_rtl2832u: Unknown symbol __umoddi3 (err 0)  
 [23157.171669] dvb_usb_rtl2832u: Unknown symbol __udivdi3 (err 0)  
 ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 ## ----
An italian forum suggests, that this might be a kernel issue ( I have 3.0.0 )

There seems to be a difference between the 32-bit version and the 64-bit version
Can anybody confirm this and maybe offer a solution ?
Thanks.

---

### Post by ezilg on 2011-10-29
In the meanwhile I updated the kernel to 3.0.4
[How to compile kernel 3.1 in Ubuntu 11.10, 11.04, 10.10 and 10.04 | HowOpenSource]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04")
 
But this didn't solve the problem with the Cinergy T Stick Black either

ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ make
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=/home/ubuntu/rtl2832u-new-3.0 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.0.4-030004-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "__udivdi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!
WARNING: "__umoddi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!
WARNING: "__divdi3" [/home/ubuntu/rtl2832u-new-3.0/dvb-usb-rtl2832u.ko] undefined!
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.0.4-030004-generic'
ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ sudo make install
cp dvb-usb-rtl2832u.ko /lib/modules/`uname -r`/kernel/drivers/media/dvb/dvb-usb/ 
depmod -a
 
ubuntu@ubuntu-Aspire-5000:~/rtl2832u-new-3.0$ dmesg | tail -n 300 > tail.txt
.
.
[  796.259743] IR RC6 protocol handler initialized
[  796.264111] dvb_usb_rtl2832u: Unknown symbol __divdi3 (err 0)
[  796.264177] dvb_usb_rtl2832u: Unknown symbol __umoddi3 (err 0)
[  796.264209] dvb_usb_rtl2832u: Unknown symbol __udivdi3 (err 0)
[  796.275315] IR JVC protocol handler initialized
[  796.281988] IR Sony protocol handler initialized
[  796.289078] lirc_dev: IR Remote Control driver registered, major 250
[  796.290856] IR LIRC bridge handler initialized
[  796.357016] dvb_usb_rtl2832u: Unknown symbol __divdi3 (err 0)
[  796.357082] dvb_usb_rtl2832u: Unknown symbol __umoddi3 (err 0)
[  796.357115] dvb_usb_rtl2832u: Unknown symbol __udivdi3 (err 0)

---

### Post by old_codger on 2011-11-10
This is exactly the same with my MSI Digivox Mini II with the rtl2832u chipset which gives a 'lsusb' response of 1d19:1101

---

### Post by ezilg on 2011-11-14
I found in a different forum the tip to install Kernel 3.2, which is suppse to take care of this issue.
Well, I wait until the first stable Kernel 3.2 is announced, then I will test it.

---

### Post by Nukleos on 2011-12-24
Try this :
[https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/zipball/master](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/zipball/master)

make
sudo make install
and enjoy !

Patrick

---

### Post by ezilg on 2012-01-30
After having upgraded to Kernel 3.2.0, I proceeded according to this link :
[https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/blob/master/README](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/blob/master/README)
This showed me :

- install compile kit
sudo apt-get install build-essential

- install linux headers
sudo apt-get install linux-headers-$(uname -r)

- install git
sudo apt-get install git

- clone this repo using git
git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git) 

- goto into source dir
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0
cd RTL2832-2.2.2_kernel-3.0.0

- edit Makefile, option INCLUDE_EXTRA_DVB (choose which include file set)
> I used via terminal : gedit Makefile
> here I commented out the line for kernel 3.2.0
> and commented in the line for kernel 3.0 and 3.1

- compile code
make clean
make

- install module
sudo make install

- insert module (or reboot)
modprobe dvb_usb_rtl2832u

If all went OK, you can see in the kernel log something like this:
  [18087.037024] dvb-usb: found a 'USB DVB-T DEVICE' in warm state.
  [18087.037031] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
  [18087.038776] DVB: registering new adapter (USB DVB-T DEVICE)
  [18087.055952] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
  [18087.287475] RTL2832U check_tuner_type : FC0012 tuner on board...
  [18087.853235] DVB: registering adapter 0 frontend 0 (Realtek DVB-T RTL2832)...
  [18087.853384] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/input/input15
  [18087.853419] dvb-usb: schedule remote query interval to 287 msecs.
  [18087.853423] dvb-usb: USB DVB-T DEVICE successfully initialized and connected.
  [18087.853447] usbcore: registered new interface driver dvb_usb_rtl2832u

After a reboot, the stick worked fine.
To watch TV, I use 'Me TV' [FONT=Verdana]

[/FONT]

---

### Post by Ashrael on 2012-02-21
I have a Cynergy T stick RC MKII (0ccd:0097 TerraTec Electronic GmbH Cinergy T RC MKII) working under 11.10 (3.0.0-16-generic) and now under 12.04 (3.2.0-23-generic-pae).

And if I am not mistaken it took only the installing of package linux-firmware-nonfree (1.11 now) and of course my friend me-tv to have a perfect tv on pc sollution.:popcorn:

Well, almost perfect, I haven't got the remote working yet...

HTH.

---

