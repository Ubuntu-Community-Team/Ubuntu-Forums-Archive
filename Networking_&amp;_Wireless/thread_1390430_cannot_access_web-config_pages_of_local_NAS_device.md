---
title: "cannot access web-config pages of local NAS devices (NSLU2, Dlink DSM-G600)"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by moleymoley on 2010-01-25
Up until yesterday I was able to access these devices through the web interfaces that they use.
I'm running Ubuntu Karmic 9.10
I have 3 PCs running on my network, and 2 NAS devices:
Ubuntu (main computer, also has an XP partition)) - static IP 192.168.1.30
Ubuntu netbook  - DHCP IP
Windows XP (HTPC) - static 192.168.1.50
Linksys NSLU2 (was running Debian, problem arose when trying different configuration, now back to stock firmware)  - static IP 192.168.1.100
Dlink DSM-G600 - static IP 192.168.1.120

I used to be able to able access these just fine using my main Ubuntu setup.
Now, it will no longer display the pages. Internet access is fine, i can even access my DSL/Router device's internal config page.

The netbook and the Windows HTPC can both log into these devices, as well as the XP partition of the Ubuntu system. 

I have tried using a VM of XP within Ubuntu, bridging the network device, i have the same symptoms - internet is fine, cannot access local network web-logins.

Access to fileshares among all machines remains unchanged.

another odd behavior is that i can SSH into the NSLU2 device from all the machines, but i get odd things from this computer - it will let me log in, asks for a username and pass, but if i run anything like mc or htop, it just blanks the terminal in an odd way.
from other computers the login and display are fine...

I have tried flushing the ip tables and routing tables using the info described within the following links:
[http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)
and
[http://www.computechgroup.com/?p=276](http://www.computechgroup.com/?p=276)


:confused::confused::confused::confused::confused:please - any help would be appreciated.:confused::confused::confused::confused:

---

### Post by moleymoley on 2010-01-26
nothing?
bummer. Well, I'm flashing the NSLU2 from the netbook, which i suppose i can admin from there as well, but most of my daily tasks are at the main Ubuntu box, and most importanly i'd really like to know what went wrong :(

i hope this thread stays alive long enough for a guru to shed some light on the situation

---

### Post by moleymoley on 2010-01-26
update - ive flashed the NSLU2 with Debian - from the problematic Ubuntu box i am able to SSH into it, and run bash commands, that works fine. The minute i try to run any program that is sort of "graphical" (for lack of knowing what they are called) ie MC, HTOP, or APTITUDE, i dont get the full display and lose my ability to perform any more commands, and need to kill the SSH session.
boo. i really really wish i knew what was up.
BY the way, i still cannot log into the D-Link NAS.

---

### Post by moleymoley on 2010-03-05
-SOLVED- (sort of)
a little over a month later, still having the same problems with a fresh install of Ubuntu, I solved this on my own.
I plugged in a wireless USB card and no longer had the strange problem displaying ncurses apps over SSH. All my weird network problems cleared up.
Removed the wireless, problems came back.
Suspected driver.
Found out i've got the SIS190 integrated NIC driver, and it well, blows.
However, changing the MTU as suggested in this post worked like a charm:

[http://ubuntuforums.org/showthread.php?t=395712](http://ubuntuforums.org/showthread.php?t=395712)

no more problems. to make it stick, i just changed the value in Network Manager to 1492 (a good year)

all set, finally.

Thanks for the help ;)

I hope this post may one day help someone - sorry for the lack of step-by step details though.

---

