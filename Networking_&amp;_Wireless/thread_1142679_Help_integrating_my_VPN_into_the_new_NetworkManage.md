---
title: "Help integrating my VPN into the new NetworkManager VPN option..."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by TMcKSmith on 2009-04-29
I just installed Jaunty, and so far I love it!  I was hoping to get some help with the fancy new "VPN" GUI option in the NetworkManager.  I have the gds-cisco-vpn-client package installed.  Currently, I connect to my VPN via the command line like so:

tmcksmith@server:~$ vpnclient connect XXX

How can I integrate this into said GUI in the NetworkManager so I can connect with a few clicks rather than using the command line?  

Any help would be appreciated.

---

### Post by Kobalt on 2009-04-29
The one thing I did to connect to a Cisco VPN was to install the network-manager-vpnc package. After that, by clicking on the network-manager icon in the notification area I had a VPN Connection option at the very bottom of the drop-down menu.

---

### Post by TMcKSmith on 2009-04-29
> **Kobalt said:**
> The one thing I did to connect to a Cisco VPN was to install the network-manager-vpnc package. After that, by clicking on the network-manager icon in the notification area I had a VPN Connection option at the very bottom of the drop-down menu.

It appears I already have this option in the drop-down-menu, I just don't know how to configure it...

When I select "Configure VPN..." it brings me to a screen with a "VPN" tab but all of the buttons (including "Add") are disabled.

---

### Post by Kobalt on 2009-04-29
Did you install the *network-manager-vpnc* package?

---

### Post by TMcKSmith on 2009-04-29
> **Kobalt said:**
> Did you install the *network-manager-vpnc* package?

ahh, sorry, you're right.  I just installed it.  Now I have the option to "Add" or "Import".  Which should I choose?  I'm assuming "Import"...but what am I actually importing here?

Thanks again.

---

### Post by Kobalt on 2009-04-30
Import can be used if you have a ***.conf file for your VPN connection, maybe used by your VPN client on Windows for example... 
Otherwise, if you know the details of your VPN connection, you just need to go through "Add" and enter them manually.

---

### Post by TMcKSmith on 2009-04-30
I have a ***.pcf file.  Is that the same thing?  When I try to "Import" that, it says:

The file '.' could not be read or does not contain recognized VPN connection information

Error: does not look like a Cisco Compatible VPN (vpnc) VPN connection (parse failed).

---

### Post by version7x on 2009-05-01
> **TMcKSmith said:**
> I have a ***.pcf file.  Is that the same thing?  When I try to "Import" that, it says:

The file '.' could not be read or does not contain recognized VPN connection information

Error: does not look like a Cisco Compatible VPN (vpnc) VPN connection (parse failed).

You can try the pcf2vpn script to view the contents of the pcf file.

I believe its located in the /usr/share/vpnc/ directory.  It will dump the .pcf to text or to a conf file if needed...

/usr/share/vpnc/pcf2vpnc mycisco.pcf > vpnc.conf

---

### Post by rfurno on 2009-05-02
> **Kobalt said:**
> The one thing I did to connect to a Cisco VPN was to install the network-manager-vpnc package. After that, by clicking on the network-manager icon in the notification area I had a VPN Connection option at the very bottom of the drop-down menu.

That did it for me. Thanks.

---

### Post by raequin on 2009-05-06
> Did you install the network-manager-vpnc package?

How does one do this?  I tried via synaptic package manager but the search for "network-manager-vpnc" returned nothing.  Both packages resulting from a search for "network-manager" were already installed.

Thanks.

---

### Post by sirctseb on 2009-09-30
I had this problem and the following solved it:
In your .pcf file, check that the Description field under [main] has a value.

I found this on the Network Manager mailing list: [http://mail.gnome.org/archives/networkmanager-list/2009-September/msg00056.html]("http://mail.gnome.org/archives/networkmanager-list/2009-September/msg00056.html")

I checked my file and it read
[main]
Description=
Host=xxx.xxx.xxx.xxx
...

and I changed it to
[main]
Description=description here
Host=xxx.xxx.xxx.xxx
...

and was then able to import the file

---

### Post by 2010fan on 2009-10-16
> **sirctseb said:**
> I had this problem and the following solved it:
In your .pcf file, check that the Description field under [main] has a value.

I found this on the Network Manager mailing list: [http://mail.gnome.org/archives/networkmanager-list/2009-September/msg00056.html](http://mail.gnome.org/archives/networkmanager-list/2009-September/msg00056.html)

I checked my file and it read
[main]
Description=
Host=xxx.xxx.xxx.xxx
...

and I changed it to
[main]
Description=description here
Host=xxx.xxx.xxx.xxx
...

and was then able to import the file

Thanks. This fixed pcf import for me. Silly error.

---

