---
title: "Karmic Koala as Bluetooth Access Point and Share its Internet Connection"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by guhpraset on 2010-01-08
How to set up my Karmic Koala 64 bit so it can acts as a Bluetooth access point and shares its internet connection with nearby bluetooth enabled devices.

The case is:

There is an Ubuntu64 9.10 desktop PC (with billionton bluetooth adapter plugged on its usb) connected to internet via adsl modem on its eth0.

Nearby, there are two cell phones (Moto q9h and SE m600i), both supports bluetooth networking. 

Now, i want to share the internet access on my PC to the phones, so they can surf the internet without wasting money on GPRS bills.

Is this possible? Please teach me how to do it.

Thank You

---

### Post by Dysport on 2010-01-08
There is a howto [here]("http://bluez.sourceforge.net/contrib/HOWTO-PAN") or check this one out [here]("http://ubuntuforums.org/showthread.php?p=4145133#post4145133")
I think the problem is rather whether your mobile phones support connecting to the internet over bluetooth. Usually they just support acting as a modem, so the other way round. If there is such a restriction in the proprietary firmware there is really not much you can do.

---

### Post by guhpraset on 2010-01-16
Thank You Dysport, unfortunately i am not smart enough to understand the tutorial provided on your links.

Recently i found easier and working tutorial [here]("http://artsownblog.blogspot.com/2008/06/bluetooth-pan-network.html").

I tried with two sony ericsson phones and succeed, both can browse in the same time. 

The weird problem is i can NOT connect using motorola q9h (windows 6.1), it failed to connect to the network, keep on searching service as if there is no service available.

---

### Post by Dysport on 2010-01-16
Does the normal pairing process work? If you for example want to transfer files over bluetooth?

---

### Post by guhpraset on 2010-01-16
Normal pairing works. Every device set to trust each other.

Transfer files over bt:
Ubuntu >>> SE phones = OK
Ubuntu >>> Moto windows mobile = OK
SE Phones >>> Ubuntu = OK, popup asking to receive file appear.
MOTO Winmo >>> Ubuntu = FAIL, no popup appared.

Fyi, this Moto works flawlessly on windows PC, even without Activesync, it able to browse the internet via bluetooth networking.

---

### Post by Dysport on 2010-01-17
Have you installed the package "gnome-bluetooth"?
```
sudo aptitude install gnome-bluetooth
```

This will install a program named "Bluetooth File Sharing", accessible under "Applications" -> "Accessories". Once started you should see a new symbol in your panel:
[IMG]http://freiesoftware.files.wordpress.com/2008/09/gnome-blue.jpg[/IMG]

---

### Post by guhpraset on 2010-01-17
to install Gnome-bluetooth, synaptic needs to remove blueman. 
I need blueman. So i dont want to do your suggestion.
I dont need file sharing, what i need is internet sharing. And it is quite solved now, partially.

Thank You

---

### Post by walmis on 2010-01-18
> **guhpraset said:**
> to install Gnome-bluetooth, synaptic needs to remove blueman. 
I need blueman. So i dont want to do your suggestion.
I dont need file sharing, what i need is internet sharing. And it is quite solved now, partially.

Thank You

Blueman has access point functionality.

Right click blueman applet, click local services, click network, tick "Network Access Point", tick "Enable Routing" and click apply.

---

### Post by Dysport on 2010-01-18
Did you get it running by now? If yes how did you do it? Just out of curiosity…

---

### Post by guhpraset on 2010-01-20
Yes, Dysport, i get it run, BUT in VERY unpractical way.

Now this windows mobile 6.1 can connect to the internet using ubuntu karmic's internet, via bluetooth networking.

Required to application:
On ubuntu karmic: blueman and firestarter
On windows mobile 6.1: registry editor

What i do:
1. On Blueman applet, right click, local adapters,
- Check NAP
- Check NAT,
- dnsmasq
- fill IP Address with 10.0.0.1
- PAN support on NetworkManager
- DUN support on Blueman

2. On windows mobile 6.1, edit the registry, (HKLM >> Comm\BTCEPAN1\Parms\TCPIP)
- disable DHCP (by set to 0)
- disable AutoCfg
- DNS to 8.8.8.8
- DefaultGateway 192.168.0.1
- IpAddress to 192.168.0.2
- Subnetmask to 255.255.255.0

