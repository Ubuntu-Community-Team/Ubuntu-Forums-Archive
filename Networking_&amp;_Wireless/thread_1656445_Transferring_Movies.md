---
title: "Transferring Movies"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by kijuhy on 2010-12-30
Hello

I have installed Ubuntu 10.04 on a through a USB stick because of harddrive failure.
I am trying to stream/transfer movies to my laptop either through sharing in the network or through
UPnP. But currently, both do not work.

Network Sharing:
When I try to access my windows 7 PCs Shares, I am asked to give a username and password for the share, I have tried my Ubuntu Login, PC Login. Both do not work.

When I use Place> Connect to server> Windows Share and enter in my PC from there, the PC login works, but then it says Ubuntu failed to mount Drive.

I read that I could go to the network PC share and Right Click>Mount, but the mount option wasn't there.

UPnP:
I have tried to connect to the PC through UPnP media sharing.

DJmount- Didn't find the Media Server
Media Tomb- Didn't find the media Server
PS3 Media Server- Cannot find media server, but I can see its server from my PC and my Phone.
________________________________________________________________________________

Can anyone suggest on how I can watch my movies on my Laptop?
Could I possibly be using anything incorrectly?

Please help, I really have no Ideas. I do know that there is nothing wrong with my network as my Nokia Phone has no problems with UPnP on 2 windows 7 PCs and the PCs also see each other fine(homegroup and network). 

Thankyou
kijuhy

---

### Post by PatchesTheCaveman on 2010-12-30
To access uPnP shares in Ubuntu, you need to install djmount, which will make them appear just like any other file on your hard drive.  To do that, go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type this and press Enter:
```
gksudo software-properties-gtk
```
Enter your password when asked.  Then in the Software Sources box that appears, check the box that's labeled *Community-maintained Open Source software (universe)* if it isn't already checked and click Close.

Next, type this in and press Enter:
```
sudo apt-get install djmount
```
Enter your password when asked and press *y* and hit Enter when it asks if you're sure you want to install.

Next, you need to create a folder where all your uPnP files will show up.  For simplicity's sake, you create it right in your root directory.  Just type this next and press Enter:
```
sudo mkdir /upnp
```

Now, make it so you can access it without being superuser:
```
sudo chmod 777 /upnp
```

Then, all you have to do to make everything show up there is type ```
djmount /upnp
```

All the UPnP shares available on your network should magically appear in that folder.  To open a window in the file browser so you can go through everything, type:
```
nautilus /upnp
```

That's it!  You can open the files just as if they were on your computer.  You can also copy them to your hard drive, if you want.  (I don't think you can write to them, because uPnP doesn't allow that.)



As for why regular file sharing isn't working:  if you have Windows Live Essentials installed on your Windows 7 computer(s), it makes a small change to the Windows file sharing protocol that breaks Samba (the Linux software that creates and accesses Windows file shares).  While the Samba team has already fixed the problem, Canonical has yet to release an Update to Ubuntu with the fix.

To work around the problem, uninstall Windows Live Essentials.  Note that sometimes Microsoft installs this software via Windows Update, so you might not be aware that you have this on your system.

---

### Post by kijuhy on 2010-12-31
> **PatchesTheCaveman said:**
> To access uPnP shares in Ubuntu, you need to install djmount, which will make them appear just like any other file on your hard drive.  To do that, go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type this and press Enter:
```
gksudo software-properties-gtk
```Enter your password when asked.  Then in the Software Sources box that appears, check the box that's labeled *Community-maintained Open Source software (universe)* if it isn't already checked and click Close.

Next, type this in and press Enter:
```
sudo apt-get install djmount
```Enter your password when asked and press *y* and hit Enter when it asks if you're sure you want to install.

Next, you need to create a folder where all your uPnP files will show up.  For simplicity's sake, you create it right in your root directory.  Just type this next and press Enter:
```
sudo mkdir /upnp
```Then, all you have to do to make everything show up there is type ```
sudo djmount /upnp
```All the UPnP shares available on your network should magically appear in that folder.  To open a window in the file browser so you can go through everything, type:
```
nautilus /upnp
```That's it!  You can open the files just as if they were on your computer.  You can also copy them to your hard drive, if you want.  (I don't think you can write to them, because uPnP doesn't allow that.)



As for why regular file sharing isn't working:  if you have Windows Live Essentials installed on your Windows 7 computer(s), it makes a small change to the Windows file sharing protocol that breaks Samba (the Linux software that creates and accesses Windows file shares).  While the Samba team has already fixed the problem, Canonical has yet to release an Update to Ubuntu with the fix.

