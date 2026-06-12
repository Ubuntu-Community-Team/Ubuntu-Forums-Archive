---
title: "Netgear Wireless registering but not connecting"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by siabost on 2009-02-16
Ubuntu 8.04, Gigabyte Desktop, AMD Athlon XP3500, 512Mb memory, Netgear DG834Gv2 Wireless Modem/Router, WG311v2 802.00g PCI Wireless Adaptor (Texas Instruments).

Have configured the router via Network cable & even tried dissabling ipv6 to no avail. My wireless connection registers in Network Manager (@ approx 50%) but when I try to select it and enter my passphrase under WEP128 (open) it fails to connect & reverts to the wired connection (through the same router) which works fine.
Both card & chip are indicated as "working out of the box" in the Ubuntu Wireless Compatible list.

When  I have run a Hardware Test on the adaptor from the System/Administration menu without the wired connection I have got:
> ERROR:root:Could not find def gateway info in /proc 
Traceback (most recent call last): 
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module> 
    sys.exit(main(sys.argv[1:])) 
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main 
    host = route.get_default_gateway() 
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway 
    t1 = self._get_default_gateway_from_bin_route() 
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route 
    if def_gateway: 
UnboundLocalError: local variable 'def_gateway' referenced before assignment

I'm stuck - any help appreciated.

---

### Post by siabost on 2009-02-16
Forgot to say: I'm using the 64bit version of Ubuntu 8.04.

Seems from other posts this could be a "64bit" problem?

---

### Post by Favux on 2009-02-16
Hi siabost,

This work around may apply to your situation:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I hope this is useful.

---

### Post by siabost on 2009-02-19
Hi,

Thanks Favux - I tried some of the suggestions on that link but ultimately what I did was:

Reverted to Ubuntu 8.04 (32bit) - didn't solve problem: connection speed was stuck at 49% with router right by computer & no wireless internet.
Ran > lshw in terminal and there seemed (I'm no expert) to be no native driver loading for the card.
Installed ndiswrapper+GUI via Synaptic.
Downloaded XP driver from website.
Selected the .inf file via ndiswrapper.
Rebooted & voila - internet connection & signal strength up to 80%.

There may still be an issue with interference with another (native) driver though I can't see it as signal strength is still s little down on what I would expect... but it connects!

This may work with Ubuntu 8.04 (64bit) but I haven't tried it.

Any thoughts, anyone, on why an "Out Of The Box" Wireless PCI card would cause so much hassle?

Thanks.

---

