---
title: "Howto: set up 3G21WZ router for ssh access"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by paulmilliken on 2011-03-29
This is a guide for how to set up a 3G21WZ wireless router.  Telecom New Zealand sells this router as a "Telecom Turbo Wireless Router" [http://store.telecom.co.nz/mobile/prepaid/mobilebroadband/telecom-turbo-router]("http://store.telecom.co.nz/mobile/prepaid/mobilebroadband/telecom-turbo-router").

1. Insert your data-enabled SIM card into the slot on the router and turn the router on.
2. Connect your PC to the router with an ethernet cable.  Type "ifconfig" on the command line and your entry for eth0 should give you your computers dynamically assigned IP address.  (Mine was 192.168.1.2).  If yours differs in the last number then take note of this.
3. Open firefox and enter 192.168.1.1 in the address bar.  This will connect you to the router via its web-interface.  The username is "admin" and the password is also "admin".
4. Click on the tab called "HSPA/3G SETTINGS" and click "disconnect".
5. Change the options to those shown in the image hspa_3g_settings.png below.  Note that it is important to use the APN direct.telecom.co.nz, otherwise all traffic initiated outside your LAN will be blocked!
6. Click "Save".  Then click connect.
7. Click the tab marked "Advanced".  Now select "NAT" and "Port Forwarding".
8. Set up port forwarding as shown in the image advanced_nat_portforwarding.png
9. Now click on "Advanced" and select "Security", "IP filtering" and "Incoming". Change the settings to look like those in the image security_ipfiltering_incoming.png.
10. Now click on "Management" and select "Save/Reboot"
11. Now click on "Basic" and "Home" and wait for a couple of minutes.  Then you should see your WAN IP address listed in the range 122.56.*.*.  Note that if your IP address is in the range 115.189.*.* then your APN is set to the default one and you will need to return to step 5 to enable ssh access.  (However, if you only want to connect to the internet then the default APN will be fine).

---

### Post by amenfield on 2012-01-26
This is really useful stuff.  Shame I can't see the pictures because I am new to the forum.  please can you tell me the settings for the IP filtering incoming.

---

### Post by amenfield on 2012-01-26
Hurrah - I can see the pictures now.  3G connection is a but flakey as we live out in the country, but it now basically works.  Thank you very much for this. :)

---

