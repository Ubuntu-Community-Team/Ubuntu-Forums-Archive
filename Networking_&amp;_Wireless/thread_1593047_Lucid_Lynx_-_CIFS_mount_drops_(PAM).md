---
title: "Lucid Lynx - CIFS mount drops (PAM)"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by idhw on 2010-10-11
Good morning everyone,

I've seem to have run into another issue in Lucid unfortunately. One of my two CIFs, using pam mount, seems to keep dropping and unmounting itself. I checked the syslog and stumbled across these entries:

```
Oct 11 09:09:02 cli59 kernel: [ 1680.124744] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 09:09:02 cli59 kernel: [ 1680.124754]  CIFS VFS: Send error in SessSetup = -13
Oct 11 09:09:02 cli59 kernel: [ 1680.124763]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 09:09:02 cli59 CRON[1959]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 11 09:17:01 cli59 kernel: [ 2159.521737] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 09:17:01 cli59 kernel: [ 2159.521747]  CIFS VFS: Send error in SessSetup = -13
Oct 11 09:17:01 cli59 kernel: [ 2159.521755]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 09:17:01 cli59 CRON[2080]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 11 09:39:01 cli59 kernel: [ 3479.319950] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 09:39:01 cli59 kernel: [ 3479.319960]  CIFS VFS: Send error in SessSetup = -13
Oct 11 09:39:01 cli59 kernel: [ 3479.319969]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 09:39:01 cli59 CRON[2179]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 11 10:09:01 cli59 kernel: [ 5279.296232] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:09:01 cli59 kernel: [ 5279.296241]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:09:01 cli59 kernel: [ 5279.296250]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:09:01 cli59 CRON[2399]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 11 10:17:01 cli59 kernel: [ 5759.112499] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:17:01 cli59 kernel: [ 5759.112509]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:17:01 cli59 kernel: [ 5759.112517]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:17:01 cli59 CRON[2503]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 11 10:39:01 cli59 kernel: [ 7079.739888] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:39:01 cli59 kernel: [ 7079.739898]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:39:01 cli59 kernel: [ 7079.739906]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:39:01 cli59 kernel: [ 7079.839269] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:39:01 cli59 kernel: [ 7079.839280]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:39:01 cli59 kernel: [ 7079.839288]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:39:01 cli59 CRON[2550]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 11 10:56:39 cli59 kernel: [ 8137.656546] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:56:39 cli59 kernel: [ 8137.656555]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:56:39 cli59 kernel: [ 8137.656564]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:56:39 cli59 kernel: [ 8137.781358] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:56:39 cli59 kernel: [ 8137.781369]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:56:39 cli59 kernel: [ 8137.781379]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:56:46 cli59 kernel: [ 8144.480107] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:56:46 cli59 kernel: [ 8144.480117]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:56:46 cli59 kernel: [ 8144.480126]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 10:56:46 cli59 kernel: [ 8144.618956] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 10:56:46 cli59 kernel: [ 8144.618967]  CIFS VFS: Send error in SessSetup = -13
Oct 11 10:56:46 cli59 kernel: [ 8144.618975]  CIFS VFS: cifs_mount failed w/return code = -13
Oct 11 11:09:01 cli59 kernel: [ 8879.430080] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Oct 11 11:09:01 cli59 kernel: [ 8879.430091]  CIFS VFS: Send error in SessSetup = -13
Oct 11 11:09:01 cli59 kernel: [ 8879.430099]  CIFS VFS: cifs_mount failed w/return code = -13

```-13 seems to refer to a permission denied problem, which is something that has me utterly confused. It CAN mount when I log in but then drops and mentions a permission denied problem?

Here's my pam mount conf showing the shares:
```

  GNU nano 2.2.2                                                 File: /etc/security/pam_mount.conf.xml                                                                                                        

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
        See pam_mount.conf(5) for a description.
-->

<pam_mount>

                <!-- debug should come before everything else,
                since this file is still processed in a single pass
                from top-to-bottom -->

<debug enable="1" />

                <!-- Volume definitions -->


                <!-- pam_mount parameters: General tunables -->

<!--
<luserconf name=".pam_mount.conf.xml" />
-->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<logout wait="0" hup="0" term="0" kill="0" />


                <!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="false" />
<volume fstype="cifs" server="svridh01" path="grp00" mountpoint="/mnt/grp00" options="nobrl,workgroup=IDHW"/>
<volume fstype="cifs" server="svridh01" path="%(DOMAIN_USER)" mountpoint="/mnt/home/%(DOMAIN_USER)" options="nobrl,workgroup=IDHW"/>

</pam_mount>





```Anyone out there that knows what is going on?

Dean.

EDIT:: Whoops, forgot to mention which one. D'oh! It's the "grp00" one.

---

### Post by dmizer on 2010-10-11
> **idhw said:**
> Anyone out there that knows what is going on?

I would highly suggest looking carefully at the grp00 server side of things. Perhaps an overzealous firewall or some other kind of network security software is getting in the way occasionally. If you have a firewall on your Lucid box, try disabling that for a while and see how that works.

---

### Post by idhw on 2010-10-12
> **dmizer said:**
> I would highly suggest looking carefully at the grp00 server side of things. Perhaps an overzealous firewall or some other kind of network security software is getting in the way occasionally. If you have a firewall on your Lucid box, try disabling that for a while and see how that works.

Thanks for the reply, I disabled the firewall but that doesn't seem to make a difference. Furthermore, the home share and grp00 share are both on the same server and the home share works just peachy. And lastly, a colleague of mine is using ubuntu 8.04 with the same share and set up, and it works great on his computer.

It really is quite a curious issue.

_***EDIT:: I might be getting close. Having a document open that is located on the share seems to prevent the share from unmounting...***_

---

### Post by idhw on 2010-10-14
*BUMP* The solution is so close guys, I can feel it. 
_***Having a document open that is located on the share seems to prevent the share from unmounting...***_

---

### Post by grimmo on 2010-10-28
Hi I have experienced a very similar issue when upgrading to 10.10 from 10.04
In my case the problem was due to my local username on ubuntu being different from my domain username. On 10.04 I could force my luser .pam_mount.conf to pass the username field to cifsmount
On 10.10 it doesn't work anymore. :-x
My workaround has been to hardcode my domain username directly into /etc/security/pam_mount.conf.xml options inside the cifsmount tags:

my modified version:

> <cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o "user=MYDOMAIN\\myusername,uid=%(USERUID),gid=%(USERGID)%,(before=\",\" OPTIONS)"</cifsmount>

mantainer version:

> <cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%,(before=\",\" OPTIONS)"</cifsmount>

of course this is fine for me, being the only user of this machine, but it wouldn't be feasible for a multiuser one. 
Probably there is a proper way to map local user names to domain ones, but I couldn't find it.

---

### Post by bslash on 2010-12-28
It has something to do with the connection being opened multiple times, by being included from the 'common-xxx' stanzas multiple times.

In our case, the solution was to:
- Comment out all mentions of pam_mount from all the common-... files in /etc/pam.d/  (that would be common-auth, common-session and common-session-interactive in a standard setup)
- add pam_mount ONLY to /etc/pam.d/gdm, you have to add it twice so that it looks like this:

```
[INDENT]auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_mount.so enable_pam_password
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session optional        pam_mount.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password[/INDENT]
```


that should do it. Notice that "enable_pam_password" is the new "use_first_pass"...

---

