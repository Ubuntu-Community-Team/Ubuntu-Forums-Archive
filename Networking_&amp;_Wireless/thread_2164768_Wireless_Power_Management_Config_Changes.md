---
title: "Wireless Power Management Config Changes"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by icecreamguy on 2013-08-01
Hello! I've been having some trouble with the wireless power management configuration on my Asus U36S laptop since moving to 13.04 from 12.04. I use Gnome Remix, but I don't think that figures into this problem. The specific trouble that I'm having is that I'm unable to figure out how to tell the power management system to not enable power management on my wireless chip when on battery power. There is a known issue with this chipset's power management system that causes extremely poor wireless performance, see [http://blog.linuxjunkie.com/blog/2012/04/11/linux-and-the-intel-centrino-wireless-n-1030/](http://blog.linuxjunkie.com/blog/2012/04/11/linux-and-the-intel-centrino-wireless-n-1030/) for a little more background info. When the laptop goes on battery, I have been unable to have the OS not enable power management - it automatically enables it and kills wireless performance as soon as I go on battery no matter what I do. Disabling power management with iwconfig manually works fine, however editing the pm script seems to have absolutely zero effect in 13.04. In fact, removing the scripts /usr/lib.../wireless and /etc/pm.../wireless appears to do nothing. Additionally, I have grepped all of /etc and /usr for the term "iwconfig_batt," which is a keyword on the line that actually does the PM operations in the wireless PM script, and found zero results.
 
It would seem that there is some other system involved with power management in 13.04, or that I just don't know what I'm doing, which is a not-uncommon occurrence. Any help anyone can provide or even just a nudge in the right direction would be greatly appreciated!

Some hardware and software details:

Model: Asus U36S
lspci: 03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
iwconfig :
 wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:48:71:19:14   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:207   Missed beacon:0


Wireless module (I think): lsmodcfg80211              510937  3 iwlwifi,mac80211,iwldvm
Kernel: 3.8.0-27-generic x86_64

Thanks again,

        -Julius

---

### Post by chili555 on 2013-08-02
Your post was a bit unclear as to whether you tried the fixes in the blog you linked. Did you change /usr/lib/pm-utils/power.d/wireless as indicated? I think I'd also change two other lines as well:```
  iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=[COLOR="#FF0000"]0[/COLOR]
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power [COLOR="#FF0000"]off[/COLOR]"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power [COLOR="#FF0000"]off[/COLOR]";;


```Did you also try the 11n_disable part?

EDIT: I made these changes on my own system, also using the driver iwlwifi, and when I unplug the AC power, iwconfig remains as:> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:D7:19:41:54:XX  
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:off[/COLOR]
          Link Quality=68/70  Signal level=-42 dBm  
As to whether the connectivity is improved or degraded, I can't comment; I've had no such issues.

---

### Post by icecreamguy on 2013-08-05
Thanks, Chili555 - I definitely appreciate the suggestions. I did try those edits in  /usr/lib/pm-utils/power.d/wireless, as well as /etc/pm/power.d/wireless, they made no difference so I tried removing the scripts entirely, which also had no effect. The additional edits you suggested also haven't made a difference when copying them back to their default locations. If you or anyone else has any ideas I would love to understand how this works. When I completely remove those scripts from both of the PM directories, the setting reported by iwconfig continues to change when I go on and off battery. If those scripts aren't doing it, I don't know what is. Thanks again

                  -Julius

---

