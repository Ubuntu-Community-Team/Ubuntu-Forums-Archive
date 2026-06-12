---
title: "cannot get windows 98 to access linux shares"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2010-11-08
This is driving me nuts. I have Samba installed on my Linux box and I can access the shares from my Linux laptop just fine. The problem comes in when I try to access the shares from a Win98 laptop. The server name shows up in the Network Neighborhood (freaking childish names!) but when I double-click it, Win98 keeps asking me for the password for the \\SHOP\IPC$ connection. 

I have deleted the .pwl file on the Win98 and logged in using the same user/pass combination as I do on the Linux. On the Linux, I ran 'smbpasswd -a derek' and supplied my password. 

Windows XP sees the server just fine, but Windows 98 just does not want to play nice. Is there any thing that I can do to fix this without breaking the connection to the XP box or the Linux laptop?

This is the uncommented portions of my smb.conf file:
```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = yes
   passdb backend = tdbsam
   obey pam restrictions = yes
   pam password change = yes
   map to guest = bad user
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

```

Thanks....

---

### Post by luvshines on 2010-11-09
Just check this on Samba server```

testparm -sv | grep lanman

```

From smb.conf> 
client lanman auth (G)
 This parameter determines whether or not smbclient and other samba client tools will attempt to authenticate itself to servers using the weaker LANMAN password hash. If disabled, only server which support NT password hashes (e.g. Windows NT/2000, Samba,etc... but not Windows 95/98 ) will be able to be connected from the Samba client.


Try setting it to yes (if it is no), restart the smbd service and give it a try

---

### Post by psusi on 2010-11-09
Stop using windows 98.  It is riddled with security holes that will not be fixed because it reached end of life long ago and is no longer supported.  As a result it will become infected and turned into a zombie bot and used to attack other people on the interwebs.

---

### Post by CharlesA on 2010-11-09
> **psusi said:**
> Stop using windows 98.  It is riddled with security holes that will not be fixed because it reached end of life long ago and is no longer supported.  As a result it will become infected and turned into a zombie bot and used to attack other people on the interwebs.

This.

Win 98 SE hasn't been supported for over 4 years now. It's probably running IE 5 or IE 5.5. *twitch*

Security in Win98 vs even a Win2K box is pathetic is comparison.

---

### Post by JOHNNYG713 on 2010-11-09
Sorry but....... W/98 ! [-o<](*,):-P LMAO !!! :P Your better off loading ubuntu and running wine!

---

### Post by rebeltaz on 2010-11-09
> **JOHNNYG713 said:**
> Sorry but....... W/98 ! [-o<](*,):-P LMAO !!! :P Your better off loading ubuntu and running wine!

Oh good Lord... What is wrong with you people? First of all, psusi... how is a computer that is not on the internet going to be infected by anything? Second of all, I never said what I was using this for so it's a little pretentious of all of you to assume that you have any idea what you are talking about. I am using this (knowingly) old computer as an MP3 jukebox for my girlfriend so anything higher than 98 is overkill. And besides that - did any of you even think to ask if the laptop I am running 98 on would run anything else?

And what is with all of you and security? Do you honestly get hacked that often? It's not like I am running these systems on a highly public corporate computer server. And as a matter of fact, out of the three or four times I have had a system infected in over 20 years, it was on XP - not 98. And yes, I used 98 well after it was officially discontinued. 

LUVSHINES -> Thank you for a thoughtful, helpful answer. lanman was the problem. I found this:

```

   1. Add these three lines to the [globals] section of your smb.conf:

      lanman auth = Yes
      client lanman auth = Yes
      client plaintext auth = Yes

   2. Restart the Samba server
   3. Re input passwords for every Win9x user:
      smbpasswd -a username
   4. Have every Win9x user log out and then log in again

```

that solved the problem. Thank you again....

---

### Post by CharlesA on 2010-11-09
> **rebeltaz said:**
> 
And what is with all of you and security? Do you honestly get hacked that often? It's not like I am running these systems on a highly public corporate computer server. And as a matter of fact, out of the three or four times I have had a system infected in over 20 years, it was on XP - not 98. And yes, I used 98 well after it was officially discontinued. 

Haven't been "hacked" yet, thank you. :)

