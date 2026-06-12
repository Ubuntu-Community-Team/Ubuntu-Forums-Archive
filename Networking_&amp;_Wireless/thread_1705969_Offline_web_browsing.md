---
title: "Offline web browsing"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by gunsnrails on 2011-03-13
Hi,

I'd like to do the next:

1- Create some websites and store them locally on a laptop with Ubuntu.
2- Set a web server on the laptop
3- Allow other computers to access the websites stored on the laptop

For the #2 I'll search about setting up Apache, NGinx or Thin server

But I have doubts about what I need for #3. The laptop has wireless integrated. When in use, the machine will not have access to the Internet, but the Internet will be the sites locally available. I'm not sure what I need for this step. For example is the integrated wireless adapter enough to server the websites or do I need to get some router (usb/pci), how many client computers it could serve, any special SW/HW needed/recommended, ..? 

I would appreciate any advices/links how to get the setup for this step.

Maybe some Ubuntu flavour would be better than other...

Cheers.

---

### Post by gunsnrails on 2011-03-16
Hi, anyone?

What I've done so far is using the "Create New Wireless Network" option. 
With that I've been able to connect a mobile device to the laptop and browse the internet with it. The laptop is connected to the net via cable.

I have installed NGinx web server and started it so I can in the laptop go to localhost and see the default index.html page of the server.

How can I access that from the mobile device as well? Any hints?

Cheers.

---

### Post by BkkBonanza on 2011-03-16
Whether you need a router or not depends on how many machines are on your net. If just two and they are connect to each other then you can get to the website by using the address of the second machine. Instead of localhost you would use either the IP or name of the laptop computer.

If you have (or want to have) several machines all on the network then you would need some form of router, which could be a device or just software running on one machine. The only thing that needs to happen is the machine accessing the page needs to get it's request to the machine with the web server. When there are only two machines it's easy as it has no where else to go anyway. 

But if more than two machines then the request will be sent to the machine set as "gateway" and if that machine has the web server, then good, but if not then it needs to know where to go after that and usually this gateway should know where to "route" to (it acts as router).

In your current setup of just the two machines you likely can just use the IP of the laptop but you may want to add a name so that you can use that instead. The simplest approach is to add a name in your /etc/hosts file (on the mobile) that tells your mobile that this name maps to the laptop IP.

eg. your laptop is 192.168.0.1 and your mobile is 192.168.0.2 you may edit /etc/hosts and add a line like,

192.168.0.1 laptop 

