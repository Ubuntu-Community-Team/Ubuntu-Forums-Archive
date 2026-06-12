---
title: "Ndiswrapper, WUSB54G,  connection drops and dies"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by vest1 on 2006-07-08
Hello,
I'm having a problem with my linksys WUSB54G and ndiswrapper. When i start up my computer everything works fine for 20 minutes or so and then the connection drops and I can't get it up again unless i reboot.

This seems to be an old problem according to a forum and google search but I was not able to find a solution anywhere.

Has anyone got any sugestions or found out how to solve this?
Thanks.
-vest1

---

### Post by Linuturk on 2006-07-10
> # Card: Linksys #[WUSB54G], 802.11b/g, USB 2.0 -- [link here|List#WUSB54G]

    * Chipset: Prism54
    * usbid: 5041:2234
    * Driver: Linksys Windows XP driver [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp)
    * Other: Works smoothly, of course ;) - this is the device the USB extension was originally developed for. WEP is running, WPA is supported using wpa_supplicant 0.2.5. No problems with both 1.1 and 2.0 host controllers. As with many other USB devices, no success with 2.4 kernels so far. Try to use 2.6.7 or better. There is a native driver for Prism54 that is working on USB support. View its status at Prism54.org
    * Other: Works with latest Windows Driver from linksys.com. However, freezes entire system if there are multiple ssids nearby with same name (common in apartments). Probably nothing ndiswrapper can do. The same happens in Windows. No success with 2.4 kernels (even with 8k stack). Works with kernel 2.6.11 

