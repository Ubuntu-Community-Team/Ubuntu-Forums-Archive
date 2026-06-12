---
title: "Wireless connection working, network appears in list, but does not connect to it"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by Rakknar on 2011-03-16
Hello,

I'm having some problems with my wireless connection. I'm on Ubuntu 10.04, on a HP ProBook 4520s, with a RaLink RT3090 wireless network card. I installed the drivers (hopefully correctly), the wireless seems to work correctly, it scans and finds networks, but when I try to connect to one, it times out after some time, while still attempting to connect. I also have a wired connection that works correctly and without problems. Other computers that try to connect to said wireless network manage to do so without any problems, so this has left me a bit baffled, since, like I said, everything seems to be in order. 
I'm a new Ubuntu user, so please tell me what other information I need to provide in order to easily and successfully facilitate troubleshooting this, because it is, as you can imagine, quite aggravating, having a laptop that needs to be connected to the internet through a cable.


Thank you,
Ragnar

---

### Post by Dumpy Dumpster on 2011-03-16
Having just had similar problems to you, I can recommend this:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Good Luck - it can be very frustrating!

---

### Post by Rakknar on 2011-03-16
Thank you for the quick reply. The problem is, I didn't install the Windows driver with ndiswrapper. While I did install ndiswrapper, I didn't use it to install the driver; I used the linux drivers that are on the ralinktech.com webpage. 

Using the first command from the link you provided, "ndiswrapper -l", I get this:

displaybyhwid : invalid driver!
hwid : invalid driver!

---

### Post by Rakknar on 2011-03-17
Can anybody help? Please?

---

### Post by grahammechanical on 2011-03-17
If network manager is scanning and finding wireless networks, then Ubuntu is using your wireless adapter with the drivers that are installed.

This issue is this: Are you using the correct pass phrase or wireless key? Are you using the correct encryption type?

Regards.

---

### Post by Rakknar on 2011-03-18
Hi,

I google'd some more last night and found this: [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) 
I managed to make it work, somewhat. It now receives packages from the wireless I try to connect to, but it still times out after a while, before establishing a link. On the other hand, I can connect to non-secure wireless networks.
The wireless network I need to connect to has WPA2 security, I think that might have something to do with it... WinXP connects to it just fine, so does Win7, it's only Ubuntu that just refuses to do anything.

Regarding pass phrase or wireless key... I have no idea what those are, could you please elaborate?


Thanks,
Ragnar

---

### Post by varunendra on 2011-03-19
What grahammechanical means is the password that you have to supply to connect to a secure wireless network.

In Ubuntu it is usually done as follows:


[LIST=1]
[*]Right click on the network-manager icon (that appears as concentric arcs on the top-right corner on screen)
[*]Select "Edit Connections"
[*]Select "Wireless" tab
[*]Select your wireless network in the list and click "Edit"
[*]Goto "Wireless Security" tab
[*]Select correct 'Security' type (should be "WPA & WPA2 Personal" in your case)
[*]Enter the correct password (mind the case of letters!)
[*]Click Apply and close the dialogue-boxes.
[/LIST]
If this doesn't fix things, try switching the 'Security' type from "WPA & WPA2 Personal" to "WPA & WPA2 Enterprise" (less likely).

---

### Post by Rakknar on 2011-03-21
Thank you for the reply.

The password is correct, the security type is WPA2 (personal). If I change it to enterprise, I don't resolve anything, as it asks for settings that were not set up in the first place...

Regards,
Ragnar

---

### Post by Rakknar on 2011-03-24
I managed to solve it, I guess. All I did was go into the "Edit Connections..." menu, to the Wireless tab, where I have the network where I want to connect to and select "None" for security. When I tried to reconnect, the pop-up to enter the password appeared and I selected WPA2 from there and entered my password et voila. It connected.

Thank you for all the replies and help!

---

