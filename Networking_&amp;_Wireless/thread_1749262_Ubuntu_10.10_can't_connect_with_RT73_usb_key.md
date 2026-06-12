---
title: "Ubuntu 10.10 can't connect with RT73 usb key"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by Marco.75 on 2011-05-04
Hi I have an edimax usb key which is fully supported in linux by the RT73Usb driver.
While I was in ubuntu 10.04 (and also in Debian Lenny) it worked perfectly... 
in ubuntu 10.10 I can't connect anymore.
It keeps on trying and eventually the network manager fails to connect.
I have tried various solutions suggested in many threads, but nothing worked.
The only thing that seems to work is:

1- unplug the usb key
2 - disable wireless networking from the network manager applet
3 - disable networking from the network manager applet
4 - plug the usb key
5 - enable networking from the network manager applet.

This doesn't work always, but 90% of the cases... otherwise I have to restart the system
and retry the above sequence.

This behaviour has been experienced by me both in Ubuntu 10.10 and Lubuntu 10.10.
How can I solve this problem?

---

### Post by Marco.75 on 2011-05-05
After a bit of investigation I discovered that the problem is in the dhcp. Actually I can't have a working connection because my wireless interface (wlan0) waits for an IP address that my router doesn't want to give for some reason.
This is not router's fault... I have an older PC with ubuntu 10.04 and it connects without problems using the same USB key! There's something different in the way ubuntu 10.10 and ubuntu 11.04 handle dhcp.

How I discovered this?

At first I tried uninstalling network-manager, and installing wicd: the advantage with wicd was just a greater clarity and "communicativity" of the applet. In fact after entering the wpa key, the wicd applet keeps on telling "waiting for IP address" or something like this.
So I configured wicd to make a static IP connection, instead of using dhcp: I gave a suitable IP address, a Mask, a gateway... et voilà: the wireless connection works.

After this experiment I installed again the gnome network-manager, and made a similar static ip configuration... (I had to manually add the DNS Server address also): same result: the wireless connection works.

So, what I'd like to know is: how can I make dhcp work in my pc? I connect it in a scenario where there are multiple computers connected to the net and mixing static ip and dinamic ip connections can lead to conflicts...
My dhcp address pool is  from xxx.xxx.xxx.2  to xxx.xxx.xxx.254 : to minimize risks of conflict I set my connection to the last one... but then again: is there a way to troubleshoot this dhcp misbehaviour? :confused:

---

### Post by chili555 on 2011-05-05
> My dhcp address pool is from xxx.xxx.xxx.2 to xxx.xxx.xxx.254If this is your router, I suggest going in to the administration pages of the router and change the range to something reasonable, such as x.2 to x.10. Then you can use any static IP from x.11 on up without fear of collision.

Would you try an experiment for me?```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```Now can you connect with DHCP?

Is your router set to mixed WPA and WPA2? I have better luck with one or the other; not mixed.

---

### Post by Marco.75 on 2011-05-05
Thanks for the suggestions!
I restricted the rooter address pool, BTW my router is set to WPA, should I try DHCP with WPA2 or Mixed mode?


The commands you gave me didn't allow me a dhcp connection... wlan0 keeps waiting for an IP untill connection times out. This happens also if I use the command line, e.g.: 

dhclient wlan0  

--->  the prompt disappears for many seconds, then comes back again, but no connection... I was told dhclient outputs its messages to syslog... so I typed

tail /var/log/syslog

and I found a list of identical errors:     DHclient: couldn't acquire IP address (or something like that)  


[SIZE=1] [/SIZE]

---

### Post by chili555 on 2011-05-05
> should I try DHCP with WPA2 or Mixed mode?Try both, although I think mixed mode is least likely to succeed.

The command line method is unlikely to work as long as Network Manager or Wicd is installed and running.

I am out of ideas. I suggest you stick with static. It may be fixed some day.

---

### Post by Marco.75 on 2011-06-03
Sorry for reviving an old post, but I think I have found the origin of my wireless problems... 
I have two kernels on my linux system:
2.6.32 and 2.6.38
if I use the last one, I can't connect (I fail to have an IP address)
if I use the first one, it works perfectly and also DHCP works...
I haven't tried with in-between kernels and with the latest stable (2.6.39 )

Since my wireless problems began after upgrading to ubuntu 10.10,
I would like to know what kernel have ubuntu 10.04, 10.10, and 11.04...

---

### Post by Marco.75 on 2011-06-20
the problem was kernel-related and now it's solved:

I solved it downloading and installing
the latest compat-wireless package here: [http://wireless.kernel.org/download/...-wireless-2.6/]("http://wireless.kernel.org/download/compat-wireless-2.6/")
Here's the whole procedure:

1st: install the build-essential package and the headers related to your kernel
then:

    $ wget [http://wireless.kernel.org/download/...ss-2.6.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")

    $ tar xjvf compat-wireless-2.6*.tar.bz2

    $ cd compat-wireless-*

    $ ./scripts/driver-select - it (shows a list of the supported drivers)

    $ ./scripts/driver-select rt2x00 (rt2x00 is for ralink driver, my chipset...)

    $ make

$ make install

reboot.

It seems that latest kernels (2.6.38 and 2.6.39) introduced something that 
prevent my ralink wifi adapter to complete a positive DHCP transaction.
With the drivers from wireless-compat everything works as expected.

Important note: the new modules don't overwrite the old ones bundled with the
kernel they are placed inside the kernel library into a directory called "update",
and are preferred by the system which loads them because they are a newer version.

---

