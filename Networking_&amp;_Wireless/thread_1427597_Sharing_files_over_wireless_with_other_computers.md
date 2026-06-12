---
title: "Sharing files over wireless with other computers"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by robinberghuys on 2010-03-11
Hey you guys. I got my somewhat older desktop running ubuntu 9.10 and I'm loving it so far.

However a while ago while I was slightly intoxicated I boasted to my roommates that sharing files with this thing should be super easy, since it's linux and all that. Since then I've been trying to set up the desktop as a streaming media server, with no success. So I turn to you for help.

I found a pretty good [guide](http://www.instructables.com/id/How-to-setup-Samba-file-server/) on how to get Samba up and running on instructables.

The problem I'm having is that my laptop is part of a school domain. Since many of my roommates go to the same university, theirs are also part of that domain. For those of you who aren't too familiar with Windows (anymore), your computer can either be part of a workgroup or a domain. A workgroup is intended for home networks and makes it easier to share files, which is what I'm trying to do, and what the guide calls for. I've illustrated the problem in the attached image. As you can see both computers connect to the same router. I don't think I really have to explain, but I just figured I should try to be as clear as possible.

My question to you is: is there any way that I can set up the ubuntu desktop, or samba, so that it can share files over the wireless network at home with the computers that run windows and are part of the school domain?

I'm guessing I should somehow be able to access the desktop from another computer on the same network if I give it proper access. I just have no idea how to do it or where to look, since almost everything I encounter calls for putting the windows machine in a home workgroup.

Anyway, thanks in advance for any possible help!

---

### Post by inobe on 2010-03-11
you can do this in terminal in just under ten minutes and everything should work fine, if you have a little trouble you can tweak the settings later, but for now lets get you started.

this is strictly a linux howto' however you will need to figure out how to setup file and printer sharing in windows xp, vista, 7.

you can copy and paste these commands into terminal and hit enter for each command, lets install samba if not already installed, open terminal and do

```
sudo apt-get install samba
```

now we need to create a samba user name and password in order for outsiders to access your samba server, you can skip this step' however it's not recommended, but if you want passwordless access skipt it.

replace **username** with your actual ubuntu user name and enter a different password other than the pass you have set for your user account, you will need to enter the password twice, you will not see it when typing it, open terminal and do

```
sudo smbpasswd -a username
```

we need to make a shared folder that outsiders will have access to, remember the username, use your actual user name, i cannot stress it enough, no mistakes.

```
mkdir /home/username/shares
```

we need to backup your current smb.conf

```
sudo cp /etc/samba/smb.conf ~
```

now lets edit your smb.conf

```
sudo gedit /etc/samba/smb.conf
```

scroll all the way down and add these lines exactly how you see it replacing user name with actual user name, click save then close when done.

```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

now lets restart samba

```
sudo /etc/init.d/samba restart
```

lets test for errors

```
testparm
```

that command will check smb.conf for errors, if the output says "loaded services file ok" you are in good shape.

now setup all the windows boxes.

---

### Post by robinberghuys on 2010-03-12
Thank you so much for the quick reply!

The guide to samba that I found said the following: "Change WORKGROUP to whatever you want your workgroup to be."

Now the thing is, the windows computers aren't part of any workgroup, because they are part of the school domain.

What you said doesn't call for changing the workgroup in Samba at all. Does that mean I shouldn't bother with changing the workgroup because it's not necessary? Can I just setup Samba like you said and should the other computers be able to login to it?

Sorry if this seems more like a windows problem. Maybe it is. But I thought I should ask here since I know these forums are a great source of help.

---

### Post by inobe on 2010-03-12
workgroup simply places the windows pc's on the network as a group.

basically you want linux to be a samba server, any pc over the network can access the samba server with that configuration.

looking at that schematic shows me you have a router, pc's connected to that router is a workgroup.

file and printer sharing in vista [http://windows.microsoft.com/en-US/windows-vista/Enable-file-and-printer-sharing](http://windows.microsoft.com/en-US/windows-vista/Enable-file-and-printer-sharing)

xp [http://compnetworking.about.com/od/windowsfilesharing/ht/enable_disable.htm](http://compnetworking.about.com/od/windowsfilesharing/ht/enable_disable.htm)

7 [http://windows.microsoft.com/en-US/windows-vista/Enable-file-and-printer-sharing](http://windows.microsoft.com/en-US/windows-vista/Enable-file-and-printer-sharing)

---

### Post by 2hot6ft2 on 2010-03-12
Nice job inobe. Short and sweet.
:popcorn:

---

### Post by inobe on 2010-03-12
thank you, i'm liking your ssh howto btw =D>

---

### Post by 2hot6ft2 on 2010-03-12
> **inobe said:**
> thank you, i'm liking your ssh howto btw =D>
Thank you, I'm kinda proud of it myself. My first how to.

---

### Post by bradmayne04 on 2010-03-13
hey I'm having a little trouble.  I'm using ubu 9.10 on a laptop tryin to connect to a vista desktop that's plugged in directly to the wireless router.  I can see the icon on the dolphin desktop and the desktop net-bios name shows up when i try to configure the printer (which is directly connected to the vista desktop) however i can not view what's in the network drive that I mapped on the vista computer. i can't even ping the vista desktop w/ the ip address that the desktop has.  I tried traceroute and it goes past the ip address and keeps on going. it's strange any ideas??

---

### Post by Kal318 on 2010-03-13
Hey there I'm having a problem with my computers aways needing username and password access to my server. Normaly I wouldn't have a problem with this how ever my Media center was build to omit both a keyboard and mouse. Is there any way to setup the server up so that it'll grant permanent to said system with out login information. Belowe is the current samba code I'm useing and note I'm fairly nood at this.

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Name"
netbios name = "Server name"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

---

### Post by robinberghuys on 2010-03-13
> **inobe said:**
> workgroup simply places the windows pc's on the network as a group.

basically you want linux to be a samba server, any pc over the network can access the samba server with that configuration.

looking at that schematic shows me you have a router, pc's connected to that router is a workgroup.

Herein lies my problem. The school laptops connected to that router aren't in the workgroup, because they are in the school domain, and can't be in any workgroup. This is the whole problem, really. If I could put them in the workgroup, I would've been able to do this yesterday. Thank you though, your guide was helpful and detailed!

---

