---
title: "Problem connecting to a share"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by Epsilon@pree on 2010-11-25
Hi,
 
I have a BTHome Hub router with a USB HDD hanging of it working like a NAD. This is formated to Fat32 and I can access it from any Windows machine in the home without problem. 
 
I am trying to access it from my Ubuntu 10.10 Netbook but when I try to map to it I get an error. The latest error is 'cli_rpc_pipe_open_noauth: rpc_pipe_bind for pipe \srvsvc failed with error NT_STATUS_UNSUCCESSFUL.
 
Its been a while since I fooled around with mapping from Linux to Windows shares. Can anyone give me a little guidance or point me at a how to guide ?
 
thanks in advance
 
Phree

---

### Post by pawhtiobo on 2010-11-25
Hi :)

Can you test it this way:

Write in nautilus address bar this:

smb://yourrouterip/yourshare

and see if you can access it that way.

See ya...

---

### Post by Epsilon@pree on 2010-11-25
> **pawhtiobo said:**
> Hi :)
 
Can you test it this way:
 
Write in nautilus address bar this:
 
smb://yourrouterip/yourshare
 
and see if you can access it that way.
 
See ya...
 
Thanks, tried that and got a 'your search didnt find any files' message.
 
Phree

---

### Post by Epsilon@pree on 2010-11-25
> **Epsilon@pree said:**
> Thanks, tried that and got a 'your search didnt find any files' message.
 
Phree
 
If I bring up network neighbourhood on the Ubuntu Netbook, I can see the workgroup and the BTHUB hanging below it. I right click and choose the 'mount manually' option. Enter the share name, the ip address and the workgroup name in the dialogue box.
 
It returned the following error,
 
' the share xxxxx could not be mounted and under details I get the following:
 
'mount.cifs:permission denied: no match for /home/phree/smbk4/xxxxx/xxx found in /etc/fstab
 
not sure what this means

---

### Post by pawhtiobo on 2010-11-25
Hi :)

Check this out:

[http://www.linuxquestions.org/questions/linux-networking-3/permission-errors-when-attempting-to-mount-shared-folders-with-smb4k-806231/](http://www.linuxquestions.org/questions/linux-networking-3/permission-errors-when-attempting-to-mount-shared-folders-with-smb4k-806231/)

[http://forums.whirlpool.net.au/archive/1092260](http://forums.whirlpool.net.au/archive/1092260)

[http://www.linuxquestions.org/questions/linux-networking-3/cifs-user-mount-still-havent-figured-this-out-836122/](http://www.linuxquestions.org/questions/linux-networking-3/cifs-user-mount-still-havent-figured-this-out-836122/)

see ya...

---

### Post by Epsilon@pree on 2010-11-26
Thanks for the response.

I have read the links and others besides and it seems they all require the etc/fstab file to be edited. I have taken a look on machine and that doesnt apper to exist. Do I create one from scratch or should it have been created when I installed something??

appologies for the dumb question, I just dont want to screw things up.

Phree

---

