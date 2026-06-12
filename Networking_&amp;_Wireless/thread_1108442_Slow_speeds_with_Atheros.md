---
title: "Slow speeds with Atheros"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by DutchShrek on 2009-03-27
well this has been asked before, but I can't seem to find any topics that have been solved (and carry the solution)

I have a Netgear WG311T, which should be the Atheros AR5001X+ chipset.
While I am connecting just fine, the transfer speeds are simply not up to par.

I'm dual booting Ubuntu 8.10 64 bit with Vista X64 and on vista I reach download speeds of up to 2MB/s
In Ubuntu on the other hand, I don't get above 500KB/s.

I read elsewhere that the link quality would have some effect on that.
iwconfig tells me the following:
```

ath0      IEEE 802.11g  ESSID:"ZWHT3"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:F4:D8:FC   
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxx-xxx-xx   Security mode:restricted
          Power Management:off
          Link Quality=24/70  Signal level=-69 dBm  Noise level=-93 dBm
          Rx invalid nwid:255  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Following other threads I managed to set the Bit Rate up to 54M, but that has not changed anything.
As you can see, the link Quality is around 24/70.

Now I have no idea what that means so I also don't know if it's the cause and how to fix it.
I'm extremely new to Linux as well so that's not helping me in my search either. (perhaps this should be in the absolute beginners forum :) )

If anyone knows if and how this can be fixed, I'd love to hear your input.

Thanks

---

### Post by pastalavista on 2009-03-27
Have you installed madwifi-tools? It is recommended for Atheros systems and is available in Synaptic PM  or ```
sudo apt-get install madwifi-tools
```After installing, reboot and try again. I don't know it will work for you but it does for me.

---

### Post by DutchShrek on 2009-03-27
would I have to uninstall the network manager currently active?
Because I just tried what you said but that by itself only made things worse.
Even firefox was failing on me.
I uninstalled it again for now.

---

### Post by pastalavista on 2009-03-27
It isn't a replacement for Network Manager so no, you don't have to uninstall but you do need to delete all previously configured connections. Madwifi is an auto-configurator I think.

[http://madwifi.org/]("http://madwifi.org/")

---

### Post by DutchShrek on 2009-03-27
hmmm well I guess I'll just give it a shot.
Thanks m8

---

### Post by DutchShrek on 2009-03-27
sorry, I'm lost
I just installed Madwifi again and I have no idea where to go from here.

You say I need to delete previously configured connection..
Well first, how do I do that? (go to edit connections and hit "delete" on my current one?)

And second, how do I get madwifi to configure it properly with the WEP encryption key?

---

### Post by pastalavista on 2009-03-27
sorry, I didn't have this link handy before. It's what I used...

[http://ubuntuforums.org/showthread.php?t=485579]("http://ubuntuforums.org/showthread.php?t=485579")

---

### Post by DutchShrek on 2009-03-27
well, I followed that to the letter. I had some trouble finding the package for madwifi-source package, because the link was dead.
I got no errors during install of any of it. So I'd call that a success at least.

But sadly no improvement in my connection.
Luckily it didn't get any worse either.
(I have my share of bad experiences in Windows when trying to improve something that's already semi-working, after "improvement" it failed entirely lol ) 

Anyway, thanks a lot for trying to help. I guess for now I'll just have to switch back to windows for big downloads.

edit, wait a minute....
I'm using Kget for downloads. At first I thought there was no improvement, but it seems to be going at little over 1MB/s
2 files at a time @ 500KiB/s.
It seems to fall back to 200 and goes up in waves.

I do call that an improvement compared to earlier.
Sure, it's not 2 MB/s like in Vista, but hey..we can't win em all.

So it looks as though your advice did help after all. let's hope it lasts, shall we
Thanks again

---

