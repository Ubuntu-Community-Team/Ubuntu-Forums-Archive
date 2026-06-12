---
title: "Network Mythbuntu to Windows 7"
date: 2012-08-05
forum: Mythbuntu
---

### Post by chuckrp on 2012-08-05
I have been trying to network the recordings folder from my Mythbuntu computer to a folder on my Window 7 computer. I have the network setup. I loaded Samba and added my user info. I am still not able to access either machine from the other. I have a shared folder set up on a spare drive in the Windows computer. I also set up the recordings folder to share. I am missing something but not sure what. Can anyone help me out?

---

### Post by nickrout on 2012-08-05
IIRC mythbuntu is set to share the recordings folder via samaba without any intervention, but my machine was first set up some years ago, and I may be wrong or something may have changed.

So you are trying to access your recordings directory on your windows machine? So you can play the recordings on windows yes? If so you need to set up (on the myth machine) /etc/samba/smb.conf and restart samba. Mine has the following section:

```
[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

```

to restart samba:

```
sudo service smbd restart
```

if that doesn't fix it then please let us know EXACTLY what you are doing and EXACTLY what you see on the windows side (can you ping from the windows box to the mythbox by ip address? by name? do you see no computers on the LAN? Do you see the mythtv box but no folders? Do you see the folder but no contents?

---

### Post by chuckrp on 2012-08-06
Here is where I am at. The windows 7 computer says that I have a Homegroup setup. I have a password. When I check the Homegroup, it sees this computer and a laptop in another room. I am not sharing with the laptop. The computers are labled CHUCK-PC and CINDY-PC. I do not see the Mythbuntu computer. I went into MythTv and it says that the IP address is the default (127.0.0.1)
I went to the recording folder in the Mythbuntu computer. Using Samba, I listed myself and this computer along with my password. Still nothing. Should I use the Homegroup label with that password? What do you think?
Thanks for your help.

---

### Post by anonymousdog on 2012-08-06
No idea how to make Samba work with Homegroups (although it might support them).  However, you need to answer Nick's questions, or no one can help you.

Can you ping the MB computer by IP address?  ...by name?

Can you see the MB PC in the Windows Explorer network listing (not necessarily within the Homegroup)?  If so, can you see the shares/folders?

---

### Post by Rotak on 2012-08-07
The problem is, that the homegroup crap of win7 home is somewhat like hiding the normal workgroup setup from users. I've found this on the web...

I am unsure, whether the default win7 homegroup is really called "MYHOME", but I think that's the only problem of you not seeing the MythBox in your network computer list...

This is in /etc/samba/smb.conf... Locate the variables in the file and replace them with these values. "netbios name" and "server string" can be chosen freely. Make sure netbios name does NOT contain whitespaces!

```

[global]
workgroup = MYHOME
netbios name = MythBox
server string = This is my MythTV box
security = share 

```

Restart samba or reboot, and check if you can see the myth box. It should be visible as "MythBox" (or whatever you entered as netbios name). If it's still not visible, try to open a file explorer and enter "\\MythBox" as the location. Maybe you can at least access it like that.

---

### Post by chuckrp on 2012-08-07
Sorry about not answering the questions.
No I cannot ping the computer using the IP address listed in Mythbuntu (127.0.0.1)
No I cannot see it listed by name
It is not listed in the Homegroup or explorer. The only 2 computers listed are the Windows 7 computer that I want to connect to and a Vista laptop that is not networked to the Win 7 computer.

---

### Post by steeldriver on 2012-08-07
The 127.0.0.1 IP is just the loopback interface - that's only used for the mythfrontend to talk to the mythbackend (on systems with no additional frontends). If it's connected to your LAN, it will also have a LAN IP which you can find using ifconfig

If you didn't opt to install SAMBA/CIFS sharing during the mythbuntu install, then remember you will need the smb server components (not just the client components) in order to export the CIFS shares. To check if your SAMBA service is running, you can do

