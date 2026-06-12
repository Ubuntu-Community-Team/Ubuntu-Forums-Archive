---
title: "Invalid command: net rap share list"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by 9000cse on 2011-06-24
Hi all, is this a UBUNTU or MS XP issue?  Or even Windows 7, as I now find.
> 
 p, li { white-space: pre-wrap; }  Invalid command: net rap share list


Whos going to be the liff saver??????]
Cheers
Andy

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> Hi all, is this a UBUNTU or MS XP issue?  Or even Windows 7, as I now find.


Whos going to be the liff saver??????]
Cheers
Andy

Not sure if I am a liff saver, but...

I'll bet you are using Samba 4 with SMBv2.  This is not a Ubuntu or a XP prob.  If you are using Samba 4 in a home LAN environment (a workgroup) I would seriously think about purging the install and installing Samba 3.

Samba 4 has warning:
[COLOR="Red"]"These packages contain snapshot versions of Samba 4, the next-generation
version of Samba. These should be considered **_experimental_**, and should
not be used in production. In particular, no guarantees are made with
regard to upgrades between versions."[/COLOR]

---

### Post by 9000cse on 2011-06-24
> **redmk2 said:**
> Not sure if I am a liff saver, but...

I'll bet you are using Samba 4 with SMBv2.  This is not a Ubuntu or a XP prob.  If you are using Samba 4 in a home LAN environment (a workgroup) I would seriously think about purging the install and installing Samba 3.

Samba 4 has warning:
[COLOR=Red]"These packages contain snapshot versions of Samba 4, the next-generation
version of Samba. These should be considered **_experimental_**, and should
not be used in production. In particular, no guarantees are made with
regard to upgrades between versions."[/COLOR]

Yes, your right on there 4 it is. But that is the version that USC gave me. So, where best to get 3 from?
Cheers, I will un-install 4 now.

Thanks
Andy

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> Yes, your right on there 4 it is. But that is the version that USC gave me. So, where best to get 3 from?
Cheers, I will un-install 4 now.

Thanks
Andy

What's USC?  If that is the Synaptics Package Manager (System>Administration>Synaptics Package Manager), Then just put samba in the **quick search** box and look for Samba.  Do not use Samba 4.

How are you going to un-install Samba 4?  You should **purge **it, not just un-install.

Edit: Ahhhh USC = Ubuntu Software Center.  I've never used it.  It is better for you to use Synaptics on my opinion.  More versatile and complete.  I see that Samba3 server does not appear to be in USC at all.  That is strange.

---

### Post by 9000cse on 2011-06-24
> **redmk2 said:**
> What's USC?  If that is the Synaptics Package Manager (System>Administration>Synaptics Package Manager), Then just put samba in the **quick search** box and look for Samba.  Do not use Samba 4.

How are you going to un-install Samba 4?  You should **purge **it, not just un-install.

Edit: Ahhhh USC = Ubuntu Software Center.  I've never used it.  It is better for you to use Synaptics on my opinion.  More versatile and complete.  I see that Samba3 server does not appear to be in USC at all.  That is strange.

I have un-installed now...How do you 'PURGE' it?

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> I have un-installed now...How do you 'PURGE' it?

In Synaptics you can "completely" remove it.  Since I don't know how you uninstalled Samba4, I'm not sure how much is left on the system.  Each method is different.

Look in Synaptics and see what is left.

---

### Post by 9000cse on 2011-06-24
Looking in SPM, Samba4 is not installed.  But, looking in Accessories, SMB4K is, just tried to run it and nothing happened. Now, I do not want to install Samba3, untill 4 has gone. Is there another way of getting rid of it?

Cheers
Andy

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> Looking in SPM, Samba4 is not installed.  But, looking in Accessories, SMB4K is, just tried to run it and nothing happened. Now, I do not want to install Samba3, untill 4 has gone. Is there another way of getting rid of it?

Cheers
Andy
Remove SMB4K.  Then I would go into the /etc/samba/ directory and rename the smb.conf file to something like: smb.conf.origv4  There should be no doubt later on what this file was originally used for.

Now you can install [COLOR="Blue"]samba-common [/COLOR] and [COLOR="Blue"]samba[/COLOR] from SPM.

I usually am working from the command line like this```
sudo apt-get install samba-common samba 
```

You can check it out first by adding an [COLOR="Red"]-s[/COLOR] to the command like this```
sudo apt-get [COLOR="Red"]-s[/COLOR] install samba-common samba 
```

---

### Post by 9000cse on 2011-06-24
Your going to love this.
It will not let me rename it.  Rename is Grayed out.

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> Your going to love this.
It will not let me rename it.  Rename is Grayed out.

