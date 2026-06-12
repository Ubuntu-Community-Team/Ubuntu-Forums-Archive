---
title: "/etc/network/interfaces vs network manager"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2010-12-02
Hopefully this is a simple question.

When is /etc/network/interfaces used, and when is whatever network manager ships with whatever version of ubuntu used?

Is this behavior different for different versions of ubuntu?

---

### Post by chili555 on 2010-12-02
/etc/network/interfaces is a part of the manual way of doing things, along with the commands, iwlist, iwconfig, ifconfig and others.

Network Manager is the automated GUI way of doing all these things with little or no fuss.

Either will do the job equally well, assuming the network card driver is in place. As far as I know, all the Ubuntus use NM except the server version. Servers generally use no windowing manager and so NM is not possible.

These two systems are designed to be mutually exclusive; that is, use one or the other, not both. I have computers with and without NM; either work well. It is a bit harder to take my manual method computer to the coffee shop and connect, but not impossible.

---

### Post by not_a_phd on 2010-12-02
> **chili555 said:**
> It is a bit harder to take my manual method computer to the coffee shop and connect, but not impossible.

You are hard core! 

Follow up question: Are there any tips and tricks that you might have to offer regarding configuring Network Manager via the .conf file in the /etc/NetworkManager folder? Or, what to place in the /etc/NetworkManager/system-connections folder when things are funky with your setup?

---

### Post by chili555 on 2010-12-02
When I want to configure manually, I ditch NM altogether, as in sudo apt-get remove --purge network-man* and the write a proper /etc/network/interfaces file. If I really want to be hard-core, I dispense with /etc/network/interfaces altogether and just do iwconfig commands. My favorite moment was sitting beside an Apple fan-boi at a doctor's office, scanning to find an 802.11***a*** network and connecting as he cursed and struggled. He looked over at my terminal window all filled with Matrix-like green numbers and letters and said, "What tha....!" 

If I want NM to do the heavy lifting, I click the NM icon and sit back and sip my no decaf, no foam, plain-old coffee and watch it spin. For me, there is no in-between; fully manual or fully automatic (no Tiptronic!)

What are you trying to accomplish? Maybe we can work it out together.

---

### Post by not_a_phd on 2010-12-02
Thank you for asking! I am trying to maintain connection to a secured (WEP or WPA) home network where the router does not broadcast the SSID. Connection holds fine when the router is configured to broadcast the SSID, but disconnects every 5-seconds or so if the SSID is not broadcast by the router.

A debian site gave some cryptic advice on the /etc/network/interfaces file, saying: "Tip: If you have trouble connecting to a network because it does not broadcast its ssid, add 'scan_ssid=1' to its network stanza."

