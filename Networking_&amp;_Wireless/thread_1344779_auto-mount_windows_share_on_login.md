---
title: "auto-mount windows share on login?"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by mattman85 on 2009-12-03
I'm a tech at a PA school district.  I'm trying to find a way to be able to either auto-mount a network share when logging into an ubuntu workstation on a windows network, or create a script (and place it on every user's ubuntu desktop) that would ask for the users name and password, then mount the share.

We are a mostly Windows network, with a little Mac OS X sprinkled around the one school.  However, some of our machines don't like to run smoothly with XP anymore, and I suggested putting Ubuntu on, since I've been using Ubuntu for a few years now.  I was able to use authtool (and other LDAP utils) to connect the Ubuntu laptop to our domain, and I can log in using my network credentials.

What I need to do now is find a way that our network shares are available when users log into the laptop..

My first thought was auto-mounting the network share.  However, the issue with that is using the users password.  Is there a way to pull the password during login?

My second thought was creating a script that can be placed on the desktop and then ran, which would prompt for a username and password, and then mount the share.  The issue that I think would be present with this thought is that I have to find a way to place it on EVERY desktop.  Something like this:

```
cp *script* /$HOME/Desktop
```

could work for placing the script on the current user's desktop, *if* it's done at login.  However, where would I put something like that?  Or is there a better way to do it?

I wouldn't normally mess around with this kind of thing, but since these laptops are going to be for teachers, they need to have access to their network files..  I'd appreciate any help anyone can offer.  Thanks!

---

### Post by mikewhatever on 2009-12-03
Check out this wiki, I think it's a shot in the right direction.
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by mattman85 on 2009-12-03
I saw that, but I have an issue with that, with regards to the usernames.

When the user logs in, in order to authenticate properly, they have to login like so:  [FONT="Fixedsys"]DOMAIN\user[/FONT] or [FONT="Fixedsys"]user@DOMAIN[/FONT], either of which gives them the username [FONT="Fixedsys"]DOMAIN\user[/FONT].  The share, however, is just [FONT="Fixedsys"]SERVERNAME\user$[/FONT], not [FONT="Fixedsys"]SERVERNAME\DOMAIN\user$[/FONT].  Is there a way to pull [FONT="Fixedsys"]user[/FONT] from [FONT="Fixedsys"]DOMAIN\user[/FONT]?  If I can pull it out, I can create an environment variable so that the system uses that variable whenever I only need the user's name, not the username that Ubuntu sees..

I can't seem to find a good way to be able to strip out the '[FONT="Fixedsys"]DOMAIN\[/FONT]' from an environment variable.  I know that there are ways, if I wanted to code in C/++.  If I did write code to just drop '[FONT="Fixedsys"]DOMAIN\[/FONT]', where would I want to put that so that it runs on login?  What language would I want to use to write the code in?  I would think that this would be the appropriate way to go about it, using DOMAIN as the example domain name:
```
get username env var, put into char array called winuser[]
loop where i=0,j=7, where winuser[0] is D of DOMAIN\ and winuser[7] is start of windows user name
set winuser[0]=winuser[7]
increment i, increment j
end loop when j is equal to NULL
set WINUSR env var to be winuser[]

```

does this make sense to anyone other than me?

---

### Post by mattman85 on 2009-12-04
OK, I'm scrapping my auto mount thoughts, as the one other tech and I debated how we want the ubuntu laptops to work.  We are going to have it auto-login and then they will have an icon (a script, or such) on the desktop which asks for username and password, and then mounts the network drive.  Does anyone have a suggestion for which programming language should be used to make the script?

---

### Post by mattman85 on 2009-12-08
Ok, so I wrote a bash script that is supposed to mount a network drive for a user.  After the user is prompted for domain username and password, it should send a line to /etc/fstab with the information to allow the nonroot user to mount the share:
```
sudo echo "\\\\SERVER\\$DOMAINUSER\$ /media/share smb rw,user,noauto 0 0" >> /etc/fstab
```

I know that \\\\ is supposed to mean \\ in the code, but is the syntax for the line correct?  Will the line show up in /etc/fstab as \\\\SERVER\\$DOMAINUSER\$ or what I want it to be (\\SERVER\$DOMAINUSER$)?

Also, even with sudo, it doesn't prompt for the password.  instead, it just says "/etc/fstab: Permission denied"

the next line of the code is:
```
mount -t cifs -o username=DOMAIN\\$DOMAINUSER,password=$DOMAINPWD,setuid=root \\\\SERVER\\$DOMAINUSER\$ /media/share
```

that *should* allow the share to be mounted, provided that the /etc/fstab line is properly inserted, as the user will be able to use mount.  I even went so far as to do a sudo visudo, create an admin samba group and give the group the rights to mount and unmount samba/CIFS shares.  however, it doesn't work.

Am I going about this wrong?  Anyone have any suggestions?  I've been all over the web, pulling at a lot of ideas, and nothing is working the way it should work.

---

### Post by Iowan on 2009-12-08
Dunno if [this]("http://ubuntuforums.org/showthread.php?t=288534") thread is TMI (too much information), or if you may be past this point.

---

### Post by mattman85 on 2009-12-09
thanks.  that has a lot of the same info I've already gotten in my searching, but I was able to add a little bit from that site.  It works great, IF I'm only mounting 1 share like \\SERVER\MYSHARE$.  but I'm trying to have the user enter their domain credentials, and then have it mount that share.  so if you log into my laptop, you would mount your share, and if I log in, I want to mount my share.  I can't get the line in my code to insert into /etc/fstab :

```
sudo echo "\\\\SERVER\\" $DOMAINUSER "\$ /media/s\ drive smb rw,user,noauto 0 0" >> /etc/fstab
mount -t cifs \\\\SERVER\\$DOMAINUSER\$ -o username=DOMAIN\\$DOMAINUSER,password=$DOMAINPWD,setuids=root,iocharset=utf8,file_mode=0777,dir_mode=0777
```

which (if I'm right) put the line:
```
\\SERVER\DOMAINUSER$ /media/s\ drive smb rw,user,noauto 0 0
```
at the end of /etc/fstab, and then it tries to mount the share.

first, I get the error: "/etc/fstab permission denied", then I get the error that I can't use mount because i'm not root..  I am trying to make it so that I don't have to give teachers the auto-login account password, but I can't figure out how to get the info into /etc/fstab, since I'm using a custom environment variable, $DOMAINUSER, which is set in the script to access any of about 1000 shares, rather than one share.. 

It's pt

---

