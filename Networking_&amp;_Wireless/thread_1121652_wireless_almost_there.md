---
title: "wireless almost there"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by dgs2001 on 2009-04-10
Hi 

I have successfuly got my I2220 Inprocom card to link to the internet wirelessly YipEE.:KS

However whenever I restart I get a new instance of my wireless network SSID appearing in the Network Connection manager and I have to enter the passphrase again Boo.!:(
I usually have to restart Networking as well

How can I set this up to automatically see that its the same network and the same passphrase.

Please Help.

Duncan

---

### Post by coffeecat on 2009-04-10
You are giving it time to autoconnect, aren't you? You're not clicking on the n-m applet icon and clicking on your network each time, are you?

I've never seen this sort of behaviour. If it doesn't autoconnect when you leave it alone, I would suggest deleting all wireless network configurations in network manager, and starting with a clean sheet. Do this by right-clicking on the n-m applet icon, and selecting 'edit connections'. Click on the Wireless tab and delete each and all entries. Now left-click on the n-m icon, select your wireless network, put in your passkey where prompted and let it connect. Now whenever you restart, just give the system a minute or so to autoconnect. It *should* remember the last network it connected to and try to reconnect to that one.

If this doesn't work, something more fundamental is wrong.

What did you have to do to get your card working? Did you have to install any extra software?

---

### Post by dgs2001 on 2009-04-14
Thanks for the reply

Yes I'm giving it time, the only other thing I notice is that if I click the Show Passphrase box in n-m I get a huge long gobbledy Gook passphrase, this is not what I put in.

I'm not sure how I ever did it, as now I can't get it to connect wirelessly at all. Even deleting all the instances and trying again doesn't work

I have ndiswrapper installed and the wireless network is showing but will not connect.

I have checked the settings on the router and they are set to allow connection. 

Duncan

---

### Post by coffeecat on 2009-04-14
> **dgs2001 said:**
> the only other thing I notice is that if I click the Show Passphrase box in n-m I get a huge long gobbledy Gook passphrase,

That's quite normal. I believe that's because your passphrase is being stored in encrypted form, not as plain text, for security reasons. Similarly, for security, the stored passphrase won't be shown as is on screen.

Sorry I can't help you with the rest.

---

