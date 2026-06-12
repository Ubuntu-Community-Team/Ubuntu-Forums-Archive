---
title: "Likewise error  when attempting to join Windows domain"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by _UsUrPeR_ on 2010-06-10
Hey all. I'm having a problem getting likewise to connect to a Windows 2008 R2 server on our network.

```
root@place:~# domainjoin-cli join domainiwant.com Administrator
Joining to AD Domain:   domainiwant.com
With Computer DNS Name: jsass.domainiwant.com

Administrator@DOMAINIWANT.COM's password: 

Error: Lsass Error [code 0x00080047]

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially the requested address does not exist.

```

I have already read up on this a little bit. Both servers are within a minute of each other, so I am not concerned about server timing. I am not sure where to go from this point. Everything I have read seems to indicate that this should "just work". Any suggestions would be helpful.

---

### Post by lumpie on 2010-06-12
Im getting the same error (and an additional one) with a Windows 2003 R2 server. I ran

1. sudo apt-get update
   2. sudo apt-get install likewise-open
   3. sudo domainjoin-cli join fqdn of your domain Administrator

   [COLOR=Silver]4. sudo update-rc.d likewise-open defaults
   5. sudo /etc/init.d/likewise-open start[/COLOR]

After step 3, I get 

Joining to AD Domain:   mydomain.local
With Computer DNS Name: ubuntu.mydomain.local
[EMAIL="Administrator@MYDOMAIN.LOCAL"]Administrator@MYDOMAIN.LOCAL[/EMAIL]'s password: [I entered it]

Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error

Both DCs are available and can ping the first of 2 NICs on the Ununtu 10.04 box, which has a DHCP address from the DC.

---

### Post by _UsUrPeR_ on 2010-06-13
Ok, I got it.

I was able to fix this by installing a the Windows DNS server on my Windows 2k8 R2 server, and switching the /etc/resolv.conf on the likewise-installed Ubuntu client to use the Windows server for DNS. That fixed my problem. I keep forgetting that Windows server products assume that they are the center of your network's universe. 

Try installing a Windows DNS server on your Win 2k3 server. I hope the same works for you.

---

### Post by lumpie on 2010-06-15
> **joelkillspeople said:**
> Ok, I got it.

I was able to fix this by installing a the Windows DNS server on my Windows 2k8 R2 server, and switching the /etc/resolv.conf on the likewise-installed Ubuntu client to use the Windows server for DNS. That fixed my problem. I keep forgetting that Windows server products assume that they are the center of your network's universe. 

Try installing a Windows DNS server on your Win 2k3 server. I hope the same works for you.

Both Windows DCs are DNS servers. I have no idea where to find /etc/resolv.conf or how to edit it if I found it.

---

### Post by lumpie on 2010-06-16
in  /etc/resolv.con, the main DC is listed  twice, the secondary is listed once, all as nameservers

nameserver 192.168.1.100
nameserver 192.168.1.101
nameserver 192.168.1.100

#the libc may not support more than 3 nameservers.
#The nameservers listed below may not be recognized.
nameserver 192.168.1.101

Completely clueless as to what to do now. :confused:

---

### Post by lumpie on 2010-06-16
I believe what is listed in   /etc/resolv.conf is correct, so this machine *does *know of the DNS servers in the domain. So maybe thats not the problem.

---

### Post by jeight on 2010-09-30
It's you Windows Firewall.  Either stop your firewall or make exceptions for the ports that likewise uses.

---

### Post by _UsUrPeR_ on 2010-09-30
I found another interesting problem with likewise, but this may require a new thread.

We are attempting to authenticate Ubuntu users against a AD database, which works up until ~15 users are logged in. From that point on, when attempting to authenticate, I am seeing that instead of substituting @fqdn via likewise, it is substituting the user's name @localhost.

An example:

an attempted login which works would normally show a login like this:

user entered at Ubuntu LTSP login screen in LDM:
jsass

