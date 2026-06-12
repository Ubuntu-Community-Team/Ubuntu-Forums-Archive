---
title: "intrepid gnome-ppp dialer permission problem"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by jeff35 on 2009-03-15
I am trying to connect my ubuntu system online.
I have the modem found, ran pppdconfig(as I remember) i need to write this down better. setup wvdialer.conf, and changed the permisions. when i dial out i get:


OK
--> Modem initialized.
--> Sending: ATM1L3DT3018226
--> Waiting for carrier.
ATM1L3DT3018226
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Mar 14 12:20:48 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8107
--> Disconnecting at Sat Mar 14 12:20:49 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

where is the /ect/ppp/pap-secrets: and chap-secrets file located?
what file do I modify now?

---

### Post by jeff35 on 2009-03-15
update
next i made pap-secrets, and chap-secrets with 777 permission:

# Secrets for authentication using PAP
# client ....server....... secret ......IP addresses
[email]you@copper.net[/email] * password

and now i get modem results of:

OK
--> Modem initialized.
--> Sending: ATM1L3DT3018226
--> Waiting for carrier.
ATM1L3DT3018226
CONNECT 460800
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sun Mar 15 02:26:15 2009
--> Pid of pppd: 10499
--> Disconnecting at Sun Mar 15 02:26:16 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


I think its closer, still working on it tho any suggestion?

---

### Post by lee292 on 2009-03-16
If it's any comfort, you're not alone!  I'm  getting errors very similar to yours.  The "secrets" files are in /etc/ppp, if you haven't already found them.  I modified them but the ppp daemon still dies!

---

### Post by jeff35 on 2009-03-18
on my system i had to create 3 file as root located in the /etc/ppp diectory,
pap-secrets
chap-secrets
options

gave them all 777 permision
sudo -i

as root chmod 777 /etc/ppp/file

where file was pap-secrets, chap-secrets, options

now i gwt online, but cant do anything, i have java installed in firefox.

results;
OK
--> Modem initialized.
--> Sending: ATDT301 8226
--> Waiting for carrier.
ATDT301 8226
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 18 14:57:06 2009
--> Pid of pppd: 10497
--> Using interface ppp0
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> local  IP address 24.155.175.84
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> remote IP address 66.90.132.234
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> primary   DNS address 67.211.172.29
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> secondary DNS address 67.211.172.30
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
defaultroute
restore default path
restoredefaultroute
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> Connect time 1.5 minutes.
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> pppd: ï¿½[10]ï¿½[08]([08]ï¿½[08]
--> Disconnecting at Wed Mar 18 14:58:39 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

what now i am still stuck?

---

### Post by robin0800 on 2009-03-22
What I did was to force gnome ppp to start with root permissions.
This should be the default, it is for kppp but not for gnome.
I did this in KDE, added kdesudo to the icon executable.
Not sure how you do this in gnome.

---

### Post by fredbird67 on 2009-05-11
In GNOME or Xfce, it would be "gksudo gnome-ppp"

---

