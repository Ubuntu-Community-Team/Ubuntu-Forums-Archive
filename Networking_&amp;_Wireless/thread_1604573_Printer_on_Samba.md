---
title: "Printer on Samba"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-10-24
I'm always getting access denied when I try to connect at Windows/ Here's my smb.conf:

[http://paste.ubuntu.com/519237/](http://paste.ubuntu.com/519237/)

Printer sharing configuration near the bottom done with system-config-samba.

---

### Post by Morbius1 on 2010-10-24
Start by returning your security setting back to the default:

Change
> security = SHARETo
> security = userThen restart samba:
```
sudo service smbd restart
```

---

### Post by Oxwivi on 2010-10-24
What will it do? Well I did as you said in any case.

Access is still denied.

---

### Post by Morbius1 on 2010-10-24
Is your printer shared and published?

_Shared:_
Administration > Printing > Right Click the attached printer > Properties > Policies > Check Enabled, Accepting Jobs, and Shared

_Published_:
 Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

---

### Post by Oxwivi on 2010-10-24
Yep, that's elementary. I successfully shared it a while ago, but had to reformat. I regret not saving the config files...

Speaking of published, I can view the printer on Windows as I've stated. And the drivers for the printer are installed too.

---

### Post by Oxwivi on 2010-10-25
Bump!

---

### Post by Morbius1 on 2010-10-25
Does it prompt for a username and password or does it just give you an "access denied"?

Do you by any change have the same name on the windows machine that you have on the Linux machine?

Disable all firewalls and try it again.

Don't use samba. Instead connect to the printer directly. I have no idea what version of windows you are using so I'll give you the procedure for WinXP:

From the Printer Wizard select:  "Connect to a printer on the Internet or on a home or office network"

Then use the following format to connect to the printer:
```
http://192.168.0.100:631/printers/Linux-Printer_Name
```

---

### Post by Oxwivi on 2010-10-25
Actually, after adding a printer on Windows, any version (XP to 7), and double-clicking on the printer's icon will bring up the printer queue. And on the title bar, it's written access denied. And of course no print requests went through.

Nope, the names are widely different.

I didn't install any firewall software, so I'm unaware of any default firewall setting or a way to modify them.

Assuming, the numbers after http:// is the IP address, how do I find the the computer's IP address on the network?

---

### Post by Morbius1 on 2010-10-25
On the machine that has the printer attached to it run the following command:
```
ifconfig
```

---

### Post by Oxwivi on 2010-10-25
*scratches head* I don't see anything remotely like an IP address:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:95:8a:be:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:706 (706.0 B)  TX bytes:706 (706.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:3e:96:6a  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe3e:966a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50366782 (50.3 MB)  TX bytes:2165501 (2.1 MB)
```
Internet and network with wireless, by the way.

---

### Post by Morbius1 on 2010-10-25
> wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:3e:96:6a  
          [COLOR=Black]inet addr:[/COLOR]**[COLOR=Blue]192.168.2.3[/COLOR]**  Bcast:192.168.2.255  Mask:255.255.255.0
That's your ip address

---

### Post by Oxwivi on 2010-10-25
Did not work.

---

### Post by Morbius1 on 2010-10-25
This format:
```
http://192.168.0.100:631/printers/Linux-Printer_Name
```Will connect directly to the cups server located at a machine whose ip address is 192.168.0.100 at port 631 that has a printer named "Linux-Printer_Name".

If it doesn't then the first things I would check:

(1) cups isn't running
To find out:
```
sudo service cups status
```To start it:
```
sudo service cups start
```(2) Linux firewall is in the way

(3) Windows firewall is in the way

You can find out from Linux if the firewall settings are getting in the way by doing this:
```
sudo apt-get install nmap
```After it's installed run:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice:
Changing 192.168.0.100 to the ip address of the machine with the printer
And again with the ip address of the machine that wants to remotely access the printer.

---

### Post by Oxwivi on 2010-10-26
I had to reformat, and this is my current settings - please look through it before I go ahead with the firewall fix:

Samba settings from system-config-samba (I did not touch the smb.conf manually yet):
[B]
Samba share for printer
[/B]
[LIST]
[*]Directory: /var/lib/samba/printers
[*]Share name: print$
[*]Description: Printer Drivers
[*]Writable - checked
[*]Visible - checked
[*]Access: Allow access to everyone
[/LIST]
 
[B]Server settings
[/B]
[LIST]
[*]Workgroup: workgorup
[*]Description: %h (Samba, Ubuntu)
[*]Authentication mode: Share
[*]Authentication server: NIL
[*]Kerberos Realm: NIL
[*]Encrypt Passwords: Yes
[*]Guest account: No guest account
[/LIST]
 
Printing applet settings:

**Server Serrings**

[LIST]
[*]Show printers shared by other systems - checked
[*]Publish shared printers connected to his system - checked
[*]Allow printing from the Internet - checked
[*]Allow remote administration - checked
[*]Allow users to cancel any job (not just their own) - checked
[*]Save debugging information for troubleshooting - unchecked
[/LIST]
 
For now, Ubuntu system shows up on Windows, but not the printer. CUPS is functioning, successfully printed a test page. Also used [this fix]("http://ubuntuforums.org/showpost.php?p=9996340&postcount=5") at /etc/init/smbd.conf.

---

### Post by Morbius1 on 2010-10-26
> [B]Samba share for printer
[/B]
[LIST]
[*]Directory: /var/lib/samba/printers
[*]Share name: print$
[*]Description: Printer Drivers
[*]Writable - checked
[*]Visible - checked
[*]Access: Allow access to everyone
[/LIST]
If you're going to use Samba as a passthrough to CUPS then [print$] is not the share for printers. [printers] is the share for printers. When your system boots CUPS will start and make available a printer list that samba will read when it starts. That printer list is available through [printers]. You will have to make a modification to the [printers] share definition to allow guests to access a given printer by changing the line refereing to guest access to this:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
#   guest ok = no
[COLOR=Blue]    guest ok = yes[/COLOR]
;    read only = yes
    create mask = 0700> [B]Server settings
[/B]
[LIST]
[*]Workgroup: workgorup
[*]Description: %h (Samba, Ubuntu)
[*]Authentication mode: Share
[*]Authentication server: NIL
[*]Kerberos Realm: NIL
[*]Encrypt Passwords: Yes
[*]Guest account: No guest account
[/LIST]
 It's your decision of cource to run that way. My preference is to run with the current defaults of:
> security = user
map to guest = Bad User
guest account = nobody
> For now, Ubuntu system shows up on Windows, but not the printer.From the Ubuntu machine that has the printer run the following command and post the output:
```
smbtree
```

---

### Post by Oxwivi on 2010-10-26
So I change name of share name to [printers[ instead of [print$]? And then I should change guest ok to yes, I suppose.

I don't think the smbtree output is good:
```
$ smbtree
Enter oxwivi's password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
```

---

### Post by Morbius1 on 2010-10-26
>          So I change name of share name to [printers[ instead of [print$]? And then I should change guest ok to yes, I suppose.No. smb.conf has two printer related shares: [printers] and [print$].

Don't modify the [print$] at all.
Change the "guest ok" in [printers] to yes.

> Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
You're getting that error message because you insist on using share level security. My preference is to use the defaults:
> security = user
map to guest = Bad User
guest account = nobody                      


---

### Post by Oxwivi on 2010-10-26
I thought changing the security to share would make things easier. Oh well...

Anyway, I did not try the firewall thing yet, but still no improvement from doing the other things.

---

