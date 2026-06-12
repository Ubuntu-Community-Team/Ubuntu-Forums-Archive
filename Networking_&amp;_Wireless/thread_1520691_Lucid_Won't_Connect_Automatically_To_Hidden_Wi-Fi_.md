---
title: "Lucid Won't Connect Automatically To Hidden Wi-Fi APs"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Windows Refugee on 2010-06-29
I've seen other users post this same issue, but can't find anyone who has been able to solve this problem...

I have SSID broadcasts turned off on my wireless router (always a good choice for increased security).  Even though I have put a check mark on "Connect Automatically" in my wireless network's configuration under SYSTEM > PREFERENCES > NETWORK CONNECTIONS, it will not connect automatically. I have to click on the network manager icon in the notification area of my desktop, and select "CONNECT TO HIDDEN WIRELESS NETWORK" in order to get online.  Network manager does indeed connect automatically to APs that broadcast their SSID.

Any suggestions ?  (I don't want to enable SSID broadcasts on my router.)

---

### Post by kerry_s on 2010-06-29
did you check the box "available to all users"?

---

### Post by Windows Refugee on 2010-06-30
> **kerry_s said:**
> did you check the box "available to all users"?

Hi, Kerry...

Yes, both "Available To All Users" and "Connect Automatically" are checked, but still no joy !  ](*,)

---

### Post by kerry_s on 2010-06-30
have you tried deleting it & setting it up again.

mines connected to a hidden ssid on 3 different ubuntu machines so i know it should work, i have no problems with auto connecting at startup, it's usually connected before the desktop is even finished loading.

can you tell us more on the type of wireless card you have?

---

### Post by sgosnell on 2010-06-30
I think it has to be a settings glitch somewhere.  My laptops connect to my network all the time, every time, without the router broadcasting the SSID, and I can also connect to other hidden networks automatically.  I've never had a problem, with any Ubuntu version back to 8.04.

---

### Post by Windows Refugee on 2010-06-30
> **kerry_s said:**
> have you tried deleting it & setting it up again.

mines connected to a hidden ssid on 3 different ubuntu machines so i know it should work, i have no problems with auto connecting at startup, it's usually connected before the desktop is even finished loading.

can you tell us more on the type of wireless card you have?


I'm currently using a Motorola branded "WN825G" PCMCIA Wi-Fi card, which has a Broadcom BCM4306 (rev 3) controller.  I used b43-fwcutter to install the driver.  I do have other USB Wi-Fi adapters, but the Motorola PC card is the only one I've gotten working on Ubuntu so far.

---

### Post by Windows Refugee on 2010-06-30
> **sgosnell said:**
> I think it has to be a settings glitch somewhere...  

OK, but what other settings should I be looking at besides "Connect automatically" and "Available to all users" in Network Manager (which are both checked) ?

...and to answer Kerry's other question, yes, I've deleted and re-created the network connection for my hidden access point at least a dozen times already.  I think it's worth repeating that APs that broadcast their SSID do connect automatically to my laptop !

---

### Post by sgosnell on 2010-07-01
I have no idea.  I've never had a problem connecting to hidden networks.

---

### Post by b k on 2010-07-01
> **sgosnell said:**
> I have no idea. I've never had a problem connecting to hidden networks.
 
Hi there, if you are using TKIP encryption for your router/gateway/AP, try changing that to AES.
 
Just a thought, not sure if it would help.

---

### Post by Windows Refugee on 2010-07-02
> **b k said:**
> Hi there, if you are using TKIP encryption for your router/gateway/AP, try changing that to AES.
 
Just a thought, not sure if it would help.


Thanks for the suggestion,  but I am using WPA2 / AES encryption !

---

### Post by sgosnell on 2010-07-02
Have you read [this troubleshooting guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)?  It might give you some ideas.  I would also suggest enabling SSID broadcast long enough to get an initial connection, then disabling it and seeing if you can connect.  That sometimes seems to help.

---

### Post by b k on 2010-07-05
> **Windows Refugee said:**
> Thanks for the suggestion, but I am using WPA2 / AES encryption !
 
Hi there have a look at post #18 of this link [http://ubuntuforums.org/showthread.php?t=1471456&page=2](http://ubuntuforums.org/showthread.php?t=1471456&page=2)
 
Try deleting the network connection first, temporarily configuring for [COLOR=red]manual[/COLOR] log in to user account upon boot up, then recreating the network connection again.
 
And if it still does not work, consider the Keyring password angle.
 
Hope the info can help you.
 
Good luck

---

### Post by kid1000002000 on 2010-07-10
I found this:

Automatically connecting to a network with a  hidden SSID is a bad idea.
  Since your computer cannot passively listen for the SSID broadcast  and automatically connect when it sees the SSID (which will not show in  the beacon broadcast, since that is how hiding the SSID works), it has  to *actively* send probe packets with the network's SSID, *even  if it is nowhere near the access point*, and wait for a response.  This means that, instead of the access point broadcasting its name all  the time, you have *all computers configured to automatically connect  to it* broadcasting its name all the time, *no matter where they  are*.
  Not to mention that, to be able to roam between several access points  with the same SSID, the computer has to know their BSSID (essentially,  the AP's MAC address). Usually they do this by listening to the beacons  broadcast by the access points. Since the beacons do not have the SSID  (hey, it's hidden!), the computer has to periodically send probe  requests *even if it is already connected to the access point*.  Making it laughably easy for an intruder to find out the SSID if even  one computer is connected to the network. Not to mention the  desassociation attacks.
  So, it gains almost zero security (it is still way too easy to find  the SSID) and loses a bit more security (the client computers constantly  announcing to the world "hey, I am a computer belonging to someone who  works at company XYZ!" even when nowhere near company XYZ). The net  result is negative.
  The only way to reduce or even avoid the security loss is to have it  connect manually instead of automatically. Which seems to be what Apple  is doing. (Windows Vista, from what I recall, warns you of the security  issues when you try to set it to automatically connect. The  NetworkManager used by most Linux distributions also seems to make you  chose the saved connection from a dropdown manually.)
  In theory, it would be possible to save the known BSSIDs for each  ESSID and only send the probe request when a beacon for one of them is  received (that is, when you are near an access point which has in the  past been used for that SSID). I do not know why nobody seems to have  tried that yet.


[http://superuser.com/questions/43836/automatically-connecting-to-hidden-ssid-wifi-network](http://superuser.com/questions/43836/automatically-connecting-to-hidden-ssid-wifi-network)

---

### Post by sihtworth on 2010-07-17
I have exactly the same problem with Lucid. The reply:

> **kid1000002000 said:**
> I found this:

Automatically connecting to a network with a  hidden SSID is a bad idea.....



makes perfect sense for someone with a laptop but I've got the problem with my desktop, so I don't really need to worry about broadcasting my SSID all over the place as my wireless router is in the next room. Has anyone else got any further suggestions on how to resolve this? I'm wondering whether I can write a script to connect, and run that automatically at logon.

---

### Post by jotape99 on 2010-08-03
Try to fill the BSSID of your configuration with @mac of your wireless router.
[[img]http://nsa17.casimages.com/img/2010/08/03/mini_100803082342735747.png[/img]](http://www.casimages.com/img.php?i=100803082342735747.png)

To get it, in a terminal ping the ip of the router, then use arp -a

---

### Post by sihtworth on 2010-08-08
> **jotape99 said:**
> Try to fill the BSSID of your configuration with @mac of your wireless router.

To get it, in a terminal ping the ip of the router, then use arp -a

Good thinking but it still doesn't seem to want to log in automatically.

---

