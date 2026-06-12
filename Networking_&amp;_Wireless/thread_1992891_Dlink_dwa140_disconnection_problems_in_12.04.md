---
title: "Dlink dwa140 disconnection problems in 12.04"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by buratino22 on 2012-06-01
Hey.


I've just finished upgrading to ubuntu 12.04 and I encountered problems with my WiFi dongle - dwa140 b1.
It constantly disconnects after a few minutes, especially when used to pass large amounts of data and the data rate is slow.
The same dongle works fine in windows so I don't believe it's a hardware issue.

 I got it working in 11.10 when it had similar problems - I had to  black list rt28*/rt2x* from loading but after the upgrade the problem returned.
I tried all  solutions I could find. The following link summarizes some:
[(http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04)"][URL="http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04%5B/URL%5D"]http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04]("[http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04)[/URL]
 I compiled the rt5370sta driver successfully but when I black list all rt28*/rt2x* drivers the dongle is then not recognized.
modprobe did not help either.
Is it possible the firmware has to be updated?

lsusb
Bus 001 Device 005: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870]

lsmod | grep ^rt
rt5370sta             730263  0 
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb

What am I missing?

---

### Post by chili555 on 2012-06-01
First of all, rt5370sta is not correct for your device:> ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter([COLOR="Red"]rev.B1[/COLOR]) [Ralink RT2870]
The good and bad thing about the internet is that people are free to post solutions that may or may not apply to your revision of the device. Without the usb.id 07d1:3c09, there is no way to know if their DWA140 is the same chipset as your DWA140. It is therefor futile, in many cases, to follow a guide for an unverified chipset. 

My sermon is not directed at you, specifically, but as a caution to any and all searchers who may read this. You are not the first, last or only person to take an unnecessary detour. Trust but verify.

You may as well remove rt5370sta from /etc/modules. I assume you added it to get it to load automatically, which it wouldn't do because it sees no hardware it can drive. Next, please try:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
```Does it help? If so, we'll need to write a quick file to make it persistent. May I see:```
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by buratino22 on 2012-06-01
Hey chili555 and thanks for your reply.
I've modprobed the rt2800usb driver but there doesn't seem to be a big change. 
It's possible that the disconnections occur less often, but I'm not sure and they're still there.
I've attached the result of the scan and iwconfig after I removed cells I'm not connected to and some MAC addresses.
Ariel.

---

### Post by chili555 on 2012-06-01
> I've attached the result of the scan and iwconfig I don't see anything remarkable that I suggest you fix.> Is it possible the firmware has to be updated?Let's try. Please download the attached file to your desktop. Right-click it and select *Extract Here*. Now open a terminal and we'll back up your existing firmware. Like my mother-in-law, we never throw anything away!```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak

```Now, we'll copy over the latest (from Ralink's website) firmware:```
sudo cp Desktop/RT2870_Firmware_V22/rt2870.bin /lib/firmware/
```Now we unload and reload the driver so it grabs the newer firmware:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Any improvement?

---

### Post by buratino22 on 2012-06-01
Hi again.
It seems both firmware files are identicle, but I did download the FW again and replaced it in /lib/firmware but to no avail!
I'm glad you listen to you mother in law, it might make your life easier...:-)

What can I do next?

---