To work around the problem, uninstall Windows Live Essentials.  Note that sometimes Microsoft installs this software via Windows Update, so you might not be aware that you have this on your system.

Thankyou so much!

I am now able to access all my music via UPnP on my laptop, but when I try to find my videos, no files appear in the file browser, I have just checked and it all appears fine on other devices.
I am using windows media center 12 as my PCs media server software.:confused:

Thanks
kijuhy

---

### Post by PatchesTheCaveman on 2010-12-31
According the documentation there should be a folder in there for each computer and under that folder there should be folders for Music, Pictures, Videos, etc.  Does a Videos folder appear at all or is it just empty?

At any rate, there's one thing you can try.  Run these two commands:
```
fusermount -u /upnp
djmount -o playlists /upnp
```

Do your videos appear now?

---

### Post by kid1000002000 on 2010-12-31
@[kijuhy]("http://ubuntuforums.org/member.php?u=1215176"): thank you

---

### Post by kijuhy on 2010-12-31
> **PatchesTheCaveman said:**
> According the documentation there should be a folder in there for each computer and under that folder there should be folders for Music, Pictures, Videos, etc.  Does a Videos folder appear at all or is it just empty?

At any rate, there's one thing you can try.  Run these two commands:
```
sudo umount /upnp
sudo djmount -o playlists /upnp
```Do your videos appear now?

Nope, here is what I got after entering the commands.

"[B][I][I]   Mount options = playlists
 * Charset : successfully initialised charset='UTF-8'*[/B]"

It does take quite a while to load (half a minute), could that be related?

Thankyou 
kijuhy

---

### Post by PatchesTheCaveman on 2010-12-31
I was trying to set up Windows Media Player to share videos from my Windows box so I could try and see what might be going on, but it isn't cooperating.  While messing around I came across a different problem that might be related to yours.

Try running these commands:
```
sudo umount /upnp
sudo chmod 777 /upnp
djmount /upnp
```

Notice I did **not** put sudo in front of djmount this time.  See how it works then.

---

### Post by PatchesTheCaveman on 2010-12-31
I was able to access videos from WMP11 after performing the above fix by browsing to the Videos/Folders/Videos folder of my computer's folder in the upnp directory.

---

### Post by kijuhy on 2011-01-01
> **PatchesTheCaveman said:**
> I was able to access videos from WMP11 after performing the above fix by browsing to the Videos/Folders/Videos folder of my computer's folder in the upnp directory.

I tried your suggestion and also tried it with an Ethernet cable, but no difference.

---

### Post by PatchesTheCaveman on 2011-01-01
What about any of the other folders in Computer/Videos/Folders?

---

### Post by kijuhy on 2011-01-01
> **PatchesTheCaveman said:**
> What about any of the other folders in Computer/Videos/Folders?

Just checked that, yes they do!
But for some reason, RMVB files don't display. I checked this on other devices,
and they were showing. I am using real alternative to view the RMVB files on WMP12

---

### Post by PatchesTheCaveman on 2011-01-01
Do they not show up or can you just not play them?

If it's the latter, download VLC:
```
sudo apt-get install vlc
```

I'm not aware of anything it can't play.  I use it on Windows and Linux and it always works great.  (And I checked and it does support RMVB.)

---

### Post by PatchesTheCaveman on 2011-01-01
Here's a cool feature of djmount that might be useful for you:

You can make shortcuts to folders that are basically just search results.  First you have to figure out the name of the folder for your computer.  It's probably something like "MY-PC:  kijuhy".  You probably want to right-click and go to Properties on that folder and copy/paste it to get it exact for the next step.

Then right-click on your desktop or wherever and click Create Launcher.  In the "Command" box type something like this
```
gnome-open "/upnp/MY-PC: kijuhy/Videos/_search/family/_and/guy/"
```
That will create a link to a folder that just has all the videos on that computer with the words "family" and "guy".  (Remember to replace the *MY-PC: kijuhy* part with your real computer name.)

You can also do use /_or/ to do something like:
```
gnome-open "/upnp/MY-PC: kijuhy/Videos/_search/anime/_and/cartoon/"
```

One more thing: ordinarily you would have to run *djmount* after every reboot.  Run this command on the terminal once and it will run every time you log in.
```
echo djmount /upnp >> ~/.profile
```

---

### Post by kijuhy on 2011-01-01
> **PatchesTheCaveman said:**
> Do they not show up or can you just not play them?

If it's the latter, download VLC:
```
sudo apt-get install vlc
```

I'm not aware of anything it can't play.  I use it on Windows and Linux and it always works great.  (And I checked and it does support RMVB.)

They don't show up.:confused:

---