# Card: Linksys #[WUSB54Gv4], 802.11b/g, USB 2.0 -- [link here|List#WUSB54Gv4]

    * Chipset: RT2500USB (RT2571F) (They just changed the chip and didn't tell anybody. Be careful which version (v1/v2/v4) you buy!)
    * usbid: 13b1:000d
    * Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com's driver. Works WELL.
    * Driver 0: Ralink driver: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid "usb X-Y: reset high speed USB device using ehci_hcd and address Z") and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). 'mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf' should do the trick.
    * Driver 1: Linksys Windows XP driver: [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp) Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing 'Tx Invalid misc' values nothing happens).
    * Driver 2: older Linksys Windows XP driver: [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
    * Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.serialmonkey.com 

There is the info from ndiswrapper's site. My apartment complex has multiple access points with the same ssid, so mine freezes up just like yours it seems. My card is a version 4 however, so I'm going to try the other drivers listed under the second entry.

From reading that, I've determined that my v4 is locking up only b/c of the multiple ssid's of the same name. It seems that the Driver included on the cd is the best bet.

---

### Post by vest1 on 2006-07-10
> **Linuturk said:**
> There is the info from ndiswrapper's site. My apartment complex has multiple access points with the same ssid, so mine freezes up just like yours it seems. My card is a version 4 however, so I'm going to try the other drivers listed under the second entry.

From reading that, I've determined that my v4 is locking up only b/c of the multiple ssid's of the same name. It seems that the Driver included on the cd is the best bet.

From the info you posted it seems to me that the multiple ssid-name problem only affects versions prior to v4?

I've got the v4 myself and I'm using the rt2500usb driver that came with my cd. Yesterday I managed to stay connected for almost two hours before the connection dropped. I think it's because I was only surfing a single page at the time and not using any other applications that use my connection. It also seems that the connection drops fast if I browse many image-heavy sites at the same time and use gaim or other internet programs.

I suspect that my device is trying to reconnect after the connection drops since it starts blinking when i open the networking configuration but with no success.

I'm using the 1.8 version of ndiswrapper that's posted in the sticky "[How to install WUSB54G for Dapper Drake]("http://www.ubuntuforums.org/showthread.php?t=192588")" thread. But it seems that a 1.19 version is out and I'm going to try and upgrade(if I find out how.) to that version and see if the problem persists, I'll let you know if it doesn't.

---

### Post by kingcharles1666 on 2006-07-10
vest1,

I have the same problem but I have a different usb wifi. I think it has to do with the fact that usb is not good for network interfaces. However there is a trick you can try to reset your wlan0 without rebooting. I use WPA encryption and when I open the network manager and change 1 of the properties of wlan0 and save it, it will reset the connection and it will work for a while again.

Charles

---

### Post by vest1 on 2006-07-10
> **kingcharles1666 said:**
> vest1,

I have the same problem but I have a different usb wifi. I think it has to do with the fact that usb is not good for network interfaces. However there is a trick you can try to reset your wlan0 without rebooting. I use WPA encryption and when I open the network manager and change 1 of the properties of wlan0 and save it, it will reset the connection and it will work for a while again.

Charles
Thanks for the tip Charles but it seems that it doesn't work for me. I tried this a couple of times with no results. The only thing that works is a reboot which is getting less entertaining than it used to be. 

I'm thinking that reseting the connection isn't enough, it seems that the hardware needs to be reset, unpluging the device and pluging it in again causes the computer to freeze and I'm not sure how to do this.

---

### Post by insyzygy on 2006-07-11
I recently got a WUSB54GC usb wifi adapter. I tried using ndiswrapper but had similar problems. I could connect but if the connection dropped or I wanted to change access points, I had to reboot. It was unsatisfactory. As the ndiswrapper website indicates many linksys cards use ralinktech components, apparently ralinktech manufacters the the electronics and linksys just packages them. (On the cd that came with it, have you looked at what the names of the driver files were. Mine were named rt73.inf rt73.sys anything with rt in front is theirs, they also have like a rt2500 and rt2570). They have linux drivers for their chips at 
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")
They also have a support forum. You will have to compile from source. Once I installed their drivers it worked great.

Also if you have an rt73 you have to use ralinktechs drives as the rt2x00.serialmonkey ones are still experimental for this chipset, for rt2570 or rt2500 I suppose either may work.

---

### Post by vest1 on 2006-07-11
> **insyzygy said:**
> I recently got a WUSB54GC usb wifi adapter. I tried using ndiswrapper but had similar problems. I could connect but if the connection dropped or I wanted to change access points, I had to reboot. It was unsatisfactory. As the ndiswrapper website indicates many linksys cards use ralinktech components, apparently ralinktech manufacters the the electronics and linksys just packages them. (On the cd that came with it, have you looked at what the names of the driver files were. Mine were named rt73.inf rt73.sys anything with rt in front is theirs, they also have like a rt2500 and rt2570). They have linux drivers for their chips at 
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")
They also have a support forum. You will have to compile from source. Once I installed their drivers it worked great.

Also if you have an rt73 you have to use ralinktechs drives as the rt2x00.serialmonkey ones are still experimental for this chipset, for rt2570 or rt2500 I suppose either may work.

Wow, this is promissing, thank you.

Too bad I can't get past step 0 in the readme. Is it hard to compile the driver and get it up and working? I downloaded the rt2500 usb driver for linux but I'm having a hard time with it so any advice would be well apreciated.

---

### Post by insyzygy on 2006-07-12
I just ran through the driver compilation process to refresh my memory and this is what you have to do. Before you start anything, to compile drivers you have to download the kernel header files. At console type 
```
 uname -r 
```
this is the kernel version you are running. In synaptic (or using apt-get) find the package "linux-headers-<your kernel version>" and download it. 
Also check if you have the package "make" installed, if not download that.

I assume you have already downloaded the driver file and untarred it. 
As they indicate you should go into the directory everything untarred to 
```
 cd RT25USB* 
```
From in that directory do 
```
 chmod 644 ./* 
```
this makes everything writeable and then do 
```
 chmod 755 ./Configure 
```
this make the Configure script executable.
finally do a
```
 dos2unix ./* 
```
to remove some weird dos text formatting stuff.
You will probably have to apt-get or use synaptic to get the package dos2unix as well.

If your running dapper this is a 2.6 kernel so do 
```
 cp Makefile.6 Makefile 
```
Now run the configure script 
```
./Configure 
```
If you installed the headers it should find them and you should just be able to press enter. Assuming this gives no errors we can continue. Next we compile 
```
 make 
```
wait a while as it works. If you get an error don't despair. 
I had to do the following to get it to work but I'm running a custom kernel which is newer than the one that dapper normally uses so it might not be a problem for you. If you get an error compiling about no field named "owner" then edit the file rtusb_main.c file and on line 95 change it (by putting // at the beginning) to read 
```
//    .owner =  THIS_MODULE, 
```
then try running make again.

If it succeeds you will have a file rt2570.ko you should do 
```
sudo cp rt2570.ko /lib/modules/<insert your kernel name here>/kernel/drivers/net/wireless 
```

Next add the line 
```
alias rausb0 rt2570 
```
to /etc/modprobe.conf

Finally type ```
 sudo depmod -a 
```
and now ```
 sudo modprobe rt2570 
```
if everything worked after typing modprobe your wifi adapter should be working, it should show up as rausb0 if you type iwconfig.

---

### Post by vest1 on 2006-07-12
> **insyzygy said:**
> Tremendous effort, thanks mate!

I had some warnings during the compilation but the .ko file got made so I carried on and I got an error with the "$ dos2unix ./*"
"dos2unix: File read/write error while converting ./LINUX_RACONFIG_V2.0.0.7.". My cards seems to use the rt2500, is it ok that it says rt2570 everywhere?

I've gotten to the point where i'm adding "alias rausb0 rt2570" to the /etc/modprobe.conf but it seems that I don't have such a file, could there be another file meant for the line? There are /etc/modprobe.d/ and /etc/modules.

Thanks again for the help:D

---

### Post by insyzygy on 2006-07-12
The error from dos2unix is because one of the files is a directory, don't worry about it. You may not yet have a /etc/modprobe.conf file. You should just create a new one. Actually linux looks multiple places so you could put the line in either a new /etc/modprobe.conf file, you could probably also put it at the end of /etc/modprobe.d/aliases and maybe even in /etc/modules, I would just create /etc/modprobe.conf

Its fine if there are warnings during compilation, as long as it finished without an error (i.e. there was a rt2570.ko file created) it should be fine. As for the 2500 vs 2570,(remember I have a slightly different version) it seems that even though its an rt2500usb device they name it rt2570, I think the reason is there is a pcmcia version that is really rt2500 and they distinguish the usb version of the same device by calling it rt2570. so rt2500usb=rt2570

Also if you do get it working I recommend reading the file iwpriv.txt it has info on the full capabilities of the driver. 
                                                      Josh

---

### Post by vest1 on 2006-07-12
After finshing all the steps you described I unblacklisted the rt2570(which I blacklisted to get ndiswrapper going(as described in the sticky thread)), uninstalled my ndwisrapper driver and rebooted. When I go into the system>admin>networking and try to activate the rausb0 the system freezes and I have to reboot, just like it did before I installed ndiswrapper. I'm thinking that there might be some kind of conflict with the old rausb0 driver and the knew one? And how does this driver differ from the one provided with Dapper? 

Thanks,
vst1

---

### Post by Teroedni on 2006-07-12
Nope its only the driver which is extreme unstable
You have to do it using conf file; Gui hardlocks:/


Just edit your etc/network/interfaces 

sudo gedit etc/network/interfaces

add this to the file 

auto rausb0
iface rausb0 inet dhcp
wireless-essid linksys
wireless-key  xxxxxxxxxx


Then save it
and do a 
```
sudo ifup rausb0
``` and you ready to go.
Unfortunally this driver is pretty bad as well
Too much traffic will often kill it eg require reeboot.

And Btw this is all you have to do in Dapper as the driver come by default;)

