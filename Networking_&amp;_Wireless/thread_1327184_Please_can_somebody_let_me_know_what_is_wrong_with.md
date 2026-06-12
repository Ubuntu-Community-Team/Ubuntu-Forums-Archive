---
title: "Please can somebody let me know what is wrong with my smb.conf file?"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by scratman on 2009-11-15
I would like to share 3 folders in my home folder, they are :-

/home/scratman/Videos
/home/scratman/Music
/home/scratman/Pictures

I can access the shared folders and files on my other machine, and I have read/write access on my other machine with no need to enter a username or password.   However, when trying to share folders and files on my machine, it requires my username and password.  I would like to be able to share folders without having to set up usernames and passwords.

My smb/conf file is attached.  Any help and advice would be appreciated as Samba does baffle me somewhat and I would like to understand what I am doing wrong.

    ; General server settings
    netbios name = HARDY
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    usershare owner only = false

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

[global]
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody

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
[DVD-ROM Drive]
    path = /media/cdrom0
    browseable = yes
    read only = yes
    guest ok = yes

[MyFiles]
    path = /home/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = 
    force group =

---

### Post by ashishmalik10 on 2009-11-15
Add following lines at the end of your smb.conf file :

[MyFile1]
path = /home/scratman/Videos
browseable = yes
read only = no

[MyFile1]
path = /home/scratman/Music
browseable = yes
read only = no

[MyFile1]
path = /home/scratman/Pictures
browseable = yes
read only = no





This should do the job.

---

### Post by Wobblybob on 2009-11-15
Hi,

Try this how to which I did when i set mine up [[COLOR="Blue"]http://myubuntublog.wordpress.com/2009/10/04/shared-directories-with-samba/[/COLOR]]("http://myubuntublog.wordpress.com/2009/10/04/shared-directories-with-samba/"), when you open the share it should bring up a box asking for password but you can tick the box telling it to remember it. I would set-up separate sections in the conf for each folder you actually want to share in your home and not the whole folder.

Good Luck

---

### Post by scratman on 2009-11-15
> **ashishmalik10 said:**
> Add following lines at the end of your smb.conf file :

[MyFile1]
path = /home/scratman/Videos
browseable = yes
read only = no

[MyFile1]
path = /home/scratman/Music
browseable = yes
read only = no

[MyFile1]
path = /home/scratman/Pictures
browseable = yes
read only = no





This should do the job.

This made every file and folder in my home folder visible, but only to view file structure, I could not open folders or files.  I'm not sure why this would be.

---

### Post by dmizer on 2009-11-15
Try this:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

   workgroup = MSHOME
   netbios name = HARDY
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Printing ##########

# CUPS printing.  Uncomment these lines to share your printer through CUPS
;   printing = cups
;   printcap name = cups

############ Misc ############

   usershare allow guests = yes

#======================= Share Definitions =======================

[Videos]
        path = /home/scratman/Videos
        read only = no
        guest only = yes
        guest ok = yes

[Music]
        path = /home/scratman/Music
        read only = no
        guest only = yes
        guest ok = yes

[Pictures]
        path = /home/scratman/Pictures
        read only = no
        guest only = yes
        guest ok = yes
```

---

### Post by scratman on 2009-11-16
dmizer you are a genius.  Thankyou so much, that has worked perfectly.  I'm not quite sure how, but it does!! :D

---

### Post by Iowan on 2009-11-16
The "security = share" does wonders to eliminate the username/password problem.  I'm sure there are a few other necessary details that go along.

---

### Post by dmizer on 2009-11-16
> **scratman said:**
> dmizer you are a genius.  Thankyou so much, that has worked perfectly.  I'm not quite sure how, but it does!! :D

For the most part, I simply used the default smb.conf file and added your share information to it. Glad it worked. :)

---

