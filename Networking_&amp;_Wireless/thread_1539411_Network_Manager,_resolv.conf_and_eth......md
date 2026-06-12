---
title: "Network Manager, resolv.conf and eth....."
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by fast_ian on 2010-07-26
Hi to all,

Newbie to Ubuntu (and *loving* it & the community!), but long time Unix hacker (when that term meant something positive ;-))

Anyway, for reasons that need not concern us here, I need to reset my DNS server addresses - No problem, I'll just go edit resolv.conf and restart - As you guys know, that doesn't work as the file gets rebuilt on every reboot....

So, I rtfm'd and "networkmanager" seems to be the applet to do this today. Trouble is, once I figured out that "Network Connections" is, in fact, "Network Manager" (!) it pops up as shown in the pic - Last used=never. If I stumble on regardless and edit one (or the other) of the ports, under ipv4 (and 6) it says use DHCP, but no client id is shown. [MAC addresses are known]

This is patently wrong as I'm currently beautifully connected thru eth1 - See pic.

What all this boils down to is:

- Why is it saying "never used"
- How/where do I tell Networkmanager to use different DNS servers? [I did search, honest!]

BTW, the machine does have 2 ports (it used to be a dual homed f/wall), but only the one on the m/board is currently connected. [Which I would have guessed would be eth0, but apparently not.....]

TIA, cheers,
Ian
PS - A little heads up - After registering I got the usual "we've sent you an email which you've gotta use to activate your account" msg - This never arrived (yes, I checked spam), but I am nevertheless able to post

---

### Post by endotherm on 2010-07-26
well, how do you get your addresses? dhcp? /etc/network/interfaces?
one easy way to knock network-manager out of the mix is to configure your interfaces and resolv.conf, and then to disable the autostart of network manager in System-Preferences-StartUp Applications. 

you can find info on configuing your interfaces file here:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

I wouldn't worry about the never connected message. the only connections I;ve seen update that value are wifi and vpn. it dosen't seem to track the lan interfaces. if you are getting your addr via dhcp, then just set the dns only (there is an option to use dhcp for the address only, leaving dns server config up to the client) ..

hth

---

### Post by Iowan on 2010-07-26
I'm not sure why, but I've had occasions where editing via Network Connections didn't work (save information), but editing via Network Manager worked fine - probably my screw-up, but just in case...

---

### Post by fast_ian on 2010-07-26
> **endotherm said:**
> well, how do you get your addresses? dhcp? /etc/network/interfaces?

DHCP

> one easy way to knock network-manager out of the mix is to configure your interfaces and resolv.conf, and then to disable the autostart of network manager in System-Preferences-StartUp Applications.Thanks for that - Parts of me yearn for the "good old manual days!"....[Leave my friggin resolver files alone, damnit! ;)]

> I wouldn't worry about the never connected message. the only connections I;ve seen update that value are wifi and vpn. it doesn't seem to track the lan interfaces.Thanks again - It was exactly that which "concerned" me - It says its active and connected, but no IP address, which suggested to me that more was broken - "My mind is now at ease!" Thanks!

> if you are getting your addr via dhcp, then just set the dns only (there is an option to use dhcp for the address only, leaving dns server config up to the client) ..That worked! - Thanks again [I'd actually previously set up eth0 that way when I believed that would be the M/board port, but completely forgot that eth1 is the truly active port - duh!.....]

Just to confirm - By default, Network Manager gets both the localhost DHCP address and DNS server names/addresses from the gateway?

[quote=Iowan]..... editing via Network Connections didn't work (save information), but editing via Network Manager worked fine[/quote]

Interesting - And more confusing! - I dunno what I'm opening anymore;

- Right click on the network icon in the Gnome panel (Looks like a short resistor (?)) and select "edit connections" - Opens the window shown in the pic. About says "Network Manager Applet 0.8".
- Go to system ->  preferences -> Network Connections - Opens the same applet.

I'm not sure of the difference between "Network Connections" and "Network Manager" - I'm selecting "Connections", but am seeing "Manager"? Or am I missing something entirely?

Thanks for the great help guys,
Cheers,
Ian

---

### Post by Iowan on 2010-07-26
Sorry I added more confusion...
If you mentioned it, I missed which version you're using.
When I think Network Manager, I think of the applet/icon in upper-right corner (on this Hardy machine, it's two monitors, on Karmic it was the resistor-looking thing, Lucid has an RJ-45 and cable/plug). The other method (System>Administration>Network on this Hardy box, or System>Preferences>Network Connections on my Lucid box) is what I consider "Network Connections".

Perhaps recent versions use the same applet - this Hardy machine calls "Network Connections" **Network Administration Tool**.

---

### Post by fast_ian on 2010-07-26
> **Iowan said:**
> Sorry I added more confusion...

Not hard to do when dealing with me! :)

> If you mentioned it, I missed which version you're using.My bad - 10.0.4 LTS "Lucid Lynx" [Great name btw!]

> ....Perhaps recent versions use the same applet....It seems so  - On my box it seems I have the Karmic resistor thing in the top right, but right-clicking that and then "about" says "Network Manager Applet 0.8". I'm pretty sure system -> prefs -> Network Connections opens the same application - It certainly looks the same.....

Thanks again,
Cheers,
Ian

---

