---
title: "Wireless works via CLI, NetMan won't manage it"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by smiley505 on 2009-07-02
I was attempting to configure my new Linksys WRT54GL as a Wireless Bridge (as a first step to making it a Repeater Bridge).  It seems as though I messed up the Network Manager while trying to set my /etc/network/interfaces file for a static IP.  Not sure how...but there it is.

As it is now, I can connect to my wireless network via the command line.  So that's good.  But, it's really not a user-friendly thing to have to use the CLI every time.  I can also plug in my ethernet cord and connect to the router that way.

Here's the kicker.  When connecting via ethernet, the Network Manager recognizes and automatically connects to the router.  The wireless will not.  When you hover over the icon, it says that for Wireless Networks, the error message is 'device not managed'.  Wired Network says 'disconnected' and it shows the 'auto eth0' message when connected via ethernet cord.

Ideas?

root@HPMini:/# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:"linksys-n"  Nickname: ""
          Mode:Managed  Frequency:2.437 GHz  Access Point:  00:21:29:DE:97:AA
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=2/5  Signal level=-77 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:237  Invalid misc:0  Missed beacon:0

pan0      no wireless extensions



I have an HP Mini 1120NR running Ubuntu UNR 9.04 (Kernel 2.6.28-13-generic, Ubuntu 4.3.3-5ubuntu4).

Any and all help would be GREATLY appreciated!!!

KDW

---

### Post by kerry_s on 2009-07-02
you can use either /etc/network/interfaces or network manager, but you can't use both. 
/etc/network/interfaces overrides network manager.

to fix just remove what ever you put in /etc/network/interfaces.

---

### Post by smiley505 on 2009-07-02
Yeah...since that is what I initially changed in order to set my static IP, that's the first thing I tried to set back to the way it was before I did anything.

I just now double-checked and there were two lines for eth0 that weren't there a minute ago.

I deleted them, saved, and rebooted.  And SHAZAM!

Could have sworn I reverted the file back to just the lo interface, but I guess not.

Thanks so much!!!!!

KDW

---

### Post by smiley505 on 2009-07-03
OK.  Now, I've rebooted a couple of times.  Now the ethernet connection is gone.  eth1 is not shown on ifconfig.  But the device IS listed in lspci.

I've rebooted a couple of times since finding this problem.  Doesn't fix it.  And I've checked /etc/network/interfaces each time.  The only lines in it are what was there originaly:
auto lo
iface lo inet loopback


Help?

KDW

---

