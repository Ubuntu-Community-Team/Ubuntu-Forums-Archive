---
title: "How to get PDA Net and Ubuntu 8.10 to work together"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by mmtarleton on 2008-12-05
Hello,

I have been searching for a single location where someone could go to get help setting up their PDA Net from their iPhone with the Ubuntu Intrepid 8.10.

I would like this to be a centralised location where all known solutions for this question are gathered.

My solution was to:

1. Right-click on the Network icon and uncheck, in this order, "Enable Wireless" then "Enable Networking"
-- then re-check "Enable Networking" then "Enable Wireless"

2. Right click on the Network icon and select "Edit Connections..."

3. Click "Add"
-- Enter in a "Connection name"
-- Enter in a "SSID"
-- Change the "Mode" to "Ad hoc"
-- Make sure the wireless security is set to none (I have not found a way to make this work with security enabled)
-- Go to the "IPv4" tab and set the "Method" to "Automatic (DHCP)"
-- Click "OK"

4. Navigate to your iPhone > Settings > Wi-Fi
-- Turn your Wi-Fi on, then proceed...

5. Left-click on the Network icon
-- Click on "Connect to Hidden Wireless Network..."
-- Under the "Connection," select your newly established connection
-- Click "Connect"

6. Now, look for your new network to show up on your iPhone Wi-Fi networks...
-- Once it appears, click on it and wait for the Network icon to display the message that it successfully connected (you should have full bars)

7. Open PDA Net and turn "Wi-Fi Routing" on and you now have successfully routed your iPhone's internet to your Ubuntu 8.10 OS.

note: I have not been able to get a connection using WEP, WPA, or WPA2
note: If there are other solutions that are faster to establish or easier to use, please do not hesitate to post.

Enjoy!!!

---

### Post by amendt on 2009-03-09
There is even a [video]("http://www.youtube.com/watch?v=BNQ6W_yUnII") to help us out.

---