---

### Post by insyzygy on 2006-07-12
Hmm. Thats sucks (that this driver is unstable to), I guess they did better with the new one (rt73) that my adapter uses. Maybe the serialmonkey drivers
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")
are more stable (anybody have experiences with them ?). The process will be the same, untar it, run make, copy the *.ko module to /lib/modules/<kernel versions>/kernel/drivers/net/wireless, add the alias to /etc/modprobe.conf.

---

### Post by vest1 on 2006-07-12
Gawd, :p.

I guess i'll just try the different drivers and see which one of them sucks the least.

The most frustrating thing is that I have to do a reboot when the driver gives up..no solution to this? :mrgreen: 

Thanks to those who answered, I'm gona try messing with this tomorrow, see if  the rt2570 driver is satisfactory or else I'll just get a new card.

Btw, has anyone had any success with a Planet wl-8314(or a card with a Marwell 8335 chip)? A pal has one and I guess I could convince him to switch with me.

-vst1

---

### Post by insyzygy on 2006-07-13
If you work from the command line does it crash? I noticed that doing 
```
 ifconfig rausb0 down 
``` would always freeze the system so I just don't do that. I think the gui may be bringing the interface down and then up again using this command and this is freezing it. If I configure mine from the console (as long as I don't do the above) it works fine and has never crashed and I could change access points and reconnect without rebooting.

