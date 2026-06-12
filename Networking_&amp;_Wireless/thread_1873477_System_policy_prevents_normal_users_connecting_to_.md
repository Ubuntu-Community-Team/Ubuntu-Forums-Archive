---
title: "System policy prevents normal users connecting to WIFI"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by natrixgli on 2011-11-01
Hi,

In Ubuntu 11.10, I've created a standard (non admin) user account. That user is unable to connect to a wireless network via wireless manager without an administrator authenticating.

Seems like it's trying to add the connection for all users. 

Anyone know a way to fix this? I can't make every user an administrator.

---

### Post by barbara_08 on 2011-11-16
Hello !  
 

 I have exactly the same problem.  
 

 I made a clean install of ubuntu 11.10 on an IBM ThinkPad T40p laptop.  
 I cannot give the user administrators rights, but I want the user to be able to create a new wireless connection.
 

 As far as I know, it worked without doing anything special on previous Ubuntu versions (I have to admit that last version I used before was 10.10, not 11.04).  
 

 But now, each time the user wants to create a new wireless connection, NetworkManager prompts him for the administrator's password.
 

 And, if the user sets a new wireless connection (using admin password), it indeed is accessible to all other users on that machine, not only to the one who initiated that connection.  
 

 I found something about advanced managing users acounts here : 

