---
title: "Possible solution for those without wired ethernet"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-02-19
I have an old Linksys router taking up space and decided to play with it.  I installed DD-WRT on it.  DD-WRT is a 3rd party firmware which adds several useful features, one of which is a wireless client bridge.  As I was playing with it, I decided such a device could be useful to linux users with problematic wifi adapters.

I've read several posts by people in dorms or apartments that had no access to a wired network connection; they were wireless only.  That's grand until you need a wired network connection to download a wireless driver.  You can't get your wireless adapter working because you need a wired connection that you don't have to download the fix.  Catch22.

Enter the wireless bridge. It gets you a wired ethernet connection using a WiFi signal. You now have a wired network connection with which to download replacement drivers or simply use the ethernet connection without worrying about the integral wireless adapter if you don't need portability.  I imagine one could also use a wireless bridge with a printer that had ethernet but not WiFi connectivity.  One can of course buy purpose designed wireless bridges but they may not be cheap.  Surplus routers may be free.

Understand that not all routers support DD-WRT or other 3rd party firmware.  For those that do, it's pretty straight forward to install.  To enable wireless bridge mode, I followed the directions found here.  I thought the directions were well written:

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

Here were the relevant parts for me:
> **Configuring DD-WRT as a Client Bridge**

 
[LIST]
[*]1. Once you have DD-WRT installed, open your browser to  [http://192.168.1.1](http://192.168.1.1) and log into the router. In older versions of DD-WRT,  the default username is *root *and the default password is *admin*. Be sure to change the default password to secure your router.
2. Next, click on the *Wireless* tab at the top.
3. Set the *Wireless Mode* to *Client Bridge*. Then click *Apply*.
4. Set the *SSID* to that of your main wireless router that is connected to the Internet.  In my case, my main wireless router SSID is *sierra*. Then click *Apply*.
[IMG]http://main.makeuseoflimited.netdna-cdn.com/wp-content/uploads/2008/11/step-1-client-bridge-apply.png[/IMG]
5. Click on the Wireless Security tab in the second row of tabs, and  configure the router to match the security settings as your main router.   In my case, my main wireless router has WPA security mode with TKIP  shared key, so I set up DD-WRT to match it.
6. Click *Apply*.
[IMG]http://main.makeuseoflimited.netdna-cdn.com/wp-content/uploads/2008/11/step-2-wireless-security.png[/IMG]
7. Click the *Setup* (very first tab in the upper left) to configure the LAN settings.
8. Assign the router a **Local IP Address** on the same  subnet as your main router, but give it a different address.  That means  that all the numbers for the address will be the same as the main  router except for the numbers in the fourth box.  For example, the  address of my main router is 192.168.1.1 so I gave my DD-WRT router an  IP of 192.168.1.2.
9. Set the *Subnet Mask* to 255.255.255.0. 
10. Set the *Gateway* and *Local DNS* to the address of the main router.
[IMG]http://main.makeuseoflimited.netdna-cdn.com/wp-content/uploads/2008/11/step-3-lan-settings.png[/IMG]
11. Click *Apply*.
[/LIST]
 Your DD-WRT router should now allow you to connect your remote  computer to your main internet router through the airwaves!  If you ever  need to reconfigure the DD-WRT router, just be sure to remember the new  IP address that you assigned in step number 8.  You could always use a  nice label maker and slap it right onto the router.
Do bear in mind that names,  addresses, encryption standards etc. will be different than those printed but the idea is the same.  I hope this will help someone.

---

