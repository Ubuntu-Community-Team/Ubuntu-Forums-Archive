---
title: "vpn configuration issue in 10.04"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by Francium on 2010-07-12
i am running lucid and trying to setup my (pptp) vpn  connection. i know my usr and pass and host name is correct because i'm  using them by windows, but whenever i try to connect to my vpn from network manager, immediately it says :  vpn connection "vpn  connection 1" failed. i have searched many hours but didn't find a  solution. i also tried to connect via command line through the guide in :  [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient),  but when i try "sudo pon myvpn nodetach" it says gethostbyname  'Usfree.hideipvpn.net': HOST NOT FOUND, but i used that name in windows  and it worked there. do i did something wrong which i don't know? any  help is appreciated...

---

### Post by JHuizingh on 2010-08-12
Did you have any luck in figuring this out?  I'm in the exact same situation where it works from windows but not linux.

---

### Post by JHuizingh on 2010-08-12
YES!!!!!!!  I found and old post by zyrorl in the forums here:  [http://ubuntuforums.org/showpost.php?p=6187094&postcount=10](http://ubuntuforums.org/showpost.php?p=6187094&postcount=10)


> **zyrorl said:**
> 
Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE). Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

...  Steps 4 and 5 were no longer relevant for me.  They involved using gconf-editor to modify a value, but when I tried the value was already correct ...


Step 6.

Test your vpn connection. It hopefully should work Bon Appetit.

Hope this helps!  :KS

---

