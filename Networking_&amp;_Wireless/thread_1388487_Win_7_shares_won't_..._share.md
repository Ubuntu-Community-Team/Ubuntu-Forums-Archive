---
title: "Win 7 shares won't ... share"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by castalla on 2010-01-23
Briefly - ubuntu box sees shares on Vista box.  Vista box sees shares on Win 7 box.  Ubuntu sees Win 7 box but won't list shares.  All access is via Everyone.

I'm using smbnetfs to manage network shares.

I've read possibly 100s of tips on how to solve this Win 7 problem - none of which work (either for me, or original posters!).

Surely, there must be a solution?  

(ps: Windows Live Asst isn't installed on the win 7 box!)

This is the testparm dump when smbnetfs is running:

Press enter to see a dump of your service definitions

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

### Post by dmizer on 2010-01-23
First of all, make sure both your Windows 7 and Ubuntu are configured correctly by visiting the 6th link in my sig.

Second of all, Windows 7 seems to be hell bent on wanting you to use "HomeGroup" file sharing, but this will not work with Samba, it will only work with other Windows 7 computers. In order to get regular file sharing to work, you'll need to click on the "Change advanced sharing settings", and make sure you have network discovery, file and printer sharing, and public folder sharing enabled in the "home or work" profile (also, make sure that "home or work" is labeled as your current profile). You should be able to use 128 bit encryption, and use either enable or disable password protected shares (depending on how much security you desire).

Then, go to "Change adapter settings", right click on your connection and select "properties". Click on the "Internet protocol version 4 (tcp/ipv4)" and select "properties". Then click on "advanced ..." (at the bottom), and select the "WINS" tab. Make sure that "Enable LMHOSTS lookup" is enabled (no need to import), and make sure that "default" is selected for NetBIOS setting.

Now, go to a folder (try the public folder first), and right click on it. Select "properties", and click on the "sharing" tab. Click on "Advanced sharing", and put a check mark in "Share this folder". Change the "share name" if you like, and click on the "permissions" button. Make sure you have permissions set as you desire (a checkmark in "change" = writeable). If you've enabled password protected shares, you'll have to tweak settings here to make sure that your Ubuntu user is included for permission.

Once this is all set, then your folder will show "shared" and it's network path will be displayed.

If you've followed the directions in my 6th link carefully, you should now be able to view your Windows 7 share.

---

### Post by castalla on 2010-01-23
Thanks for the reply - I'll give it a try and report back tomorrow.

---

### Post by dmizer on 2010-01-23
I just finished setting this up myself, so it's still fresh in my mind. I did run into a snag that I didn't mention here regarding the shares, but I'm hoping it won't effect you.

For some reason, I was not able to get guest access to function.

---

### Post by castalla on 2010-01-23
I just followed your instructions for setting up the Win 7 end - the PC Man file manager sees the Win 7 box - it then goes to loading .... then returns with 0 items.

All the other devices (Vista, NAS) display shared files.

---

### Post by dmizer on 2010-01-23
What version of Win7 do you have?

Edit:
Also, please post the current output of testparm?

---

### Post by castalla on 2010-01-23
It's Win 7 Ultimate

Testparm:

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

### Post by dmizer on 2010-01-23
Don't forget to add the netbios name option as outlined in "Problem 2 - part 2". Also, make sure that samba is in fact installed:
```
sudo apt-get install samba
```
Finally, are there any other Linux machines on the network, or is it just the Windows 7 machine and Ubuntu?

---

### Post by castalla on 2010-01-23
Okay - will do that ... but tomorrow as it's getting late here.

On the network, there's a Vista PC, Win 7 PC, a linux NAS, and the ubuntu box.  Vista and NAS show on shares without problem.

Thanks for the help.

---

### Post by castalla on 2010-01-24
Just got this:

Reading package lists... Done
Building dependency tree... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-common-bin samba-common
E: Package samba has no installation candidate


What now?

---

### Post by dmizer on 2010-01-24
> **castalla said:**
> Just got this:

Reading package lists... Done
Building dependency tree... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-common-bin samba-common
E: Package samba has no installation candidate


What now?

What version of Ubuntu are you using?

---

### Post by castalla on 2010-01-25
Hi!

Linux SmartQ 2.6.24.7 #819 PREEMPT Thu Dec 24 16:20:13 CST 2009 armv6l GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

### Post by dmizer on 2010-01-26
That's really strange. My Karmic install finds the samba package without issue. Perhaps you have some alternate repositories enabled?

If you are unsure, please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by castalla on 2010-01-26
Here we go:

deb [http://ports.ubuntu.com](http://ports.ubuntu.com) karmic main universe restricted multiverse

---

### Post by castalla on 2010-01-26
Oh dear - I installed samba - now linux fails to boot!

---

### Post by dmizer on 2010-01-26
Take a look here: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/416093](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/416093)

You should be able to boot into recovery mode. Then you can remove samba from the boot process for further troubleshooting.

To remove samba from the boot process, install chkconfig (sudo apt-get install chkconfig), and run this command:
```
chkconfig --list samba
```
You should get output that looks like this:
```
samba                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
```
Turn any "on" number "off". Since run levels 2, 3, 4, and 5 are marked "on" in my system, I would disable samba on boot with the following command:
```
sudo chkconfig --level 2345 samba off
```

Once you've done that, please post your entire /etc/samba/smb.conf file.

---

### Post by castalla on 2010-01-26
The only thing I could do was reinstall linux - so I'm back to a pretty basic level - it'll take me at least a day to rebuild my system.

Previously, I had installed smbnetfs which gave me access to my Vista box.  Should I continue to do that - or should I attempt to install samba first?

---

### Post by dmizer on 2010-01-26
> **castalla said:**
> The only thing I could do was reinstall linux - so I'm back to a pretty basic level - it'll take me at least a day to rebuild my system.

Previously, I had installed smbnetfs which gave me access to my Vista box.  Should I continue to do that - or should I attempt to install samba first?

You should not need any tools other than samba and cifs. I do have things working this way.

Sorry to hear you reinstalled, but keep in mind that there's almost always a way to avoid that.

---

### Post by castalla on 2010-01-26
Cifs - now you're introducing something else!

I just installed smbnetfs ...

What do I do now?

I have absolutely no idea about the post you made about recovery mode ... the whole system locked up ... and any attempt to restart just gave me a blank screen.

(No wonder people turn to Windows ... sorry!)

---

### Post by castalla on 2010-01-26
I've now got my system back to previous level - although I can't for the life of me remember how I got a shell script on the desktop to start the share via smbnetfs .... !!!  I made the script file executable, yes ... but then what?  I'm just getting so confused (and tired!) - will leave until tomorrow.

Thanks for the help.

---

### Post by dmizer on 2010-01-26
> **castalla said:**
> Cifs - now you're introducing something else!

I just installed smbnetfs ...

What do I do now?

I have absolutely no idea about the post you made about recovery mode ... the whole system locked up ... and any attempt to restart just gave me a blank screen.

(No wonder people turn to Windows ... sorry!)

If you want to use smbnetfs, I'm afraid I won't be able to help you, as I know nothing about it.

When booting, enter the grub menu, and select "recovery mode". To enter the grub menu, hold down the <shift> key during boot.

Alternatively, you could have used a live cd to change the permissions of the samba script in /etc/init.d/

---

### Post by castalla on 2010-01-27
That's a pity!

I did say in my first post that I was using smbnetfs - just assumed that was what we were trying to get working!

Seems there's no solution then - I can't install samba as its using too much swap for the install.

---

### Post by dmizer on 2010-01-27
> **castalla said:**
> That's a pity!

I did say in my first post that I was using smbnetfs - just assumed that was what we were trying to get working!

Seems there's no solution then - I can't install samba as its using too much swap for the install.

It's possible to get the Nautilus shares working correctly with some configuration, but I was unable to do so without installing samba. You may also be successful with this method: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by castalla on 2010-01-27
I'm completely baffled by all this.

What I don't understand is that the linux box sees the Win 7 PC but can't list the shares.

The linux box sees Vista PC and lists!  The Vista box sees Win 7 and lists!

So what's so special about smbnetfs and win 7?

I've got a humble internet radio which apparently runs some basic linux - even that sees and lists the win7 shares!

---

### Post by castalla on 2010-01-27
Has anybody in the ubuntu community **actually** got smbnetfs to see win7 shares?

I suspect it's not possible - would love to be contradicted!

---

### Post by dmizer on 2010-01-27
> **castalla said:**
> I'm completely baffled by all this.

What I don't understand is that the linux box sees the Win 7 PC but can't list the shares.

The linux box sees Vista PC and lists!  The Vista box sees Win 7 and lists!

So what's so special about smbnetfs and win 7?

I've got a humble internet radio which apparently runs some basic linux - even that sees and lists the win7 shares!

If smbnetfs is not working for you to connect to Win7, then you can try an alternate method. I do have file sharing working between Karmic and Win7, but I am not able to get it working with smbnetfs.

If you must use smbnetfs, then I suggest opening a bug report. Otherwise, you should be able to use this method: [http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share](http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share)

You should also be able to use the gvfs method I mentioned a few posts ago: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by castalla on 2010-01-28
Thanks.

My problem is that I have a MID with a 'tuned' version of ubuntu (LXDE) - this has none of the services on the menus which are in the first link you give.  So looks like I'm scuppered!

How do I submit a bug report for smbnetfs?  I contacted the author but haven't had a reply.

---

### Post by castalla on 2010-01-29
... slight bump ...

Anybody?

---

### Post by jedat1 on 2010-01-29
Second to this request.
I've managed to get the win7 machine to see ubuntu by turning off homegroup but thats it. and if i turn homegroup off can't share with my PS3

---

### Post by castalla on 2010-01-30
Seems there's no answer to this one.

---

### Post by castalla on 2010-02-04
Does anybody have Windows 7 shares working on Ubuntu?

If so, could you please outline how you achieved this?

There's no viable how-to as far as I can see - includes 100s of google searches!  Plenty of problems, but few solutions!

---

### Post by dmizer on 2010-02-04
> **castalla said:**
> Does anybody have Windows 7 shares working on Ubuntu?

If so, could you please outline how you achieved this?

There's no viable how-to as far as I can see - includes 100s of google searches!  Plenty of problems, but few solutions!

Yes.

Please see the 6th link in my sig.

---

### Post by castalla on 2010-02-05
Thanks for the reply.  We've been here before!

To recap: using smbnetfs - this sees Vista and NAS shares - fails to show win7 shares - but does find the win7 pc.  I have disabled firewall on the win7 - no effect.

I managed to install samba and fusesmb - this showed the Vista and Win7 boxes - but no shared folders.  It also stopped smbnetfs working - shared pcs but no folders!  I ended up reinstalling ubuntu and reinstating smbnetfs - back to Vista and NAS shares.

The win7 shares are seen by Vista and Busybox linux - there's no password, accessed by Everyone with all rights - all machines have MSHOME workgroup.

I'm really stuck with this.

---

### Post by dmizer on 2010-02-05
> **castalla said:**
> Thanks for the reply.  We've been here before!

To recap: using smbnetfs - this sees Vista and NAS shares - fails to show win7 shares - but does find the win7 pc.  I have disabled firewall on the win7 - no effect.

I managed to install samba and fusesmb - this showed the Vista and Win7 boxes - but no shared folders.  It also stopped smbnetfs working - shared pcs but no folders!  I ended up reinstalling ubuntu and reinstating smbnetfs - back to Vista and NAS shares.

The win7 shares are seen by Vista and Busybox linux - there's no password, accessed by Everyone with all rights - all machines have MSHOME workgroup.

I'm really stuck with this.

Try mounting the share with cifs instead of smbnetfs (second link in my sig). Obviously smbnetfs is not helping you here.

---

### Post by castalla on 2010-02-05
Been there - done that!

The error is that the system does not support CIFS !

---

### Post by dmizer on 2010-02-05
> **castalla said:**
> Been there - done that!

The error is that the system does not support CIFS !

All Linux systems support CIFS, and Windows 7 will most certainly serve shares to CIFS.

---

### Post by castalla on 2010-02-05
Okay - I'll give it a try (again!) - stay tuned!

Thanks so much for your help.

---

### Post by castalla on 2010-02-05
In your instructions for smbfs Cifs you talk about modifying the nsswitch.conf for netbios name.  

Can I test the smbfs install by just mounting using the win7 box's IP address?  If it works then I will modify to use the netbios name.

---

### Post by dmizer on 2010-02-05
> **castalla said:**
> In your instructions for smbfs Cifs you talk about modifying the nsswitch.conf for netbios name.  

Can I test the smbfs install by just mounting using the win7 box's IP address?  If it works then I will modify to use the netbios name.

If your server is on a static IP, or if it is on a permanant DHCP lease assigned by MAC address, then yes, you can use the win7's IP address.

---

### Post by castalla on 2010-02-05
Okay - have to do something else for the next hour or so - but will try then.  More later!  Fingers crossed ...

---

### Post by castalla on 2010-02-05
Still crossed ....

 sudo mkdir /media/WIN
user@SmartQ:~$ sudo mount -t cifs //192.168.0.146/SDTOOL /media/WIN -o guest,rw,locharset=utf8,file_mode=0777,dir_mode=0777
mount error: cifs filesystem not supported by the system
mount error(19): No such device
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


???

---

### Post by dmizer on 2010-02-05
> **castalla said:**
> Still crossed ....

 sudo mkdir /media/WIN
user@SmartQ:~$ sudo mount -t cifs //192.168.0.146/SDTOOL /media/WIN -o guest,rw,locharset=utf8,file_mode=0777,dir_mode=0777
mount error: cifs filesystem not supported by the system
mount error(19): No such device
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


???

What is the output of:
```
aptitude search libsmbclient samba-common samba
```

You are apparently not using anything even remotely resembling a standard Ubuntu install. Please provide more information on your OS.

---

### Post by castalla on 2010-02-05
Here's the output:


user@SmartQ:~$ aptitude search libsmbclient samba-common samba
p   dpsyco-samba                    - Automate administration of access to samba
p   ebox-samba                      - eBox - File Sharing
p   egroupware-sambaadmin           - web-based groupware suite - Samba administ
p   gadmin-samba                    - GTK+ configuration tool for samba
p   gsambad                         - GTK+ configuration tool for samba (transit
p   libsamba-hostconfig-dev         - Samba host configuration library - develop
p   libsamba-hostconfig0            - Samba host configuration library
p   libsamba-util-dev               - Samba utility function library - developme
p   libsamba-util0                  - Samba utility function library
i   libsmbclient                    - shared library for communication with SMB/
p   libsmbclient-dev                - development files for libsmbclient
p   python-samba                    - Python bindings for Samba
v   python2.6-samba                 -
p   samba                           - SMB/CIFS file, print, and login server for
v   samba-client                    -
i A samba-common                    - common files used by both the Samba server
i A samba-common-bin                - common files used by both the Samba server
p   samba-dbg                       - Samba debugging symbols
p   samba-doc                       - Samba documentation
p   samba-doc-pdf                   - Samba documentation in PDF format
p   samba-ldb-tools                 - LDAP-like embedded database - tools
p   samba-tools                     - Samba testing utilities
p   samba4                          - LanManager-like file server for Unix (vers
p   samba4-clients                  - client utilities from Samba 4
p   samba4-common-bin               - Samba 4 common files used by both the serv
p   samba4-dev                      - tools for extending Samba
p   samba4-testsuite                - test suite from Samba 4
p   system-config-samba             - GUI for managing samba shares and users

---------------------

Is there a command which will show the OS info ?

---

### Post by dmizer on 2010-02-05
I don't think this will show me what I need, but it might help:
```
lsb_release -a
```

Do you have alternate repositories enabled as well?

---

### Post by castalla on 2010-02-05
I think it's just karmic

user@SmartQ:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu karmic (development branch)
Release:        9.10
Codename:       karmic

---

### Post by dmizer on 2010-02-05
Well, you don't have gnome, and you don't have KDE (as far as I can tell) ... and your package list looks as though you have 3rd party or PPA for samba packages installed. All of this stuff seems to be working against you.

Your package list indicates that you do indeed have CIFS installed, but when you try to use it, the kernel says CIFS isn't there ... I'm not even remotely sure what to do to help you next.

---

### Post by castalla on 2010-02-05
This is what I get if I log-in via ssh:


Linux SmartQ 2.6.24.7 #819 PREEMPT Thu Dec 24 16:20:13 CST 2009 armv6l


Infuriating, isn't it!?

---

### Post by castalla on 2010-02-05
I just tried smbclient to the win7 box - got this:

 smbclient -L //winpc
Enter user's password:
Domain=[WINPC] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
Domain=[WINPC] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


Does that explain anything?

---

### Post by Morbius1 on 2010-02-05
As I am in agreement with everything that dmizer has posted I really don't want to intrude but it might be a known bug or it could be that you seem to have a one of a kind linux installation.

See if this bug report applies to your error message:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681)

---

### Post by castalla on 2010-02-05
Thanks - the more the merrier!

I guess it could be a bug from what I've read so far.  I used karmic repositries - but don't know what to do next?  If I enable say jaunty - should I uninstall samba and smbclient first then reinstall?

---

### Post by castalla on 2010-02-06
Another clue?  I need advice ...


This works:

user@SmartQ:~$ sudo smbclient //winpc/SDTOOL
Enter root's password:
Domain=[WINPC] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]
smb: \> dir
. D 0 Tue Feb 2 16:52:13 2010
.. D 0 Tue Feb 2 16:52:13 2010
qi.nb0 A 3208 Thu Mar 12 14:35:38 2009
SD Card Fusing Tool.exe A 57424 Fri Jul 3 21:11:17 2009
Support Blog.url A 56 Fri Jul 3 21:45:27 2009
u-boot-4_3.bin A 98968 Fri May 8 10:05:30 2009
u-boot-7.bin A 98984 Fri May 8 09:56:46 2009
uninst.exe A 52045 Fri Jun 5 20:17:30 2009
vcredist_x86.exe A 2717352 Mon Mar 23 11:02:52 2009

40755 blocks of size 524288. 18803 blocks available
smb: \>

Sort of progress ... but where to next? I want to be able to browse the share via PC Man file manager.

---

### Post by castalla on 2010-02-07
I've hit the buffers on this.

I don't think it is possible to view Win 7 shares ...

To summarize:

Can't use smbmount - as it switches to CIFS which is not compiled.

SmbFuse can't list any contents of directories (neither Vista nor Win7) - (at least not with the smb.conf file I've used!) - that's using PCManFM. The Vista shares do show in SMPlayer browse, however, but NO Win7 shares.

