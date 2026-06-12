---
title: "How to broadcast server name via DHCP"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2011-11-11
I'm a longtime linux user, but relatively unfamiliar with DHCP. I have a netbook with
ubuntu 10.04 which connects to the network via wifi and DHCP. I have another computer
here with ubuntu 10.04 as well as a mac mini - OS is Lion or OSX 10.7.
They are both connected via ethernet.

Neither of the other computers can 'see' the netbook. I.E. if I choose **Network** on my
other ubuntu machine, there is no icon for the netbook.

I can connect with the netbook from the mac by using the following protocol
smb://192.168.1.104/sharename - having gotten the broadcast IP address from ifconfig
or from the Wireless Icon -> **Connection Information**  dropdown item.

[COLOR="Blue"]So how do I get the netbook to broadcast a **name**?[/COLOR]

NOTE: The netbook can 'see' both of the other computers.

thanks
tim

---

### Post by northd_tech on 2011-11-12
What exactly are you trying to share on the network- a printer, file(s),  directory(ies)?  If you just want to have shared access to a directory (and/or directory tree), then the easiest way is to go into System > Administration > Shared Folders.

Then you will need to "Click to make changes" and enter a password, then click the "General Properties" tab and enter the desired [Windows Networking/Samba] WORKGROUP.  Go to the Users tab and grant permission for whichever user(s) you wish (and hopefully you already added these using System > Administration > Users and Groups so that you just need to add a checkmark next to their name(s) now).  Now finally, go to the "Shared Folders" tab and "Add" the path to your desired Shared Folder (which you will 'broadcast' or "Share using: Windows Networks (SMB)"- and this is the only option in my current configuration for Shared Folders).

For printers, I haven't broadcast Linux printers to Windows computers via Samba/Windows Networking before, but I have set up remote Windows printers under Ubuntu using System > Administration > Printing.  then "Add" > Printer > Network Printer > Windows Printer via SAMBA and "Browse" to your "Share" item on the WORKGROUP.

I have also set up Linux printers as Network Printers and shared them with other Linux (& UNIX) computers/workstations, but that was under Red Hat Linux a long time ago (and I seem to recall using the Hostname and/or IP address to do so).

If you're just accessing photos, data, MP3 music, videos, etc. then the easiest way will be to just set up a Shared Folder directory tree like above.  Otherwise, an NTFS 'shared partition' for your media/data if you need to share INTERNAL disk space with Win XP/Vista/7 works well (and is how I usually prefer to set up dual boot systems for ease of data access and backup).

Sharing an internet connection is not so easy, but I remember reading threads on this forum about that subject- search around here a bit if that is what you wish to do.

---

### Post by tim042849 on 2011-11-12
> **northd_tech said:**
> What exactly are you trying to share on the network- a printer, file(s),  directory(ies)?  Director(ies).
> **northd_tech said:**
> If you just want to have shared access to a directory (and/or directory tree), then the easiest way is to go into System > Administration > Shared Folders.
 
**I see no such menu item as   [COLOR="DarkRed"]Administration > Shared Folders[/COLOR]. on either one of our ubuntu computers.** They are both 10.04
> **northd_tech said:**
> 
Then you will need to "Click to make changes" and enter a password, then click the "General Properties" tab and enter the desired [Windows Networking/Samba] WORKGROUP.  Go to the Users tab and grant permission for whichever user(s) you wish (and hopefully you already added these using System > Administration > Users and Groups so that you just need to add a checkmark next to their name(s) now).  Now finally, go to the "Shared Folders" tab and "Add" the path to your desired Shared Folder (which you will 'broadcast' or "Share using: Windows Networks (SMB)"- and this is the only option in my current configuration for Shared Folders).
 
From my original post, the workstation is 'visible' on the network. It has a static IP address
and is connected via ethernet.
The netbook connects via DHCP and wireless. It is not visible on the network, except by
pointing a samba URL to it using the IP that it is assigned.
In both cases, sharing is set by going to the file browser and right-clicking on the icon/button
for the folder, choosing [COLOR="DarkRed"]Properties->Sharing[/COLOR] and [COLOR="DarkRed"]Properties->Permissions[/COLOR].
That works for the workstation, but not for the netbook.

