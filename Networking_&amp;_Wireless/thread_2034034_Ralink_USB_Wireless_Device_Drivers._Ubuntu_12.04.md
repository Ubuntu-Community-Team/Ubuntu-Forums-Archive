---
title: "Ralink USB Wireless Device Drivers. Ubuntu 12.04"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by nebbynebneb on 2012-07-27
First time poster on here since installing Ubuntu on my custom PC build. I have a Ralink Wireless USB adapter that I plan on using as a means to connect my PC to my router, however due to the awful instructions and install CD provided by the manufacturer, I cannot work out how to install the drivers of the device. Anyone who has particular knowledge in this field (*cough* chili *cough*) would be greatly appreciated here! Incase you guys were wondering I've already looked for solutions in 10+ threads and couldn't find anything. Also I have zero internet access on my Ubuntu PC so any downloads I make will be on my Macbook which does currently have internet access and then transferred via USB to the PC. Any help would be appreciated guys!

---

### Post by chili555 on 2012-07-27
You rang?? Please insert the device and run and post:```
lsusb
lsmod | grep rt2
rfkill list all
```Thanks.

---

### Post by nebbynebneb on 2012-07-27
The legend has arrived.

```
benjaminpc@benjamin-pc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 003: ID fafa:fafa  
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
benjaminpc@benjamin-pc:~$ lsmod | grep rt2
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              55301  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
benjaminpc@benjamin-pc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by chili555 on 2012-07-27
> rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              55301  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211Looks like you have plenty-o-drivers already. Let's see:```
iwconfig
sudo iwlist wlan0 scan
```You don't need to post extensive scan results; just tell me it scans or else an error or other message if it doesn't.

---

### Post by nebbynebneb on 2012-07-27
for the iwconfig I got no wireless extensions on; lo, eth1 and eth0 and then this for wlan0.
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

Then when I tried to scan wlan0 it said that the interface doesn't support scanning because the device or resource is busy.

---

### Post by chili555 on 2012-07-27
> interface doesn't support scanning because the device or resource is busy.Verrrry interesting. We wonder what is busy and why.```
dmesg | grep -i rt2
```

---

### Post by nebbynebneb on 2012-07-27
I think I may know what it is, I am using a USB lead hooked up to my iPhone as a means of gaining access to the internet to paste code to you, this might be interupting something? If not I also have 1 storage USB device plugged in and a USB device used for my wireless mouse. Here is your code.

```
[   69.754515] Registered led device: rt2800usb-phy0::radio
[   69.754523] Registered led device: rt2800usb-phy0::assoc
[   69.754531] Registered led device: rt2800usb-phy0::quality
[   69.754538] usbcore: registered new interface driver rt2800usb
[ 1089.060495] Modules linked in: ipheth arc4 rt2800usb rt2800lib crc_ccitt rt2x00usb rt2x00lib mac80211 cfg80211 nls_utf8 isofs bnep rfcomm bluetooth parport_pc ppdev nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_hdmi snd_hda_codec_via snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device mei(C) snd lp parport mac_hid soundcore snd_page_alloc video atl1c usbhid hid usb_storage

```

---

### Post by chili555 on 2012-07-27
> I think I may know what it is, I am using a USB lead hooked up to my iPhone as a means of gaining access to the internet to paste code to you, this might be interupting something?I believe so. I think Network Manager is saying that the iPhone has connectivity so it's using it and has set aside the Ralink. You probably selected it in NM.

If you detach the iPhone and wait a few moments for NM to notice the change of state, can you scan? Can you click the NM icon, see networks and connect?

---

### Post by nebbynebneb on 2012-07-27
Yeah it worked fine that time completed the scan. The USB is clearly picking up my router and can connect to it, it just won't connect the internet after this. If it makes any difference, after I connect to my router I constantly get the pop up saying that I've been disconnected and that I am now offline.

---

### Post by chili555 on 2012-07-27
While it seems to be connected, please run:```
iwconfig
```We are interested in your signal quality. We might also try a driver parameter:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=Y
```Is your router set to mixed mode WPA and WPA2? You will probably have better luck with WPA2 only.