### Post by PatchesTheCaveman on 2011-01-01
It looks like *djmount* doesn't support that type of file then.  Unfortunately, there have been no changes to *djmount* since 2006 and there isn't much activity on their forum, so it's unlikely anyone's around to fix it anymore.

However, I'm going to take a quick look at the source code and see if it's doing something simple that I can fix.  I can't make you any promises though.  :-)

ETA:  it looks like I can just add a line to the source code to get it to pick up RMVB.  Unfortunately I don't have any files of that format to test it with so you'll have to be my guinea pig :evil:

If you have any other types of files it's not picking up, let me know so I can add them in too.

---

### Post by PatchesTheCaveman on 2011-01-01
Okay, I don't have the toolset to build an Ubuntu package right now (I'm away from home for the holidays and am stuck on dialup) so you're going to have to build it yourself.  Don't worry!  It's pretty easy.

First, unmount the upnp directory you have right now.  Open a terminal and run:
```
fusermount -u /upnp
```

Then, uninstall the version of djmount you currently have installed:
```
sudo apt-get purge djmount
```

Next, install everything you'll need to build my version:
```
sudo apt-get install build-essential libfuse-dev
```

Now, download the version of djmount I attached to this post, and extract it to somewhere easy to get to, like your home directory.

Then, change to the directory you installed it to:
```
cd ~/djmount-0.71patches1
```

Now run the configure script:
```
./configure
```

Next, compile it:
```
make
```

Finally, install it on your system:
```
sudo make install
```

Now you can remount your uPnP folder:
```
djmount /upnp
```

Hopefully you can now access the RMVB files.  Let me know how it works.

If everything goes well I'm going to see if anyone else needs some file types supported by it and submit a properly packaged version to be included in an Ubuntu update.

---

### Post by kijuhy on 2011-01-03
After installing djmount, I went into the RMVB playlist but there was still nothing there.
I checked if the other playlists still worked fine but there was nothing in the other playlists I checked.
When checking other videos, my PC went into hibernation and the file browser didn't respond for about about a minute, an error popped up saying "Transport endpoint is not connected."

I exited out to the main directory, and the upnp folder was gone, I thought it was deleted and created another /upnp in the terminal but it said it was already there. I tried to delete it using the rm command, but it said permission denied. I created another folder to mount to, and mounted it in the terminal, but even though it responds with the usual success message, the folder was empty.

:confused:

---

### Post by PatchesTheCaveman on 2011-01-03
Try rebooting and rerun djmount.

To unmount a djmount folder, run:
```
fusermount -u /upnp
```
It shouldn't be necessary to delete the folder.  

I will poke around in the code some more and see if there's anything else I can change that would fix it.

---

### Post by kijuhy on 2011-01-03
It comes up with "fusermount: entry for /upnp not found in /etc/mtab".
The same thing happened when I was unistalling the other DJmount.

---

### Post by PatchesTheCaveman on 2011-01-03
Reboot to remove any locks that might be on the folder.

Then force delete the old upnp folder:
```
sudo rm -rf /upnp
```

Now, recreate it and make it world-writable:
```
mkdir /upnp
chmod 777 /upnp
```

Now, hang on a second and install the new version of djmount I'm almost done with.  I found another place I could add RMVB support.  I'll upload it in a sec.

---

### Post by PatchesTheCaveman on 2011-01-03
Here you go.

Just extract it, *cd* to the new folder, and
```
./configure
make
sudo make install
```
to compile and install again.

Make sure you've got the right version going:
```
djmount --version
```

And then remount your folder:
```
djmount /upnp
```

Make sure you're **not** *sudo*ing *djmount*.  That caused me a lot of problems when I was experimenting.

Hopefully that'll make RMVBs show up cause I looked everywhere and couldn't find anything else.

---

### Post by kijuhy on 2011-01-03
Doesn't seem to have any effect, the only change I saw was that the icons of the media servers had turned from folders to folders with locks on them.

:sad:

---

### Post by PatchesTheCaveman on 2011-01-03
This is just a wild shot in the dark, but try renaming one of your .rmvb files to .rm.  Since it's still a RealMedia extension, they still should play fine in Real Alternative.  Check and make sure.

Then, see if that file shows up in the djmounted folder.  If so, make sure that will play in Linux.

If that works, you can rename a whole folder of .rmvb files to .rm from the Windows Command Prompt with this command:
```
ren *.rmvb *.rm
```

If that doesn't work, you'll either have to access that folder via standard Windows file sharing (I can help you get that working if its still broken) or convert your RMVB files to another format like AVI.

---

