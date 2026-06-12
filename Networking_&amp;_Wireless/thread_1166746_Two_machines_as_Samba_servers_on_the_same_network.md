---
title: "Two machines as Samba servers on the same network?"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-05-22
Hi all,

I have three computers. For convenience, let's call them:

Studio
Laptop
Lounge

Studio is running Xfce so I only want to access that from the other computers, not access other computers from it. Laptop and Lounge are running Gnome. Studio is accessible via samba from Laptop and Lounge faultlessly. Drag and drop files from one machine to the other, voila, no request for password or user. All permissions fine. Now ... 


* Problem 1: Lounge is visible on Laptop, but when I try to access one of the shared folders, it asks for the user name and password. I fill in and hit 'connect' and get:

> Opening "Shared Folder". You can stop this operation by clicking 'cancel'. ... assuming 'Shared Folder' is the name of the folder I am attempting to open. I click cancel (or just leave it for awhile) and it takes me back to the 'Enter Password' window.


* Problem 2: Laptop is not visible at all in 'Network' on Lounge. I have a feeling I may have them both set up as servers and this is the problem, but not really sure how to tell! Should I uninstall the samba package on one of them and just install smbfs?

I know I am entering the correct password for Lounge, so that is definitely not the problem.

Thanks in advance to any of you networking masterminds out there who may be able to help me out (and others!). Lounge and Laptop could access Studio 'out of the box' with no problems without me doing anything (that I can remember).

---

### Post by Bucky Ball on 2009-05-22
Okay, now Laptop is showing up on Lounge, so I go back to Laptop to create a shared folder, hit okay and get this message:

> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.Hmm. The plot thickens like grandad's gravy ... but at least I'm thinking that it is down to what is happening with the Laptop configuration. The other two machines seem to be behaving and the problems are now centred around Laptop and that problem now seems to be:


New Problem 1: Can't create share on Laptop.

:) :(

---

### Post by superprash2003 on 2009-05-22
what are you using for file sharing?? you could use NFS as its a  linux only network.. try accessing via ip ( do not depend on places->network )

---

### Post by Bucky Ball on 2009-05-22
Problem I have with that (and I tried) is router serves dynamic IP. I have tried changing it to static, but when I set one computer up, the rest disappear in the router admin GUI for some reason and it screws the network totally. I have a D-Link 704P which is otherwise great.

I also got somewhere with SSH but couldn't get the static IP working (that was the last time I tried). Samba just seems easier (and safer) for the moment (haven't got hours to spend right now cos end of semester exams and as setting a static IP tends to bring the network down and I need it reliably up right now ... ) and is working fine except for the glitch with the laptop, whatever that is.

Thanks for the idea, though. Any others? :)

---

### Post by Iowan on 2009-05-22
Does your router/DHCP server have the option to set up static leases? They have most of the advantages of static addresses, and reap some additional benefits like DNS  and gateway assignment.

---

### Post by Bucky Ball on 2009-05-22
Hi Iowan. I have not seen anything like that but will have a look in a little while. The only other way I thought of doing it was to write down the MAC addresses of two of the machines, then when I set a static address on one machine and the other two disappear (and I can't 'clone' the MAC addresses) I insert the details I have written down for the other two machines and see if I can force the issue that way.

But as I say, don't really want to risk that right now, have assignment due on Monday and another on Wednesday so need network up. :)

I will get to the bottom of this eventually!

BTW Superprash2003, NFS and SSH did seem to work okay when I tried them, just the dynamic IP address was the problem.

---

### Post by superprash2003 on 2009-05-23
try disabling dhcp server in your router ,and then setup static ip using your router's ip as the gateway ip

---

### Post by Bucky Ball on 2009-05-23
Set static IPs in network settings on each individual machine once DHCP server switched off on the router you mean?

For instance 'Lounge' machine may be set up like this using the 'Network' GUI:

IP: 192.168.0.5
Subnet Mask: 255.255.255.0
Gateway IP: 192.168.0.1 (the router's IP)

?

---

### Post by superprash2003 on 2009-05-24
yes..

---

### Post by Bucky Ball on 2009-05-25
Okay, I will try that in a week or so when the holidays start and I can safely break my network and install with the time to fix it again! lol I had some problems with setting the static IP on each individual machine last time I tried but realised as I was fixing the mess that I had set the router to static IP rather than dynamic and tried it. That caused some considerable confusion as you might imagine as the three machines tried to force there IPs on a router that was just sitting quietly but had no static IPs to set. So this time I will have both static and dynamic *dis*-abled on the router before I set up the machines. :)

I am still bamboozled though, with the samba issue (and would prefer to use samba rather than terminal - any suggestions welcome). Why is the laptop having these problems? I think maybe a permissions thing.

I discovered last night, using the names of machines given previously, that when I am looking at my network on Laptop, both Laptop and Studio are there. Drag a file from Studio and drop it on the Laptop desktop; no problem. Grab a file from Laptop and drop it into a folder on Studio on the network and no go. Hmm. 

One other differences, and it may be more significant than I'm thinking, is that Studio and Lounge, which are problem free and communicate fine, are both dual-booting with XP. Laptop is dual-booting with Vista (don't blame me, I had no choice as HP don't make XP drivers for Laptop as I discovered after immediately loading XP onto it when it arrived ... only to find no hardware worked ... doesn't seem like it should be legal to do that to me but money talks).

