---
title: "Static IP not kept on reboot"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by daniel_summers on 2009-12-28
I've got an Xubuntu 9.10 laptop that's been assigned a static IP address, and must have that address to access network resources at work.  However, as it's a laptop, there are times I take it home or on travel, and at that point, I need to be able to use DHCP to get a dynamic address.

I've set it up using the guide at [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/) , which works until reboot.  There is a note that for this to stick, you may have to uninstall the DHCP client.  Well, that's not an acceptable solution in my case.  :)  Is there a way to specify a static IP for eth0 (i.e., eth0 will NEVER participate in DHCP), while maintaining DHCP capability for wlan0?

Thanks...

---

### Post by shairozan on 2009-12-28
Have you tried setting the IP address manually through the network manager as opposed to the interfaces file? While that works fine on a server that doesn't have anything specifically controlling the network connections, I believe you might be better served to use the UI. 

To do this, you can right click on the network connection icon (either wireless or the computer for a wired icon) and select "edit connections"

Select your connection and hit edit

The 4th tab, or IPV4 settings will have options for setting a static address or acquiring one via DHCP. Try that and see if it works. Then, if you ever need a DHCP address, you can go to the same menu and set it back to DHCP. Very similar to how Windows does it.

---

### Post by daniel_summers on 2009-12-28
Excellent - that's what I was thinking, but when they took Network Manager out of the menus, I didn't know how to get there.  I've set it through there, and will post back here next time I reboot and let you know whether it took.  :)  Thanks!

---

### Post by daniel_summers on 2009-12-29
Just rebooted, and it kept the IP.  Thanks for the help!

---

