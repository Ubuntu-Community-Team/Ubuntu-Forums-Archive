---
title: "Network provider blocking Linux PC's from accessing web"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by Durham on 2011-02-21
Today I have tested the networks at several schools in the area,and at the town hall. It is not possible to surf on www on any of these networks using a PC running Linux. My conclusion is that there has to be some kind
of filtering of traffic that exclude PC's running Linux.

From the same PC I can send and receive email, I can ping and trace (mtr) addresses on www, and I can view webpages that are on servers on the inside of the filtering-gateway. The filter used is InterScan Web Security Virtual Appliance from TrendMicro

I have also demonstrated for the admins at the town hall that using Linux-PC on a "clean" network, surfing is no problem. By doing these small tests I have demonstrated that Linux is not the problem.

Tomorrow I'm going to visit the network providers admins, so that they could see what happens when a PC running Linux tries to access www.

What kind of things should I test to document, or find the problems? So far I have just used MTR to document slow respons, wget --no-proxy to document that www hangs and ends time out, ifconfig to show NiC settings, and route...

Could this be a problem with /etc/resolve.conf? 

The network provider is the same company that refused to turn on IMAP on the exchange servers, resulting in 3 week without mail at our school. All the other schools had to upgrade Outlook in order to connect to the new exchange-server with MS MAPI settings. MS Gold partners are so nice...

---

### Post by SeijiSensei on 2011-02-22
I think you should start with a Windows machine.  Perhaps the gateway only supports Internet Explorer.  I would try both IE and Firefox on a Windows machine and verify both can connect.

If IE works and Firefox does not, you might explore using [User-Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/) to masquerade your browser as IE.  If that works on Windows, it will probably work with Firefox on Linux as well.

---

### Post by pricetech on 2011-02-22
I'd also try a Windows VM to see if that works.

---