I know the two OS are on totally different partitions and never the twain shall meet etc, but ... hunting for any differences at the moment.

---

### Post by dmizer on 2009-05-25
Try this: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Bucky Ball on 2009-06-02
Okay, I just discovered something really weird people, and particularly those of you who have been following this. Yes, Lappy does show up on all the machines as Lappy, but the real name of the laptop on the network is actually:

```
HPLappy
```Not to be seen anywhere. But Lappy is! Now for the weird part; I go to work on Studio, boot into the XP install and check 'Network Places', there's Lappy but it is like this:

> CAD architects, Stockholm . East 32nd st, 34th fl (Lappy)Followed by the other two computers on the network!!!!!

I am now officially bamboozled. That could be at the bottom of all my problems, but what the hell is happening there? I can't find any reference anywhere else to this on either machine! When I switch the laptop off (HPLappy), Lappy vanishes from the network, so I know it is the laptop that is being identified as Lappy instead of what it should be and not a 'ghost' machine (or in the machine!).
 
Is someone stealing my identity? There doesn't seem to be any problem with our usage meter, just clagging up my network. How to get rid of this problem, delete from the network and reassign as correct name???

---

### Post by dmizer on 2009-06-02
I reviewed this thread (it's been a while) and couldn't determine if HPLappy was a Windows computer or a Linux box. If it's a Windows computer, please refer to this document: [http://support.microsoft.com/kb/295017](http://support.microsoft.com/kb/295017)

If it's a Linux computer, please post the /etc/samba/smb.conf file from HPLappy.

---

### Post by Bucky Ball on 2009-06-03
Thanks dmizer, that is just the file I was looking I guess as the anomaly is right there at the top of the file:


```
[global]
    netbios name = Lappy
    server string = CAD architects, Stockholm. East 32nd st, 34th floor
    workgroup = HOME
    security = user
    hosts allow = 192.168.0.1
    interfaces = 127.0.0.1/8 192.168.0.0/24
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = /etc/printcap
    load printers = no
    cups options = raw
;    printing = cups
    guest account = smbguest
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 8
    password level = 8
;    encrypt passwords = yes
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
    
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
;    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
    username map = /etc/samba/smbusers
;    smb passwd file = /etc/samba/smbpasswd
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no

wins support = no
[homes]
    comment = Home Directories
    path = /home
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    share modes = no
    locking = no

;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
;    available = yes
;    guest ok = no
;    printable = no
[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = no
;    guest ok = no
    printable = yes
    share modes = no
    locking = no

;    available = yes
;    browseable = yes
[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gsambadpdf %s %u
    lpq command = 
    lprm command = 

;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no

[fatso]
path = /media/fatso
available = yes
browsable = yes
public = yes
writable = no

[bigboy]
path = /media/bigboy
available = yes
browsable = yes
public = yes
writable = no
```Maybe you can help me to figure that out. I obviously need to change a few things;

netbios name to HPLappy perhaps? And get rid of what is in the server string and replace with? Maybe I'll compare with a samba.conf from one of the other machines that's networking okay.

I have a lot more time to spend on this come tomorrow night so I will read up on some of the other links also ...

Thanks :)