[COLOR="Red"]**Yikes!**[/COLOR] As I write, I now see that the netbook is visible on the Ubuntu workstation's [COLOR="Blue"]Places -> Network[/COLOR] and [COLOR="DarkRed"]Finder[/COLOR] on the
mac is also picking it up. I'm a noob when it comes to mac and not a network geek, so I
am unable to conjecture as to why things are working now and weren't yesterday.

I appreciate the reply. I would add that I used similar methods as you for printer sharing for
the workstation. For the mac I had to use CUPS and had to point to the CUPS server via the
mac's static IP, not localhost.

Thanks
tim

---

### Post by capscrew on 2011-11-12
> **tim042849 said:**
> ...
[COLOR="Blue"]So how do I get the netbook to broadcast a **name**?[/COLOR]

NOTE: The netbook can 'see' both of the other computers.

thanks
tim

When its all said and done, SMB/CIFS (Samba) relies on NETBIOS broadcasts to match NETBIOS name to IP address.  The Local Master Browser (LMB) holds a small database.  When you browse the network you are viewing this list.

Samba can either be configured to resolve the hostname (/etc/hosts) to NETBIOS NAME or you can explicitly declare the NETBIOS name in /etc/samba/smb.conf.  If you are using DHCP with IP addresses that can change you MUST use the latter method.

To declare the NETBIOS name in the /etc/samba/smb.conf file.  You can add this to the [global] section```
netbios name = <your_hostname>
nameresolve order = bcast
```

This is how windows is configured.  It's called a B-node.

---

### Post by tim042849 on 2011-11-12
> **capscrew said:**
> When its all said and done, SMB/CIFS (Samba) relies on NETBIOS broadcasts to match NETBIOS name to IP address.  The Local Master Browser (LMB) holds a small database.  When you browse the network you are viewing this list.

Samba can either be configured to resolve the hostname (/etc/hosts) to NETBIOS NAME or you can explicitly declare the NETBIOS name in /etc/samba/smb.conf.  If you are using DHCP with IP addresses that can change you MUST use the latter method.

To declare the NETBIOS name in the /etc/samba/smb.conf file.  You can add this to the [global] section```
netbios name = <your_hostname>
nameresolve order = bcast
```

This is how windows is configured.  It's called a B-node.
Thank you for the explanation capscrew. One other question. Your example is for one machine
on the network. How would one code for two or more?
I.E. would it be: ```

netbios name = host1
nameresolve order = bcast
netbios name = host2
nameresolve order = bcast

```??
IOWS: is a **nameresolve** rule needed for each host entry?

Also, I note that there is no smb.conf on the Mac (darwin). I imagine there is a similar
process. I will research that elsewhere.
regards
tim

---

### Post by capscrew on 2011-11-12
> **tim042849 said:**
> Thank you for the explanation capscrew. One other question. Your example is for one machine
on the network. How would one code for two or more?
I.E. would it be: ```

netbios name = host1
nameresolve order = bcast
netbios name = host2
nameresolve order = bcast

```??
IOWS: is a **nameresolve** rule needed for each host entry?

Also, I note that there is no smb.conf on the Mac (darwin). I imagine there is a similar
process. I will research that elsewhere.
regards
tim

Each host that is configured as a B-node needs exactly what I showed you.  There is no centralized place for this.  The Local Master Browser collates the information.  On a host with Samba this is done by the daemon ***nmbd***.  This daemon can function as a Master browser, but so can any Windows host.  The role is by elections between the various hosts on the LAN.

To see the results try these from the command line of the Ubuntu host```
smbtree
smbclient -L <netbios_name>
```

Post the info and I will annotate it for you.

---

### Post by dandnsmith on 2011-11-12
sorry - same info, without realising it had just been answered while I was typing

---

### Post by capscrew on 2011-11-12
> **tim042849 said:**
> ...Also, I note that there is no smb.conf on the Mac (darwin)

