---
title: "Share Bluetooth (PANU) internet connection over wired network"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by joebrady on 2011-01-06
I have a wired home network setup with multiple computers connected to a hub and linksys router.  Various Windows and Linux systems.  I can communicate/transfer between all comps.

My main server/media center runs Ubuntu 9.10.  I can connect to my phone via PANU bluetooth and get internet connection on this system.

Is there a way to share this internet connection via LAN to the router so that other systems in the house can use the internet connection?

---

### Post by PatchesTheCaveman on 2011-01-07
I provided instructions on how to enable internet connection sharing in this thread:
[http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454)

---

### Post by joebrady on 2011-01-07
Great.  I will give that thread a read when I get home.  Thank you.  Hopefully I can manage...

---

### Post by joebrady on 2011-01-12
Patches:

Thanks for the link and all the info in that thread.  I followed it step-by-step (running into the same errors as the poster each time) but I successfully have managed to get my phone connected to the Linux computer via bluetooth (PANU/bnepo) and other machines connected to the net via the wired LAN attatched to the switch.    (although I don't seem to be able to see the shares on the linux comp from my windows laptop....)

All I need to do now is get everything automated on start-up.

First I need the computer to auto-connect to one of my two phones (whichever has the BT turned on)  I think I can do that with the following, but I haven't tried yet....

it is necessary to place a config file named
'ifcfg-bnep0' in /etc/sysconfig/network-scripts/ (reportedly for Redhat).

For static addresses, 'ifcfg-bnep0' could look like follows:
    DEVICE=bnep0
    BOOTPROTO=static
    IPADDR=10.0.0.1
    NETMASK=255.0.0.0
    ONBOOT=no

For DHCP, 'ifcfg-bnep0' could look like follows:
    DEVICE=bnep0
    BOOTPROTO=DHCP
    ONBOOT=no


Then I need firestarter to start on boot as well AFTER the network connections have been made.  (without entering ROOT password)  Not preferable, but I can do it this way I believe:

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your */etc/sudoers* file in your favorite text editor and add the following line at the end: 
   [COLOR=#bd3030]username[/COLOR]   ALL= NOPASSWD: /usr/bin/firestarter 
  Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line. 
  Simply replace [COLOR=#bd3030]username[/COLOR] with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command *sudo firestarter*. 
  A note on the security aspects: This method makes a trade off in local security for convenience. If your user account becomes compromised the attacker will be able to control the firewall. However this method is preferable to having a shared root user password in a multiuser setting. It is also preferable if the alternative is not to run Firestarter at all.

---

### Post by PatchesTheCaveman on 2011-01-12
joebrady:  Network configuration in Ubuntu in other Debian-based distros takes place in /etc/network/interfaces, not the location you provided that Red Hat/Fedora uses.  Please note that you **must** uninstall NetworkManager if you are configuring your network connections manually in this file, otherwise they'll step on each others toes.

I'm working on finding good instructions for getting your particular setup working that way.  I'll post back when I find some.

You might find that setting the bluetooth connection to "Connect automatically" might be easier and good enough.  In that case, you might need to start Firestarter on login as you stated above, as I believe it monitors your Internet connection and resets the firewall when it becomes active.

But, you don't actually ever have to start the Firestarter application to get it working.  What's happening is *ufw*, the actual firewall program Firestarter just configures, is starting before the network connections are active.  If you run:
```
sudo service ufw restart
```
once your connection is active that should bring everything online.

If you get everything configured in /etc/network/interfaces, Ubuntu will start your networking before it starts *ufw*, so everything should Just Work.

---

### Post by joebrady on 2011-01-12
Ah, I missed the RedHat part there....:confused:

I haven't seen anywhere to enable "connect automatically" for my PANU/bnep0 connection yet, maybe I just haven't looked in the correct place yet...  When I go to Network Manager and Edit Connections, it is not listed.

I may have to go the /etc/network/interfaces route, as I would like network to connect as soon as possible after boot (helps with my XBMC that autostarts)

I'll look at it again this evening and see what I can come up with, thanks again for your help!

---

### Post by joebrady on 2011-01-13
I've looked everywhere I could think of and I can't find a way to enable AutoConnect for the bnep0 device.  

When I click on the Network Manager icon in the task bar it shows the MAC address for my phone as being Available, but when I got to edit connections, it is not shown.

Maybe adding this would do it?  Not sure about the uuid though....

[INDENT]

~ $ sudo cat /etc/NetworkManager/system-connections/Auto\ bnep0 


[connection]
id=Auto bnep0
uuid=78960c3d-b227-4c7d-8952-b9b051af72cd
type=802-3-ethernet
autoconnect=true
timestamp=0
[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false
[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:1f:e2:fa:b3:10
mtu=0

[/INDENT]

---

### Post by joebrady on 2011-05-25
So I did finally get this all going smoothly (except for autoconnect, which I decided I didn't really need)  

When I connect my phone to the Linix box via BT, Firestarter kicks off and assigns everything connected to my switch an address via DHCP.  Works great, everything gets and internet connection.  

My next step that I'd like to do, which I haven't found any examples of through search (maybe wrong terms) is plug my wireless router into the switch.  That way I could also connect a wireless device to this shared internet connection.  

Possible?  Any hints or suggestions before I try to accomplish this?

---

