---
title: "Shared folders access"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by shurkes on 2011-07-25
Hi,
I am using an UBUNTU machine as a server to share folders.
Is there anyway to manage the access in a way that few computers will have access to some folder end other computers will have access to other folders?

thanks

---

### Post by Morbius1 on 2011-07-25
Yes. There is a parameter called "hosts allow" that you can add to the share definition to limit access by remote machine.

For example let's say you have a share at /mnt/Data your share definition would look like this:
 
> [Data]
path = /mnt/Data
guest ok = yes
hosts allow = some-listsome-list can be a list of ip addresses:
```
 hosts allow = 192.168.0.100, 192.168.0.101, 192.168.0.103
```Or a list of host names:
```
 hosts allow = machine1, machine2, machine4
```You can even give access to everyone on your lan except one machine:
```
hosts allow = 192.168.0. EXCEPT 192.168.0.102
```

---

### Post by shurkes on 2011-07-25
Thanks,
thats exactly what i am looking for.
Is there any graphical tool to do it?
If not, where is that file where i can edit the list?
Thanks

---

### Post by Morbius1 on 2011-07-25
Most of the graphical tools for samba are destructive in that they don't edit the config file they replace it and usually end up making a mess.

The samba config file is at: /etc/samba/smb.conf

---

### Post by shurkes on 2011-07-25
Thanks,
Forgive me that my knowledge is such basic...
When i am opening the conf file, it says {read only}, how can i edit it?

in the file, i have in the bottom something like this for some folders.
"
[untitled folder]
	path = /home/yesples1/Documents/Public/untitled folder
	writeable = yes
;	browseable = yes
	guest ok = yes
"
Should I add the hosts allow line there just like that?

Thanks again,

---

### Post by malcmail on 2011-07-25
If you are using the command line then use sudo before the command to edit the file. Make a backup of the original first though just in case.

---

### Post by Morbius1 on 2011-07-26
To edit smb.conf as root it's not sudo it's gksu:
```
gksu gedit /etc/samba/smb.conf
```[COLOR=Blue]*sudo with a gui application will eventually corrupt your system.*[/COLOR]
```
[untitled folder]
    path = /home/yesples1/Documents/Public/untitled folder
    writeable = yes
;    browseable = yes
    guest ok = yes
    hosts allow = whatever
```[I][COLOR=Blue]Although Linux can handle such things when forced to do so your life will be a lot easier if you avoid having spaces in names. "untitled-folder" would be a better folder name.

[/COLOR][/I][COLOR=Blue][COLOR=Black]And remember, anytime you edit smb.conf directly you need to restart samba:
[/COLOR][/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][I][COLOR=Blue]

[/COLOR][/I]

---

### Post by shurkes on 2011-07-26
Thanks for that great info,
I have two more questions:
1:
i have like 7 shared folders in that machine and i can access them all from others machines conected to that network but in tha conf file i see only 3 folders. When i made those folders time ago i used teh Nautilus to make the share of them all, way cant i see them in that conf file?
2:
How can i change the folders names to avoid space? when i renamed the folder, the golders name were not changed when i browse from another macine.

Thanks

---

### Post by Morbius1 on 2011-07-26
[1] There are two ways to create a samba share.

One is the Classic Share and it's share definition is in /etc/samba/smb.conf.

The other is called Usershare ( created in Nautilus ) and it's share definition is in /var/lib/samba/usershares

The "hosts allow" on a per share basis only works with Classic Shares. There is no way to add it to a Usershare definition. So I would recommend you go back into Nautilus and "un-share" the folder and then recreate the share in smb.conf. 

[2] My comment on spaces was more of an FYI. You can leave what you have it's just that in the future you should avoid spaces in names.

---

### Post by shurkes on 2011-07-26
Excellent,
It works.

Thanks a lot

---

### Post by shurkes on 2011-07-26
Hi again,
When i do the list of the host by IP it works. i couldnd figure out how to do it by the computer name.
I put my IP and it worked but when i put my computer name (localhost) i was asked to give a password.
Any idea?

---

### Post by Morbius1 on 2011-07-27
Using host names with Samba is problematic especially if you try to use it immediately after boot and if you have many machines on your lan. Ip addresses are better. You might want to investigate if your router has something called DHCP Reservation ( it has many names so look at the help on your router ). DHCP Reservation can assign the exact same ip address to the exact same machine every time that machine boots by linking a specified ip address to the MAC address of the machine in question. That way you don't have to modify the OS to have a static ip address.

Also you can't use "localhost" as a computer name. You have to have a real name. You can set smb.conf to broadcast a real name by adding the following line to the [global] section:
```
netbios name = something
```"something" can be anything you want as long as it's 15 characters or less in length. And remember to restart samba when you make changes to smb.conf:
```
sudo service smbd restart
```

---

### Post by shurkes on 2011-07-28
That is a great idea, I'll try to figure out how to configure my router, so far i didn't find out how to do it but i believe i should look for the right forum for that.
Thanks,

---