### Post by chili555 on 2012-06-01
> It seems both firmware files are identicle,I don't believe they are. Please run:```
md5sum /lib/firmware/rt2870.bak [COLOR="Red"]<--the old one[/COLOR]
md5sum /lib/firmware/rt2870.bin [COLOR="Red"]<--the new one[/COLOR]
```Are they the same?

Wonder what Network Manager is doing all this time. While your connection is misbehaving, please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

Sometimes, maybe even often, the fault is not necessarily the driver; it may be Network Manager, wpa_supplicant or even the router.

---

### Post by buratino22 on 2012-06-01
The firmware files were not identical but as I said, I already tried the new firmware from the RALink site and it didn't help.
When the disconnection occurs there is no special output in the syslog.
I've also disabled IPV6 in my wifi connection. 

syslog output:
>  <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'XXXX'.
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> dhclient started with pid 2572
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  1 20:35:54 ubuntu NetworkManager[911]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info>   address 10.0.0.1
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info>   prefix 24 (255.255.255.0)
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info>   gateway 10.0.0.138
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info>   nameserver '10.0.0.138'
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  1 20:35:57 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> DNS: starting dnsmasq...
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> Policy set 'XXXX' (wlan0) as default for IPv4 routing and DNS.
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> Activation (wlan0) successful, device activated.
Jun  1 20:35:58 ubuntu NetworkManager[911]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.


---

### Post by chili555 on 2012-06-02
As you've said, there is no sign of disconnects here, making it difficult to see what's going amiss. I am, however, interested in this:> Jun 1 20:35:57 ubuntu NetworkManager[911]: [COLOR="Red"]<info> address 10.0.0.1[/COLOR]
Jun 1 20:35:57 ubuntu NetworkManager[911]: <info> prefix 24 (255.255.255.0)
Jun 1 20:35:57 ubuntu NetworkManager[911]: <info> [COLOR="Red"]gateway 10.0.0.138[/COLOR]
Jun 1 20:35:57 ubuntu NetworkManager[911]: <info> nameserver '10.0.0.138'Is there a router or other access point that has a DHCP server running that gives you an x.1 address? And the address of the access point is x.138?? That seems very unusual. Please tell us more about your configuration.

---

### Post by buratino22 on 2012-06-02
The AP is a Netgear VV2000 running a V2.7.21_[2.7.21]("tel:2.7.21")_test1  FW.
It's a wan modem + AP which I got from the ISP as is.
It was a bit odd that the router would take a higher ipv4 address , but I encountered no problems with it so far  using Windows wireless from this and other computers in the same  network. 
Just to fend off problems I reconfigured the AP ip address to 10.0.2.10 and the DHCP address pool to start at 10.0.2.11. I got 10.0.2.12 this time.
There was no change in the disconnection problem and again the syslog showed no change (other than the new ip's i changed). I don't think it's the router's fault.

Thinking there might have been some upgrade problem I tried a 12.04 live CD but encountered the exact same behavior. 

 Ariel.

---

### Post by chili555 on 2012-06-02
Is your router set to WPA and WPA2 mixed mode? WPA2 only is preferred. Grasping at straws a bit here, may I see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```I am running low on mojo.

---