Now you can access the laptop as: [http://laptop](http://laptop) instead of [http://192.168.0.1](http://192.168.0.1)

---

### Post by gunsnrails on 2011-03-17
> **BkkBonanza said:**
> But if more than two machines then the request will be sent to the machine set as "gateway" and if that machine has the web server, then good, but if not then it needs to know where to go after that and usually this gateway should know where to "route" to (it acts as router).

Thanks BkkBonanza. Yes very good point. Utimately this wont be only two computers. Actually the laptop should become a box that is seen as a Wireless Access Point by the other devices. Connecting to it using the SSID and a key. But the box (WAP) will run its own web server to provide the content, so it will be running Linux inside. At this point I would like to replicate the setup with a laptop.

Potentially tens of devices would connect to the box.

Maybe I should approach other way to replicate this setup (?)

Thanks.

---

### Post by BkkBonanza on 2011-03-17
If you want to mimic the router/server that someday will be a seperate box then I'd suggest the best way is to install **VirtualBox** and create a virtual machine version of the server you want. 

Then you can start it on the laptop, build and customize it as needed. It will connect to your network "as if" it were a physical machine (and there's several options how it can connect to your network). When you don't want a router/server you can shut it down (but still have full normal use of the laptop). It is really a totally seperate machine running within your regular machine.

One good thing about this method is you learn to install/config a server/router without it messing with the laptop (desktop) config. And later if you build a real physical machine you can copy over the system to a real hard disk and mount it in the real server and away you go with pretty much the same system.

If you do this then you would setup some iptables rules to configure it as a router for the network, install dnsmasq (as a dhcp server, to assign IPs to the network), install the web server software (Nginx is great) and other apps you want. 

To run a WAP on the laptop you need certain conditions met. First, the wifi card in the laptop needs to support "master mode" (Atheros ath9k cards are good). Then you need to install software to run the WAP (hostap is usually used). It does authentication and beacon packets etc. This stuff has to run on the physical machine (not a VM) due to the driver support it needs.

I run Ubuntu on a small home-built Jetway mini-ITX box that acts as a wifi router, torrent client, firewall, iSCSI file server etc. It's been great and I learned a lot setting it all up. Ideally you router would have two ethernet ports but with wifi you could get around that.

---

### Post by gunsnrails on 2011-03-17
> **BkkBonanza said:**
> To run a WAP on the laptop you need certain conditions met. First, the wifi card in the laptop needs to support "master mode" (Atheros ath9k cards are good). Then you need to install software to run the WAP (hostap is usually used). It does authentication and beacon packets etc. This stuff has to run on the physical machine (not a VM) due to the driver support it needs.

Great pointers. I'd like to get close to the box setup as much as possible. I have this spare laptop so I would like to have it as a separate machine instead of running virtually. Then I would "cut" the cable and try to get content to different devices.

I'm using a ThinkPad T41 for this with integrated wireless, wgconfig eht1 mode Master returns an operation not permitted and it goes to Ad-Hoc so I guess I'll look for a USB card that can work on Master. And then head for the hostap. 

Thanks again. I'll be reporting the progress.

Yeah Jetway mini-ITX look similar to the idea I have when ready :)

---

### Post by BkkBonanza on 2011-03-17
If you do find a usb dongle that can do master mode be sure to post it here. I haven't found one yet. The Atheros cards are miniPCIe and I bought one on ebay to replace my laptop's internal card (which works fine). I think that maybe the ThinkPads can't do that due to differences in the interface but I'm not sure. I have 4 dongles and none of them do master mode.

---

### Post by gunsnrails on 2011-09-20
> **BkkBonanza said:**
> If you do find a usb dongle that can do master mode be sure to post it here. I haven't found one yet. The Atheros cards are miniPCIe and I bought one on ebay to replace my laptop's internal card (which works fine). I think that maybe the ThinkPads can't do that due to differences in the interface but I'm not sure. I have 4 dongles and none of them do master mode.

Hi, after a long time I'm back with this.

I purchased a USB wify adapter that "in theory" supports master mode. But can't set it.
This is the device:
[http://www.telewell.fi/en/index.php?node_id=17011&product_id=56](http://www.telewell.fi/en/index.php?node_id=17011&product_id=56)

Here the documentation where it mentions about access point mode:[URL="http://www.telewell.fi/en/manuals/TW-WLAN802.11nv2USB_manual_gb.pdf"] http://www.telewell.fi/en/manuals/TW-WLAN802.11nv2USB_manual_gb.pdf
[/URL] 
The documentation says that I works in AP mode.

When I use: iw list it tells:
```
Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * WDS
         * monitor
         * mesh point
```But when I use: sudo iwconfig wlan0 mode master it tells:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```From the syslog I can see:

```
kernel: [   39.602530] Registered led device: rt2800usb-phy0::radio
kernel: [   39.602629] Registered led device: rt2800usb-phy0::assoc
kernel: [   39.602732] Registered led device: rt2800usb-phy0::quality
kernel: [   39.604723] usbcore: registered new interface driver rt2800usb
kernel: [   39.655574] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
```The manufacturer provides the drivers for Linux and I have downloaded them. I hope installing them will help. But I am not sure if they will be better than the ones that the system currently uses.

You can see the readme file they provide here:
[http://pastie.org/2562367](http://pastie.org/2562367)

I'm about to follow the instructions but I have some questions. They ask me to:

> define the linux kernel source include file path LINUX_SRC
modify to meet your need. in the makefile.

I'm trying this with the latest Linux Mint and still on the T41. Any advice what to put in there?

And the next questions are not trivial for all as well:

> 3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
    ** Build for being controlled by WpaSupplicant with Ralink Custom Event
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -dComments? Is there an easier way to get the drivers installed for the device?

Thanks.

---

### Post by gunsnrails on 2011-09-20
Hi,

I just installed and ran hostapd and then I can see that the device is set into master mode.
Don't know why the direct command didn't do it.

Now I'll see if I can get something connected to it.

---

