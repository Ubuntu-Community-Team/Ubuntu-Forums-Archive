---
title: "Slow boot up"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by aseem_mal on 2006-02-02
Hi. Ever since I switched from Wired to Wireless internet, the Ubuntu start-up slows down. During start-up, It actually loads all the processes, then when it reaches "Configuring Network Interfaces", it stops for about 60 to 90 seconds, then contniues to boot-up.:-k 

I changed my networking back to wired, and it did not stop at the "Configuring Network Interfaces" stage.

Note: My wireless network uses DHCP with WEP connection.

Any ideas, tips, tricks?:confused:

---

### Post by mpvano on 2006-02-02
1. Make sure you've specified your ESSID, and CHANNEL NUMBER (or Frequency - most drivers only accept one or the other) in your wireless configuration.

2. Make sure you are not using a wireless access point that's incorrectly configured as far as channel number goes. If you can find out if there are any other wireless access points in range of your computer - check their channel numbers.

If your card supports scanning (many don't!) you can do this by using the command "sudo eth0 iwlist scan" (substitute your interface name for eth0). Note that you must run the command with sudo or the information it returns may be stale, since it won't do a new scan if you're not running as root.

If your card doesn't scan, try the same thing in windows or get someone with windows over to do a scan for access points - this still works in most windows wireless drivers.

Surprisingly, you can operate for a long time without realizing your sharing a channel - there's more than enough bandwidth on a channel for several internet connections - however this REALLY confuses some drivers when they try to connect initially.

Where I live (Minnesota) there's been an explosive growth in access points. Everywhere I go (including my HOME) there are now at least two overlapping networks, greatly increasing wireless connection problems on ALL platforms. I think everyone got new routers for Christmas!

There are really only three possible channels in an overlapping coverage area - channels are 6 channels wide. This means that if you have a neighbor on channel 6 (the usual default) You need to be on channel 1 or 11 to operate properly.

If those channels are already all in use then you should figure out which are the two weakest ones and try to avoid the strongest one. Typically, the next channel choices are 3 and 9, etc.

3. Don't use DHCP. Check your router's DHCP range and assign yourself a static address in the range it does NOT use for DHCP. You will probably need to manually set the gateway and DNS addresses as well if you don't use DHCP, but you can find those numbers out by doing "ifconfig", "cat /etc/resolv.conf"  and "route" commands under your existing settings.

You can still leave DHCP set up for your visitors or for computers you rarely use with wireless. Most routers use a 254 address subnet. Using 100 for DHCP still leaves you plenty of static addresses. Actually most routers already restrict the DHCP range to less than the full range of addresses - all you need to do is check the router configuration and use any address outside that range that's not in use - Typically this means avoiding .0, .255, and .1 (most routers use .1 for themselves).

4. If you don't know how to set up your network using values typed into /etc/network/interfaces, read the man page on that file. That's where you can set up all these things and your encryption keys so that your boot up takes no time at all.  Most other ways to configure your networks don't allow you to force all of these values.

5. If you know your neighbors and feel confident enough about doing this, suggest to them that they add WEP keys to any open networks they are running. Even if they don't need or want the security, open networks "capture" your card more easily at startup. If they REALLY want to allow free access, tell them to use 40 bit keys and make the key something stupidly easy to remember.

This will still leave you the problem of switching BACK from DHCP settings when you have been out at a coffee shop or something. I switch all network settings by actually switching /etc/network/interfaces files then restarting all the interfaces, but if the last settings I was using used DHCP, it can take Ubuntu's current DHCP client a very long time to quit so that I can get on with resetting the connection.

Beginners often have trouble making wireless work because they don't realize they've wedged their system with several zombie DHCP client instances running at once if they try switching settings too quickly out of desperation....

hope this helps you out....

Mario

---

### Post by aseem_mal on 2006-02-02
That sure worked!!! Thanks a bunch.


[QUOTE=mpvano]1. Make sure you've specified your ESSID, and CHANNEL NUMBER (or Frequency - most drivers only accept one or the other) in your wireless configuration.

2. Make sure you are not using a wireless access point that's incorrectly configured as far as channel number goes. If you can find out if there are any other wireless access points in range of your computer - check their channel numbers.

If your card supports scanning (many don't!) you can do this by using the command "sudo eth0 iwlist scan" (substitute your interface name for eth0). Note that you must run the command with sudo or the information it returns may be stale, since it won't do a new scan if you're not running as root.

If your card doesn't scan, try the same thing in windows or get someone with windows over to do a scan for access points - this still works in most windows wireless drivers.

Surprisingly, you can operate for a long time without realizing your sharing a channel - there's more than enough bandwidth on a channel for several internet connections - however this REALLY confuses some drivers when they try to connect initially.

Where I live (Minnesota) there's been an explosive growth in access points. Everywhere I go (including my HOME) there are now at least two overlapping networks, greatly increasing wireless connection problems on ALL platforms. I think everyone got new routers for Christmas!

There are really only three possible channels in an overlapping coverage area - channels are 6 channels wide. This means that if you have a neighbor on channel 6 (the usual default) You need to be on channel 1 or 11 to operate properly.

If those channels are already all in use then you should figure out which are the two weakest ones and try to avoid the strongest one. Typically, the next channel choices are 3 and 9, etc.

3. Don't use DHCP. Check your router's DHCP range and assign yourself a static address in the range it does NOT use for DHCP. You will probably need to manually set the gateway and DNS addresses as well if you don't use DHCP, but you can find those numbers out by doing "ifconfig", "cat /etc/resolv.conf"  and "route" commands under your existing settings.

You can still leave DHCP set up for your visitors or for computers you rarely use with wireless. Most routers use a 254 address subnet. Using 100 for DHCP still leaves you plenty of static addresses. Actually most routers already restrict the DHCP range to less than the full range of addresses - all you need to do is check the router configuration and use any address outside that range that's not in use - Typically this means avoiding .0, .255, and .1 (most routers use .1 for themselves).

4. If you don't know how to set up your network using values typed into /etc/network/interfaces, read the man page on that file. That's where you can set up all these things and your encryption keys so that your boot up takes no time at all.  Most other ways to configure your networks don't allow you to force all of these values.

5. If you know your neighbors and feel confident enough about doing this, suggest to them that they add WEP keys to any open networks they are running. Even if they don't need or want the security, open networks "capture" your card more easily at startup. If they REALLY want to allow free access, tell them to use 40 bit keys and make the key something stupidly easy to remember.

This will still leave you the problem of switching BACK from DHCP settings when you have been out at a coffee shop or something. I switch all network settings by actually switching /etc/network/interfaces files then restarting all the interfaces, but if the last settings I was using used DHCP, it can take Ubuntu's current DHCP client a very long time to quit so that I can get on with resetting the connection.

Beginners often have trouble making wireless work because they don't realize they've wedged their system with several zombie DHCP client instances running at once if they try switching settings too quickly out of desperation....

hope this helps you out....

Mario[/QUOTE]

---

### Post by dsierpin on 2006-02-02
mpvano-

Thanks so much for the detailed response.  You are obviosly extremely knowledgeable on this subject.  The time and effort you took in writing this reply will be extraordinarily helpful to MANY people; it is much appreciated.   It's folks like you that make this community what it is.

---

### Post by andrewski on 2006-05-31
By the way, I'm not sure what was done to solve this, but Dapper doesn't have the same problems at that point.  It just rocks. :cool:

---

