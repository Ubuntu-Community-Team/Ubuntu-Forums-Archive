---
title: "Samba - Specific Active Directory permissions question"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by dave562 on 2009-06-24
Thanks to a lot of great documentation provided by the community I have been able to get my Ubuntu box (8.04 LTS) joined to my Active Directory domain.  With a combination of Kerberos, PAM and WinBind I can log onto the Ubuntu box with accounts from the domain.  I'm having a problem configuring the Samba share though.

I specifically want to control access to the Samba share, and limit access to a particular Active Directory account.  I have seen a lot of different smb.conf examples regarding this issue, but I haven't been able to get any of them to work.

Can someone share an example that shows how to limit read/write access to a share based on Active Directory user accounts?

So far I have tried the following

read list = <account name>
read list = @<domain>+<account name>
Valid Users = <account name>
Valid Users = @<domain>+<account name>

With "Valid Users", when I attempt to connect to the share I am prompted for a user name and password.  I've tried every possible permutation of valid combinations and I can't access the share.  With "read list", I just get the standard Windows error message about not having permission to access the share.

Thanks in advance for any help.

---

### Post by dave562 on 2009-06-24
I have been doing some further tweaking of the smb.conf file and the following configuration is the closest I have gotten to a working config.  At this point, when I attempt to connect to the share from a Windows box, I am prompted for a username and password.

Can someone take a look at my smb.conf and suggest how I need to adjust it?  The values in ()'s are legit values, but I've obfuscated them here for security reasons.

Could the problem be that I am using both a "realm" and "workgroup"?

-------------

[global]
        security = ads
        realm = (domain name in caps)
        password server = (FQDN of domain controller)
        workgroup = 2CP
        winbind refresh tickets = yes
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2

[test]
        path = /home/2CP/darmstrong
        valid users = test, itadmin
        write list = test, itadmin
        read list =

---

### Post by jb1023 on 2009-08-24
Dave, did you ever find a solution to this issue?  I am running into the this right now but can't really find any straight forward solutions.  Thanks.

---

### Post by dave562 on 2009-08-25
JB,

In my case the issue turned out to be the line

winbind separator = '\'

It seems that Samba has some problems parsing the smb.conf file and when it treats the \ as an escape character.  With the above line in the configuration file, the actual winbind separator is '.
When defining domain user and groups under the share definition, they need to be in the format of (domain)'(user or group).  Not (domain)\(user or group).  Make sense?

It seems like a lot of people prefer to use the + as an alternate separator.  In that case, the line in smb.conf would be

winbind separator = +

And then your share definitions would be (domain)+(user or group).

---