I believe you will find the smb.conf file at:** /etc/smb.conf **not at:/etc/samba/conf

---

### Post by tim042849 on 2011-11-12
> **capscrew said:**
> I believe you will find the smb.conf file at:** /etc/smb.conf **not at:/etc/samba/conf
This is probably true for Mac OSX 10.6 and earlier. However, it is my understanding that
apple has 'ditched' samba, in part because of licensing issues. I believe that nsmb.conf is now
the configuration file and could be found at /etc/nsmb.conf **or**  ```


     ~/Library/Preferences/nsmb.conf
                     The user's configuration file, conflicts will be overwritten by the global file.

``` 
from 'man nsmb.conf' on Mac Lion.
:redface: But I'm just learning this...

---

### Post by tim042849 on 2011-11-12
> **capscrew said:**
> Each host that is configured as a B-node needs exactly what I showed you.  There is no centralized place for this.  The Local Master Browser collates the information.  On a host with Samba this is done by the daemon ***nmbd***.  This daemon can function as a Master browser, but so can any Windows host.  The role is by elections between the various hosts on the LAN.

To see the results try these from the command line of the Ubuntu host```
smbtree
smbclient -L <netbios_name>
```

Post the info and I will annotate it for you.
From smbtree: ```

WORKGROUP
	\\LINUS          		Tim's Mac mini
		\\LINUS\tim            	
		\\LINUS\Tim Johnson's Public Folder	
		\\LINUS\Linus          	
		\\LINUS\IPC$           	
	\\HPMINI         		hpmini server (Samba, Ubuntu)
		\\HPMINI\tims           	
		\\HPMINI\IPC$           	IPC Service (hpmini server (Samba, Ubuntu))
		\\HPMINI\print$         	Printer Drivers
	\\BARBARA        		barbara server (Samba, Ubuntu)
		\\BARBARA\barbaras       	
		\\BARBARA\IPC$           	IPC Service (barbara server (Samba, Ubuntu))
		\\BARBARA\print$         	Printer Drivers

```
And from smbclient ```

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (hpmini server (Samba, Ubuntu))
	tims            Disk      

	Server               Comment
	---------            -------
	BARBARA              barbara server (Samba, Ubuntu)
	HPMINI               hpmini server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            BARBARA

```
Hopefully I did that correctly... HPMINI is the netbook on DHCP
And Steve Jobs is probably rolling in his grave because I gave a mac a hostname of Linus..
thanks again
tim

---

### Post by capscrew on 2011-11-12
> **tim042849 said:**
> From smbtree: ```

WORKGROUP
	\\LINUS          		Tim's Mac mini
		\\LINUS\tim            	
		\\LINUS\Tim Johnson's Public Folder	
		\\LINUS\Linus          	
		\\LINUS\IPC$           	
	\\HPMINI         		hpmini server (Samba, Ubuntu)
		\\HPMINI\tims           	
		\\HPMINI\IPC$           	IPC Service (hpmini server (Samba, Ubuntu))
		\\HPMINI\print$         	Printer Drivers
	\\BARBARA        		barbara server (Samba, Ubuntu)
		\\BARBARA\barbaras       	
		\\BARBARA\IPC$           	IPC Service (barbara server (Samba, Ubuntu))
		\\BARBARA\print$         	Printer Drivers

```
And from smbclient ```

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (hpmini server (Samba, Ubuntu))
	tims            Disk      

	Server               Comment
	---------            -------
	BARBARA              barbara server (Samba, Ubuntu)
	HPMINI               hpmini server (Samba, Ubuntu)

	Workgroup            [COLOR="Red"]Master[/COLOR]
	---------            [COLOR="Red"]-------[/COLOR]
	WORKGROUP            [COLOR="Red"]BARBARA[/COLOR]

```
Hopefully I did that correctly... HPMINI is the netbook on DHCP
And Steve Jobs is probably rolling in his grave because I gave a mac a hostname of Linus..
thanks again
tim

Interesting.  If I'm not mistaken SUN (oops, I mean Oracle) Solaris also wrote their own SMB/CIFS server.  You did everything correctly as far as I can see.

