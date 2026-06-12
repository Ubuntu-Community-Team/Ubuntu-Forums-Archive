---
title: "Cisco VPN stopped working after Network Manager upgrade"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by karlhm76 on 2009-02-08
Hi, I upgraded network manager to 0.7 this morning and now my cisco vpn client stopped working.

The errors are:

```

Feb  9 11:39:15 karl-eee NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
Feb  9 11:39:15 karl-eee NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 6739 
Feb  9 11:39:15 karl-eee NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
Feb  9 11:39:15 karl-eee NetworkManager: <info>  VPN plugin state changed: 1 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  VPN plugin state changed: 3 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  VPN connection 'CCVPN' (Connect) reply received. 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  VPN plugin failed: 1 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  VPN plugin state changed: 6 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  VPN plugin state change reason: 0 
Feb  9 11:39:25 karl-eee NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Feb  9 11:39:25 karl-eee NetworkManager: <info>  Policy set 'Auto KarlsInternet' (ath0) as default for routing and DNS. 
Feb  9 11:39:37 karl-eee NetworkManager: <debug> [1234139977.116614] ensure_killed(): waiting for vpn service pid 6739 to exit 
Feb  9 11:39:37 karl-eee NetworkManager: <debug> [1234139977.116773] ensure_killed(): vpn service pid 6739 cleaned up 

```

I have no idea why its not working. I imported the pcf file and last time that's pretty much all it took. I remember I had to use an older version of network-manager-vpnc to fix a group password bug, but this new version doesn't seem to have it.

If I revert back to the older version of network manager it works fine, but I need the new version because of the bluetooth and wireless broadband support.

Does anyone have any ideas why its not working? 

Thanks in advance.

---

### Post by joeldrapper on 2009-02-08
Sorry, I'm no ubuntu expert so can't really help you. Just wanted to say, I've had a few problems after upgrading too [http://ubuntuforums.org/showthread.php?t=1064292](http://ubuntuforums.org/showthread.php?t=1064292)

---

### Post by karlhm76 on 2009-02-10
Anyone? 

I just need to know whether its a bug or its a credentials/setup issue.

If its a setup issue then I can get some limited help from the tech people at work.

Until I can work it out I guess I'll go back to the older version and look for information on how to set up wireless broadband on it.

Thanks in advance.

---

### Post by parepidemos on 2009-02-19
> **karlhm76 said:**
> Anyone? 

I just need to know whether its a bug or its a credentials/setup issue.

If its a setup issue then I can get some limited help from the tech people at work.

Until I can work it out I guess I'll go back to the older version and look for information on how to set up wireless broadband on it.

Thanks in advance.

Not sure if this is it, but I recently switched from Kubuntu to Ubuntu and had a similar problem. I tracked it down to the ike daemon (it was opening UDP port 500) by testing with vpnc from the console. I shut down the daemon and was able to connect just fine.

You can do a quick check to see if anything has port 500 open:

~$ sudo netstat -naup | egrep 500

I'm not yet sure if anything on the system needs ike (kvpnc?) but I went ahead and uninstalled it.

Regards,
parepidemos

---

### Post by inosuke on 2009-11-15
> **parepidemos said:**
> 
I tracked it down to the ike daemon (it was opening UDP port 500) by testing with vpnc from the console. I shut down the daemon and was able to connect just fine.

You can do a quick check to see if anything has port 500 open:

~$ sudo netstat -naup | egrep 500

I'm not yet sure if anything on the system needs ike (kvpnc?) but I went ahead and uninstalled it.

Thanks parepidemos,
Exactly the same was happening to me after upgrading to Karmic. Shutting down the iked has solved the problem.

One thing confused me was command line vpnc, which worked just fine even if iked was running. It simply established another session to another IP (the VPC server was 'multi-homed -- ?!not sure this is correct terminology') which I don't understand why nm plug-in could not do.

---

