---
title: "Windows Networking and authentication"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by nirajandps on 2010-11-02
Hi!
 
I am working on my course project in a test environment. 
 
I have an Ubuntu Server with Squid Proxy installed in it. My AD/DHCP server is Windows Server 2008 R2. 
 
My AD/DC is dhcpserver.techxpert.com
My domain is techxpert.com
My Ubuntu machine name is SQUID-PROXY
My ubuntu machine user is squiuser
My DC IP is 170.0.0.1
My Ubuntu IP is 170.0.0.2(reserved by DHCP)
 
 
**_My samba configuration is_**
 
**[FONT=Times New Roman]/etc/samba/smb.conf [/FONT]**
[FONT=Courier New][global][/FONT]
[FONT=Courier New]security = domain[/FONT]
[FONT=Courier New]realm = TECHXPERT.COM[/FONT]
[FONT=Courier New]workgroup = techxpert[/FONT]
[FONT=Courier New]password server = *[/FONT]
[FONT=Courier New]idmap uid = 10000-20000[/FONT]
[FONT=Courier New]idmap gid = 10000-20000[/FONT]
 
 
**_My kerberos setting is_**
 
[FONT=Courier New][libdefaults][/FONT]
[FONT=Courier New]default_realm = TECHXPERT.COM[/FONT]
[FONT=Courier New]krb4_config = /etc/krb.conf[/FONT]
[FONT=Courier New]krb4_realms = /etc/krb.realms[/FONT]
[FONT=Courier New]kdc_timesync = 1[/FONT]
[FONT=Courier New]ccache_type = 4[/FONT]
[FONT=Courier New]forwardable = true[/FONT]
[FONT=Courier New]proxiable = true[/FONT]
[FONT=Courier New]# The following libdefaults parameters are only for Heimdal Kerberos.[/FONT]
[FONT=Courier New]v4_instance_resolve = false[/FONT]
[FONT=Courier New]v4_name_convert = {[/FONT]
[FONT=Courier New]host = {[/FONT]
[FONT=Courier New]rcmd = host[/FONT]
[FONT=Courier New]ftp = ftp[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]plain = {[/FONT]
[FONT=Courier New]something = something-else[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]}[/FONT]
 
[FONT=Courier New][realms][/FONT]
[FONT=Courier New]TECHXPERT.COM = {[/FONT]
[FONT=Courier New]kdc = dhcpserver.techxpert.com[/FONT]
[FONT=Courier New]admin_server = dhcpserver.techxpert.com[/FONT]
[FONT=Courier New]}[/FONT]
 
 
[FONT=Courier New][domain_realm][/FONT]
[FONT=Courier New].techxpert.com = DHCPSERVER.TECHXPERT.COM[/FONT]
[FONT=Courier New]techxpert.com = DHCPSERVER.TECHXPERT.COM[/FONT]
 
 
[FONT=Courier New][login][/FONT]
[FONT=Courier New]krb4_convert = true[/FONT]
[FONT=Courier New]krb4_get_tickets = true[/FONT]

**[FONT=Times New Roman]_My nsswitch configuration is_[/FONT]**
**[FONT=Times New Roman]/etc/nsswitch.conf[/FONT]**
[FONT=Times New Roman]The only change here was adding [/FONT][FONT=Courier New]winbind[/FONT][FONT=Times New Roman] twice. [/FONT]
[FONT=Courier New]# /etc/nsswitch.conf[/FONT]
[FONT=Courier New]#[/FONT]
[FONT=Courier New]# Example configuration of GNU Name Service Switch functionality.[/FONT]
[FONT=Courier New]# If you have the `glibc-doc' and `info' packages installed, try:[/FONT]
[FONT=Courier New]# `info libc "Name Service Switch"' for information about this file.[/FONT]
[FONT=Courier New]passwd: compat winbind[/FONT]
[FONT=Courier New]group: compat winbind[/FONT]
[FONT=Courier New]shadow: compat[/FONT]
[FONT=Courier New]hosts: files dns[/FONT]
[FONT=Courier New]networks: files[/FONT]
[FONT=Courier New]protocols: db files[/FONT]
[FONT=Courier New]services: db files[/FONT]
[FONT=Courier New]ethers: db files[/FONT]
[FONT=Courier New]rpc: db files[/FONT]
[FONT=Courier New]netgroup: nis[/FONT]
 
 
**Now I joined this ubuntu machine to windows domain techxpert.com using command after restarting services**
 
[FONT=Courier New]net ads join -U administrator[/FONT]
[FONT=Times New Roman][FONT=Verdana]I successfully joined the domain techxpert.com[/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana]but when i do **nslookup dhcpserver.techxpert.com **it gives me error, also I can't get answer when I do **host 170.0.0.1 **[/FONT][/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=red]Now my main problem is I can't get to list or access the active directory users. When I do [COLOR=blue]wbinfo -g [/COLOR][COLOR=red]it only shows me local user instead of all active directory users.[/COLOR][/COLOR][/FONT]**[/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=#ff0000]So when I make authentication configration in squid.conf, and try accessing from web browser, the authentication pop-up comes but after entering the details of username and password, the authentication doesn't take place.[/COLOR][/FONT]**[/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=purple]I need to complete the project by 6th November,2010 and I am stuck in this one. Without solving this case, my squid is a failure. [/COLOR][/FONT]**[/FONT]

[FONT=Times New Roman]**[FONT=Verdana][COLOR=#800080]Please help me out. I will highly appreciate any info.[/COLOR][/FONT]**[/FONT]

---

### Post by bab1 on 2010-11-03
> **nirajandps said:**
> Hi!
 
I am working on my course project in a test environment. 
 
I have an Ubuntu Server with Squid Proxy installed in it. My AD/DHCP server is Windows Server 2008 R2. 
 
My AD/DC is dhcpserver.techxpert.com
My domain is techxpert.com
My Ubuntu machine name is SQUID-PROXY
My ubuntu machine user is squiuser
My DC IP is 170.0.0.1
My Ubuntu IP is 170.0.0.2(reserved by DHCP)
 
 
**_My samba configuration is_**
 
**[FONT=Times New Roman]/etc/samba/smb.conf [/FONT]**
[FONT=Courier New][global][/FONT]
[FONT=Courier New]security = domain[/FONT]
[FONT=Courier New]realm = TECHXPERT.COM[/FONT]
[FONT=Courier New]workgroup = techxpert[/FONT]
[FONT=Courier New]password server = *[/FONT]
[FONT=Courier New]idmap uid = 10000-20000[/FONT]
[FONT=Courier New]idmap gid = 10000-20000[/FONT]
 
 
**_My kerberos setting is_**
 
[FONT=Courier New][libdefaults][/FONT]
[FONT=Courier New]default_realm = TECHXPERT.COM[/FONT]
[FONT=Courier New]krb4_config = /etc/krb.conf[/FONT]
[FONT=Courier New]krb4_realms = /etc/krb.realms[/FONT]
[FONT=Courier New]kdc_timesync = 1[/FONT]
[FONT=Courier New]ccache_type = 4[/FONT]
[FONT=Courier New]forwardable = true[/FONT]
[FONT=Courier New]proxiable = true[/FONT]
[FONT=Courier New]# The following libdefaults parameters are only for Heimdal Kerberos.[/FONT]
[FONT=Courier New]v4_instance_resolve = false[/FONT]
[FONT=Courier New]v4_name_convert = {[/FONT]
[FONT=Courier New]host = {[/FONT]
[FONT=Courier New]rcmd = host[/FONT]
[FONT=Courier New]ftp = ftp[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]plain = {[/FONT]
[FONT=Courier New]something = something-else[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]}[/FONT]
 
[FONT=Courier New][realms][/FONT]
[FONT=Courier New]TECHXPERT.COM = {[/FONT]
[FONT=Courier New]kdc = dhcpserver.techxpert.com[/FONT]
[FONT=Courier New]admin_server = dhcpserver.techxpert.com[/FONT]
[FONT=Courier New]}[/FONT]
 
 
[FONT=Courier New][domain_realm][/FONT]
[FONT=Courier New].techxpert.com = DHCPSERVER.TECHXPERT.COM[/FONT]
[FONT=Courier New]techxpert.com = DHCPSERVER.TECHXPERT.COM[/FONT]
 
 
[FONT=Courier New][login][/FONT]
[FONT=Courier New]krb4_convert = true[/FONT]
[FONT=Courier New]krb4_get_tickets = true[/FONT]

**[FONT=Times New Roman]_My nsswitch configuration is_[/FONT]**
**[FONT=Times New Roman]/etc/nsswitch.conf[/FONT]**
[FONT=Times New Roman]The only change here was adding [/FONT][FONT=Courier New]winbind[/FONT][FONT=Times New Roman] twice. [/FONT]
[FONT=Courier New]# /etc/nsswitch.conf[/FONT]
[FONT=Courier New]#[/FONT]
[FONT=Courier New]# Example configuration of GNU Name Service Switch functionality.[/FONT]
[FONT=Courier New]# If you have the `glibc-doc' and `info' packages installed, try:[/FONT]
[FONT=Courier New]# `info libc "Name Service Switch"' for information about this file.[/FONT]
[FONT=Courier New]passwd: compat winbind[/FONT]
[FONT=Courier New]group: compat winbind[/FONT]
[FONT=Courier New]shadow: compat[/FONT]
[FONT=Courier New]hosts: files dns[/FONT]
[FONT=Courier New]networks: files[/FONT]
[FONT=Courier New]protocols: db files[/FONT]
[FONT=Courier New]services: db files[/FONT]
[FONT=Courier New]ethers: db files[/FONT]
[FONT=Courier New]rpc: db files[/FONT]
[FONT=Courier New]netgroup: nis[/FONT]
 
 
**Now I joined this ubuntu machine to windows domain techxpert.com using command after restarting services**
 
[FONT=Courier New]net ads join -U administrator[/FONT]
[FONT=Times New Roman][FONT=Verdana]I successfully joined the domain techxpert.com[/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana]but when i do **nslookup dhcpserver.techxpert.com **it gives me error, also I can't get answer when I do **host 170.0.0.1 **[/FONT][/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=red]Now my main problem is I can't get to list or access the active directory users. When I do [COLOR=blue]wbinfo -g [/COLOR][COLOR=red]it only shows me local user instead of all active directory users.[/COLOR][/COLOR][/FONT]**[/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=#ff0000]So when I make authentication configration in squid.conf, and try accessing from web browser, the authentication pop-up comes but after entering the details of username and password, the authentication doesn't take place.[/COLOR][/FONT]**[/FONT]
[FONT=Times New Roman]**[FONT=Verdana][COLOR=purple]I need to complete the project by 6th November,2010 and I am stuck in this one. Without solving this case, my squid is a failure. [/COLOR][/FONT]**[/FONT]

[FONT=Times New Roman]**[FONT=Verdana][COLOR=#800080]Please help me out. I will highly appreciate any info.[/COLOR][/FONT]**[/FONT]

From the [**_Ubuntu Forums Code of Conduct_**]("http://ubuntuforums.org/index.php?page=policy"):

[QUOTE=Forum Code of Conduct]
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.[/QUOTE]

---

### Post by nirajandps on 2010-11-17
> **bab1 said:**
> From the [**_Ubuntu Forums Code of Conduct_**]("http://ubuntuforums.org/index.php?page=policy"):

Hi!

I don't want anyone to do my work. I just thought may be someone else has gone through the same problem. But I have solved the issue. I think you didn't went through the post thoroughly I never said any one to do my work. 

In any case, thank you and if someone is stuck in the same problem, I may be helpful.

Thank you

---

