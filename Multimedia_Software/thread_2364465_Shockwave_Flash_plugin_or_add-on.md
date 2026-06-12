---
title: "Shockwave Flash plugin or add-on"
date: 2017-06-23
forum: Multimedia Software
---

### Post by christon74 on 2017-06-23
Good evening fellow Ubunters
How do you update Adobe Flash player?  On the add on page I can read: "Shockwave Flash is known to be vulnerable and should be updated". OK. Now I have tried updating it but here is the message I get: "Enabling channel 'xenial-partner' failed. I am afraid it is once again a losing battle. Unless any of you has the solution.....

Oh, and just one other very, very irritating thing: My password hardly ever is recognized, even though I have ticked the 'remember' box. 

Thank you in advance for all help.

---

### Post by oldos2er on 2017-06-23
```
sudo apt-get upgrade && sudo apt-get dist-upgrade
``` should update your system including flashplugin.

---

### Post by Dennis N on 2017-06-23
Recommended way is to enable the Canonical Partners repository in Software and Updates dialog, Other Software tab. Refresh your software lists. Then install adobe-flashplugin package. It will provide the latest version of flash.

---

### Post by christon74 on 2017-06-23
Thanks to both of you:), Oldos and Dennis. Oldos, I think I need do a reboot:
```
christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# sudo apt-get upgrade && sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-92 linux-headers-3.13.0-92-generic
  linux-image-3.13.0-92-generic linux-image-extra-3.13.0-92-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-92 linux-headers-3.13.0-92-generic
  linux-image-3.13.0-92-generic linux-image-extra-3.13.0-92-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@hp1:/home/christophe# 
```
Dennis, it seems I cannot enable Canonical Partners. I just cannot tick the box. I have cliked on it up to twelve times.  (Software and updates)

---

### Post by deadflowr on 2017-06-23
> Dennis, it seems I cannot enable Canonical Partners. I just cannot tick the box. I have cliked on it up to twelve times. (Software and updates)
Try the manual method then
```
sudo nano /etc/apt/sources.list
```
change the line
```
# deb http://archive.canonical.com/ubuntu trusty partner

```
to
```
 deb http://archive.canonical.com/ubuntu trusty partner

```
(simply remove the # at the front of the line.
Then press ctrl + X to save and exit.
then re-run the apt-get update command.
then make sure adobe-flashplugin is installed and run an upgrade.

Note, there is no reason to run sudo with a command if you are already running as root (you switched to root during the sudo su)

> Oh, and just one other very, very irritating thing: My password hardly ever is recognized, even though I have ticked the 'remember' box. 

What remember box?

---

### Post by christon74 on 2017-06-23
Hi there deadflowr. Well, yes, I have had trouble logging in, it is not the first time, and yes, there is a line which says 'remember me, or remember my password.
Now here is what the GNU nano screen says:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-proposed restricted main multivers$

---

### Post by deadflowr on 2017-06-23
Your sources.list file is all messed up if you only have proposed.
I recommend generating a full sources.list.
Use can do so with repogen here:
[https://repogen.simplylinux.ch/]("https://repogen.simplylinux.ch/")
it'll also allow you to add the enabled canonical Partners repos
Enabled all the top four Main Universe Multiverse and Restricted
Also enable Security and Updates.
Everything else is optional to you and your tastes and needs.

> Hi there deadflowr. Well, yes, I have had trouble logging in, it is not the first time, and yes, there is a line which says 'remember me, or remember my password.
Logging into Ubuntu or Ubuntu Software or something else?

---

### Post by christon74 on 2017-06-24
Hello again Deadflowr, thanks for that. Going to try it. 
I mean logging to the ubuntu forum.

---

### Post by vasa1 on 2017-06-24
> **christon74 said:**
> Hello again Deadflowr, thanks for that. Going to try it. 
I mean logging to the ubuntu forum.
Questions about the forum, *per se*, should be asked in [Forum Feedback & Help]("https://ubuntuforums.org/forumdisplay.php?f=48").

---

### Post by christon74 on 2017-06-24
Hello again Deadflowr. I have just tried repogen and I get this message:
The program 'curl' is currently not installed. You can install it by typing:
apt install curl
root@hp1:/home/christophe# apt install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package curl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by howefield on 2017-06-24
You cannot install curl until you set up and update your repository information so ignore the method on the repogen website that uses curl.

Open your sources.list file with..

```
sudo nano /etc/apt/sources.list
```

and copy the sources generated by the repogen website into it, close out and save.

then do a 

```
sudo apt update
```

---