### Post by buratino22 on 2012-06-02
It's WPA2 only (AES).
 ```

 cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
 minstrel_ht
 
``` Just on a hunch I had a few days ago (when reading  the compilation  instructions for the rt5370sta driver - which you told me doesn't fit) I  tried changing my AP to WEP encryption and the problem persisted.
 Lets recap - 
 1. We don't think it's the dongle itself as it works fine in windows for long periods of time.
 2. It's probably not the firmware since we replaced it.
 3. It's not the router or encryption, and probably not the supplicant since we tried with different encryption methods.
 I still have the tingling sensation this has something to do with the driver or power management.
 
 Can't blame you for running out of Mojo I feel lost too...
 I have another WiFi donge which I tried but unfortunate it's not fully  supported (TL-WN821N). the TP-Link dongle works faster, but also suffers  from disconnections, more of them. I couldn't get the TP-Link to work  under 11.10 so I'm pessimistic.
 Can we deduce  something from this?  The drivers are different, naturally (Atheros HW)
 would printouts of the same commands (syslog, scan etc.) help in someway?
 Thanks,
 Ariel.

---

### Post by chili555 on 2012-06-02
> I still have the tingling sensation this has something to do with the driver or power management.I never fight the tingle. Let's try:```
sudo iwconfig wlan0 power off
```Any improvement?

I notice your iwconfig shows N speeds. Is there improvement with N turned off in the router?

---

### Post by buratino22 on 2012-06-02
There's no improvement when disabling power management and my routers' 801.11n can't be manually disabled it seems.

Is there some way to disable 801.11n on my Ubuntu?
Any other ideas?
Ariel.

---

### Post by chili555 on 2012-06-02
> The AP is a Netgear VV2000> my routers' 801.11n can't be manually disabled it seems.Could you please double-check the exact model number?

---

### Post by buratino22 on 2012-06-02
The model is VVG2000. I believe it's a model made especially for my  ISP/Infrastructure provider and not sold directly to consumers.
 It's fairly new (just got it a few weeks ago)
 You know of another model NetGear which allows disabling 801.11n?
 Ariel.

---

### Post by chili555 on 2012-06-02
You might look for and select 'Legacy Mode' as shown attached. I am not sure it will help, but I think we should try. Netgear isn't clear about what these modes represent, but 54Mbps and below are B or G and speeds above that are various N modes. 

Some drivers in Linux are troubled by N or won't do N at all. Sometimes we pick the least objectionable alternative: not working at all or working at lower speeds. If and when we find a fix, we'll find or add to an existing bug report.

---

### Post by buratino22 on 2012-06-03
Hey.

Thank you.
decreasing the AP speed to 54Mbps seems to solve the disconnection problem.
Should we keep investigating this? Is this some bug with supporting N in the rt28/x driver?
Ariel.

---

### Post by buratino22 on 2012-06-03
Hi.

Great success! - It seems that setting my AP speed to 54Mbps solved the disconnection problems.
Does this indicate some problem with the rt2800 driver or supplicant?
How can we investigate this further?
Thanks again,
Ariel.

---

### Post by chili555 on 2012-06-03
It's probably a bug in the driver. I suggest you file a bug report here: [http://rt2x00.serialmonkey.com/wiki/index.php/Rt2x00Wiki:Bug_reports](http://rt2x00.serialmonkey.com/wiki/index.php/Rt2x00Wiki:Bug_reports)

I'm very glad it's working! The searchers will appreciate if you use thread tools at the top and mark Solved.

---

### Post by brandon88tube on 2012-06-03
Did you change this in your router or somewhere in linux? If it was the latter, could you explain how one would go about doing this as I'm having the same issue of constantly getting disconnected whenever I have a lot of network activity (downloading a lot of stuff). I have the same dwa-140 rev. b1 usb device and I never had this problem until I upgraded to 12.04. Before, all I had to do was blacklist the rt2800 and rt2x000 drivers in order to get it working properly, but of course they had the brilliant idea of getting rid of the rt2870sta driver. Obviously, they didn't test the new rt2800 one enough and figured that it worked. I even tried compiling the old 2010 rt2870 driver from ralink's site, but it keeps failing on the make with 2 errors. So, I can't even use that driver.

---

### Post by buratino22 on 2012-06-03
> Did you change this in your router or somewhere in linux?

I changed the network speed in my router settings.
AFAIK 2870 is old and its' use is discouraged but it's worth a shot. what were your compilation errors? 
As for the new drivers I'll issue a bug report as suggest here when I get the chance, hope fully it's a solvable driver issue.

---

### Post by chili555 on 2012-06-03
> Did you change this in your routerYes, in the router. The poster logged on to the administrative pages of the router and looked for wireless settings and changed to 'legacy mode.' It may be and probably is different in yours. What is the make and model of your router; perhaps I can help.> AFAIK 2870 is old and its' use is discouraged but it's worth a shot. what were your compilation errors? Correct. It is doubtful you'll get it to work on a 3.2-xx kernel, it hasn't been updated since rt2800usb is (???) mainline.

---

### Post by brandon88tube on 2012-06-03
I was hoping it would've been in linux because I use N speeds in Windows and on my phone. Router isn't a good option for me. Ugh, now I'm going to have to mess around some more and waste a bunch of time.

---

