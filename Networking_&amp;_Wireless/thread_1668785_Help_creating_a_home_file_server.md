---
title: "Help creating a home file server"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by HP dv4 on 2011-01-16
I would like to use an unused desktop running Ubuntu desktop edition as sort of a file server for my house. I don't need to do much other than use it as a networked drive. All of the computers in the house are running either Windows or linux (and a google tv if possible). What programs do I need to use it for this purpose? I've heard something about apache and samba. What else do I need?

---

### Post by inobe on 2011-01-16
very simple to do, ignore creating the password if it's just over your network and you want insecure access.

1) we need to install samba if it's not already installed.

```
sudo apt-get install samba
```

that command will install samba and the service will also be enabled.

2) we need to create a samba user name and password to secure your shares from outsiders, it's an option to do so, replace "username" with your actual user name, for example /home/bob, you will need to enter a pass twice, you will not see your pass when typing, let the pass be different from your actual log in pass.

```
sudo smbpasswd -a username
```

3) we need to make a shared folder that outsiders will have access to instead of them accessing the entire home folder, be sure to edit out username with actual account user name, you can call shares whatever or leave it.

```
mkdir /home/username/shares
```

4) we need to backup your current smb.conf.

```
sudo cp /etc/samba/smb.conf ~
```

5) now lets edit your smb.conf.

```
gksu gedit /etc/samba/smb.conf
```

when gedit opens up with your smb.conf' scroll down to the end and add this replacing username with your actual user name, and replace shares if differently named in step 3.

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

now click save and close gedit

6) now lets restart samba.

```
sudo /etc/init.d/samba restart
```

7) lets test for errors.

```
testparm
```

that command will check smb.conf for errors, if the output says "loaded services file ok" you are in good shape.

now you can go to a windows machine or whatever and try to access your ubuntu machine, you will need your user name and password you created earlier in order to access the kubuntu machine shares if option taken, you can access the windows network from ubuntu so as long that machine has file and printing sharing enabled.

---

### Post by HP dv4 on 2011-01-16
I have a slight problem. In the config file, I could not find a section under the title [shared](that's what I named it)so I changed the path under the headings of [print$] and [profiles]. Nothing is showing up on my windows machine.

---

### Post by inobe on 2011-01-16
> **HP dv4 said:**
> I have a slight problem. In the config file, I could not find a section under the title [shared](that's what I named it)so I changed the path under the headings of [print$] and [profiles]. Nothing is showing up on my windows machine.

scroll all the way to the bottom, skip one space, you create the section after that space with copy and paste, just copy and paste the code and edit out whatever and click save.

example

```
blah blah windows blah network

[shares]
path = /home/bob/shares
available = yes
valid users = bob
read only = no
browsable = yes
public = yes
writable = yes
```

notice space between **blah blah windows blah network** and **[shares]**

**[shares]** creates a section, this will be all the way down :)

after done please reboot all your machines

---

### Post by inobe on 2011-01-16
it seems like you may have messed up your conf file, you can restore it to it's original settings doing 

```
sudo cp /etc/samba/smb.conf.backup /etc/samba/smb.conf
```

because we backed up the original in step 4 we can start over.

use that if you don't remember what you changed editing the file.

close gedit then start over with step 5.

---

### Post by HP dv4 on 2011-01-17
I went to the trouble of reinstalling Ubuntu to make sure that I would start over fresh. I went through all of the steps again on the fresh system and got nothing. Just to make sure, where I go to find the shares folder in Windows? I couldn't find it anywhere in windows explorer.

---

### Post by HP dv4 on 2011-01-23
You didn't tell me that there was a GUI version of Samba waiting for me in the Ubuntu Software Center.

---

