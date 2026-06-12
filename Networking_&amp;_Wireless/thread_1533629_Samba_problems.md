---
title: "Samba problems"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by tony7671 on 2010-07-18
Like many people it seems, I'm having trouble connecting to a Samba share on a machine running Lucid, in my case from a Windows 7 machine. I've tried all of the usual suggestions I can find. I can see the share from my windows machine, and when I try to connect to it, I get a Windows prompt "Enter network password". I have the same username set up under Windows and Ubuntu, and I am not using a domain controller. The workgroup is WORKGROUP in Windows, and that is what I have set in smb.conf in Ubuntu. This is where the problems start - the commentary all seems to say "use the same user name as for Windows" - however, the "Enter network password" box effectively insists on a domain qualifier, defaulting to the name of the Windows machine if non is supplied, so I've tried without, and with WORKGROUP\<username>, in a variety of combinations of upper and lower case - all fail, with Windows just continually re-presenting the login window. I have used smbpassword.

Strange thing was it was working briefly - I had access to the share, and was able to copy files to it from Windows. However,  I disconnected looking to map the share to a drive letter, and it refused to connect again. This does seem to imply I have all the software I need installed, and there aren't any firewalls getting in the way. I just can't understand what has changed, and I'm not sure how I got it to connect in the first place.

A scan of the logs is less than revealing - all I could find in auth.log is something like this when trying to connect:

Jul 18 13:35:07 bowmore smbd[30049]: pam_unix(samba:session): session opened for user tony by (uid=0)
Jul 18 13:35:07 bowmore smbd[30049]: pam_unix(samba:session): session closed for user tony

Sometimes there are a few seconds between the two entries. I haven't found any meaningful troubleshooting facilities for this.

Any suggestions gratefully received. Seems like there are a lot of people who have wasted a lot of hours trying to get this apparently straightfoward thing to work, and I've become one of them!

Thanks,

Tony

---

### Post by Morbius1 on 2010-07-18
> This is where the problems start - the commentary all seems to say "use  the same user name as for Windows"Of all the samba myths that one has to be the goofiest. If I have a family of four does that mean that if I want to share folders all of them have to have the same username and password?

Sorry about that.

Please post the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s

```One question: Do you want to have the remote user supply a username and password to access the share? Or was your original intent to allow anyone on your home network to have access to the share?

---

### Post by tony7671 on 2010-07-18
> **Morbius1 said:**
> Of all the samba myths that one has to be the goofiest. If I have a family of four does that mean that if I want to share folders all of them have to have the same username and password?

Sorry about that.



It's perhaps more accurate to say that this is more of a recommendation to make things easier (!) if you can do it.

> 

Please post the output of the following commands:
```
net usershare info
sudo net usershare info

```Both return nothing (although the share in question can be seen by browsing from the Windows machine).

> 
```

testparm -s

``````

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[WIN]"
WARNING: The "only user" option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad Password
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
    comment = Windows filesystem
    path = /usr2/windows

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

[WIN]
    valid users = tony, @sambashare, @tony
    read only = No
    only user = Yes
root@bowmore:/var/log/samba# 

