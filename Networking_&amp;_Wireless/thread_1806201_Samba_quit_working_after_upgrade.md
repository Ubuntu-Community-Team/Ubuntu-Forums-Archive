---
title: "Samba quit working after upgrade"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by phsonnek on 2011-07-17
I just upgraded to 10.04, as of this upgrade, samba has quit working.

From Windows I can ping the linux box (192.168.1.110)  If from Windows I key in ->Start->Run->\\192.168.1.110  I connect to my linux box.

If I try to access the linux box through the name, (\\tardis) I get network path not found.

Everything worked fine before the upgrade, now I cannot see my linux box via its network name.  I have a WD TV Live on my network and I must be able to see the linux box via its network name or I cannot connect to it.

iptables shows no rules

smbtree returns
SONCOM
	\\WINDOZE        		
	\\WDTVLIVE       		WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED


Here is my smb.conf file.

[global]
    ; General server settings
        netbios name = tardis
        server string = tardis
        workgroup = SONCOM
        announce version = 5.0
;       socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        log file = /var/log/samba/log.%m
        max log size = 1000

;       passdb backend = smbpasswd
        security = user
;       null passwords = no
;       username map = /etc/samba/smbusers
;       name resolve order = hosts wins bcast

        wins support = yes

        printing = cups
        printcap name = CUPS

;       syslog = 1
        syslog only = yes
        username map = /etc/samba/smbusers
        usershare owner only = false
        encrypt passwords = true
        guest ok = yes
        guest account = wdlive

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes][Torrent]
        path = /home/phsonnek/Torrent
        writeable = yes
        browseable = yes
        valid users = wdlive

[Videos]
        path = /home/wdlive
        writeable = yes
        browseable = yes
        valid users = wdlive

    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

[phsonnek]
        path = /home/phsonnek
        browseable = yes
        writeable = yes
        create mask = 0644
        directory mask = 0755
        force user = phsonnek
        force group = phsonnek
        valid users = phsonnek

What has changed that I am over looking?

---

### Post by jmoorse on 2011-07-17
First off, +1 for the name Tardis!

Second, your problem appears to be DNS, not samba.  Because:

> **phsonnek said:**
> 
From Windows I can ping the linux box (192.168.1.110)  If from Windows I key in ->Start->Run->\\192.168.1.110  I connect to my linux box.


Can you ping your Ubuntu server by name from Windows (ping tardis)?

Please post the output of 'hostname -f' from Ubuntu

---

### Post by phsonnek on 2011-07-17
hostname -f
tardis

---

### Post by phsonnek on 2011-07-17
What about the output from smbtree?

smbtree returns
SONCOM
\\WINDOZE
\\WDTVLIVE WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED


I would expect to see \\TARDIS  listed as well.  Wouldn't you?

---

### Post by jmoorse on 2011-07-17
> **phsonnek said:**
> What about the output from smbtree?

smbtree returns
SONCOM
\\WINDOZE
\\WDTVLIVE WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED


I would expect to see \\TARDIS  listed as well.  Wouldn't you?

I am not familiar with smbtree, but because you can connect by \\[IP] I don't think it is samba at fault.  It almost looks like your internal domain names are different.  hostname -f showed no suffix.

What does smbtree -b show?

On Windows run ipconfig /all and let me know what the host name is with the suffix (eg: dalek.local)

---

### Post by phsonnek on 2011-07-17
smbtree -b

SONCOM
	\\WINDOZE        		
	\\WDTVLIVE       		WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

---

### Post by jmoorse on 2011-07-17
On Windows run ipconfig /all and let me know what the host name is with the suffix (eg: dalek.local)

---

### Post by phsonnek on 2011-07-17
Host name . . . . . . : Windoze

---

### Post by phsonnek on 2011-07-17
I added the parameter  	client lanman auth = yes  to smb.conf Now smbtree -b  returns the following?

Shouldn't \\TARDIS be listed?


SONCOM
	\\WINDOZE        		
	\\WDTVLIVE       		WDTV LIVE
		\\WDTVLIVE\IPC$           	IPC Service (WDTV LIVE)

---

### Post by jmoorse on 2011-07-17
Can you ping tardis from windows by name: ping tardis
Can you ping windoze from ubuntu by name: ping windoze

?

---

### Post by phsonnek on 2011-07-17
EUREKA!

I just discovered that nmbd was not running (no clue as to why it was not running, it should have started on its own)

smbtree -b now returns
SONCOM
	\\WINDOZE        		
	\\WDTVLIVE       		WDTV LIVE
		\\WDTVLIVE\IPC$           	IPC Service (WDTV LIVE)
	\\TARDIS         		tardis
		\\TARDIS\myhome         	
		\\TARDIS\IPC$           	IPC Service (tardis)
		\\TARDIS\Videos         	
		\\TARDIS\Torrent        	
		\\TARDIS\phsonnek       	

and I can connect from windoze (and more importantly from wdlive.)


Now I just have to figure out why nmbd did not auto-start.

Thanks for the help.  You got my brain working in the right direction.

---

### Post by jmoorse on 2011-07-17
Awesome!

Anything interesting in:

/var/log/samba/log.nmbd ?

---

### Post by capscrew on 2011-07-17
> **phsonnek said:**
> EUREKA!

I just discovered that nmbd was not running (no clue as to why it was not running, it should have started on its own)

smbtree -b now returns
SONCOM
	\\WINDOZE        		
	\\WDTVLIVE       		WDTV LIVE
		\\WDTVLIVE\IPC$           	IPC Service (WDTV LIVE)
	\\TARDIS         		tardis
		\\TARDIS\myhome         	
		\\TARDIS\IPC$           	IPC Service (tardis)
		\\TARDIS\Videos         	
		\\TARDIS\Torrent        	
		\\TARDIS\phsonnek       	

and I can connect from windoze (and more importantly from wdlive.)


Now I just have to figure out why nmbd did not auto-start.

Thanks for the help.  You got my brain working in the right direction.

This is due to the the changes in the init system when moving to the Upstart system.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.google.com/search?q=nmbd+not+starting+ubuntu+10.04&btnG=Go!#hl=en&pq=nmbd%20not%20starting%20workaround%20ubuntu%2010.04&xhr=t&q=nmbd+workaround+ubuntu+10.04&cp=4&qe=bm1iZCB3b3JrYXJvdW5kIHVidW50dSAxMC4wNA&qesig=L2EIJbTJxDy54C7fHuMkXw&pkc=AFgZ2tm_vBcEYBAvI0YtKsgLI9JeNOAEEnCIMldn2M-PTW0fKDNvfzsy2u8mEMAAE3-m9kIJYPsHdOUqzJNo-Qwd2biQFkn2Aw&pf=p&sclient=psy&source=hp&aq=f&aqi=&aql=&oq=nmbd+workaround+ubuntu+10.04&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=804c136e9e03bc4a&biw=1122&bih=639&bs=1")

---

