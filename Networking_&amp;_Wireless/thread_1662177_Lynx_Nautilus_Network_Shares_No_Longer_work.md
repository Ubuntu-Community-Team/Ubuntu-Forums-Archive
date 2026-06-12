---
title: "Lynx Nautilus Network Shares No Longer work"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by pgmer6809 on 2011-01-07
HI,
I used to be able to browse my window machines from my Lynx ubuntu machine but this has stopped working for some reason.
The smbclient can still see the windows machine,
and Nautilus can still see the Windows workgroup, but when I try to open the windows workgroup it times out.
It looks like a security issue, in that the logs say stuff about not being able to log in. But none of my windows machines have that much security for internal connections, and besides it used to work.
below is output from smbclient (which works in a way) and from nmap showing open ports (looks ok).

Any ideas?

-----
here is the output of
```
smbclient -L delloffice
```

greg@shadow:~$ smbclient -L delloffice
Enter greg's password: 

	Sharename       Type      Comment
	---------       ----      -------
	DELL_OFF_PEN    Disk      
	MAC_EXG_DELL    Disk      
	PRINTER$        Disk      
	COLOR_LEXMAR    Printer   
	DEL_OF_DWNLD    Disk      
	DELLGREG        Disk      
	IPC$            IPC       Remote Inter Process Communication

	Server               Comment
	---------            -------
	DELLOFFICE           Dual boot W98/Xandros

	Workgroup            Master
	---------            -------
	MORSEHOUSE           DELLOFFICE
	WORKGROUP            ZORRO

here is the smbclient connecting successfully
```
/tmp$ smbclient -N //delloffice/dellgreg
```

smb: \> dir
  .                                   D        0  Thu Jun  8 12:56:58 2006
  ..                                  D        0  Thu Jun  8 12:56:58 2006
  desktop.bmp                         A   116414  Sun Apr 25 14:35:00 2004
  dad-2004-06-15-at-08-40.txt         A     6094  Tue Jun 15 13:17:46 2004
  solitaire-screenshot.bmp            A  1712610  Sun Mar 14 01:20:04 2004

and here is the output of a couple of nmaps: (windows first then Ubuntu)
greg@shadow:/tmp$ ```
sudo nmap -sS -sU -T4 192.168.0.5

```
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-01-07 15:16 PST
Interesting ports on 192.168.0.5:
Not shown: 1995 closed ports
PORT     STATE         SERVICE
135/tcp  open          msrpc
139/tcp  open          netbios-ssn
1027/tcp open          IIS
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
MAC Address: 00:C0:4F:40:F3:BF (Dell Computer)

Nmap done: 1 IP address (1 host up) scanned in 2.34 seconds
greg@shadow:/tmp$ ```
sudo nmap -sS -sU -T4 192.168.0.9

```
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-01-07 15:16 PST
Interesting ports on 192.168.0.9:
Not shown: 1993 closed ports
PORT     STATE         SERVICE
22/tcp   open          ssh
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
68/udp   open|filtered dhcpc
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

---

### Post by PatchesTheCaveman on 2011-01-07
Do you have Windows Live Essentials installed on the Windows machine you're trying to connect to?  Microsoft sometimes installs it as part of Windows Update so you might not even know you have it.

It changes the way Windows communicates via SMB just enough to break Samba.  There is more information and a couple workarounds here:
[http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

---

### Post by pgmer6809 on 2011-01-09
> **PatchesTheCaveman said:**
> Do you have Windows Live Essentials installed on the Windows machine you're trying to connect to?  Microsoft sometimes installs it as part of Windows Update so you might not even know you have it.

It changes the way Windows communicates via SMB just enough to break Samba.  There is more information and a couple workarounds here:
[http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

The windows machine has not changed. It is still Win98 :)!
I think the auto updates I have been installing for Lynx have hosed something.
Which is best, user authentication, or share authentication?

pgmer6809

---

### Post by luvshines on 2011-01-09
Are you able to connect from command line ie smbclient //... ?

User auth or share auth should come into picture when you make Samba shares on Lynx and connect them from another client.

---

### Post by pgmer6809 on 2011-01-10
> **luvshines said:**
> Are you able to connect from command line ie smbclient //... ?

User auth or share auth should come into picture when you make Samba shares on Lynx and connect them from another client.

Yes. See original post for sample output when connecting to smbclient.
Note that the cmd line method allows me to input a p/w if required for the windows machine, but the Nautilus method does not.
That is why I think it is a security issue, and something in the smb.conf file was changed when I d/l-ed some updates to Ubuntu.

---

### Post by PatchesTheCaveman on 2011-01-10
Perhaps Ubuntu has an old/invalid saved password.  That would explain why it doesn't work and why Nautlius doesn't ask for a password.

To check, go to System > Preferences > Password and Encryption Keys.

---

### Post by Morbius1 on 2011-01-10
When I first saw your nmap output I thought that the problem was obvious in that your Windows machine doesn't have port 445 ( SMB over IP ) open.

But later you said this was a Win98 machine. I've never used Win98 ( I started with WinNT 3.51 ). I don't know if Win98 used 445 for Samba. I'm wondering if Win98 is expecting a lanman password.

Try adding the following line to the global section of smb.conf:
```
client lanman auth = yes
```Then restart samba:
```
sudo service smbd restart
```It's just a guess on my part but it would fit your description. If there was a samba update it would revert to the default smb.conf unless you intervened and it would reset "client lanman" to the default of "no".

---