```This does show some evidence of the messing around I have tried to get it to work - using different usernames and groups. I have tried various permutations of options, so it's possible they may not make much sense the way they stand now!
> 
One question: Do you want to have the remote user supply a username and password to access the share? Or was your original intent to allow anyone on your home network to have access to the share?It would be quite nice to have whatever username the user was logged on under in Windows being the one that applied for access to the share.

Thanks

---

### Post by Morbius1 on 2010-07-18
Things don't seem to be in the "proper" sections but I think it will still work. It seems you have one share:

> [global]
comment = Windows filesystem
    path = /usr2/windows> [WIN]
    valid users = tony, @sambashare, @tony
    read only = No
    only user = Yes
If we're lucky [-o< maybe this is a linux file permissions problem and not a samba problem. I need to see the permissions on /usr2/windows:

```
ls -al /usr2/windows
```I'm not familiar with the "only user = Yes" parameter either. If it were me I'd comment it out. But let me see what it does before we make any changes to this.
[COLOR=Blue] EDIT: It seems testparm gave you a waring about the "only user" option:[/COLOR]
> WARNING: The "only user" option is deprecatedI'd comment it out by placing a # in front of that line.

---

### Post by KillerPancake on 2010-07-18
Tony, I've been having a similar problem, but have discovered that I can connect to the share and successfully enter username and password using the IP address of the server instead of server name.  

Calling it a workaround for now...

---

### Post by tony7671 on 2010-07-19
> **Morbius1 said:**
> Things don't seem to be in the "proper" sections but I think it will still work. It seems you have one share:


I think that might be me being lazy initially and using Webmin.

When I came to look at the permissions I realized something else had happened - I'd been using it with some configuration changes, and I thought I'd reboot to see if that cleared the problems. After rebooting, the secondary disk hadn't mounted properly, so the actual directory shared didn't exist. In trying to fix this, at some point I managed to hose /etc/fstab, so that on reboot the machine couldn't mount the root partition. After some messing about, I booted off a live CD, mounted the main hard disk, and fixed fstab - and it all sprung to life!

> I'm not familiar with the "only user = Yes" parameter either. If it were me I'd comment it out. But let me see what it does before we make any changes to this.
[COLOR=Blue] EDIT: It seems testparm gave you a waring about the "only user" option:[/COLOR]
I'd comment it out by placing a # in front of that line.I tried that previously (before the reboot), and that seemed at the time to stop the share itself being visible. As I say, prior to that it had been working (I'm not imagining it - a file I copied on at that time is still there!)

The upshot is that it is working now, and although I'm not 100% sure what I did to make it work, I feel like I've learnt something!

Morbius - Thanks very much for your help.

Tony

---

### Post by tony7671 on 2010-07-19
> **KillerPancake said:**
> Tony, I've been having a similar problem, but have discovered that I can connect to the share and successfully enter username and password using the IP address of the server instead of server name. 

I think I did have that problem initially, but I dealt with it by making an entry in c:\windows\system32\drivers\etc\hosts (which you need to edit as administrator on a Windows 7 machine). Guess we should be running a WINS server or something like that ...

Tony

---

### Post by hostingdude on 2013-02-03
I don't have much experience here, but I'm finding the same problem, and I'm positive it's on the Windows 7 side.

I have a CentOS 5.x 64-bit server with a share on it (Ubuntu vs. CentOS is irrelevant here, same problem on either OS, as you will see), and my Windows 7 Ultimate 64 machine CAN access it when I have the SAMBA share completely open, using:

username: guest
admin: guest

This is when I set it up going to COMPUTER, MAP NETWORK DRIVE, pick a drive (Z) and choose folder as:

\\(ip address)\(shared samba folder)

e.g.:

\\000.000.000.000\samba_drive

when I connect, I get a window labelled WINDOWS SECURITY, which at the top says: 

Enter Network Password 
Enter your password to connect to: 000.000.000.000

Then it lets me login one of two ways:

(My Computer Name)\(my Windows username)
e.g.:
STATION15\jones123

plus a password
with a REMEMBER MY CREDENTIALS checkbox below it

...OR...

USE ANOTHER ACCOUNT

And that allows me to select a USERNAME and PASSWORD...

THE PROBLEM IS THIS:

When I choose that second option to put in the SAMBA username, my Win7 computer still PREPENDS \STATION15\ to the front of the username (that's my Windows 7 computer name).

And my login is REJECTED by the Samba server...

So let's say that my SAMBA setup on Linux is waiting for this combo:

username: sambaguy
password: SambaPass1

Apparently, WINDOWS is SENDING THIS:

username: \STATION15\sambaguy
password: SambaPass1

and I'm rejected...


AGAIN, this is ONLY after I set up the credential requirements on the SAMBA Server.


NOW IT GETS WEIRD -- It only does it on THIS PC, which is:

Windows 7 Ultimate 64-bit, UPGRADED from a Windows Vista Ultimate 64-bit.

On ANY OTHER PC I own, I do NOT have this problem -- all the others do NOT try to prepend my computer name to my login name:

Windows 7 Home Premium 32-bit works fine
Windows 7 Home Premium 64-bit works fine
Windows 7 Professional 64-bit works fine
Windows 8 64-bit (on cheap craptop... no clue what version or how to even find it... I H8 Win8) works fine
(Even an Android phone and tablet work fine to connect - one ICS, one Jelly Bean)

But the problem is on THIS COMPUTER which is:

Windows 7 Ultimate 64-bit -- upgraded using the Microsoft Upgrade, from Windows Vista Ultimate 64-bit...

So, unless other folks have problems using Windows 7 Ultimate to connect to Samba with this specific issue, then I am thinking that...

This may be a problem that's legacy to Windows Vista.

Since my upgrade to Win7 was via the MS upgrade method, and not by a fresh installation... I am thinking that SOME of my control and .conf files are still VISTA-ish... that some of them were simply left alone, or only lightly-modified by Windows 7 when I did the upgrade. Whereas, if I had done a fresh Win7 install, I would have gotten all new and properly set configuration files.

I say this also because Vista is known to have this type of problem... Vista had known samba connection problems.

Somebody with more experience with Windows could take a guess at this and perhaps could HELP(!) me configure Windows 7 so it's not sending the COMPUTER NAME as a prepend to the username when I go to log in to Samba remotely.

I know the Samba end is set up right since every other computer on the planet can connect...

Can someone help?

Also, is this related to YOUR issue? Was your computer OS an upgrade from Vista to Win7? You may have tweaked something in your Win7 that fixed the issue, and after a reboot (or directly after the tweak) you connected... You say you still don't know why. This theory may apply to you too...

Please help!

---

### Post by varunendra on 2013-02-03
Thread too old to be resurrected. Closed.

I see you have already started a thread for the same question here : [http://ubuntuforums.org/showthread.php?t=2111902](http://ubuntuforums.org/showthread.php?t=2111902)

Please don't create multiple posts for same question as it dilutes community efforts. If you are tempted to do so, just post a link to your original post in a relevant place. And please do not bump old threads. From the [CoC]("http://ubuntuforums.org/index.php?page=policy")-
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thank you.

---

