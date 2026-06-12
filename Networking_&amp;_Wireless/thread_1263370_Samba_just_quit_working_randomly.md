---
title: "Samba just quit working randomly"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by grimdeath on 2009-09-10
I noticed that today I could not access my mapped ubuntu share in either of my Windows pc's. This has been working without issue for months.

The only thing odd was that my ubuntu machine was powered off the other day (I never turn it off!). Perhaps the power went out in my house one evening, im not sure.

I had it setup so I could just enter this to access my mapped drive:

```
\\192.168.1.101\MyFiles
```

Here is my current smb.conf file:

```

[global]
    ; General server settings
    netbios name = grimdeath-server
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

	usershare owner only = false

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = grimdeath
    force group = grimdeath

```

I have not changed anything related to networking or Samba recently so I dont know why it is doing this. Any idea what I can do?

Searching around I found people saying they had similar issues but their solutions did not seem to help. Restarting samba, etc...

If need be I dont mind clearing everything else and starting again from scratch. I absolutely have to have access to my important files on my Ubuntu machine though!

*edit*
the only thing I have dont on the Ubuntu machine lately is install ImageWriter to help create a create a  version of the Ubuntu Netbook Remix as a live boot drive. Perhaps I have installed some regular updates as well. Sorry grasping at straws here but it'st he only thing ive done on the machine lately.

---

### Post by grimdeath on 2009-09-13
bump...

still not sure why this just quit working all of a sudden. I have not had time to sit down and troubleshoot the issue but I think the best bet will be to just remove all the existing networking and start from scratch.

there are no guides I know of that show how to do that, if you guys get a chance to explain what all I need to do in order to do that I would really appreciate it.

---

### Post by uncle-c on 2009-09-14
If your Ubuntu machine was powered off and then restarted perhaps the Samba daemon is not currently running on Ubuntu ? Have you checked which services are running on Ubuntu ?

```


$ ps aux | grep smb


```

If you have Samba running on your Ubuntu then you should get output like this,

```


[unclec@localhost ~]$ ps aux | grep smb
root      2017  0.0  1.0  16928  2548 ?        Ss   08:46   0:00 smbd -D
root      2033  0.0  0.4  16928  1092 ?        S    08:46   0:00 smbd -D
unclec    2294  0.0  0.2   4124   680 pts/0    S+   09:18   0:00 grep smb
[unclec@localhost ~]$ 

```

where "smbd -D" represents the Samba daemon.

---

### Post by grimdeath on 2009-09-15
The wife is getting ticked that she cant access her photos on the file server so thanks for the reply!

I had tried restarting Samba a few times while trying other possible fixes. No luck. Here's the result of the line you posted:

```

1000      4195  0.0  0.0   3336   800 pts/0    S+   23:18   0:00 grep smb
root      4647  0.0  0.2  14032  2712 ?        Ss   Sep10   0:00 /usr/sbin/smbd -D
root      4648  0.0  0.0  14032   940 ?        S    Sep10   0:00 /usr/sbin/smbd -D

```

---

### Post by grimdeath on 2009-09-15
thought I would bump this one last time.

I am going to spend my whole evening after work and see if I can get this sorted on my own. Any advice for removing the existing samba setup and starting over or similar is welcome.

Thanks

---

### Post by capscrew on 2009-09-15
I can't see any reason to remove the Samba daemon in your situation.  You do need to dig into what is actually going on.  Samba seems to be working.  There is another daemon that needs to be running at the same time.  The nmbd daemon.  To check both try```
ps aux|grep mbd
```

You should get a results like this```
ps aux|grep mbd
root      4719  0.0  0.3   6524  1308 ?        Ss   10:30   0:00 [COLOR="Blue"]/usr/sbin/nmbd -D[/COLOR]
root      4721  0.0  0.6  10128  2356 ?        Ss   10:30   0:00 /usr/sbin/smbd -D
root      4762  0.0  0.3  10128  1060 ?        S    10:30   0:00 /usr/sbin/smbd -D
bruce     5471  0.0  0.2   3008   848 pts/0    S+   11:16   0:00 grep --color=auto mbd
```

Is it possible that the IP address has changed when you restarted the Ubuntu host?  Are you using DHCP to set the IP address?

It appears that you created the share by manually configuring /etc/samba/smb.conf.  This is good.  This is also the only variable your the configuration.  To reconfigure all you need to do is update your conf file ([COLOR="Red"]AFTER MAKING A COPY OF IT[/COLOR]).

---

### Post by grimdeath on 2009-09-15
Yea I figured it wasnt needed but I am sort of at my wits ends. Here the results from mdb

```

