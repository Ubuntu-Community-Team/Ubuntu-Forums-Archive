---
title: "minor samba problem"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by dajasc on 2009-03-15
After a little messing around I got samba working on my Ubuntu machine.  The good news is now the windows machines can see the shares on the Ubuntu machine.  The bad news is that the windows machines no longer see each others' shares.  If I type the computer name into the box on the windows machines I can still get to them but just clicking on "view workgroup computers" now shows only the Ubuntu machine.  

I have changed nothing in the windows configuration so I'm concluding that it is my smb.conf that is doing something.  Any ideas would be appreciated.

```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


domain master = yes
preferred master = yes
local master = yes
wins support = yes
wins proxy = yes
os level = 65

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user
security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root


#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


[media]
path = /home/media
browseable = yes
public = yes
writeable = yes
guest ok = yes



```

---

### Post by fatbotgw on 2009-03-15
I wouldn't think your samba settings would prevent Windows from seeing shares.  Have you tried rebooting your Windows computers?  It's been my experience that Windows sometimes won't see a share until after a reboot.

---

### Post by inobe on 2009-03-15
here is the proper way to setup file smb 


now i suggest setting up a small network using the windows wizard first before anything else...........

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

choose the nautilus setup' i prefer just to share from one folder in nautilus.........

be sure to create a user name and password for ubuntu' windows is already insecure lols' don't make your linux box the same.........

create or select and existing folder during the setup' you don't want to share your home directory for security purposes !
ubuntu needs a reboot

---

### Post by dajasc on 2009-03-19
After rebooting the windows machine I now see only the windows shares.  But if I type in \\192.168.100.202 (the address of the Ubuntu machine) then it opens the shares.  It won't just browse to it.  It's fine.  I'll map the shares I want in windows as network drives.  It's just strange.

---

### Post by uzi09 on 2009-03-19
are you just doing a simple share of some folders on your ubuntu machine??

if so, your smb.conf file looks like it's doing a lot more than just that.

Best is to just stick with a **very** basic setup. Like this one:
```

# Global Parameters
[global]
workgroup = MIDEARTH
security = SHARE
[Plans]
path = /plans
read only = Yes
guest ok = Yes

```
source: [http://www.samba.org/samba/docs/man/Samba-Guide/simple.html](http://www.samba.org/samba/docs/man/Samba-Guide/simple.html)

That guide, "Samba by Example", is a fantastic guide to get started on. You take something simple, see if it works. Then modify it little by little checking if it works on the way to finally get to where you want to be!

---

### Post by dajasc on 2009-03-20
I took your advice.  Stripped it down to just what you have there.  It still works, but in the same way it did.  You can't browse to it but you can type its address in and get there.

I was thinking maybe it could be related to going through the firewall.  Does it broadcast its name through some port other than 137, 138, or 139?  You would think if that were it it would never have worked even one time and it did.

---

### Post by FishRCynic on 2009-03-20
> **dajasc said:**
> I took your advice.  Stripped it down to just what you have there.  It still works, but in the same way it did.  You can't browse to it but you can type its address in and get there.

I was thinking maybe it could be related to going through the firewall.  Does it broadcast its name through some port other than 137, 138, or 139?  You would think if that were it it would never have worked even one time and it did.

not a firewall issue - gvfs samba nautilus and microsoft tcpip and
resolving the ip address 

go back and use the wins server you had originally albeit unintentionaly setup - (if you ubuntu machine is 24/7 like a server as it will be the wins server and you set your windows machines to use it)

OR

set up localhost with the ip's  of the applicable machines (both for your
ubuntu machine and windows machines) 

either method should let you browse correctly

---

### Post by dajasc on 2009-03-21
Turning the wins server back on is fine.  How exactly do I get the windows machines to use it?  They are windows XP if that matters.

---

### Post by dajasc on 2009-03-21
I should have added that the router was already set up to hand out 192.168.100.202 as the primary wins server (that's the Ubuntu machine's static address).  I thought that was the problem the first time around, that the windows machines didn't know that they are supposed to be getting wins from the Ubuntu machine.  Apparently that was not enough to solve it.

Also, yes, the ubuntu server runs 24/7.

---

### Post by dajasc on 2009-03-23
I checked and the windows machines actually report in ipconfig /all that 192.168.100.202 (the Ubuntu server) is the primary WINS server.  They still only see themselves though and not the Ubuntu machine.

Ideas?

---

### Post by dajasc on 2009-03-26
Let me start by saying that I am really starting to hate samba.

I decided that I would just live with the inability to browse to the samba shares.  Irritating but fine.

Then I installed a new hard drive, working fine, mounted fine etc.  Now I want to share it.  I added its path as follows in /etc/samba/smb.conf:

```

[music drive]
path=/home/david/music
browseable = yes
public = yes
writeable = yes
guest ok = yes

```

This is in the same smb.conf file as the others that more or less work with security = shared.  I restart samba.  I go to it in windows like the others and it prompts for a password.  Password?!?!?  Why do I need a password for this one and not the others?  Permissions on the folder are set the same as the other folders so what is the problem?

Suggestions are appreciated.

---

