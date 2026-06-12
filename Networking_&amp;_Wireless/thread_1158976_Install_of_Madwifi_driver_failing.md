---
title: "Install of Madwifi driver failing"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by mattewens on 2009-05-14
> :~/madwifi-0.9.4$ sudo make install
> sh scripts/find-madwifi-modules.sh 2.6.28-11-generic
> for i in ath/ ath_hal/ ath_rate/ net80211/; do \
>                 make -C $i install || exit 1; \
>         done
> make[1]: Entering directory `/home/user/madwifi-0.9.4/ath'
> test -d //lib/modules/2.6.28-11-generic/net || mkdir -p
> //lib/modules/2.6.28-11-generic/net
> install ath_pci.ko //lib/modules/2.6.28-11-generic/net
> install: cannot stat `ath_pci.ko': No such file or directory
> make[1]: *** [install] Error 1
> make[1]: Leaving directory `/home/user/madwifi-0.9.4/ath'
> make: *** [install-modules] Error 1
> :~/madwifi-0.9.4$ iwconfig
> lo        no wireless extensions.
>
> eth0      no wireless extensions.
>
> wmaster1  no wireless extensions.
>
> wlan0     IEEE 802.11bg  ESSID:""
>           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
>           Tx-Power=20 dBm
>           Retry min limit:7   RTS thr:off   Fragment thr=2352 B
>           Power Management:off
>           Link Quality:0  Signal level:0  Noise level:0
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
>
> pan0      no wireless extensions.
>
> wmaster0  no wireless extensions.
>
> wlan1     IEEE 802.11abg  ESSID:"********"
>           Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
>           Tx-Power=20 dBm
>           Retry min limit:7   RTS thr:off   Fragment thr=2352 B
>           Power Management:off
>           Link Quality:0  Signal level:0  Noise level:0
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sp0nge on 2009-05-14
I'm getting a similar error when rebuilding the compat wireless driverset after the latest update. I thought this had something to do with updates to the linux-headers but this didn't seem to effect my situation. 

I'm not sure what to do now, but I'll keep tinkering and let you know if I figure it out.

---

### Post by mattewens on 2009-05-15
Any progress on this one guy's?

---

