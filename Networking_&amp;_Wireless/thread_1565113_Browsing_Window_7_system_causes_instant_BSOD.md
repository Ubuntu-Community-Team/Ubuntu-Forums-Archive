---
title: "Browsing Window 7 system causes instant BSOD"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by bpsanborn on 2010-08-31
[B]Hi guys,

I am new to Linux and Ubuntu but an advanced user on Windows. On my home Workgroup network, I an running Ubuntu 10.04.1 on a spare PC and Windows 7 Professional on a  fast 4 core AMD PC. I built both PCs myself. The Win7 system is fully updated with maintenance. So is the Ubuntu system. The Win7 desktop system sees and shares files and printers with an XP SP3 laptop and Win 7 Home edition Netbook... and the the Ubuntu system The Ubuntu system can browse and see shares on the the XP Laptop but not the Window 7 Desktop or Netbook.  Both Win7 systems can browse and share the the Ubuntu system. There are no current problems anywhere in my Windows network.

Ubuntu gets into a login loop when trying to see the Win7 systems.   But before that problem gets solved... I have problem with random BSODs (00007f) on the Windows 7 systems immediately when I first try to browse the network from Ubuntu.   The effect is instantaneous.  You click on an icon that will browse the network and bingo the Windows system takes a BSOD 00007f dump. 

This appears to be something new in 10.04.1.  I have loaded 8.04 and 9.10 in past just for training and and curiosity reasons and never had this problem.  In the past, I lost interest and never went deeper.  This time I have a dedicated PC in my network for Ubuntu and need to get deeply into Linux.  I am trying to get up to speed on Linux this time around because I find that Linux systems are appearing in the network at work and I need to understand how to use and network Linux.  

Any help would be appreciated.

Brian
[/B]

---

### Post by endotherm on 2010-08-31
on the win7 box, I would recomend shutting down all apps, and running (as admin from a terminal) 
```
sfc.exe /SCANNOW
```and perhaps reinstalling samba on the ubuntu system.

a misconfiguration should never BSOD a box (be it client or server) so it almost has to be a bad file, or a more serious issue.

as for the login loop, in the ubuntu systems /etc/samba/smb.conf
add a line like this to the globals section:
```
client NTLMv2 auth = yes
```post back with these commands from the ubuntu box:
```
sudo cat /etc/samba/smb.conf
sudo net usershare

```samba is in kind of a transition in ubuntu, as samba is for a text based server platform, and ubuntu is desktop. try to think of the gui share creation (usershare) as kind of an add-on to enhance the text based nature of samba. the text based type (which is in my opinion more sure and stable) is configured in /etc/samba/smb.conf. if you use the gui usershare, the system still uses smb.conf, but augments it with per-user information about shares. this means that a share created by the gui is only online if the user is logged in, or at least it used to.

here is the community documentation for samba, and a howto:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

my advice is whichever approach to configuring samba you use, pick one and try to stick with it. bad things happen when you try to mix gui administration with text based. if you go with the gui, you may want to just tweak your smb.conf, but don't create shares in it that have already been created in the gui.

