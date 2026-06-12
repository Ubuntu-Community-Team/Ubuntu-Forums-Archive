---
title: "RT2500 Success!"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by queenorych on 2006-06-22
Just to help anyone trying to get an RT2500 card to work.

For an unsecured network your /etc/network/interfaces should look like:
auto ra0
iface ra0 inet dhcp
pre-up iwconfig ra0 essid tng
pre-up iwconfig ra0 key off

where tng is my essid.  This is because the rt2500 driver included with dapper defaults to restricted (no open networks allowed).


Notes on the RT2500.

If the dapper rt2500 doesn't work, try a the updated driver rt2500!  Then try rt2x00.  If you have a usb, I think you need the 2570 driver.

The driver included in dapper is an old cvs version.  It does not support smp!  I think the new rt2500 cvs allows for smp, though I haven't verified this.  Wpasupplicant will not work with rt2500!  You must use the wpa support through the rt2500 driver.  Network manager doesn't seem to work.  It may work with wep, since the driver defaults to restricted (see above). 

The new replacement for all rt cards is rt2x00, does support smp.  Although the rt2x00 is still beta, it seems to connect and such.  It also should work with wpasupplicant.

You should use iwconfig to setup the card. iwpriv should only be used for wpa setups.  iwconfig ra0 ap (your access point) should be last.

If you are having trouble setting up the card, make a bash script and use something like:

ifconfig ra0 up
iwconfig essid youressid
sleep 5 #waiting to connect
dhclient ra0

use iwconfig to see if the card is connected to your ap.  It should say something like (note the "Access Point:"):
ra0       RT2500 Wireless  ESSID:"tng"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:90:4B:BE:84:B7
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=83/100  Signal level=-57 dBm  Noise level:-196 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Don't bother with any gui utils.  Especially the gnome network setup as it doesn't work with wpa and other options.  It will just write over your /etc/network/interfaces and slow you down.  I tried to use RaConfig2500, but it always says device is not found.

If you have more issues checkout the rt2500 forums at [http://rt2x00.serialmonkey.com/phpBB2/](http://rt2x00.serialmonkey.com/phpBB2/) and this forum!

Good luck!

---

