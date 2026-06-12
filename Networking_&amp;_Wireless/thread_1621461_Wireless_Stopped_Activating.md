---
title: "Wireless Stopped Activating"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by rickcjmac on 2010-11-14
I am using an HP Pavilion dv2000. 

I installed Ubuntu 10.10 on a partitioned drive about a month ago. The other partition is running Windows Vista. I have used the wireless (WLAN) switch without problems until about a week ago. 

I started a few torrents using the default bit torrent client. Everything was fine until I shut down the computer and started it up again the next day. The torrents were in the middle of their downloads when I shut off the computer. 

Now flipping the switch does nothing. Ubuntu can't see any wireless networks. 

In Windows I get a normal pop up message when I disable the switch but not when I enable it. Was working in Windows previously too. 

I am at a loss. Any help is GREATLY appreciated as I use this computer for school and Internet is a must.

---

### Post by rickcjmac on 2010-11-14
Ok I figured it out. 

I booted up the Windows Vista partition and this is what I did.

Go to HP Wireless Assistant
Click on PROPERTIES in the lower left part of the screen
Inside the properties tab select all of the options
     There should be four options
          1) HP Wireless Assistant icon in notification area 
          2) Status change messages 
          3) Initial status messages 
          4) Independent controls for installed wireless devices 
I selected all of the options then clicked APPLY in the lower left part of the screen.

At this point a button appears in the HP Wireless Assistant window under ACTION (next to status) that says "TURN ON"

I clicked TURN ON and it started my wireless again.

Hope that helps someone :)

---