If you work from console does it freeze. To scan you can do 
```
 iwlist rausb0 scanning 
```
to associate to a particular access point you can do
```
sudo iwconfig rausb0 essid "access point name "
```
Then you get an ip address
```
 sudo dhclient rausb0
```
and your on the net 

To switch to a different access point or get a new ip address if the connection is lost just do iwconfig or dhclient again.
Using it this way may be more stable than through the gui, it is for me (but I have a different version so who knows.)

---

### Post by vest1 on 2006-07-13
Aight, I'm using the rausb0 now. So far so good, it seems faster and more stable than the ndis.

Thanksies;) 

Now it's just the sound, tv-card and changig the file systems on my ntfs drives to fat without loosing the files..:mrgreen:

---

### Post by aqau on 2006-07-23
If that didn't work, you can go to my site that i made just for this because i had such a problem with it.  [http://www.cicerosonline.com/WUSB54GC/](http://www.cicerosonline.com/WUSB54GC/)

It is very similar to what you are doing but a little different.

---

### Post by goonies on 2006-08-05
how do you tell if you are using the new driver, dapper includes this driver and i had it working somehow, curiousty made me install the newest rt2570 from ralink.net with the instructions provided in this thread, i know the new rt2570 is placed in a different spot than the stock one thats included with dapper, question is how can i tell which one i am running, if im still running the old one, or if im running the new one, also how can i quickly switch between them?

thanks for your help on this

---

### Post by goonies on 2006-08-05
```
[17179599.024000] rt2570: Unknown symbol verify_area
[17179599.036000] rt2570: Unknown symbol verify_area
[17179599.064000] rt2570: Unknown symbol verify_area
[17179599.072000] rt2570: Unknown symbol verify_area
[17179599.076000] rt2570: Unknown symbol verify_area
```

i get this error when trying to use the new driver =\

---

### Post by vasoconstrictor on 2006-08-08
I'm using the Belkin FD7050 USB wi-fi pen that uses the rt2571f.
The module I'm using is the rt2570 that ships with xubuntu (ubuntu dapper).
I had the same hangs and connection drops that everyone complains about.

To avoid restarting the machine when the connection drops, I simply unplug the usb device and replug it. I suppose that since it's a PNP device, this simply forces the module to be reloaded.

Another thing I noticed is that the usb pen would get extremely hot at times. 
In total despair, I improvised a heat sink ( a metal pencil sharpener :D ) and just placed it on top of the chip.

I'm now bombarding the thing with azureus, x2x and the sporadic web browsing. It has managed to remain connected for much longer (from disconnecting 5 or 6 times a day to only once or twice under the same circumstances.  

Can any of you guys verify if this is actually the case or if its just a fluke?

Nevertheless, the windows drivers didn't have this problem, which means that the linux module is really the cause of this.

I just hope a better module comes out before I mod my wi-fi pen :D

---

