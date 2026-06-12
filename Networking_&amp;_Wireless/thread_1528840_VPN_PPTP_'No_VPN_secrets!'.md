---
title: "VPN PPTP 'No VPN secrets!'"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by newbiefly on 2010-07-11
tried this:
[http://ubuntu-chronicles.blogspot.com/2009/12/karmic-vpn-itshiddencom.html]("http://ubuntu-chronicles.blogspot.com/2009/12/karmic-vpn-itshiddencom.html")

and this [http://linux.dipin.info/2010/02/howto-vpn-connection-setup-on-ubuntu.html]("http://linux.dipin.info/2010/02/howto-vpn-connection-setup-on-ubuntu.html")

and this:

[http://ubuntuforums.org/showpost.php?p=8261958&postcount=6]("http://ubuntuforums.org/showpost.php?p=8261958&postcount=6")

and my syslogs still lookin like this:
```
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2015
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  VPN plugin state changed: 1
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  VPN plugin state changed: 3
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  VPN connection 'its hidden' (Connect) reply received.
Jul 11 08:58:09 fly-laptop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'its hidden' failed to connect: 'No VPN secrets!'.
Jul 11 08:58:09 fly-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jul 11 08:58:09 fly-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 11 08:58:21 fly-laptop NetworkManager: <debug> [1278856701.002440] ensure_killed(): waiting for vpn service pid 2015 to exit
Jul 11 08:58:21 fly-laptop NetworkManager: <debug> [1278856701.002531] ensure_killed(): vpn service pid 2015 cleaned up
```

seems to be a lot of other unsolved threads with same issue using VPN PPTP GETTING THE SAME ERRORS.  whats up with that?

---

### Post by bogusstrawman on 2011-06-25
Just in case others stumble on this and still don't know what "No VPN secrets" means - it means there is no password. I had this problem with Ubuntu 11 - if you are using network manager and tick the "available to all users" it won't save your password (and without telling you it won't save it).

Also, after you have edited the VPN settings you have to disconnect from the network and then reconnect to be able to use the VPN - again, it doesn't say you have to do this.

Very frustrating.

---

### Post by MartinusEx on 2011-06-25
I installed openvpn client on one of my machines and got the same message.

In a thread i found earlier today on this it says to switch to 
"TLS certificate and password security " and enter a nonsense user name and pwd in the appearing fields.

It did not work for me but you might give it a try.

I still use terminal to start the openvpn client with root privileges.
This works fine.

rgds

Martin

---

### Post by newbiefly on 2011-07-22
[http://ubuntuforums.org/showthread.php?t=91249&page=22](http://ubuntuforums.org/showthread.php?t=91249&page=22)
mgmiller wrote:

You need to install 2 packages:
network-manager-pptp
pptp-linux
If you do the first, it will install the second as a dependency. 

Reboot the computer. (This is important, don't skip this step)

Open Network Configuration (System, Preferences, Network Configuration).
Highlight your VPN connection, hit Edit.

At IPv4 Settings Tab: choose method Automatic (VPN).

At VPN Tab:
1 - input the IP address of the target computer in the gateway field.
2 - input your user name. Leave all else blank, unless you are tunneling to a domain, then enter the domain name where indicated.
3 - hit Advanced button.

At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2. Uncheck all others.

At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.

At Echo: check Allow PPP echo packets.
Leave all else blank. Hit OK, OK to save and get out.

Log off (also important, don't skip this step)
Log on

Note: Your password is requested on VPN startup. You can add it to the default keyring if you want, or leave it out for a little more security.

Once the vpn is open, you can remote desktop over it by entering the nat address of the machine on the other side.
To browse, now the browse network gui may work, you may need to manually enter the IP of the remote machine (eg. 10.0.0.5) in the top. You may need to click reload a few times.
Or if you saved it as a bookmark, select it and you may again have to click reload a few times.

You may need to enter gvfs-mount smb://url example: gvfs-mount smb://10.0.0.5, although, I found clicking reload a few times above seems to work well.

In fact, since 9.04, clicking reload was not needed at all. The clicking reload bit was needed in Intrepid (8.04), which is what these instructions were originally written for.

---