Smbnnetfs can list Vista shares but not Win7 - both in PCManFM and SMPlayer

**Smbclient can access the Win7 shares and list them via dir**

So the Win7 box is accessible ....

Has anybody got any ideas on this - I think I've put a fair amount of effort into this - and if somebody does have the answer could they please tell me!!???

---

### Post by dmizer on 2010-02-07
> **castalla said:**
> I don't think it is possible to view Win 7 shares ...

It's perfectly possible to view Win7 shares. It's just not possible with your configuration. There is something you've done to customize your system that is preventing you from using CIFS.

---

### Post by castalla on 2010-02-08
Oh sorry ... I meant it isn't possible on my device (because of the lack of cifs).  The kernel provided for the device does seem to have been crippled!  I'm trying to discover if there's an alternative OS.

Thanks again.

---

### Post by dmizer on 2010-02-08
> **castalla said:**
> Oh sorry ... I meant it isn't possible on my device (because of the lack of cifs).  The kernel provided for the device does seem to have been crippled!  I'm trying to discover if there's an alternative OS.

Thanks again.
I have Win7 shares working on Ubuntu, Ubuntu netbook remix, Kubuntu, and Xubuntu. Kubuntu, Xubuntu, and Ubuntu all use the same kernel. So unless you can tell us more about what you have installed on your machine, we can not help you. Where did you download it, what did the link say? Did it come pre-installed? If so, what did you buy, where, and what is the model?

