---
title: "Check Point VPN-1 SecureClient"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by mcarni on 2009-08-30
When my company decided to send me to Germany to work, they gave me a laptop with XP, a PIN and a RSA Secur ID fob.
They installed " Check Point VPN-1 SecureClient" as a VPN client on the xp computer, and they instructed me to enter my PIN and the 6 digits number from the fob whenever I wanted to access the server in UK.

My mission recently has been to try to customise my home crunchbang linux install so that I could install it on a USB stick and boot from the USB stick when at work.
A part form a little cock up which I posted somewhere else on the crunchbanglinux forums, ( I overwrote windows MBR...:D ) everything is going smoothly and I now have a bootable usb stick with #!.

Next on my list is how to get the VPN to work.
I read several posts on different forums, there are several   conflicting suggestions.
I seem to understand that "vpnc" can be a linux replacement for "Check Point VPN-1 SecureClient".
I exported the "check point" profile and I opened it as a text, but I am struggling to find similarities with the vpnc config file.
Is there any of you that has already done something similar and could give me a hand in finding the correct matches between "check point" and vpnc config items?

This is what I got form the copy of the "check point" profile.

User name:     <my username on this laptop>
PIN:        <a pin I was given tgether with the fob>
Tokencode:    <6 digit number randomly displayed by the fob>

Location Profile     <my company's server IP address>
Destination         <my company's server name>

Advanced
office mode (selected)
Connectivity enhancements (selected)
    Use NAT traversal tunneling (selected)
        IKE over TCP (selected)
        Force UDP encapsulation (selected)
    visitor mode (unselected)
Hub mode configuration (route all traffic through gateway (unselected)


Something I found when I exported in Windows the configuratio.srp file

(<my company's server IP address>
    :attributes (
        :read_only (false)
        :description ("<my company's server IP address> default profile")
    )
    :options (
        :support_tcp_ike (true)
        :force_udp_encapsulation (true)
        :support_tcpt (false)
        :support_ip_assignment (true)
        :sr_route_through_gw (false)
        :ps_ha_scheme (ps_pool)
    )
    :gateways ()
    :policy_servers ()
    :site (<my company's server IP address>)
)

Thanks in advance, and sorry if I used the wrong terminology, I am not an IT guy&#8230;

M

---

### Post by peterbechlutzka on 2009-10-02
Dear Mcarni
Did you manage to find a solution?
I am very interested!
/Peter

---

