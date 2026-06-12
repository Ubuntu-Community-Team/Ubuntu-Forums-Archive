---
title: "Icybox Nas (samba) Connection Problems"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by alastairpjb on 2011-04-19
[FONT=Arial, sans-serif][COLOR=#000000][SIZE=3]**[SIZE=2]Ubuntu 10.10 Laptop[/SIZE]**[/SIZE][/COLOR][SIZE=2][COLOR=#000000](wireless)                 <---> [/COLOR][/SIZE][SIZE=2][COLOR=#000000]**Router**[/COLOR][/SIZE][SIZE=2][COLOR=#000000](wireless                 & ethernet) <---> [/COLOR][/SIZE][SIZE=2][COLOR=#000000]**Nas:-**[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]**ICYBOX                 IB-NAS3221-B**[/FONT][/COLOR][/SIZE][FONT=Arial, sans-serif][SIZE=2][COLOR=#000000](ethernet)[/COLOR][/SIZE][/FONT]

                  [SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]I                 have spent ages looking how to get a stable connection from my laptop to my router. I have found out lots of information but it means nothing to me =/. I am rubbish with commands and struggle to do basics. [COLOR=DarkGreen]
**Please help any ideas/information are welcome!**[/COLOR][/FONT][/COLOR][/SIZE]

                 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=5]_Goal_[/SIZE][/FONT][/COLOR]

Permanently mount nas samba share (megadrive) without it disconnecting every few mins.
or
a script that runs in the background and runs [FONT=Arial, sans-serif][SIZE=2][COLOR=#0000ff]"smbmount                 //192.168.2.65/megadrive /megadrive -o                 username=megadrive,password=mypassword" [COLOR=black]every 60secs[/COLOR][/COLOR][/SIZE][/FONT]. That would do the trick. 

(I have no idea how to write a script took me ages to work out that smbmount thingy).
                 

  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=5]_Main Problem _[/SIZE][/FONT][/COLOR]

                                  [SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]Can ***temporarily ***connect                 to the nas but connection                 auto disconnects after a few mins. When the                 connection is running it can copy, read, write and                 stream dvds. But will not                 copy large files(e.g 3GB)?[/FONT][/COLOR][/SIZE]
                                                                                                                                              [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]
