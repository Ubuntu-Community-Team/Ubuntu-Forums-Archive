---
title: "Smbclient connects to share but Gigolo can't"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by kpuz on 2012-05-10
I'm having a problem with Gigolo which is giving me trouble with connecting to samba shares on my work network.  It prompts for password even after I enter the correct one.  I am also adding the domain name and server names properly but it doesn't connect.  
However, I am able to connect to the shareusing smbclient using
smbclient \\\\server\\share -U username -W domain mypassword

Can anyone help me with this.  I don't know if the problem is with gigolo or not.  Before upgrading to Xubuntu 12.04 I was able to connect to this share.  Any help is apprecieated

---

### Post by kpuz on 2012-05-10
Some more information:
Connecting with same credentials while running Nautilus fails
Connecting with same credentials while booted into Linux Mint (on another partition) succeeds.

Seems to me like whatever package both nautilus-server-connect and gigolo require is not behaving as it should.  Any help?

---

### Post by Jose Catre-Vandis on 2012-05-12
Tested this on my boxes. (Xubuntu 12.04 desktop & Ubuntu 12.04 server)

All seems to work OK.

Ignored domain box. 

1. Tried first to connect using the admin login for the server. This works. 

2. Next tried as user (no passwords created on server). This worked. 

3. Tried without entering a user, this also worked.

So it does all work as expected. I know this doesn't fix it for you but it may help in finding out what is wrong?

---

### Post by Toz on 2012-05-12
@kpuz, Do you have the package **gvfs-backends** installed?

---

### Post by kpuz on 2012-05-12
Hi Toz, 
I do have the gvfs-backends package installed.

I keep getting a password prompt after putting in the server/share/domain information.  My password has one uppercase letter in it.  I'm wondering if there is a problem with support for uppercase letters in whatever service gigolo is a frontend is for.  I will have to do some major testing by setting up a home samba server to figure this out.

---

### Post by Toz on 2012-05-12
> **kpuz said:**
> Hi Toz, 
I do have the gvfs-backends package installed.

I keep getting a password prompt after putting in the server/share/domain information.  My password has one uppercase letter in it.  I'm wondering if there is a problem with support for uppercase letters in whatever service gigolo is a frontend is for.  I will have to do some major testing by setting up a home samba server to figure this out.

My password is a combination of uppercase, lowercase, numberic and punctuation characters and it works fine. Does either your share name or workgroup name have a space in it? Can you post back a screen shot of the gigolo settings page for the bookmark?

Gigolo is a front-end to gvfs. What happens if you try to mount it manually:
```
gvfs-mount smb://server/share
```
...and error messages?

---

### Post by kpuz on 2012-05-14
Hi Toz,
I've attached the screen for gigolo with my credentials.

Here's the output of smbclient -L \\\\server\\share -U khan -W slri_lan1
```

Sharename       Type      Comment
	---------       ----      -------
	C$              Disk      Default share
	computing       Disk      Support Team
	Cordes_lab      Disk      Cordes Lab
	evs-labdata1-iso Disk      Share associated with Virtual Volume evs-labdata1-iso
	gingras_lab     Disk      gingras_lab
	Grynpas_lab     Disk      Grynpas Lab
	IPC$            IPC       Remote IPC
	Lye_lab         Disk      Lye Lab
	McNeill_lab     Disk      McNeill_lab
	offices         Disk      Offices
	Okamoto_lab     Disk      Okamoto Lab
	Roder_lab       Disk      Roder Lab

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

Here's the error message I get for mounting via command-line:

gvfs-mount //server/share

```
Error mounting location: Failed to mount Windows share
```

gvfs-mount //server/share -U khan -W slri_lan1

```
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: Failed to mount Windows share
```

---

### Post by Toz on 2012-05-14
Is gvfs-fuse installed?
```
apt-cache policy gvfs-fuse
```

Have you by chance installed any other fuse file systems?
```
dpkg -l | grep fuse
```

Is your account a member of the fuse group?
```
groups
```

Is gvfs-fuse-daemon running for your account?
```
mount | grep gvfs
```

Maybe try reintalling gvfs-fuse and gvfs-bin:
```
sudo apt-get install --reinstall gvfs-fuse gvfs-bin
```

---

### Post by kpuz on 2012-05-14
Reinstalling didn't fix the issue.

apt-cache policy gvfs-fuse
```
gvfs-fuse:
  Installed: 1.12.1-0ubuntu1
  Candidate: 1.12.1-0ubuntu1
  Version table:
 *** 1.12.1-0ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

