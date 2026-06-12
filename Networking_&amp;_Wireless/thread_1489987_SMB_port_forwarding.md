---
title: "SMB port forwarding?"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Vi3GameHkr on 2010-05-21
I've had some extensive problems using SMB to share files between my desktop and laptop computers.

I want the desktop to act as the server, and the laptop as the client.  I think I set the desktop up okay but have no way of testing it, because of the laptop.  I think the problem might be in my router, but that can easily be fixed with port forwarding I assume... Well it would be easy if I knew what ports I needed to forward!

On my laptop, When I go to Places > Network, sometimes I get an error message saying
> Could not display "network:///".

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken.  Please select another viewer and try again.

I don't quite understand what that error is, but I try to open Network again and it opens successfully without a problem.  None of the other network machines appear (and from my desktop, all the network machines appear except for my laptop) but I get an icon labeled "Windows Network".  When I click that, I see WORKGROUP, so I click that and get "Opening "WORKGROUP". You can stop this operation by clicking cancel" which stays on the screen for a really long period of time.  After that I just get "Unable to mount location Failed to retrieve share list from server"

The Desktop is running 10.04 64-bit and the laptop is running 10.04 32-bit.  They can ping each other just fine so my only idea as to what the problem is would be port forwarding.

---

### Post by wheredidrealitygo on 2010-05-21
SMB (Server Message Block on Windows, SAMBA under Linux) is a non-route-able protocol, meaning it cannot go past the router, it can go *through* the router to work on the local LAN without any ports being forwarded.

Ports only need to be forwarded if you're trying to go beyond the router, meaning onto the internet. On the local LAN no ports need to  be forwarded, only possibly unblocked on the actual server because both machines (laptop and desktop) are behind the same router.

Post your /etc/samba/smb.conf from your server so people can check and make sure the server is set up properly, also you should be attempting to connect to it through "Places", "Connect to Server", "Windows Share", then type the IP address of the desktop as the "Server" field, the name of the share in the "Share" field, and the user name in the "User Name" field.

Want an easier solution? install openssh-server on the desktop, and use "ssh" instead, same method, except put "ssh" as protocol instead of "Windows Share", then you only need the server address and user name, other fields can be left blank. *Bonus*: doesn't need configuring like SMB does. Install it and it works.

---

### Post by Vi3GameHkr on 2010-05-22
> [global]
    ; General server settings
    netbios name = marcus-desktop
    server string =
    workgroup = Workgroup
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
    path = /home/files/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = marcus
    force group = sambashare

There you go.  I think I thought I ssh earlier, but I was recommended against it for some reason I have forgotten by now.  SSH does work over the internet if configured right, correct?  My goal right now is to share files between the desktop and laptop, and later on I might be taking my laptop away from home more often (I've got the whole summer to work with this) so I would like to be able to access some files securely over the internet (no confidential information of course, just to be safe) but I can play with that later.

Thanks,

---

