---
title: "Browsing Windows 7 Network Drives"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by wolfgentleman on 2013-01-02
I have been searching for several days now, I have a Windows 7 PC with a 1TB USB drive shared on the network. It is available for read and write to anyone who has the username and password to the PC. In Windows I would double click the PC on the network, type in the username/password, double click the shared drive and I would have have read write abilities. I cannot seem to access it from Linux, however. I have my network on static IPs so if I need to connect using the IP I can do that.

I have tried:


[LIST]
[*]The program: Smb4K
[*]mount -t cifs //192.168.1.20/Backup-Drive '/Backup Drive/' -o rw user='PC name' password='password'
[*]mount -t cifs //192.168.1.20/ '/Backup Drive/' -o rw
[/LIST]
And I have pressed the next button on google so many times my hand hurts and have came back with negative results.

---

### Post by ketan985 on 2013-01-03
Hi... I also Faced such problem When I was new 

Open  file manager

Just Press  CTRL+L

You will able to write address  write follwing

smb://192.168.1.20

Enjoy your Windows share !!!

---

### Post by wolfgentleman on 2013-01-03
It said:
> 
Timeout on server
192.168.1.20


---

### Post by wolfgentleman on 2013-01-07
bump

---

### Post by wolfgentleman on 2013-01-08
bump

---

### Post by wolfgentleman on 2013-01-10
bump

---

### Post by drdos2006 on 2013-01-10
Here are some notes I made when I had the same issue.

The Samba configuration should be modified to show the Windows 7 workgroup or homegroup.
From a terminal onthe Ubuntu machine, type :
sudo gedit /etc/samba/smb.conf

Enter your password and change this section in Global.
# Change this to the workgroup/NT-domain name your Samba server will part of
      workgroup = MyWorkGroup
Change MyWorkGroup to your Windows7 workgroup name.
Restart samba with sudo /etc/init.d/smbd restart

//////////////////////////////////////////////////////
There are a couple of ways to get to the section to allow Windows7 sharing.

From the Control Panel -> Network and Internet -> Network and Sharing Center -> Advanced sharing settings -> Choose Homegroup and sharing options-> Change Advanced sharing settings

From the Control Panel -> Network and Internet -> HomeGroup -> Choose Homegroup and sharing options -> Change Advanced sharing settings

Turn on network discovery
Turn on file and printer sharing
Turn on sharing so that anyone with network access can read and write files in the Public folders
Use 128-bit encryption to help protect file sharing connections
Turn on password protected sharing
Use user accounts and passwords to connect to other computers.
Save and close


Right click the folder you wish to share.
Share with -> HomeGroup(Read/Write) or 
Share with -> Specific people
Choose Read/Write plus the Share button.

Once the folder is shared an information dialogue should show at the bottom of the page when the shared folder is highlighted.
It should show State: Shared and Shared With: Your sharing selection(s)

From the Ubuntu machine, Places, Network should now show the Windows machine
Selct the Windows machine and the Windows shared folders should be seen.

Select the folder, enter the user name of the Windows machine, password, remember the password or not and you should be connected.
///////////////////////////////////////////////////////
Update
From the Control Panel -> Network and Internet -> Network and Sharing Center -> Advanced Sharing Settings.
In both the Current Profile and also in the expanded Public section, Turn on Network Discovery, File and Printer Sharing.
Turn off Password Protected Sharing.
Save and CLose.

From Computer, 
Select the folder you wish to share.
Right click the folder, Share With -> Specific People.

In the Drop Down List select Everyone

From the Drop Down List for Everyone, select Read or Read/Write.

From your Ubuntu machine, you should be now be able to connect.
//////////////////////////////////////////////////////

regards

---

### Post by wolfgentleman on 2013-01-12
bash: /etc/init.d/smbd: No such file or directory

It was already set in the config file, and my windows pc is already set to everyone and is password protected.

---

### Post by Cheesemill on 2013-01-12
Are you using a homegroup or a workgroup on Windows 7 to share you files?

Homegroups only work with Windows 7 & 8, you have to use workgroup sharing for other OS's to connect.

---

### Post by wolfgentleman on 2013-01-12
Workgroup.

---

### Post by drdos2006 on 2013-01-12
When you open a terminal and type "sudo /etc/init.d/smbd restart"
do you get something like this ?
> 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart smbd
smbd start/running, process 3224


regards

---

### Post by wolfgentleman on 2013-01-13
bump

---

### Post by wolfgentleman on 2013-01-14
bump

---

### Post by wolfgentleman on 2013-01-14
> **wolfgentleman said:**
> **bash: /etc/init.d/smbd: No such file or directory**

It was already set in the config file, and my windows pc is already set to everyone and is password protected.

I posted the output already.

---

### Post by wolfgentleman on 2013-01-14
I finally figured it out.
Problem:
```
mount -t cifs //192.168.1.20/Backup-Drive '/Backup Drive/' -o rw user='PC name' password='password'
```Fix:
```
mount -t cifs //192.168.1.20/Backup-Drive '/Backup Drive/' -o rw,user='PC name',password='password'
```

It is very funny how putting a space instead of a comma messed up the whole command.

---

### Post by Cheesemill on 2013-01-14
> **wolfgentleman said:**
> It is very funny how putting a space instead of a comma messed up the whole command.
Not really.

If you look at the mount command documentation it is very clear about needing to use commas to string together different filesystem options (-o).

```
man mount
```

>        -o, --options opts
              Options are specified with a -o flag followed by a comma separated string of options. For example:

                     mount LABEL=mydisk -o noatime,nouser


---

### Post by drdos2006 on 2013-01-14
And No, you did not post an output of "sudo /etc/init.d/smbd",
you posted an output of "bash: /etc/init.d/smbd".

regards

---

### Post by wolfgentleman on 2013-01-14
That is what it spit out. I typed the command, hit enter, and thats what it spit out at me. I know what I saw, I know what I pasted. And I found the command in that format on a site (spaces instead of commas) and I finally used "info mount" to figure out why it wasn't working.

---

### Post by wolfgentleman on 2013-01-14
The attached image is proof that I did post the output. Thank you very much.

---

### Post by CharlesA on 2013-01-14
> **Cheesemill said:**
> Not really.

If you look at the mount command documentation it is very clear about needing to use commas to string together different filesystem options (-o).

```
man mount
```

I remember running into that when I was trying to mount a cifs share via the terminal. Royal pain in the butt! I finally got it figured out, but there was a few different "howtos" that had different information.

> **wolfgentleman said:**
> The attached image is proof that I did post the output. Thank you very much.

You never said what version of Ubuntu you were running.

smbs and nmbd started in 10.04, if I remember right. Before that it was just smb or samba, not sure.

---

### Post by drdos2006 on 2013-01-14
As I stated, you should have got something like this.

> 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart smbd
smbd start/running, process 5482


Glad you got it sorted out. Maybe Konsole accepts and shows different results for terminal commands ?? 

regards

---

### Post by CharlesA on 2013-01-14
> **drdos2006 said:**
> Maybe Konsole accepts and shows different results for terminal commands ??

Doubt it. It should throw the same messages the normal terminal would. It is likely they are running an older version of Ubuntu on that machine, or they don't have Samba installed on the machine they are trying to access the share from.

---

