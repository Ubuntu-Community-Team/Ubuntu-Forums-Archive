---
title: "Xbox Media Center and SAMBA won't talk, help please."
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by Mischief on 2007-02-17
Hi fellas,

I'm trying to share files from Ubuntu to my Xbox via Samba but it just won't work.

First, I've connected the Xbox via nic and I can ping the Xbox. I then installed Samba following various guides from the forum. 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

Did all the steps, added users and edited the config-file for Samba.

> [global]
    ; General server settings
    netbios name = Burken
    server string =
    workgroup = workgroup
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

[Flicks]
    path = /media/sdb1/Flicks
    browseable = yes
    read only = no
    guest ok = no  
    create mask = 0644
    create mask = 0777
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP


In XBMC, I've set the same user name and password as the one I created in Samba. 
When I choose to "add source" for "My Videos" I get the following error:

[B]"Remote Share"

"Could not connect to the remote server"[/B]

The path I entered (IP for my second nic) was "smb://192.168.0.100", I've also tried just "192.168.0.100" with the same result.

I can't see how this can be so difficult. I don't even know if I'm remotely close of getting this working. 

I used to share via Windows Media Connect and Upnp. Is there a Upnp share application available for Ubuntu to use instead?

Please help me out here.

Thanks in advance.

---

### Post by Mischief on 2007-02-18
Ok, I've kept trying throughout the night yesterday and waisted the entire Sunday. 

I tried connecting to the Xbox via gFTP and got the following error:
> 
Looking up 192.168.0.10
Trying 192.168.0.10:21
Cannot connect to 192.168.0.10: No route to host
Waiting 30 seconds until trying to connect again

How is it that I can ping the Xbox but is unable to connect to it via FTP?

Any suggestions?

---

### Post by antharr on 2007-02-20
Need more info.

-What are the settings on your Xbox?
-Do have DHCP enabled?
-Whats the IP, Subnet Mask, and Gateway set to on your computer and Xbox?
-What kind of router are you using?

---

### Post by Mischief on 2007-02-21
Thanks for helping out!

> -What are the settings on your Xbox?

Which settings?


> -Do have DHCP enabled?

It's enabled on the NIC to ethernet but static on the NIC to Xbox


> -Whats the IP, Subnet Mask, and Gateway set to on your computer and Xbox?

eth0: Connected to broadband router 
Automatic Configuration (DHCP)

eth1: From computer to Xbox
Static IP address
Ip Address: 192.168.0.100
Sub Net Mask: 255.255.255.0
Gateway: None

Xbox:
Static:
IP Address: 192.168.0.10
Sub Net Mask: 255.255.255.0
Gateway: 192.168.0.1
DNS: 192.168.0.1


> -What kind of router are you using?

No router, the Xbox is connected via NIC from my computer. There's however a broadband router connected to eth0.

Also, I'm still confused why I can't FTP to the Xbox. I remember in Windows (yes, I know Ubuntu isn't Windows) that the network icon would go on when Xbox was powered on. Is there a feature for that too in Ubuntu?

Thanks!

---

### Post by mmkevins on 2007-02-22
I have been successful at sharing my home folder in ubuntu with my xbox via samba, but I am not able to share external hard drives.  I have read on and on about various problems that are similar, but nothing I have tried has worked.  Since my xbox  can see files in my home directory, I feel like I am almost there.

Is there something that needs to be done to make the external drives accessible??  Perhaps some kind of a symbolic link to my home folder?

Any help would be appreciated, as I have spent hours and hours reading about samba and only now am resorting to posting.

---

### Post by Teva on 2007-03-04
> **mmkevins said:**
> I have been successful at sharing my home folder in ubuntu with my xbox via samba, but I am not able to share external hard drives.  I have read on and on about various problems that are similar, but nothing I have tried has worked.  Since my xbox  can see files in my home directory, I feel like I am almost there.

Is there something that needs to be done to make the external drives accessible??  Perhaps some kind of a symbolic link to my home folder?

Any help would be appreciated, as I have spent hours and hours reading about samba and only now am resorting to posting.


Hey mmkevins,

Would you be able to share your smb.conf file or at least tell me what settings I should have?  I had my XBOX working with Dapper no problem then I did a fresh install to Edgy (by the way I've only been using Linux for 2 months) and I can see my share drive from the XBOX but it keeps asking for my username and password.  I've entered those in my path for the XBOX but it keeps asking.  I'm pretty sure my XBOX is set up correctly because I can use that same link when I boot my PC into Windoze.  When I originally set up Dapper, I didn't have to touch my smb.conf file and like I said it was working flawlessly.  Is there something I'm missing?

Thanks a lot.

Teva

---

### Post by Iceni on 2007-03-06
> **Teva said:**
> Hey mmkevins,

Would you be able to share your smb.conf file or at least tell me what settings I should have?  I had my XBOX working with Dapper no problem then I did a fresh install to Edgy (by the way I've only been using Linux for 2 months) and I can see my share drive from the XBOX but it keeps asking for my username and password.  I've entered those in my path for the XBOX but it keeps asking.  I'm pretty sure my XBOX is set up correctly because I can use that same link when I boot my PC into Windoze.  When I originally set up Dapper, I didn't have to touch my smb.conf file and like I said it was working flawlessly.  Is there something I'm missing?

Thanks a lot.

Teva

This is just a random suggestion but in your smb.conf have you eneabled guest? Mine looks like this:

[MyFiles]
    path = /home/xxx/shares
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = xxx
    force group = xxx

On Edgy, running xbox 1.6 with xecuter 3 and media center 2.0. No problems at all.

---