What AD sees via Likewise: "jsass@schooldistrict.org" (schooldistrict.org is the added FQDN required for AD authentication)

When an attempted login fails, it will show something like this:

user entered at Ubuntu LTSP login screen in LDM:
jsass

what AD sees via Likewise: "jsass@ubuntu.localhost (ubuntu.com would be the name given in the /etc/hostname file). 

I have not seen any way to get this to reliably concatenate "@schooldistrict.org" to the end of a user's name. Again, this is something that only happens once about 15 users have already successfully authenticated against the AD database. It seems like a likewise-specific problem.

---

### Post by atworkwithjf on 2010-10-12
@joekillspeople

Are yous till having issues here with Likewise-Open?  I'm curious which version of Ubuntu you are using and what version of Likewise.  Version 6 is available on the Likewise-Open website.

It also seems that most of your issues have to do with DNS related issues on your linux machines.  

I'll be happy to help you resolve this if I can get some more information.

-atworkwithjf

---

### Post by karmasagent on 2010-11-22
@ atworkwithjf

I could use some assistance. I've read through every thread on the internets about this one and still no solution.

I am stuck on the error:

"Error: Lsass Error [code 0x00080047]

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS
server. Potentially the requested address does not exist."

I am running Windows Server 2008 R2 in a virtual machine (VMWare Workstation - the latest), as is my Ubuntu 10.10 installation. I have 3 other Windows-based VMs that all connect to the W2K8R2 domain server without issue. The domain is cylon.local and the domain server itself is named hivemind.

My /etc/resolv.conf file looks like this:

# Generated by NetworkManager
search 192.168.5.10
nameserver 192.168.5.10


Both are the IP of my W2K8R2 Domain Controller which is set up also as the domain DNS server.

I have manually set the network config information in my network adapter as such:

IP: 192.168.5.55
Netmask: 255.255.255.0
Gateway: 192.168.5.1
DNS Servers: 192.168.5.10, 4.2.2.2

When I proceed through the steps - either GUI or command line these are the values I use (copy/pasted from my console - two attempts represented):

"sudo domainjoin-cli join cylon.local michael
Joining to AD Domain:   cylon.local
With Computer DNS Name: ubuntu.cylon.local

michael@CYLON.LOCAL's password: 

Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
michael@ubuntu:~$ sudo domainjoin-cli join cylon michael
Joining to AD Domain:   cylon
With Computer DNS Name: ubuntu.cylon

michael@CYLON's password: 

Error: Lsass Error [code 0x00080047]

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS
server. Potentially the requested address does not exist"

I've done the uninstall/reinstall of likewise-open and have tried every other little trick listed in this thread and others. I have a netscreen onsite so have all machine firewalls turned off. I'm pulling my hair out!!

Any assistance on this matter would be VERY much appreciated.

Thanks!

:confused:

---

### Post by atworkwithjf on 2010-11-22
There is a bug in OpenLDAP.

Have you looked into the Likewise forums?