ps: All three machines dual-boot a Ubuntu 'blend' and a flavour of Windows; Vista on the laptop and XP other two (rarely used).

---

### Post by dmizer on 2009-06-03
Yes, I highly suggest you compare it with one that works correctly. That smb.conf file seems overly complex. The server string option isn't even necessary, you can remove it if you like.

Before you edit your smb.conf, make a backup so you can revert to the old one if necessary:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-old
```

To edit the smb.conf file, you can enter this command at the terminal:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by Bucky Ball on 2009-06-03
```
[global]
;    netbios name = lounge
    server string = 
    workgroup = home
    security = domain
    hosts allow = 127. 192.168.0.
    interfaces = 127.0.0.1/8 192.168.0.0/24
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = /etc/printcap
    load printers = no
    cups options = raw
;    printing = cups
;    guest account = nobody
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 8
    password level = 8
;    encrypt passwords = yes
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
    wins server = 
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
;    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
    enable spools = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
;    smb passwd file = /etc/samba/smbpasswd
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
    usershare owner only = false
    password server = 192.168.0.1
;    guest ok = no

[homes]
    comment = Home Directories
    path = /home
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    share modes = no
    locking = no

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    share modes = no
    locking = no

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    writeable = yes
;    available = yes
;    browseable = yes
;    printable = no
    locking = no
    create mode = 0600
    directory mask = 0700
    valid users = Ignoring unknown parameter "enable spools"
, Lappy$, Unknown parameter encountered, anna, root, smbguest

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    share modes = no
    locking = no

[pdf-documents]
    path = /home/pdf-documents
    comment = Converted PDF Documents
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gsambadpdf %s %u
    lpq command = 
    lprm command = 

[LoungeShare]
    path = /home/anna/Desktop/LoungeShare
    comment = Lounge
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    share modes = no
    locking = no

[MusicVid]
    path = /media/musicvid
    comment = Lounge
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    share modes = no
    locking = no
```

That is from Lounge. As you can see, there are some glaring differences. As you mention, server string = empty. HOME is home.

Getting late here and I should be studying, but will begin experimentation when I get home tomorrow.

---

### Post by Bucky Ball on 2009-06-05
After emptying the server string and changing from 'Lappy' to 'HPLappy' (which matches what I have setup in the 'Network' GUI, this is what I get when attempting to share a folder. No machines appear on my network, including HPLappy, the one I'm working on, or Lounge, which is currently switched on:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.'

HOME is the correct domain incidentally.

So, quick step backwards and slightly to the side.

---

### Post by Bucky Ball on 2009-06-07
Update: 'Studio' is in the process of dying and can't figure which bit of hardware it is. I had 'Lounge' and 'HPLappy' on but in 'Network' on both, there was nothing, empty.

Getting a little frustrated, thought I might change the scene and work on trying to diagnose the problem with Studio for awhile and lo and behold, the thing actually booted and I got to a desktop. Maybe I'll check the network. Lo and behold, Studio, Lounge and HPLappy are all there on all machines! Everything can drag and drop from and to Studio, but Lounge and HPLappy still have problems with each other; even though they can see each other, they can't see shared folders.

Question 1: I'm figuring I have Studio (desktop) set up as a Samba Server, as when it crashed again and I switched it off, the network became empty again.

Question 2: If I can only have one server (and I'm wondering if you can have two on the same LAN), I would prefer it was HPLappy. How would I change this?

Question 3: Would I perhaps be better off uninstalling everything Samba and starting again from scratch, following a tutorial on setting up a LAN with Samba and *getting it right from the start?* This has all been a bit ad hoc over the last year or so with me having a nibble at the conundrum on occasion, so now I probably have a web of confusion.

Cheers :)

---

### Post by Bucky Ball on 2009-06-14
Well, this is where I'm up to. Now that I have had a bit more time to check things out and learn a bit more about samba, I realise there are some problems. I have one server and it is Studio. This I don't want. As this problem has changed a bit, I have posted here:

[http://ubuntuforums.org/showthread.php?t=1187251](http://ubuntuforums.org/showthread.php?t=1187251)

I want to uninstall samba on all three machines, start from the beginning and attempt to get it right this time.

Thanks so far. :)

---

