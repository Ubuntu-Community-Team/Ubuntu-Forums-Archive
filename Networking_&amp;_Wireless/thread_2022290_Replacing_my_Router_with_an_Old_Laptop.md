---
title: "Replacing my Router with an Old Laptop"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by zshuford on 2012-07-10
Lately, my home wireless router has been going in and out. It's not dropping connection, just dropping it's connection to the Internet (the DSL modem is fine). After fiddling with it for a couple weeks, I've decided it's time to replace it.

And I figured, I already have an old Thinkpad R61 that's currently serving as a LAMP server for a little vanity website I have (it gets maybe a dozen hits a day) so why don't I put it to a better use?  I'm going to get my hands on a spare PCMIA Ethernet card tomorrow and attempt to set it up as a router all on it's own. So here's my game plan so far:

(1) Set up the server as a router following these instructions:
[http://imranasghar.blogspot.com/2009/09/how-to-make-ubuntudebian-as-router.html]("http://imranasghar.blogspot.com/2009/09/how-to-make-ubuntudebian-as-router.html")

(2) Set up the server with ADSLPPPoE following [these instructions]("https://help.ubuntu.com/community/ADSLPPPoE").

I should then have Internet access through a computer plugged into eth2, right?

Then, move on to....

(3) Install linux-igd for upnp functionality (gotta get that "Open NAT" message on my Xboxes!) :)

Now this is where I get fuzzy....

(4) I would *like* to use wlan0 as an access point. I'm not sure if the built-in wireless supports "master mode," though. Assuming it does, I plan to [follow the steps here]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint"). But is there a way to check beforehand? I have no idea if mine can do the "master mode" thing. If not, I plan to continue to use my router, but use it only as an AP, and not handle the routing. If it can't do Master Mode, what do I need to configure to make the old wireless router function just as an access point?

(5) Lastly, I need some way to handle access restrictions. My google-fu is weak on this one, though. How do I ban certain MAC addresses at certain times of the day (ie, my son, who failed most of his classes in his first semester at college, doesn't get the Internet between 22:00 and 6:00 any more. I need to preserve that functionality).

---

### Post by Kirk Schnable on 2012-07-10
This is a fantastic topic.  While I question the sanity behind using a laptop as an always-on network appliance, I do a similar setup but with a Mini ITX board computer I built specifically to be my router. 

It looks like you're spot-on with your tutorials.  My connection to the Internet is not DSL so I do not need to mess with PPPOE stuff, but I do have an excellent iptables script which I've written up.  It allows for port forwarding, IP whitelisting, and everything not whitelisted is dropped.  I'd be happy to pastebin it for you if it would save you some time.  Depending on your DSL modem, it may just be a normal ethernet connection coming out, you might not need to do any PPPOE authentication.  However, I'm going to assume you know how your stuff is setup and I'll let you handle that.

My personal router doesn't support UPNP.  Personally I believe UPNP is incredibly dangerous because it allows any software on your network to forward ports at will.  This seems like very bad practice to me, but to each his own.

As far as making wlan0 an access point, I know it can be done, but I just elected to buy a Ubiquiti AirRouter and run it in Ethernet Bridge \ WiFi AP mode.  A Linksys router with DD-WRT would do the trick too.  A lot of router firmwares support Switch+AP without NAT\Routing.

To find out if your card supports Master Mode, you should be able to do some Googling.  Find the model of your card, and post it here and Google.  That will be your best way to find out if it's supported or not.  A lot of cards I've seen are not supported.  You may be able to buy a replacement WiFi card for your laptop which supports master mode, but I also question the potential of using laptop antennas.  Remember, they are the receivers for transmissions by all WiFi clients, which could seriously hurt the range of your network.

I've never attempted the access restrictions you're looking for... HOWEVER what I would recommend is to get the MAC addresses of the hardwares.  Then setup DHCP reservations for these MACs and then you know what IP he's coming from.  Then it should be easy to use iptables to restrict that MAC.  Even if you have to run a cronjob to turn the access on and off at the times you want, that would achieve your goal.

Depending on the technical level of your son, he may be able to bypass the restrictions I outline above by setting a Static IP.  I am not sure if it's possible to do MAC Address based iptables stuff.  I don't think it is, but it's worth a look on Google.

I suppose you could remedy this security "hole" by only allowing traffic from whitelisted internal IPs.  That would be painful to maintain as you get new hardware though, so I'd avoid taking that approach if possible.

I'll give this some more thought, the access lists are intreaguing to me as they're not quite like anything I've ever tried to do with my router before.

Hopefully I've given you some food for thought, and you can ask some more detailed questions this round.  I will be subscribing to your thread so I can keep up to speed.

Kirk

---