The thing is that 98 has no sort of "user account" login, like Win NT or 2K, or XP has.

Depending on the specs of the laptop, you'd probably be able to run something like Puppy linux on it.

Running an outdated OS, even if you aren't using it for internet browsing, is a bad idea.

---

### Post by rebeltaz on 2010-11-09
> **CharlesA said:**
> 
The thing is that 98 has no sort of "user account" login, like Win NT or 2K, or XP has.

Running an outdated OS, even if you aren't using it for internet browsing, is a bad idea.

Now that we are having an intelligent discussion :) WHY is running an outdated OS a bad idea? I honestly cannot see a downside except that (in the case of Windows - doesn't apply to Linux) the big software companies don't get the money you spend on the upgrades. :cry: And why is 'no user account' a bad thing? When only one (or in my case) two people are even in the same vicinity as the computer, why do I need more than one user account? 

Not trying to be obnoxious here... I honestly would like to know your opinions on these questions?

---

### Post by CharlesA on 2010-11-09
For what it's being used for, one account would work, I suppose.

However:

In the case of Windows 98, you didn't "need" to log into it, you could just hit cancel and access the desktop and go about your business.

Win NT changed that since you needed an account on the machine to be about to "login" and access the desktop.

I suppose it boils down to being able to access the machine physically, but physical access = root access, since someone could just boot off a livecd and pull the data off, so the point I was trying to make is moot.

Anyway, if an OS is no longer getting security updates, it's time to move on, as that OS is vulnerable to new expolits, since it's no longer being patched for them. That's a pretty good reason to not use something that's out of date. :)

---

### Post by rebeltaz on 2010-11-17
> **CharlesA said:**
> 
I suppose it boils down to being able to access the machine physically, but physical access = root access, since someone could just boot off a livecd and pull the data off, so the point I was trying to make is moot.

Anyway, if an OS is no longer getting security updates, it's time to move on, as that OS is vulnerable to new expolits, since it's no longer being patched for them. That's a pretty good reason to not use something that's out of date. :)

Just wanted to reiterate that this is an mp3 jukebox without internet access. So there is no data that could possibly be desired and no potential for exploits since - no internet! Besides, older equipment won't run the latest OS' even if I wanted to. I'm just a big fan of the old idiom - if it ain't broke, don't fix it... 

Sorry for taking so long to reply...

---

### Post by luvshines on 2010-11-18
> **rebeltaz said:**
> Just wanted to reiterate that this is an mp3 jukebox without internet access. So there is no data that could possibly be desired and no potential for exploits since - no internet! Besides, older equipment won't run the latest OS' even if I wanted to. I'm just a big fan of the old idiom - if it ain't broke, don't fix it... 

Sorry for taking so long to reply...

That being said, did you try the setting which I specified in my earlier comment

---

### Post by rebeltaz on 2010-11-18
> **luvshines said:**
> That being said, did you try the setting which I specified in my earlier comment


I did.. in my initial reply I did thank you:

> **rebeltaz said:**
> LUVSHINES -> Thank you for a thoughtful, helpful answer. lanman was the problem. I found this:

```

   1. Add these three lines to the [globals] section of your smb.conf:

      lanman auth = Yes
      client lanman auth = Yes
      client plaintext auth = Yes

   2. Restart the Samba server
   3. Re input passwords for every Win9x user:
      smbpasswd -a username
   4. Have every Win9x user log out and then log in again


```

that solved the problem. Thank you again....

You may have missed it because of my security rant! ;) But, again... thank you.

---

### Post by jrssystemsnet on 2010-11-18
like the man says in his sig, please mark the issue [SOLVED] (as in, change the thread title so that it says [SOLVED] at the end) once your problem is fixed.  This helps people find what they are looking for - people looking to help don't waste time where it's not needed, and people looking to get help can see that there is an answer already in the thread to try. :)

---

### Post by rebeltaz on 2010-11-18
> **jrssystemsnet said:**
> like the man says in his sig, please mark the issue [SOLVED] (as in, change the thread title so that it says [SOLVED] at the end) once your problem is fixed.  This helps people find what they are looking for - people looking to help don't waste time where it's not needed, and people looking to get help can see that there is an answer already in the thread to try. :)

oops! Sorry... doing it now!

---