```
service smbd status
```on the mythbuntu box. FWIW I've found that if you change the smbd.conf it seems to require a reboot (not just a smbd service restart) to propagate the changes - at least in the case of the workgroup.

Hope that helps - I can post my mythbuntu /etc/samba/smb.conf if it would help (and yes I can see the shares from Windows 7)

---

### Post by chuckrp on 2012-08-07
The Samba service are installed. I typed the "service smbd status" and it listed Samba as running. I also typed IPCONFIG and go the INET, BCAST, and MASK addresses. I also have the name of the Mythbuntu computer now.
So I did an internet search and found a site under LIBERIANGEEK.NET. There were some other things there that I did. I can now go to Thunbar File Mgr-Network and the Windows 7 computer, Mythbuntu computer and the laptop are listed there. If I click on the Win 7 computer it says that "Failed to open Win 7" (failed to retrieve shared list from server). I have rebooted both machines. 
So I am thinking there is a problem with the sharing on the Win 7 computer or the Mythbuntu does not know where to look. I have tried to connect to the Myth computer by entering the IP address and the name. No luck.
Any suggestions?

---

### Post by steeldriver on 2012-08-07
afaik the only thing required to get the Win7 box to see the mythbuntu exports was to set the correct workgroup in /etc/samba/smb.conf

I haven't tried to see the Win7 box from mythbuntu so I can't comment on that

---

### Post by nickrout on 2012-08-08
> **chuckrp said:**
> The Samba service are installed. I typed the "service smbd status" and it listed Samba as running. I also typed IPCONFIG and go the INET, BCAST, and MASK addresses. I also have the name of the Mythbuntu computer now.
So I did an internet search and found a site under LIBERIANGEEK.NET. There were some other things there that I did. I can now go to Thunbar File Mgr-Network and the Windows 7 computer, Mythbuntu computer and the laptop are listed there. If I click on the Win 7 computer it says that "Failed to open Win 7" (failed to retrieve shared list from server). I have rebooted both machines. 
So I am thinking there is a problem with the sharing on the Win 7 computer or the Mythbuntu does not know where to look. I have tried to connect to the Myth computer by entering the IP address and the name. No luck.
Any suggestions?

on your linux box type ```
ifconfig
```Your lan is probably connected to eth0. What is the IP address associated with eth0? Lets pretend for clarity it is 192.168.1.5

Once you have that, go to the windows box and type (in a cmd window)```
ping 192.168.1.5
```

Can you get a connection?

If so what happens when you open an explorer window omn windows (explorere NOT internet explorer) and type \\192.168.1.5\ into the address bar (and hit enter)?

---

### Post by chuckrp on 2012-08-08
I did the ifconfig and got the address. It was in the section labled WLAN. Went to the Win 7 computer and was able to ping the Myth computer. So typed in the address in the explorer bar and the Myth folders were there. I made a short cut on the desktop and it connects. 
Thanks for the help.

---

### Post by chuckrp on 2012-08-16
Here is a new question concerning the same issue. I was able to connect the Win 7 to Mythbuntu computer. It worked perfect the first 2 times. Since I have rebooted the computers they will not talk to each other. The Myth computer still sees the Win 7 computer but will not talk to it. The Win 7 computer does not see the Myth computer. I can not ping it or by typing the address into the run bar. What do you think?
 
See the messages in "Network Mythbuntu to Windows 7" forum for all the other messages.

---

### Post by nickrout on 2012-08-16
> **chuckrp said:**
> Here is a new question concerning the same issue. I was able to connect the Win 7 to Mythbuntu computer. It worked perfect the first 2 times. Since I have rebooted the computers they will not talk to each other. The Myth computer still sees the Win 7 computer but will not talk to it. The Win 7 computer does not see the Myth computer. I can not ping it or by typing the address into the run bar. What do you think?
 
See the messages in "Network Mythbuntu to Windows 7" forum for all the other messages.

On reboot did the IP addresses change?

In linux the command to check the ip address is ifconfig. In windows it is ipconfig.

---

