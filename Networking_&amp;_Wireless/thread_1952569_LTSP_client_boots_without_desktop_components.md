---
title: "LTSP client boots without desktop components"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by Avinash.Rao on 2012-04-04
Hi, 

Linux 11.10 32-bit Desktop Edition with all updates installed on a Dell Inspiron laptop with 4GB RAM. Machine works well locally.

I have installed LTSP and configured according to the documentation. The installation was successful without any errors. 

The LTSP client a sony vaio laptop is able to login but the desktop is without any component even the side panel is missing. Below is my lts.conf. 

user@host:/var/lib/tftpboot/ltsp/i386$ more lts.conf 
[default]
           LDM_DIRECTX=True
	   LOCALDEV=True



Any help is appreciated.
Avinash

---

### Post by Avinash.Rao on 2012-04-04
Hi,

With the below lts.conf the client is not able to login, after entering the username and password, the prompt comes back to login screen!

 # Global defaults for all clients
           # if you refer to the local server, just use the
           # "server" keyword as value
           # see lts_parameters.txt for valid values
           ################
           [default]
               #X_COLOR_DEPTH=16
               LOCALDEV=True
               SOUND=True
               NBD_SWAP=True
               SYSLOG_HOST=server
               #XKBLAYOUT=de
               SCREEN_02=shell
               SCREEN_03=shell
               SCREEN_04=shell
               SCREEN_05=shell
               SCREEN_06=shell
               SCREEN_07=ldm
               # LDM_DIRECTX=True allows greater scalability and performance
               # Turn this off if you want greater security instead.
               LDM_DIRECTX=True
               # LDM_SYSLOG=True writes to server's syslog
               LDM_SYSLOG=True

---

### Post by Avinash.Rao on 2012-04-06
I finally fixed it, got the answer from ltsp-discuss group.
The clients get a clean desktop if 'ubuntu 2d' is chosen as the preferred session at the login screen. This can be made as the default screen by adding a line in lts.conf. Hope this helps others.

 # Global defaults for all clients
           # if you refer to the local server, just use the
           # "server" keyword as value
           # see lts_parameters.txt for valid values
           ################
           [default]
               X_COLOR_DEPTH=24
               LOCALDEV=True
	       LDM_SESSION="gnome-session --session=gnome-fallback"
	       LDM_SESSION="gnome-session --session=ubuntu-2d"
               SOUND=True
               USE_LOCAL_SWAP=True
	       NBD_SWAP=False
	       SYSLOG_HOST=server
               #XKBLAYOUT=de
               SCREEN_02=shell
               SCREEN_03=shell
               SCREEN_04=shell
               SCREEN_05=shell
               SCREEN_06=shell
               SCREEN_07=ldm
               # LDM_DIRECTX=True allows greater scalability and performance
               # Turn this off if you want greater security instead.
               LDM_DIRECTX=True
               # LDM_SYSLOG=True writes to server's syslog
               LDM_SYSLOG=True

---

### Post by mightyiam on 2013-05-02
Raring no longer has unity-2d. What's the solution, now, please?

---

