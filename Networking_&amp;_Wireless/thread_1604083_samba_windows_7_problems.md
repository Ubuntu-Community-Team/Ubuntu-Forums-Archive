---
title: "samba windows 7 problems"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by tainio on 2010-10-23
Hi

I am trying to setup an Ubuntu based media server. I have installed Ubuntu Desktop as I find it a bit easier to use. 

I have setup Samba on in Ubuntu using[ this guide]("http://ubuntuforums.org/showthread.php?t=202605")

I have followed all the steps but I have a problem with mounting the drive in Windows 7 64bit home eddition. I use \\(ip address)\MyFiles\ and it asks me for user name and password which I enter and then I get error "the mapped drive could not be created - an extended error has occurred"

I have changed 128bit and allowed NTLMv1 in Windows 7 but that has not worked. 

I can not try on any other OS as I only have windows 7

Any ideas please?

Thanks

---

### Post by tainio on 2010-10-24
I have now setup Putty and I can remotely access my Ubuntu machine from my Windows 7 machine but I still can not map the network drive. I have tried deleting Samba and starting again and I'm getiing the same problem.

---

### Post by tainio on 2010-10-24
Sorry something I forgot to mention, the one step from the guide I had a problem with was stopping Samba with...

sudo /etc/init.d/samba stop

It says "sudo: /etc/init.d/samba: command not found"

Maybe this is part of my problem?

---

### Post by luvshines on 2010-10-24
Have you tried using the 'net use' from command console of windows machine to map the network drive.
That may give some extra information to debug

For /etc..., use ```
sudo service smbd [restart/start/stop] 
``` instead

---

### Post by tainio on 2010-10-24
I have just tried that and get "system error 67 has occurred"

A search show this error is[COLOR=Black] "[/COLOR][COLOR=#0000ff][COLOR=Black]The network name cannot be      found"
    
Why would Windows ask for the user name and password if this was the case?
    
I must have gone wrong somewhere along the line but I have no idea where. I have tried setting it up 3/4 times now.

Using "sudo service smb restart/start/stop" does not work either it says "smb: unrecognized service"
  [/COLOR][/COLOR]

---

### Post by tainio on 2010-10-24
I can ping my Ubuntu machine from my Windows machine but not the other way round

---

### Post by luvshines on 2010-10-24
> **tainio said:**
> I have just tried that and get "system error 67 has occurred"

A search show this error is[COLOR=Black] "[/COLOR][COLOR=#0000ff][COLOR=Black]The network name cannot be      found"
    
Why would Windows ask for the user name and password if this was the case?
    
I must have gone wrong somewhere along the line but I have no idea where. I have tried setting it up 3/4 times now.

Using "sudo service smb restart/start/stop" does not work either it says "smb: unrecognized service"
  [/COLOR][/COLOR]

If it is not going by name, try using IP

And for smb, OOPS!!, my mistake, it's smbd (I have edited earlier post as well to reflect this)

---

### Post by tainio on 2010-10-24
I have tried both the name and IP address and have the same problem

I have also tried using smbd. I wasn't sure if I should use the brackets (sorry new to Linux/Ubuntu) and I get the following responses

without - "stop: unkown instance"
With - "The script you are attempting to invoke has been converted to an Upstart job, but [stop] is not supported for Upstart jobs

---

### Post by aunlead on 2010-10-24
I faced a similar problem, i could ping my linux box from windows but couldnt connect (VPN/SAMBA) to it... after running around in circles for a while, i realised that it was because of the firewall rules on the Ubuntu.... 

Try adding "allow" rules to iptables or use" firestarter" like i did and under "allow connections from host" - add your windows box's ip...

hope that helps....

---

### Post by luvshines on 2010-10-24
> **tainio said:**
> I have tried both the name and IP address and have the same problem

I have also tried using smbd. I wasn't sure if I should use the brackets (sorry new to Linux/Ubuntu) and I get the following responses

without - "stop: unkown instance"
With - "The script you are attempting to invoke has been converted to an Upstart job, but [stop] is not supported for Upstart jobs

Oh ok, you don't have to use [], that was just a placeholder notation I used

---

### Post by aunlead on 2010-10-24
> **tainio said:**
> I have tried both the name and IP address and have the same problem

I have also tried using smbd. I wasn't sure if I should use the brackets (sorry new to Linux/Ubuntu) and I get the following responses

