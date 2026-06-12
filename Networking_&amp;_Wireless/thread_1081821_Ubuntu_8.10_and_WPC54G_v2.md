---
title: "Ubuntu 8.10 and WPC54G v2"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by dlacertosa on 2009-02-26
I'm having trouble getting this PCMCIA card to work under Ubuntu 8.10.

I've ran through everything in the Comprehensive NDISWrapper Troubleshooting Guide ([http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)) and according to the guide my card should be working.

On initial installation of Ubuntu, I couldn't connect to any wireless networks and no wireless networks were found.

Then, I went the NDISWrapper route and installed the Windows drivers.  Wireless networks then showed up in network manager but I still couldnt connect to any wireless networks.  

My router does not broadcast SSID and I use WEP Encryption.  I was able to get another laptop to connect to the network so I'm sure it has to do with the wireless card on this particular laptop.

When I enter my 'hidden wireless' information and mouse over the network manager icon, it just says "Attempting to join the wireless network XXXXXXX ...." and then eventually says that I've been disconnected.  I am a noob with Linux so I don't know what to post here to help debug.  Any help would be appreciated.

---

### Post by dlacertosa on 2009-03-01
I've taken a look at my deamon.log file and it says:

<info> wlan0: link timed out
<info> Activation (wlan0/wireless): association took too long, failing activation.

---

### Post by dlacertosa on 2009-03-01
Problem fixed.

network-manager and network-manager-gnome were the problems.

After installing NDISWRAPPER and installing wicd ([http://wicd.net/](http://wicd.net/)) I was able to connect to my network without any problems.

---

