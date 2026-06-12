---
title: "Lousy computer name recognition"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by mås on 2009-05-07
Hi,
I've a problem of computer name recognition - well I think so. Ubuntu 8.04 LTS 64 bit.  
Let's say the computer name is seagull.
D-Link router DIR-100 is connected to WAN and the LAN and should work as a DNS server and also an DHCP server for the LAN.
WAN is working quite well, but when I shall configure LAN in the router, I can't find the computer name of this ubuntu machine in the scrollbox (but I find a connected windows machine).
I've enabled "roaming" for the network, but I have tried other approaches too (DHCP and Static).
The computer name don't seem to be fully recognized.  I say fully, because when I ping seagull I get the address, ok from terminal but very slow from Network Tools Ping.  
Samba is running, but of cause not working.
And the connection to my DynDns test area isen't working either.
This last thing was working before, but after the old router resigned I can't get this things to work with the new one.
:confused:It seems to me that somthing quite basic is wrong, but what???
Please give me som clues!
/Lars

---

### Post by Iowan on 2009-05-07
No guarantees, but try editing **/etc/dhcp3/dhclient.conf**. Edit the line similar to:```
send host-name "mycomputername";

```

---

### Post by mås on 2009-05-08
> **Iowan said:**
> No guarantees, but try editing **/etc/dhcp3/dhclient.conf**. Edit the line similar to:```
send host-name "mycomputername";

```
Thank you Iowan, I tried that but with no progress.
When I restarted the network, I got this message:
 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
:confused:Doesn't sound good, does it?  May be someone got an idea?

Excuse me, Iowan, I wasn't rigorous enough when testing your suggestion.  As long as I had the "roaming" network option, your suggestion didn't work, but when I choose the DHCP approach, it did work; well I got an understandable OK when restarting the network, and I could reach my dyndns test area, but the LAN still do not work.
I'll test some modifications and will get back and report the results in a day or so.
In the meanwhile, thank you, and have a nice Icehocky evening!
/Lars

---

### Post by mås on 2009-05-12
The WAN seems to be ok.
So the question now has become "how to get samba work"?!
I can't get full samba connections in the LAN not even a good connection with the serving computer itself.
When I run 
  ~$ smbclient //MY_COMPUTERNAME/MY_ACCOUNTNAME
I got the message (after the password):
  Domain=[MY_COMPUTERNAME] OS=[Unix] Server=[Samba 3.0.28a]
  **tree connect failed: NT_STATUS_BAD_NETWORK_NAME**

On the other hand I get:
~$ smbclient -L MY_COMPUTERNAME
Password: 
```
Domain=[MY_COMPUTERNAME] OS=[Unix] Server=[Samba 3.0.28a]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    Sambafiler      Disk      SAMBA Lagerplats
    IPC$            IPC       IPC Service (MY_COMPUTERNAME server (Samba, MY_COMPUTERNAME))
    PDF             Printer   PDF
    Kyocera-FS-10102 Printer   Kyocera Mita FS-1010
    samba           Disk      Just user accounts
Domain=[MY_COMPUTERNAME] OS=[Unix] Server=[Samba 3.0.28a]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
    MY_WORKGROUP         MY_COMPUTERNAME
```

Please give me some guidelines to make samba work!
Regards/Lars

---

### Post by Iowan on 2009-05-12
I Googled the error. What I found suggests bad sharename. I found the question posed many times - but didn't find answers posted...

---

### Post by cariboo on 2009-05-12
Have you setup your samba password?

```
sudo smbpasswd -L -a <username>
```

to add the passwd, and

```
sudo smbpasswd -L -e <username>
```

to enable the account.

---

### Post by mås on 2009-05-13
Thanks for the suggestions!
Yes that's already done.

---

### Post by mås on 2009-05-13
Thanks Iowan!
I've experiensed the same thing googling - many articulations but no solutions, somewhat frustating!

---