At the present time the Local Master Browser is the host BARBARA.  Since you don't have any problems the command *smbtree *only returns the tree view of all the shares on the LAN.  If you want to see it work you can up the debug (to a max of 10).  Try *smbtree -d3 *to see some of the goodness.

Apple is becoming less BSD and Ubuntu is becoming less Debian.  Change, not necessarily progress, marches on.

---

### Post by tim042849 on 2011-11-12
> **capscrew said:**
> Interesting.  If I'm not mistaken SUN (oops, I mean Oracle) Solaris also wrote their own SMB/CIFS server.  You did everything correctly as far as I can see..
<Duh> I wish I knew precisely what made it start working. Do you think it was when I
used the smb URL (smb://198.168.1.104/tims)? If so, does that mean that both the hosts LINUS
and BARBARA recorded and stored parameters? If so, what would happen if some guest lappie at
the house logs into wifi when HPMINI is offline and grabs that IP? 
I am adding the entry to smb.conf on BARBARA as we speak.
> **capscrew said:**
> 
At the present time the Local Master Browser is the host BARBARA.  Since you don't have any problems the command *smbtree *only returns the tree view of all the shares on the LAN.  If you want to see it work you can up the debug (to a max of 10).  Try *smbtree -d3 *to see some of the goodness.

Apple is becoming less BSD and Ubuntu is becoming less Debian.  Change, not necessarily progress, marches on.
Well put.
thanks
tj

---

### Post by capscrew on 2011-11-12
> **tim042849 said:**
> <Duh> I wish I knew precisely what made it start working. Do you think it was when I
used the smb URL (smb://198.168.1.104/tims)? If so, does that mean that both the hosts LINUS
and BARBARA recorded and stored parameters? If so, what would happen if some guest lappie at
the house logs into wifi when HPMINI is offline and grabs that IP? 
I am adding the entry to smb.conf on BARBARA as we speak.

Well put.
thanks
tj

This needs a 2 part answer, so pull up a comfy chair... 

Samba consists of 2 daemons known as **smbd **and **nmbd** and a suite of tools for manipulation.

Part 1 -- The SMB/CIFS protocol uses NETBIOS names to map to IP addresses.  DNS uses IP addresses to map to hostnames.  This fundamental difference is overcome on Samba hosts *that use hostnames and DNS* by using the hostname and IP mapping in the /etc/hosts file to convert to a NETBIOS name.  This is what *nmbd *is for.

If you are using DHCP (a pool of IP addresses) then the /etc/hosts file is useless.  The IP address can change.  The *nmbd * understands that when you to explicitly declare the NETBIOS name in the smb.conf file there is no need to look at the /etc/hosts file as the NETBIOS name is already declared.  In fact you can declare the NETBIOS name with any Samba host.  The method of IP addressing (static of DHCP) becomes irrelevant.  Either way works -- static IP and hostname or DHCP and explicitly declaring the NETBIOS name.  FYI: hostname != NETBIOS name.    

Part 2 -- When a host with Samba is started it announces its NETBIOS name to the LAN and the Browse Master accepts or denies it.  If the name is accepted then that name is mapped to the announcing hosts IP address.  

The Master Browser(MB) can be any host that can participate in SMB browser election.  All Windows and Samba servers are participants.  I'll bet Stevie's products do too.  If you turn off the host that is performing as the MB an election would be held to elect a new MB and the list would be rebuilt.  This takes up to 15 minutes (another story).

I'll bet that it just took some time for the host HPMINI to be added.

If a different host with Samba is is handed the IP address that HPMINI used in the past, it still would be accepted if it had a different NETBIOS name.  If you think about it; this is a better solution for home (casual) users.  They just need to declare the NETBIOS name.  No futzing with static IP addressing, hostnames or DNS settings.

I hope this answers your questions.

-Cap

---

### Post by tim042849 on 2011-11-12
Thank you Cap.  Your answers are very good and my questions have been answered.
I just need to 8-) grok your response. Very informative thread!
tim

---

