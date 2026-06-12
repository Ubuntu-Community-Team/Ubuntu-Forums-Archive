---
title: "Joining Ubuntu 10.04 in active directory"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-09-20
Hi

i'm having problems joining my fresh install of ubuntu 10.04 in active directory.

- i've installed likewise-open 5.4
- edit /etc/resolv.conf and put the server ip
- edit /etc/nsswitch.conf and change the line hosts to: **hosts: files dns [NOTFOUND=return]**   (because i'm using a domain that as the .local prefix

- sudo domainjoin-cli join mydomain.local Administrator
- enter the administrator password

and after all the steps i have this error:
[B]error: Lsass Error [code 0x00080047]
87 (0x57) ERROR_INVALID_PARAMETER - Unknown error[/B]

I don't know what i can do more.
Hope someone can help me

many thanks

---

### Post by guimenez on 2010-09-20
i've finally solved this problem.
i've installed the last likewise-open package version 6
and now i can join to domain.

Now, my problem is that i can't login to domain :(

in the login screen i put DOMAIN.LOCAL\user
then i put the password but it fails to login

any help?

thanks

---

### Post by HelpyHelperton on 2010-09-20
> **guimenez said:**
> i've finally solved this problem.
i've installed the last likewise-open package version 6
and now i can join to domain.
 
Now, my problem is that i can't login to domain :(
 
in the login screen i put DOMAIN.LOCAL\user
then i put the password but it fails to login
 
any help?
 
thanks
 
 
Have you tried:
 
DOMAIN\user
 
You can also set AssumeDefaultDomain to 1
 
/opt/likewise/bin/lwconfig AssumeDefaultDomain 1
 
Make sure you're using the latest version of Open from the Website 6.0.8269
 
After you set this, you can login with just 'user' instead of 'DOMAIN\user'.

---

### Post by guimenez on 2010-09-21
> **HelpyHelperton said:**
> Have you tried:
 
DOMAIN\user
 
You can also set AssumeDefaultDomain to 1
 
/opt/likewise/bin/lwconfig AssumeDefaultDomain 1
 
Make sure you're using the latest version of Open from the Website 6.0.8269
 
After you set this, you can login with just 'user' instead of 'DOMAIN\user'.
It doesn't work.
i've try DOMAIN\user and nothing
and i don't have nothing in /opt folder (likewise does't exist)

if i put **kinit [email]user@domain.local[/email]**  it ask me for a password and it works well when i put the right password.