without - "stop: unkown instance"
With - "The script you are attempting to invoke has been converted to an Upstart job, but [stop] is not supported for Upstart jobs
well to restart the samba service, you can try - 
sudo service samba restart

---

### Post by tainio on 2010-10-24
> **luvshines said:**
> Oh ok, you don't have to use [], that was just a placeholder notation I used

That's what I thought but it didn't work with or without

---

### Post by tainio on 2010-10-24
> **tainio said:**
> That's what I thought but it didn't work with or without
OK it seems to work now. I must have been doing something wrong, sorry.

---

### Post by tainio on 2010-10-24
> **aunlead said:**
> I faced a similar problem, i could ping my linux box from windows but couldnt connect (VPN/SAMBA) to it... after running around in circles for a while, i realised that it was because of the firewall rules on the Ubuntu.... 

Try adding "allow" rules to iptables or use" firestarter" like i did and under "allow connections from host" - add your windows box's ip...

hope that helps....

I installed firestarter and allowed my IP address from my windows machine and I am still having no luck. I have also added my ubuntu ip in my Windows firewall and that didn't help.

---

### Post by aunlead on 2010-10-24
well can you post the ouputs of -
> testparm -sp

and

> net usershare info

---

### Post by tainio on 2010-10-24
testparm -sp

> 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = JTIP1
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    wins support = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /media/mediaserver/media
    force user = jtip1
    force group = jtip1
    read only = No
    create mask = 0644


---

### Post by tainio on 2010-10-24
net usershare info does not seem to work

---

### Post by luvshines on 2010-10-24
Is /media/mediaserver ... an external drive ??
Also, if it is ext4 or NTFS ?

---

### Post by tainio on 2010-10-24
it is an internal drive and it is ext4

---

### Post by luvshines on 2010-10-24
> **tainio said:**
> it is an internal drive and it is ext4

Gud :)
Ensure that each of the directory in your shared path starting from / upto the media(including mediaserver, media and second media after mediaserver) is having the read permission for the forced user jtip1

---

### Post by tainio on 2010-10-24
jtip1 is the user created during Ubuntu setup/system admin

---

### Post by luvshines on 2010-10-24
> **tainio said:**
> jtip1 is the user created during Ubuntu setup/system admin

I was just asking for a sanity check that directories are readable by that user

And also if you are able to access the shares from the Ubuntu server itself (through nautilus), to check that shares have been created properly

---

### Post by tainio on 2010-10-24
> **luvshines said:**
> I was just asking for a sanity check that directories are readable by that user

And also if you are able to access the shares from the Ubuntu server itself (through nautilus), to check that shares have been created properly
Just checked and I can access the folders and read and write to them from both the cmd line and nautilus

---

### Post by tainio on 2010-10-24
I have done it! No idea how or what I did but it's now working.

Thank you both very much for your help it is very much appreciated

---

### Post by CharlesA on 2010-10-24
Did you use ***smbpasswd -a*** to add a samba user?

smb.conf looks good.

Note on the firewall: Don't use firestarter. Use ufw or gufw.

EDIT: Glad you got it working. :)

Don't forget to mark the thread as solved from the thread tools menu. :)

---

### Post by tainio on 2010-10-24
thanks

will do!

---

### Post by tainio on 2010-10-25
booted up both machines (still setting up the media server and it's not ready to be left on 24/7 yet) this evening and I can't connect again. I have no idea what has changed. Any ideas what else I could try please?

---

### Post by luvshines on 2010-10-25
make sure smbd service is running on the server side

---

### Post by CharlesA on 2010-10-25
> **tainio said:**
> booted up both machines (still setting up the media server and it's not ready to be left on 24/7 yet) this evening and I can't connect again. I have no idea what has changed. Any ideas what else I could try please?

Do they have a static IP address, or just grabbing whatever one they can get?

---

### Post by endotherm on 2010-10-25
try restarting samba on the server (command above) and see if that clears it up. 
I have to restart samba on my server every boot. since it only happens once every couple months i haven't really been annoyed enough to troubleshoot it yet.

---

### Post by tainio on 2010-10-25
I did try restarting Samba and have just tried it again but that did not work.

---

### Post by tainio on 2010-10-25
Ok so I have worked it out, I had to type the following for permissions

> sudo chmod 0777 /media/mediaserver/media

I guess this is not a major problem, but is there a way to permantly set the permissions for this folder?

---

### Post by CharlesA on 2010-10-25
Is the drive that is being mounted a NTFS or FAT32 drive?

Do you have it set to mount in fstab?

---

