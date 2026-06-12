---
title: "Home Network with PC as server HELP!"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by eddie3000 on 2010-12-28
Hello folks! This is a great forum. :D

First I would like make clear that I am a newbie with ubuntu. I will explain what I want to do at home, and I would appreciate any help or information on the subject.

I am tired of carrying my external HDDs around home from one PC to another, so I thought it might be a good idea to have an old computer stacked with several discs as a server, maybe using ubuntu server. It doesn't have a graphical interface, which might make it complicated for me. Can I use a desktop ubuntu instead? 

I also want to have access to the server from any computer on my network, but I want to have to type in a password or something. As all computers are also going to be connected to the internet I want the server to be secure.

I haven't got much experience with samba either. I have managed to share folders between computers using ubuntu and windows xp, but I sometimes get asked for a user and password. When this happens, no matter what I enter it won't work. I have read that you have to add users and passwords in samba, but how? Do I have to enter all the users and passwords of all the computers on all the computers? Can I just create one user and password for all computers? How is this done with ubuntu server?

Basically, I would like to have a server (or normal computer) so I can access all my documents, photos and videos from all the computers in my home network, also with access to the internet, and a passsword on the server to keep unauthorized users out. And I would like it all to work with ubuntu if possible, and occasionally windows xp.

Does anybody know about a simple and plain tutorial for dummies on how to use samba and all of it's features? A tutorial on home networks would also be a must in my case, as I know pretty little and when I come across a problem, I tend to solve things by trying different combinations in my setup without really knowing what I'm doing.;)


It would be great if anybody can point me in the right direction.  It would also be nice to hear different approaches, setups or ideas for something like this.

THANK YOU!

---

### Post by spiky001 on 2010-12-28
Hi I have the same thing here I have installed the normal Desktop version of Ubuntu, The rest is not that hard to set up,  A few things need to be installed I,E ssh and I have just installed Remmina which takes care of Remote desktop, Dose this sound like the sort of thing your looking for?

---

### Post by mmad on 2010-12-28
I recently set up an ubuntu server, and because its doubling up as a media centre that my brothers would be using, I added a GUI too.

I installed ubuntu server, then the ubuntu desktop on top of it and then I installed webmin. 

If its just a file server, then don't waste the storage/ram on the GUI and go straight to webmin.

Webmin is an absolutely brilliant interface which allows me to get used to using my server quickly. It lets you add samba shares, monitor/kill processes and install updates to the server remotely. 

