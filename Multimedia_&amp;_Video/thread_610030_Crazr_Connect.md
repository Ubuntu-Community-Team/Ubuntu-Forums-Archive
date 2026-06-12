---
title: "Crazr Connect"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by t.z0n3 on 2007-11-11
I found this tutorial on a website, and I tried to use it. 

> In this tutorial we will learn how connect your Motorola V3X to ubuntu 7.04 trough USB

First of all, we will download the moto4lin utility from the repositories.

sudo aptitude update

sudo aptitude install moto4lin

Once installed, we need to change the configuration file of moto4lin.

cd $HOME/.qt

gedit moto4linrc

We change the old values to this ones. The most important values are, the device, product and vendor values. Those values are for the motorola V3X. Other motorola have different values. I'm sure you may look in web for those values or you may get them inside the moto4lin using inside preferences the update list button. You can activate the auto connect option too.

[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=3002
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=3001
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=0

Now we are going to make a little script in our home directory to load the module and launch moto4lin.

moto4lin you need access from root login to work, so we make a sudo launch.

cd $HOME

gedit motorola

This will be the script:

sudo modprobe cdc_acm

sudo moto4lin

now we only need to allow execution for the script with chmod and we have our script.

chmod 700 motorola

./motorola

If all has gone right we will be able to connect our Motorola V3X by USB.

But this happened.

```
 matthew@matthew:~$ sudo aptitude update
Password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]         
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US              
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US          
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Get:3 http://security.ubuntu.com feisty-security/restricted Packages [6360B]
Ign http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources                 
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US        
Hit http://security.ubuntu.com feisty-security/restricted Sources             
Hit http://security.ubuntu.com feisty-security/universe Packages              
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]        
Get:5 http://security.ubuntu.com feisty-security/universe Sources [6295B]       
Ign http://security.ubuntu.com feisty-security/universe Sources                 
Get:6 http://security.ubuntu.com feisty-security/multiverse Packages [6101B]    
Hit http://security.ubuntu.com feisty-security/multiverse Sources               
81% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers]  8542B/s 1s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com feisty-security/multiverse Packages              
  Sub-process bzip2 returned an error code (2)
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US          
Get:7 http://security.ubuntu.com feisty-security/restricted Packages [6403B]    
83% [7 Packages gzip 0] [Waiting for headers] [Waiting for headers]   8542B/s 1s
gzip: stdin: not in gzip format
Err http://security.ubuntu.com feisty-security/restricted Packages              
  Sub-process gzip returned an error code (1)
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US    
Get:8 http://security.ubuntu.com feisty-security/universe Sources [6490B]       
84% [8 Sources gzip 0] [Waiting for headers]                          8542B/s 1s
gzip: stdin: not in gzip format
Err http://security.ubuntu.com feisty-security/universe Sources                 
  Sub-process gzip returned an error code (1)
Hit http://us.archive.ubuntu.com feisty Release                                 
Hit http://us.archive.ubuntu.com feisty-updates Release                         
Hit http://us.archive.ubuntu.com feisty/main Packages                           
Hit http://us.archive.ubuntu.com feisty/restricted Packages                     
Hit http://us.archive.ubuntu.com feisty/main Sources                            
Hit http://us.archive.ubuntu.com feisty/restricted Sources                      
Hit http://us.archive.ubuntu.com feisty/universe Packages                       
Hit http://us.archive.ubuntu.com feisty/universe Sources                        
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                     
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                      
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                   
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages             
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                    
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources              
Fetched 4564B in 8s (540B/s)                                                    
Reading package lists... Done
matthew@matthew:~$ sudo aptitude install motp4lin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "motp4lin"
The following packages have been kept back:
  cupsys cupsys-bsd cupsys-client cupsys-common libcupsimage2 libcupsys2 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

What should I do?

---

### Post by FXEF on 2007-11-11
You typed, sudo aptitude install motp4lin

Should read: sudo aptitude install moto4lin

---

### Post by t.z0n3 on 2007-11-11
Sorry. ^^; Thanks.

---

