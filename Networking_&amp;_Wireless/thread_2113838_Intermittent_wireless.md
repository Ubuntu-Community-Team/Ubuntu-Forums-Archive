---
title: "Intermittent wireless"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by Kopkins on 2013-02-08
When I first started using Ubuntu on my macbook 8,1, the wireless card was not supported. I had to compile and patch the driver for the broadcom 4331 chip. It works well and I've been using it for almost a year now. The module that needs loaded is b43 and I have set it up so system stuff like suspend doesn't mess with it. But sometimes just while I'm on the computer the module needs to be reloaded because I lose internet connectivity. The network is still connected, but no access to internet. so ```
sudo modprobe -r b43
sudo modprobe b43
```
Then the connection will be repaired. I do this 1-3 times a day. 

I also noticed now, that jockey-gtk (additional driver) has started showing me a broadcom STA driver for their hardware, but I don't see my chip listed there. And I feel like I read somewhere that the STA driver is not very good.

Should I just stick to my current setup or try the STA driver?

Thank you,

Kopkins

---

### Post by Kopkins on 2013-02-11
Does anyone know if the STA driver is good?

---

### Post by Benjamindaines on 2013-02-11
I have the same issue, my system will drop off the network and become unable to connect again until I reload the module, and even then it doesn't always work, or if it does it doesn't work for long.  I'm coming to the conclusion that the driver just kind of sucks, and bug reports need to be submitted, then we either have to wait and hope or figure out how to fix the driver ourselves. :\

---

### Post by Kopkins on 2013-02-11
Are you using the STA driver? Or did you compile it yourself?

b43 has been for me lately, I've reloaded 6 times today, and two of the times I didn't have to enter my password for sudo because they were so frequent.

Even if we file bugs, the more people affected, the faster the fix. Since this doesn't affect many people it would be a long time before anything got done, even then the STA driver is from broadcom and it would require them to fix it because it is proprietary.

I just realized the STA driver does not support my wireless card, even though it is shown in additional drivers.

---

### Post by Kopkins on 2013-03-15
This is driving me crazy, does anyone have any ideas? 
I can barely use my computer sometimes because I have to reload b43 for every new webpage i visit.

---

### Post by varunendra on 2013-03-15
> **Kopkins said:**
> This is driving me crazy, does anyone have any ideas? 
I can barely use my computer sometimes because I have to reload b43 for every new webpage i visit.
Please follow the 'Wireless Script' link in my signature, follow the instructions in the linked post and post back the contents of "netinfo.txt" file here so we can see what is going on.

Broadcom drivers are usually stable once working.

---

### Post by Kopkins on 2013-03-15
It was considerably long, I find it nicer to use pastebin for stuff like this. I hope you don't mind.

[http://pastebin.com/AxXDXD6E](http://pastebin.com/AxXDXD6E)

Thank you for your help, Varun.

Kopkins

---

### Post by varunendra on 2013-03-15
> **Kopkins said:**
> It was considerably long, I find it nicer to use pastebin for stuff like this.

A wise decision indeed :)

However, I couldn't find anything substantial in it except a long series of these -
> [27387.734095] wlan0: authenticate with *[COLOR="#000080"]<MAC address removed>[/COLOR]* (try 1)
[27387.748253] wlan0: authenticated
[27387.748757] wlan0: associate with <MAC address removed> (try 1)
[27387.752570] wlan0: RX ReassocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[27387.752579] wlan0: associated
[27421.429683] wlan0: **deauthenticating** from *[COLOR="#000080"]<MAC address removed>[/COLOR]* by local choice (reason=3)
[27422.985563] b43-phy1: Broadcom 4331 WLAN found (core revision 29)
[27423.195556] b43-phy1: Loading firmware version 666.2 (2011-02-23 01:15:07)

The last two lines are generated, I assume, when you unload/load the module again.

I suspect it is the result of a known bug in Network Manager where it keeps hopping from one access point to another when there are so many of them with same ESSID (DCCC in your case).

If so, the MAC addresses in the series of these messages **will be different almost everytime the message appears in dmesg**. In that case, I can think of two possible solutions/workarounds.

1)
Create different profiles (with different names) associated with different access points (Same ESSID, but different MAC addresses) and bind each with a specific MAC Id. Then you should be able to manually connect to one which seems to have strongest signal where you are. Since the profile is bound to a specific MAC address, it shouldn't try roaming across a different one.

But this is just my assumption, I haven't ever tried using multiple profiles with same ESSID myself, so can't assure if it'll work as I expect.

2)
Try wicd instead of Network Manager. It is known to work better in this situation.

---

### Post by varunendra on 2013-03-15
I was just pointed by my good friend [Hadaka]("http://ubuntuforums.org/member.php?u=1599436") to a Solved thread addressing similar problem : [http://ubuntuforums.org/showthread.php?t=2107365&highlight=BCM4331](http://ubuntuforums.org/showthread.php?t=2107365&highlight=BCM4331)

You might wish to try that before dumping NM.

I can't say for sure but I assume (by it's name) that the 'qos' parameter to b43 driver does just what NM is infamous for in this situation - always 'hop' to the better one. So maybe disabling that option (setting qos=0), as the post suggests, can help ?

---

### Post by Kopkins on 2013-03-15
I did switch over to wcid and whitelisted it's systray icon. I haven't had any issues with it yet, so I'll see how it goes. I'll try the info in that thread at some point. I did lose connectivity with wicd briefly, but it put the interface back up pretty quickly. I'm switching back to nm now to try passing those options. Hopefully it works. If not wicd seems to work pretty well.

Edit: enabled b43 with options using nw-manager. It's still too early to tell if it works. But wicd DOES lose connectivity intermittently, but is DOES reconnect better where nm seems to get confused about reconnecting(at least before I added the options to b43).

Thanks again.

---

### Post by varunendra on 2013-03-15
I'll eagerly wait for the final feedback, as this seems to be one of a few longstanding issues.
But for the same reason, I also like it to be tested long enough before the feedback.

---

### Post by Kopkins on 2013-03-15
It definitely isn't any better, maybe I need to reboot first. But I've had to reload b43 3 times by the time I am actually able to get from my homepage to this page. I won't be at school for a while which is where the problem is the worst (spring break), but I occasionally have the issue on my home network, which is curious because there is only 1 MAC address for the essid. I will post back as soon as I have any more info.

---

### Post by Kopkins on 2013-03-16
Adding those options does not work for me, I'm switching to WICD to see if it works better.

---

### Post by Kopkins on 2013-03-18
WICD is not working better, I'm still having real connectivity issues, only WICD is slower to reconnect after reloading the module.

---

### Post by wildmanne39 on 2013-03-18
Hi, it is likely that your encryption set to enterprise is causing the problem I would change it to just wpa2 personal if you have that option.
Thanks

---

### Post by wildmanne39 on 2013-03-18
Also according to modinfo
```
3.2.0-38-generic SMP mod_unload modversions 
larry@larrys:~$ modinfo bcma
filename:       /lib/modules/3.2.0-38-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y