3. Initiate connection from winmo to karmic (Bluetooth Manager > Personal Network > add your ubuntu)

4. After connection, in ubuntu terminal.
'ifconfig' commands will show that bnep0 now appeared, without ip address
now give it an Ip address, in my case i choose 192.168.0.1.
command: sudo ifconfig bnep0 up 192.168.0.1

5. Using firestarter, enable internet sharing with bnep0

Done.  Now winmo should able to browse the internet, just make sure the opera connection setting set to "work", not "the internet".
NOTE:
- Everytime you reconnect winmo to ubuntu, you need to repeat step 4 and 5.
- I have messed my ubuntu by following few 'not working tutorial' before, maybe i missed some step.

Now another question is.. *should i start this in another thread?*
Is it possible to make the step easier? We can do it VERY easy using SE phones, they connect easily without requiring user to touch ifconfig nor firestarter.

---

### Post by Dysport on 2010-01-20
When you connect one of the other phones (that work flawlessly), what does it say when you type 'ifconfig bnep0'?

To me it looks like the Windows phone is expecting a dhcp lease but your computer does not act as a dhcp server. Thus installing and configuring dhcp3-server may resolver your problem.
Also, have you tried bridging bnep0 and your network adapter in /etc/network/interfaces?

---

### Post by walmis on 2010-01-21
> **guhpraset said:**
> Yes, Dysport, i get it run, BUT in VERY unpractical way.

Now this windows mobile 6.1 can connect to the internet using ubuntu karmic's internet, via bluetooth networking.

Required to application:
On ubuntu karmic: blueman and firestarter
On windows mobile 6.1: registry editor

What i do:
1. On Blueman applet, right click, local adapters,
- Check NAP
- Check NAT,
- dnsmasq
- fill IP Address with 10.0.0.1
- PAN support on NetworkManager
- DUN support on Blueman

2. On windows mobile 6.1, edit the registry, (HKLM >> Comm\BTCEPAN1\Parms\TCPIP)
- disable DHCP (by set to 0)
- disable AutoCfg
- DNS to 8.8.8.8
- DefaultGateway 192.168.0.1
- IpAddress to 192.168.0.2
- Subnetmask to 255.255.255.0

3. Initiate connection from winmo to karmic (Bluetooth Manager > Personal Network > add your ubuntu)

4. After connection, in ubuntu terminal.
'ifconfig' commands will show that bnep0 now appeared, without ip address
now give it an Ip address, in my case i choose 192.168.0.1.
command: sudo ifconfig bnep0 up 192.168.0.1

5. Using firestarter, enable internet sharing with bnep0

Done.  Now winmo should able to browse the internet, just make sure the opera connection setting set to "work", not "the internet".
NOTE:
- Everytime you reconnect winmo to ubuntu, you need to repeat step 4 and 5.
- I have messed my ubuntu by following few 'not working tutorial' before, maybe i missed some step.

Now another question is.. *should i start this in another thread?*
Is it possible to make the step easier? We can do it VERY easy using SE phones, they connect easily without requiring user to touch ifconfig nor firestarter.

You're doing it wrong :)
bnep interfaces are added to pan1 bridge, so no need to configure them explicitly. Also make sure the ip you specify in blueman is not in a subnet of your existing network. 
After connecting Windows mobile, it should receive a dhcp offer within 30 secs.

---

### Post by Dysport on 2010-01-21
> **walmis said:**
>  Also make sure the ip you specify in blueman is not in a subnet of your existing network. 

That sounds very plausible. We've had similar problems with vpn and and IPs in the same subnet.
Did it work with the specified changes?

---

### Post by guhpraset on 2010-01-21
> **Dysport said:**
> When you connect one of the other phones (that work flawlessly), what does it say when you type 'ifconfig bnep0'?

ifconfig does exactly the same. bnep0 only appeared when a phone connected to pc. K618 and M600i from SE can connect and browse without requiring me to do anything, while for moto q9h i have to give an ip address to bnep0 and setup internet sharing before it can enjoy the internet.

> **Dysport said:**
> To me it looks like the Windows phone is expecting a dhcp lease but your computer does not act as a dhcp server. Thus installing and configuring dhcp3-server may resolver your problem.

I have dhcp3-server installed, maybe it come bundled with my karmic, how to configure it?