the other benefit to text-based configuration is that it is much better understood and supported by the community. much of the support given online for linux is done in terms of commands and settings lines, because they are almost gaurenteed to work on most systems (whereas everyone's desktop is different), and because asking volunteers to capture, crop, annotate, upload, and embed "point and click" images is sometimes asking too much.

---

### Post by bpsanborn on 2010-09-01
Thanks to folks on the forum, I have solved the problems I was having with Ubuntu 10.04.1 browsing shares on Win7.  Win7 defaults to requiring password access to shares.  The fix was in the smb.conf file.  I had to allow password encryption.   That file has been poked at for the last two days with too many suggested changes from the forum.  I don't know which ones did something and which ones did not.

I am still getting a random BSOD (00007F)  in Win7 when I click on the network icon in the Nautilus File Manager. With my recent changes... this time...  I got an error message on the Ubuntu side and I can see that  Ubuntu/Samba/Nautilus sent out a NETWORK\\\ query.  I'll try chasing  it on the Windows side as well.   

Thanks for the help.  Here is the info from the Ubuntu system you asked for.  The NET command produced no output:

brian@linux:~$ sudo cat /etc/samba/smb.conf
    server string = %h server (Samba, Ubuntu)
    security = share
;    netbios name = linux
#    encrypt passwords = no
    map to guest = Bad User
#    obey pam restrictions = Yes
    guest account = brian
#    pam password change = Yes
#    passwd program = /usr/bin/passwd %u
#    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
#    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
#    panic action = /usr/share/samba/panic-action %d
#    valid users = %S
    create mask = 0775
    directory mask = 0775
    guest ok = yes
    name resolve order =  lmhosts hosts wins bcast
#    null passwords = yes
    workgroup = WORKGROUP
        client lanman auth = Yes
        lanman auth = Yes


[homes]
    comment = Home Directories
;    browseable = yes
    writeable = yes
    path = /home/brian
    valid users = brian, brian

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    create mask = 0700

[Documents]
    path = /home/brian/Documents
    valid users = brian
    read users = brian
    write users = brian writable = yes
    read only = No
;    browseable = yes
    guest ok = yes

[brian_home]
    comment = Brian's Home Directory
    path = /home/brian
    writeable = yes
;    browseable = yes
    valid users = brian, brian

---

### Post by endotherm on 2010-09-01
glad you got it working. I personally use a differant set of settings (security=user no lanman auth, etc) but if it works for you, thats all that matters. just out of curisoity though, using lanman auth, did you have to edit the win7 local security policy to allow unsecure protocols?

---

### Post by Morbius1 on 2010-09-01
I have never ever heard of a BSOD on windows ( although I admit I know nothing of Win7 ) caused by accessing a shared resource.

On a side note your smb.conf is in a bit of a mess.

[homes] like [printers] is a mega share and represents a group of things. It's meant to represent the home folder of every login user on that system. It's usually there if the system is being used as a server and your configuration seems more peer - to -peer.

Also, allowing guest access but only for brian seems odd and there is no "read users" or "write users" as in:
> [Documents]
    path = /home/brian/Documents
    valid users = brian
    [COLOR=Blue]read users = brian
    write users = brian[/COLOR] writable = yes
    read only = No
;    browseable = yes
    guest ok = yesI think you meant to say "read list" and "write list"

Luckily samba has a built in algorithm for people like you and I - what it cannot understand it ignores. So the above share will be interpreted by samba as:
> [Documents]
    path = /home/brian/Documents
    valid users = brian
    read only = NoWhich will have the same effect.

---

### Post by bpsanborn on 2010-09-01
Morbius1,
 
I'm guility as charged. Being new to Linux, Ubuntu and Samba, I am driving way out in front my headlights without knowledge. I have been reading the forums and trying everything that seemed to have a chance of fixing things. I have been hacking away at the the smb.conf file for two and a half days now. 
 
Now that the problem has been identified and fixed, I would love to go back to a simple default smb.conf file. Is there a suggested base file example for a mixed Ubuntu/win7/winxp network? Should I remove and then reinstall Samba?
 
BTW, as might be expected, I traced traced the BSOD to a win7 netbios handler. Some have suggested on the win7 forums side that it may be related to the ZoneAlarm firewall and anti-virus program I am using on win7.
 
Thanks for the help
 
Brian

---

### Post by bpsanborn on 2010-09-01
Endotherm,
 
I'm not sure I need that lanman stuff anymore. At the time I was still trying to get ubuntu/samba to "see" the win7 systems. At the forums suggestion I went to the advanced network security policy section of win7 admin services and stopped win7 from insisting on using 128 encription and ntlm2. I'm going to have to step myself back from some of those changes because I don't think they were the cause of the problems.
 
I'll report back when I norrow down what is useless and what causes a change in behavior.
 
Brian

---