```
you do not need b43 just bcma, I will do some more research on it.

I do know that it was not supported originally.

Edit: Never mind I think the issue was in the beginning that it shows as needing bcma in modinfo and it really needs the b43.

So it is most likely the encryption only.

---

### Post by Kopkins on 2013-03-18
My encryption was set to "WEP 40/128-bit key HEX or ASCII" not to enterprise. Regardless I changed it to wpa/wpa2 personal. Hopefully this works

---

### Post by Kopkins on 2013-03-18
I'm still not maintaining connectivity, but when I lose connectivity I have noticed that all of the connection show 100% signal strength.

I'm only on kernel 3.2, and I think that 3.3 is the one that addresses b43. Should I consider upgrading the kernel? Or upgrading to 13.04 or 12.10? I wanted to stick with the LTS but the wireless is really a problem.

---

### Post by monochromec on 2013-04-28
Also having problems with wireless access (ie. connections frequently dropped) after upgrading from quantal to raring. After toying around with the firmware settings a bit, I downgraded the kernel from 3.8.0-19 (apparently stock with raring) to 3.2.0-32 and the wifi connection is stable now.

---

### Post by Kopkins on 2013-04-29
I've tried kernels 3.0 3.2 3.3 3.5 3.7 3.8. So far 3.5 works the best. But I still haven't found a good fix. I have serious breakage with wireless. where sometimes I get kernel panics trying to connect via command line after the gui fails.

---

