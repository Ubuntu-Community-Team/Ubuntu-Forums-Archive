---
title: "Reverse USB tether 12.04 and android ICS"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by visual1ce on 2012-06-05
I'd like to connect my phone via USB to my laptop and access internet on my phone through my laptop. Here are some details:

Laptop:
connected by ethernet cable to ADSL router
internet works fine

Phone:
Samsung galaxy s2
USB Tethering is on
Installed app "Reverse Tether"

So when I connect phone to laptop via USB I get a new connection in network connections and in ifconfig i get a new item: usb0. So I click on connect in Reverse Tether and (eventually) it tells me that it got a desired ip and gateway ip but no internet connection. I think I need to bridge the connections...

As far as I know I have no software firewall running and the router firewall is disabled.

So how can I do this?

---

### Post by linux_falguni on 2012-07-12
connect phone to PC/laptop via USB 
turn on USB Tethering
network-manager auto configures usb0 as a client using phone as dhcp server
edit the usb0 connection in network-manager, change ipv4 settings ->mehtod-> Shared to other computers.
it will start dhcp server, assume new ip address and configure  bridge for you
now start "Reverse Tether" in your phone
it will configure phone as a client using PC/laptop as dhcp server, get ip and gateway
done

---

### Post by impredario on 2012-12-07
@linux_falguni -- Thanks for the clear step-by-step guide!

Followed your instructions exactly. At the last step, selected **Automatic Configuration** in Reverse Tether app & touch **Connect**. It shows blue dots (success) for

[LIST]
[*]USB Tethered
[*]Desired IP
[*]Gateway IP
[/LIST]
It then stops with message[INDENT]Failed. Can not reach network. For troubleshooting tips please visit littlelan.com/amm/faq
[/INDENT]On Linux, **ifconfig** shows
```
$ ifconfig usb0
usb0      Link encap:Ethernet  HWaddr d2:bf:4d:dd:89:65  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d0bf:4dff:fedd:8965/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5938 (5.9 KB)  TX bytes:25889 (25.8 KB)
```On Android, **ifconfig** shows
```
$ su
# ifconfig usb0
usb0: ip 10.42.0.49 mask 255.255.255.0 flags [up broadcast running multicast]
```I have read the FAQ and rerun the Getting Started Guide. However, no joy. Suggestions?

My setup:

[LIST]
[*]Ubuntu 12.04 with latest updates from Canonical
[*]LG C800G phone with Android 2.3.6
[*]Reverse Tether version build.2012.09.08.paid
[/LIST]
>>> UPDATE 2012-12-13 <<<
Found a solution on StackExchange > Android Enthusiasts > ["How do you set up internet pass-through (reverse-tether) on linux?"]("http://android.stackexchange.com/questions/14256/how-do-you-set-up-internet-pass-through-reverse-tether-on-linux")  After following linux_falguni's steps above and letting Reverse Tether fail, I entered the following in terminal on Android device:
```
$ su
#route add default gw 10.42.0.1 dev usb0
```10.42.0.1 happens to be the IP address of the network interface for usb0 on Linux, as you can see from the Linux ifconfig output above.

Now I can browse the web and run apps (at least the ones I've tried so far) on my Android device through my Ubuntu Linux PC. Currently investigating ways to automate the process, with or without Reverse Tether.

---

