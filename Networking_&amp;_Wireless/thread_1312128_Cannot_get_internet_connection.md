---
title: "Cannot get internet connection"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by davewo on 2009-11-02
I can log into the system.  When I click on the Foxfire Icon, we cannot get connection.  It shows as working "offline".  After unchecking that and retrying, it goes back into same state...."offline".
 
I am wondering if it has to do with some computer settings or some "keyring" settings.
 
Any suggestions would be appreciated.

---

### Post by rossmoore on 2009-11-02
OK. You're in Ubuntu, with a "task bar" across the top?
[EDIT: I see you're using Edubuntu. But that's fine, very similar setup I think]
What type of internet connection do you have? Wifi to a router? ADSL modem plugged in to you computer? Cable modem?

---

### Post by davewo on 2009-11-02
Wifi to Router to dsl.

---

### Post by rossmoore on 2009-11-03
OK, so your router has a connection fine, I presume. You're missing your wifi connection to the router.

There should be an applet top right - is that connected (with a kind of power meter of vertical bars)? If it is not connected you'll have two little screens I think. And if you right click on it you should get a couple of tickboxes - "Enable Networking" and "Enable Wireless". Are they both present and enabled?

If you're disconnected, but the two tickboxes are there, then you have a working wireless card that simply isn't connected to the router. We should be able to fix that. If the "Enable Wireless" tickbox isn't present then we need to get your wireless card working.

If you're connected, but Firefox still has problems, then something else (not quite sure what) isn't working. Again, we can trouble-shoot that too I'm sure.

---

### Post by davewo on 2009-11-03
Thanks for the help!!
 
I always get the two "tv screens" at the top right corner.  The "broadcast" button on the computer itself shows "waves" going out, apparently indicating it has made an electronic connection.
 
When I right or left click on the two tv screens, I get "Connection Properties"; this has two tabs:  General and Support tabs.
 
General tab:
 
Name - lo
Status: Idle
 
Support tab:
 
Internet Protocal (Ip04)
 
   Address: gives address location 
   Subnet Mask: gives subnet mask numbers
   Network Device:  Local Loopback
     Address:  00: 00: 00: 00: 00: 00:
 
Help (button)                                 Close (button)
 
btw; this computer/wireless card does work fine in two other locations; so I believe the wireless card is working fine.  I can make connection to the internet with Firefox at these other two locations.
 
I have never seen a "power meter" (with two little vertical bars) at either the working or non-working location.

---

### Post by rossmoore on 2009-11-03
Hmmm. Perhaps edubuntu is more different than I thought. This certainly seems to indicate you're not connected to anything - the local loopback (that's what lo is) isn't very useful for anything.

You should be able to get a list of wifi connections available from that network icon. Sorry, but are you sure you haven't switched the wireless switch on your laptop off by mistake?!

If you install wifi-radar
sudo apt-get install wifi-radar
[or use Synaptic to install it] can you then run that (it goes under Internet in the menu) and see a list of wifi networks available?

---

### Post by davewo on 2009-11-08
I found the switch for the wireless card on the keyboard and the wireless card is operating.  I also found a list of networks.
 
I think I've narrowed the problem to a probably "encrypted" router that is associated with the dsl connection. I couldn't get online with another router.
 
If I can determine the password of the encrypted router, I can probably figure out how to get onto their system.
 
Problem now...I don't know where to start with Linux to set up a new wireless connection in the network.
 
Any suggestions?
 
Thanks

---

### Post by peepingtom on 2009-11-08
Get permission to use the router.
Receive the password.
Left-click the network icon.
Select a network connection.
Enter the password.

---

### Post by rossmoore on 2009-11-09
Well said peepingtom. I'm beginning to understand the problem the OP is having. Just follow peepingtom's instructions.

---

