---
title: "Wireless works in one location but not another"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by browndog289 on 2010-09-27
Hello

I have been setting up an Ubuntu 10.04 32-Bit Desktop system for a customer. It is an old AMD Athlon system that I have connected an Edimax EW-7711UAn Wireless USB adaptor to - [http://www.edimax.co.uk/en/produce_detail.php?pd_id=261&pl1_id=1&pl2_id=44]("Edimax Website").

I initially had a problem where no wireless networks were found - but after reading on the web I discovered that it was loading two modules (rt2800usb and rt2870sta) so I added rt2800usb to the blacklist. I was then able to configure the system to connect my home wireless network on my Linksys WAG200G router. It connected without any problems so I finished setting up the system.

The next day I took the system to my customers and it found his wireless network SSID so I clicked to connect and it asked me for the password which I entered - it then tried to connect for a couple of minutes and came back with the password box - even after several more attempts I could not connect.

I decided to do a bit of troubleshooting - so I disabled the security on his router and it connected. I then went to WEP 64-Bit and that also connected so I went to WEP 128-Bit and that too connected. However when I changed it to any WPA or WPA2 mode it fails to connect. I checked and MAC filtering is disabled and it is mixed mode (B & G).

I said I would try again another day and went home - I checked on my home router and that is set to use WPA with a key renewal of 3600 - the same as my customers which is weird.

My setup at home is:

Linksys Wireless-G ADSL Gateway WAG200G
Firmware Version: 1.01.09 
Wireless Network Mode: Mixed	
Wireless Network Name (SSID): xxxxxx
Wireless Channel: 11	
Wireless SSID Broadcast: Enabled
Security Mode: WPA-Personal	
Encryption: 	TKIP
Passphrase: 	xxxxxx
Group Key Renewal: 3600	seconds
MAC Filtering: Disabled

My customers setup is:

Linksys Wireless-G ADSL Gateway WAG54G2
Firmware Version: 1.00.19 
Wireless Network Mode: Mixed	
Wireless Network Name (SSID): xxxxxx
Wireless Channel: 6	
Wireless SSID Broadcast: Enabled
Security Mode: WPA-Personal	
Encryption: 	TKIP or AES
Passphrase: 	xxxxxx
Group Key Renewal: 3600	seconds
MAC Filtering: Disabled

I've also attached a copy of dmesg, modprobe and iwconfig logs to this post in a zip file as the max attachment size is 19.5Kb.

Can anyone help me to connect this to my customers router as I really don't want to have to use WEP because of it's lack of security.

Many Thanks

	
Browndog

---

### Post by grahammechanical on 2010-09-27
Are you sure that you put in the right password? With WPA it is called WPA-PSK or Wireless Key. It is 10 characters long. There should be a label on the bottom of the router. I am reading this information off of the tract provided with my router on how to set up the router. I ask this obvious question because it seems to me (he of little knowledge) that the Operating System is doing its job correctly. And also, I once messed up my wireless connection by using the logon password instead of the Wireless key. In other words I am speaking from experience.

regards

regards

---

### Post by browndog289 on 2010-09-27
Hi

Thanks for your reply.

I am entering the same passphrase as that listed in the router under Wireless -> Wireless Security -> Passphrase.

I have checked the passphrase several times to make sure it is the same as the one in the router. I have even connected the ubuntu system to the router with a lan cable and copied and pasted the passphrase but with no success.

I've set up his other laptops and a couple of iphones to connect to it without any problems in the past. Even my kubuntu netbook connects to it.

Regards

Browndog

---

### Post by bkratz on 2010-09-27
> **browndog289 said:**
> Hi

Thanks for your reply.

I am entering the same passphrase as that listed in the router under Wireless -> Wireless Security -> Passphrase.

I have checked the passphrase several times to make sure it is the same as the one in the router. I have even connected the ubuntu system to the router with a lan cable and copied and pasted the passphrase but with no success.

I've set up his other laptops and a couple of iphones to connect to it without any problems in the past. Even my kubuntu netbook connects to it.

Regards

Browndog



A lot of wireless devices in Ubuntu (including mine) don't like to see mixed mode ( a router or A/P setting ) but like either WPA with tkip or WPA2 with AES, but not the both setting. Perhaps this is why it seems to work in some situations (but not others). Hopefully this helps.

---

### Post by browndog289 on 2010-09-27
Hi,

Thanks for your reply. I logged in to the router and tried it as WPA-Personal with the same passphrase but it doesn't give me an option to choose TKIP or AES individually under encryption it has a drop down menu but the only option with any WPA / WPA2 setting is "TKIP or AES".

I have tried all the encryption types from WPA to WPA2 but none will let me connect with this system - it just keeps returning the password. Disabled Encryption and any form of WEP work without any issues.

---

### Post by browndog289 on 2010-09-28
My customers router is set to Manual mode for WPA not Wifi Protected Setup - which I believe requires a PIN code. This means that it should just connect with the passphrase. However it is still failing to connect. 

Does anyone have any suggestions?

---

### Post by sgosnell on 2010-09-28
I notice that your customer has older firmware, but I'm not sure that's an issue, although it could be.  I don't have a lot of experience with Linksys.  You might try a forum search for WPA connection problems, I think there are a number of threads addressing it.

---

