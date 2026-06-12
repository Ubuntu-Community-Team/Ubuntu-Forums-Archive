---
title: "Cannot connect to known working OpenVPN server"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by nickfank on 2008-12-28
I have just done a fresh install of 8.10 with the plan to replace windows. It's gone well except for my OpenVPN connection. I have a server at my work that I can connect to reliably via the windows OpenVPN client, but I cannot duplicate it using the Network Manager in Ubuntu.

I tried to "import" the .OVPN file that I used in windows & copied over my static key file. However, when I select the connection in network manager it fils, and in syslog, I see these messages:

[FONT="Courier New"]Dec 28 21:41:55 DiningRoom NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Dec 28 21:41:55 DiningRoom NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 13963 
Dec 28 21:41:55 DiningRoom NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Dec 28 21:41:55 DiningRoom NetworkManager: <info>  VPN plugin state changed: 3 
Dec 28 21:41:55 DiningRoom NetworkManager: <info>  VPN connection 'doxpop-vpn' (Connect) reply received. 
Dec 28 21:41:55 DiningRoom NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'doxpop-vpn' failed to connect: 'Missing required local IP address for static key mode.'. 
Dec 28 21:41:55 DiningRoom NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Dec 28 21:41:55 DiningRoom NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. [/FONT]

So, I tried to edit my OpenVPN connection to set a local IP address, but after saving with [OK], I go back in to edit and the address is gone. 

Thinking it might be a problem with the edit function, I tried to set up a new connection starting with the local IP address in there from the start, and again, it seems to have been deleted when I go back to look.

Any thoughts? Is this a bug or am I missing something about how this should behave? If it is a known bug, is there a workaround? 

Thanks!

---

### Post by kevdog on 2008-12-28
Have you tried anything else other (other client) than the Network Manager client version?

---

### Post by nickfank on 2008-12-29
No, I've only tried doing this through the GUI tool provided by Network Manager, which was installed by default initially and the OpenVPN plug-in for Network Manager, which I added after the initial install.

I tried to locate the client configuration file in the hope that I'd be able to manually transfer all of the required information from the .ovpn file, but I was not able to find anything that looked like what I needed (Perhaps that's why the local address information isn't being saved.) In particular, I did a "find" on client.conf and only found an example file connected to the OpenVPN directories. However, I thought that perhaps Network Manager might store the information elsewhere and then feed it to the client software on the command line in a script.

If you can point me at the location of the correct files, I would feel confident editing or creating them manually instead of using the GUI. I'm a neophyte on OpenVPN and Ubuntu but generally familiar with Linux in the Debian flavor.

I also have su access to the server side if peeking at the conf files there would help. (But since it works nicely for the Win and Mac clients, I'm not eager to change anything on the server side.) The server is a Debian box, so presumably running the same software one would expect on an Ubuntu server but a few versions older.

Sorry about the long post- wanted to let you know what I've already tried & give you a notion of my ability level so we can quickly move past the "power cycle the modem" phase <grin>.

Regards,
     -Nick

---

### Post by bj0 on 2008-12-30
Have you tried just using the standard openvpn client?
```
sudo aptitude install openvpn
```

Then copy your *.conf file and key files to /etc/openvpn (described in more detail on openvpn's quickstart guide)

I am having trouble getting NetworkManager's openvpn plugin to work, but using the standard openvpn client works fine for me.

---

### Post by nickfank on 2008-12-30
Thanks for the suggestion. I'll give that a try. It may be a couple of days before I come back and post the results, as the computer is dead at the moment. I hope it's just a power supply and I'll be back quickly.

Regards,
      -Nick

---

### Post by nickfank on 2009-01-01
OK, Here's what worked for me:

Our admin guru on the office server end assigned me a static IP address, since our reading indicated that the dhcp option might not work once I got onto linux.

I followed bjO's suggestion & installed the regular openvpn package using "sudo aptitude install openvpn".

Then I copied my nickf.key and nickf.ovpn files from the windows box to /etc/openvpn.

I renamed the nickf.ovpn file to nickf.conf and edited a couple of lines: 

I commented out the "tap-sleep 1" line. It's a windows-only option.

I added "ifconfig nnn.nnn.nnn.nnn 255.255.255.0" as the last line (where the nnn's are the ip address our admin guy gave me in step 1).

Then I started openvpn (my PWD was /etc/openvpn): openvpn ./nickf.conf

an "ifconfig" in another terminal window confirmed that I had acquired a new network interface with the expected IP address, and I able to use servers inside the firewall, so I'm done.

Next, I want to make it a bit more automated so I don't have to leave the terminal window idling, but I don't expect that will be a challenge.

Thanks bjO for pointing me at what I needed, and kevdog for confirming that I needed to look beyond the network manager plug-in.

So... Problem solved. Can one of the old hands on this forum give me some pointers on how I should report the Network Manager plugin problem back upstream to the maintainers or developers?

Thanks
   -Nick

---

