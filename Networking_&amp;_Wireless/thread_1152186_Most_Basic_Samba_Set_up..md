---
title: "Most Basic Samba Set up."
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-05-07
Hey everyone,

I tried following directions here [http://www.jonathanmoeller.com/screed/?p=889](http://www.jonathanmoeller.com/screed/?p=889) .

_However once im done the terminal merely displays the message _

Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE


_Here is what i see if i Type "samba" into the terminal:_

samba                        
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
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

[test]
    path = /home/domce/test
    valid users = domce
    read only = No
    guest ok = Yes
domce@domce-laptop:~$ 


So what should i do ? I would like to be able to use my computer with my windows network.

---

### Post by trendal.toews on 2009-05-07
Have you tried [this]("http://ubuntuforums.org/showthread.php?t=288534") ?

---

### Post by DeusExM1 on 2009-05-07
time to try it.

---

### Post by trendal.toews on 2009-05-07
It got me going.  I admit I am having a problem yet with permissions on one of the storage drives but I can read it fine and read/write on the other one we have.

---

### Post by DeusExM1 on 2009-05-07
well i installed samba via The Add/remove programs and i have a GUI for it. But i have no idea what to do with "shares", or how to set it up. I will try the guide you posted.

---

### Post by trendal.toews on 2009-05-07
Is this what you did?

Quoting from that link I gave you......




Pre-work

There are a few preliminary actions we need to take before we can start mounting using cifs.

Although smbfs is no longer part of Ubuntu, smbfs is still the metapackage which contains all the dependencies necessary for using cifs to mount Samba shares. Hardy does allow for some cifs functionality out of the box, so it may seem like this command is not necessary, but the smbfs metapackage is critical for this howto. Even if you are positive you DO have the smbfs metapackage installed, run this command anyway.
Code:
[B]
sudo aptitude install smbfs[/B]

Now we need to create a location where the samba share can mount. Change "sharename" in the following code to something unique to the remote share, and that you will recognize (usually the share name itself). By creating the mount point in the /media folder, you will get a nifty icon to appear on your desktop like when a cdrom mounts.
Code:
[B]
sudo mkdir /media/sharename
[/B]
To mount a windows share on a DHCP network, it is convenient to be able to mount by netbios name, so you don't have to modify the mount parameters every time you reboot your network. This can be easily enabled by doing the following:

Edit your nsswitch file
Code:
[B]
sudo nano /etc/nsswitch.conf[/B]

search through the file and look for the line that looks something like so:
Code:

hosts:          **files mdns4_minimal [NOTFOUND=return] dns mdns4**

and add "wins" to the line so it looks something like this:
Code:

hosts:          **files mdns4_minimal [NOTFOUND=return] wins dns mdns4**

Save the file by hitting ctrl+x, type "y" to save the buffer, and <enter> to exit.
note: Order does matter. "wins" MUST be before "dns".

Now you'll need to install winbind
Code:
[B]
sudo aptitude install winbind[/B]

Reboot, or restart your network.

---

### Post by DeusExM1 on 2009-05-07
the problem im having is when i type "[B]sudo aptitude install smbfs" then the console says 

The following actions will resolve these dependencies:

Remove the following packages:
samba4
samba4-common

Score is -172

Accept this solution? [Y/n/q/?] 


So i have to click no, or it will uninstall everything i have for samba...
[/B]

---

### Post by trendal.toews on 2009-05-07
I don't have either one of those installed on my Jaunty system.  Are you sure you need it?

---

### Post by DeusExM1 on 2009-05-07
possibly. i think its the gui for printer sharing. 

In any case this samba thing is quite a nightmare. After all this effort, my computer is finally seen by other windows computers, but they cant browse it. also i still cant see other computers on my pc.

---

### Post by trendal.toews on 2009-05-07
> **DeusExM1 said:**
> possibly. i think its the gui for printer sharing. 

In any case this samba thing is quite a nightmare. After all this effort, my computer is finally seen by other windows computers, but they cant browse it. also i still cant see other computers on my pc.


I'm sharing printers on the network and multiple storage devices including one on a Windows box without Samba4 installed.

---

### Post by DeusExM1 on 2009-05-07
honestly i have no idea. Samba takes a lot of effort, so im gonna stop messing with it and forget about it. I have managed to make it so that

1. I can see other computers
2. Other computers see me
3. Other computers can put stuff on my computer 

What i cannot do:
1. I cannot put stuff on other computers. I am prompted for a password. I enter the password i used for samba but it wont work. The other computer is not protected by a password. So yeah i give up.

---

### Post by trendal.toews on 2009-05-07
> **DeusExM1 said:**
> ............. So yeah i give up.

Oh come on..........  Maybe for the moment but not for good.  I'm sorry I don't have the answer for ya.  I really am just a noob. But I have got so much help from here that I like to do what I can.

---

### Post by trendal.toews on 2009-05-07
Maybe someone else could help him...?  I'm not the only turtle in the tank.  It seems like its almost there just missing a little something yet.

---

### Post by DeusExM1 on 2009-05-07
haha its not you man its okay. You helped a lot already. I can get basic functionality with what i have right now.

I can transfer files back and forth by just putting stuff on my computer, since both my computer and the rest of the network can see that 1 share. So it will do i guess.

I just hate how user unfriendly it is.

---

### Post by trendal.toews on 2009-05-07
Yeah I know. Sometimes its a pain.  But I enjoy working on it and I do it for fun.  I charge $$ when I work on Windows machines.  Which I do 8 hours a day.

---

### Post by capscrew on 2009-05-07
> **DeusExM1 said:**
> haha its not you man its okay. You helped a lot already. I can get basic functionality with what i have right now.

I can transfer files back and forth by just putting stuff on my computer, since both my computer and the rest of the network can see that 1 share. So it will do i guess.

I just hate how user unfriendly it is.

I believe you have installed Samba4.  This is still under development.  Most (99.9%) users experience is with Samba3.  I would remove Samba4 **completely** (purge) and install Samba3.  I don't think you will lose any data, but I would make copies of it if you are paranoid.

Once you have done that you can follow the tutorial of your choice.

---

### Post by DeusExM1 on 2009-05-07
yeah i believe i did that. When i was installing the necessary components samba 4 was uninstalled. Its alright though, we can consider it solved, since basic network connectivity is what i got.

---

### Post by capscrew on 2009-05-07
You are happy with what you have now?

---

### Post by DeusExM1 on 2009-05-07
I dont know if i would say happy, but it it works. I really dont want to go through the configs again, its just too lengthy. Maybe another time =/

---

### Post by trendal.toews on 2009-05-07
Thanks capscrew for coming online here.  I kinda felt like my noobness lead him down a dead end street.

---

### Post by capscrew on 2009-05-07
> **KatmanHH said:**
> Thanks capscrew for coming online here.  I kinda felt like my noobness lead him down a dead end street.

I saw you earlier in the day with your own questions.  You where not alone and your advice was good.

---

### Post by trendal.toews on 2009-05-07
ThanksO:)

---