[http://doc.ubuntu-fr.org/users-admin](http://doc.ubuntu-fr.org/users-admin)  (sorry, it's in French).  
 So I installed ***gnome-system-tools*** and could indeed access advanced configuration for the users rights (**via GUI "Users and Groups"** - this a word to word translation from french, I don't know if this GUI has the same name in english)  
 I set my user the apropriate rights and tested after reboot : the administrator's password was still asked …   
 I then used this tool to create a brand new « test » user with the apropriate rights and tested again after reboot : the administrator's password was still expected by NetworkManager…   
 

 I finally tried to add the users in the sudoers file for NetworkManager only, but the administrator's password was still asked.  
 I am not sure about the syntax I used in the sudoers file :  
 *username ALL=(root) NOPASSWD:/usr/sbin/NetworkManager*
 

Has anyone a tip to help solve this problem ?
   

Thank you very much !

---

### Post by praseodym on 2011-11-16
Hi,

checkbox "available to all users" and "connect automatically" as "root"-user in the network-manager applet.

---

### Post by barbara_08 on 2011-11-17
Hello ! 

Thank you for your help. 

Those boxes are checked (now I see how I can make a wireless connection available to all users or not !), but unfortunately, this does not solve my problem. 

I set up two laptops with Ubuntu 11.10 for my colleagues so that they can work from other places than the office (home, hotels, …). So I need them to be able to create a new wireless connection for their own sessions (or for all users, that's not the problem) without having to enter the "root"-user password. 

Is there any way to make this possible or are they bound to use a wired connection (which doesn't ask for the "root"-user password) ?

---

### Post by praseodym on 2011-11-17
Setting up connections needs user rights. In 11.10 IMHO the tool "users-admin" is not used anymore. Install it and checkbox all USER-rights for your colleagues (except "administrative") and login again

---

### Post by scofflan on 2011-11-17
[praseodym]("http://ubuntuforums.org/member.php?u=1411497") Your not listening  [barbara_08]("http://ubuntuforums.org/member.php?u=1495277") has already stated that he has installed ***gnome-system-tools ***which contains the****user-admin application and tried adding all permissions except admin and this has not worked. 

I am in the same situation. our employees work off Ubuntu laptops and need to be able to connect to wireless networks without having the admin password.

To clarify these are the steps I have taken

Clean install of 11.10 on a Dell Laptop
install gnome-system-tools
open user-admin via the "users and groups" gui 
create a <new user> 
modify <new users> permissions by check marking everything except administrate system
login as <new user>
attempt to connect to a wireless access point 

This brings up a warning "system policy prevents modification of network settings for all users" 


What we need is a method to allow the user to modify the network settings just for themselves and not other users. How can this be done?

---

### Post by barbara_08 on 2011-11-18
Yes exactly : it looks like Ubuntu 11.10 doesn't care what boxes are checked, the only one that matters to the Ocelot is the "Admin" box. It won't give the users the right to create a new wireless connexion. 

Never had that problem with previous Ubuntu versions. Is that a bug or a regression ? :(

I had the chance to get some help, and here is the way we "temporarily solved" the problem. It's not perfect, but … 

First, give the concerned user(s) sudo rights only for the commands concerning the network. Then create a "managewireless.desktop" file containing the "sudo nm-connection-editor" command and drag and drop this new launcher on the Dock. 

The user can use this launcher to set a new connection, but he needs to know every single parameters of the wireless connection. This is quite acceptable if it is his home wireless network, but it could be harder on places such as hotels, or clients offices … 

Here is the content of the files : [INDENT] root@ubuntu:/etc/sudoers.d# cat netmaster   # Self made...
 Cmnd_Alias     NETMASTER = /usr/bin/nm-applet, /usr/bin/nmcli, \
         /usr/bin/nm-connection-editor, /usr/bin/nm-online, \
         /usr/bin/nm-tool, /usr/sbin/NetworkManager

 username ALL = NOPASSWD: NETMASTER

[/INDENT][INDENT]username@ubuntu:~$ cat GestionnaireDeConnexions.desktop
[Desktop Entry]
 Version=1.0
 Type=Application
 Terminal=false
 Category=GNOME;GTK;
 Exec=sudo nm-connection-editor
 Name=Gestionnaire_de_Connexions
 Comment=Gestion des connexions reseau
 Icon=/usr/share/pixmaps/gnome-nettool.xpm

[/INDENT]I hope this will help and if someone has a better solution, I will be very glad to read it ! 


P.S: @ Scofflan : I'm a girl ! ;) Thank you for your post, I had the feeling I was almost the only one to have that problem …

---

### Post by scofflan on 2011-11-18
This work around can also be accomplished by opening "Edit Connections" from nm-applet.
The user can create a new network if they know all of the connection settings for an access point and save it if they uncheck "Available to all users" 

This is still not a usable work around if your users are not great with computers. 

The problem appears to be that the "Available to all users" is checked by default.
If this could be changed to be unchecked by default the user would not need administrative privileges as they would not be changing other users settings.

[barbara_08]("http://ubuntuforums.org/member.php?u=1495277") thanks for the feedback and sorry for assuming you were a guy.

---

### Post by scofflan on 2011-11-19
This is a bug that is being tracked upstream in the Debian Bugs under [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136)

The preferred solution to this bug would be to not set "Available to all users" as the default in network-manager.

As a work around I have modified the PK with the following (this not the ideal solution as it could be a security risk)

sudo mkdir /etc/polkit-1/localauthority/55-networkmananger.d

Create this file 
/etc/polkit-1/localauthority/55-networkmananger.d/10.org.freedesktop.networkmanger.pkla

[Normal User Permissions]
           Identity=unix-group:adm
           Action=org.freedesktop.NetworkManager.settings.modify.system
           ResultAny=no
           ResultInactive=no
           ResultActive=yes


Set the permissions of the user to allow everything except administrative rights. (this will add the user to the adm group). If you don't want to use this group make sure your pkla reflects this under Identity=unix-group: 

Now your users in the adm group will be able to add new wireless networks with out authenticating against the administrative password. The new connection will be available to all users unless you edit the newly added connections in network-manager.

---

### Post by barbara_08 on 2011-11-21
Scofflan, thank you again for your help. 

Yes, you're right, I didn't realise that unchecking the "Available for all users" box in nm-applet would let the user set a new connection without giving the admin password … :oops:

But as you pointed out, using this applet is not the best for users who are not great with computers. 

Modifying the policy for the nm is a better idea as i gives them the ability to just select any detected wireless network. 

Here is what I did :
Edit this file : */usr/share/polkit-1/actions/*[I]org.freedesktop.NetworkManager.policy
      [/I]
look for that section : [INDENT]<action id="**org.freedesktop.NetworkManager.settings.modify.system**">
     <description>Modify network connections for all users</description>
     <description xml:lang="de">[FONT=Tahoma]...[/FONT]</description>
...
<message>System policy prevents modification of network settings for all users</message>     <message xml:lang="de">...</message>
...
    <defaults>
       <allow_inactive>no</allow_inactive>
       [B]<allow_active>auth_admin_keep</allow_active> => set to "Yes"
[/B]
     </defaults>
   </action>


[/INDENT]And set "yes" instead of "auth_admin_keep" under "allow_active"


I tried this on another laptop with no "gnome-system-tools" ("users-admin" tool) installed, and it worked perfectly.  :)

---

### Post by scofflan on 2011-11-22
Excellent that is even better. I think this is something that can be lived with until the default is changed from "Available to all users"

---

### Post by tommyarmour on 2011-12-14
> **barbara_08 said:**
> Scofflan, thank you again for your help. 

Yes, you're right, I didn't realise that unchecking the "Available for all users" box in nm-applet would let the user set a new connection without giving the admin password … :oops:

But as you pointed out, using this applet is not the best for users who are not great with computers. 

Modifying the policy for the nm is a better idea as i gives them the ability to just select any detected wireless network. 

Here is what I did :
Edit this file : */usr/share/polkit-1/actions/*[I]org.freedesktop.NetworkManager.policy
      [/I]
look for that section : [INDENT]<action id="**org.freedesktop.NetworkManager.settings.modify.system**">
     <description>Modify network connections for all users</description>
     <description xml:lang="de">[FONT=Tahoma]...[/FONT]</description>
...
<message>System policy prevents modification of network settings for all users</message>     <message xml:lang="de">...</message>
...
    <defaults>
       <allow_inactive>no</allow_inactive>
       [B]<allow_active>auth_admin_keep</allow_active> => set to "Yes"
[/B]
     </defaults>
   </action>


[/INDENT]And set "yes" instead of "auth_admin_keep" under "allow_active"


I tried this on another laptop with no "gnome-system-tools" ("users-admin" tool) installed, and it worked perfectly.  :)

So I think I am going to try this on my buddy's laptop tomorrow. 

The line that reads:        <allow_active>auth_admin_keep</allow_active> =>  

    "AM I SUPPOSED TO JUST TYPE"

<allow_active>yes<keep/allow_active> =>

---

### Post by tommyarmour on 2011-12-15
**So this is what it reads by default:**


Here is what I did :
Edit this file : /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy

look for that section :
<action id="org.freedesktop.NetworkManager.settings.modify.sys tem">
<description>Modify network connections for all users</description>
<description xml:lang="de">...</description>
...
<message>System policy prevents modification of network settings for all users</message> <message xml:lang="de">...</message>
...
<defaults>
<allow_inactive>no</allow_inactive>
<allow_active>auth_admin_keep</allow_active>

</defaults>
</action>


**Then after the changes it should read like this:**

Edit this file : /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy

look for that section :
<action id="org.freedesktop.NetworkManager.settings.modify.sys tem">
<description>Modify network connections for all users</description>
<description xml:lang="de">...</description>
...
<message>System policy prevents modification of network settings for all users</message> <message xml:lang="de">...</message>
...
<defaults>
<allow_inactive>no</allow_inactive>
<allow_active>yes</allow_active>
</defaults>
</action>


**This makes sense to me. I was hella confused.**

---

### Post by mbilauca on 2012-03-20
Editing the /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy file worked great! Thank you for sharing this!

---

### Post by UranUtan on 2012-05-24
Hi Barbara,

Editing /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy
and change the value of <allow_active>auth_admin_keep</allow_active> to <allow_active>yes</allow_active>

really works great. Thanks very much.

---

### Post by morfal on 2013-05-11
Hello,

The workaround works well, but I am interested in the fix itself.
According to the debian bug track here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136), it should be fixed in version network-manager/0.9.4.0-7 but maybe just for debian. It's still open in gnome bug track [https://bugzilla.gnome.org/show_bug.cgi?id=660392](https://bugzilla.gnome.org/show_bug.cgi?id=660392)
Is this problem never going to be fixed?

---

