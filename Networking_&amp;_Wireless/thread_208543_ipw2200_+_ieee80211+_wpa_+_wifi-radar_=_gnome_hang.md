---
title: "ipw2200 + ieee80211+ wpa + wifi-radar = gnome hangs"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by JustDave on 2006-07-03
I have a Toshiba Satellite, model 1415-S173. The CD/DVD combo drive failed so I replaced it with an upgrade off of eBay. While looking around I figured I'd add an internal wireless card and RAM. Everything installed fine.

Not knowing anything about Ubuntu working with the ipw2200BG card I googled it and came up with this link:
[ http://ubuntuforums.org/showthread.php?t=26623]("http://ubuntuforums.org/showthread.php?t=26623")

Following the steps outlined in the first post from the above link I started off with:[INDENT][B]sudo apt-get update
 sudo apt-get install build-essential
 sudo apt-get install gcc
 sudo apt-get install linux-headers-$(uname -r)[/B][/INDENT]This went smoothly. (I have kernel 2.6.15-25-386, btw)


Using **dmesg | grep ipw** showed that I had driver version 1.1.1 with a warning that I should upgrade. I forget what the reason was that it listed. I then looked at the firmware recommendation here:
[http://ipw2200.sourceforge.net/firmware.php]("http://ipw2200.sourceforge.net/firmware.php")

I downloaded the **v3.0** package for driver **1.1.1** and above.

Before I could follow the next steps I had to create the /usr/lib/**hotplug/firmware/** directory:[INDENT][B]sudo tar xvzf ipw2200-fw-3.0.tgz
sudo cp ipw2200-*.fw /usr/lib/hotplug/firmware/[/B][/INDENT]Then I downloaded the latest ieee80211 subsystem (1.1.14) from here:
[http://prdownloads.sourceforge.net/ieee80211/]("http://prdownloads.sourceforge.net/ieee80211/")

I executed the following commands without issue:[INDENT][B]sudo tar xvzf ieee80211-1.1.14.tgz
cd ieee80211-1.1.14
sudo sh remove-old[/B][/INDENT]Then I downloaded the latest ipw2200 driver (1.1.3) from here:
[http://prdownloads.sourceforge.net/ipw2200/]("http://prdownloads.sourceforge.net/ipw2200/")

I executed the following commands without issue:[INDENT][B]cd ..
sudo tar xvzf ipw2200-1.0.6.tgz
cd ipw2200-1.0.6
sudo sh remove-old[/B][/INDENT]Then I make/installed ieee80211 without issue:[INDENT][B]cd ..
cd ieee80211-1.0.3
make
sudo make install[/B][/INDENT]Then I make/installed ipw2200 without issue:[INDENT][B]cd ..
cd ipw2200-1.1.3
make
sudo make install
[/B][/INDENT]When I went to install the **wpa_supplicant** package I was informed that I already had the latest installed. I then used the following command:[INDENT]**sudo gedit /etc/wpa_supplicant.conf**
[/INDENT]The file was blank so I added the following but with the info needed for my AP:
[INDENT][B]ctrl_interface=/var/run/wpa_supplicant
  
network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="your_secret_key"
}[/B]
[/INDENT] 
I then rebooted and issued the following command:
[INDENT]**dmesg | grep ipw**
[/INDENT] This gave me the following information:
[INDENT][B]ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.3 dmprq
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)[/B]
[/INDENT] 
Feeling rather pleased with myself up to this point I issued the following command:
[INDENT]**sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd**
[/INDENT] This returned the following message:
[INDENT]**Daemonize..**
[/INDENT] 
Not knowing I should be seeing more (or at least I think so from further reading) I believe all is well at this point. I then proceed to create the sh script to automatically start WPA at boot:
[INDENT]**sudo gedit /etc/init.d/wifi_wpa.sh**
[/INDENT] to which I added these lines:
[INDENT][B]#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w
fi
  
exit 0
  [/B][/INDENT] I then change the script's permissions and create a link to it:
[INDENT][B]sudo chmod +x /etc/init.d/wifi_wpa.sh
sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa[/B]
[/INDENT] 
Now I'm excited. I reboot looking forward to some wifi goodness. Unfortunately Gnome hangs at the splash screen. I then reboot to recovery mode and work back and forth removing steps in reverse until Gnome loaded. The last step removed was the creation of the **wpa_supplicant.conf** file.

By this time it was after 3 in the morning and I had to be to work in 4 hours so I left it well enough alone. After work, I looked for a wifi manager, thinking there must be something easier to do what I want and I came across **wifi-radar**. I installed this application using synaptic. I launched the program and edited the settings for the "default" network it listed.

I entered the following data:

Network name: [B]hotpoint
[/B]Mode: **auto**
Channel: **auto**
Key: **my_wpa_key**
Use WPA driver: **ipw**
Connection commands, After: **ifconfig eth1 mtu 1430**

I saved and tried connecting. That failed. I then changed **eth1** to **eth2** out of frustration while viewing the screen shot at [http://wifi-radar.systemimager.org/]("http://wifi-radar.systemimager.org/")

I saved and tried connecting. Success!!! Ok feeling good about myself again. I unplug the cat5 cable just to make sure and yes, I'm able to browse the net and check on my Gmail accounts, completely wireless. I shut down the laptop but then decided to find some sort of signal applet to display in the sytem tray. I turn the laptop on and watch it go through it's paces until it gets to the Gnome splash and then it hangs again.

I've tried removing the wifi-radar package, the wpasupplicant package and even removed/installed the ifconfig package but nothing seems to work. If anyone has some suggestions on getting my desktop back I'd greatly appreciate it. Thank you.

---

### Post by wieman01 on 2006-07-03
Interestingly I had the same issue with my "ipw2200". It hangs during the boot process because the system tries to sychronize the clock to "ntp.ubuntulinux.org" while the network is not(!) connected.

I experienced that my computer would not connect to my router / internet unless I restarted the network after the system startup. That's an odd thing, but I could NOT get it to work after a _**single**_ "ifup" or "/etc/init.d/networking start".

So my workaround is this:

1. Disable synchronization with to "ntp.ubuntulinux.org" (forgot which configuration file it is, but you will find it easily).
2. Start & immediately "restart" the wireless network during the boot process (play around with your boot scripts).

After this, the system should work alright. I know this is a bit ugly, but I gave up after a couple of sleepless nights. The same thing works perfectly with my "WUSB54G V4" so I cannot explain why the setup is an issue with the "ipw2200".

Hope this helps.

He

---

### Post by JustDave on 2006-07-05
Thanks :)

I ended up doing a fresh install of Dapper. I had previously upgraded the distro while waiting on a replacement CD drive. I think some of my problems stemmed from that.

After a fresh install of Dapper and adding some additional repositories I added wifi-radar again but this time I didn't add any configuration commands for "after" connecting. It's working great. It even seems to have set it's self up to auto connect after boot.

The network manager that was already installed didn't look like it supported WAP. I'll have to look again though to make sure.

Using **dmesg | grep ipw** again it says I should update the driver.

[INDENT][B]ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, ipw2200: Copyright(c) 2003-2006 Intel Corporation
Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)[/B][/INDENT]

I think I'll try updating them again along with the firmware. I think it will be ok this time around. lol

Just an edit note, I even disconnected the wireless connection using wifi-radar thinking that if the connection isn't there it wont use it. It still hung so I'm not so sure if it is the same problem as yours. :(

---

### Post by JustDave on 2006-07-05
[QUOTE=wieman01]Interestingly I had the same issue with my "ipw2200". It hangs during the boot process because the system tries to sychronize the clock to "ntp.ubuntulinux.org" while the network is not(!) connected.

I experienced that my computer would not connect to my router / internet unless I restarted the network after the system startup. That's an odd thing, but I could NOT get it to work after a _**single**_ "ifup" or "/etc/init.d/networking start".

So my workaround is this:

1. Disable synchronization with to "ntp.ubuntulinux.org" (forgot which configuration file it is, but you will find it easily).
2. Start & immediately "restart" the wireless network during the boot process (play around with your boot scripts).

After this, the system should work alright. I know this is a bit ugly, but I gave up after a couple of sleepless nights. The same thing works perfectly with my "WUSB54G V4" so I cannot explain why the setup is an issue with the "ipw2200".

Hope this helps.

He[/QUOTE]

I guess I shouldn't have jumped the gun on saying it was fine. I've got the same problem again but it's intermittent. If the first boot hangs at the gdm screen the second time through seems to work (or third). I'll try your work around and see if that fixes things. Thanks :)

---

### Post by wieman01 on 2006-07-06
> I guess I shouldn't have jumped the gun on saying it was fine. I've got the same problem again but it's intermittent. If the first boot hangs at the gdm screen the second time through seems to work (or third). I'll try your work around and see if that fixes things.

I suspected you would have the same problem because it continues to exist on my end even after an upgrade of all components. That's very odd... the log files don't really reveal anything either. 

In the first place I reckoned that this had to do with "ipv6" but the problem persists despite the fact that I have disabled the module. 

Would be interesting to hear what you do about it. I finally gave up because I can live with the workaround during startup (= restarting of network). 

He

---

### Post by awaldram on 2006-07-06
I have the same card 2200bg but no issues 

where I seem to differ is i'm using the wext driver in wpa_supplicant not ipw

so give it a whirl and see if it helps

---

### Post by wieman01 on 2006-07-06
> **awaldram said:**
> I have the same card 2200bg but no issues 

where I seem to differ is i'm using the wext driver in wpa_supplicant not ipw

so give it a whirl and see if it helps

Yeah... I am using Wext as well but to no avail. Must be something else.

He

---

### Post by awaldram on 2006-07-07
heres my wpa_supplicant.conf encase it helps

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin


network={
ssid="Pegasus"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="scarypasswordkey"
}

---

