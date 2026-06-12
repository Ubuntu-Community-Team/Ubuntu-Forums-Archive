---
title: "Sharing files between Windows XP and Ubuntu 10.04"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by Zdravkovski on 2010-09-23
I have pc and a laptop. On the pc i have winXP 32-bit and on the laptop Ubuntu 10.04 64-bit . Can I share files between these two computers (cause i don't want to make dual-boot on my laptop), and if I can, how ?

---

### Post by pedro_orange on 2010-09-23
Yes you can! 

Samba!

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jodlajodla on 2010-09-23
If you want to show some files to other users in network group, first you need to change group. You can do with gedit, just open terminal and log in as root, then paste:
```
gedit /etc/samba/smb.conf
```Find:
```
workgroup = WORKGROUP
```and change the workgroup name to you group on Win.

Then you need to click on folder and click Network Sharing. If you haven't got installed Samba, you will need to do this, first. Then you need to chech all option boxes. Have fun! (if sharing does not working yet, you need to restart computer)

If you have any question, just post it :)

---

### Post by sikander3786 on 2010-09-23
Just another confirmation. You can :-)

If you don't want to be geeky and don't want to tweak samba by going through the configuration files. Here is a very basic setup/installation guide.

Right click any folder you want to share from Ubuntu, go to Sharing Options, tick Share this folder. You'll see a pop-up mentioning installation of some services, select install. After the installation is complete, log out and log in again. Again go to Sharing Options and tick Share this folder and click apply. There are options for guest and write access, configure them according to your needs. And now your shares should be visible on the Windows machine. You already know how to access your Ubuntu machine from Start > Run > \\ipaddress or \\ubuntu-computer-name.

The default workgroup on samba is "workgroup". Configure the Windows machine for the same one.

You can create separate user accounts for samba but not necessary. You can also use your Ubuntu username/password for accessing shares from Windows.

Hope this helps a newbie. There are too many geeky guides on the net but I've not yet found a simple one for newbies.

**[COLOR="Red"]EDIT:[/COLOR]** If your shares reside on a NTFS partition, you'll need to add usershare owner only = false under Global menu in the smb.conf file.

---

### Post by jodlajodla on 2010-09-23
If you want to have network disk, you can read this [http://ubuntuforums.org/showthread.php?p=9855996](http://ubuntuforums.org/showthread.php?p=9855996)

---

