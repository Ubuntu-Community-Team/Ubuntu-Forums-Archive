---
title: "[SOLVED] How to config Myth 8.04 via Terminal"
date: 2008-12-15
forum: Mythbuntu
---

### Post by zf3636 on 2008-12-15
Hi I want to configure Mythfilldatabase via the Terminal I have used the su mythtv command and when I try to type my password Ii will not allow me to type anything I have even tried copy and paste by opening a 2nd Terminal window, what other option can i try I am the only admin user setup to use mythtv any help with this will be greatly appreciated thx.

---

### Post by volkswagner on 2008-12-15
When you installed the system, did you set up "yourself" as mythtv user?

If you did, you were not supposed to.  mythv user is created by the install script.

Hopefully you did create a different user for the admin.  If you did you can use "sudo" in front of the command you are trying to run.  This will give you root privileges for that command.  mythv is an underprivileged user. 

```
sudo mythfilldatabase
```

or 

```
sudo mythbuntu-control-centre
```

If you are doing this via ssh, the later will need a forwarded x session, like.....

```
ssh -X user@192.168.1.xxx
```

You may need to clarify, as I am not sure your exact issue.

---

### Post by zf3636 on 2008-12-16
Hi when i installed mythbuntu form the live cd i created just one admin user name and password to install mythbuntu on, I have recently created a mytharchivee temp directory on the home user which has more user rights I hope this helps, I want to config mythfilldatabase to grab XMLTV info for mythtv in the uk whats been happening evrry time i try to configue my XML file saves itself in the home folder and not in mythtv, which mythtv needs to use when mythfilldatabase runs.

---

### Post by uMuppet on 2008-12-16
> **zf3636 said:**
> Hi when i installed mythbuntu form the live cd i created just one admin user name and password to install mythbuntu on, I have recently created a mytharchivee temp directory on the home user which has more user rights I hope this helps, I want to config mythfilldatabase to grab XMLTV info for mythtv in the uk whats been happening evrry time i try to configue my XML file saves itself in the home folder and not in mythtv, which mythtv needs to use when mythfilldatabase runs.

You can keep it in the user home folder as long as your user has been added to the mythtv group which automatically happins when you install mythtv.  Just make sure that the temp mythfilldatabase folder has group write privileges. 

```
sudo chmod 775 -R /home/myuser/.mythtv/mythfilldatabase
```

This will enable mythtv read/write access to the mythfilldatabase folder and all its contents.

---

### Post by EasyRiderOnTheStorm on 2008-12-16
I know exactly where you're coming from. I myself do most everything logged is as my user (not mythtv), but as you mention, mythfilldatabase uses a grabber configuration file that he looks for in the mythtv user's home; so if you're logged in as anything else and try to run it, it doesn't find that file and complains/fails.

I've found two fairly easy ways around that, either should sort you out:

- find the file he's looking for (should have the name of your <video source>.xmltv) in /home/mythtv/.mythtv and copy it over to your user's /home/<username>/.mythtv folder - now mythfilldatbase will find it even if you're not logged in as mythtv

- **Even easier**, switch to root first ("su root"), which you can do with your admin password, **then** switch to mythtv ("su mythtv"), which now you being root you can do without needing a password at all. That's what I do... ;)

Hope that helps...

---

### Post by zf3636 on 2008-12-17
Hi under user and groups my username, under the home directory which has admin privileges and a second as root, do i need to create a mythtv user under the mythtv group. I have tried some of the options like sudo mythfilldatabase which does allow me to configure, I can get channel info when mythtv is running but i can'nt preview while watching live tv, only works when I select manage recordings/ Program finder options. I ran mythfilldatabase manually I get the following error failed xmltv returned error 512. I still can not type my password when requested any ideas will be greatly appreciated thx.

---

### Post by EasyRiderOnTheStorm on 2008-12-18
I'm sorry, I'm not sure I understand you. 

A user called mythtv belonging to mythtv group should have been created when you installed Mythbuntu. Since it was created by the installer, I have no idea what it's password is, but I never needed to log into that user except for mythfilldatabase, which I did as described in my previous post. The only other users on the system are the root and my default user, both of which were also created by Mythbuntu on install. I never had to create users or groups, or add any users to groups.

If I'm not mistaken, one of the causes for the 512 error is exactly a "missing" config file. Did you run mythfilldatabase as the user mythtv? If not, did you have a copy of the config file in the /home/<username>/.mythtv folder? I think mythfilldatabase should also tell you where it was looking for the file; if it does not, try to run it with "--verbose most". Make sure there's a copy of the config file (or a symlink to it) where it says it's looking for it. With permissions for all to read.