But of course.  The file is owned by root.  You need to either use Nautilus as root: (<alt-f2> gksudo nautilus  Or use the terminal (sudo <the proper command you need>

If you use Nautlius then close it as soon as you are done.  You should not use root Nautilus for general usage.

---

### Post by 9000cse on 2011-06-24
[OK, that seems to be done. 
Samba 3 installed. But on running it, all I get is pw box. then nothing.  

Got something working in my faviour.  BUT
> 
 p, li { white-space: pre-wrap; }  Could not save properties. You do not have sufficient access to write to /usr/share/applications/kde4/knetattach.desktop


Andy

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> [OK, that seems to be done. 
Samba 3 installed. But on running it, all I get is pw box. then nothing.  

Got something working in my faviour.  BUT

Andy

I'm almost afraid to ask...  What did you do to configure Samba.  I see you are running Kubuntu (KDE) and not Ubuntu (Gnome).  I have not used KDE for 5 years or so.  I'm not sure I am the right person to advise you on KDE problems.

I see that you have what appears to be a permissions problem.  Do you have an aversion to using the code blocks button (this thing #).  I makes life sooooo much better for the people that are trying to help you.

---

### Post by 9000cse on 2011-06-24
> **redmk2 said:**
> I'm almost afraid to ask...  What did you do to configure Samba.  I see you are running Kubuntu (KDE) and not Ubuntu (Gnome).  I have not used KDE for 5 years or so.  I'm not sure I am the right person to advise you on KDE problems.

I see that you have what appears to be a permissions problem.  Do you have an aversion to using the code blocks button (this thing #).  I makes life sooooo much better for the people that are trying to help you.


Not sure what # means. HASH key, but where does that come into it?
KDE, ??
I would rather use Terminal,  This is one of the reasons I switched from XP etc.  
Yes, this permissions problem keeps coming up.  At first I installed 10.10, that had permission issues.
To the extent that I had no choose but to reinstall. That's the reason I decided to go with 11. So far, much better.  BUT, This permission issue??? How to I over come it?

I know how you must be feeling, re dealing with a user.  I used to work on helpdesks. MS stuff. I am an MSCP, or is MCP, god knows.  Was never really into it. But the money was good. So. I have been there and listening to 'OTHER' while trying to fix a problem. Hard, when your not in front of a system

---

### Post by redmk2 on 2011-06-24
> **9000cse said:**
> Not sure what # means. HASH key, but where does that come into it?
At the top of the editor you use to respond to this thread, is a series of symbols.  On the right hand side is a button that has a # on it.  That is the button to use the wrap text in "code blocks (e.g [CODE]text here [ /CODE] ).  It should be right next to the "quote button".  If it is not there you need to switch to the advanced mode in the editor.
>  
KDE, ??
KDE is the desktop you are using.  The distro you downloaded was Kubuntu and not Ubuntu.  If you installed 11.04 Ubuntu and you have KDE errors something is really wrong here.> 

I would rather use Terminal,  This is one of the reasons I switched from XP etc. 
Using the terminal is fine by me, but you still have to deal with configuring for the correct desktop.  Is your desktop KDE?> 

Yes, this permissions problem keeps coming up.  At first I installed 10.10, that had permission issues.
To the extent that I had no choose but to reinstall. That's the reason I decided to go with 11. So far, much better.  BUT, This permission issue??? How to I over come it?
No Ubuntu/Kubuntu install should have permissions *problems*.  Some files are not owed by the logged in user (you for instance).  Some are owned by the system and as such only root has access.  This is by design.  You need to learn about how the system works; lots of reading I'm afraid.  Most of this can be hidden by the GUI but it is still there.
> 
I know how you must be feeling, re dealing with a user.  I used to work on helpdesks. MS stuff. I am an MSCP, or is MCP, god knows.  Was never really into it. But the money was good. So. I have been there and listening to 'OTHER' while trying to fix a problem. Hard, when your not in front of a system
I will suppress my first inclination to respond to that.

So what do you want to do?  Reinstall the whole OS using Ubuntu instead of Kubuntu?  Try and figure this mess out?  

I would start over and install Ubuntu 10.04.2 LTS (Lucid).  It is stable and has known answers to most errors.  My feeling is you are going to have a lot of problems in the beginning.  That is normal.  It is part of being new to the OS.  Re-installs are common whilst you are learning.  If it was easy this forum would not exist.

---

### Post by 9000cse on 2011-06-25
Hi.  How are you today? OK, understood all below.
> **redmk2 said:**
> At the top of the editor you use to respond to this thread, is a series of symbols.  On the right hand side is a button that has a # on it.  That is the button to use the wrap text in "code blocks (e.g [CODE]text here [ /CODE] ).  It should be right next to the "quote button".  If it is not there you need to switch to the advanced mode in the editor.
The only # I see is the one next to the number of the thread (#14).  I do not think I'll worry about that right now.
>  
KDE is the desktop you are using.  The distro you downloaded was Kubuntu and not Ubuntu.  If you installed 11.04 Ubuntu and you have KDE errors something is really wrong here.Using the terminal is fine by me, but you still have to deal with configuring for the correct desktop.  Is your desktop KDE? No Ubuntu/Kubuntu install should have permissions *problems*.  Some files are not owed by the logged in user (you for instance).  Some are owned by the system and as such only root has access.  This is by design.  You need to learn about how the system works; lots of reading I'm afraid.  Most of this can be hidden by the GUI but it is still there.Understood.  Clicking on the 'HELP' button, I get '[COLOR=#000000][FONT=Ubuntu][COLOR=#535353]**Ubuntu Desktop Guide'  So, this must be UBUNTU ?**
[/COLOR][/FONT][/COLOR]
> 
I will suppress my first inclination to respond to that.LOL.
> 

So what do you want to do?  Reinstall the whole OS using Ubuntu instead of Kubuntu?  Try and figure this mess out?  

I would start over and install Ubuntu 10.04.2 LTS (Lucid).  It is stable and has known answers to most errors.  My feeling is you are going to have a lot of problems in the beginning.  That is normal.  It is part of being new to the OS.  Re-installs are common whilst you are learning.  If it was easy this forum would not exist.Right, Reinstall it is then. With 'Ubuntu 10.04.2 LTS (Lucid)'  I have found a copy here.
http://releases.ubuntu.com/lucid/  this one ['64-bit PC (AMD64) desktop CD']("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso")  Would you recommend this link, or suggest another?
The one thing that worries me about this. With 10 I did not have a system that full suited my needs. Lots if issues with it.   11 solved that.  Apart from the permission glitch. But I had that with both versions.  

I would love to try and figure this mess out before having to revert to a reinstall.  If that is possible.  If things crash while do so. What the heck, I'll have to reinstall at that point.
Thanks for you time and help here. It is most appreciated. 
Cheers
Andy

---

### Post by redmk2 on 2011-06-25
> **9000cse said:**
> Hi.  How are you today? OK, understood all below.

The only # I see is the one next to the number of the thread (#14).  I do not think I'll worry about that right now.
Are you looking for the #Button when you are in the editor?  When you can type your response?  When you have the smilies on the right and the formating at the top or the text box?> 

Understood.  Clicking on the 'HELP' button, I get '[COLOR=#000000][FONT=Ubuntu][COLOR=#535353]**Ubuntu Desktop Guide'  So, this must be UBUNTU ?**
[/COLOR][/FONT][/COLOR]
Huh?   Where is this help button?  What is in the file /etc/issue ```
cat /etc/issue
```> 

Right, Reinstall it is then. With 'Ubuntu 10.04.2 LTS (Lucid)'  I have found a copy here.
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)  this one ['64-bit PC (AMD64) desktop CD']("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso")  Would you recommend this link, or suggest another?
That will do.> 
The one thing that worries me about this. With 10 I did not have a system that full suited my needs. Lots if issues with it.
What were the issues?> 
11 solved that.  Apart from the permission glitch. But I had that with both versions.
Hmmmmmmm>  

I would love to try and figure this mess out before having to revert to a reinstall.  If that is possible.  If things crash while do so. What the heck, I'll have to reinstall at that point.
Hopefully someone wonders by who knows KDE.  I have no experience with KDE so I'm the wrong guy to ask.  :-(> 

Thanks for you time and help here. It is most appreciated. 
Cheers
Andy
Good luck

---

### Post by 9000cse on 2011-06-25
Hi, sorry it's taken a long time to get back to this. Been a bit busy today.

> **redmk2 said:**
> Are you looking for the #Button when you are in the editor?  When you can type your response?  When you have the smilies on the right and the formating at the top or the text box?Huh? 
If it's surposed to be there, I cannot see it :(
> 
 Where is this help button?  On the Desktop task bar, from left to rigth, File, edit, View, Places, Help.
> 
What is in the file /etc/issue ```
cat /etc/issue
```Got the /etc/  but do not have issue ?  I do not understand the [code]
> 
That will do.What were the issues?Hmmmmmmm 
Had some problems with Firefox, installing some software. Again, all down to permissions.
> 
Hopefully someone wonders by who knows KDE.  I have no experience with KDE so I'm the wrong guy to ask.  :-(
Good luckOK, I can well understand. I may have to reinstall to 'Ubuntu 10.04.2 LTS (Lucid).  But before I do, I would love to be able to fix this KDE problem.  
Kubuntu (KDE) and not Ubuntu (Gnome) -  These are the front end, Yes? So, if that is the case, and I have them running side by side. That would cause a problem, a conflict?
Anyway, never did get your name. But thanks for all your time and help. Please keep an eye on this thread, see how it progress.


[SIZE=3][COLOR=Red]ANYBODY OUT THERE KNOW ABOUT KDE?  [/COLOR][/SIZE]
Because this guy needs a lot , well some, help.
Cheers, and thanks for reading
Andy

---

### Post by redmk2 on 2011-06-25
> **9000cse said:**
> Hi, sorry it's taken a long time to get back to this. Been a bit busy today.


If it's surposed to be there, I cannot see it :(
Then you will need to change the editor options.  At the top left of the page click on **_User CP_**.  Then under **_Settings & Options_** select **_Edit Options _**.  At the bottom of the page you can select **_editor options_**.  Select: **_[COLOR="Blue"]Standard Editor - Extra Formatting Controls[/COLOR]_**.> 

On the Desktop task bar, from left to rigth, File, edit, View, Places, Help.

What is a "Desktop Task Bar"?  Be kind now, I've only been doing this for about 10 or 12 years now.  :D> 
Got the /etc/  but do not have issue ? 
Sure you do, it is a file not a folder.> 
 I do not understand the command?
In the terminal type in the following command and then hit <enter>```
cat /etc/issue
```> 
Had some problems with Firefox, installing some software. Again, all down to permissions.
I'll bet this is a problem of familiarity; your familiarity. > 
OK, I can well understand. I may have to reinstall to 'Ubuntu 10.04.2 LTS (Lucid).  But before I do, I would love to be able to fix this KDE problem.  
Kubuntu (KDE) and not Ubuntu (Gnome) -  These are the front end, Yes? So, if that is the case, and I have them running side by side. That would cause a problem, a conflict?
Gnome and KDE are Desktop Environments.  You can install them both, but you pick one or the other at login time.  The KDE errors have to do with Samba interacting with the KDE environment.  When you use Gnome you will have Gnome errors for sure, but they won't be the same cures to those errors. > 
Anyway, never did get your name. But thanks for all your time and help. Please keep an eye on this thread, see how it progress.
Red is the name.> 


[SIZE=3][COLOR=Red]ANYBODY OUT THERE KNOW ABOUT KDE?  [/COLOR][/SIZE]
Because this guy needs a lot , well some, help.
Cheers, and thanks for reading
Andy

---

### Post by 9000cse on 2011-06-26
Hi Red.  OK, ....I see the difference now in the text.

> **redmk2 said:**
> Then you will need to change the editor options.  At the top left of the page click on **_User CP_**.  Then under **_Settings & Options_** select **_Edit Options _**.  At the bottom of the page you can select **_editor options_**.  Select: **_[COLOR="Blue"]Standard Editor - Extra Formatting Controls[/COLOR]_**. I see a difference.  
> 
What is a "Desktop Task Bar"?  Be kind now, I've only been doing this for about 10 or 12 years now.[/qoute] Ok, maybe that's a windows term. Just taken a SS, but what I wanted to show you is not there. But that's what I call the task bar. [quote] :DSure you do, it is a file not a folder.In the terminal type in the following command and then hit <enter>```
cat /etc/issue
```I'll bet this is a problem of familiarity; your familiarity. I get ```
Ubuntu 11.04 \n \l

``` My Familiarty.  Not sure I understand that that?
>  Gnome and KDE are Desktop Environments.  You can install them both, but you pick one or the other at login time.  The KDE errors have to do with Samba interacting with the KDE environment.  When you use Gnome you will have Gnome errors for sure, but they won't be the same cures to those errors. Red is the name.
Right, OK, this system just goes straight to DT.  I will change it.

Thanks RED.

---

### Post by redmk2 on 2011-06-26
> **9000cse said:**
>  I get ```
Ubuntu 11.04 \n \l

```


Seeing the above tells me that you have a Gnome based DE (what you call the DT).  It also tells me that you have not completely purged SMB4K (the K stands for KDE).  How do you do that?  I haven't a clue, but it is interfering with the proper running of the system.

You know what I would do anyway. ;-)

---

### Post by 9000cse on 2011-06-26
> **redmk2 said:**
> Seeing the above tells me that you have a Gnome based DE (what you call the DT).  It also tells me that you have not completely purged SMB4K (the K stands for KDE).  How do you do that?  I haven't a clue, but it is interfering with the proper running of the system.

You know what I would do anyway. ;-)

[COLOR="Red"][SIZE="3"]A funny thing happened to me on the way to the Forum......[/SIZE][/COLOR]

I DL 'Ubuntu 10.04.2 LTS (Lucid)'.  Burnt the ISO onto a CD. Re-Booted system from the CD. All going well.  And then full stop, on line 17659, or something like that.
I think the GODS just want me to use an Etch A Sketch Classic.
Now Back with a clean vers of 11.  done nothing to it. Bog Standard.  Have not fiddled. Just the default.  
> 
Unable to mount location, Failed to retrieve share list from server.

All I want to do is share out the drive I have for the kids to attach to. So they can save their school work.  Such FUN, Don't you just love it. :) 
And I still cannot find this #

I'm off to bed. Got to be up at 5am, to kick the CAT. It's 2311 here.

Andy, and if that Vettel wins another race, I'm going to punch him on the noise.

---

### Post by redmk2 on 2011-06-26
> **9000cse said:**
> [COLOR="Red"][SIZE="3"]A funny thing happened to me on the way to the Forum......[/SIZE][/COLOR]

I DL 'Ubuntu 10.04.2 LTS (Lucid)'.  Burnt the ISO onto a CD. Re-Booted system from the CD. All going well.  And then full stop, on line 17659, or something like that.
I think the GODS just want me to use an Etch A Sketch Classic.
Probably hardware conflict that 11.04 resolves.> 

Now Back with a clean vers of 11.  done nothing to it. Bog Standard.  Have not fiddled. Just the default.
Good deal.>   

All I want to do is share out the drive I have for the kids to attach to. So they can save their school work.

First you have to make sure the machine can be ID'd by hostname (/etc/hosts) or COMPUTER NAME (NetBIOS).  Are you running DHCP to obtain an IP address?  If so can you make that a reserved IP address in the router?  This will make the IP address the same all the time.

My suggestion here is to try ONE THING AT A TIME.  Let's get this done and we will go to the next step.> 

Such FUN, Don't you just love it. :)  And I still cannot find this #
Are you referring to the button (#) to wrap text in [code] brackets in the the forum editor or something else?> 

I'm off to bed. Got to be up at 5am, to kick the CAT. It's 2311 here.

Andy, and if that Vettel wins another race, I'm going to punch him on the noise.
I think you mean nose.  Noise is what comes out the tailpipes.  I watched the race.  The team is hard to beat.  Superb cars and flawless pit stops.  Mark is not fast enough to contend.

---

### Post by 9000cse on 2011-06-27
> **redmk2 said:**
> Probably hardware conflict that 11.04 resolves.Good deal.First you have to make sure the machine can be ID'd by hostname (/etc/hosts) or COMPUTER NAME (NetBIOS).  Are you running DHCP to obtain an IP address?  If so can you make that a reserved IP address in the router?  This will make the IP address the same all the time.  Yes, it seems that way.
Static IP, always, on all systems here. and router has been told to keep them
> 
My suggestion here is to try ONE THING AT A TIME.  Let's get this done and we will go to the next step.Are you referring to the button (#) to wrap text in [code] brackets in the the forum editor or something else? Agreed. 
I can now see a NW, both ways. BUT, What is LR-UBUNTU'?  I keep getting this from a windows system when trying to attach to a share. Keeps asking for a username and PW, UBUNTU tells me. > Unable to mount location, Failed to retrieve share list from server.



However, now I can see systems.  But I have a new system that's arrived called 'LR-UBUNTU' and get > The Permissions of 'SMB' could not be determined 
 which, are not set, apart from logging in which is auto.
> 
I think you mean nose.  Noise is what comes out the tailpipes.  I watched the race.  The team is hard to beat.  Superb cars and flawless pit stops.  Mark is not fast enough to contend.
 Thanks for picking up on that. Now the whole UBUNTU world know I cannot spell. :D
Yes, They were the Joke of the pit lane, now nothing can come near them. Feel sorry for Mark, the one guy on the grid that deserves a WC, it's him.  Anyway. Come the BGP, rules change. Will that effect RB, I doubt it. But maybe the others will be a tad closer.  My money is on Button and Alonso. £10 on each to win.

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> Yes, it seems that way.
Static IP, always, on all systems here. and router has been told to keep them
Good deal.> 

I can now see a NW, both ways. BUT, What is LR-UBUNTU'? 
Could that be the hostname the system.  It's easy to find out.  what do you get use this command form the terminal```
hostname
```
I get something like this ```
red@jaguar:~$ [COLOR="Blue"]hostname[/COLOR]
[COLOR="Red"]jaguar[/COLOR]
red@jaguar:~$
```
> 
 I keep getting this from a windows system when trying to attach to a share. Keeps asking for a username and PW, UBUNTU tells me.
ONE THING AT A TIME.  Let's not muck it up here with too many things at one time.  I can fix your probs from here if you slow down.>  

However, now I can see systems.  But I have a new system that's arrived called 'LR-UBUNTU' and get 
 which, are not set, apart from logging in which is auto.
What machine is set to login automatically?> 

 Thanks for picking up on that. Now the whole UBUNTU world know I cannot spell. :D
Yes, They were the Joke of the pit lane, now nothing can come near them. Feel sorry for Mark, the one guy on the grid that deserves a WC, it's him.  Anyway. Come the BGP, rules change. Will that effect RB, I doubt it. But maybe the others will be a tad closer.  My money is on Button and Alonso. £10 on each to win.
Probably Alonzo.  He is more aggressive than Button.

---

### Post by 9000cse on 2011-06-27
> **redmk2 said:**
> Good deal.Could that be the hostname the system.  It's easy to find out.  what do you get use this command form the terminal```
hostname
```
I get something like this ```
red@jaguar:~$ [COLOR="Blue"]hostname[/COLOR]
[COLOR="Red"]jaguar[/COLOR]
red@jaguar:~$
```

Ok, her's mine
```
asjmm@asjmm-saviour:~$ hostname
asjmm-saviour
asjmm@asjmm-saviour:~$ 
```

LR_UBUNTU????  This does show up on all the XP & 7 systems, but access denied. 
> 
ONE THING AT A TIME.  Let's not muck it up here with too many things at one time.  I can fix your probs from here if you slow down.What machine is set to login automatically?
Agreed, Mine, This UBUNTU one.
> 
Probably Alonzo.  He is more aggressive than Button.

Yes, agreed, Certain races suite Button, but not all.  But when he gets the bit between his teeth..WOW, he can drive. Canada proved that.

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> Ok, her's mine
```
asjmm@asjmm-saviour:~$ hostname
asjmm-saviour
asjmm@asjmm-saviour:~$ 
```
Then the hostname of that system is *[COLOR="Blue"]asjmm-saviour[/COLOR]* without a doubt.  The next thing we need to do is see if it is listed correctly in the /etc/hosts file.  Post the output of the command ```
cat /etc/hosts
``` 

My /etc/ hosts file looks like this ```
red@jaguar:~$[COLOR="Red"]cat /etc/hosts[/COLOR]
127.0.0.1	localhost
[COLOR="Red"]192.168.1.3	jaguar
[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


> 

LR_UBUNTU????  This does show up on all the XP & 7 systems, but access denied. 
It is not important at this point.  My hunch is that it is old information that is still held by the Windows system.  Don't worry about it right now.  We are only concerned with the host [COLOR="Blue"]asjmm-saviour[/COLOR] (your Ubuntu install). > 


Yes, agreed, Certain races suite Button, but not all.  But when he gets the bit between his teeth..WOW, he can drive. Canada proved that.
Yes that was a fantastic race.  I have been to the Canadian GP.  The track is very interesting.  Never been there when it rained thank god.

---

### Post by 9000cse on 2011-06-27
```
asjmm@asjmm-saviour:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	asjmm-saviour

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
asjmm@asjmm-saviour:~$ 

```

Not been to any over the pond. Ben to a few in Europe though.
SPA, when it rains is wet ;-)

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> ```
asjmm@asjmm-saviour:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	asjmm-saviour

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
asjmm@asjmm-saviour:~$ 

```
What is the IP address of the host asjmm-saviour (192.168.etc.etc)?  It is also important to note for future reference that NetBIOS names can't exceed 15 characters.  This hostname is close, but should work.> 

Not been to any over the pond. Ben to a few in Europe though.
SPA, when it rains is wet ;-)
A treacherous course at best.

---

### Post by 9000cse on 2011-06-27
Hi Red, Yes, 192.168.xxx.xxx
I take it that asjmm-saviour is UBUNTU NetBIOS name?

I have driven the 'RING' in the wet, but that, for me was just a Sunday afternoon drive. 12:45.456m, in the dry, under 10, in a 9000.  as Bikes were going past as if I had parked up for lunch.  :D

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> Hi Red, Yes, 192.168.xxx.xxx
Okay: take that address and use it like this in the /etc/hosts file```
127.0.0.1	localhost
192.168.xxx.xxx	asjmm-saviour

```

You will have to do this using sudo rights.  The easiest way for you is to hit <alt+f2>  and in the box run this command: **[COLOR="DarkGreen"]gksudo gedit /etc/hosts[/COLOR]**

Change the IP address from 127.0.1.1 to 192.168.xxx.xxx (using your IP address)> 

I take it that asjmm-saviour is UBUNTU NetBIOS name?

ONE THING AT A TIME.  :D  I'll explain that in a bit.> 

I have driven the 'RING' in the wet, but that, for me was just a Sunday afternoon drive. 12:45.456m, in the dry, under 10, in a 9000.  as Bikes were going past as if I had parked up for lunch.  :D
I spent my time as a participant racing cars years ago.  I've lost too many friends to racing (Indy, Can-Am and F1).

---

### Post by 9000cse on 2011-06-27
OK Done..


So, you know the buz from the real thing. Not done any real racing. But a lot of Karting and track days.

---

### Post by 9000cse on 2011-06-27
OK done.

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> OK done.

At this point from the terminal of asjmm-saviour you should be able to ping itself by hostname and have it return pings form the 192.168..xxx.xxx IP address.  like this ```
red@[COLOR="Red"]jaguar[/COLOR]:~$ ping [COLOR="Red"]jaguar[/COLOR]
PING [COLOR="Red"]jaguar[/COLOR] (192.168.1.3) 56(84) bytes of data.
64 bytes from [COLOR="Red"]jaguar[/COLOR] (192.168.1.3): icmp_seq=1 ttl=64 time=0.016 ms
64 bytes from [COLOR="Red"]jaguar[/COLOR] (192.168.1.3): icmp_seq=2 ttl=64 time=0.020 ms
64 bytes from [COLOR="Red"]jaguar[/COLOR] (192.168.1.3): icmp_seq=3 ttl=64 time=0.015 ms
64 bytes from [COLOR="Red"]jaguar[/COLOR] (192.168.1.3): icmp_seq=4 ttl=64 time=0.013 ms

--- malibu ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.013/0.016/0.020/0.002 ms

```

Now on to the next step.  have you installed the Samba server?  If so can you see it from Places>>Network ?

---

### Post by 9000cse on 2011-06-27
Hi their. OK.
```


PING asjmm.saviour (92.242.132.15) 56(84) bytes of data.
^C
--- asjmm.saviour ping statistics ---
25 packets transmitted, 0 received, 100% packet loss, time 24005ms

asjmm@asjmm-saviour:~$ ping asjmm-saviour
PING asjmm-saviour (192.168.1.69) 56(84) bytes of data.
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=1 ttl=64 time=0.023 ms
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=2 ttl=64 time=0.024 ms
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=3 ttl=64 time=0.025 ms
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=4 ttl=64 time=0.025 ms
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=5 ttl=64 time=0.025 ms

--- asjmm-saviour ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8998ms
rtt min/avg/max/mdev = 0.023/0.024/0.025/0.003 ms
asjmm@asjmm-saviour:~$ 
```

Yes, Samba - server installed.  But do not see it under Places>>network
Had to fire up SAMBA Server Configuration.

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> Hi their. OK.
```


asjmm@asjmm-saviour:~$ ping asjmm-saviour
PING asjmm-saviour (192.168.1.69) 56(84) bytes of data.
64 bytes from asjmm-saviour (192.168.1.69): icmp_req=1 ttl=64 time=0.023 ms
...

--- asjmm-saviour ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8998ms
rtt min/avg/max/mdev = 0.023/0.024/0.025/0.003 ms
asjmm@asjmm-saviour:~$ 
```

Yes, Samba - server installed.  But do not see it under Places>>network
Had to fire up SAMBA Server Configuration.

What do you mean by "fire up SAMBA Server Configuration"?  What do you get from the terminal from this```
pgrep -l mbd
```

This is what I get```
pgrep -l mbd
972 smbd
[COLOR="Blue"]1073 nmbd[/COLOR]
1076 smbd
1648 smbd
2623 smbd

``` 
The nmbd daemon (service) is important.  It's the name service daemon for Samba.

You might have to restart these with ```
sudo service nmbd restart
``` and ```
sudo service smbd restart
```

How about posting the results of ```
testparm -s
```

---

### Post by 9000cse on 2011-06-27
```

asjmm@asjmm-saviour:~$ pgrep -l mbd
794 smbd
820 smbd
1809 nmbd
4857 smbd
4859 smbd
4923 smbd
6073 smbd
17880 smbd
asjmm@asjmm-saviour:~$ 

```
```

asjmm@asjmm-saviour:~$ sudo service nmbd restart
[sudo] password for asjmm: 
nmbd start/running, process 18026
asjmm@asjmm-saviour:~$ 

```
```
asjmm@asjmm-saviour:~$ sudo service smbd restart
smbd start/running, process 18037
asjmm@asjmm-saviour:~$ 

```
```
asjmm@asjmm-saviour:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[scalextric]"
Processing section "[ebay]"
Processing section "[KIDS]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = SAVIOUR
	netbios name = [COLOR="Red"]LR-UBUNTU[/COLOR]
	server string = %h server (Samba, Ubuntu)
	map to guest = [COLOR="red"]Bad User[/COLOR]
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[scalextric]
	path = /media/stuff/scalextric
	read only = No
	guest ok = Yes

[ebay]
	path = /media/DATA/ebay
	read only = No
	guest ok = Yes

[KIDS]
	path = /media/KIDS
	read only = No
	guest ok = Yes
asjmm@asjmm-saviour:~$ 

```

Hows it looking?

---

### Post by redmk2 on 2011-06-27
The system is running and you know how to reload the smbd and nmbd processes with ```
sudo service <process> restart
``` That's a good thing.

> **9000cse said:**
> 
```
asjmm@asjmm-saviour:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[scalextric]"
Processing section "[ebay]"
Processing section "[KIDS]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = SAVIOUR
	netbios name = [COLOR="Red"]LR-UBUNTU[/COLOR]  **[COLOR="Purple"]<-- this should be removed.[/COLOR]**
	server string = %h server (Samba, Ubuntu)
	map to guest = [COLOR="red"]Bad User[/COLOR] [COLOR="Purple"]**<--This is normal **[/COLOR]
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[scalextric]
	path = /media/stuff/scalextric
	read only = No
	guest ok = Yes

[ebay]
	path = /media/DATA/ebay
	read only = No
	guest ok = Yes

[KIDS]
	path = /media/KIDS
	read only = No
	guest ok = Yes
asjmm@asjmm-saviour:~$ 

```

Hows it looking?

Look for my comments above in [COLOR="Purple"]**purple**[/COLOR].

You do not need to declare a NetBIOS name.  The nmbd daemon converts the hostname (asjmm-saviour in your case) to a NetBIOS name.  You are just creating a conflict here.  But...on the other hand we now know why the Windows machines saw that name.  I think if you just remove the line ```
netbios name = [COLOR="Red"]LR-UBUNTU[/COLOR]
``` and restart the both processes then *Bob's your Uncle'*!

There may be some tinkering that needs to be done and we can take care of that later.  Let us see the output of (and it will be a lot) this```
smbtree -d3
```

Edit:  i forgot to ask:  Have you added yourself (the user asjmm) to the Samba users database?  If not then you need to do this```
smbpasswd -a asjmm
```  Hopefully you are the same user on the windows machine.  if not then you will always be the guest *[COLOR="DarkSlateGray"]**nobody**[/COLOR]* on Samba shares from a Windows machine.

This will be the next thing we will tackle.

---

### Post by 9000cse on 2011-06-27
I need to get back to root to be able to change the SMB.conf file. Lost the code to be able to do that. It's somewhere in these threads, 
Yes, asjmm in samba
Cheers
Andy

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> I need to get back to root to be able to change the SMB.conf file. Lost the code to be able to do that. It's somewhere in these threads, 
Yes, asjmm in samba
Cheers
Andy

Crikey mate, we just did that kind of thing.  You need to do this: <alt+f2> and in the box type ```
gksudo  gedit /etc/samba/smb.conf
```

---

### Post by 9000cse on 2011-06-27
Got this, acccess denied.

```
asjmm@asjmm-saviour:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::225:22ff:fe11:916e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter asjmm's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Connecting to host=192.168.1.69
Connecting to 192.168.1.69 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Got a positive name query response from 192.168.1.250 ( 192.168.1.250 )
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.250 ( 192.168.1.250 )
Connecting to host=192.168.1.250
Connecting to 192.168.1.250 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
[COLOR="Red"]failed tcon_X with NT_STATUS_ACCESS_DENIED[/COLOR]
Connecting to host=BTHOMEHUB
Connecting to 192.168.1.250 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="red"]SPNEGO login failed: Logon failure[/COLOR]
[COLOR="red"]failed tcon_X with NT_STATUS_ACCESS_DENIED[/COLOR]
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Connecting to host=192.168.1.69
Connecting to 192.168.1.69 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SAVIOUR
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Connecting to host=192.168.1.69
Connecting to 192.168.1.69 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\SHARONSPC      		
Connecting to host=SHARONSPC
resolve_lmhosts: Attempting lmhosts lookup for name SHARONSPC<0x20>
resolve_wins: Attempting wins lookup for name SHARONSPC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SHARONSPC<0x20>
Connecting to 92.242.132.15 at port 445
Connecting to 92.242.132.15 at port 139
Error connecting to 92.242.132.15 (Connection refused)
cli_start_connection: failed to connect to SHARONSPC<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\ROMING         		Me2
Connecting to host=ROMING
resolve_lmhosts: Attempting lmhosts lookup for name ROMING<0x20>
resolve_wins: Attempting wins lookup for name ROMING<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROMING<0x20>
Connecting to 92.242.132.15 at port 445
Connecting to 92.242.132.15 at port 139
Error connecting to 92.242.132.15 (Connection refused)
cli_start_connection: failed to connect to ROMING<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\LR-UBUNTU      		asjmm-saviour server (Samba, Ubuntu)
Connecting to host=LR-UBUNTU
resolve_lmhosts: Attempting lmhosts lookup for name LR-UBUNTU<0x20>
resolve_wins: Attempting wins lookup for name LR-UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LR-UBUNTU<0x20>
Connecting to 92.242.132.15 at port 445
Connecting to 92.242.132.15 at port 139
Error connecting to 92.242.132.15 (Success)
cli_start_connection: failed to connect to LR-UBUNTU<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
HOME
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.250 ( 192.168.1.250 )
Connecting to host=192.168.1.250
Connecting to 192.168.1.250 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
failed tcon_X with NT_STATUS_ACCESS_DENIED
Connecting to host=BTHOMEHUB
Connecting to 192.168.1.250 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO [COLOR="red"]login failed: Logon failure[/COLOR]
[COLOR="Red"]failed tcon_X with NT_STATUS_ACCESS_DENIED[/COLOR]

```
  Tried ```
smbpasswd -a asjmm
```
Got nowhere.
Just cleared the screen.

Funny thing is. I have an XP LT next to me. It sees 

> 
asjmm-saviour server (samba, ubuntu) ( Lr-ubuntu)

Then the shared drives.
> 
ebay
james
kids
scalextric

Gets straight into Scalextric.  But cannot access the others.

---

### Post by redmk2 on 2011-06-27
I'm going to go over the data you provided.  I can tell you now that what we did is working.  You can see it in the first 20 or so lines.  The problem is Samba sees it as SAVIOUR.  I'll bet you can't use dashes (-) in the hostname.  We should change that to be sure.

In addition theres are other hosts on the network with shares so I will have to know what they are.

You shuld not have any problems using gedit as root.  Try using it this way from the command line (cut and paste)```
gksudo gedit /etc/samba/smb.conf &
```

don't forget the &

---

### Post by 9000cse on 2011-06-27
OK look in there, it worked. SAVIOUR is in there. ASJMM ot asjmm is not.

I have in samba, asjmm-saviour. all PC on network are name-saviour (name being the use, wife, jmaes, siobhan, etc.

Could that have anything to do with it?

I have just rebooted the system. and seem to have lost the Lr-ubuntu

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> OK look in there, it worked. SAVIOUR is in there. ASJMM ot asjmm is not.

Duh! ](*,)  What the hell does that mean.  Looked in where?> 

I have in samba, asjmm-saviour. all PC on network are name-saviour (name being the use, wife, jmaes, siobhan, etc.

In samba where? What are those names?  Users?  Samba users?  Host names?> 

Could that have anything to do with it?

Of course.  

It is best not to confuse the help here. 

Full disclosure.  Remember I said one step at a time.  Why did you go and muck about with  Samba on a fresh install?  What happened to "Bog Standard. Have not fiddled. Just the default."?

I feel like we have been here before... :-(

Edit:  I think you mean you can see servers (Samba and windows) and you can see the shares on the the host asjmm-saviour.  Am I right?  if so...as an experiment and understanding that we have removed the netbios name from the smb.conf file, **I sugesst we change the hostname of the Ubuntu machine**.  This can be temporary.  We both need to be more specific in what we are doing.  Sorry for getting upset.  I don't think either of us want to do this forever.

---

### Post by 9000cse on 2011-06-27
> **redmk2 said:**
> Duh! ](*,)  What the hell does that mean.  Looked in where? In samba where? What are those names?  Users?  Samba users?  Host names?

Of course.  

It is best not to confuse the help here. 

Full disclosure.  Remember I said one step at a time.  Why did you go and muck about with  Samba on a fresh install?  What happened to "Bog Standard. Have not fiddled. Just the default."?

I feel like we have been here before... :-(

OK, sorry, have not tampered with anything. 
Looked in the sba.conf file. Saviour is there, asjmm is not
All systems ahve user name-saviour. as in asjmm-saviour (I explain that later).
> Edit: i forgot to ask: Have you added yourself (the user asjmm) to the Samba users database? If not then you need to do this I have in samba, 
> What are those names? Users? Samba users? Host names?  name-saviour. as in asjmm-saviour

> I feel like we have been here before... 
OK, I have to stop being the helpdesk guy, I'm now a user. It's hard to switch...I will not touch a thing until you tell me to. 
I won't even pick my nose.

---

### Post by redmk2 on 2011-06-27
See my update at the bottom of the previous post.

---

### Post by 9000cse on 2011-06-27
> Edit: I think you mean you can see servers (Samba and windows) and you can see the shares on the the host asjmm-saviour. Am I right?  Yes.
> if so...as an experiment and understanding that we have removed the netbios name from the smb.conf file, I sugesst we change the hostname of the Ubuntu machine. This can be temporary.  OK, I'll do that now.

> We both need to be more specific in what we are doing. Yes >  Sorry for getting upset. I don't think either of us want to do this forever.
No problem, it's you that's helping me out. I tend to forget that. It's the other way round, in my head.  
I'll change the  hostname name now.

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> OK, sorry, have not tampered with anything. 
Looked in the sba.conf file. Saviour is there, asjmm is not

I assume you mean that Saviour is the workgroup name.  is this correct?
I also have to assume that asjm is your user name.  As such it should never appear in the /etc/samba/smb.conf file.
> 

All systems ahve user name-saviour. as in asjmm-saviour (I explain that later).
I have in samba, name-saviour. as in asjmm-saviour.  
Where would you have asjmm-saviour?  Are you saying that you see the name asjmm-saviour when browsing in Places>>Network?> 

OK, I have to stop being the helpdesk guy, I'm now a user. It's hard to switch...I will not touch a thing until you tell me to. 
I won't even pick my nose.
I think you can be trusted to pick your nose, maybe not your friends nose.  :-)

---

### Post by 9000cse on 2011-06-27
> **redmk2 said:**
> I assume you mean that Saviour is the workgroup name.  is this correct?
Yes, 
> 
I also have to assume that asjm is your user name.  As such it should never appear in the /etc/samba/smb.conf file. 
asjmm is the user name, yes
> 
Where would you have asjmm-saviour?  Are you saying that you see the name asjmm-saviour when browsing in Places>>Network?

All Windows system are name-saviour. name being the user. Saviour being the workgroup. Don't ask why, it just is. I'm not to sure myself. This system, UBUNTU. user name is asjmm, workgroup is Saviour. How and why I get 
```
asjmm@asjmm-saviour:~$ 

``` I'm not to sure. I must have followed what I had put on the Windows system. As to where, that sits, I do not know.  Come to thing of it, I have not put it anywhere. Set this up with a User name of asjmm and a work group of saviour. Cannot remember anywhere else that I might have put that..
> 
I think you can be trusted to pick your nose, maybe not your friends nose.  :-)
No comment.

PS, Also, when you look in Network, there is a share  asjmm-saviour, with in that is print$

---

### Post by redmk2 on 2011-06-27
> **9000cse said:**
> Yes, 

asjmm is the user name, yes

All Windows system are name-saviour. name being the user. Saviour being the workgroup. Don't ask why, it just is. I'm not to sure myself. This system, UBUNTU. user name is asjmm, workgroup is Saviour. How and why I get 
```
asjmm@asjmm-saviour:~$ 

``` I'm not to sure. I must have followed what I had put on the Windows system. As to where, that sits, I do not know.  Come to thing of it, I have not put it anywhere. Set this up with a User name of asjmm and a work group of saviour. Cannot remember anywhere else that I might have put that..

No comment.

PS, Also, when you look in Network, there is a share  asjmm-saviour, with in that is print$

I think I understand.  A samba resource is //server/share  This means that the print share is expressed as //sajmm-saviour/print$

The other shares (what you are calling drives) are```
ebay
james
kids
scalextric 
```
They also can be expressed as: 
```
//sajmm-saviour/ebay
//sajmm-saviour/james
//sajmm-saviour/kids
//sajmm-saviour/scalextric
```

If you can still see these then Samba is working correctly.  Now we have to adjust the access to these various shares.  Can you see these shares using a Windows machine?  I know I'm asking again on this issue.  :D

It's late.  Do you wish to stop?  I am about to be called to supper.

---

### Post by 9000cse on 2011-06-28
Hi, it's me. I'm back.  Fall asleep. Sorry.
The shares ```
//asjmm-saviour/ebay
//sajmm-saviour/james
//sajmm-saviour/kids
//sajmm-saviour/scalextric
```

Yes

Edit. This morning. Shares on Ubuntu gone. Had to redo them. Windows systems only see Printers and Faxes under asjmm-saviour
So a bit confused.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Hi, it's me. I'm back.  Fall asleep. Sorry.
The shares ```
//asjmm-saviour/ebay
//sajmm-saviour/james
//sajmm-saviour/kids
//sajmm-saviour/scalextric
```

Yes

Edit. This morning. Shares on Ubuntu gone. Had to redo them. Windows systems only see Printers and Faxes under asjmm-saviour
So a bit confused.

What did you do to redo them?

---

### Post by 9000cse on 2011-06-28
Hi, and good morning, or afternoon depending on where you live.

Click on the folders and shared options.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Hi, and good morning, or afternoon depending on where you live.

Click on the folders and shared options.

You will have to be more descriptive.  Did you right click on a folder and set new sharing options?  Are we back to you doing thisgs and then me asking WTF?

---

### Post by 9000cse on 2011-06-28
No, When I booted system, and checked how far we had progressed, I found that the folders, were not shared out. So re-shared them

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> No, When I booted system, and checked how far we had progressed, I found that the folders, were not shared out. So re-shared them

So what are these?

```
[scalextric]
	path = /media/stuff/scalextric
	read only = No
	guest ok = Yes

[ebay]
	path = /media/DATA/ebay
	read only = No
	guest ok = Yes

[KIDS]
	path = /media/KIDS
	read only = No
	guest ok = Yes

```

i got them from your smb.conf file,  This is the info returned using the command[I] testparm -s 
[/I].

Are you going to only create shares using the GUI (right click and share them out method)?  If so then you should remove the shares you have created in the *smb.conf* file.

Lets just see what usershares you have created today.  What do you get from this command ```
net usershare list
```

---

### Post by 9000cse on 2011-06-28
Hi

```
asjmm@asjmm-saviour:~$ net usershare list
james
ebay
scalextric
antonia
asjmm@asjmm-saviour:~$ 

```

So, GUI & SMB do it in a different way?

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Hi

[code[asjmm@asjmm-saviour:~$ net usershare list
james
ebay
scalextric
antonia
asjmm@asjmm-saviour:~$ 
[/code]

So, GUI & SMB do it in a different way?

Very different.  The share definitions for the GUI way (called usershares) are stored in binary form at: /var/lib/samba/usershares 

It's confusing to create the share both ways.  You decide what you want to do for this issue.  Remove one or the other and see what happens.

But...  It sounds like at least you can now see the server and its printer share.  This is good.

I needed to see if the nmbd daemon loaded correctly when you first boot up.  What is the output of the command ```
pgrep -l mbd
```

Remember I said don't do anything without me telling you to?  You really need to do what YOU said you would do.

---

### Post by 9000cse on 2011-06-28
> **redmk2 said:**
> Very different.  The share definitions for the GUI way (called usershares) are stored in binary form at: /var/lib/samba/usershares 

It's confusing to create the share both ways.  You decide what you want to do for this issue.  Remove one or the other and see what happens.

But...  It sounds like at least you can now see the server and its printer share.  This is good.

I needed to see if the nmbd daemon loaded correctly when you first boot up.  What is the output of the command ```
pgrep -l mbd
```

Remember I said don't do anything without me telling you to?  You really need to do what YOU said you would do.

OK, But I do try not to. 

```


asjmm@asjmm-saviour:~$ net usershare list
james
ebay
scalextric
antonia
asjmm@asjmm-saviour:~$ pgrep -l mbd
3241 nmbd
3248 smbd
3250 smbd
5674 smbd
5676 smbd
5678 smbd
6255 smbd
asjmm@asjmm-saviour:~$ 

```

Hows that look?

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> OK, But I do try not to. 

```


asjmm@asjmm-saviour:~$ net usershare list
james
ebay
scalextric
antonia
asjmm@asjmm-saviour:~$ pgrep -l mbd
3241 nmbd
3248 smbd
3250 smbd
5674 smbd
5676 smbd
5678 smbd
6255 smbd
asjmm@asjmm-saviour:~$ 

```

Hows that look?

It looks okay so far.  

Can use these shares now?  Can you see files in 
the shares from the Windows machines?

Are you going to delete the shares in the /etc/samba/smb.conf file?

---

### Post by 9000cse on 2011-06-28
> **redmk2 said:**
> It looks okay so far.  

Can use these shares now?  Can you see files in 
the shares from the Windows machines?

Are you going to delete the shares in the /etc/samba/smb.conf file?

YES, But asking for UN & PW.  But I have not set any. Then it comes back with \\asjmm-saviour\ xxxxx is not accessible. you might not have permissions to use this network

No, I would like to keep using samba, seems easy.  But if you think that could be a problem, then yes I will
Andy

EDIT..  All shares do the above. Apart from Scalextric, that goes  straight to files.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> YES, But asking for UN & PW.  But I have not set any. Then it comes back with \\asjmm-saviour\ xxxxx is not accessible. you might not have permissions to use this network


No, I would like to keep using samba, seems easy.  But if you think that could be a problem, then yes I will
Andy

EDIT..  All shares do the above. Apart from Scalextric, that goes  straight to files.

The user/pass is solvable in a couple of ways.  First we need to see what type of shares you are going to be using.  Using /etc/samba/smb.conf file creates "classic shares". The shares created using the GUI are called "usershares"  BOTH ARE Samba Shares.

So which will it be: classic shares or usershares?

---

### Post by 9000cse on 2011-06-28
classic shares

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> classic shares

Then you need to **[COLOR="Blue"]remove the shares that you created with the GUI[/COLOR]**.  Then you need to [COLOR="DarkGreen"]**reload the smbd and nmbd**[/COLOR] processes.

I will be leaving soon for about 4 to 5 hours today.  Hurry up and let me know what happens.

---

### Post by 9000cse on 2011-06-28
Done
```


asjmm@asjmm-saviour:~$ net usershare list
asjmm@asjmm-saviour:~$ sudo service nmbd restart
[sudo] password for asjmm: 
nmbd start/running, process 10447
asjmm@asjmm-saviour:~$ sudo service smbd restart
smbd start/running, process 10454
asjmm@asjmm-saviour:~$ 

```

I think that's right?

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Done
```


asjmm@asjmm-saviour:~$ net usershare list
asjmm@asjmm-saviour:~$ sudo service nmbd restart
[sudo] password for asjmm: 
nmbd start/running, process 10447
asjmm@asjmm-saviour:~$ sudo service smbd restart
smbd start/running, process 10454
asjmm@asjmm-saviour:~$ 

```

I think that's right?

Can you see the original shares you had in the smb.conf file?

---

### Post by 9000cse on 2011-06-28
Yes, just opened it in RO and they are there.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Yes, just opened it in RO and they are there.

What is RO????

---

### Post by 9000cse on 2011-06-28
read Only.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> read Only.

Ahhhh, that would be "opened **[COLOR="Red"]as[/COLOR]** RO".

But that's not what I meant anyway.  I want to know if you can see the shares when browsing to them (Places>>Network).

Just curious: Are you a native English speaker?

---

### Post by 9000cse on 2011-06-28
Yes
> 
Just curious: Are you a native English speaker?


Sometimes, depends who she is!

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Yes

So you can browse to see the shares and English is your primary language: right?

---

### Post by 9000cse on 2011-06-28
Yes to all above

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> Yes to all above

Okay!

At this point we have to stop for a few hours.  I can fix the shares any what you want and even make you a template for future shares.  Don't go mucking about in the smb.conf file.  I will sort the user/pass situation also.

---

### Post by 9000cse on 2011-06-28
OK, I think 4 to five hours I'll be in bed. That's Midnight here. So leave until tomorrow.  
Where about's on this planet do you live?
OH BTW, why did you ask if I spoke Klingon, Sorry English.

---

### Post by redmk2 on 2011-06-28
> **9000cse said:**
> OK, I think 4 to five hours I'll be in bed. That's Midnight here. So leave until tomorrow.  
Where about's on this planet do you live?
Los Angeles, California, USA (GMT-8 is the TZ).> 
OH BTW, why did you ask if I spoke Klingon, Sorry English.

Because you don't always use the language properly.  For example your use of the term "in" instead of "as" in the RO response.  Another example is the use of the term "right" when what is really meant is "correct".

I don't speak "Queens English" either, but I try to use the proper terms.  I check my spelling too.  I'm a terrible speller and I have lots of typos.  I just check my work.  It is a reflection of who I am.

---

### Post by 9000cse on 2011-06-28
What is the 'Queens English?'  She speaks Latin most of the time. 
Come over here for a few years, we will soon change your habbits :)
English is a Language which changes with each generation. 
The English that was spoken last week, will differ come next week.
Reminds me of a quote, Charles V I think.
> 
I speak German to my Horse, French to woman, Spanish to God, Italian to men.  I find English is just not worth speaking any more.  Well, it went something like that.  Hay Ho, as they say. 
OH, I'm dyslexic by the way. Always have been. But nobody apart from me believed it. Until it was proven by the Uni I attended. 45 years into my Liff.  
OH Well, as Peter Green once sang.
Type later.
Andy  :guitar:

---

### Post by redmk2 on 2011-06-29
> **9000cse said:**
> What is the 'Queens English?
[**_This_**]("http://www.urbandictionary.com/define.php?term=Queens%20English") is what I mean by that.> 
Come over here for a few years, we will soon change your habbits :)
  
What makes you think I haven't spent time in th UK?  BTW -- habits only has one b in it.  :-)
> 
English is a Language which changes with each generation. 
The English that was spoken last week, will differ come next week.

When you are speaking about technical matters you need to be precise.  The [**_[COLOR="DarkSlateGray"]lingua franca[/COLOR]_**]("http://en.wikipedia.org/wiki/Lingua_franca") of tech is [**_[COLOR="DarkSlateGray"]proper English[/COLOR]_**]("http://en.wikipedia.org/wiki/English_in_computing").> 

Reminds me of a quote, Charles V I think.[QUOTE]I speak German to my Horse, French to woman, Spanish to God, Italian to men. I find English is just not worth speaking any more
[/QUOTE]I think you have that wrong -- It was the *Holy Roman Emperor* Charles V (a Hapsburg), ruler of France and Spain speaking of language in general```
 I speak Spanish to God, Italian to women, French to men, and German to my horse.
```No mention of English.  On the other hand; he wasn't English anyway.> 
Well, it went something like that.  Hay Ho, as they say.

Hmmmmmmmm
>  
OH, I'm dyslexic by the way. Always have been. But nobody apart from me believed it. Until it was proven by the Uni I attended. 45 years into my Liff.

I assume you mean life, not Liff.
>  
OH Well, as Peter Green once sang.
Type later.
...
Uh huh...

I think we ought to limit this to Samba concerns. :-)

---

### Post by 9000cse on 2011-06-29
No, I mean LIFF, LIFE is not complete, neither is the last letter!

SAMBA is good ;-)

---

### Post by 9000cse on 2011-06-30
Hi, I did not get a reply from you yesterday.  Have you given up on me? :(

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> Hi, I did not get a reply from you yesterday.  Have you given up on me? :(

I took "SAMBA is good" to mean that everything was working fine and you needed no more help.

---

### Post by 9000cse on 2011-06-30
> **redmk2 said:**
> I took "SAMBA is good" to mean that everything was working fine and you needed no more help.

Hi Red, No, I was saying SAMBA GOOD. as in 
> Uh huh...

I think we ought to limit this to Samba concerns. 

I was agreeing with you.

Anyway, I would not just let it go, even if I had sorted out. without saying something..like.  THANK YOU.  

And besides, you told me not to touch anything.

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> Hi Red, No, I was saying SAMBA GOOD. as in 


I was agreeing with you.

Anyway, I would not just let it go, even if I had sorted out. without saying something..like.  THANK YOU.  

And besides, you told me not to touch anything.

Refresh my memory: What doesn't work?  I believe you can see all the shares from all the windows machines but can't manipulate the contents.  Does this change if you use a different machine?

Do the windows machines have user passwords?  Do you want to allow everyone to see everything?

---

### Post by 9000cse on 2011-06-30
> **redmk2 said:**
> Refresh my memory: What doesn't work?  I believe you can see all the shares from all the windows machines but can't manipulate the contents.  Does this change if you use a different machine?
They are seen but cannot be accessed. Do not have permission. 

Do the windows machines have user passwords?  Do you want to allow everyone to see everything?[/quote]
YES.


> I can fix the shares any what you want and even make you a template for future shares. Don't go mucking about in the smb.conf file. I will sort the user/pass situation also.

We were going to stick with Classic.

---

### Post by redmk2 on 2011-06-30
> 
[Are] we were going to stick with classic?
Yes we will use classic shares.

There are 2 ways of allowing the users access to the files held on the Ubuntu machine in the Samba shares.  [LIST]
[*]Add them as users to Ubuntu and then give them a Samba password.
[*]Allow rw access for everyone
[/LIST]

Either way works.  I use the first method.  There are a few more steps bu it is much more secure.  The second way allows anyone on your network to browse to share (see it) and manipulate that data (I believe deleting it too).

If you want to use the more secure method, then you need to add the users (same user/pass combo) to the Ubuntu machine.  After that you need to issue this command for each user (same password) at from the Ubuntu terminal```
smbpasswd -a <user>
```

Substitute the user name for <user> of course.  :D

---

### Post by 9000cse on 2011-06-30
Hi, OK, using the code above, I have added the users.
How can I prove they are there?

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> Hi, OK, using the code above, I have added the users.
How can I prove they are there?

For Ubuntu you can do this from the terminal```
getent passwd
```
That will list all users on the system.  You can check for a specific user by name this way```
getent passwd|grep <user>
```If I do that on my system it looks like this  ```
getent passwd|grep red
```  The output looks like this```
red:x:1000:1000:Red MK2,,,:/home/red:/bin/bash
```

To see the Samba passwd data base you do this ```
sudo pdbedit -l
```

That will list all the Samba users by name and Ubuntu user number.

---

### Post by 9000cse on 2011-06-30
OK, I think something went wrong somewhere?
```

asjmm@asjmm-saviour:~$ getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:105:46:usbmux daemon,,,:/home/usbmux:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:119:RealtimeKit,,,:/proc:/bin/false
hplip:x:111:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:112:121::/home/saned:/bin/false
asjmm:x:1000:120:ASJMM,Here,my mobile number,My home number,:/home/asjmm:/bin/bash
Debian-exim:x:113:123::/var/spool/exim4:/bin/false

```
```

asjmm@asjmm-saviour:~$ getent passwd|grep james
```
```

asjmm@asjmm-saviour:~$ getent passwd|grep asjmm
asjmm:x:1000:120:ASJMM,Here,,my mobile number,My home number,:/home/asjmm:/bin/bash
```
```

asjmm@asjmm-saviour:~$ getent passwd|grep alice
```
```

asjmm@asjmm-saviour:~$ sudo pdbedit -l
[sudo] password for asjmm: 
Usage: [OPTION...]
  -L, --list                            list all users
  -v, --verbose                         be verbose
  -w, --smbpasswd-style                 give output in smbpasswd style
  -u, --user=USER           
```

That's all I get.

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> OK, I think something went wrong somewhere?
```

asjmm@asjmm-saviour:~$ getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:105:46:usbmux daemon,,,:/home/usbmux:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:119:RealtimeKit,,,:/proc:/bin/false
hplip:x:111:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:112:121::/home/saned:/bin/false
asjmm:x:1000:120:ASJMM,Here,my mobile number,My home number,:/home/asjmm:/bin/bash
Debian-exim:x:113:123::/var/spool/exim4:/bin/false

```
No james listed here (above)> 
```

asjmm@asjmm-saviour:~$ getent passwd|grep james
```
So this will return nothing.  It is correct.> 
```

asjmm@asjmm-saviour:~$ getent passwd|grep asjmm
asjmm:x:1000:120:ASJMM,Here,,my mobile number,My home number,:/home/asjmm:/bin/bash
```
```

asjmm@asjmm-saviour:~$ getent passwd|grep alice
```
Hmmmmm, this command only lists the user.  It doesn't add the user.  This user does not exist in the Ubuntu user database (passwd).  This command in effect does this: **list the database passwd|* only list the name I give.* ** The first part sends all the information to the second part and youonly see the result of the two parts.> 

```

asjmm@asjmm-saviour:~$ sudo pdbedit -l
[sudo] password for asjmm: 
Usage: [OPTION...]
[COLOR="Red"]  -L, --list   [/COLOR]                         list all users
  -v, --verbose                         be verbose
  -w, --smbpasswd-style                 give output in smbpasswd style
  -u, --user=USER           
```

That's all I get.

Be precise.  you need to use this -L not this-l (see read above).

Did you add the users via the GUI?  Are alice and james the users you are adding. Do you need to restart the entire system?

---

### Post by 9000cse on 2011-06-30
> **redmk2 said:**
> No james listed here (above)So this will return nothing.  It is correct.Hmmmmm, this command only lists the user.  It doesn't add the user.  This user does not exist in the Ubuntu user database (passwd).  This command in effect does this: **list the database passwd|* only list the name I give.* ** The first part sends all the information to the second part and youonly see the result of the two parts.
> 
Be precise.  you need to use this -L not this-l (see read above).
Thought so, I get.
```
asjmm@asjmm-saviour:~$ sudo pdbedit -L
[sudo] password for asjmm: 
Debian-exim:113:
asjmm@asjmm-saviour:~$ 

```
[quote]
Did you add the users via the GUI? 
NO.
>  Are alice and james the users you are adding.Yes > Do you need to restart the entire system?
Might be a good idea. Well restart now.

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> 
```
asjmm@asjmm-saviour:~$ sudo pdbedit -L
[sudo] password for asjmm: 
Debian-exim:113:
asjmm@asjmm-saviour:~$ 

```

I don't see you as a Samba user either here.

Who is Debian-exim?

I think we should concentrate on just adding the users to Ubuntu.  You can add a user (with defaults) like this and follow the prompts (use the same user/pass as in windows)```
sudo adduser <user>
```

---

### Post by 9000cse on 2011-06-30
> **redmk2 said:**
> I don't see you as a Samba user either here.

Who is Debian-exim?

No idea.
> 

I think we should concentrate on just adding the users to Ubuntu.  You can add a user (with defaults) like this and follow the prompts (use the same user/pass as in windows)```
sudo adduser <user>
```


OK, tht's easy.
```
asjmm@asjmm-saviour:~$ sudo adduser james
[sudo] password for asjmm: 
Adding user `james' ...
Adding new group `james' (1001) ...
Adding new user `james' (1001) with group `james' ...
Creating home directory `/home/james' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for james
Enter the new value, or press ENTER for the default
	Full Name []: James
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
asjmm@asjmm-saviour:~$ 

```

I'll do the rest later.

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> No idea.



OK, tht's easy.
```
asjmm@asjmm-saviour:~$ sudo adduser james
[sudo] password for asjmm: 
Adding user `james' ...
Adding new group `james' (1001) ...
Adding new user `james' (1001) with group `james' ...
Creating home directory `/home/james' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for james
Enter the new value, or press ENTER for the default
	Full Name []: James
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
asjmm@asjmm-saviour:~$ 

```

I'll do the rest later.

Just go back and use the command to list the Ubuntu users.  Then try the command to list the Samba users.  You should see all 3 users in both databases.

I have to pop out myself.  I will be back in 4 hours (you will be asleep).  Post what you have done so I can see it.

---

### Post by 9000cse on 2011-06-30
OK, have a good one.
UBUNTU
```

asjmm@asjmm-saviour:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:105:46:usbmux daemon,,,:/home/usbmux:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:119:RealtimeKit,,,:/proc:/bin/false
hplip:x:111:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:112:121::/home/saned:/bin/false
asjmm:x:1000:120:ASJMM,Here,07845112828,02380555894,:/home/asjmm:/bin/bash
Debian-exim:x:113:123::/var/spool/exim4:/bin/false
james:x:1001:1001:James,,,:/home/james:/bin/bash
antonia:x:1002:1002:Antonia,1,,:/home/antonia:/bin/bash
alice:x:1003:1003:Alice,2,,:/home/alice:/bin/bash
boss:x:1004:1004:Sharon,,,:/home/boss:/bin/bash
asjmm@asjmm-saviour:~$ 
```

SAMBA
```

asjmm@asjmm-saviour:~$ cat /etc/passwd | grep /home | cut -d: -f1
syslog
usbmux
saned
asjmm
james
antonia
alice
boss
asjmm@asjmm-saviour:~$ 


```

I think that's what your after.

Andy

---

### Post by redmk2 on 2011-06-30
> **9000cse said:**
> OK, have a good one.
UBUNTU
```

asjmm@asjmm-saviour:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
...
[COLOR="Purple"]syslog:x:101:103::/home/syslog:[/COLOR][COLOR="DarkGreen"]/bin/false[/COLOR]
...
asjmm:x:1000:120:ASJMM,Here,xxxxxx,xxxxxxx,:/home/asjmm:/bin/bash
[COLOR="Purple"]Debian-exim[/COLOR]:x:113:123::/var/spool/exim4:/bin/false
james:x:1001:1001:James,,,:/home/james:/bin/bash
antonia:x:1002:1002:Antonia,1,,:/home/antonia:/bin/bash
alice:x:1003:1003:Alice,2,,:/home/alice:/bin/bash
boss:x:1004:1004:Sharon,,,:/home/boss:/bin/bash
asjmm@asjmm-saviour:~$ 
```

This works for finding mortal users (real peoples accounts).  Unfortunately some of the /home entries are system users to allow processes to own their own files.  See the entry for [COLOR="Purple"]syslog[/COLOR] above.  It looks like the mail program you are using created the system user [COLOR="Purple"]Debian-exim[/COLOR].

I assume that the mortal users in your network are:
james
antonia
alice
boss
asjmm 

I assume that the strife is Sharon. ;-)
> 
SAMBA
```

asjmm@asjmm-saviour:~$ cat /etc/passwd | grep /home | cut -d: -f1
syslog
usbmux
saned
asjmm
james
antonia
alice
boss
asjmm@asjmm-saviour:~$ 

```

I think that's what your after.

Andy

The Ubuntu (mortal) users look good.  The use of awk to strip the user names from the return is good.  You could have used a conditional if to remove the users that had a /home but did not have a [COLOR="DarkGreen"]/bin/bash shell[/COLOR].  See if you can figure that out.  You are progressing.

The Samba data should be from the command **pdbedit -L**.  This will have the Samba users after you add them using ```
smbpasswd -a
```

Remember to use the same password that is use in the login/pass combo when prompted.  Then the user (on either Ubuntu or Windows) and the Samba user login/pass will be the same.  I use the same login/pass on all my machines (including the Wireless AP and router admin).

One last thing -- all caps is a WINDOWS thing.  Linux folks are lazy -- all lowercase, no spaces and names no longer than need be.  Most of my hostnames are 5 characters and the user names are 3 to 5 characters.  Its all style, but CAPS SHOUT OUT.  :-)

To summarize - We have the Ubuntu users, now we need those users to also be Samba users and for you to list them here.

---

### Post by 9000cse on 2011-07-01
All I get here is this.
```


asjmm@asjmm-saviour:~$ pdbedit -L
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/passdb.tdb!
User Search failed!
```
```

asjmm@asjmm-saviour:~$ smbpasswd -a
When run by root:
    smbpasswd [options] [username]
otherwise:
    smbpasswd [options]

options:
  -L                   local mode (must be first option)
  -h                   print this usage message
  -s                   use stdin for password prompt
  -c smb.conf file     Use the given path to the smb.conf file
  -D LEVEL             debug level
  -r MACHINE           remote machine
  -U USER              remote username
extra options when run by root or in local mode:
  -a                   add user
  -d                   disable user
  -e                   enable user
  -i                   interdomain trust account
  -m                   machine trust account
  -n                   set no password
  -W                   use stdin ldap admin password
  -w PASSWORD          ldap admin password
  -x                   delete user
  -R ORDER             name resolve order
asjmm@asjmm-saviour:~$ 

```
Something maybe has not started?

---

### Post by redmk2 on 2011-07-01
Sorry about that. I figured you would remember tho use sudo.

Pdbedit you always needs sudo to run.  So the correct incantation to see a listing of Samba user iss```
sudo pdbedit -l
```

To add a user you should also use sudo and you need to declare the user name.  So the correct incantation is ```
sudo smbpasswd -a <user>
```

Use the same user/pass that you used when adding them to Ubuntu

---

### Post by 9000cse on 2011-07-01
> **redmk2 said:**
> Sorry about that. I figured you would remember tho use sudo.

Pdbedit you always needs sudo to run.  So the correct incantation to see a listing of Samba user iss```
sudo pdbedit -l
```

To add a user you should also use sudo and you need to declare the user name.  So the correct incantation is ```
sudo smbpasswd -a <user>
```

Use the same user/pass that you used when adding them to Ubuntu


I did remember, but forgot to. Thanks.
Any, ```
asjmm@asjmm-saviour:~$ sudo pdbedit -L
Debian-exim:113:
asjmm@asjmm-saviour:~$ 

```
&
```

asjmm@asjmm-saviour:~$ sudo pdbedit -L
james:1001:James
alice:1003:Alice
Debian-exim:113:
antonia:1002:Antonia
boss:1004:Sharon
asjmm@asjmm-saviour:~$ 

```


Hows that?

---

### Post by redmk2 on 2011-07-01
> **9000cse said:**
> I did remember, but forgot to. 
...
```

asjmm@asjmm-saviour:~$ sudo pdbedit -L
james:1001:James
alice:1003:Alice
Debian-exim:113:
antonia:1002:Antonia
boss:1004:Sharon
asjmm@asjmm-saviour:~$ 

```
Hows that?

It appears that you have not put your name in the smbpasswd database.  Add your asjmm account.  That is your account; right?

I'm curious: Why did you add the Debian-exim account (a system account) to this Samba suer database?  What password did you use?

To remove the Debian-exim entry you came do this ```
sudo smbpasswd -x Debian-exim
```

Post the updated info```
sudo pdbedit -L
```

---

### Post by 9000cse on 2011-07-01
Yep saw that, ...Woops.

```


asjmm@asjmm-saviour:~$ sudo pdbedit -L
james:1001:James
alice:1003:Alice
antonia:1002:Antonia
boss:1004:Sharon
asjmm:1000:ASJMM,Here,my mobile,my home,
asjmm@asjmm-saviour:~$ 


```

I have to pop out to see my VET. get my X-Ray results.  Will be back in around 30mins.

Have not heard back form you since Friday, everything OK?

I seem to have been abandoned :-(

---