---

### Post by nebbynebneb on 2012-07-27
Signal quality appears to be awful. 

```
wlan0     IEEE 802.11bgn  ESSID:"SKY79578"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1F:33:7C:AB:88   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=27/70  Signal level=-83 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:13   Missed beacon:0

```

When I entered in the second bit of code you said nothing came up other than the 'sudo' request for my password. Was that meant to happen?

---

### Post by chili555 on 2012-07-27
> When I entered in the second bit of code you said nothing came up other than the 'sudo' request for my password. Was that meant to happen?Yes. That means command accepted and there are no errors or warnings. That's what you want.> wlan0     IEEE 802.11bgn  ESSID:"SKY79578"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1F:33:7C:AB:88   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          [COLOR="Red"]Link Quality=27/70[/COLOR]  Signal level=-83 dBm  Yikes! Are you at all close to the router? Did the driver parameter make a difference in performance?

---

### Post by nebbynebneb on 2012-07-27
Also, not sure if what my router setting are and I have no idea how to find out. To be honest I don't know what WPA is anyway, not a huge nerd in router settings and what not and I didn't set up the router.

---

### Post by nebbynebneb on 2012-07-27
Didn't improve my performance much at all, went up to 29/70 :( You think this might be the problem?

---

### Post by chili555 on 2012-07-27
> **nebbynebneb said:**
> Didn't improve my performance much at all, went up to 29/70 :( You think this might be the problem?It almost certainly is.

I have to be away for a bit; back later. Pizza time!

---

### Post by nebbynebneb on 2012-07-27
****. My laptop is right next to my desktop though and the signal on that is perfect? 

Okay man, it's getting late here (GMT) and by the time you get back I'll most likely be off. If I don't reply within 20-30 of your next post I've probably gone to bed. I'm also out all day tomorrow for my Nan's birthday but might be on in the afternoon (your time), however if I am intoxicated I may be slightly hard to work with but we should hopefully find this easy to resolve!

---

### Post by nebbynebneb on 2012-07-27
Also, if it's any help my PC still keeps disconnecting/going offline and reconnecting to the network every 30 seconds, think this has anything to do with my dickballs connection?

---

### Post by chili555 on 2012-07-28
After a reboot, please let us have a look at:```
dmesg | grep algo
```Thanks.

---

### Post by nebbynebneb on 2012-07-28
Hey I'm back home now and will be on for around another 4 hours. Let's do this!

```
[     9.182246] ieee80211 phy0: Selected rate control [COLOR="Red"]algo[/COLOR]rithm 'minstrel_ht'
```

---

### Post by nebbynebneb on 2012-07-28
Just did that bit of code again because I wasn't sure if I was connected to the network and I also got this line along with the previous one.

```
[   460.222606] ieee80211 phy1: Selected rate control [COLOR="Red"]algo[/COLOR]rithm 'minstel_ht'
```

---

### Post by chili555 on 2012-07-28
> Selected rate control algorithm '**minstel_ht**'Exactly right. Nothing wrong and therefor fixable there. All the reasonably easy fixes at this point require access to the router. Is the routers yours within which to change some settings? 

If you'd prefer to address other migraine-inducing fixes first,I'll be happy to help either way.

---

### Post by nebbynebneb on 2012-07-28
Router is mine yes however I will not be able to play around with settings until tomorrow as it is being used by many people in the household currently, think we can hold off until then?

---

### Post by chili555 on 2012-07-28
Well, I've been around since 2005 and 14,000 posts; I don't suppose I'll be going away anytime soon!

In the meantime, look on one of the other computers, ipconfig /a or whatever it is in That Other O/S, and find out the gateway address for your router, possibly something like 192.168.1.1. We'll use that later.

Do you have a time UTC in mind? Depending on the Formula One broadcast, I can try to be available then.

---

### Post by nebbynebneb on 2012-07-28
The IP I type into my address bar to edit my router settings is 192.168.0.1 if that's what you mean? 
I'm available anywhere between 12pm UTC to 12am UTC from what I know, take your pick!

