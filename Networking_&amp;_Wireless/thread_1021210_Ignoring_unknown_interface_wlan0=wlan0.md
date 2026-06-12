---
title: "Ignoring unknown interface wlan0=wlan0"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by imhotep1 on 2008-12-25
Hello my friends

Dell Latitude D800 Laptop with Nvidia Go5650 and the network controller is Broadcom BCM4309 802.11a/b/g (rev 0).

I only use Wlan0, no cable.
I successfully installed the Wlan0 and could use it. I used the drivers from [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) with worked perfectly for me.

Unfortunately, my stella emulator destroyed my X11 config. file.
With the Ubuntu rescue, recovery console I initalised the X11 setting. 
After that Ubuntu haven't recognized my Wlan0 any more. I reinstalled it, did different things, but nothing helps. 

The network icon with auto eth0 and wirelss networks is greyed out.
sudo ifup wlan0 --> Ignoring unknown interface wlan0=wlan0
sudo ifdown wlan0 --> interface wlan0 not configured
imhotep@imhotep-laptop:/usr/share$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PVZ-51912"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

I did:  sudo ifcongi wlan0 up 
Of course, wlan0 is in /etc/network/interfaces with auto wlan0 as it was ever before.
I also did: sudo /etc/init.d/networking restart  --> Ingnoring unknown interace wlan0=wlan0

What else can I do?

---

### Post by tonytraductor on 2009-05-11
I'm having a similar issue on a laptop with Jaunty.
I removed gnome-network-manager, when installing a lxpanel netstat monitor (b/c I use openbox), and since then, I can't connect.

sudo ifup eth0 
gives
ignoring unknown interface eth0=eth0

sudo ifup wlan0
gives
ignoring unknown interface wlan0=wlan0

My output from iwconfig is much like that posted by the OP (ie. wlan0 is listed).

I can't apt-get gnome-network-manager back, since I can't connect.

Please assist.

thanks

---

### Post by Peter09 on 2009-05-11
You need to connect hardwired to get network manager.

Can you post the output of

```
lshw -C network
```

and the contents of

/etc/network/interfaces

---

### Post by Peter09 on 2009-05-11
Also the full output of

```
ifconfig
```

---

### Post by Iowan on 2009-05-11
Comment out (#) the extra lines in /etc/network/interfaces (so you can put them back if things get worse - leave **auto lo** and **iface lo inet loopback**), and restart networking.

---

### Post by lightsound952 on 2009-05-11
Oh my, This is special.

I was attempting to set up a dhcp server which involves changing a few configuration files. I finally got the dhcp server to send an appropriate ip address, broadcast address, subnet address, etc. to the client computer and my internet crashed. 
sudo ifup wlan0 -> Ignoring unknown interface wlan0=wlan0
I believe the only changes I made were to /etc/network/interfaces , /etc/default/dhcp-server.conf , /etc/dhcp3/dhcpd.conf , /etc/rc.local , and /etc/sysctl.conf but there might have been more.. Also thinking about it now I may have accidentally removed a package prefixed dhcp in synaptic (Not sure if that has anything to do with this though.)

Having internet on my host computer is more important than having it as a gateway. I am currently running off a live disk and my wireless is working. 

Maybe I should've started testing a dhcp server on a live disk... Oh well.

Uhm.. Oh right. If anyone can explain to me what configuration file could cause this sort of disaster I would be oober happy. I would give you a copy of the log file... but that's a lot of typing since I'm on a live disk.. And uhm.. Thanks?

---

### Post by lightsound952 on 2009-05-11
Update.
/etc/network/interfaces , /etc/default/dhcp3-server.conf , /etc/rc.local , and /etc/sysctl.conf have all been reverted to the old content but there's still no change. Wireless still wont connect.

@tonytraductor 
  There's a couple ways I know of to solve this. The easiest is to insert an installation disk into the computer and run it through synaptic, you could also download it onto a flash drive from someone else's computer. There's probably more but I'm not that smart.

---

### Post by lightsound952 on 2009-05-13
After playing around with the files for a while I've decided to give up. I installed an older distribution of ubuntu and my dhcp server is up and running, 9.04's network manager is too buggy for me. lol.

---

### Post by Dunhausen on 2010-06-09
I believe I solved this problem by adding the lines

```

auto wlan0
iface wlan0 inet dhcp

```

to /etc/network/interfaces

(fyi I had also installed wicd)

---