> **Dysport said:**
> Also, have you tried bridging bnep0 and your network adapter in /etc/network/interfaces?
I'm not sure maybe firestarter did it for me. How to "bridging bnep0 and eth0"?

---

### Post by guhpraset on 2010-01-22
> **walmis said:**
> You're doing it wrong :)
bnep interfaces are added to pan1 bridge, so no need to configure them explicitly.

yes i  must be doing it in wrong way, it is very uncomfortable. But it is working. Without giving an ip to bnep0 and setup internet sharing on firestarter, the winmo phone cant browse the internet, cant even do a ping.

> **walmis said:**
>  Also make sure the ip you specify in blueman is not in a subnet of your existing network. 
After connecting Windows mobile, it should receive a dhcp offer within 30 secs.
sorry, i dont understand, i know almost nothing about networking, could you please just give me a "how to"?

While i enabled dhcp, iptools said that winmo did received an ip, but its gateway stays blank, no matter i messed the winmo registry it keeps blank, thats why i choose to set it manual. A clear how to will very helpful.

---

### Post by walmis on 2010-01-22
Ok, first uninstall dhcp3-server, dnsmasq packages. Leave only dnsmasq-base.
Then set IP address on your winmobile to automatic.
Get the latest version of blueman (1.21)
Get rid of firestarter (it's old and buggy)
reboot.
Now set ip address in blueman to something random, like 10.214.94.1
make sure dnsmasq and nat are checked and click apply.

Now you can connect your winmo phone. Wait about 30 secs and it should get an address.
Check ```
tail -f /var/log/syslog
``` to see if dnsmasq is getting any requests

---

### Post by guhpraset on 2010-01-22
@Walmis
I did what you told, and this is what happened:

Jan 22 22:21:45 KarmicKoala64 avahi-daemon[862]: Withdrawing address record for fe80::210:60ff:feeb:fe58 on bnep0.
Jan 22 22:21:59 KarmicKoala64 bluetoothd[832]: link_key_request (sba=00:10:60:EB:FE:58, dba=00:26:BA:2D:32:F9)
Jan 22 22:21:59 KarmicKoala64 bluetoothd[832]: Added new connection: bnep0
Jan 22 22:21:59 KarmicKoala64 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:43/bnep0, iface: bnep0)
Jan 22 22:21:59 KarmicKoala64 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:43/bnep0, iface: bnep0): no ifupdown configuration found.
Jan 22 22:21:59 KarmicKoala64 NetworkManager: <WARN>  device_creator(): /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:43/bnep0: couldn't determine device driver; ignoring...
Jan 22 22:22:01 KarmicKoala64 avahi-daemon[862]: Registering new address record for fe80::210:60ff:feeb:fe58 on bnep0.*.
Jan 22 22:22:10 KarmicKoala64 kernel: [ 7014.890007] bnep0: no IPv6 routers present
Jan 22 22:23:11 KarmicKoala64 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:43/bnep0, iface: bnep0)
Jan 22 22:23:11 KarmicKoala64 avahi-daemon[862]: Withdrawing address record for fe80::210:60ff:feeb:fe58 on bnep0.
-------now winmo initiate connection------   
Jan 22 22:24:18 KarmicKoala64 bluetoothd[832]: link_key_request (sba=00:10:60:EB:FE:58, dba=00:26:BA:2D:32:F9)
Jan 22 22:24:18 KarmicKoala64 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:42/bnep0, iface: bnep0)
Jan 22 22:24:18 KarmicKoala64 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:42/bnep0, iface: bnep0): no ifupdown configuration found.
Jan 22 22:24:18 KarmicKoala64 NetworkManager: <WARN>  device_creator(): /sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/bluetooth/hci0/hci0:42/bnep0: couldn't determine device driver; ignoring...
Jan 22 22:24:18 KarmicKoala64 bluetoothd[832]: Added new connection: bnep0
Jan 22 22:24:20 KarmicKoala64 avahi-daemon[862]: Registering new address record for fe80::210:60ff:feeb:fe58 on bnep0.*.
Jan 22 22:24:29 KarmicKoala64 kernel: [ 7153.850009] bnep0: no IPv6 routers present
-------now i try to browse using phone-------
nothing happened, phone complaining, it said "Could not locate remote server"

Could you please diagnose what is wrong?

Btw, please excuse me, i have to go out of town for few days, so my next response will be delayed for about a week. I will do your next clue as soon as i get back.
Thank You very much.

---