However, since I am using network manager, and I *really* like network manager (when it works), I was wondering if there was a way to slip in this configuration item. (Especially since I don't know what a "network stanza" is!! :redface: )

This option seems to tell the driver to expect a single character (presumably '\0') for the SSID name during a scan.

I have spent about 6-weeks getting to this point, and have been up to my elbows in driver source code and wpa_supplicant debug messages. I would like to see if I can get network-manager over the hump on this problem to be able to connect to a network where the SSID is not broadcast.

I have more data on the problem if you are interested... I was preparing for a mega-post in the morning. :D

---

### Post by chili555 on 2010-12-03
I rather imagine that Network Manager is changing to ssid_scan=1 all by itself. Let's look at the syslog:```
sudo cat /var/log/syslog | grep ssid
```Mine says, only slightly redacted:> Dec  3 06:40:51 LAPTOP40 NetworkManager[898]: <info> Config: added 'ssid' value 'mylilrouter'
Dec  3 06:40:51 LAPTOP40 NetworkManager[898]: <info> Config: added 'scan_ssid' value '1'If your syslog has filled and been saved, you may have to look in syslog.1.

I will be interested in your additional information. What wireless driver is being used?

---

### Post by not_a_phd on 2010-12-03
> **chili555 said:**
> I rather imagine that Network Manager is changing to ssid_scan=1 all by itself. 
I will be interested in your additional information. What wireless driver is being used?

You are correct (thus removing my last remaining thread of hope to get to the bottom of this)! Network manager was indeed performing the ssid_scan=1 operation as shown in your syslog.

I am presently using RaLink rt2860sta v2.4.0.0 drivers, downloaded from the RaLink site. These were compiled on my machine using Sven's exquisite instructions on this forum for setting the right flags in config.mk and also the right cipher in cmm_wpa.c. I also have version 26 of their firmware installed. 

I have configured the wpa_supplicant to output all of its debug messages to the syslog and its own output file by setting adding the "-dddt" option to the wpa_supplicant Dbus service EXEC= configuration option (per instructions given on the NetworkManager/Debugging site). This has provided a plethora of info that I can make little sense of. I have included a tar/gzip file of the syslog and wpa_supplicant output files that follow the boot and connection of my eeePC901 both with and without the router SSID broadcast enabled. You are free to parse through these, but I think the interesting part is extracted below...

With SSID broadcast disabled on my WPA/TKIP encrypted home network, I tailed the syslog with the command: 
```
tail -f /var/log/syslog
``` 
and would see a "CTRL-EVENT-DISCONNECTED removed keys" kernel message appear every 5-seconds or so. The network-manager would reconnect me like a champ, but I was suffering 20-30% packet loss while pinging my router. This wasn't good.

With the wpa_supplicant debug logging on, I could see the following messages around the disconnect event (these are also in the _nocast log files attached):
```

Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: Wireless event: cmd=0x8b15 len=20
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: Wireless event: new AP: 00:00:00:00:00:00
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: Setting scan request: 0 sec 100000 usec
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: Added BSSID 00:0f:66:0b:32:f7 into blacklist
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: State: COMPLETED -> DISCONNECTED
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: WEXT: Operstate: linkmode=-1, operstate=5
Dec  2 17:16:08 jim-laptop-0 NetworkManager[821]: <info> (ra0): supplicant connection state:  completed -> disconnected
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: EAPOL: External notification - portEnabled=0
Dec  2 17:16:08 jim-laptop-0 wpa_supplicant[954]: EAPOL: SUPP_PAE entering state DISCONNECTED

```

The interesting two lines of the log are:
> Wireless event: cmd=0x8b15 len=20
> Wireless event: new AP: 00:00:00:00:00:00

0x8b15 is SIOCGIWAP from include/linux/wireless.h which refers to a macro to 'get access point MAC addresses'. The AP MAC address returned is clearly invalid, resulting in the disconnect. 

I stumbled upon the whole SSID broadcast thing on the Debian site:[http://wiki.debian.org/DebianEeePC/HowTo/Wifi]("http://wiki.debian.org/DebianEeePC/HowTo/Wifi")

Here, they gave some cryptic advice on the /etc/network/interfaces file, saying: "Tip: If you have trouble connecting to a network because it does not broadcast its ssid, add 'scan_ssid=1' to its network stanza."

What this seems to do is tell the driver to expect a single character '\0' for the SSID name during a scan.

I thought that the correlation between my symptoms and the SSID thing was perhaps a memory offset issue in the code. Clearly the folks at Redhat are already on top of this fix though.

While my system works (very well) with the SSID broadcasted, and I have little reason to change it. I am still annoyed that it does not work when I don't broadcast the SSID. I would like to find the fix, if not for myself, for the children of the world! :D

---

### Post by chili555 on 2010-12-03
I'm not sure I have much to add. We could try manual methods and rule in/out Network Manager as the culprit, but that leaves wpa_supplicant, the driver and probably a few other things I haven't considered. May I assume there are no competing drivers loading and that you've used the conventional method to set up a hidden network in Network Manager? If so, frankly, I'm out of ideas. 

I have googled for ssid scan, rt2860sta, rt2860sta.dat, hidden and wpa_supplicant. I see variations on the theme but no silver bullet solution.

[http://wolfs-ubuntu.blogspot.com/2009_06_01_archive.html](http://wolfs-ubuntu.blogspot.com/2009_06_01_archive.html)> The driver does not connect to SSIDs that are hidden (as was the case with my WLAN). I had to set the router to show my SSID in order to get a connection. This was the reason it took me that long to figure out how to install.

---

### Post by not_a_phd on 2010-12-03
> **chili555 said:**
> I'm not sure I have much to add. We could try manual methods and rule in/out Network Manager as the culprit, but that leaves wpa_supplicant, the driver and probably a few other things I haven't considered. May I assume there are no competing drivers loading and that you've used the conventional method to set up a hidden network in Network Manager? If so, frankly, I'm out of ideas. 

I have googled for ssid scan, rt2860sta, rt2860sta.dat, hidden and wpa_supplicant. I see variations on the theme but no silver bullet solution.

[http://wolfs-ubuntu.blogspot.com/2009_06_01_archive.html](http://wolfs-ubuntu.blogspot.com/2009_06_01_archive.html)

Yeah, I am also in the out of ideas camp. While I am quite happy that I have found a solution that works for me, I really wanted to find a more generic solution.

A couple things still bother me. 1. The wireless on this machine worked and works flawlessly with my network with the hidden ssid on the Maverick Live CD. It does so even with the conflicting drivers loaded (rt2860sta+rt2800+rt28xx). 2. The wireless appeared to work in Karmic. It may be that the disconnects were happening in the background, and I had never looked at the syslog in the detail that I had when dealing with the completely failed wireless in Maverick. I may take the time to reinstall and look at this more closely. 

I am a little wary of going the totally manual route, as I am not terribly familiar (yet) with the driver/wpa_supplicant/ifconfig framework. If it did not work for me, I don't think I could say for sure that the problem wasn't introduced with my tinkering.

I don't think that I have conflicting drivers loading. I have blacklisted all of the rt28xx and rt2800 generic drivers. It may be possible that there is something compiled into the Ubuntu kernel that I am not aware of, but I haven't looked through the config file to see. A perusal of an lsmod listing doesn't show anything fishy to me.

I connected to the hidden network using the network manager gui. I clicked on the icon on the gnome panel, selected connect to hidden wireless network, entered the SSID name, encryption type, and key. It did the rest. I presume that is what you mean by conventional.

The Wolf's Ubuntu corner page was an excellent read. Thank you. I had not seen that one. Though, it looks like he is reporting the same deficiency, with no real solution except to turn on the ssid broadcast.

Thanks for looking at the problem. I will probably nibble at it from time to time. It might disapear with Natty as mysteriously as it appeared with Maverick, but I doubt it will.

---

### Post by chili555 on 2010-12-04
> A couple things still bother me. 1. The wireless on this machine worked and works flawlessly with my network with the hidden ssid on the Maverick Live CD. It does so even with the conflicting drivers loaded (rt2860sta+rt2800+rt28xx). Hmmm!

I wonder if it is rt2860sta that's at fault. Perhaps rt2800usb? pci?? will work. I suggest you try setting the router to not broadcast the SSID and then do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
```Or rt2800usb, if that's what you are using. Any improvement? I will be shocked if it does, because the reputation of the rt2800xx series is poor.

---

### Post by not_a_phd on 2010-12-04
> **chili555 said:**
> Hmmm!

I wonder if it is rt2860sta that's at fault. Perhaps rt2800usb? pci?? will work. I suggest you try setting the router to not broadcast the SSID and then do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
```Or rt2800usb, if that's what you are using. Any improvement? I will be shocked if it does, because the reputation of the rt2800xx series is poor.

Yes. I have been down that route already. What I have found is that the rt2800pci drivers work pretty well with my home network in nonbroadcasting-ssid+WEP mode. But, they do not work at all for my computer on any kind of WPA network (open or PSK).

---