### Post by kijuhy on 2011-01-06
Sorry for the late reply, maybe I'll have to just temporarily uninstall windows live essentials to manually transfer the movies to the laptop's old harddrive and hope it doesn't fail again.

So do I have to just uninstall the windows live essentials and connect to the network share with Ubuntu?
Or do I need to replace the system file?

Thanks
kijuhy

---

### Post by PatchesTheCaveman on 2011-01-07
Actually, someone discovered a workaround on the Linux side that fixes that bug too:  [http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

That way you can play your movies off the Windows share without worrying about the laptop's drive.

---

### Post by kijuhy on 2011-01-07
When I opened the conf file, it was a read only file, is there a way to change that?

Thanks 
kijuhy

---

### Post by PatchesTheCaveman on 2011-01-07
You have to edit it as superuser.  The easiest way is to run the following command on a terminal or by pressing ALT+F2 to get the Run dialog:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by kijuhy on 2011-01-07
That worked very well, until other problems came up....

I can now access the windows share, but ubuntu cannot mount the folders.

---

### Post by PatchesTheCaveman on 2011-01-07
> I can now access the windows share, but ubuntu cannot mount the folders.

What do you mean you can access the Windows share?  At what point do you get that error message?

---

### Post by kijuhy on 2011-01-07
I can go into the network, and then see my workgroup, and then see my computer, and then see the folders inside, but I can't go into the folders.

---

### Post by PatchesTheCaveman on 2011-01-07
What happens when you run:
```
smbclient -L *<windows computer name>* -U *<valid username on windows machine>*
```

e.g. if your Windows computer is called ZOMBIE and your username on it is *kijuhy*:
```
smbclient -L slayer -U kijuhy
```

If you have guest sharing enabled or don't have a password on the Windows computer, use *guest* as the username and leave the password blank.

---

### Post by kijuhy on 2011-01-08
I get:

1.Error returning browse list: NT_STATUS_ACCESS_DENIED
2. My Windows 7 version
3. List of all computers on the network
4. A list of all the workgroups in the network and their masters.

---

### Post by PatchesTheCaveman on 2011-01-08
Copy/paste the result of these commands:
[code]cat /etc/samba/smb.conf
dpkg-query -l "samba*"[code]

---

### Post by kijuhy on 2011-01-09
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

client use spnego = no

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  samba                     2:3.4.7~dfsg-1ubuntu3.2   SMB/CIFS file, print, and login server for Unix
un  samba-client              <none>                    (no description available)
ii  samba-common              2:3.4.7~dfsg-1ubuntu3.2   common files used by both the Samba server and client
ii  samba-common-bin          2:3.4.7~dfsg-1ubuntu3.1   common files used by both the Samba server and client
un  samba4                    <none>                    (no description available)
un  samba4-clients            <none>                    (no description available)
un  samba4-common             <none>                    (no description available)

---

### Post by PatchesTheCaveman on 2011-01-09
Did you run:
```
sudo service smb restart
```

If not it has to be a password mismatch.  Make sure you're using a valid username and password on the Windows machine or you have public file sharing turned on in the Network and Sharing Center.

---

### Post by kijuhy on 2011-01-10
After adding to the samba file, I powered off the computer and then powered it back on.
But now that I try to restart the it, it says smb: unrecognized service.
I have turned password protected sharing off in the windows 7 computer so that it doesn't ask for the Username and Password as none of the Usernames work even thought they don't have passwords.

I have attached a picture to show where I put the fix into in case I did that wrong.

---

### Post by PatchesTheCaveman on 2011-01-10
Sorry I meant:
```
sudo service smbd restart
```
My apologies.

Your smb.conf file is fine.  I had you post it earlier by way of a terminal command.  ;-)

---

### Post by kijuhy on 2011-01-11
Still the same, could it be something else?
When testing after restarting samba, there was a message after trying to get into the windows workgroups, it still worked and let me into the list of workgroups, but I think it may be related to the problem.

---

### Post by PatchesTheCaveman on 2011-01-11
Let's give manual mounting a shot. Figure out the computer name and the name of the file share on the Windows machine. Then, open a terminal and run the following commands:
```
sudo mkdir /mnt/windows
sudo smbmount -o guest //*<computer name>*/*<share name*>/ /mnt/windows
```

Even if that doesn't work it should give us a more useful error.

---

### Post by kijuhy on 2011-01-12
My folder of RMVB files suddenly appeared in the network folder, and all my RMVB movies seem to play fine.:confused: But the original movies folder with the other RMVB files still doesn't open.:confused:I didn't change anything, so it might go away next time I try.

The terminal gave me this error:
Warning: mapping 'guest' to 'guest,sec=none'

Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found

---

