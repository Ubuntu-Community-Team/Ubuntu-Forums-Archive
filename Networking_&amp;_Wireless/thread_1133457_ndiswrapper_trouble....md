---
title: "ndiswrapper trouble..."
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Woooooot on 2009-04-23
I wonder if anyone can help me. At the moment, in order to connect to my router I have to wait for the system to load, load a terminal and type:

sudo modprobe ndiswrapper

I enter my password, and close the terminal. Something else pops up asking for a password for the keyring. I enter that password and in a few seconds I'm connected. 

I want to get rid of the need to enter a keyring password, and also initiate ndiswrapper automatically at start-up using a script. I know it's possible but I'm a noob and I don't know how to do it. :confused:

Thanks in advance.

---

### Post by cariboo on 2009-04-23
The command you are looking for is:

```
sudo ndiswrapper -m
```

from the ndiswrapper man page
> -m
    writes an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used. 

The second password you have to enter is to connect to your router because of your encrcyption settings.

---

### Post by Woooooot on 2009-04-23
Cariboo,

Thank you for the swift reply. I entered the command you provided into a terminal, and was presented with the following output:

module configuration already contains alias directive

I restarted my computer, and nothing has changed. I still have to go through the same procedure detailed in my first post.

Other ideas anyone?

---

### Post by Woooooot on 2009-04-29
After a bit of digging, I managed to sort it out. When I originally entered:
[FONT=monospace]
[/FONT]```
sudo ndiswrapper -m
```[FONT=monospace]

I got the following output[FONT=Verdana]:

[/FONT][/FONT]> module configuration already contains alias directive[FONT=monospace]

However, when I brought up the config file like this:

[/FONT]```
gksudo gedit /etc/modules
```[FONT=monospace]

I found there wasn't any entry for ndiswrapper, so I changed it to look like this:

[/FONT]> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper[FONT=monospace]

I then changed my keyring password to match my login password, and presto! Apparently, my login password is fed to the keyring manager via a command in this file: /etc/pam.d/gdm

I loaded the file like so:

[/FONT]```
gksudo gedit /etc/pam.d/gdm
```[FONT=monospace]

And here is the contents:

[/FONT]> #%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-passwordI think it is the last two lines that are doing the job here, but I really don't know coz I'm a noob :)

FYI: My original OS version was 7.10, which I upgraded to 8.04 and finally 8.10. I installed ndiswrapper manually on 7.10 and have always connected as described in my first post, but got sick of it.

Now I'm: :guitar: 

I hope this helps anyone who is having the same problem.

---

