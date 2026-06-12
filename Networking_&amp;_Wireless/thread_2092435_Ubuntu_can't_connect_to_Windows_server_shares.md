---
title: "Ubuntu can't connect to Windows server shares?"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by ebonweaver on 2012-12-07
I'm seeing a TON of threads about connecting to windows shares not  working on Ubuntu 12.  Thus far some people find uppercasing the domain  works for unknown reasons, but that has not worked for me.  If I use the  nautilus method (alt+f2 or command line) regardless of how I case the  domain I'm given the same error:

Could not display "smb://[server address]/[share name lowercased]
Error: Failed to mount windows share
Please select another viewer and try again

Huh?  What's a viewer?  Why is it lowercasing the share name when it has  a capital first letter?  Why is it not able to mount the share?

If I use the File -> connect to server method I'm also met with  "Failed to mount Windows share" as an error at the top of the window.

Shares are hosted on Windows 2008 r2 servers on a domain.  Client is  Ubuntu 12.04 LTS, not bound to domain, using local account.  I'm not  looking to bind, just connect to the shares using a domain account.   This should be a very basic thing, I'm shocked to see that it might  simply not work, and that it's certainly not point and click easy by  this point in time even if there is a way to make it work.

---

### Post by redmk2 on 2012-12-08
> **ebonweaver said:**
> I'm seeing a TON of threads about connecting to windows shares not  working on Ubuntu 12.  
Can you give us an example or two?> 
Thus far some people find uppercasing the domain  works for unknown reasons...
Example of this would be nice also.> 
If I use the  nautilus method (alt+f2 or command line) regardless of how I case the  domain I'm given the same error:

Could not display "smb://[server address]/[share name lowercased]
Error: [COLOR="Red"]*Failed to mount*[/COLOR] windows share
This appears to be an authentication problem.  It is NOT saying the share isn't there, but it is stating it can't mount the share.> 
Please select another viewer and try again.  Huh?  What's a viewer?
A viewer is the interface you are using to view the mounted share (i.e. Nautilus or CLI or Dolphin or Thunar (File Managers)).

Why is it lowercasing the share name when it has  a capital first letter?The case is not important in Samba for mounting the shares.  //SERVER_Name/share is the same as //server_name/Share.> 
 Why is it not able to mount the share?
My guess is that it's an authentication problem.  We won't know until you supply some more information.  I would start with the output of these 2 CLI commands```
smbclient -L [server address]

smbtree -d3
``` > 

If I use the File -> connect to server method I'm also met with  "Failed to mount Windows share" as an error at the top of the window.

Shares are hosted on Windows 2008 r2 servers on a domain.  Client is  Ubuntu 12.04 LTS, not bound to domain, using local account.  I'm not  looking to bind, just connect to the shares using a domain account.
What do you mean by "using local account...connect to the shares using a domain account"?  If you are using a local (to Ubuntu) user, how is the Windows share to authenticate your user at all.> 
This should be a very basic thing, I'm shocked to see that it might  simply not work, and that it's certainly not point and click easy by  this point in time even if there is a way to make it work.
Let's not guess.  We can tell more after you supply the output of the 2 CLI commands listed above.  What version of Ubuntu are you using?

---

### Post by ebonweaver on 2012-12-10
Using:
smbclient -L //server.domain.com -U domain_user
I get prompted for the proper password rather than the local account if I don't put in -U, and it says:
session setup failed: NT_STATUS_LOGON_FAILURE

smbtree gives a ton of output as follows with local network info scrubbed for security:

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 [removed info]
added interface eth0 [removed info]

Prompts for local account password, after which:

tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from [removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name ACCESS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ACCESS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ACCESS<0x1d>
Got a positive name query response from [removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=[removed info]
Connecting to [removed info] at port 445
Doing spnego session setup (blob length=136)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
ACCESS
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name ACCESS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ACCESS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ACCESS<0x1d>
Got a positive name query response from [removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=[removed info]
Connecting to [removed info] at port 445
Doing spnego session setup (blob length=136)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\[removed info]         
Connecting to host=[removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name [removed info]<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name [removed info]<0x20>
resolve_wins: Attempting wins lookup for name [removed info]<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name [removed info]<0x20>
resolve_hosts: getaddrinfo failed for name [removed info] [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name [removed info]<0x20>
Got a positive name query response from [removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to [removed info] at port 445
Doing spnego session setup (blob length=136)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\[removed info]          
Connecting to host=[removed info]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name [removed info]<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name [removed info]<0x20>
resolve_wins: Attempting wins lookup for name [removed info]<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name [removed info]<0x20>
resolve_hosts: getaddrinfo failed for name [removed info] [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name [removed info]<0x20>
cli_start_connection: failed to connect to [removed info]<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

I'm not sure what this is supposed to show as it appears the command causes the system to spider the local subnet for any machines with shares and try to mount them, but it used local credentials which would obviously fail.  The server in question is not on the local subnet if that's what you were looking for.

In answer to your question, the local account on Ubuntu has nothing to do with the domain account I'm attempting to use to connect to the server with.  Windows is to authenticate the user by way of the credentials in the connection dialogue, that's what it's there for.

As for your request for other threads about this kind of issue, here are a few:
[http://askubuntu.com/questions/134249/connecting-to-windows-7-shares-from-12-04](http://askubuntu.com/questions/134249/connecting-to-windows-7-shares-from-12-04)
[http://askubuntu.com/questions/134420/cant-connect-to-ms-windows-share-after-switching-to-12-04](http://askubuntu.com/questions/134420/cant-connect-to-ms-windows-share-after-switching-to-12-04)
[http://askubuntu.com/questions/130522/windows-7-and-ubuntu-12-04-cant-connect-anymore](http://askubuntu.com/questions/130522/windows-7-and-ubuntu-12-04-cant-connect-anymore)
[http://askubuntu.com/questions/127223/network-authentication-not-working](http://askubuntu.com/questions/127223/network-authentication-not-working)

Unfortunately things others said worked like uppercasing the domain or editing the smb.conf file did not work for me.  In fact, the latter seems to have zero impact on the client, because as I dug into this further I checked the server security logs.  Ubuntu is apparently failing to properly identify it's NTLM version, which would explain the auth failure.  A Mac or windows machine connects with type NTLMv2 as it should, but Ubuntu is type - and fails.  Despite changing the smb.conf (which I thought only affected a share on Ubuntu, not how Ubuntu connected to a share) to have:
client ntlmv2 auth = yes
which by documentation says disables lanman/ ntlmv1, it still does not try v2 according to the Windows logs.  I would expect out of the box it would be able to negotiate the most common connection types, but if that's not the case is there somewhere this needs to be configured?

---

### Post by ebonweaver on 2012-12-10
Further update:
Somehow, perhaps in that smbtree command as it noted it was reloading smb.conf, the system is now trying NTLMv2 and according to Windows successfully authenticating.  This ONLY is tried if you upper case the domain.  If you lower case the domain (as it actually is in the DC) it will NOT try v2, it just tries - and fails.  However, the client still says it can't mount the share, try another viewer, and the security log shows that the client logs off the instant it logs on.  This ONLY happens however if I use the Go -> Location function.  If I use smbclient at CLI it still tries NTLM - and fails to connect, presumably because it's not trying the domain and therefore auth type properly.

So I'm seeing two issues here.  On one hand, the system is not using proper auth methods in all connection cases, and has what can only be called a significant bug when it comes to the casing of the domain as relates to auth types tried.  Second, it's then unable to actually show/mount the share, so the connection immediately drops, which would appear to be a bug in the file manger UI.  There is nothing recorded in the syslog related to this failure.

---

### Post by ebonweaver on 2012-12-10
Ok, another update, and resolution though NOT anything intelligent.

From CLI if I put in -W DOMAIN I got this error:

tree connect failed: NT_STATUS_DUPLICATE_NAME

That led me to a thread that didn't really give me an answer, but made a comment that made me thinks samba in Ubuntu had a(nother) serious issue, and turns out I was right.  It can't use cnames, you MUST use the aname or IP of the server, otherwise it somehow trips over itself in the resolution.

So, two bugs in Ubuntu 12:

1. You MUST uppercase the domain name when connecting to a Windows server otherwise it fails to use all auth type properly.

2. You MUST use the IP or aname as cnames do not resolve properly.

---

### Post by Thinkin on 2013-01-03
Yes, confirmed.  Using Nautilus I was immediately able to connect to the Windows 2008 server on the network using Capitals for the domain name and the actual internal ip address.

---

### Post by jonnjonzzn on 2013-01-04
Seems like everytime I try Ubuntu again I run into an issue like this.  Lots of mickey mouse stuff when trying to use in a corporate environment.  I realize this isn't isn't a primary target market for Ubuntu or any other Linux distribution for that matter anymore, but still... geesh.  Works out of the box on Fedora and SUSE as it should.

---

### Post by minja on 2013-02-22
OK, UPPERCASE resolved my problem.
Thanks,
Minja
> **ebonweaver said:**
> Ok, another update, and resolution though NOT anything intelligent.

From CLI if I put in -W DOMAIN I got this error:

tree connect failed: NT_STATUS_DUPLICATE_NAME

That led me to a thread that didn't really give me an answer, but made a comment that made me thinks samba in Ubuntu had a(nother) serious issue, and turns out I was right.  It can't use cnames, you MUST use the aname or IP of the server, otherwise it somehow trips over itself in the resolution.

So, two bugs in Ubuntu 12:

1. You MUST uppercase the domain name when connecting to a Windows server otherwise it fails to use all auth type properly.

2. You MUST use the IP or aname as cnames do not resolve properly.

---