[http://www.likewise.com/community/index.php/forums/viewannounce/863_6/](http://www.likewise.com/community/index.php/forums/viewannounce/863_6/)

Details the problem.  They have a version on their website which is not effected in the same way the version in main is (not dependent on the build of OpenLDAP in maverick).

This bug in OpenLDAP has a fix already committed so it should not be long before it's resolved in an update.

---

### Post by jimerman on 2011-02-19
Sorry, I am new to Ubuntu.  I followed the link, but I don't understand how to install / apply the package you are referring to.  I have Ubuntu 10.4.

I click on the page [ttps://launchpad.net/~ssalley/+archive/ppa/+packages]("https://launchpad.net/%7Essalley/+archive/ppa/+packages"), that shows me 2 packages.  What do I download?  LW-Open?  openldap?  Both?   OK, so how do I download?

I clicked on the architecture (i386), then do I download all of the built files?  How do I incorporate those into my installed version?

---

### Post by atworkwithjf on 2011-02-21
You should consider downloading the newest version from the Likewise website (version 6).

[http://www.likewise.com/download/](http://www.likewise.com/download/)

This is a much updated version compared to the PPA version.  

Their Docs are available here:

[http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html)

Quickstart Guide:

[http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#quick-start](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#quick-start)

---

### Post by jimerman on 2011-02-23
Thanks!  I downloaded the Ubuntu x86 version from Likewise web site, but when I execute the installer it says it is not supported.  I removed Likewise from the Software Center and rebooted, but no go.

I think this will solve the problem, but it won't let me install.  Perhaps there are some conf files to remove?
________________________________
    MIT Kerberos - MIT Kerberos 5 and other licenses
    OpenLDAP - OpenLDAP Public License
    Likewise DCE-RPC - BSD
    LibXML2 - BSD
    libuuid from e2fsprogs - BSD
    libiconv - LGPLv2
    OpenSSL - BSD

For more details and for the full text for each of these 
licenses, read the LICENSES and COPYING files included with 
this software.
Do you accept the terms of these licenses? (yes/no)
yes

License accepted.

Would you like to install now? (yes/no)
yes
Install started

You have the likewise-open package from Ubuntu installed.
Upgrading from the likewise-open package is not supported.
administrator@wkstn10:~/Downloads/Ubuntu/AddOns$ 
________________________________________

---

### Post by atworkwithjf on 2011-02-23
Sounds like you are using the installer for the wrong architecture.

Are you using 32 bit or 64 bit Ubuntu?

---

### Post by jimerman on 2011-02-23
32 bit, and made sure to download the right one from Likewise.  However, after I did that, I couldn't get the GUI to come up, so I'm not sure the installation was clean.  I have reinstalled Ubuntu 10.10, installed Likewise from the Software Center, and run a system update.  I am back where I started.

---

### Post by atworkwithjf on 2011-02-23
We DO NOT advise using the software center.  Use the Synaptic Package Manager.

The software center is not a very useful way of managing packages.  If you use the synaptic package manager you will find two packages, the domainjoin-gui and likewise-open and that's all you need to do.

You will also need to be certain that your DNS is correctly pointing to your domain controller as your DNS and that you have your search domain specified properly.  AD is VERY picky about this.

Finally, be sure that you have removed the references to mdns and mdns4_minimal from your nsswitch.conf's hosts entry as I'm pretty sure you're not using multicast dns.

---

### Post by gsrkashyap on 2011-02-23
having the dns server in /etc/reslov.conf file in the below format solved my issue.

nameserver xxx.xxx.xxx.xxx

---

### Post by Roasted on 2011-02-25
No go here. In my /etc/resolv.conf I have an entry that says to be auto generated by NetworkManager. However, the nameserver entries it has listed ARE our legit DNS servers, so there's nothing for me to change, yet I'm getting the same error when trying to join Ubuntu to the domain. 

Any insight?

---

### Post by _UsUrPeR_ on 2011-02-25
I think I figured out what was wrong with my specific user's problems. Their domain name (user@reallylongextraneousname.com) was really long, and the domain name was being truncated. In order to resolve the problem, I had to have the users put in their full domain manually instead of having it auto completed.

---

### Post by Roasted on 2011-02-25
Well, that's not a solution to my issue, as our domain name is quite short. I am receiving this error now:

1225 (0x4C9) ERROR_CONNECTION_REFUSED - Unknown Error.

This is in terminal when I am running sudo domainjoin-cli join domain my_user

EDIT - Found the solution on Likewise forums:

Same thing happened to me on an Ubuntu 10.04 that was renamed, all kinds of nasty lw_errors after that. I couldn&#8217;t log in with the GUI or command line. Oddly enough I could log in by starting a ssh session from another host : ssh domainname\\username@host 
At first I tried deleting lsass-adcache.db but that wasn&#8217;t good enough. 

I fixed it by stopping lsassd, 
Then removing all the the likewise db files from /var/lib/likewise-open5/db/ 
Then start lsassd and join the domain again. 
No errors this time.

I just hope we don't have to go through that EACH time we join one to the domain. There might be hundreds of systems...

---

### Post by galen666 on 2011-03-09
Hi,
 
I have the same problem as many others. I've tried some fixes but nothing works:
 
- Upgrading to what I think is the newest version of likewise (6.0.0.8330). 
- Editing /etc/nsswitch.conf per [https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/561878](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/561878)
- Patch openldap per [http://ubuntuforums.org/showthread.php?t=1613973](http://ubuntuforums.org/showthread.php?t=1613973)
- Configuring a static IP
- Check DNS settings (they look fine)
- Tried domainjoin via both cli and gui (same error)
- Checked that the time is in sync (looks right)
 
*My issue seems to be that the client can't find the LDAP server.*
 
I'm running 10.10
uname -ovr
2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 GNU/Linux
 
**sudo domainjoin-cli --loglevel info --log . join my.company.domain.com username**
 
[COLOR=darkred]Joining to AD Domain: my.company.domain.com[/COLOR]
[COLOR=darkred]With Computer DNS Name: computername.my.company.domain.com[/COLOR]
[COLOR=darkred]username@MY.COMPANY.DOMAIN.COM's[/COLOR][COLOR=darkred] password: [/COLOR]
[COLOR=darkred]20110309172806:INFO:Running module join[/COLOR]
[COLOR=darkred]20110309172806:INFO:Starting krb5.conf configuration (enabling)[/COLOR]
[COLOR=darkred]20110309172806:INFO:Reading krb5 file /tmp/likewisetmpdHGRjM/etc/krb5.conf[/COLOR]
[COLOR=darkred]20110309172806:WARNING:Short domain name not specified. Defaulting to 'my'[/COLOR]
[COLOR=darkred]20110309172806:INFO:Creating krb5 stanza 'appdefaults'[/COLOR]
[COLOR=darkred]20110309172806:INFO:Writing krb5 file /tmp/likewisetmpdHGRjM/etc/krb5.conf[/COLOR]
[COLOR=darkred]20110309172806:INFO:File /tmp/likewisetmpdHGRjM/etc/krb5.conf modified[/COLOR]
[COLOR=darkred]20110309172806:INFO:Finishing krb5.conf configuration[/COLOR]
[COLOR=darkred]Error: Lsass Error [code 0x00080047][/COLOR]
[COLOR=darkred]40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error[/COLOR]
[COLOR=darkred]20110309172807:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR][/COLOR]
[COLOR=darkred]40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error[/COLOR]
[COLOR=darkred]Stack Trace:[/COLOR]
[COLOR=darkred]main.c:938[/COLOR]
[COLOR=darkred]main.c:479[/COLOR]
[COLOR=darkred]djmodule.c:323[/COLOR]
[COLOR=darkred]djauthinfo.c:843[/COLOR]
[COLOR=darkred]djauthinfo.c:1187[/COLOR]
 
Any suggestions?

---

### Post by hooks on 2011-03-15
I had issues with Likewise for a long while as well and, after lots of searching and reading through posts, I finally got Likewise Open AND Likewise CIFS - the file server from Likewise that works with Likewise Open - to work together.

Long story short...

1. Don't use the Ubuntu repositories to install Likewise. Download it from the Likewise site.
2. Edit /etc/hosts and /etc/nsswitch
3. Join with the command line utility
```
/opt/likewise/bin/domainjoin-cli join [FQDN of your Domain] [Domain Admin Account Name]
```
4. Set /etc/init.d/srvsvcd to start automatically
```
sudo update-rc.d -f srvsvcd defaults
```
5. Create a startup script in /etc/init.d and have it run the Likewise DNS updater program, and make the script run on startup as well with update-rc.d
```
#!/bin/bash
/opt/likewise/bin/lw-update-dns
```
6. Create the share from the management console of a Windows machine as the Domain Admin

If you want more detail, check out the post on my blog: [http://lordandhooks.com/blog/playing-with-likewise-open-cifs/]("http://lordandhooks.com/blog/playing-with-likewise-open-cifs/")

---

### Post by galen666 on 2011-03-29
Dunno if it makes a difference, but I'm installing 6.0
 
I had installed this from Likewise before, but looks like I installed LikewiseOpen-6.0.0.8330-linux-x86_64-rpm instead of the Debian/Ubuntu one. Anyway, I downloaded LikewiseOpen-6.0.0.8336-linux-amd64-deb this time and installed it:
 
sudo Downloads/LikewiseOpen-6.0.0.8336-linux-amd64-deb.sh

..creating directory, verifying archive, uncompressing, checking setup environment
 
Do you accept the terms of these licenses? (yes/no)
yes
License accepted.
Would you like to install now? (yes/no)
yes
Install started
You have the likewise-open package from Ubuntu installed.
Upgrading from the likewise-open package is not supported.
 
It isn't getting installed in /opt.  The only version on my system is /usr/bin/domainjoin-cli. I have to wonder if this is getting installed at all.
 
I did have to fix some links:
sudo ln -fs /usr/lib/liblber-2.4.so.2 /usr/local/lib/
sudo ln -fs /usr/lib/libldap_r-2.4.so.2 /usr/local/lib/
 
..which resolved an error I was getting "domainjoin-cli: /usr/local/lib/liblber-2.4.so.2: no version information available (required by /usr/lib/likewise-open/libnetapi.so.0)"
 
Unfortunately it still is not working. Maybe adding the domain controller IP address to the hosts file had an effect, but I'm getting a slightly different error now.
 
[COLOR=darkred]Joining to AD Domain:   my.company.domain.com
With Computer DNS Name: computer.my.company.domain.com[/COLOR]
[COLOR=#8b0000]username@MY.COMPANY.DOMAIN.COM's password: 
20110329133522:INFO:Running module join
20110329133523:INFO:Starting krb5.conf configuration (enabling)
20110329133523:INFO:Creating blank krb5.conf
20110329133523:INFO:Reading krb5 file /tmp/likewisetmpSPbrr5/etc/krb5.conf
20110329133523:WARNING:Short domain name not specified. Defaulting to 'my'
20110329133523:INFO:Creating krb5 stanza 'libdefaults'
20110329133523:INFO:Creating krb5 stanza 'domain_realm'
20110329133523:INFO:Creating krb5 stanza 'realms'
20110329133523:INFO:Creating krb5 stanza 'appdefaults'
20110329133523:INFO:Writing krb5 file /tmp/likewisetmpSPbrr5/etc/krb5.conf
20110329133523:INFO:File /tmp/likewisetmpSPbrr5/etc/krb5.conf modified
20110329133523:INFO:Finishing krb5.conf configuration[/COLOR]
[COLOR=darkred]Error: Lsass Error [code 0x00080047][/COLOR]
[COLOR=darkred]2453 (0x995) NERR_DCNotFound - Unknown error
20110329133523:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR][/COLOR]
[COLOR=darkred]2453 (0x995) NERR_DCNotFound - Unknown error[/COLOR]
[COLOR=darkred]Stack Trace:
main.c:938
main.c:479
djmodule.c:323
djauthinfo.c:843
djauthinfo.c:1187[/COLOR]
 
Instead of getting LDAP server down, now I'm getting DC not found.

---

### Post by atworkwithjf on 2011-03-30
It would appear from your post that the repository version is installed as well as the 6.0 version.

You need to remove the repository version using the synaptic package manager first and then you can install LikewiseOpen-6.0

If the repository version is present you will not have a successful install of 6.0.

---

### Post by galen666 on 2011-03-30
OK I see now that I was misreading the message I got after trying to install Likewise. I thought it said you successfully installed the software, but it was trying to tell me I had a previous version installed and was not allowed to upgrade from that version to this one.
 
Anyway, I uninstalled 5.4 and installed 6.0 successfully. However I still can't get domainjoin to work. It takes about 20 seconds now until I get the error below.
 
**sudo domainjoin-cli --loglevel info --logfile . join my.company.domain.com username**
 
<lots of messages, no errors, then...>
 
20110330111957:INFO:Running module join
Error: LW_ERROR_LDAP_CONSTRAINT_VIOLATION [code 0x00009d7b]
 
20110330112052:ERROR:LW_ERROR_LDAP_CONSTRAINT_VIOLATION [LW_ERROR_LDAP_CONSTRAINT_VIOLATION]
 
Stack Trace:
/builder/src-buildserver/Platform-6.0/src/linux/domainjoin/domainjoin-cli/src/main.c:958
/builder/src-buildserver/Platform-6.0/src/linux/domainjoin/domainjoin-cli/src/main.c:514
/builder/src-buildserver/Platform-6.0/src/linux/domainjoin/libdomainjoin/src/djmodule.c:332
/builder/src-buildserver/Platform-6.0/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:723
/builder/src-buildserver/Platform-6.0/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:1140
 
FYI, my version of libldap:
[B]dpkg --list | grep -i 'libldap'
ii  libldap-2.4-2                        2.4.23-0ubuntu3.4                                 OpenLDAP libraries[/B]
 
I found a message that said this happens when you don't have sufficient permissions to join a machine to the domain. However, I do this all the time with this account if the computer is running Windows. This isn't a test network, it is a company network and they do allow people to join laptops, etc. to the domain using their domain credentials.

---

### Post by atworkwithjf on 2011-03-30
It would appear that you already have a machine object in AD for which this user does not have permission to make some modification.  There's a host of parameters it may want to modify and cannot do so.

One way to validate this would be to either perform the join the domain with the Administrator account in AD or to delete the machine account and retry the join.

---

### Post by galen666 on 2011-03-30
I see what you mean. Based on the [LDAP error codes]("http://www.stone-ware.com/support/techdocs/kb/s2150/LDAP%20Error%20Codes.htm"). More info [here]("http://download.oracle.com/javase/1.3/docs/api/javax/naming/directory/InvalidAttributeValueException.html").
 
I think I've run into something similar before when trying to rejoin a domain with the same machine name after installing a new OS. I might be able to work around it simply by changing the machine name.  
 
OK this worked. 
 
sudo vi /etc/hostname
 
<picked a new hostname>
 
sudo domainjoin-cli --loglevel info --logfile . join my.company.domain.com username
 
<about 90 seconds of waiting, then lots of messages followed by the important one:>
 
**SUCCESS**
 
I should have left the domain before formatting the drive and installing Ubuntu. It isn't critical at this point, but I could probably get my old hostname joined by using it on another computer then joining and leaving the domain, then leaving and joining again with this one. Not worth the trouble though.
 
Thanks for all your help atworkwithjf!

---

### Post by atworkwithjf on 2011-03-30
Hey not a problem, that's what we're here for.

One cool thing you can do with new systems before you perform the domainjoin is to se the setname option:

 > sudo /opt/likewise/bin/domainjoin-cli setname MYHOSTNAME

This will properly configure your hostname prior to join and can save you the step of manually setting it using the network manager or editing the conf files.

---

### Post by Neill_R on 2011-11-29
bump

---

### Post by shurkes on 2012-05-02
can anyone help me?
just installed on my company notebook th 12.04 ubuntu and trying join the domain.
likewise is installed, getting the follwoing message after typing my password:
Error: LW_ERROR_LDAP_CONSTRAINT_VIOLATION [code 0x00009d7b]

Thanks

---