Otherwise, the problem is related to something you have installed or changed. CIFS is installed on your device. You are having a problem because something you have installed (maybe smbnetfs?) is interfering with CIFS.

---

### Post by llawwehttam on 2010-02-08
> **dmizer said:**
> I have Win7 shares working on Ubuntu, Ubuntu netbook remix, Kubuntu, and Xubuntu. Kubuntu, Xubuntu, and Ubuntu all use the same kernel. So unless you can tell us more about what you have installed on your machine, we can not help you. Where did you download it, what did the link say? Did it come pre-installed? If so, what did you buy, where, and what is the model?
 
Otherwise, the problem is related to something you have installed or changed. CIFS is installed on your device. You are having a problem because something you have installed (maybe smbnetfs?) is interfering with CIFS.
 
I agree. I have been using windows shares on ubuntu for ages and never had any problems .Your install seems very custom and that is problebly why you are having problems.

---

### Post by castalla on 2010-02-08
Thanks for the replies.

The linux is pre-installed - here's the info I can find:

Linux SmartQ 2.6.24.7 #819 PREEMPT Thu Dec 24 16:20:13 CST 2009 armv6l

This is preinstalled on the SmartQ MID Q5.

The only installs I have done are ssh, smbnetfs, samba, and fusesmb.

Is there a way to add cifs - or does it have to be a recompiled kernel?

