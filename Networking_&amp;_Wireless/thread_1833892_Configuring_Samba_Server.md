---
title: "Configuring Samba Server"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by shibby4555 on 2011-08-26
Hey guys,
So I am just a regular Ubuntu user here, I don't have a ton of skill with networking but I am trying to set up a Samba server for easy file sharing between my 5 computers on an LAN. 

All my of my computers run Ubuntu 10.10 0or greater and I don't really use Windows and all the tutorials are geared to accessing files from Samba on Windows.

So I set up the etc/samba/smb.cnf file as such

```

[global]
    ; General server settings
    netbios name = shibby
    server string =
    workgroup = linux
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

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
    force user = shibby
    force group = linux

```
So I set my username and password up. Then I entered to following command:
```
 smbclient -L linux
```Then I get the following error:
```
Connection to linux failed (Error NT_STATUS_UNSUCCESSFUL)
```So how do I exactly access the Samba server from another machine?
Thanks in advance.

---

### Post by Morbius1 on 2011-08-26
You got a desktop environment on this server ( Gnome, KDE, XFCE, etc... ) ?

> So I set my username and password up. Then I entered to following command:
     Code:
      smbclient -L linux 
Then I get the following error:
     Code:
     Connection to linux failed (Error NT_STATUS_UNSUCCESSFUL) 
Who is "linux". The name of your host is "shibby".

---

### Post by shibby4555 on 2011-08-26
> **Morbius1 said:**
> You got a desktop environment on this server ( Gnome, KDE, XFCE, etc... ) ?

Who is "linux". The name of your host is "shibby".



I wasn't sure if you login with the host or workgroup, I tried both and neither worked. This is under a gnome desktop environment.

I just tried it again, logged in with shibby. It worked once and the following came up for 30 seconds

```

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      
    MyFiles         Disk      
    IPC$            IPC       IPC Service ()
    downloads       Disk      
    shpongle        Disk      

```

Then it disconnected with the following and hasn't worked anymore.

```
Connection to shibby failed (Error NT_STATUS_UNSUCCESSFUL)
NetBIOS over TCP disabled -- no workgroup available
```

---

### Post by Morbius1 on 2011-08-27
I don't think I've ever seen that error message in an all linux network before - plus it seems to be intermittent.

* Um .... The first thing I would do is disable the firewall on shibby. If you haven't done anything to the firewall then no action is required but if you have then disable it.

* Then make sure Samba itself is working. Run the following command:
```
nautilus smb://192.168.0.100
```[COLOR=Blue][I]Change 192.168.0.100 to the ip address of shibby.

[/I][COLOR=Black]What should happen is Nautilus will open up to the shibby machine and you should be able to drill down to your myfiles share.

* Now this depends on what you have done to your configuration. You've already altered the smb.conf and deviated from the default settings so I'm not sure what else you've done but I would reset the name resolve settings to place the only working mechanism first :

Change this:
[/COLOR][/COLOR]> name resolve order = hosts wins bcast[COLOR=Blue][COLOR=Black]
To this:
[/COLOR][/COLOR]```
name resolve order = bcast hosts wins 
```[COLOR=Blue][COLOR=Black] 
Then restart samba:
[/COLOR][/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Blue][COLOR=Black]

Now run your smbclient or smbtree command again and see if that did anything.
[/COLOR][/COLOR]

---

