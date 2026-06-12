---
title: "Help connect to Windows VPN from 9.10"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by giesen2 on 2009-12-10
Everything on my Ubuntu 9.10 laptop is working perfectly including regular Internet. However, when I try to connect to the VPN at my job, I get an error.

On my Windows Vista laptop, this works very easily, just connect to network, VPN, enter connection info and it works all the time.

In Synaptic I've enabled all the pptp options. I have a VPN entry configured in the new GUI. However, when I try to connect, I see a very generic error message flash on the screen (one of those fade-in notification displays), "VPN connection failed".

I've also searched on this and followed at least a dozen guides on how to set up a Microsoft VPN on Ubuntu and none of them have worked.

Is there any way I can at least get a more detailed error message?

---

### Post by kirisajenkins on 2009-12-28
I am having the exact same issue.  Any ideas?

---

### Post by roy2000 on 2009-12-28
Hi, I also had problems getting VPN to work. Apparently you can't just use the "Network Connections" GUI for the setup and make the entries as you would in Windows. I used these instructions to get VPN working (connected).
                                 [COLOR=#000080]_[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn/](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn/)_[/COLOR]


 I am still working on getting Ubuntu to recognize the shares on the company network. The only one that works at the moment is the Proxy Server, to allow Firefox to connect to the Internet via the VPN.

Hope this helps a little.

Regds.,  Roy

---

### Post by kirisajenkins on 2009-12-30
I still could not get things to work.  I ended up finding out that it was simply the Firestarter (firewall) that was causing all the grief.  Even with the setting added to the "user-pre" file it would not allow traffic.  Further, when I turned off the firewall and made the VPN connection, the firewall turned back on and then killed the connection.  I ended up having to just uninstall Firestarter.  Working like a charm now :)

---

### Post by digger61 on 2010-01-02
Hi,
I am having similar problems with a PPTP VPN from 9.10.

I get one of 3 responses:

1. an entry in syslog saying there were no VPN secrets but no messages on screen
2. an on-screen message saying that the VPN connection 'Page Associates' failed VPN service didn't start
3. an on-screen message saying that the VPN connection 'Null' failed VPN service didn't start

I really can't see what I'm doing wrong - any thoughts appreciated.

Jon

---