---

### Post by dmizer on 2010-02-08
> **castalla said:**
> Thanks for the replies.

The linux is pre-installed - here's the info I can find:

Linux SmartQ 2.6.24.7 #819 PREEMPT Thu Dec 24 16:20:13 CST 2009 armv6l

This is preinstalled on the SmartQ MID Q5.

The only installs I have done are ssh, smbnetfs, samba, and fusesmb.

Is there a way to add cifs - or does it have to be a recompiled kernel?
OK, this makes a lot of sense.

Please give me a few days to do some research and I'll post back.

---

### Post by castalla on 2010-02-08
Thanks so much for your help.

cheers

---

### Post by castalla on 2010-02-15
Hi - no pressure - just wondering if you have any progress on this?

---

### Post by dmizer on 2010-02-15
> **castalla said:**
> Hi - no pressure - just wondering if you have any progress on this?

None at all.

I can't seem to figure out what they're using to drive that device. Have you reinstalled the OS? If so, where did you get it?

---

### Post by castalla on 2010-02-16
Yes - it's a firmware reflash - available at [http://en.smartdevices.com.cn/Support/Downloads/SmartQ5/Firmware/200912/30-48.html](http://en.smartdevices.com.cn/Support/Downloads/SmartQ5/Firmware/200912/30-48.html)

