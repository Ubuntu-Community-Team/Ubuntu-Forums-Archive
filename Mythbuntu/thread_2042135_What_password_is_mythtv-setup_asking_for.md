---
title: "What password is mythtv-setup asking for?"
date: 2012-08-14
forum: Mythbuntu
---

### Post by philled on 2012-08-14
I am a long-time Mythtv user, but new to Mythbuntu. I've set up a mythbackend and whenever I try to run mythtv-setup it prompts me for a password in order to shutdown mythbackend - see [http://i48.tinypic.com/25pit0p.jpg](http://i48.tinypic.com/25pit0p.jpg). 

I assumed that this was the password of the user I'm logged in as, but it never accepts this password. The password prompt doesn't actually say which user it's requesting the password for. Can someone please advise which user it needs the password for and what the default password is.

---

### Post by nickrout on 2012-08-14
It is the password for the current user, and that user should be the one you set up when you installed mythbuntu. This user will have the appropriate permissions via sudo (see specifically /etc/sudoers).

---

### Post by philled on 2012-08-14
> **nickrout said:**
> It is the password for the current user, and that user should be the one you set up when you installed mythbuntu.
I am certain I am entering the correct password for the current user but it just keeps re-asking me for the password over and over until I click the cancel button. 

> **nickrout said:**
> This user will have the appropriate permissions via sudo (see  specifically /etc/sudoers).
There is nothing in /etc/sudoers specifically about MythTV - should there be? It contains this line which makes me think nothing MythTV specific is required:

[FONT=Courier New]# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL[/FONT]

---

### Post by nickrout on 2012-08-14
> **philled said:**
> I am certain I am entering the correct password for the current user but it just keeps re-asking me for the password over and over until I click the cancel button. 


There is nothing in /etc/sudoers specifically about MythTV - should there be? It contains this line which makes me think nothing MythTV specific is required:

[FONT=Courier New]# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL[/FONT]

It should contain the line

```
%admin ALL=(ALL) ALL
```

and your user should be in the admin group. check with the id command.

---

### Post by philled on 2012-08-14
Thanks Nick. I'll check that out. BTW, one thing that occurred to me - should I be running mythtv-setup as a sudo command or not? I.e. as user "phill" should I be running:

[FONT=Courier New]$ mythtv-setup[/FONT]

or

[FONT=Courier New]$ sudo mythtv-setup[/FONT]

---

### Post by philled on 2012-08-14
> **nickrout said:**
> It should contain the line

```
%admin ALL=(ALL) ALL
```and your user should be in the admin group. check with the id command.

I don't have an admin group. I have one called adm - is that the same, or has something gone amiss in my setup?

---

### Post by tgm4883 on 2012-08-14
```
%sudo ALL=(ALL:ALL) ALL
```

The above is correct. You don't need to run it with sudo, as it is elevating to that status when it's asking for the password. The user you are logged in as will need to be able to be a priviledged user, which the first user is.

---

### Post by nickrout on 2012-08-14
> **philled said:**
> I don't have an admin group. I have one called adm - is that the same, or has something gone amiss in my setup?

are you in the sudo group, again check with the id command.

---

### Post by philled on 2012-08-14
> **nickrout said:**
> are you in the sudo group, again check with the id command.
The output of id is as below (please ignore the spaces in some of the group names - that's something odd happening with the format of the post):

[FONT=Courier New]uid=1000(phill) gid=1000(phill) groups=1000(phill),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare),122(mythtv)[/FONT]

When I run mythtv-setup from the command line, should I run is as "mythtv-setup" or "sudo mythtv-setup"?

---

### Post by nickrout on 2012-08-14
without sudo

sudo is built into the script mythtv-setup.

---

### Post by philled on 2012-08-15
> **nickrout said:**
> without sudo
sudo is built into the script mythtv-setup.
Just wanted to say thanks to the people who helped me with this, especially Nick who I know is also active on the MythTV Users mailing list. It's working great now so thanks for your help.

---

### Post by nickrout on 2012-08-15
> **philled said:**
> Just wanted to say thanks to the people who helped me with this, especially Nick who I know is also active on the MythTV Users mailing list. It's working great now so thanks for your help.no problems, glad to help.

---

