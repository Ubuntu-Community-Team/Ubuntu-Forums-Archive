---
title: "IP config issue"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by fieldway on 2009-11-13
Hi

I installed 9.10 32bit server as well as  Moodle and Drupal6 package which install fine but can't access from a browser

I can ping IP address and get a reply, but once I try to open IP address in a browser the below message come back.  I also try to edit the /etc/network/interfaces with the IP, network, mask etc.. and this cause the machine to lost all network connection.  get no reply when enter ifconfig


"What should you do now?
Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing."

Any ideas how to solve this would be great

---

### Post by Yoann Juet on 2009-11-14
Try to connect to your server through a terminal window then type in the following command :

# telnet @YOUR_SERVER_IP 80

If you can get an established connection, the issue would be applicative ; otherwise, check for firewall rules, default routing, subnet mask (...)

---

