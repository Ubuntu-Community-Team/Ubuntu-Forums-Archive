---
title: "Samba service not starting at boot"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by banquet on 2009-10-13
I am running Ubuntu 9.04 and am having trouble with samba starting at system boot.
The system is used as a file server for music and movies that i want everyone on the network to have access to without the need for a password, most of these computers are running Windows.
This is achieved using samba shares. However the samba service does not start properly on system boot. Each time I reboot I have to manually 
sudo /etc/init.d/samba start OR restart
After this everything works fine until the next reboot. Because of this I believe that there are no problems with my smb.conf
I believe the problem has something to do with the system's IP address being assigned by DHCP running on my router. The problem started occuring after I changed from a static IP to DHCP. I would like to keep it on DHCP. Does anyone know how to slove this problem? A temporary fix would be to restart samba 30 seconds after boot. How would it be possile to do this? 

Steps I have taken so far to try and solve this problem are:


To ensure samba services are set to run at boot

```
sudo update-rc.d -f samba remove
sudo  update-rc.d samba defaults

```Also under System->Administration->Service Sabma is ticked

After boot I cannot access the samba shares on other computers on the network.
Checking the samba status gives

```
sudo /etc/init.d/samba status
 * nmbd is not running
 * smbd is not running
```After restarting samba I am then able to access the shares.


```
sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                                  
start-stop-daemon: warning: failed to kill 2990: No such process
                                                                                    [ OK ]
 * Starting Samba daemons                                                           [ OK ]
``````
sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running
```

---

### Post by Boondoklife on 2009-10-13
can you post your smb.conf just to make sure you dont have anything there that can cause an issue. Also try to disconnect your connection and start samba see if it starts.

```
smbclient -L localhost
```

---

### Post by Iowan on 2009-10-13
> **banquet said:**
> I would like to keep it on DHCP. Does anyone know how to slove this problem? Depending on your DHCP server, you *should* be able to issue the Samba server a "static lease" based on MAC address - Server always has the same address, but can get DNS information, etc., from DHCP server.

---

### Post by bab1 on 2009-10-13
> ...I believe the problem has something to do with the system's IP address being assigned by DHCP running on my router. The problem started occuring after I changed from a static IP to DHCP. I would like to keep it on DHCP. Does anyone know how to slove this problem? A temporary fix would be to restart samba 30 seconds after boot. How would it be possile to do this?

I have not seen this problem before, but I'll bet that samba is starting BEFORE the host is assigned an IP address.  Samba then quits, as it can't function correctly.  I do know that if your DHCP lease is renewed the smbd daemon will re-boot.  You might try looking in the system logs (dmesg and samba) for relevant info.

I believe that even if you assign a "reserved" address from DHCP; Samba will not be available upon boot.  in other words it's a timing problem you need to resolve.  First IP address then Samba.

---

### Post by banquet on 2009-10-14
Thanks for the replies,

heres my smb.conf

```
[global]
        netbios name = ice
        server string = %h server (Samba, Ubuntu)
        workgroup = WORKGROUP
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        guest account = ice
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[Videos]
        comment = Video
        path = /home/ice/Videos
        guest ok = Yes

[Downloads]
        comment = Completed Downloads
        path = /torrents/completed
        guest ok = Yes

[Disk_Images]
        comment = Installer ISO's
        path = /home/ice/Disk_Images/
        guest ok = Yes

[Music]
        comment = Music and Music Video
        path = /home/ice/Music/
        guest ok = Yes
```After disconnecting the network cable and restarting samba still failed to start.

```
ice@ice:~$ smbclient -L localhost
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)
ice@ice:~$ sudo /etc/init.d/samba restart
[sudo] password for ice:
 * Stopping Samba daemons                                                       
start-stop-daemon: warning: failed to kill 2599: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ]
ice@ice:~$ smbclient -L localhost
Enter ice's password:
Domain=[ICE] OS=[Unix] Server=[Samba 3.3.2]

        Sharename       Type      Comment
        ---------       ----      -------
        Videos          Disk      Video
        Downloads       Disk      Completed Downloads
        Disk_Images     Disk      Installer ISO's
        Music           Disk      Music and Music Video
        IPC$            IPC       IPC Service (ice server (Samba, Ubuntu))
Domain=[ICE] OS=[Unix] Server=[Samba 3.3.2]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            ICE

```This computer is assigned a reserved address from the router. I'm not really sure what to look for with dmesg and samba logs. How can I tell if samba is trying to start before being assigned an IP?

