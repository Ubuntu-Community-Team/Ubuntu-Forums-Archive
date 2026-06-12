---
title: "Connection to a Hidden Wireless WiFi with Ubuntu 10.04"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by bobcrunch on 2010-08-20
[SIZE=2]I needed a Linux capability installed on my Toshiba net-book with Windows 7 Starter so I could service Unix/Linux products in the field (ssh into the system, etc.).  For my needs, I decided that Ubuntu 10.04 installed with WUBI would be an ideal solution.  I have been very happy with my decision.

I was having no problem connecting to the Internet with a wired LAN or an open WiFi, but I was having all kinds of problems connecting to my hidden home wireless which I thought was as vanilla as it could get.  It was a Linksys using WPA-Personal with TKIP encoding.  Searching the Internet got me all kinds of gobbledygook about editing files in /dev/xxx, etc., and all sorts of irrelevant advice.  After much hacking, I finally prevailed, and the following is a simple explanation (I hope) using the existing Ubuntu tool.  This should cover most PC installations of recent Ubuntu releases.

Go to the top of the Ubuntu desktop, find the network icon (a pizza-slice of concentric circles) next to the speaker icon. (If you're connected to a wired LAN, the icon will be two opposite-pointing arrows)  Left click and a drop-down menu will appear.  Click on "Create New Wireless Network...".  A dialog box will open, and then click on the "Wireless Security" and choose "WPA & WPA Personal".  Then type in your Network Name and Password (Passphrase - must be at least 8 characters).  Click Create.  The box will close, and you'll get a "Connection Established" message, but if you're actually connected, you should go out and buy a lottery ticket.

You now need to go back up and right click the network icon and select "Edit Connections...".  This will open another dialog box.  Click on the "Wireless" tab, and select your network name and click "Edit".  This opens another Dialog box at the "Wireless" tab.  For Mode, select "Infrastructure", not the default "Ad Hoc". Note that this was my biggest hurdle in getting things working. "Ad Hoc" sounds like such a nice choice, but wrong.  Next, confirm that the in SSID is correct.  Leave BSSID and MAC Address blank unless you've set up a Broadcast SSID or have a strange PC setup.  Click on the "Wireless Security" tab, and for Security select "WPA & WPA2 Personal", and enter your Password (Passphrase).  If this is your only hidden wireless, select "Connect automatically".  Next, click on the "IPv4 Settings" tab and select "Automatic (DHCP)". Click "Apply".

Now go back and right click the network icon and select "Edit Connections".  You can now delete all your failed attempts.  If you checked "Connect automatically", it should establish a connection.  If not, left click the network icon and connect manually (using "Connect to Hidden Wireless Network" or some other selection).[/SIZE]

---

### Post by grahammechanical on 2010-08-20
Can I add just one little thing to your comments? 

The pass-phrase to use when creating a wireless connection is the wireless or network security key for your router/modem. It is found on a label attached to the router. It is indeed 8 characters long and is case sensitive. I am using information from an instruction leaflet that came with my router. I mention this because network manager remembers the password, which is good, but does not inform you if you have entered the wrong one. It simply asks for authentication. This is not good. As this does not happen immediately you may not realise that the reason for connection failure is due to the wrong password. I found this out myself .

regards.

---

### Post by jarviser on 2010-08-20
Far easier to leave the network SSID showing. Any decent sniffers will find it anyway. Makes it difficult to attach things like streamers, wifi printers etc if it's hidden.

I reckon it's just as safe to rely on WPA encryption, make sure all passphrases and passwords are changed from factory settings, use all 63 characters of passphrase not just 8,  and rename the SSID to another manufacturers' model number rather than hiding it. As the allies discovered in WW2, better to give the enemy false but credible intelligence than try to hide the truth.

And before doing anything, delete all existing wifi networks in Edit Connections.

But if you want it hidden, good write-up!

---

### Post by bobcrunch on 2010-08-20
> **grahammechanical said:**
> Can I add just one little thing to your comments? 
 
The pass-phrase to use when creating a wireless connection is the wireless or network security key for your router/modem. It is found on a label attached to the router. It is indeed 8 characters long and is case sensitive. I am using information from an instruction leaflet that came with my router. I mention this because network manager remembers the password, which is good, but does not inform you if you have entered the wrong one. It simply asks for authentication. This is not good. As this does not happen immediately you may not realise that the reason for connection failure is due to the wrong password. I found this out myself .
 
regards.
 
The Linksys WiFi allows the user to choose the Passphrase and SSID.  It's for home use.  Otherwise, you have to look on the router, or ask the sysadmin.

---

### Post by jarviser on 2010-08-21
I think that applies to all wifi routers, in fact I would say it's essential to change passphrase and admin password from the default (label) ones to  new ones. There have been cases such as with the British BT HomeHubs where manufacturers use an algorithm to generate passwords from the serial number, MAC etc. That info is usually retrievable from data traffic and can be used to decipher the passwords much quicker. Use all 63 characters in WPA and it's pretty much unbreakable (in 2010) unless you are GCHQ.

---

### Post by Bob99 on 2010-09-07
Thank you for your clear, precise and accurate fix to my wireless problem. I have found that many LINUX users tend to be overly verbose and seem to assume that all LINUX users are 100% up on all aspects of the system. I have been stumbling along for a couple of weeks searching the forum for answers to no avail. It was so refreshing to finally get a knowledgeable clear precise answer.

Keep up the good work.

---

