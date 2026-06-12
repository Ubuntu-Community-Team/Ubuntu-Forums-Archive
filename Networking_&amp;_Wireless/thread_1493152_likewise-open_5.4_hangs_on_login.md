---
title: "likewise-open 5.4 hangs on login"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by johnbuntu on 2010-05-25
I'm running Ubuntu 10.04 Server x86 64-bit and installed likewise-open, which I think is version 5.4.  I can authenticate with Active Directory credentials, but it seems to hang when I log in.  I can press Ctrl-C and break out of the hang, but was interested to see what was causing the behavior.  I noticed lsassd was taking up about 99% of CPU while in this hung state.  I then did a 
```
tail -f /var/log/syslog
```
and discovered lsassd was doing some type of query for what appeared to by every user in our Active Directory as I saw hundreds of entries like this being added to the syslog:
```
May 25 14:21:27 coe-web lsassd[1225]: 0x7f5bc72c1710:The user attributes in the cache data for 'domain\johndoe' are invalid. The cache database or user data in Active Directory could be corrupt.
```
Is there some setting I can change so it doesn't do this?

---

### Post by johnbuntu on 2010-05-27
This seemed to do the job:
$ sudo lwregshell
cd [HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory\]
set_value MemoryCacheSizeCap 1048576
set_value NssGroupMembersQueryCacheOnly 1
set_value CacheType "memory"
exit
$ sudo lwsm refresh lsass
$ sudo /etc/init.d/lsassd restart

---

### Post by transformania on 2010-06-28
Thank you so much for posting this solution.

Works great.

---

### Post by transformania on 2010-06-28
I should mention that this solved a different, but related, problem for me, which was that when I right-clicked on a file or folder in Gnome/Nautilus and chose Properties, lsassd and nautilus processes would use between 60 and 100 percent of my cpu for about 3 minutes, then finally show the properties box.

---

### Post by b0z0n3 on 2010-07-26
> **johnbuntu said:**
> This seemed to do the job:
$ sudo lwregshell
cd [HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory\]
set_value MemoryCacheSizeCap 1048576
set_value NssGroupMembersQueryCacheOnly 1
set_value CacheType "memory"
exit
$ sudo lwsm refresh lsass
$ sudo /etc/init.d/lsassd restart

This fixed my problem with konsole taking forever to give me a prompt.

Thanx!

---

### Post by hosungs on 2010-09-22
I applied the commands, and it seemed to correct the issue initially. However, after a while, I found that lsassd crashed and thus didn't allow any AD user login. I'm wondering if anyone has also experienced this type of problem? Thanks.

---

### Post by hosungs on 2010-09-27
I'm following up on my own question (previous reply). When I try this approach (memory cache), any AD login trial crashes lsassd with the following syslog:

Sep 27 14:34:40 icsc kernel: [513664.923643] lsassd[16708]: segfault at 3331352d30 ip 00007ff555dbc6e7 sp 00007ff54db82808 error 6 in liblsacommon.so.0.0.0[7ff555d9f000+24000]

I also believe this behavior is related to some system instabilities I've been experiencing these days when I let multiple users log on to the Linux server with their AD credentials. When I try such simultaneous logons with my students, the system seems hanging strangely. The actual phenomenon is, shell prompts are there, but most commands like 'w', 'sudo', ... hang up. 'ls' works though properly listing directory contents. It's almost impossible to reproduce deterministically. It only happens some times when quite a few student users log on to my Linux server simultaneously. Today I guess I finally found a fix --- restarting lsassd does return the system to a usable state, but of course that fix is not very satisfactory. Any help or pointer would be greatly appreciated. Thanks.

FYI, the Linux server I'm mentioning is Ubuntu 10.04 server x64, and the Likewise-open version I'm using is 5.4.0.42111-3~ppa7. I had to install the PPA version to fix the default-domain issue (which might have been configured through /etc/samba/lwiauthd.conf).

---

### Post by atworkwithjf on 2010-10-12
For users who are not married to using the version provided in the repository it's highly suggested that they download the most updated version from Likewise's website ([www.likewise.com]("http://www.likewise.com")) as there are a number of fixes that are not in the repo version (it actually takes some time for those updates to make it through a number of hoops).

Likewise-open 6.0 resolves a number of outstanding issues.

If you have to use one of the versions in one of the many available repos then the ppa packages are your best source for updated versions for your platform.

[https://launchpad.net/~likewise-open/+archive/likewise-open-ppa/+packages](https://launchpad.net/~likewise-open/+archive/likewise-open-ppa/+packages)

---