after boot my log.smbd contains

```
[2009/10/15 14:07:44,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/10/15 14:07:44,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/10/15 14:07:44,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/10/15 14:07:44,  0] lib/interface.c:load_interfaces(523)
  ERROR: Could not determine network interfaces, you must use a interfaces config line
[2009/10/15 14:08:24,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
```and log.nmbd

```
[2009/10/15 14:07:44,  0] nmbd/nmbd.c:main(850)
  nmbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/10/15 14:07:44,  0] lib/interface.c:load_interfaces(523)
  ERROR: Could not determine network interfaces, you must use a interfaces config line
[2009/10/15 14:08:24,  0] nmbd/nmbd.c:main(850)
  nmbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
```

---

### Post by Boondoklife on 2009-10-14
Try adding this to your config file

interfaces=10.0.1.30/24 127.0.0.1/8

replace the 10.0.1.30/24 with your ip/subnet

---

### Post by bab1 on 2009-10-15
> After disconnecting the network cable and restarting samba still failed to start.


```
ice@ice:~$ smbclient -L localhost
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

```

I think the smbd daemon is running but has not recognized a valid IP address.  Connection refused is not the same as SMB is not running.

When you restart the smbd it now finds the correct (and now up) IP address and all is well.

```
[2009/10/15 14:07:44,  0] lib/interface.c:load_interfaces(523)
  **[COLOR="Red"]ERROR: Could not determine network interfaces[/COLOR]**, you must use a interfaces config line
[2009/10/15 14:08:24,  0] smbd/server.c:main(1260)
  **[COLOR="Red"]smbd version 3.3.2 started[/COLOR]**.

```

This confirms the notion.

```
[2009/10/15 14:07:44,  0] lib/interface.c:load_interfaces(523)
  ERROR: Could not determine network interfaces, you must use a interfaces config line
[2009/10/15 14:08:24,  0] nmbd/nmbd.c:main(850)
  nmbd version 3.3.2 started.

``` 

The same for nmbd.

You might want to read [**_this_**]("http://ubuntuforums.org/showthread.php?t=1140094&highlight=smb+reload") completely.  The gist of it is that smbd is sensitive to IP address configuration.  I  recommend you seriously consider manually configuring the all networking parameters for the server.  No reserved addresses, just plain old manual static configuration with /etc/network/interfaces.

---

### Post by Dropbear on 2009-11-01
A workaround for this problem

```
sudo gedit /etc/rc.local
```

then add the line 

```
/etc/init.d/samba restart
```

just above where it says exit 0

This fixed the problem for me.

---

### Post by JPA619 on 2009-11-03
Hey Dropbear,
 
Thank you for the suggestion!  It works!
 
John

---

### Post by FirstByté on 2009-11-21
> **Dropbear said:**
> A workaround for this problem

```
sudo gedit /etc/rc.local
```

then add the line 

```
/etc/init.d/samba restart
```

just above where it says exit 0

This fixed the problem for me.

You are so sweet... Now I don't have to keep
```
sudo /etc/init.d/samba restart
``` each time
:popcorn:

---

### Post by alecz20 on 2010-03-22
> **Dropbear said:**
> A workaround for this problem

```
sudo gedit /etc/rc.local
```

then add the line 

```
/etc/init.d/samba restart
```

just above where it says exit 0

This fixed the problem for me.

This did not work for me. 
Samba doesn't start even if I add it in /etc/rc.local

---

### Post by BrainwreckedTech on 2010-08-26
I had this problem, too.  It's a race condition between starting Samba, when the interface is available, and when it gets its IP.  Sometimes [FONT="Courier New"]sudo restart samba[/FONT] would work, sometimes the process wasn't even running (which makes the restart command fail -- the init.d restart does a "blind" stop and start).

In [FONT="Courier New"]/etc/network/interfaces[/FONT], add this line to the appropriate iface stanza

```
post-up /etc/init.d/smbd restart
```

Now you're not messing with your RC scripts, and Samba will be restarted after the interface is completely up.

---

### Post by alecz20 on 2010-08-26
Thanks, I will try your solution if I ever get the problem again.


I ended up re-installing the whole system and now it is working fine.

However there is no telling when it might fail again.

---

