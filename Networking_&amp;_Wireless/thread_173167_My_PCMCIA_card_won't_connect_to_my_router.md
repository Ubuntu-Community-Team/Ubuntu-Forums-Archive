---
title: "My PCMCIA card won't connect to my router"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by FiReiSFuN on 2006-05-09
I have a Thinkpad R40e, with a Trendnet 421PC PCMCIA b/g card.  I can install the suggested drivers via Ndiswrapper, and have followed all of the faqs for the connection of the card to the router.

IWCONFIG shows me device wlan0 and it is configured, but I cannot connect to  my router.

IWLIST scans and detects my router, and in the Ubuntu network setup wizard the name of my router is listed, and after I enter the information for WEP encryption and accept, the device takes a long time to initialize, but refuses to connect to the router.

Running IWCONFIG again sees that my card is recognized as wlan0, but none of the wireless information from my router is entered, and it does not list the Mac ID of my router.

Any suggestions as to how to get a fully configured PCMCIA card connecting to my access point?

Any info would be well appreciated.

---

### Post by dickohead on 2006-05-09
It might just be me, but I have a linksys router and my wireless card ONLY ever works if I disable all encryption....

Really sucks, cos my range expander requires encryption to operate.

So try turning off encryption and broadcast the SSID and see how far that gets you.

---

### Post by FiReiSFuN on 2006-05-09
Hmm, I don't have a linksys router, its a D-Link, but I'll definately try disabling encryption and see what happens.  Thanks for the input.

---

### Post by jml on 2006-05-09
I agree with the previous posts.  I've read that WEP encryption does not work well with Ubuntu's graphical front end.  I've also read that setting up WEP at the command line by editing a configuration file does work.  If you can get an unencrypted connection working, then you know that your hardware setup is ok.  Here is a link to the wireless troubleshooting guide.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Hope this helps.

Joe

---

### Post by harisund on 2006-05-09
ok try this 
```

sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid Name_Of_Your_Wireless_Network
sudo iwconfig wlan0 key 13579086421234567890098765
sudo dhclient wlan0

```
And check if your internet works. ping, browse or whatever. 

Of course, don't forget to substitute Name_Of_Your_Wireless_Network with your wireless network name and the long number I have written with your own 'wep' key. 

I just hate the GUI anyway.

---

### Post by dickohead on 2006-05-10
Yeah, that GUI needs some serious fixer-uppers, like perhaps actually OBTAINING an IP address, really irritates me having to bring my interface down and up each time I change networks.

---

### Post by Durito on 2006-05-10
[QUOTE=dickohead]Yeah, that GUI needs some serious fixer-uppers, like perhaps actually OBTAINING an IP address, really irritates me having to bring my interface down and up each time I change networks.[/QUOTE]


Once you get connected, you can download wifiradar (I think it's called) through Synaptic. It's no Kismet, but it's an improvement.

---

