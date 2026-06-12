---
title: "mount samba share and error 115"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by wagoner on 2012-12-19
Alright, I've been stuck trying to mount my samba share for the last day and half now.:mad:  I finally got it, sort of.

My samba share has been working pretty well, or so I thought.  I can browse to it with a file manager, and I've been able to do everything using the netbios name instead of the IP address.  

As an example, here is the result of smbclient with the name of the server, LINUX-HIHN.  Note that I did not use the servers IP address.

```
adam@adam-Dell16:~$ smbclient -NL \\linux-hihn
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        LaundrySink     Disk      Backup Computer
        IPC$            IPC       IPC Service (Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386)
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Server               Comment
        ---------            -------
        LINUX-HIHN           Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386

        Workgroup            Master
        ---------            -------
        WORKGROUP            

```

Here is nmblookup
```
adam@adam-Dell16:/mnt/sink$ nmblookup -A 192.168.15.101
Looking up status of 192.168.15.101
        LINUX-HIHN      <00> -         B <ACTIVE> 
        LINUX-HIHN      <03> -         B <ACTIVE> 
        LINUX-HIHN      <20> -         B <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
        WORKGROUP       <00> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

```

Everything works great, right?  The servers IP address, 192.168.15.101 resolves to it's host name, LINUX-HIHN, without a problem.

So now I try to mount the samba share, adding the verbose option so that I can see what is going on.
```
adam@adam-Dell16:~$ sudo mount -t cifs -v -o user=adam //linux-hihn/LaundrySink /mnt/sink
Password: 
mount.cifs kernel mount options: ip=69.16.143.24,unc=\\linux-hihn\LaundrySink,,ver=1,user=adam,pass=********
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:~$ sudo mount -t cifs -v -o user=adam //192.168.15.101/LaundrySink /mnt/sink
Password: 
mount.cifs kernel mount options: ip=192.168.15.101,unc=\\192.168.15.101\LaundrySink,,ver=1,user=adam,pass=********

```

It turns out that mount works fine if I use the IP address.  By using the verbose option on the mount command, it shows that the name resolves to ip=69.16.143.24.  Where the hell does that come from?  The machine is actually at 192.168.15.101!  Here is what happens when I try to ping the IP address from the mount command.

```
adam@adam-Dell16:/mnt/sink$ ping 69.16.143.24 -c5
PING 69.16.143.24 (69.16.143.24) 56(84) bytes of data.

--- 69.16.143.24 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4030ms

```This IP is completely bogus!  It's not on my network anywhere!

I can mount the share with the IP address.  I don't plan to use it everyday, but good grief.  Does anyone know what went wrong?

---

### Post by redmk2 on 2012-12-20
> **wagoner said:**
> Alright, I've been stuck trying to mount my samba share for the last day and half now.:mad:  I finally got it, sort of.

My samba share has been working pretty well, or so I thought.  I can browse to it with a file manager, and I've been able to do everything using the netbios name instead of the IP address.  

As an example, here is the result of smbclient with the name of the server, LINUX-HIHN.  Note that I did not use the servers IP address.

```
adam@adam-Dell16:~$ smbclient -NL \\linux-hihn
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        LaundrySink     Disk      Backup Computer
        IPC$            IPC       IPC Service (Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386)
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Server               Comment
        ---------            -------
        LINUX-HIHN           Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386

        Workgroup            Master
        ---------            -------
        WORKGROUP            

```

Here is nmblookup
```
adam@adam-Dell16:/mnt/sink$ nmblookup -A 192.168.15.101
Looking up status of 192.168.15.101
        LINUX-HIHN      <00> -         B <ACTIVE> 
        LINUX-HIHN      <03> -         B <ACTIVE> 
        LINUX-HIHN      <20> -         B <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
        WORKGROUP       <00> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

```

Everything works great, right?  The servers IP address, 192.168.15.101 resolves to it's host name, LINUX-HIHN, without a problem.

So now I try to mount the samba share, adding the verbose option so that I can see what is going on.
```
adam@adam-Dell16:~$ sudo mount -t cifs -v -o user=adam //linux-hihn/LaundrySink /mnt/sink
Password: 
mount.cifs kernel mount options: ip=69.16.143.24,unc=\\linux-hihn\LaundrySink,,ver=1,user=adam,pass=********
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:~$ sudo mount -t cifs -v -o user=adam //192.168.15.101/LaundrySink /mnt/sink
Password: 
mount.cifs kernel mount options: ip=192.168.15.101,unc=\\192.168.15.101\LaundrySink,,ver=1,user=adam,pass=********

```

It turns out that mount works fine if I use the IP address.  By using the verbose option on the mount command, it shows that the name resolves to ip=69.16.143.24.  Where the hell does that come from?  The machine is actually at 192.168.15.101!  Here is what happens when I try to ping the IP address from the mount command.

```
adam@adam-Dell16:/mnt/sink$ ping 69.16.143.24 -c5
PING 69.16.143.24 (69.16.143.24) 56(84) bytes of data.

--- 69.16.143.24 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4030ms

```This IP is completely bogus!  It's not on my network anywhere!

I can mount the share with the IP address.  I don't plan to use it everyday, but good grief.  Does anyone know what went wrong?

The IP address is legit.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://69.16.143.24.ipaddress.com/").  I have a feeling that your LAN DNS is misconfigured in some way.

[COLOR="Blue"]Edit: sorry for the error on the previous thread.  I was just leaving when I saw your post.  The proper incantation should be:  mount -t cifs //server/share -o <whatever>

Never the less you still have a name server problem that needs to be corrected, [/COLOR]

---

### Post by Morbius1 on 2012-12-20
It would appear that 69.16.143.24 is the ip address of the DNS server for your ISP. ( [http://who.is/nameserver/resolver2.qwest.net/](http://who.is/nameserver/resolver2.qwest.net/) ). I have actually seen this type of thing before.

I don't know the full extent of how you are set up but out of curiosity run the following command to see how you are resolving netbios names:
```
testparm -sv | grep "name resolve order"
```If "bcast" isn't first in order you might want to rearrange it to put it first and then restart smbd.

---

### Post by wagoner on 2012-12-20
Thanks Morbius1.  Yes, I have the name resolve order set to use bcast first.

```
adam@adam-Dell16:~$ testparm -sv | grep "name resolve order"
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[ADAMS_FILES]"
Loaded services file OK.
Server role: ROLE_STANDALONE
        name resolve order = bcast wins lmhosts hosts

```

I'll try to answer your question about my set-up.  
I have two desktop computers wired to linksys router. This all sits on my desk right now.  The linksys router is wired to my dsl modem/router down in the basement.  It's a Qwest Q1000Z that I got from the phone company.

Here is the result of smbtree.  Perhaps this will explain it further.
```

adam@adam-Dell16:~$ smbtree
Enter adam's password: 
WORKGROUP
        \\LINUX-HIHN                    Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386
                \\LINUX-HIHN\IPC$               IPC Service (Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386)
                \\LINUX-HIHN\LaundrySink        Backup Computer
                \\LINUX-HIHN\print$             Printer Drivers
        \\ADAM-DELL16                   Samba 3.5.11
                \\ADAM-DELL16\PSC-1600-series   HP PSC 1600 series
                \\ADAM-DELL16\IPC$              IPC Service (Samba 3.5.11)
                \\ADAM-DELL16\ADAMS_FILES    
                \\ADAM-DELL16\print$         

```

How can this be fixed?

---