dpkg -l | grep fuse
```
ii  fuse                                                        2.8.6-2ubuntu2                          Filesystem in Userspace
ii  gvfs-fuse                                                   1.12.1-0ubuntu1                         userspace virtual filesystem - fuse server
ii  libfuse2                                                    2.8.6-2ubuntu2                          Filesystem in Userspace (library)
```

groups
```
mustafa adm cdrom sudo dip plugdev lpadmin sambashare
```

mount | grep gvfs
```
gvfs-fuse-daemon on /home/mustafa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mustafa)

```

---

### Post by LewisTM on 2012-05-14
A wild guess: once I found that all of my gvfs problems were caused by my ~/.gvfs dir being owned by root.
These commands would show you
```

sudo umount ~/.gvfs
ls -al ~|grep gvfs
```
If this is the case you will have to change the owner, then execute
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```

---

### Post by kpuz on 2012-05-14
Hi LewisTM,
The .gvfs folder is owned by me.  Thanks for the help.

> **LewisTM said:**
> A wild guess: once I found that all of my gvfs problems were caused by my ~/.gvfs dir being owned by root.
These commands would show you
```

sudo umount ~/.gvfs
ls -al ~|grep gvfs
```
If this is the case you will have to change the owner, then execute
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```

---

### Post by Toz on 2012-05-14
> **kpuz said:**
> 
groups
```
mustafa adm cdrom sudo dip plugdev lpadmin sambashare
```


Try adding your account to the fuse user group.

---

### Post by kpuz on 2012-05-16
I ran:
sudo usermod -aG fuse mustafa

then:
less /etc/group | grep fuse

shows me:
```
fuse:x:105:mustafa
```

group shows me as a member of fuse group.

But the problem persists.  I keep getting password prompt even though I enter correct password.

---

### Post by kpuz on 2012-05-16
Some more information:
Xubuntu 12.04-64bit live cd: same problem
Ubuntu 12.04-64bit live cd: same problem

---

### Post by Toz on 2012-05-16
Not sure if you did, but you need to log out and back in for the group to take effect.

---

### Post by Toz on 2012-05-16
> **kpuz said:**
> Some more information:
Xubuntu 12.04-64bit live cd: same problem
Ubuntu 12.04-64bit live cd: same problem

