---
title: "Network Connectivity - RTL8110cs"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by kowala on 2009-03-10
Hello guys,

After days of searching for a solution I am finally posting my problem...I probably should have reversed the above order of operations.

I have just installed Ubuntu 8.10.  I have an Abit IP35 Pro motherboard with two onboard Realtek RTL8110sc NIC.  When I L-click on the Network Manager button atop the screen I have two greyed out connections, Auto eth0 and Auto eth1.  These are both named Wired Network (ABIT Computer RTL-8110SC/8169SC Gigabit Ethernet).  I assume this means the operating system is recognizing the device type and has the proper driver.  While both NIC cards are configured to run DHCP they do not attain an address.

I actually prefer a static address so I created my own Wired Connection but then ran into the bug where the default eth0 connection becomes the default on reboot.  It seems this bug was well documented and I followed the instructions below.[instructions]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")

In short these were to remove the Network Manager followed by editing the /etc/network/interfaces and /etc/resolv.conf.  While I had little trouble editing these two files this did not prove to be a fix.  After setting the NIC's to static addressing I could ping the NIC's from the Ubuntu machine.  I could not ping my default gateway.

I have also tried the instructions found at [http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/") which show a way to keep Network Manager installed and setup static addressing.

The bottom line is static or dhcp...neither seem to work.

I then ran across this post [http://ubuntuforums.org/showthread.php?t=1091989&highlight=rtl8169]("http://ubuntuforums.org/showthread.php?t=1091989&highlight=rtl8169")which claimed that blacklisting the r8169 driver and reinstalling the r8168 driver proved to be a fix.  I tried this method as well without success.

One thing of interest to me is that when the pc first boots the router shows a connection light.  The moment I logon to Ubuntu the light goes dark.

Anyway...I really don't want to toss in the towel on my home Ubuntu server.  I am open for any suggestions.

Thank you,

Kowala

---

