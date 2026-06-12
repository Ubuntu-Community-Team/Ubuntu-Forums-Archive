---
title: "Ethernet connection does not come back if cable had been manually disconnected"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by klearvue on 2011-01-28
OS: Maverick
Ethernet driver: tested with sky2 an sk98lin 

This has been driving me crazy for the last few months: if I unplug ethernet cable while my laptop is on reconnecting it sometimes does not bring the connection back.

And once ethernet is gone nothing that I try seems to consistently bring it back. Rebooting, disabling/enabling the driver, disabling/enabling NIC in BIOS, changing driver from sky2 to sk98lin, deleting connection from Network Manager, resetting the router - nothing helps.

It seems to come back randomly a few weeks later. Once I used live Ubuntu on a USB stick and ethernet came back not only on a live distro but then when I rebooted also on my main OS. But when I tried that trick next time ethernet was missing in the live distro as well.

Also once I was able to revive ethernet but compiling sk98lin driver, blacklisting sky2 and rebooting. Of course next time doing the same routine did not help.

The thing is - ethernet works fine with either sky2 or sk98lin and I can unplug the cable and plug it back in most of the time without any issues. But then every so often - bang and I'm stuck with only wireless until ethernet suddenly starts working again.

Any help would be greatly appreciated.

---

### Post by grahammechanical on 2011-01-28
The poor little machine does not know whether it is coming or going.

Do you switch off the modem/router before you pull out the cable? Do you disconnect the connection before you pull out the cable? All that problem solving may have muddled up the configuration files. There may now be conflicting settings.

Regards.

---

