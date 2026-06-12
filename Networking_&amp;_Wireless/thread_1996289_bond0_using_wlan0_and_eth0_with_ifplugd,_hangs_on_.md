---
title: "bond0 using wlan0 and eth0 with ifplugd, hangs on system shutdown"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by leo_m on 2012-06-04
I have bonded wireless and ethernet together in fallback mode, so that only one IP address is used for both (so my port-forwards from router to a given IP address continue to work irrespective of which I am connected via).  Additionally, I have used ifplugd on wlan0 and eth0 (which are bonded using bond0) so that automatic ifup/down is carried out on these interfaces.  I am using Ubuntu 12.04 64-bit and a USB wireless dongle as my wlan0 interface.  The modules r8712u and r8169 are loaded (I do not know which one pertains to my wlan0, I guess it is r8712u).  I am also using libvirt bridges (virbr0: NAT and virbr1: routed) to run two VMs on this machine; these libvirt interfaces are brought up at boot time (using libvirtd); I am using proxy arp to be able to connect my VMs to wireless LAN (enabled ipv4 forwarding and bond0 proxy arp via sysctl).

But this gives me a system where the computer becomes unresponsive for hours while shutting down (so a hard-power off needs to be done) *if I browse internet* in a session.  If I do not browse internet, there is no problem during shutdown.

