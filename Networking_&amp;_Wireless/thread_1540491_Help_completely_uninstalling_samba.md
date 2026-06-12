---
title: "Help completely uninstalling samba"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by gaines2166 on 2010-07-27
I would appreciate help in completely uninstalling samba, including all the configuration files.

I've tried uninstalling it through synaptic, but that apparently doesn't remove everything.

I installed 9.04 last fall on my computer (switching from Win XP).   I wanted to make sure that it would work for the 2-PC LAN I share with my wife, so I left XP on her machine and set up samba. 

It worked adequately until I switched her over to 9.04 a few months ago, and I tinkered with it and also tried to install nfs, but without any luck.

Recently I decided to try again, so I started with nfs (as recommended for Ubuntu-only networks and spent several days trying to get it going, with no luck.  The last few days I've been trying to get samba going, again with no luck.  

(I've spent hours and hours on sites offering help with nfs and samba,  googling them and searching this forum, trying different tweaks to smb.conf, etc.  I've made some progress -- and learned a lot about linux, but....)

So, I am convinced that if I can clean out everything samba (and maybe nfs?), and start over, I just might be able to get back to some productive work.

I've been learning a bit about using the terminal, but it would be very helpful to know the exact commands to use (I had to google "foo" today to understand what a site was trying to convey with a sample command.)

I appreciate any help!

---

### Post by capscrew on 2010-07-28
> **gaines2166 said:**
> I would appreciate help in completely uninstalling samba, including all the configuration files.

I've tried uninstalling it through synaptic, but that apparently doesn't remove everything.

What does it leave?> 

I installed 9.04 last fall on my computer (switching from Win XP).   I wanted to make sure that it would work for the 2-PC LAN I share with my wife, so I left XP on her machine and set up samba. 

It worked adequately until I switched her over to 9.04 a few months ago, and I tinkered with it and also tried to install nfs, but without any luck.

What *tinkering *did you do?> 

Recently I decided to try again, so I started with nfs (as recommended for Ubuntu-only networks and spent several days trying to get it going, with no luck.  The last few days I've been trying to get samba going, again with no luck.
What's the problem?>   

(I've spent hours and hours on sites offering help with nfs and samba,  googling them and searching this forum, trying different tweaks to smb.conf, etc.  I've made some progress -- and learned a lot about linux, but....)

So, I am convinced that if I can clean out everything samba (and maybe nfs?), and start over, I just might be able to get back to some productive work.

I've been learning a bit about using the terminal, but it would be very helpful to know the exact commands to use (I had to google "foo" today to understand what a site was trying to convey with a sample command.)

I appreciate any help!

To remove any package *** completely *** you do this from the terminal:```
sudo apt-get purge <<name of package>>
```

There are multiple packages for Samba, do you know what you have installed?

You can do this in Synaptic too.  It asks if you want to completely remove the package in the dialog box.

---

### Post by gaines2166 on 2010-07-28
Originally Posted by **gaines2166**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9646023#post9646023")                 
                 [I]I would appreciate help in completely uninstalling samba, including all the configuration files.

I've tried uninstalling it through synaptic, but that apparently doesn't remove everything.
[/I]
                                 
What does it leave?

*You can do this in Synaptic too.  It asks if you want to completely remove the package in the dialog box.*

After I previously tried "Mark for complete removal" in Synaptic, these files were still in /etc/samba: smbconf, smbusers, gdbcommands, smb.conf.old.gadmin-samba-0.2.7, smb.conf.ucf-dist, smb.conf.ucf-old, smbpasswd.  I don't know enough to check other significant file locations, but I did note samba user-specific files dating back to when I installed Ubuntu.

I just tried your suggested command (thanks!), but the files listed above are still apparently there.   I'll try a reboot and let you know if it seems to have completely cleared out the old files.

*What's the problem?*

I want to get rid of the old configuration files and any others that affect samba so that I can try a clean reinstall.

I just rebooted and the files are still in /etc/samba.

---

### Post by capscrew on 2010-07-28
> **gaines2166 said:**
> Originally Posted by **gaines2166**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9646023#post9646023")                 
                 [I]I would appreciate help in completely uninstalling samba, including all the configuration files.

I've tried uninstalling it through synaptic, but that apparently doesn't remove everything.
[/I]
                                 
What does it leave?

*You can do this in Synaptic too.  It asks if you want to completely remove the package in the dialog box.*

After I previously tried "Mark for complete removal" in Synaptic, these files were still in /etc/samba: smbconf, smbusers, gdbcommands, smb.conf.old.gadmin-samba-0.2.7, smb.conf.ucf-dist, smb.conf.ucf-old, smbpasswd.  I don't know enough to check other significant file locations, but I did note samba user-specific files dating back to when I installed Ubuntu.

I just tried your suggested command (thanks!), but the files listed above are still apparently there.   I'll try a reboot and let you know if it seems to have completely cleared out the old files.

*What's the problem?*

I want to get rid of the old configuration files and any others that affect samba so that I can try a clean reinstall.

I just rebooted and the files are still in /etc/samba.

You should be able to safely remove all the files from /etc/samba.  The only other place there are Samba config files is at: /var/lib/samba.  These are generated when you use Nautilus (GUI) to configure Samba.  They are dynamic and can be left alone.

In my opinion this is a problem :gadmin-samba-0.2.7
You don't need this to be successful with Samba.

---

### Post by gaines2166 on 2010-07-28
> **capscrew said:**
> You should be able to safely remove all the files from /etc/samba.

Is there a command I can use to safely delete the /etc/samba directory (or just the files if the directory should stay)?  I tried deleting the files using the Nautilus File Manager and opening as administrator, but it didn't work.

Thanks for the help!

---

### Post by capscrew on 2010-07-28
> **gaines2166 said:**
> Is there a command I can use to safely delete the /etc/samba directory (or just the files if the directory should stay)?  I tried deleting the files using the Nautilus File Manager and opening as administrator, but it didn't work.

Thanks for the help!

Safely delete -- that's really up to the operator.  :-)

Here is what I would do (from the terminal):
```

# Move to the directory
cd /etc/samba

# Confirm that you are in the right place
pwd

# Confirm the files are there
ls -al

# Interactively remove the files
sudo rm -i *

```

---

