---
title: "Cannot connect to printer. win7-&gt;ubuntu samba"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by AtrocityDT on 2010-02-10
Hello everybody,

I have a brand new laptop with windows 7 (64bit) and a desktop with ubuntu freshly installed 3 days ago. I've spent the last 12 hours tweaking the smb.conf file and have the file sharing in a stable state (2mb/s) xfer rate. 

My problem aside from the slow xfer rate, is I cannot seem to get the windows 7 computer to access the printer that is hooked up to my ubuntu box. 

To recap:
Laptop - Windows 7 connected wireless
Desktop - Ubuntu 9.10 with samba 3.5.4
Printer - Hooked to desktop (and working)
File Sharing - Good

Problem: 
Laptop - Cannot connect to printer

My current smb.conf is pasted below... any help would be appreciated, my wife needs to be able to print from her brand new laptop =P
---------------------------
[global]
    ; General server settings
    netbios name = kory
    server string =
    workgroup = morton
    announce version = 5.0
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    large readwrite = no
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

[WD USB 2]
	path = /media/WD USB 2
;	writeable = no
;	browseable = yes
	guest ok = yes

---

### Post by Morbius1 on 2010-02-10
You shouldn't need to use smb.conf to print, use CUPS Server to print.

These are the paths for 9.04 so there may be differences if you're using Karmic:

Using CUPS is a two step process:
[B]
Enable Sharing for that Printer:

[/B]System > Administration > Printing > Right Click the attached printer > Properties > Policies > Check Enabled, Accepting Jobs, and Shared

 **Enable Publishing of the Shared Printer**:

System > Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

I think the cups service is automatically restarted when you do all this but just in case, enter the following in a Terminal:

[B]sudo service cups restart

[/B]Give it a shot, and if it doesn't work let us know what the exact error messages that Win7 is giving you.

---

### Post by AtrocityDT on 2010-02-10
Well, I commented out the printer lines in my smb.conf and reaccomplished the printer sharing and publishing steps you just mentioned. (I had done them last night multiple times)

I can't even see the printer now, whereas before on the windows box I could see the printer but was unable to add it.

A few things that might help, I can access the printer from internet explorer on the windows box (192.168.1.39:631/printers) but cannot see it in the add printers wizard anymore.

Also, view the attached JPG, I don't think there are win7 drivers for the printer loaded on the linux box?

---

### Post by Morbius1 on 2010-02-10
Actually I didn't mean for you to comment the lines out in smb.conf. CUPS will still use the smb protocol for discovery of services to Windows - it's just that you didn't need to alter the default printer sections in smb.conf.

Mine looks like this:
> [printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
When you're in the **Print Wizard in Windows** can you access the printer directly:
URL: \\192.168.1.39\Ubuntu_Printer_Name

---

### Post by tonyguntrum on 2010-02-10
I am haveing the same trouble.  I can not connect my vista or xp comuters to my ubunto 9-10.  I've tryed everything I've read here on the boards, but I am new to linux and not sure I'm following correctly.
when I try to connect using IE   [\\192.168.1.107\C4600]("file://\\192.168.1.107\C4600") it trys to connect but says windows can not find [\\192.168.1.107\C4600]("file://192.168.1.107/C4600") please check the spelling.  
when I use windows to find it just says no printers found.
when I use select printer by name [\\server-a\C4600]("file://\\server-a\C4600") it keeps telling me something about the spool or to restart the computer, or sometimes it just can't find it.
 
the server ip is 192.168.1.107 the name is server-a and the printer name is C4600 probably obvious,, if there is anyother information anyone needs to help me I will do my best to find it.  
 
I'd really appreciate anyhelp I can get.  I really dont want to go back to windows.  As I learn more about linux, hoping eventualy to move all my computers to it.
 
Thank you

---

### Post by Morbius1 on 2010-02-10
There does seem to be an issue with Karmic and basic services starting up at boot. Try to start them manually and see if it gets you further along:

Open **Terminal**
Type **sudo service cups restart**
Type **sudo service samba restart**

---

### Post by tonyguntrum on 2010-02-10
cups restarted fine but for samba I got samba: unrecognized service
is this a program i need to install myself? I downloaded ubunto 3 days ago installed and downloaded anouther 500 some megs of updates today.
 
awsome, instaled samba from the applications/ubuntu software center, and now windows see and installed the printer fine.  hopefully it works as well on xp as the vista machines
 
Thank You very much for your help

---