if i put **sudo ssh user@localhost** it ask me for a password and it says that is always wrong :(

i don't know what is happening.

thanks

---

### Post by guimenez on 2010-10-10
Please, any help on this?

thanks

---

### Post by luvshines on 2010-10-11
Did you get a chance to look at this:
[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/567473](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/567473)

What does these files say:
```

cat /etc/nsswitch.conf | egrep "^passwd|^group|^shadow"
cat /etc/pam.d/sshd
cat /etc/pam.d/common-auth
```

Maybe you would also like to check auth logs to see what may be going wrong

Also, if this works:
```
wbinfo -a <DOMAIN-NAME>\\<username>%<passwd>
```

---

### Post by dmizer on 2010-10-11
Have a look here: [http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)

---

### Post by atworkwithjf on 2010-10-11
[guimenez]("http://ubuntuforums.org/member.php?u=385263"),

The first thing you may want to check is if you can actually see your domain controller and if your machine is talking to your DNS server properly.

I'll assume your domain controller is also your DNS server.

Can you ping your DC?

If not let's have a look at your nsswitch.conf

One of the things that changed recently in Ubuntu was the hosts resolution order...

The defaults are now:
```

    hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```The problem here is that if you're not using multicast DNS or files, it bails and so you'll have no host resolution.  I'd contend that this should read:
```

    hosts:          files mdns4_minimal [NOTFOUND=continue] dns mdns4

```This would actually insure that dns is considered in the absence of mdns4_minimal (otherwise why even bother having dns in the options???!!!)

So I would advise you start by making that single change and then seeing if it resolves any DNS issues.

Then I would try joining the domain again.  If you are using 6.0 your install lopcation _should_ be /opt/likewise

usiong sudo join the domain and make sure it succeeds.  It should say SUCCESS!
```

> sudo /opt/likewise/bin/domainjoin-cli join MYDOMAIN.COM Administrator

```It will prompt you for the Admin password for your DC and then it shold join without issue.

Let's start there and if problems persist let me know and I'll see is I can help further.

-atworkwithjf

---

### Post by guimenez on 2010-10-12
> **atworkwithjf said:**
> [guimenez]("http://ubuntuforums.org/member.php?u=385263"),

The first thing you may want to check is if you can actually see your domain controller and if your machine is talking to your DNS server properly.

I'll assume your domain controller is also your DNS server.

Can you ping your DC?

If not let's have a look at your nsswitch.conf

One of the things that changed recently in Ubuntu was the hosts resolution order...

The defaults are now:
```

    hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```The problem here is that if you're not using multicast DNS or files, it bails and so you'll have no host resolution.  I'd contend that this should read:
```

    hosts:          files mdns4_minimal [NOTFOUND=continue] dns mdns4

```This would actually insure that dns is considered in the absence of mdns4_minimal (otherwise why even bother having dns in the options???!!!)

So I would advise you start by making that single change and then seeing if it resolves any DNS issues.

Then I would try joining the domain again.  If you are using 6.0 your install lopcation _should_ be /opt/likewise

usiong sudo join the domain and make sure it succeeds.  It should say SUCCESS!
```

> sudo /opt/likewise/bin/domainjoin-cli join MYDOMAIN.COM Administrator

```It will prompt you for the Admin password for your DC and then it shold join without issue.

Let's start there and if problems persist let me know and I'll see is I can help further.

-atworkwithjf

thanks for replying

i've change the nsswitch.conf, because without that i can't join the domain
my nssswitch.conf as hosts: files dns

i've successfully join the domain, the main problem its that i can't login :(

i don't know how to start 

thanks

---

### Post by guimenez on 2010-10-12
this is my configuration files:

---------------- /etc/pam.d/common-auth ---------------
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_lsass.so try_first_pass
auth	requisite	 pam_deny.so
auth	required	 pam_permit.so
auth	optional	 pam_mount.so 
session	optional	 pam_mount.so 


---------------- /etc/pam.d/common-session -------------
session	[default=1]	 pam_permit.so
session	requisite	 pam_deny.so
session	required	 pam_permit.so
session	required	pam_unix.so 
session	sufficient	pam_lsass.so 
session	optional	pam_mount.so 
session	optional	pam_ck_connector.so nox11


--------------- /etc/pam.d/login ------------------------
auth optional pam_faildelay.so delay=3000000
auth required pam_securetty.so
auth requisite pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required pam_env.so readenv=1
session required pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth optional pam_group.so
session required pam_limits.so
session optional pam_lastlog.so
session optional pam_motd.so
session optional pam_mail.so standard
@include common-account
@include common-session
@include common-password
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional pam_mount.so 
auth optional pam_mount.so try_first_pass

----------------------------------------------------------------------

thanks and hope someone can help me

this config work well in ubuntu 10.04 but not in the new ubuntu 10.10

---

### Post by guimenez on 2010-10-12
when i execute this command:    ssh [email]user@domain.local[/email]

it says connection fail and is ask me for my password and then gives the message permission denied

---

### Post by luvshines on 2010-10-12
> **guimenez said:**
> when i execute this command:    ssh [email]user@domain.local[/email]

it says connection fail and is ask me for my password and then gives the message permission denied

Are you trying to ssh to domain controller ??

In comment #6, I asked for nsswitch.conf and sshd PAM file and wbinfo command
Also in comment #7, the link has a zipped folder which contains some PAM file and nsswitch templates, have a look

I can't see 'winbind.so' anywhere in the PAM files you posted in Comment #10

Are you sure it is working with 10.04 ?

---

### Post by guimenez on 2010-10-12
i'm using likewise-open and its not compatible with winbind

and winbind doesn't exist now on Ubuntu 10.10 :(

i'm using ssh just for test purpose

if i use     $kinit user

the system identify correctly the user  "user@domain.local" and it ask for a password, and when i enter the password it works well.

but in the gdm login or ssh not :(

thanks

---

### Post by luvshines on 2010-10-12
> **guimenez said:**
> i'm using likewise-open and its not compatible with winbind

and winbind doesn't exist now on Ubuntu 10.10 :(

i'm using ssh just for test purpose

if i use     $kinit user

the system identify correctly the user  "user@domain.local" and it ask for a password, and when i enter the password it works well.

but in the gdm login or ssh not :(

thanks

Ah!! Sorry, missed the Likewise thing

What does ssh <AD-domain-name>\\<username>@localhost say ?

I hope you are using the name in its correct format(5.2, 5.3):
[http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-51-guide.html#id2562120](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-51-guide.html#id2562120)

---

### Post by guimenez on 2010-10-12
it says:

ssh: connect to localhost port 22: Connection refused

if i list my domain users it show all users

thanks

---

### Post by luvshines on 2010-10-12
> **guimenez said:**
> it says:

ssh: connect to localhost port 22: Connection refused

if i list my domain users it show all users

thanks

You have openssh-server installed on the machine to which you are trying to ssh(the machine which is configured against Active Directory) ?

---

### Post by guimenez on 2010-10-12
No i didn't

i've installed openssh-server and try it: ssh domain\\user@localhost

now it say: the authenticity of host 'localhost (::1)' can't be estabilished

then it ask me for continue and then is ask my user password and says: permission denied, please try again.



thanks

---

### Post by atworkwithjf on 2010-10-12
[guimenez]("http://ubuntuforums.org/member.php?u=385263"),

A couple things.

First, make sure SELinux is disabled.  Second, if you have not explicitly set the use default domain option for LikewiseOpen, you will need to prepend the domain to the username when logging in:
```

    DOMAIN\username

```
I also am curious if you rebooted your machine after the installation.   Rather than go through every service and restart them individually,  let's just do that to make sure everything is restarted properly.

I'm going to assume you're using the 6.0 version as opposed to the older 5.x version in the apt-get repo.  Run the following command:
```

    > sudo /opt/likewise/bin/lw-get-status

```

- atworkwithjf
Open Source Community Engineer
Likewise Software

---

### Post by guimenez on 2010-10-13
> **atworkwithjf said:**
> [guimenez]("http://ubuntuforums.org/member.php?u=385263"),

A couple things.

First, make sure SELinux is disabled.  Second, if you have not explicitly set the use default domain option for LikewiseOpen, you will need to prepend the domain to the username when logging in:
```

    DOMAIN\username

```
I also am curious if you rebooted your machine after the installation.   Rather than go through every service and restart them individually,  let's just do that to make sure everything is restarted properly.

I'm going to assume you're using the 6.0 version as opposed to the older 5.x version in the apt-get repo.  Run the following command:
```

    > sudo /opt/likewise/bin/lw-get-status

```

- atworkwithjf
Open Source Community Engineer
Likewise Software

Once again thanks for help me :D

i've installed last likewise-open, because the new Ubuntu 10.10 only join the domain with this version.

i'm trying using at gdm login this: DOMAIN\user or just user (i ticked the using of prefix)
but nothing, it doesn't give me any error just ask again for login.

i run the command:  > sudo /opt/likewise/bin/lw-get-status

and the log is in the file sudo that i've attached.

thanks

---

### Post by atworkwithjf on 2010-10-14
Which version of Likewise-Open is this?  You realise that 10.10 is not yet supported correct?

---

### Post by guimenez on 2010-10-14
> **atworkwithjf said:**
> Which version of Likewise-Open is this?  You realise that 10.10 is not yet supported correct?

No i didn't know that. I will wait for a new version

Thanks

---

