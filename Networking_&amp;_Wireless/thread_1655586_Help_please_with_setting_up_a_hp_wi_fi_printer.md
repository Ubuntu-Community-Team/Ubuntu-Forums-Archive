---
title: "Help please with setting up a hp wi fi printer"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by colinmccubbin on 2010-12-29
This isn't a Ubuntu question as such, but since I'm running Ubuntu I'm seeking advice here first ;-)


I have just purchased a hp C410 multifunction printer which has wi-fi  connectivity.

I first tried the automatic wifi setup and if found my wireless access point, on the printer's display I confirmed it was the right access point and put in the access code, it then went and happily got an ip.. 

I then ran hp's find utility which said it couldn't find any printer.

When I looked at the printer's 'wireless network test report'. It had picked up an ip of 169.254.42.209 which is not in the range that my router serves, which is in the expected  192.168.2.100 up range.. Yet the same report states that it has the right SSID (network name) and access code. Other boxes on my home network are being assigned ips in the expected range, so where is this one coming from?

Does anyone have any experience with hp's wi-fi printers? Can I manually tell it not to use 'AutoIP' to request a dynamic ip,  and instead 'give it' a static ip through it's keypad? 

I currently have the printer and scanner working as a local USB device, on ubuntu 9.04, installing the HP Linux imaging and printing software took some trial and error, but appears to work, I'm printing and scanning with it just fine.

Thanks for any advice.

---

### Post by colinmccubbin on 2010-12-29
I just 'googled' the "169.254.42.209" address and a whois tells me that:

[I]IP Information - 169.254.42.209
Whois* Information

NetRange: 169.254.0.0 - 169.254.255.255
CIDR: 169.254.0.0/16
OriginAS:
NetName: LINKLOCAL-RFC3927-IANA-RESERVED
NetHandle: NET-169-254-0-0-1
Parent: NET-169-0-0-0-0
NetType: IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment: This is the "link local" block. It was set
Comment: aside for this special use in the Standards
Comment: Track document, RFC 3927 and was further
Comment: documented in the Best Current Practice
Comment: RFC 5735, which can be found at:
Comment: [http://www.rfc-editor.org/rfc/rfc3927.txt](http://www.rfc-editor.org/rfc/rfc3927.txt)
Comment: [http://www.rfc-editor.org/rfc/rfc5735.txt](http://www.rfc-editor.org/rfc/rfc5735.txt)
Comment: It is allocated for communication between hosts
Comment: on a single link. Hosts obtain these addresses
Comment: by auto-configuration, such as when a DHCP
Comment: server cannot be found.
Comment: A router MUST NOT forward a packet with an IPv4
Comment: Link-Local source or destination address,
Comment: irrespective of the router's default route configuration
Comment: or routes obtained from dynamic routing protocols.
Comment: A router which receives a packet with an IPv4
Comment: Link-Local source or destination address MUST NOT
Comment: forward the packet. This prevents forwarding of
Comment: packets back onto the network segment from which
Comment: they originated, or to any other segment.
RegDate: 1998-01-27
Updated: 2010-03-15
Ref: [http://whois.arin.net/rest/net/NET-169-254-0-0-1](http://whois.arin.net/rest/net/NET-169-254-0-0-1)

OrgName: Internet Assigned Numbers Authority
OrgId: IANA
Address: 4676 Admiralty Way, Suite 330
City: Marina del Rey
StateProv: CA
PostalCode: 90292-6695
Country: US
RegDate:
Updated: 2004-02-24
Ref: [http://whois.arin.net/rest/org/IANA](http://whois.arin.net/rest/org/IANA)

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName: Internet Corporation for Assigned Names and Number
OrgAbusePhone: +1-310-301-5820
OrgAbuseEmail: [email]abuse@iana.org[/email]
OrgAbuseRef: [http://whois.arin.net/rest/poc/IANA-IP-ARIN](http://whois.arin.net/rest/poc/IANA-IP-ARIN)

OrgTechHandle: IANA-IP-ARIN
OrgTechName: Internet Corporation for Assigned Names and Number
OrgTechPhone: +1-310-301-5820
OrgTechEmail: [email]abuse@iana.org[/email]
OrgTechRef: [http://whois.arin.net/rest/poc/IANA-IP-ARIN](http://whois.arin.net/rest/poc/IANA-IP-ARIN)

[/I]

Am I right in assuming from the above that this ip was probably used at hp for testing or wirelessly accessing the printer at the factory, and for some reason is not being updated now?

I'm going to see how to reset the printer to it's factory default and try again.

---

### Post by PatchesTheCaveman on 2010-12-29
No, devices automatically select a random address from the 169.254.0.0/16 range when they can't get an IP address via DHCP (e.g. automatically from your router).  I have no idea why it can't get an IP address from your router when all your other devices can.

Have you tried resetting your router?  Unplug it and plug it back in and then attempt to connect your printer to the wireless network again.

---

### Post by Boondoklife on 2010-12-29
I have an HP C4795 that is a wifi printer, to get it working I had to install hplip tookbox. Once you have this installed then you can plug it in via usb to setup the wifi portion of the printer. Once you have that setup and you confirm the printer is connecting to the network you can ditch the usb cable and just map it using hplip as your default printer.

I would also delete the usb printer so it does not get picked by accident.

Note this may not be proper for your situation, but I figured I would mention it just in case it was.

---

### Post by colinmccubbin on 2010-12-29
Thanks for the information!

The hplip site [http://hplipopensource.com](http://hplipopensource.com) has said for several days:

[I]Site off-line

HPLIP Website is currently under maintenance. We will be back shortly.

For downloading HPLIP Packages please visit [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/)

Thank you for the patience[/I]

Strange English there(!), I went to the sourceforge site yesterday and downloaded/installed the hplip files, which got me printing and scanning OK,  so I'll restart my router/network, reset the printer to defaults, and try again.

---

### Post by Boondoklife on 2010-12-29
it should be in the package manager, that is where i install it from. try there

---

### Post by colinmccubbin on 2010-12-29
Yes! After rebooting the printer now has ip 192.168.2.104 and the 'Configuration Source' that the test report shows is now DCHP rather than AutoIP, so it looks like the printer is now talking to my router and is on my home network.

It's too late now to do more tonight, I'll try to swap from USB to wi-fi again in the morning. I actually will just plug it into a network cable and not use the wi-fi, so will see if plugging it in gets a local ip as well.

Thank you again,:p

---