root      4642  0.0  0.1   8272  1812 ?        Ss   Sep10   0:13 /usr/sbin/nmbd -D
root      4643  0.0  0.0   8140   656 ?        S    Sep10   0:00 /usr/sbin/nmbd -D
root      4647  0.0  0.2  14032  2712 ?        Ss   Sep10   0:00 /usr/sbin/smbd -D
root      4648  0.0  0.0  14032   940 ?        S    Sep10   0:00 /usr/sbin/smbd -D
1000     27977  0.0  0.0   3336   800 pts/1    S+   17:21   0:00 grep mbd

```

I havent thought about the IP changing, I swear I have restarted in the past due to updates that required it. Where is the IP information related to Samba configured, I do not see anything for that in the conf file (sorry it has been a few months since I set all this up!). If you can explain where I can check that I will compare to my local IP's now. It seems like it might be something along those lines.

I have already backed up my conf file when I was trying some other changes on my own, I can restore it if need be.

*edit*
duh I figured it out myself lol...long day at work obviously! yea the IP of the linux machine had changed, the last part of it changed from .101 to .102! Not sure why. Any tips for keeping that static?

For anyone that has a similar issue do this:
Go to System > Admin > Network Tools, on the Network Devices drop down change it to your Ethernet Interface and you will see you IP address listed. For command line you can just use ipconfig.

Such a simple thing...those are the worst problems :P Live and learn! Thanks for all the help

---

### Post by capscrew on 2009-09-15
> **grimdeath said:**
> Yea I figured it wasnt needed but I am sort of at my wits ends...


How about the IP address?  What are the results of ```
ifconfig -a
```

I get this for my eth0```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:76:cd:54:e0  
          [COLOR="Blue"]inet addr:192.168.1.12[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fecd:54e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2076896 (1.9 MB)  TX bytes:241285 (235.6 KB)
          Interrupt:11 Base address:0xc000 

```

---

### Post by grimdeath on 2009-09-15
see my post above, I was able to get it resolved. It was the IP after all, the very end of it changed from 101 to 102 for some odd reason.

---

### Post by capscrew on 2009-09-15
> yea the IP of the Linux machine had changed, the last part of it changed from .101 to .102! Not sure why. Any tips for keeping that static? 

Not sure why?  You configured the interface to use DHCP.  Usually the DHCP server renews the lease with the current IP address.  But sometimes not.  Good lesson: NO DHCP with dynamic IP addressing for interfaces that are used by servers e.g Samba!  If you can't manually configure the interface then at the least configure your DHCP server to hand you the same address (reserved) all the time.

---

### Post by grimdeath on 2009-09-15
> **capscrew said:**
> Not sure why?  You configured the interface to use DHCP.  Usually the DHCP server renews the lease with the current IP address.  But sometimes not.  Good lesson: NO DHCP with dynamic IP addressing for interfaces that are used by servers e.g Samba!  If you can't manually configure the interface then at the least configure your DHCP server to hand you the same address (reserved) all the time.

Ok I will look into doing that. This was my first foray into networking with Linux, which I am not pro in for Windows either! I was sure I would run into a few issues eventually. Again thanks for the help.

---

### Post by Iowan on 2009-09-15
It then becomes decision time as to how to fix it (or new thread time...). You can either edit **/etc/network/interfaces** to set up a static adddress, or (if the DHCP server can handle it) set up a static lease on your DHCP server. If your Samba server is on a machine with a desktop (and Network Manager), you can configure a manual address there.

Oops - looks like I'm being a bit redundant... (sorry **capscrew**)

---

### Post by capscrew on 2009-09-15
> **Iowan said:**
> It then becomes decision time as to how to fix it (or new thread time...). You can either edit **/etc/network/interfaces** to set up a static adddress, or (if the DHCP server can handle it) set up a static lease on your DHCP server. If your Samba server is on a machine with a desktop (and Network Manager), you can configure a manual address there.

Oops - looks like I'm being a bit redundant... (sorry **capscrew**)

...and I get to hop up on my soap box, Iowan. 

First we have to see if NM is managing the manually configured IP.  If so then ay config at /etc/network/interfaces is useless as the config is held elsewhere.  :-(  

Either way a manually configured address (static) is what you get.  If you prefer the DHCP server to hand out the address you have 2 choices; dynamic or reserved.  Reserved is always a fixed address as this is what you are reserving; the IP address to a specific MAC address.  :-)

But what the heck it's all just semantics anyway!

---

### Post by Iowan on 2009-09-15
Whilst we're debating ;) NM _*should*_ ignore an interface configured in */etc/network/interfaces*, so try the configuration via NM first - or be prepared to comment out changes to */etc/network/interfaces*.

---

### Post by capscrew on 2009-09-15
Whilst that MAY be true, we both have heard the bleating of less experienced users complaining that the settings that they have tried in /etc/network/interfaces disappeared upon the next reboot.  

All of my desktops and servers are "sans NM" and the IP address is statically configured by via the aforementioned /etc/network/interfaces file.

My wireless hosts are laptops (or sub laptops and have either XP or Mac OSX installed.

I guess I should break down and get a small laptop to experiment with Linux and wireless setups.

---