Now this is interesting. What is the actual name of your server and share (if you don't mind sharing)?

---

### Post by Toz on 2012-05-16
Can you also try this:

In one terminal window, run:
```
GVFS_SMB_DEBUG=60 /usr/lib/gvfs/gvfsd -r
```

In another terminal window, run:
```
gvfs-mount //server/share -U khan -W slri_lan1
```

A bunch of debug code will display in the first terminal window. Please post that debug code back here.

---

### Post by LewisTM on 2012-05-16
> **kpuz said:**
> Here's the error message I get for mounting via command-line:

gvfs-mount //server/share

```
Error mounting location: Failed to mount Windows share
```

gvfs-mount //server/share -U khan -W slri_lan1

```
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
Error mounting location: Failed to mount Windows share
```
Back to these commands, I think they have the wrong syntax so the errors are misleading.

The right command should be:
```
gvfs-mount smb://khan@labdata1.ad/Okamoto_lab
```

---

### Post by kpuz on 2012-05-17
> **Toz said:**
> Now this is interesting. What is the actual name of your server and share (if you don't mind sharing)?

Server: labdata1.ad
Share: Okamoto_lab

I did restart the computer but problem was still there.  Please note: I have been trying to connect using gigolo this whole time and not really with gvfs-mount command line option.

---

### Post by kpuz on 2012-05-17
> **LewisTM said:**
> Back to these commands, I think they have the wrong syntax so the errors are misleading.

The right command should be:
```
gvfs-mount smb://khan@labdata1.ad/Okamoto_lab
```

I agree, my syntax was all wrong.  With new syntax that you provided, is there a way to add domain information with the username?  

When using gvfs-mount smb://khan@labdata1.ad/Okamoto_lab
I get prompted for the Domain and then the password.  I input the password and domain but I keep getting reprompted.

---

### Post by kpuz on 2012-05-17
> **Toz said:**
> Can you also try this:

In one terminal window, run:
```
GVFS_SMB_DEBUG=60 /usr/lib/gvfs/gvfsd -r
```

In another terminal window, run:
```
gvfs-mount //server/share -U khan -W slri_lan1
```

A bunch of debug code will display in the first terminal window. Please post that debug code back here.

Here's the debug code after fixing the gvfs-mount syntax:
```
GVFS_SMB_DEBUG=60 /usr/lib/gvfs/gvfsd -r
INFO: Current debug levels:
  all: 60
  tdb: 60
  printdrivers: 60
  lanman: 60
  smb: 60
  rpc_parse: 60
  rpc_srv: 60
  rpc_cli: 60
  passdb: 60
  sam: 60
  auth: 60
  winbind: 60
  vfs: 60
  idmap: 60
  quota: 60
  acls: 60
  locking: 60
  msdfs: 60
  dmapi: 60
  registry: 60
Using netbios name MUSTAFA-IBM.
Using workgroup WORKGROUP.
smbc_stat(smb://labdata1.ad/okamoto_lab)
SMBC_server: server_n=[labdata1.ad] server=[labdata1.ad]
 -> server_n=[labdata1.ad] server=[labdata1.ad]
Opening cache file at /var/run/samba/gencache.tdb
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Attempt to open gencache.tdb has failed.
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up labdata1.ad#20 (sitename (null))
Opening cache file at /var/run/samba/gencache.tdb
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Attempt to open gencache.tdb has failed.
no entry for labdata1.ad#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name labdata1.ad<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name labdata1.ad<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name labdata1.ad<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name labdata1.ad<0x20>
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for labdata1.ad#20: 10.197.103.1
Opening cache file at /var/run/samba/gencache.tdb
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Attempt to open gencache.tdb has failed.
internal_resolve_name: returning 1 addresses: 10.197.103.1:0 
s3_event: Added timed event "tevent_req_timedout": 0x7f407402c810
Connecting to 10.197.103.1 at port 445
s3_event: Added timed event "tevent_req_timedout": 0x7f407402e1b0
s3_event: Destroying timer event 0x7f407402e1b0 "tevent_req_timedout"
s3_event: Destroying timer event 0x7f407402c810 "tevent_req_timedout"
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 0
	SO_BROADCAST = 0
	TCP_NODELAY = 1
	TCP_KEEPCNT = 9
	TCP_KEEPIDLE = 7200
	TCP_KEEPINTVL = 75
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 24040
	SO_RCVBUF = 87380
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	TCP_QUICKACK = 1
 session request ok
Substituting charset 'UTF-8' for LOCALE
s3_event: Added timed event "tevent_req_timedout": 0x7f407402e060
s3_event: Schedule immediate event "tevent_queue_immediate_trigger": 0x7f407400b3f0
s3_event: Run immediate event "tevent_queue_immediate_trigger": 0x7f407400b3f0
s3_event: Destroying timer event 0x7f407402e060 "tevent_req_timedout"
Doing spnego session setup (blob length=89)
got OID=1.2.840.48018.1.2.2
got OID=1.3.6.1.4.1.311.2.2.10
got principal=labdata1$@AD.MSHRI.ON.CA
kerberos_kinit_password: as khan using [MEMORY:cliconnect] as ccache and config [(null)]
Kinit failed: Configuration file does not specify default realm
     negotiate: struct NEGOTIATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmNegotiate (1)
        NegotiateFlags           : 0x60088215 (1611170325)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        DomainNameLen            : 0x0009 (9)
        DomainNameMaxLen         : 0x0009 (9)
        DomainName               : *
            DomainName               : 'WORKGROUP'
        WorkstationLen           : 0x000b (11)
        WorkstationMaxLen        : 0x000b (11)
        Workstation              : *
            Workstation              : 'MUSTAFA-IBM'
     challenge: struct CHALLENGE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmChallenge (0x2)
        TargetNameLen            : 0x0012 (18)
        TargetNameMaxLen         : 0x0012 (18)
        TargetName               : *
            TargetName               : 'SLRI_LAN1'
        NegotiateFlags           : 0x60888215 (1619558933)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               1: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        ServerChallenge          : 1c82f28bfa40eff0
        Reserved                 : 0000000000000000
        TargetInfoLen            : 0x0080 (128)
        TargetNameInfoMaxLen     : 0x0080 (128)
        TargetInfo               : *
            TargetInfo: struct AV_PAIR_LIST
                count                    : 0x00000005 (5)
                pair: ARRAY(5)
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbDomainName (0x2)
                        AvLen                    : 0x0012 (18)
                        Value                    : union ntlmssp_AvValue(case 0x2)
                        AvNbDomainName           : 'SLRI_LAN1'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbComputerName (0x1)
                        AvLen                    : 0x0010 (16)
                        Value                    : union ntlmssp_AvValue(case 0x1)
                        AvNbComputerName         : 'LABDATA1'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsDomainName (0x4)
                        AvLen                    : 0x001c (28)
                        Value                    : union ntlmssp_AvValue(case 0x4)
                        AvDnsDomainName          : 'ad.mshri.on.ca'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsComputerName (0x3)
                        AvLen                    : 0x002e (46)
                        Value                    : union ntlmssp_AvValue(case 0x3)
                        AvDnsComputerName        : 'labdata1.ad.mshri.on.ca'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvEOL (0x0)
                        AvLen                    : 0x0000 (0)
                        Value                    : union ntlmssp_AvValue(case 0x0)
Got challenge flags:
Got NTLMSSP neg_flags=0x60888215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
     authenticate: struct AUTHENTICATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmAuthenticate (3)
        LmChallengeResponseLen   : 0x0018 (24)
        LmChallengeResponseMaxLen: 0x0018 (24)
        LmChallengeResponse      : *
            LmChallengeResponse      : union ntlmssp_LM_RESPONSE(case 24)
            v1: struct LM_RESPONSE
                Response                 : d90466175bf2bbf99aa1a644fcaefdbafd1bd2430e900dbb
        NtChallengeResponseLen   : 0x00ac (172)
        NtChallengeResponseMaxLen: 0x00ac (172)
        NtChallengeResponse      : *
            NtChallengeResponse      : union ntlmssp_NTLM_RESPONSE(case 172)
            v2: struct NTLMv2_RESPONSE
                Response                 : fc8bb0771d9e3c4591b47edda2950e19
                Challenge: struct NTLMv2_CLIENT_CHALLENGE
                    RespType                 : 0x01 (1)
                    HiRespType               : 0x01 (1)
                    Reserved1                : 0x0000 (0)
                    Reserved2                : 0x00000000 (0)
                    TimeStamp                : Thu May 17 03:49:46 PM 2012 EDT
                    ChallengeFromClient      : 3721102950b93297
                    Reserved3                : 0x00000000 (0)
                    AvPairs: struct AV_PAIR_LIST
                        count                    : 0x00000005 (5)
                        pair: ARRAY(5)
                            pair: struct AV_PAIR
                                AvId                     : MsvAvNbDomainName (0x2)
                                AvLen                    : 0x0012 (18)
                                Value                    : union ntlmssp_AvValue(case 0x2)
                                AvNbDomainName           : 'SLRI_LAN1'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvNbComputerName (0x1)
                                AvLen                    : 0x0010 (16)
                                Value                    : union ntlmssp_AvValue(case 0x1)
                                AvNbComputerName         : 'LABDATA1'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvDnsDomainName (0x4)
                                AvLen                    : 0x001c (28)
                                Value                    : union ntlmssp_AvValue(case 0x4)
                                AvDnsDomainName          : 'ad.mshri.on.ca'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvDnsComputerName (0x3)
                                AvLen                    : 0x002e (46)
                                Value                    : union ntlmssp_AvValue(case 0x3)
                                AvDnsComputerName        : 'labdata1.ad.mshri.on.ca'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvEOL (0x0)
                                AvLen                    : 0x0000 (0)
                                Value                    : union ntlmssp_AvValue(case 0x0)
        DomainNameLen            : 0x0012 (18)
        DomainNameMaxLen         : 0x0012 (18)
        DomainName               : *
            DomainName               : 'slri_lan1'
        UserNameLen              : 0x0008 (8)
        UserNameMaxLen           : 0x0008 (8)
        UserName                 : *
            UserName                 : 'khan'
        WorkstationLen           : 0x0016 (22)
        WorkstationMaxLen        : 0x0016 (22)
        Workstation              : *
            Workstation              : 'MUSTAFA-IBM'
        EncryptedRandomSessionKeyLen: 0x0010 (16)
        EncryptedRandomSessionKeyMaxLen: 0x0010 (16)
        EncryptedRandomSessionKey: *
            EncryptedRandomSessionKey: DATA_BLOB length=16
[0000] BF 82 6E 2E D2 67 E1 95   65 58 41 BE 3F 47 C8 C6   ..n..g.. eXA.?G..
        NegotiateFlags           : 0x60088215 (1611170325)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
smbc_stat(smb://labdata1.ad/okamoto_lab)

```

---

### Post by kpuz on 2012-05-17
More information:

Linux Mint 12 64 bit live cd: same problem.

But the installed Linux Mint 12 on my hard drive is able to log into the share.

---

### Post by mathfreak on 2012-05-18
> **kpuz said:**
> I agree, my syntax was all wrong.  With new syntax that you provided, is there a way to add domain information with the username?  

When using gvfs-mount smb://khan@labdata1.ad/Okamoto_lab
I get prompted for the Domain and then the password.  I input the password and domain but I keep getting reprompted.

Fresh install of Ubuntu 12.04 LTS here and I'm having the exact same issues. The following command works perfectly. I can connect and transfer files

```
smbclient \\\\newucnet\\shareroot -U <my username> -W <my domain>

```

But attempting to connect via Nautilus or gvfs-mount just prompts me over and over for domain and password.

I'm also getting the exact same error trying to add a printer shared on the network. This is my bigger issue.

---

### Post by LewisTM on 2012-05-18
This [thread]("http://ubuntuforums.org/showthread.php?t=1170587") proposes two fixes by adding lines to the /etc/samba/smb.conf file.
Maybe one of them can be helpful. Especially the [FONT="Courier New"]spnego = no[/FONT] part judging from kpuz's last debugging error.
There is also the long hostname [bug]("http://developerslog.org/?p=73") but I doubt that's the case here.

---

### Post by kpuz on 2012-05-18
Thank you.  The lanman fix did the trick for me.  The share is now mounting properly.

---

### Post by mathfreak on 2012-05-18
> **LewisTM said:**
> This [thread]("http://ubuntuforums.org/showthread.php?t=1170587") proposes two fixes by adding lines to the /etc/samba/smb.conf file.
Maybe one of them can be helpful. Especially the [FONT="Courier New"]spnego = no[/FONT] part judging from kpuz's last debugging error.
There is also the long hostname [bug]("http://developerslog.org/?p=73") but I doubt that's the case here.

Yes! This did it! I did both fixes, but it looks like it was the LANMAN fix that did it.

---

