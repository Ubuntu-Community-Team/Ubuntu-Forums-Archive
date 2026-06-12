---
title: "VPN and mail issue"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by trundlenut on 2011-06-27
I have a rather strange problem caused by a VPN connection.  I have an Ubuntu server running Davmail in my office which allows me to access my work exchange server with Thunderbird.

When I am in the office everything works fine.  The problem arises when I connect to the office network via a VPN connection.  I find that I can send small emails (i.e. a simple message with a few lines of text) but larger emails won't send (i.e. an email with a 100kB PDF attachment).  Thunderbird starts to send the email but then it hangs at around 40% of sending and eventually times out.

While connected to the VPN I can access the Ubuntu server via SSH and webmin, the Windows SBS server via RDP (which acts as the VPN server) and shares on the same server.

The problem would seem to lie with the VPN connection but I don't know where to start looking for the issue.  Our external IT people are unlikely to be of much help as they seem to consider Linux as some kind of voodoo or devil worship.

I have only tried the VPN from one external location so I suppose the problem could lie with my router.

---

### Post by SeijiSensei on 2011-06-28
I'm guessing your office is using PPTP since the VPN server is running Windows?  You might need to play with some settings in your client configuration like the MTU.  

Another option is to add OpenVPN to your Ubuntu server and build your own separate VPN connection.  I have OpenVPN boxes running at customers' sites in client mode.  During boot they make a connection out through the office firewall to a machine I maintain and set up the tunnel.  I've never had problems moving files of arbitrary size over OpenVPN.

---

### Post by trundlenut on 2011-06-28
Thanks for that, it is indeed PPTP.  I would prefer not to setup a separate VPN connection as there is the potential to muck up the existing connections which would cause my boss to have one of his "high blood pressure" moments.  We have two ADSL lines which the router forwards the vpn connections on to the windows server.

Where would I find the option to change the MTU? I assume you mean on my laptop rather than the server.  In network manager I can't see anything like that.

---

### Post by SeijiSensei on 2011-06-28
You're going to have to browse around configuration files and do some Googling.  The MTU setting may be in the configuration for the pppd (note not pptpd) program that gets launched to handle the actual connection after pptpd is run.  

I haven't done any configuration of pptpd for a long time now, so I'm afraid I can't be a lot more help.

Your running an OpenVPN session between a box in your office and one in your home isn't really going to interfere with the pptpd sessions, but I can understand that it might be hard to convince the powers-that-be of that.

Here's some help from the [PPTP Client site]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#installing_pppd"):

> Connections via tunnel freeze
Are your connections from the PPTP Client or from another machine on your network?

Problem: TCP connections via the tunnel freeze once they attempt to transfer large amounts of data.

Diagnosis: path MTU discovery may be failing due to ICMP blocking by hosts after the PPTP server.

Solution: manually restrict the MTU on the interface, by adding mtu 1404 or some smaller value as an option to the pppd program, either in the peers file for the tunnel, in the options file, or on the command line. You can also restrict the MTU on the interface after the tunnel has connected, using a command like ifconfig ppp1 mtu 1400.

The effect is that new TCP connections from your host will use an maximum segment size (MSS) that is lower. This may prevent path MTU discovery from being necessary.

---

### Post by trundlenut on 2011-07-10
Right, this was a problem with the MTU.  Looking at my router I found the MTU was set to 1432, my VPN connection was set to 1400.  I reduced the MTU on the VPN to 1300 and now it works.

Just need to work out how to set this value as default now.

---