There's somebody who has developed a way to recompile for a slightly different smartq model ( V5/V7) - I haven't any idea if this could be done for the Q5 - [http://www.smartqmid.com/phpBB3/viewtopic.php?f=18&t=1005&start=0](http://www.smartqmid.com/phpBB3/viewtopic.php?f=18&t=1005&start=0)

Thanks for all your help on this.

---

### Post by castalla on 2010-03-05
... I suppose this is a lost cause?

Anyway, thanks for the time you've taken over this.

---

### Post by dmizer on 2010-03-06
> **castalla said:**
> ... I suppose this is a lost cause?

Anyway, thanks for the time you've taken over this.

I believe that if I could actually get my hands on one of these things that I could get it done, but the manufacture has customized the OS to the point where it's too obscure now.

I think that I have included new information regarding Windows 7 configuration in my "fix windows browsing" howto. You can take a look there again and possibly find a fix.

But frankly, no ... I don't have anything else to suggest here. I'm really sorry. You might try the samba forums, or another community with more knowledge about your device.

---

### Post by castalla on 2010-03-06
Thanks again.

---

### Post by castalla on 2010-05-10
**Update**

I have finally been able to solve this problem.

I discovered that I was able to enable CIFS by using *insmod cifs.ko* after I'd hunted down the actual module file (which took ages to track down!)

Your smbfs tips work a treat.  Thanks again for your help.

---

### Post by dmizer on 2010-05-11
> **castalla said:**
> **Update**

I have finally been able to solve this problem.

I discovered that I was able to enable CIFS by using *insmod cifs.ko* after I'd hunted down the actual module file (which took ages to track down!)

Your smbfs tips work a treat.  Thanks again for your help.

I am so glad to hear this! Thanks for the update.

---