[SIZE=2]My                             Network [/SIZE][/SIZE][SIZE=2]Link[/SIZE][SIZE=2] is [/SIZE][SIZE=2]on                             my desktop panel with these properties [/SIZE][SIZE=2]and                             
ubuntu has the password saved[/SIZE][SIZE=2]:-[/SIZE][/FONT][/COLOR][INDENT]*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]_Launcher                             Properties_[/SIZE][/FONT][/COLOR]*
*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]                                                                                                                                                                                                                     Name: megadrive [/SIZE][/FONT][/COLOR]*
*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]                                                                                                                                                                          Location:                             [/SIZE][/FONT][/COLOR][COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]smb://megadrive;megadrive@192.168.2.65/megadrive[/SIZE][/FONT][/COLOR]*
*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]Co[/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]mment:[/SIZE][/FONT][/COLOR]*
[/INDENT]
[LIST=1]
[*][FONT=Arial, sans-serif][SIZE=2][COLOR=#000000]First                     click on my desktop network shortcut an error appears. [/COLOR][/SIZE][/FONT]                     [SIZE=2]
[/SIZE]
[*][FONT=Arial, sans-serif][SIZE=2][COLOR=#8b0000]"Error"
"Could                     not open location                     'smb://megadrive;megadrive@192.168.2.65/megadrive'"
"No data                     available"[/COLOR][/SIZE][/FONT]
[*][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]Second                     time I click on the shortcut I am taken to the network folder                     fast.(WORKS)[/FONT][/COLOR][/SIZE]
[/LIST]
                                  
[LIST]
[*][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]I                     have noticed that if I set the nas spin-down time to 2mins this                     problem disappears but keeping this setting will wear out my                     Hardrive. [/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]Streaming                     a DVD from nas to laptop works correctly it is just the folders                     that lose their link temporarily.[/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000000][COLOR=#000000]Ubuntu                     finds the device twice? [/COLOR][COLOR=#000000]But cannot                     open MEGADRIVE just view properties. [/COLOR][COLOR=#000000]The                     permissions tab in properties says[/COLOR] [FONT=Arial, sans-serif]*The                     permissions of “Windows shares on Megadrive” could not be                     determined.*[/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]**First                     Location:**      *Places>Network>***MEGADRIVE** [/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]**Second                     Location:***Place>Network>WindowsNetwork>MEGADRIVE>***MEGADRIVE**[/FONT][/COLOR][/SIZE]
[/LIST]
                                                                              [COLOR=#000000][FONT=Arial, sans-serif][SIZE=5]**_Problem                 B_**[/SIZE][/FONT][/COLOR]

[SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]Wanted to auto mount the NAS samba share at boot but it does not                 work. Added the following                 line to the below files [/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif](fstab & rc.local) [/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Arial, sans-serif] separately. [/FONT][/COLOR][/SIZE]                 [SIZE=2]

[/SIZE][INDENT][FONT=Arial, sans-serif][SIZE=2][COLOR=#0000ff]smbmount                 //192.168.2.65/megadrive /megadrive -o                 username=megadrive,password=mypassword[/COLOR][/SIZE][/FONT]
[/INDENT][SIZE=2] 
[/SIZE][INDENT][FONT=Arial, sans-serif][SIZE=2][COLOR=#000000]etc>rc.local--(result)--->                 Does nothing[/COLOR][/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial, sans-serif][SIZE=2][COLOR=#000000] etc>fstab-----(result)---> Boot error; [/COLOR][COLOR=#800000]“[/COLOR][COLOR=#8b0000]**An                 error occurred while mounting 0 Press S to skip mounting or M for                 manual recovery”**[/COLOR][/SIZE][/FONT]
[/INDENT][COLOR=#000000][FONT=Arial, sans-serif]_[SIZE=2]**fstab                 File **[/SIZE][SIZE=2]**Below:-**[/SIZE]_[/FONT][/COLOR]
                                                                                                                 [FONT=Arial, sans-serif][SIZE=2]#                             /etc/fstab: static file system information. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             Use 'blkid -o value -s UUID' to print the universally unique                             identifier [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             for a device; this may be used with UUID= as a more robust way                             to name [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             devices that works even if disks are added and removed. See                             fstab(5). [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             <file system> <mount point>   <type>                              <options>       <dump>  <pass> [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]proc                                        /proc           proc    nodev,noexec,nosuid 0                                   0 [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             / was on /dev/sda5 during installation [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]UUID=a0df2d2b-50fc-4e28-ad5a-70694bb75429                             /               ext4    errors=remount-ro 0       1 [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             swap was on /dev/sda6 during installation [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]UUID=5f10b01e-1443-4092-a8b6-645dbb78e42e                             none            swap    sw              0       0[/SIZE][/FONT]
                             [COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]smbmount                             //192.168.2.65/megadrive /megadrive -o                             username=megadrive,password=mypassword[/SIZE][/FONT][/COLOR]
                                                                                                 

                                  [COLOR=#000000][FONT=Arial, sans-serif]_[SIZE=2]**rc.local                 File **[/SIZE][SIZE=2]**Below:-**[/SIZE]_[/FONT][/COLOR]
                                                                                                                 [FONT=Arial, sans-serif][SIZE=2]#!/bin/sh                             -e [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             rc.local [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             This script is executed at the end of each multiuser                             runlevel. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             Make sure that the script will "exit 0" on success                             or any other [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             value on error. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             In order to enable or disable this script just change the                             execution [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             bits. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             By default this script does nothing. [/SIZE][/FONT]
                             
                             [FONT=Arial, sans-serif][SIZE=2]exit                             0 [/SIZE][/FONT]
                             [COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]smbmount                             //192.168.2.65/megadrive /megadrive -o                             username=megadrive,password=mypassword[/SIZE][/FONT][/COLOR]
                                                                                

                
                 [FONT=Arial, sans-serif][COLOR=#000000][SIZE=5]_My                 _[/SIZE][/COLOR][COLOR=#000000][SIZE=5]_Network                 Set Up _[/SIZE][/COLOR][COLOR=#000000][SIZE=3][B]

[SIZE=2]Laptop[/SIZE][/B][/SIZE][/COLOR][SIZE=2][COLOR=#000000](wireless)                 <---> [/COLOR][/SIZE][SIZE=2][COLOR=#000000]**Router**[/COLOR][/SIZE][SIZE=2][COLOR=#000000](wireless                 & ethernet) <---> [/COLOR][/SIZE][SIZE=2][COLOR=#000000]**Nas**[/COLOR][/SIZE][SIZE=2][COLOR=#000000](ethernet)[/COLOR][/SIZE][/FONT][SIZE=2]
[/SIZE]                                   [SIZE=2][COLOR=#000000][FONT=Arial, sans-serif]
Laptop                 IP:192.168.2.2 (DHCP)                                                                                                                                            (ext4)
Router IP:192.168.2.1 (Static) 
                                                                                                                                          Nas IP: 192.168.2.65 (Static) (fat32)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]                                   [U][B]
Terminal Readout of network Below:[/B][/U] -
                
                                                                                                                 [FONT=Arial, sans-serif][SIZE=2]$[COLOR=#0000ff]                             smbtree [/COLOR][/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]Enter <user> password:[/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]WORKGROUP [/SIZE][/FONT]
                             [COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]MEGADRIVE [/SIZE][/FONT][/COLOR]
                             [FONT=Arial, sans-serif][SIZE=2]    \\MEGADRIVE                                          Megadrive Network Storage [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\MEGADRIVE\lp                                             Generic dot-matrix printer entry [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\MEGADRIVE\IPC$                                           IPC Service (Megadrive Network Storage) [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\MEGADRIVE\public                                         Folder Share for public [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\MEGADRIVE\mega                                            [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        [COLOR=#0000ff]\\MEGADRIVE\megadrive[/COLOR]                                       [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]    \\CQ61                                               CQ61 server (Samba, Ubuntu) [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\CQ61\print$                                         Printer Drivers [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]        \\CQ61\IPC$                                           IPC Service (CQ61 server (Samba, Ubuntu)) [/SIZE][/FONT]
                                                                                                 [FONT=Arial, sans-serif]


[COLOR=#000000][SIZE=2]_**Samba                 Log (Icybox NAS)**_[/SIZE][/COLOR][/FONT]
                                                                                                                                                                                                             
                                                                                                            [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2][2007/01/02                             04:59:48, 0[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]smbd version                             3.0.25a started.[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]
                                                                                                            [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             05:28:11, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             connect to service megadrive initially as user megadrive                             (uid=7003, gid=100) (pid 1724)[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             05:42:37, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             closed connection to service megadrive[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                                                                                                                                                                                    [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:14:46, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             connect to service megadrive initially as user megadrive                             (uid=7003, gid=100) (pid 1960)[/SIZE][/COLOR][/FONT][COLOR=DimGray]
                                                                                                                                                        [/COLOR][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:21:25, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             closed connection to service megadrive[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                                                                                                                                                                                    [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:32:46, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             connect to service megadrive initially as user megadrive                             (uid=7003, gid=100) (pid 2053)[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                                                                                                                                                                                    [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:38:47, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             closed connection to service megadrive[/SIZE][/COLOR][/FONT][COLOR=DimGray]
                                                                                                                                                        [/COLOR][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:42:11, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             connect to service megadrive initially as user megadrive                             (uid=7003, gid=100) (pid 2081)[/SIZE][/COLOR][/FONT][COLOR=DimGray]

[/COLOR]                                                                                                                                                                                                                                                                    [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)[/SIZE][/COLOR][/FONT][FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2] [2007/01/02                             06:48:31, 1[/SIZE][/COLOR][/FONT][COLOR=DimGray]
[/COLOR]                                                                                                             [FONT=Arial, sans-serif][COLOR=DimGray][SIZE=2]cq61 (192.168.2.2)                             closed connection to service megadrive[/SIZE][/COLOR][/FONT]
                                                                                

                 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=5]_Quick                 Summary_[/SIZE][/FONT][/COLOR]
                 
[LIST]
[*][COLOR=#000000][FONT=Arial, sans-serif]Samba                     Connection dropped by Laptop to Nas after few mins                                                                              [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif]Laptop                     unable to automount Nas[/FONT][/COLOR]
[/LIST]
[SIZE=4][COLOR=DarkGreen]Any Help Would Be really appreciated![/COLOR][/SIZE]:confused:

---

### Post by alastairpjb on 2011-04-19
removed

---

### Post by alastairpjb on 2011-04-19
removed

---

### Post by alastairpjb on 2011-04-19
removed

---

### Post by Morbius1 on 2011-04-19
> [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3][SIZE=2]My                             Network [/SIZE][/SIZE][SIZE=2]Link[/SIZE][SIZE=2] is [/SIZE][SIZE=2]on                             my desktop panel with these properties [/SIZE][SIZE=2]and                             
ubuntu has the password saved[/SIZE][SIZE=2]:-[/SIZE][/FONT][/COLOR][INDENT]*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]_Launcher                             Properties_[/SIZE][/FONT][/COLOR]*
*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]                                                                                                                                                                                                                         Name: megadrive [/SIZE][/FONT][/COLOR]*
*[COLOR=#333333][FONT=Arial, sans-serif][SIZE=2]                                                                                                                                                                             Location:                             [/SIZE][/FONT][/COLOR][COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]smb://megadrive;megadrive@192.168.2.65/megadrive[/SIZE][/FONT][/COLOR]*[/INDENT]Location: nautilus smb://192.168.2.65/megadrive
> [COLOR=Black][FONT=Arial, sans-serif][SIZE=2]smbmount                              //192.168.2.65/megadrive /megadrive -o                              username=megadrive,password=mypassword[/SIZE][/FONT][/COLOR]The line above is the wrong syntax for fstab:
```
//192.168.2.65/megadrive /megadrive cifs username=megadrive,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0
```
[COLOR=Blue]**EDIT: To test it without rebooting run the following command after you update fstab:**[/COLOR]
```
 sudo mount -a
```[COLOR=#000000][FONT=Arial, sans-serif]_[SIZE=2][/SIZE]_[/FONT][/COLOR]> [COLOR=#000000][FONT=Arial, sans-serif]_[SIZE=2]**rc.local                 File **[/SIZE][SIZE=2]**Below:-**[/SIZE]_[/FONT][/COLOR]
                                                                                                                 [FONT=Arial, sans-serif][SIZE=2]#!/bin/sh                             -e [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             rc.local [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             This script is executed at the end of each multiuser                             runlevel. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             Make sure that the script will "exit 0" on success                             or any other [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             value on error. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             In order to enable or disable this script just change the                             execution [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             bits. [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]# [/SIZE][/FONT]
                             [FONT=Arial, sans-serif][SIZE=2]#                             By default this script does nothing. [/SIZE][/FONT]
                             
                             [FONT=Arial, sans-serif][SIZE=2]exit                             0 [/SIZE][/FONT]
                             [COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]smbmount                              //192.168.2.65/megadrive /megadrive -o                              username=megadrive,password=mypassword[/SIZE][/FONT][/COLOR]
                                                                                Place the line before the "exit 0" line not after it.

---

### Post by alastairpjb on 2011-04-19
> **Morbius1 said:**
> Location: nautilus smb://192.168.2.65/megadrive
The line above is the wrong syntax for fstab:
```
//192.168.2.65/megadrive /megadrive cifs username=megadrive,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0
```[COLOR=Blue]**EDIT: To test it without rebooting run the following command after you update fstab:**[/COLOR]
```
 sudo mount -a
```Place the line before the "exit 0" line not after it.

[SIZE=2]I have entered the code adove into fstab file.[/SIZE]
[COLOR=DimGray]
[/COLOR][INDENT][COLOR=DimGray]# /etc/fstab: static file system information.[/COLOR]
[COLOR=DimGray]#[/COLOR]
[COLOR=DimGray]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/COLOR]
[COLOR=DimGray]# for a device; this may be used with UUID= as a more robust way to name[/COLOR]
[COLOR=DimGray]# devices that works even if disks are added and removed. See fstab(5).[/COLOR]
[COLOR=DimGray]#[/COLOR]
[COLOR=DimGray]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/COLOR]
[COLOR=DimGray]proc            /proc           proc    nodev,noexec,nosuid 0       0[/COLOR]
[COLOR=DimGray]# / was on /dev/sda5 during installation[/COLOR]
[COLOR=DimGray]UUID=a0df2d2b-50fc-4e28-ad5a-70694bb75429 /               ext4    errors=remount-ro 0       1[/COLOR]
[COLOR=DimGray]# swap was on /dev/sda6 during installation[/COLOR]
[COLOR=DimGray]UUID=5f10b01e-1443-4092-a8b6-645dbb78e42e none            swap    sw              0       0[/COLOR]
[COLOR=Blue]//192.168.2.65/megadrive /megadrive cifs username=megadrive,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0[/COLOR]
[/INDENT][SIZE=2]When I entered mount -a in terminal a chdir error appeared. I rebooted the machine anyway regardless of error and the following appeared before logon:-[/SIZE][INDENT][COLOR=DimGray]fsck from until-linux-ng 2.17.2[/COLOR]
  [COLOR=DimGray] /dev/sda5: clean, 184808/3662848 files, 4979177/14648064 blocks[/COLOR]
  [COLOR=DimGray] * Starting AppArmor profiles            mount error(101): Network is unreachable[/COLOR]
  [COLOR=DimGray] Refer to the mount.cifs(8) manual page (e.g man mount.cifs)[/COLOR]
  [COLOR=DimGray] mountall: mount /megadrive [954] terminated with status 32[/COLOR]
  
  [COLOR=DimGray] Skipping profile in etc.bin.firefox[/COLOR]
  [COLOR=DimGray] *Setting sensor limits                                 [OK][/COLOR]
  [COLOR=DimGray] *Starting Samba 4 daemon samba              [OK][/COLOR][/INDENT][SIZE=2]ubuntu logged on (without mounting drive) My network shortcut still works the same one click error, second click works and then 1-6mins ish later connection dropped. After another reboot I opened the terminal and typed mount -a nothing happened no error and no mount?:confused:

[/SIZE]  [SIZE=2]I adjusted the the rc.local file too no success (no mount) =/[/SIZE][INDENT][COLOR=DimGray]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR=Blue]smbmount //192.168.2.65/megadrive /megadrive -o username=megadrive,password=mypasword[/COLOR]

exit 0[/COLOR] 
[/INDENT][SIZE=2][COLOR=DarkGreen]Thanks for the help **Morbius1**!! Its nice to have something to try but no success[/COLOR] :( Any more Ideas?[/SIZE][INDENT][COLOR=DimGray]
[/COLOR][/INDENT]

---

### Post by Morbius1 on 2011-04-20
.

---

### Post by Morbius1 on 2011-04-20
> [COLOR=Black]* Starting AppArmor profiles            mount error(101): Network is unreachable[/COLOR]I know nothing of AppArmor but I would suggest you disable it ( however that is done ) and try to access the lan again.
> [COLOR=DimGray][COLOR=Black]*Starting Samba 4 daemon samba [/COLOR]             [OK][/COLOR]Go into Synaptic and uninstall all things Samba4 related. THe description of Samba4 from Synaptic:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. [COLOR=Blue]These should be considered _experimental_, and should not be used in production.[/COLOR] In particular, no guarantees are made with regard to upgrades between versions. I have no idea why it's in the repositories.

---

### Post by alastairpjb on 2011-04-20
:) The problem is solved! I have deleted the additional line to rc.local and modified fstab with:-

//192.168.2.65/megadrive /megadrive cifs username=megadrive,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0


Also deleted all things apparmor & samba4!

**[COLOR=DarkGreen]Thankyou for you quick response Morbius1 really appreciate it[/COLOR]!**.

[SIZE=4]_The Final Method to Load Icybox IB-NAS3221-B_[/SIZE]

_Step 1_
(Follow the manual on how to make windows share)

_Step1b_

Stick this code into bottom of etc>fstab file replacing it with your info.

[COLOR=Blue]//192.168.2.65/megadrive /megadrive cifs username=megadrive,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0[/COLOR] 

Type $ [COLOR=Blue]sudo mount -a[/COLOR] 

Reboot computer
[U]
Step 2[/U]
go to Places>File System>megadrive (or whatever you called your network)

_Step 3_
Then click Bookmarks>Add Bookmark

_Step 4_
That created a link in Places

_Extra to get desktop panel icon_
1) I dragged the megadrive link from Places>megadrive to my Home Folder
2) Then I dragged the the megadrive shortcut from Home Folder to Desktop panel
3) That creates a link like the firefox button on your desktop except it takes you to the megadrive (or whatever you called your network)!
4) (If you right click and press properties you can change the icon picture, Name, Location, Comment)

NB: Don't delete the shortcut from you Home Folder as it will stop the desktop panel link working!

[COLOR=DarkGreen]Thanks again [B]Morbius1! 
[/B][/COLOR]

---