[http://www.webmin.com/](http://www.webmin.com/)

To connect your server, I'd suggest a wired ethernet connection to your router, then the router can handle all the hard work for you.

---

### Post by eddie3000 on 2010-12-28
I'll look at webmin to see if I can get it going. But I would like to know if, once I get ubuntu server going, I can create one single user with one password or I have to create a user per computer. I have a multimedia PC in the sitting room, an old computer for internet browsing, two laptops and another computer in the garage (yes, it may seem an odd place to have one).
And one more question, how safe is would ubuntu server be from external intruders? I doubt I have anything anyone may be interested in, but it's just a paranoid feeling I have. And I guess many learning hackers may just have a go for fun. I wouldn't like people seeing my photos wothout my permission.

---

### Post by spiky001 on 2010-12-28
Do you have a router that should have an inbuilt firewall, There is a firewall built into ubuntu UFW but would need to be set up.  As for webmin I have not used it so cant help with that, If you had one user/password that would mean only one person at a time can log in to server, would that cause a problem?

---

### Post by mmad on 2010-12-28
> **eddie3000 said:**
> I'll look at webmin to see if I can get it going. But I would like to know if, once I get ubuntu server going, I can create one single user with one password or I have to create a user per computer. I have a multimedia PC in the sitting room, an old computer for internet browsing, two laptops and another computer in the garage (yes, it may seem an odd place to have one).
And one more question, how safe is would ubuntu server be from external intruders? I doubt I have anything anyone may be interested in, but it's just a paranoid feeling I have. And I guess many learning hackers may just have a go for fun. I wouldn't like people seeing my photos wothout my permission.

You only need a single username/password combination to access from any of your computers. As for getting webmin going, its simple - just install it and make your default account - done :D. I for one was surprised how easy it was. As for the server security - well I cant say for sure but as this is a prominent server distribution I would assume that it is quite secure. Hope that helps.

---

### Post by eddie3000 on 2010-12-28
Thanks guys!! I will have a go and try to get it going. It'll take me some time, but I'll get back here to tell you if all goes well or not. I still have to get scrap parts for the server.
As far as I know, my router does not have a built in firewall. If you think it is a good thing to have I could look at the possiblitiy of getting one. At the moment I have 3 routers, the sort you get free with internet companies when you purchase an internet connection.
Thanks again and Happy New Year to you all.

---

### Post by eddie3000 on 2010-12-28
I must admit that webmin looks like a very interesting option. The tutorial seems to be very good indeed, and it looks easy. Thanks.

---

### Post by drdos2006 on 2010-12-28
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by headvampyre@hotmail.co.uk on 2010-12-28
Hi, if you need help setting up sambe, ill post my configuration (smb.conf), just edit the e.g. 
netbios name = MYSERVER
workgroup = MYDOMAIN
and stuff like that.
my smb.conf:

[global]
    netbios name = MYSERVER
    disable netbios = No
    workgroup = MYDOMAIN
    realm = MYREALM.COM
    server string = You Are Logged On To %L Via %m(%I)
    allow trusted domains = Yes
    paranoid server security = Yes
    server signing = Yes
    server schannel = Yes
    client signing = Yes
    client schannel = Yes
    smb encrypt = Yes
    use spnego = Yes
    client use spnego = yes
    getwd cache = Yes
    oplocks = Yes
    level2 oplocks = Yes
    block size = 4096
    deadtime = 10
    announce as = NT Server
    announce version = 4.9
    follow symlinks = Yes
    nt pipe support = Yes
    nt status support = Yes
    enable spoolss = Yes
    local master = Yes
    domain master = Yes
    domain logons = Yes
    preferred master = Yes
    os level = 65
    logon path = \\MYSERVER\Settings$\%U
    logon drive = M:
    logon home = \\MYSERVER\MyDocs$\%U
    logon script = Logon.bat
    security = user
    idmap gid = 10000-20000
    idmap uid = 10000-20000
    idmap backend = ldap
    idmap cache time = 600
    wins support = Yes
    wins proxy = Yes
    dns proxy = Yes
    name resolve order = wins bcast
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind refresh tickets = Yes
    winbind reconnect delay = 60
    winbind separator = @
    winbind cache time = 300
    winbind offline logon = No
    winbind nss info = Yes
    hostname lookups = Yes
    hosts allow = 192.168.0. 192.168.1. 
#   Remember to put your subnet in hosts allow = - Applications #   > Terminal > ipconfig > the number that is like ww.xx.yy.zz
#   copy the first three numbers and put a . after (no spaces)
    machine password timeout = 60
    lm announce = No
    printcap name = cups
    printing = cups
    printcap cache time = 500
    use client driver = Yes
    cups options = "raw media=a4"
    load printers = Yes
    cups connection timeout = 15
    show add printer wizard = Yes
    passdb backend = tdbsam
    passwd program = /usr/sbin/smbldap-passwd "%u"
    passwd chat = *New*password* %n\n *Retype*new*password* %n\n *all*authentication*tokens*updated*
    add user script = /usr/sbin/useradd -m '%u'
    delete user script = /usr/sbin/userdel %u
    add group script = /usr/sbin/groupadd -p '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/groupmod -m '%u' '%g'
    delete user from group script = /usr/sbin/groupmod -x '%u' '%g'
    set primary group script = /usr/sbin/usermod -g '%g' '%u'
    add machine script = /usr/sbin/useradd -g machines -d /usr/lib/nobody %u
    add share command = /usr/local/bin/addshare
    message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m"
    case sensitive = Yes
    preserve case = Yes
    short preserve case = Yes
    nt acl support = Yes
    map acl inherit = Yes
    acl compatibility = win2k
    acl map full control = Yes
    acl check permissions = Yes
    store dos attributes = Yes
    ea support = Yes
    obey pam restrictions = No
    unix password sync = No
    pam password change = Yes
    encrypt passwords = Yes
    update encrypted = No
    null passwords = No
    guest ok = No
    map to guest = Bad User
    guest account = nobody
    time server = Yes
    admin users = @root
    map to guest = Bad User
    client plaintext auth = No
    lanman auth = No
    client lanman auth = No
    ntlm auth = No
    client ntlmv2 auth = Yes
    guest ok = Yes
    max protocol = SMB2
    min protocol = LANMAN2
    interfaces = eth0 eth1 wlan0 wlan1 lo
    bind interfaces only = Yes
    socket options = TCP_NODELAY IPTOS_LOWDELAY  SO_RCVBUF=65536 SO_SNDBUF=65536
    enhanced browsing = Yes
    administrative share = Yes
    host msdfs = Yes
    veto files = /*.divx/VIRUS.*/Virus.*/virus.*/*.eml/*.nws/*.{*}/
    hide dot files = Yes
    hide unreadable = Yes
    hide files = /*.java/*.cpp/*.c/*.dll/thumbs.db/desktop.ini/
    delete readonly = No
    follow symlinks = Yes
    utmp = Yes
    log level = 1
    debug level = 1
    max log size = 250
    log file = /etc/samba/SambaLog.log
    panic action = /usr/share/samba/panic-action %d
    syslog = 0
    debug timestamp = Yes
    read raw = Yes
    write raw = Yes
    wide links = No
    max xmit = 65536
    timestamp logs = False
    dos filetimes = No
    dos filetime resolution = Yes
    fake directory create times = Yes
    default case = lower
    dos charset = UTF-8
    unix charset = UTF-8
    display charset = UTF-8
    mangling method = hash2
    template homedir = /home/DOMAINS/%L/%U
    template shell = /dev/null
    unix extensions = Yes
    usershare allow guests = No
    usershare max shares = 1000000000
    usershare owner only = Yes
    usershare path = /MYDOMAIN/Shares/UserShares

[netlogon]
    path = /MYDOMAIN/Shares/LogonScripts
    volume = NETLOGON
    comment = Logon Script Share
    msdfs root = Yes
    read only = No
    guest ok = Yes
    writeable = Yes
    write list = @root
    browseable = No
    locking = No
    fstype = FAT
    nt acl support = Yes
    store dos attributes = Yes
    valid users = %U

[SYSVOL]
    path = /MYDOMAIN/Shares/SYSVOL
    volume = SYSVOL
    comment = SYSVOL$
    msdfs root = Yes
    read only = No
    guest ok = Yes
    writeable = Yes
    write list = @root
    browseable = No
    locking = No
    fstype = FAT
    nt acl support = Yes
    store dos attributes = Yes
    valid users = %U

# Printing Shares
[print$]
    path = /MYDOMAIN/Shares/Install/Drivers/Printers
    comment = Printer Drivers
    volume = PRINTDRVS
    browseable = Yes
    guest ok = No
    read only = Yes
    write list = @root, @serveradmin, @wheel, @root
    valid users = %U
    force user = %U

[printers]
    path = /MYDOMAIN/Shares/Printing/Machines
    comment = Printers On %L
    volume = PRINTERS
    browseable = No
    printable = Yes
    public = No
    writeable = Yes
    guest ok = No
    valid users = %U
    force user = %U
# End Of Printing Shares

[Settings$]
    path = /MYDOMAIN/mestizaje.org/Profiles/Settings
    volume = USERDATA
    comment = My Settings
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[MyDocs$]
    path = /MYDOMAIN/Profiles/MyDocs
    volume = USERDOCS
    comment = My Documents
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[AppData$]
    path = /MYDOMAIN/Profiles/AppData
    volume = APPLICATIONDATA
    comment = APPLICATIONDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[Desktop$]
    path = /MYDOMAIN/Profiles/Desktop
    volume = DESKTOPDATA
    comment = DESKTOPDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[StartMenu$]
    path = /MYDOMAIN/Profiles/StartMenu
    volume = STARTMENUDATA
    comment = STARTMENUDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[Cookies$]
    path = /MYDOMAIN/Profiles/Cookies
    volume = COOKIEDATA
    comment = COOKIEDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[Favourites$]
    path = /MYDOMAIN/Profiles/Favourites
    volume = IEFAVDATA
    comment = IEFAVDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[NetHood$]
    path = /MYDOMAIN/Profiles/NetHood
    volume = NETDATA
    comment = NETDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[PrintHood$]
    path = /MYDOMAIN/Profiles/PrintHood
    volume = PRINTDATA
    comment = PRINTDATA
    read only = No
    writeable = Yes
    create mask = 0600
    directory mask = 0700
    profile acls = Yes
    browseable = No
    guest ok = No
    printable = No
    hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
    fstype = NTFS
    locking = No
    csc policy = disable
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

[Shared]
    path = /MYDOMAIN/Shares/Shared
    volume = SHAREDAREA
    comment = Shared Area On %L
    valid users = %U
    msdfs root = Yes
    read only = No
    writeable = Yes
    browseable = Yes
    fstype = NTFS
    locking = No
    nt acl support = Yes
    store dos attributes = Yes
    vfs object = recycle
    recycle: config-files = /etc/samba/samba-recycle.conf

samba-vscan-clamav.conf:

[samba-vscan]
max file size = 0 
verbose file logging = no  
scan on open = yes
scan on close = yes 
deny access on error = yes
deny access on minor error = yes
send warning message = yes
infected file action = quarantine
quarantine directory  = /MYDOMAIN/CLAMAV/Cb7@1-3
quarantine prefix = vir-
max lru files entries = 100
lru file entry lifetime = 5
exclude file types = 
clamd socket name = /var/run/clamd
libclamav max files in archive = 1500
libclamav max archived file size = 5120000
libclamav max recursion level = 5

samba-recycle.conf:

name = .recycle
mode = KEEP_DIRECTORIES|VERSIONS|TOUCH
maxsize = 0
exclude = *.tmp|*.temp|*.o|*.obj|~$*|*.~??
excludedir = /tmp|/temp|/cache|/MYDOMAIN/CLAMAV/Cb7@1-3
noversions = *.doc|*.xls|*.ppt


Okay, thats my samba configuration. Remember to replace anything like MYSERVER, MYDOMAIN etc. etc. with the real server name and the name of the workgroup/domain. you also need to create every directory shown, execpt the \\MYSERVER\ directories. you can change the permissions, and samba should automatically synchronize with the unix password databases. This is a configuration for a domain network and can be used for authentication accross windows(the easy option) and if you try you can implement the authentication into linux and Mac. For the username use MYSERVER\myusername, MYDOMAIN\myusername or MYSERVERIPADDRESS\myusername. Best of luck with getting this to work, remember to create the file contents ive show in /etc/samba (dont add the colon to the end of the file name).
Jacob :)

---

### Post by headvampyre@hotmail.co.uk on 2010-12-28
Oh, i almost forgot - to install samba use this command: sudo apt-get install samba samba-common samba-common-bin smbfs acl libpam-smbpass

---

### Post by eddie3000 on 2010-12-29
That's a big .conf file you got Headvampyre! Or at least it looks big to me. Figuring out what each line means is going to take me quite a bit of time googling around, and it'll be very instructive too. 

The webmin tutorial recommends installing a debian version of linux. Wouldn't that include a samba package?

Though it seems fairly straightforward, as a newbie I probably won't be capable of solving any problems I come across, so I will please ask everybody to be patient. I hope not to bore you with silly questions.

I have seen that there are different debian images available. Some are marked as i386, AMD, ARM, PowerPC and so on. Depending on the scraps I can get to build my server, I will probably end up with either an AMD or Intel processor. Does this mean I should download the AMD or i386 version depending on the processor I use?? :confused: If I can get to choose, what processors would be best and why?

Thanks!

---

### Post by kevinthecomputerguy on 2010-12-30
Headvampyre-
 
Thanks for that post, we can all learn alot from your samba conf, Its easy to see there is years worth of knowledge behind that one!
 
-KevinTheComputerGuy

---

### Post by perspectoff on 2010-12-31
> **eddie3000 said:**
> Hello folks! This is a great forum. :D

First I would like make clear that I am a newbie with ubuntu. I will explain what I want to do at home, and I would appreciate any help or information on the subject.

I am tired of carrying my external HDDs around home from one PC to another, so I thought it might be a good idea to have an old computer stacked with several discs as a server, maybe using ubuntu server. It doesn't have a graphical interface, which might make it complicated for me. Can I use a desktop ubuntu instead? 

I also want to have access to the server from any computer on my network, but I want to have to type in a password or something. As all computers are also going to be connected to the internet I want the server to be secure.

I haven't got much experience with samba either. I have managed to share folders between computers using ubuntu and windows xp, but I sometimes get asked for a user and password. When this happens, no matter what I enter it won't work. I have read that you have to add users and passwords in samba, but how? Do I have to enter all the users and passwords of all the computers on all the computers? Can I just create one user and password for all computers? How is this done with ubuntu server?

Basically, I would like to have a server (or normal computer) so I can access all my documents, photos and videos from all the computers in my home network, also with access to the internet, and a passsword on the server to keep unauthorized users out. And I would like it all to work with ubuntu if possible, and occasionally windows xp.

Does anybody know about a simple and plain tutorial for dummies on how to use samba and all of it's features? A tutorial on home networks would also be a must in my case, as I know pretty little and when I come across a problem, I tend to solve things by trying different combinations in my setup without really knowing what I'm doing.;)


It would be great if anybody can point me in the right direction.  It would also be nice to hear different approaches, setups or ideas for something like this.

THANK YOU!

My opinion:

Buy an inexpensive 1 Tb NAS for about $159 (like the Buffalo Linkstation, Iomega Home Media Network NAS, or something similar) and then use it for all your network storage. You can access it from Windows, Linux, or Mac computers. Will take all of a day to configure.

Doing it from scratch (like FreeNAS at [http://freenas.org](http://freenas.org)) can be done, but if you want to be up and running quickly, just buy one.

I tried what you want to do and that's the conclusion I came to.

---