---

### Post by zf3636 on 2008-12-18
Hi I have installed mythtv as you have, I have a default user and a root, the trouble i am finding is that i can not config as the mythtv user? I ran mythfilldatabase manual as the default user but config file /home/sohail/.mythtv/PAL-TV .xmltv is empty, please delete and run me with --configure, when i type su root on the Terminal window it will not allow me to type a password and the same happens when i type su mythtv currently my PAL-TV.xml file is  saved in home not mythtv/.mythtv. Can you explain how to run mythfilldatabase as the user mythtv? so i can run mythfilldatabase  and config within mythtv thx for your help.

---

### Post by EasyRiderOnTheStorm on 2008-12-18
> **zf3636 said:**
> I ran mythfilldatabase manual as the default user but config file /home/sohail/.mythtv/PAL-TV .xmltv is empty, please delete and run me with --configure

I hope that **space** in "PAL-TV .xmltv" is not really there. If it is, it's probably messing with accessing that file properly unless Myth was unusually cautiously written. Make sure your "video source" configured in mythbackend setup does not indeed end with a space ("PAL-TV ").

Also, please check if the file exists, delete it if it's empty, find the proper one that is not empty, and copy it to that path (/home/sohail/.mythtv/PAL-TV.xmltv, if that's it).

> **zf3636 said:**
> when i type su root on the Terminal window it will not allow me to type a password and the same happens when i type su mythtv currently my PAL-TV.xml file is  saved in home not mythtv/.mythtv.

What exactly do you mean by "will not allow"? It should ask for a password, but be advised - you won't see **anything** as you type it. If you type the wrong one, it looks like this:

```
easyrider@mybox:~$ su root
Password:
su: Authentication failure
```

If you get it right, it looks something like this:

```
easyrider@mybox:~$ su root
Password:
root@mybox:/home/easyrider# su mythtv
$
```

Note how the prompt changes to show I'm no longer logged as "easyrider".

One more thing: when you're doing "su root", you need to use the actual root password, which is not the same thing as your user password. It might be identical to it, or it might not. If it's not, and you don't know it, you can't log in as root. So try this:

```
sudo su mythtv
```

...which should get you the same result in one step instead of two, with the added advantage that the password it asks is your **user** password now, not the root one. That one you certainly should know.

It works like this ("whoami" tells you what user you are logged in as, at any moment):

```
easyrider@mybox:~$ whoami
easyrider
easyrider@mybox:~$ sudo su mythtv
[sudo] password for easyrider:
$ whoami
mythtv
```

If you can get to where it says "mythtv", you should be golden.

---

### Post by zf3636 on 2008-12-19
Hi I have type the commands with the following result

easyrider@mybox:~$ sudo su mythtv
[sudo] password for easyrider:
$ whoami
sh:whoami: not found

also while i was in mythfrontend in the ,Setup,General option i have notice a user mythtv and a different password similar to this one 37M2PjK3 do i type this password instead of the default users password when i type the following command su mythtv.

---

### Post by EasyRiderOnTheStorm on 2008-12-20
I hope you didn't actually type **everything** that was there, letter by letter - that was a cut & paste sample of what it looks like when you do it. All you had to type was:

```
whoami
sudo su mythtv
whoami

```

...and of course, your user password as you were prompted for it.
Having said that, it would be strange for your system to not find the "whoami" command. It's bog standard, it should be there. Anyway, it's only to make sure you managed to log in as mythtv, it has no importance otherwise. If you get the "$"-and-nothing-else prompt after the "sudo su mythtv", you're pretty much there, you can try to launch "mythfilldatabase".

The password you've found in the "General settings" is the password used for mysql database access. It's not for use related to your system and users, it's needed if anybody wishes to open the database directly. As mythtv obviously needs to do that, it needs that password, so it's configurable under the settings. Warning: Do not try to change it, it'll mess up stuff if it's not changed everywhere correctly. 

Bottom line: you don't need it, don't worry about it. Oh, and it's not the best idea to post passwords and/or login names to forums either. Mine weren't real btw. It might not matter, but if anyone is sufficiently bored and malevolent, why help him break your box...

---

### Post by zf3636 on 2008-12-20
Hi NO!! I did not type whoami i knew that was an example i just typed the following  and when prompted the password,
birons@birons:~$ sudo su mythtv
[sudo] password for birons:
$ 

and the Mythfrontend password that was also a false one, I agree with you 100% about password protection.

I have managed to config mythfilldatabase to get channel info for uk working, and I used Mythbackend Channel Editor screen to config I did not number my channels nor did I put channel frequencies  in thx for all your help & advice.

---

