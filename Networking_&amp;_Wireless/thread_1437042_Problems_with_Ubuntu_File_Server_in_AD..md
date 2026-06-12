---
title: "Problems with Ubuntu File Server in AD."
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by AsherSevyn on 2010-03-23
Hey guys, I have went through 3 tutorials now for setting up Ubuntu as a file server in a Windows Domain. I installed Samba, configured the Smb file according to the tutorial ([http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)) and installed Winbind. I can ping the Ubuntu machine from any computer on the domain but I cannot see the shares that I have established. No authentication is needed at this point we want it to be opened to all on the domain. Any recommendations would be greatly appreciated. ~Asher

---

### Post by jrssystemsnet on 2010-03-23
See [http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind#Joining_The_Domain](http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind#Joining_The_Domain) -

* did you successfully get a Kerberos ticket?
* did you successfully join the AD domain?
* did **wbinfo -u** successfully return a list of your AD's users?
* does **smbclient -U Administrator -L 127.0.0.1** successfully return a list of the shares on the local Samba server?

---

### Post by AsherSevyn on 2010-03-25
Thanks for the reply.

It looks like I'm having some difficulty joining the domain. I did a "sudo domainjoin-cli join MYDOMAIN USERNAME" and I am getting the message Unable to parse krb5.conf [code 0x00080040] "The file on your system could not be parsed. 

Here is my krb5.conf


[libdefaults]

default_realm = [KMLLC.KNOWLEDGEMOSAIC.COM]("http://kmllc.knowledgemosaic.com/")

[realms]
        YOUR.KERBEROS.REALM = {

             kdc = [domaincontroller.kmllc.knowledgemosaic.com]("http://domaincontroller.kmllc.knowledgemosaic.com/")
       }

[domain_realms]


     .kerberos.server = [KMLLC.KNOWLEDGEMOSAIC.COM]("http://kmllc.knowledgemosaic.com/")

---

### Post by jrssystemsnet on 2010-03-25
I believe your /etc/krb5.conf should look like this:

```
[libdefaults]
        default_realm = KMLLC.KNOWLEDGEMOSAIC.COM

[realms]
        KMLLC.KNOWLEDGEMOSAIC.COM = {
                kdc = **domaincontroller**.kmllc.knowledgemosaic.com
                admin-server = **domaincontroller**.kmllc.knowledgemosaic.com
                default_domain = KMLLC.KNOWLEDGEMOSAIC.COM
        }

[domain_realm]
        .kmllc.knowledgemosaic.com = KMLLC.KNOWLEDGEMOSAIC.COM
        kmllc.knowledgemosaic.com = KMLLC.KNOWLEDGEMOSAIC.COM
```

Note the **bold**ed bits, you need to replace that with the name of an actual domain controller (with the GC available!) in your domain - and you also should make sure that your Samba box can successfully resolve that FQDN to said domain controller!

---

### Post by AsherSevyn on 2010-03-25
So I updated my krb5.conf file as specified. 

The name of the domain controller is: km-pdcfs

the Domain is Kmllc.knowledgemosaic.com

Does this look right because I am getting the same error.


[libdefaults]
        default_realm = KMLLC.KNOWLEDGEMOSAIC.COM

[realms]
        KMLLC.KNOWLEDGEMOSAIC.COM = {
                kdc = km-pdcfs.kmllc.knowledgemosaic.com
                admin-server = km-pdcfs.kmllc.knowledgemosaic.com
                default_domain = KMLLC.KNOWLEDGEMOSAIC.COM
        }

[domain_realm]
        .kmllc.knowledgemosaic.com = KMLLC.KNOWLEDGEMOSAIC.COM
        kmllc.knowledgemosaic.com = KMLLC.KNOWLEDGEMOSAIC.COM

---

### Post by jrssystemsnet on 2010-03-25
Yep, that looks right.

Try [b]sudo net ads join -S km-pdcfs.kmllc.knowledgemosaic.com -U administrator
[/b] and post results here.

---

### Post by AsherSevyn on 2010-03-25
Here's what I got. It appears it's having trouble with the hostname: UFSERVER.

root@UFSERVER:/etc# sudo net ads join -S km-pdcfs.kmllc.knowledgemosaic.com -U ntilbrook
sudo: unable to resolve host UFSERVER
Enter ntilbrook's password:
Failed to join domain: Invalid configuration ("workgroup" set to 'KMLLC.KNOWLEDGEMOSAIC.COM', should be 'KMLLC') and configuration modification was not requested
root@UFSERVER:/etc# 

Any ideas?

---

### Post by jrssystemsnet on 2010-03-25
A couple.  First, fix your sudoers file - you should not be getting errors like that when you sudo.  This has nothing to do with Samba, this is something you've got broken with your sudoers and/or /etc/hosts.

After that... well, honestly, **apt-get remove** samba and winbind entirely, delete the entry for this machine from the Computers section of your Active Directory, and start over again following my how-to e-x-a-c-t-l-y and carefully, not mixing and matching from other how-tos you find elsewhere.  At this point it's extremely difficult to figure out what's gotten hosed where, because there hasn't been a controlled process to get from point A to point B.

---

### Post by AsherSevyn on 2010-03-25
I am more than happy to follow your how-tos. Thank you so much for your help. I am a Linux n00b but I am willing to learn. I have gone through 4 different tutorials. What would you say the best way to fix my sudo file? 

Before the default host name was "ntilbrook-desktop" but linux has issues with hostnames longer than 15 characters so I changed my hostname to: UFSERVER. Could this be part of the problem?

---

### Post by jrssystemsnet on 2010-03-25
That might be part of the problem.  First, try changing your hostname to ufserver - no caps.  I don't know for a fact that putting a hostname in caps will break normal linux host resolution... but I don't know for a fact that it *won't*, either. :)

Once you've changed your hostname to ufserver in /etc/hostname, go to /etc/hosts.  It should look like this:

```
127.0.0.1	localhost
127.0.1.1	ufserver.knowledgemosaic.com	ufserver

```

For good reference, go to your AD DNS and add a host for ufserver.knowledgemosaic.com, of course with the correct IP address to get to ufserver.

Then restart ufserver.

When it comes back up, using sudo should work without errors, and you should be ready to start over with installing samba and winbind, configuring them, and adding ufserver to your domain.

---

### Post by jrssystemsnet on 2010-03-25
TEST your sudo before trying to start over with the how-to, though - I don't want you to start again with Samba until we've gotten your hosts problem resolved!

---

### Post by AsherSevyn on 2010-03-25
Yeah it seems there definitely is a problem here.

even though I entered ufserver as the new hostname and it reflects when I use hostname because it shows:

root@UFSERVER:/etc# hostname
ufserver
root@UFSERVER:/etc# 

However for some reason the actual file "hosts" shows this:

127.0.0.1       ntilbrook-desktop       localhost.localdomain   localhost
127.0.1.1       ntilbrook-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
~

---

### Post by jrssystemsnet on 2010-03-25
so **sudo nano /etc/hosts** and edit it to reflect your current hostname.

Then restart the machine, so that it will pick everything up.

---

### Post by AsherSevyn on 2010-03-25
You were right. Restarting fixed the host name.

I corrected the hosts file:

Here is the current Hosts file:

127.0.0.1       localhost
127.0.1.1       ufserver.knowledgemosaic.com ufserver

However when I attempt to join the domain I get this:

root@ufserver:/etc# sudo net ads join -S km-pdcfs.kmllc.knowledgemosaic.com -U ntilbrook
Enter ntilbrook's password:
Failed to join domain: Invalid configuration ("workgroup" set to 'KMLLC.KNOWLEDGEMOSAIC.COM', should be 'KMLLC') and configuration modification was not requested

Any ideas?

---

### Post by jrssystemsnet on 2010-03-25
Just what it says on the tin: in /etc/samba/smb.conf, find where you set WORKGROUP, and change it from KMLLC.KNOWLEDGEMOSAIC.COM to just KMLLC.  Then try again.

---

### Post by AsherSevyn on 2010-03-25
WHOOOHOOO Progress!

It seems like I just joined the domain.

There is a DNS error.

Here is the result thus far:

root@ufserver:/etc/samba# sudo net ads join -S km-pdcfs.kmllc.knowledgemosaic.com -U ntilbrook
Enter ntilbrook's password:
Using short domain name -- KMLLC
Joined 'UFSERVER' to realm 'kmllc.knowledgemosaic.com'
DNS update failed!
root@ufserver:/etc/samba#

---

### Post by jrssystemsnet on 2010-03-25
Is user "ntilbrook" an Administrator in the domain?

Does ufserver show up in the Computers list in the AD now?

---

### Post by AsherSevyn on 2010-03-25
Yes, I am the domain Admin.

and Yes ufserver is showing up in domain users on my domain controller. 

Well done!

Now we just have to see whats going on with DNS.

---

### Post by AsherSevyn on 2010-03-25
OMG THE SHARE IS SHOWING UP ON THE NETWORK!

Bravo jrssystemsnet!

You are the man!

:popcorn:

The DNS error I am still trying to figure out which is probably the cause if it not showing up when I browse network computers but I can get to it from any computer by \\ufserver.
I'm thinking DNS.

---

### Post by AsherSevyn on 2010-03-25
I'm not sure what string is causing it but for some reason a login prompt challenge pops up when trying to access \\ufserver.

The funny part is that you can type in anything, hit Ok and it will let you in.

So the challenge is initiated but the verification is not being accessed.

I need to figure out how to remove the login option all together.

There isn't anything on here that needs permissions.

We need a server that just lets people in when they access it.

---

