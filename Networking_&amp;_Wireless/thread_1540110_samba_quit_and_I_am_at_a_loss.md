---
title: "samba quit and I am at a loss"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by swedski on 2010-07-27
Hello
Newbie no hacker here who is beginning to get frustrated.  First it took me a while to get samba configured for my network and after many searches threads and posts I finally got it working.  I go away for a month come home and now my Ubuntu 9.10 machine refuses to see my windows network.  It did this just two days ago.  I get the FAILED TO RECIVE SHARE LIST ERROR  and cannot mount windows share.
here is my Smb.conf

[global]
    ; General server settings
    netbios name = mark
    server string =
    workgroup = a135
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
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = mark
    force group = a135


I have a popcorn hour media tank and several laptops that this machine just will not access any longer.
Tired and frustrated and hope someone can help me
Mark
PS my smb and network access is also painfully slow and refuses to hook up at start up is this related?

---

### Post by swedski on 2010-07-27
Just gets better
I find a fix and try to start samba and it tells me its not installed as a service.  It even tells me how to install it which it does. How can that be?
Still doesn't work

---

### Post by grandsatrap on 2010-07-27
Hey.
You are trying to access your Windows shares from your Ubuntu computer? Is Samba running on Windows or Ubuntu? (Which is the server?)

I have an Ubuntu server (9.04) with Samba running and I can access it from Windows XP. If this is your setup then I can help you.

---

### Post by Iowan on 2010-07-27
Is basic networking functioning - can you ping between the machines?

---

### Post by swedski on 2010-07-28
I can ping my NMT but for some reason I can't see it in Network anymore.  I can see my domain a135 but it won't open

---

### Post by varunendra on 2010-07-30
Have you tried **[Howto: Fix Windows share browsing issues]("http://ubuntuforums.org/showthread.php?t=1169149")  ** thread under Tutorial & Tips section started by **[COLOR=Red]dmizer[/COLOR]**? It is dedicated to the same kind of problems & is pretty much active.

---

### Post by swedski on 2010-08-08
Thank you varunendra,
Link helped.  I went through all three problems and it is working now.  
Why varunendracan't there be an easier networking solution?

---

### Post by varunendra on 2010-08-08
> **swedski said:**
> Thank you varunendra,
Link helped.  I went through all three problems and it is working now.  
Why varunendracan't there be an easier networking solution?

Glad it helped!

Since I'm just a simple user like you, my answer to your question may be misleading so I'd rather keep quite. However I'd like to mention that despite a few difficulties I like ubuntu because it has some advantages over windows that (to me) matter more than those few difficulties. I still use both windows & ubuntu but trust ubuntu more.

Besides, ubuntu being open source, even normal users like us can contribute to help making it better. Sometimes it is as easy as reporting a bug or telling others what worked for you.

Like here, you can contribute your bit by just telling us what exactly worked for you and marking this thread as [solved], and maybe we could offer better help next time to someone like you!

---

