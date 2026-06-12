---
title: "rlimit_max (1024) below minimum Windows limit (16384)"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2010-03-12
Anyone getting that error when running testparm on their samba.conf file?

How can it be resolved?

---

### Post by tad1073 on 2010-03-15
bump

---

### Post by tad1073 on 2010-03-15
I am only bumping this because it will be my 1000 post whooohoooo!!!!!!!

---

### Post by nikclev on 2010-04-25
I'm getting the same message when I run testparm, no idea what it means either.

---

### Post by Nelse on 2010-04-28
I'm getting the same thing too.  I can connect to the Internet but cannot see any other computers on my network.

---

### Post by draxx31 on 2010-04-30
I have the same problem than you...

---

### Post by peter3 on 2010-05-04
Add the line:

*    -    nofile    16384

to your /etc/security/limits.conf    file
and reboot.

It worked for me.

---

### Post by johnd16 on 2010-05-13
On my freshly installed 10.04 (Linux samba 2.6.32-22-server #33-Ubuntu  SMP) with minimal packages, 
adding "* - nofile 16384" to /etc/security/limits.conf 
doesn't change the testparm output after a reboot.  

# testparm  still returns: "rlimit_max: rlimit_max (1024) below minimum  Windows limit (16384)"

Even tried enabling/adding "session required pam_limits.so" to  /etc/pam.d/su and reboot
Result of testparm is identical: "rlimit_max: rlimit_max (1024) below  minimum Windows limit (16384)"

Any suggestions how to correctly remove the rlimit_max warning?

---

### Post by bartbr on 2010-05-15
> **peter3 said:**
> Add the line:

*    -    nofile    16384

to your /etc/security/limits.conf    file
and reboot.

It worked for me.



It worked for me too! Thank you!  :P


I found this reference: [http://lists.samba.org/archive/samba/2010-January/153331.html](http://lists.samba.org/archive/samba/2010-January/153331.html)

---

### Post by Strongman332 on 2010-05-20
i have tried this and it did not work for me

---

### Post by ***J*** on 2010-06-10
Does anyone know why this comes up?

---

### Post by Leppie on 2010-06-24
just tested this on my lucid server and works like a charm.

---

### Post by Morbius1 on 2010-06-24
[http://lists.samba.org/archive/samba/2010-January/153320.html](http://lists.samba.org/archive/samba/2010-January/153320.html) :
> On Mon, Jan 25, 2010 at 11:44:03AM +0000, Miguel Medalha wrote:
>
> I just installed samba on a new server, 3.4.5-42, 64 bit version from  
> Sernet, over CentOS 5.4.
>
> When running testparm, I get the following warning:
>
> rlimit_max: rlimit_max (8192) below minimum Windows limit (16384)
>
> I searched Google for some answer but I couldn't find a satisfactory  
> one. What should I do to solve this?
> Can someone from the Samba team enlighten me on this?

It's a warning, you can safely ignore it. Windows 7 clients need to
have exactly the same number of open handles available as Windows
servers, else it fails in some file copy situations with a "out of
handles" message. Samba has taken care of it for you, but it's just
letting you know your fd limit is set a bit low.

Jeremy



---

### Post by Leppie on 2010-06-24
haha, that's good to know. so both scenarios work :)

---

### Post by jringoot on 2010-08-25
> **Strongman332 said:**
> i have tried this and it did not work for me

It does not work for me either.
It is not ubuntu specific though, you can have the error on Centos 5:

[http://lists.samba.org/archive/samba/2010-January/153331.html](http://lists.samba.org/archive/samba/2010-January/153331.html)

and solaris as well:

[http://lists.samba.org/archive/samba/2010-February/153949.html](http://lists.samba.org/archive/samba/2010-February/153949.html)

---

### Post by mybconsulting on 2010-10-27
Hi! I tried this issue but the problem is still present:

rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)

thank you :(

---

### Post by Morbius1 on 2010-10-27
Please see post #13.

It's not a problem that needs to be fixed.

---

### Post by trevelyon on 2010-12-17
This did not work for me either (new lucid install).  I noticed that the * domain specification does not apply to root (according to the files).  Basically, this worked for me:

Add the lines:

* - nofile 16384
root - nofile 16384

to your /etc/security/limits.conf file
and reboot.


I really only needed the root line but include the * to be complete in providing a true *.  Hope this helps,

---

### Post by SciFi-Bob on 2011-02-10
The line 
root - nofile 16384
worked for me, but I guess it's because it was a server that I never log in to as an ordinary user - just root.
Otherwise, you may need the "* - nofile 16384" line, or more exactly, replace the "*" with the user running samba.

I did not have to reboot though, just logout and in again, then the warning was gone.
I have not yet tried to reboot the server, so I don't know if this setting will survive a reboot - but it would be strange if not..

---

### Post by psyncho on 2011-03-21
might not want to just blindly start changing config files, in general.  

For this particular item, not sure if this has been addressed yet, but here's a security reason for that setting of 1024

[https://lists.ubuntu.com/archives/ubuntu-devel/2010-September/031446.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-September/031446.html)

---

### Post by rhoyerboat on 2011-05-12
I wonder if this warning from testparm will indicate any impact on the performance of samba, does anyone have any experience with that?

---

### Post by ozkr on 2011-08-17
I found a solution in this site:

[http://www.gtkdb.de/index_7_1240.html](http://www.gtkdb.de/index_7_1240.html)

:D

---

### Post by Phil Binner on 2011-08-17
I have a slightly different, but probably related problem. testparn includes the output

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)

I have not been able to get the command

testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf 

to update the smb.conf, however, I get permission denied, or some such. I think I would have to log in as root to make this work, so I just updated smb.conf with sudo gedit instead. That would have prevented the change from being done.

Anyone know how I can get testparm to output the new file, i.e. how i get teh permission to work.

In the meantime I'll try your fix. Thanks.

---

### Post by capscrew on 2011-08-17
> **Phil Binner said:**
> I have a slightly different, but probably related problem. testparn includes the output

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)

I have not been able to get the command

testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf 

to update the smb.conf, however, I get permission denied, or some such. I think I would have to log in as root to make this work, so I just updated smb.conf with sudo gedit instead. That would have prevented the change from being done.

Anyone know how I can get testparm to output the new file, i.e. how i get teh permission to work.

In the meantime I'll try your fix. Thanks.

There is no *fix* -- There is no error.  This has been mentioned several times in this thread.  The answer is:  Leave it alone.  This is meant as a notification only.

---

### Post by Phil Binner on 2011-08-17
Yes, but the problem is that I get the same symptoms. I can't see any other computers, Windows or Ubuntu, and they can't see me. Without Samba I can at least see the windows machines.

---

### Post by capscrew on 2011-08-17
> **Phil Binner said:**
> Yes, but the problem is that I get the same symptoms. I can't see any other computers, Windows or Ubuntu, and they can't see me. Without Samba I can at least see the windows machines.

The symptoms you are referring to are not related in any way to the subject of: **rlimit_max (1024) below minimum Windows limit (16384)**.  They are best resolved in the other thread you started.

---

### Post by Skorzen on 2011-08-24
> **bartbr said:**
> It worked for me too! Thank you!  :P


I found this reference: [http://lists.samba.org/archive/samba/2010-January/153331.html](http://lists.samba.org/archive/samba/2010-January/153331.html)

Worked for me.

Samba version: samba3x-3.5.4-0.70.el5_6.1

---

### Post by Morbius1 on 2011-08-24
This thread simply will not die.
> **capscrew said:**
> There is no *fix* -- There is no error.  This  has been mentioned several times in this thread.  The answer is:  Leave  it alone.  This is meant as a notification only.

---

### Post by mmerlone on 2012-03-05
> **capscrew said:**
> There is no *fix* -- There is no error.  This has been mentioned several times in this thread.  The answer is:  Leave it alone.  This is meant as a notification only.

Sort of. The message per se is not an error, but can lead to one. I manage a small network with 100+ users, and once in a while I hit the limit and some clients gets errors when trying to connect to a service.

Or, in other words, you will get an error when samba hit the limit.

---

### Post by 10nchik on 2012-09-13
ulimit -n 16384

copypast from:
[http://how-it.ru/public/root/110-samba__preduprezhdenie__rlimit_max__rlimit_max__1024__below_minimum_windows_limit__16384__.html](http://how-it.ru/public/root/110-samba__preduprezhdenie__rlimit_max__rlimit_max__1024__below_minimum_windows_limit__16384__.html)

---

### Post by freesbee on 2012-10-11
> **peter3 said:**
> Add the line:

*    -    nofile    16384

to your /etc/security/limits.conf    file
and reboot.

Didn't work for me as well 
My installation is fresh Ubuntu 12.04 with samba 3.6.3

---

### Post by Morbius1 on 2012-10-12
> **Morbius1 said:**
> [http://lists.samba.org/archive/samba/2010-January/153320.html](http://lists.samba.org/archive/samba/2010-January/153320.html) :

On Mon, Jan 25, 2010 at 11:44:03AM +0000, Miguel Medalha wrote:

>
> I just installed samba on a new server, 3.4.5-42, 64 bit version from  
> Sernet, over CentOS 5.4.
>
> When running testparm, I get the following warning:
>
> rlimit_max: rlimit_max (8192) below minimum Windows limit (16384)
>
> I searched Google for some answer but I couldn't find a satisfactory  
> one. What should I do to solve this?
> Can someone from the Samba team enlighten me on this?

[COLOR=Blue]It's a warning, you can safely ignore it. Windows 7 clients need to
have exactly the same number of open handles available as Windows
servers, else it fails in some file copy situations with a "out of
handles" message. **Samba has taken care of it for you**, but it's just
letting you know your fd limit is set a bit low.[/COLOR]

Jeremy
It's not an issue that needs to be fixed.

---

### Post by low351 on 2013-09-09
> **peter3 said:**
> Add the line:

*    -    nofile    16384

to your /etc/security/limits.conf    file
and reboot.

It worked for me.

This worked for me as well thank you!

Note: the reboot isn't necessary, just log out and log back in.

---

### Post by oreodoh2 on 2014-04-24
> **peter3 said:**
> Add the line:

*    -    nofile    16384

to your /etc/security/limits.conf    file
and reboot.

It worked for me.

Also worked for me - thanks for the fix!

---

### Post by Pablo_Daniel_Carne on 2014-05-07
to apply the setting to root you need to add the following line in /etc/security/limits.conf
----------
root   -   nofile 16384
----------
reboot, and then test with ulimit -a | grep "open files"
below setting only applies to normal users:
----------
*   -   nofile   16384
----------

---

### Post by it.helpdesk.getech on 2014-10-05
Thank you for the tip it word for me as well I just need to reboot and it's not there anymore. Now can someone tell me what the error mess is all about.

---

### Post by Morbius1 on 2014-10-05
Still hasen't changed from 4 years ago.
> [http://lists.samba.org/archive/samba/2010-January/153320.html](http://lists.samba.org/archive/samba/2010-January/153320.html) :

On Mon, Jan 25, 2010 at 11:44:03AM +0000, Miguel Medalha wrote:

>
> I just installed samba on a new server, 3.4.5-42, 64 bit version from  
> Sernet, over CentOS 5.4.
>
> When running testparm, I get the following warning:
>
> rlimit_max: rlimit_max (8192) below minimum Windows limit (16384)
>
> I searched Google for some answer but I couldn't find a satisfactory  
> one. What should I do to solve this?
> Can someone from the Samba team enlighten me on this?

[COLOR=Blue]It's a warning, you can safely ignore it. Windows 7 clients need to
have exactly the same number of open handles available as Windows
servers, else it fails in some file copy situations with a "out of
handles" message. **Samba has taken care of it for you**, but it's just
letting you know your fd limit is set a bit low.[/COLOR]

Jeremy

Jeremy is Jeremy Allison, one of the developers of Samba so you'd think his comments would carry some weight. I mean if he doesn't know how it works then we should all start using NFS.

---

