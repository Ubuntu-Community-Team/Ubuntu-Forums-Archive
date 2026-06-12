---
title: "OpenVPN No Secrets error when connecting."
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by T3kG33k on 2009-11-05
So here we are again, back on the rain slick precipice of darkness.  The upgrade from 9.04 to 9.10 went beautifully.  There wasn't a single hickup or error message indicating that anything could be wrong.  But not everything was right.
OpenVPN and VPN my friends appears to have taken another dive and this time it appears to be a different issue than in 9.04, which was a different issue than in 8.10.
Now, I've been searching the Ubuntu Forums, Launch Pad, and the rest of the internet since 11-2-09 and still I haven't found anything definate as a solution to the issue that others as well as myself are seeing.](*,)
With the type of quality build that one would see come from the people at Canonical you would expect a fix for this issue to come about and be implemented and hold fast through the releases but no.  It appears that things here do not work this way.

Now that I've blown off the necessary steam lets get down to business and get this puppy rolling!
Basically what I believe this issue is coming down to is the encryption keyring.  This is coming from the error in the system log stating:
[SIZE="1"]
5 15:47:00 t3kg33k-top NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Nov  5 15:47:00 t3kg33k-top NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 1581
Nov  5 15:47:00 t3kg33k-top NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Nov  5 15:47:00 t3kg33k-top NetworkManager: <info>  VPN plugin state changed: 3
Nov  5 15:47:00 t3kg33k-top NetworkManager: <info>  VPN connection 'HomeConnection1' (Connect) reply received.
Nov  5 15:47:00 t3kg33k-top NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'HomeConnection1' failed to connect: 'No VPN secrets!'.
Nov  5 15:47:00 t3kg33k-top NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov  5 15:47:00 t3kg33k-top NetworkManager: <info>  Policy set 'Auto ASMGUEST' (eth1) as default for routing and DNS.
Nov  5 15:47:13 t3kg33k-top NetworkManager: <debug> [1257457633.003092] ensure_killed(): waiting for vpn service pid 1581 to exit
Nov  5 15:47:13 t3kg33k-top NetworkManager: <debug> [1257457633.003667] ensure_killed(): vpn service pid 1581 cleaned up[/SIZE]

I know that some users have been running VPN from the CLI and I applaud their ability but there is a GUI for a reason and it should work as such! 
So what's the deal?  I've updated everything and still no joy.  Ive performed complete removals of the network manager application and related and still nothing.  OpenVPN has be completely removed and the connection profile has been recreated several times.  Reboots? I've performed a ton and full powe rcycles also.  So where am I going wrong here?
Everything worked beautifully in 9.04?

EDIT:
I don't what the hell happened but it just started working on its own!  After fighting with this for almost four days I just tried it and it connected! WTF!?
PS
I apologize for the damage caused to virgin eyes.

---

### Post by T3kG33k on 2009-11-06
Nevermind.  Everything is back to "normal"

---

### Post by T3kG33k on 2009-11-07
All is well now that I've downgraded back to 9.04.  I ran sudo apt-get install network-manager-openvpn and rebuilt my profile after a reboot.

---

### Post by slcpunk on 2009-11-18
> **T3kG33k said:**
> All is well now that I've downgraded back to 9.04.  I ran sudo apt-get install network-manager-openvpn and rebuilt my profile after a reboot.

For what its worth - I am seeing the same problems.  However its just a network manager issue, so if you can live with another way of managing the VPN, there is no need to go back to 9.04

I have used gopenvpn and it works quite well.  The only issue is that it prompts me for the admin password ( although the documentation says it shouldn't ).  

Anyway, hope that might help in the interim.

---