---

### Post by nebbynebneb on 2012-07-29
Tell me when you are here bossman, I'm ready when you are :)

---

### Post by nebbynebneb on 2012-07-29
I have made some progress!! After manually entering IPv4 Settings under the wireless connections tab I am able to connect to my router and I also get the 'Connection Established' pop-up. However I am still unable to connect to any internet pages and after a minute of so I get disconnected from the router. I hope this helps draw us closer to a conclusion :P

---

### Post by chili555 on 2012-07-29
I am sort of here and sort of in the stands at Hungaroring. I suggest you go into the router's administration pages and:

# Check under wireless security and set it to WPA2 only; not some mixed WPA and WPA2 mode.

# See if there is any setting for signal strength; make sure it is set to 100%. Please see attached for an example from another router. Notice the transmit power is set to High.

# Try some other channel with, perhaps, less interference. I have good luck with 1 and 11. 

Save your settings and close out of the router and check again:```
iwconfig
```Any improvements?

Go, Lewis!

---

### Post by nebbynebneb on 2012-07-29
Wow, you are gonna have a lot to catch up on when you get back! Just looked on my Router Settings page (192.168.0.1) and checked the attached devices tab to see if my router is picking up on my computer. I set the unique IP address for my computer as 192.168.0.21 and although my computer is saying connection established my router is saying that the device isn't even connected. I have no idea what is going on here!!

---

### Post by nebbynebneb on 2012-07-29
Right I am on my settings page and looking at what I can do. I am currently using WEP and my other two options are WPA-PSK and WPA-802.1x, which one would you like me to use?

---

### Post by chili555 on 2012-07-29
WEP is pretty insecure, so I'd strongly recommend WPA[COLOR="Red"]2[/COLOR]-PSK, if it's available; otherwise WPA-PSK.

---

### Post by nebbynebneb on 2012-07-29
Just changed the settings and on both Channels 1 and 11 and even after a reboot my PC could no longer establish a connection with my router.

---

### Post by nebbynebneb on 2012-07-29
Just tried again and got a signal strength of 41/70, it's getting better for sure!

---

### Post by chili555 on 2012-07-29
What does this tell us?```
iwconfig
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=Y
iwconfig
```What do the signal quality readings look like with the driver parameter applied?

---

### Post by chili555 on 2012-07-29
> my PC could no longer establish a connection with my router.Were you challenged for a *WPA* password?

---

### Post by nebbynebneb on 2012-07-29
After doing the driver parameter it's not even showing a 'proper' connection to my router. I'm not challenge for a WPA password as such but I am being constantly challenge to provide **A** password

---

### Post by chili555 on 2012-07-29
> **nebbynebneb said:**
> After doing the driver parameter it's not even showing a 'proper' connection to my router. I'm not challenge for a WPA password as such but I am being constantly challenge to provide **A** passwordGotcha! The popup is a bit different now.

Once you supply the WPA password, what happens next?

---

### Post by nebbynebneb on 2012-07-29
No, the pop-up is exactly the same as any other time my computer has asked me for a password. I provide the password and then nothing happens, I try *iwconfig* and I can't get associated with an access point or an ESSID, then a minute later the pop-up asking me for my password comes back and the process repeats.

---

### Post by chili555 on 2012-07-29
> No, the pop-up is exactly the same as any other time my computer has asked me for a password.That's correct. It is, in fact, different now in Ubuntu 12.04's version of Network Manager than it was in older versions. What does this tell us?```
iwconfig
```Lewis wins!!

---

### Post by nebbynebneb on 2012-07-29
Right I have come to a conclusion. I just used a telephone extension line to run my router upstairs to my room and try see if the signal makes any difference, it did. I instantly connected to the router when it was next to my PC as opposed to downstairs. I'm going to play around with the location of my router until I can find a spot where it can be permanently seated and can also provide me with a connection. Thanks for all your help Chili, you da man!! If you have any suggestions of what I can do to boost my signal I'd love to hear them!

---

