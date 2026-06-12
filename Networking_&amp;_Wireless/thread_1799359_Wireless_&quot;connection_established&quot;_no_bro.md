---
title: "Wireless &quot;connection established&quot; no browse no ping"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by jimhabegger on 2011-07-07
Ubuntu 11.04, wireless adapter BCM4312.

The connection works for a while, for a random length of time from a few minutes to a few hours, then stops working. The laptop says it's connected, and the router says it's connected, but the browser can't find any Web pages, it can't find the router, and there is no response to pings from the router or any other device on the local network or on the Internet. "Host unreachable." When I try to ping to the laptop from another one, it times out.

If I shut down the computer and try again a few hours later, it works fine again for a while, then after a while it stops working again.

In case it's relevant, sometimes when I restart networking from the command line, it says "ignoring unknown interface eth1=eth1," even though ifconfig -a lists eth1 as up with an ip address. eth1 is the wireless adapter. 

Another laptop with Ubuntu 11.04 connects to the same router with no problems.

Using a fixed IP address doesn't change anything.

---

### Post by R Clemons on 2011-07-07
Having a similar problem on 11.04 with an Atheros AR928X Wireless Network Adapter.  If I disconnect from the network and then reconnect it starts working again.  Never had this problem on Maverick.

---

### Post by jimhabegger on 2011-07-07
Disconnecting and reconnecting doesn't work for me.

---

### Post by westie457 on 2011-07-07
> **jimhabegger said:**
> Ubuntu 11.04, wireless adapter BCM4312.

The connection works for a while, for a random length of time from a few minutes to a few hours, then stops working. The laptop says it's connected, and the router says it's connected, but the browser can't find any Web pages, it can't find the router, and there is no response to pings from the router or any other device on the local network or on the Internet. "Host unreachable." When I try to ping to the laptop from another one, it times out.

If I shut down the computer and try again a few hours later, it works fine again for a while, then after a while it stops working again.

In case it's relevant, sometimes when I restart networking from the command line, it says "ignoring unknown interface eth1=eth1," even though ifconfig -a lists eth1 as up with an ip address. eth1 is the wireless adapter. 

Another laptop with Ubuntu 11.04 connects to the same router with no problems.

Using a fixed IP address doesn't change anything.

Hi Not 100% sure we can fix this before it gets too technical.

Do you know which driver you are using?

Are you using the STA driver installed via 'additional drivers' or a different one? 
Go to System > Administration > Additional Drivers this will tell you which non-free drivers are installed on your system. Post back here when you know what you have please.

---

### Post by jimhabegger on 2011-07-07
Additional drivers:
Broadcom STA wireless driver

---

### Post by westie457 on 2011-07-07
Okay we should be able to get this sorted with the following method that is an adaptation of one I had to do myself.

Ready here we go.

1 In 'Additional Drivers' de-activate the STA driver. Ignore any message that says to reboot.

2 Open 'Synaptic Package Manager' and type your password when asked.

3 Do a search for 'bcm'using the button to the right of quick search.

4 Mark the STA driver for complete removal

5 Now go to Settings > Repositories and in the Ubuntu Software tab make sure the top 4 boxes have a tick in them then click Close. Then click reload to update the sources.

6 Now search, using the same search box that you used earlier, for 'firmware-b43-lpphy-installer'. Mark for installation. You should notified that this package depends on 'b43-fwcutter' and should be installed at the same time. Accept this then click on apply.

7 When the dust has settled it will be time to reboot and you should now have a stable connection.

Any problems come back here and post what they are.

No problems come back here and mark this as solved please

---

### Post by westie457 on 2011-07-07
OOPS. Silly me forgot to mention that you will need a cable to do this.

---

### Post by jimhabegger on 2011-07-07
Thank you, westie!

I tried your method about an hour ago, and it's still working, after moving the laptop twice. Not sure about it yet, because sometimes before, it worked for several hours before it stopped working again. I'll wait a few more hours before marking it solved.

Two notes, for anyone else who tries this solution:

1. In step 1, there was no option to de-activate. The only option was "remove." After that, I did not find anything searching for "bcm" in installed programs. I suspected that the remove option uninstalled it, and to verify that, I re-activated the driver. Then I was able to find it with the "bcm" search in installed programs. Then I went back to "Additional Drivers" and removed it again, and skipped to step 5.

2. The download of firmware-b43-lpphy-installer stalled for a long time. I was just about to log out to abort it, when it finally timed out and restarted, continuing where it left off. After that, it kept getting slower and slower, almost down to nothing before it finished downloading.

> **westie457 said:**
> Okay we should be able to get this sorted with the following method that is an adaptation of one I had to do myself.

Ready here we go.

1 In 'Additional Drivers' de-activate the STA driver. Ignore any message that says to reboot.

2 Open 'Synaptic Package Manager' and type your password when asked.

3 Do a search for 'bcm'using the button to the right of quick search.

4 Mark the STA driver for complete removal

5 Now go to Settings > Repositories and in the Ubuntu Software tab make sure the top 4 boxes have a tick in them then click Close. Then click reload to update the sources.

6 Now search, using the same search box that you used earlier, for 'firmware-b43-lpphy-installer'. Mark for installation. You should notified that this package depends on 'b43-fwcutter' and should be installed at the same time. Accept this then click on apply.

7 When the dust has settled it will be time to reboot and you should now have a stable connection.

Any problems come back here and post what they are.

No problems come back here and mark this as solved please

---

### Post by sw00 on 2011-09-05
Thank you westie457, solved my problem perfectly.

---