My /etc/network/interfaces  is as follows:
```
auto lo
iface lo inet loopback

# ===================
# PHYSICAL DEVICES
# ===================

# ===================
# eth0 config
# ===================

## Not using 'auto eth0' because am using ifplugd to issue the ifup command once physical link is active.
## I want to assign the IP address only if the link is
## ...actually connected, so am using ifplugd to assign the IP address and set route via ifup, based on 
## ...actual connection to the ethernet port. ifup uses configuration in this file.
## Zeroconf can add a 169.x.x.x route when the device is configured using static mode instead of manual mode, 
## ...but that should not cause any major problems ('ip route show').
## To avoid addition of the route by zeroconf, either set zeroconf config appropriately or use manual
## ...method instead of static method in interface config below.
#iface eth0 inet static
#    address 192.168.1.32
#    network 192.168.1.0
#    netmask 255.255.255.0
#    broadcast 192.168.1.255
#    gateway 192.168.1.254
#    dns-nameservers 192.168.1.254


# Manual mode because this device is part of a bonding interface
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth0
iface eth0 inet manual
    bond-master bond0
    bond-primary eth0 wlan0


# ===================
# wlan0 config
# ===================

# auto wlan0 needed because I want to be able to run wpa_supplicant at boot, 
# ...contrast with eth0 where I do not have to
# ...run anything special at boot, so eth0 is ready to be managed by ifplugd
auto wlan0

## ifconfig cannot set wireless adapters up, (cannot associate with AP): the equivalent is to use some
## ...program to set up the connection maually, e.g., iwconfig, wpa_cli (text based interface to wpa_supplicant)
## ...or wpa_supplicant (directly, not via a frontend program).
## iwconfig notes:
## According to /etc/network/if-pre-up.d/wireless-tools, different drivers expect configuration 
## ...to be done at different times, some at 'pre-up', some at 'up'/'post-up' and some a mix of the two
## ...(/etc/network/if-pre-up.d/wireless-tools is referenced from 'man wireless').
## ...The lines with 'wireless-' prefixed are executed after the adapter is brought up, so may not work with
## ...all the drivers (from /usr/share/doc/wireless-tools/README.Debian, referenced from 'man wireless').
## ...These lines (the ones prefixed with wireless-) are used by wireless-tools (iwconfig family).
## wpa_supplicant notes:
## Lines prefixed, on the other hand, with 'wpa-' are used to configure device using wpa_supplicant.
## Network Manager is able to handle wireless very well, but brings the interface up properly *after* the
## ...user logs in, so is of limited use in that sense (I intend to set up remote access prior to login, so
## ...that I do not have to login locally at the machine after a restart/boot-up).  Although Network Manager
## ...supports 'system' and 'user' config types, with 'system' config type being used to bring interfaces up
## ...before login probably, I want to keep Network Manager totally separate and independent of this file and 
## ...primarily for use in 'user' mode.
## If the association with AP has occurred (e.g., through the use of wpa_supplicant), then the link beat 
## ...is detected by ifplugd which then executes ifup wlan0.
## ifup wlan0 will not assign any IP addresses or gateways to wlan0 if the interface is set to manual
## ...instead of static.  
## If the interface is set to static, then it is automatically assigned, via zeroconf,
## ...an IP route like 169.254.0.0/16 metric 1000 although I do not include this in my static configuration.
## To allow automatic run of wpa_supplicant at 
## ...boot time, I need to set iface to be configured at boot using auto wlan0, but since I do not want any config
## ...to be done at boot, I 'should ideally' set the method to manual instead of static.
## ...If I don't use auto wlan0, wpa_supplicant won't run, there will be no association with the AP and hence
## ...ifplugd won't detect a link
## ...beat.  This is chicken-and-egg situation 'cos I am running wpa_supplicant in pre-up, not in sys init.
## ...[pre-up-->wpa_supplicant-->association with AP-->link beat detected by ifplugd-->ifup called-->pre-up called]
## ...So, the question is how to run wpa_supplicant at boot time but not configure the interface at all and
## ...configure it later using ifup via ifplugd.  I do not want to use wpa_action as I do not want two managers
## ...(wpa_action and ifplugd) to manage the wlan0 link.  I prefer using ifplugd because it can also allow to 
## ...automatically prefer eth0 over wlan0 whenever connected, which wpa_action won't: wpa_action is good only
## ...to handle roaming in wlan0 (disconnections and reconnections on wlan), but not across eth and wlan.
## ...The id_str mechanism in wpa_supplicant.conf is used by wpa_action in conjunction with config in this file.
## ...I have not provided that config as this computer is not meant to roam.
## ...See also /usr/share/doc/wpa_supplicant/README.modes.gz

## static because I do not want to write scripts to configure it in manual mode and I do not want to use
## ...wpa_action (wpa_action 
## ...can use logical interfacing config via id_str mechanism to move static config to a different iface stanza,
## ...keeping this stanza as 'iface wlan0 inet manual', but then ifplugd can clash with, so to say, wpa_action
## ...as both can attempt to bring the interface down when it is deactivated).  The downside of using static is
## ...that there is a zeroconf invalid route now plus ifplugd will attempt an ifup anyway, but that will exit
## ...immediately as the interface is already configured
#iface wlan0 inet static
#        address 192.168.1.33
#        network 192.168.1.0
#        netmask 255.255.255.0
#        broadcast 192.168.1.255
#        gateway 192.168.1.254
#    dns-nameservers 192.168.1.254
# ------------------- iwconfig section begin
#    # If you want to use wireless-tools package to manage the wireless device, uncomment the following:
#    #pre-up iwconfig wlan0 essid any mode Managed channel <channel-here> ap <AP ID here> rate auto key <wpa2 key here>
#    #wireless-channel <channel-here>
#    #wireless-ap <AP ID here>
#        #wireless-key <wpa2 key here>
#        #wireless-mode managed
# ------------------- iwconfig section end
# ------------------- wpa_supplicant section begin
#    # If you want to use wpa_supplicant package to manage the wireless device, uncomment the following:
#    #pre-up /sbin/wpa_supplicant -c/etc/wireless_supplicant.conf -Dwext -iwlan0 -B 
#    #     OR
#    #pre-up /sbin/wpa_cli -iwlan0 reconfigure #won't work as it assumes wpa_supplicant to be running
#    # If any wpa- option/s specified below, then wpa_supplicant and wpa_cli are automatically started
#    # ...and killed as appropriate by wpa_supplicant scripts in /etc/network/if-<event>.d/ dirs
#    # ...If using a custom path to the config file, should use a wpa-conf option for the same
#    # If the following lines with wpa- prefixes are uncommented, then do not run wpa_supplicant via pre-up
#    # ...above
#    wpa-driver wext
#    wpa-conf /etc/wireless_supplicant.conf
#    # wpa-roam is supposed to be used by wpa_action using a new logical interface stanza and this iface stanza
#    # ...should use manual mode in such a case (iface wlan0 inet manual): see 'man wpa_action' and
#    # ...refer wpa_supplicant script/s in /etc/network/if-<event>.d/ dirs
#    # Uncomment line below if you want to use roaming/wpa_action, comment out wpa-conf line above in that case
#       #wpa-roam /etc/wireless_supplicant.conf
#    # If you are bringing wpa_supplicant up via pre-up, you need to bring it down yourself as well, so
#    # ...uncomment the line below.  If you do not do that, then due to pre-up, ifplugd will attempt to
#    # ...start another instance of wpa_supplicant upon disconnect/reconnect which is not good 
#    # ...(and will fail but may result in instability).  
#    # ...I prefer using the pre-written scripts in /etc/network/if-<event>.d/ dirs to
#    # ...bring wpa_supplicant and wpa_cli up/down automatically
#    #pre-down /sbin/wpa_cli -iwlan0 terminate
# ------------------- wpa_supplicant section end

# Manual mode because this device is part of a bonding interface
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 wlan0
iface wlan0 inet manual
    wpa-driver wext
    wpa-conf /etc/wireless_supplicant.conf
    bond-master bond0
    bond-primary eth0 wlan0



# ===================
# VIRTUAL DEVICES
# ===================
auto bond0
iface bond0 inet static
    # LACP confuration - verified working for 12.04
    #bond-mode 802.3ad
    #ifplugd ensures only one physical device is active at a time
    #...our network data-rate is much less than the individual device data-rate,
    #...so no point in trying to send traffic on more than one device
    bond-mode active-backup 
    bond-miimon 100
    bond-lacp-rate 1
    bond-slaves none
    bond-primary eth0 wlan0
        address 192.168.1.34
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
    dns-nameservers 192.168.1.254
# From https://help.ubuntu.com/community/UbuntuBonding:
# 'slaves' may not work in Ubuntu 10.04+ so it is better to use 'bond-master' in eth0 section
# ...and 'bond-slaves none' so the bonding interface comes up quickly. 
# see also: http://ubuntuforums.org/showthread.php?t=1876061

```What can I do to resolve the computer becoming unresponsive while shutting down?

---

### Post by leo_m on 2012-06-13
Is it useless to have both bond0 and ifplugd running simultaneously since, in the configuration above, both end up doing the same thing anyway.  Could having both be the reason for the instability at shutdown?  I shall try removing ifplugd in that case and then see if it makes a difference. 

Should I also have used the -b bond0 parameter while invoking wpa_supplicant?  Does bonding interface (bond0) not use the underlying (slave) interface's MAC address while bringing that interface up (specifically, when authenticating wlan0 with wireless AP), when bonding is configured for fallback mode?

From: [http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/nic-bonding-between-eth0-and-wifi-678669/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/nic-bonding-between-eth0-and-wifi-678669/)

---

### Post by leo_m on 2012-06-21
Update: Since switching to Ubuntu Studio, I no longer have the problem of unstable (frozen) shutdowns: well, either switching to Ubuntu Studio OR not using ifplugd anymore did that.

---

