---
title: "vpnc freezes after short time"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by InFro on 2010-08-11
Hello,

I am in a need to use Cisco VPN.
I installed network-manager-vpnc, configured cisco vpn through NetworkManager. It works slow, but the bigger problem is that after minute or so the connection just freezes.
Then I tried kvpnc. It works like it should from speed point of view. But it also hangs up after minute or two.

Tried to change MTU of my wired connection to 1500 - no good.

Tried to uncomment line in /etc/ppp/options "mru 542" - no good.

Created /var/run/vpnc because it was giving some error "can't open pidfile /var/run/vpnc/pid for writing".

From logs everything seems fine except for "nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1." in last line. If I use kvpnc it gives no errors.

SO, how do I debug this thing or does anyone knows something I don't in this case?
Could it be my router's fault?

Thanks.

--
Ubuntu 10.04 x64, 2.6.32-24-generic

---

### Post by cashy on 2010-08-27
Hi,

Maybe you have the same problem as mine.

Check: [http://ubuntuforums.org/showthread.php?t=1558914&highlight=vpnc](http://ubuntuforums.org/showthread.php?t=1558914&highlight=vpnc)

cashy

---

### Post by dcheng on 2010-10-12
I don't know if I have the same issue, but I thought I'd ask here as well.

I'm running 10.04 off of a USB flash drive on a Dell Lattitude D610.  For an older machine with a failed HDD, this seems to work well, and I don't have too many issues.  However, one of the main things I had hoped to use this machine for was to be able to VPN into my work and use RDP to do some work from home.  This works great for anywhere from 20 minutes to an hour or so.  Then it just stops working.

If I log out from the VPN, my network connection still works (my work does not allow split tunneling, so I have not been able to test that while the VPN connection is up), and I can access public Internet resources.  If I try to log back into the VPN, though, I still cannot access anything.  I authenticate fine, and vpnc says that I'm connected, but I can't ping anything, DNS lookups fail, and obviously, no RDP by IP address or DNS.  It takes a reboot of the machine to be able to re-establish a VPN connection.  The particular profile that I'm using has no problems on either Windows or OS X machines, and I'm able to remain connected for 24 hours or longer.

Tonight, I just left the VPN connection up and just sent pings across the network.  The pings stopped after about an hour (maybe 85 seconds short of an hour), and that seems to have been the longest that I've remained connected.  No error messages in /var/log/syslog, though I do see the connection being established, and I also get the "can't open pidfile" message in the GP; however, that was as the connection was being established.  Is there someplace else that I should look for error messages?

Also, earlier today, I turned on the computer and puttered around for about 20 minutes before I attempted to establish the VPN connection.  The connection came up, but I was unable to do anything, similar to the timeouts I have experienced.  I'm not sure if that's related in any way, other than the fact that when I exited the VPN connection, my normal network access had no problems and I was able to connect and work after a reboot.

As I mentioned earlier, I can re-connect and work only after a reboot.  I'd like to troubleshoot this further, but I don't know where else to look for messages.  I did look at some of the other threads, and I have verified that the MTU is reasonable (1500 bytes on the wired or wireless connection and 1412 on the tunnel).  I did not play with the /etc/ppp/options file because that appears to be related to a PPP connection, not an IPSEC connection, and this particular type of timeout did not seem to be related.

Any direction that can be provided would be appreciated.

---

### Post by rock4christ on 2010-10-12
I might be having a similar problem. Vpnc says it connects fine, but can't access anything.

---

### Post by InFro on 2010-10-18
Soooo, finaly I have Ubuntu 10.10 on my laptop. I thought maybe everything will magically work now. But sadly no go....

Problem stays the same: I connect (using kvpnc), connection works perfectly for 10 seconds or so, and then stops saying "
debug: "ping_check.sh" started.
[COLOR="Red"]error: Ping to xxx.xxx.xxx.xxx within 4 checks every 0s has failed.[/COLOR]
".
Tried to google the error message, but with no luck.
Anyhow, doesnt ping check **every 0s** look strange?

---

### Post by dgomon on 2011-02-18
Hi.
If still interested.
I have had same issue (but not problem) and i found some properties in [COLOR="Navy"]Settings :: Profile :: Network :: General[/COLOR].  In the group **Connection Status Check**,  the **Check Connection Status** property is switched on, but **Ping hostname/IP address** is not set and **interval** is set to **0** (zero).
Two ways can resolves this issue:  **switch off** the **Check Connection Status** property or specify **correct IP for ping and reasonable value for interval**.

I hope this helps you.

*Sorry for my english.*

---

### Post by babsjr77 on 2012-02-27
Check your route with "route -n". vpnc was adding a route which caused me problems. VPN connection would work for only about 30 seconds.

I had a route for 192.168.0.0 on both eth0 and tun0. Doing a "route del 192.168.0.0 dev tun0' after connecting to vpnc fixed the problem.

---

