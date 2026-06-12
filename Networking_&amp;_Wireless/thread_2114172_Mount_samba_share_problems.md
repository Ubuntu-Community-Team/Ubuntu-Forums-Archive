---
title: "Mount samba share problems"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by dfandrew on 2013-02-09
Hello,

I tried to mount a samba share on my user home. The device that i would mount is a network hd, with a linux microkernel and samba installed.

I create a folder in my home "/home/andrea/smb_mount" end i run the command:

sudo mount -t cifs -o username=admin,password+admin //192.168.57.4/sda1 /home/andrea/smb_mount 

The mount is successful, i can navigate the smb share, I can create a folder with mkdir command, but I don't have permission to write a file.

The samba configuration of my network hd is the following:
[global]                                                                      
workgroup = workgroup                                                      
server string = Server mule                                                
load printers = no                                                         
guest account = nobody                                                      
security = share                                                           
short preserve case = yes
encrypt passwords = yes                                                     
interfaces = br0                                                           
dns proxy = no                                                             
preserve case = yes                                                         
short preserve case = yes                                                   
netbios name = MyServer                                                  
bind interfaces only = True                                                
debug level = -1                                                           

[sda1]                                                                  
   path = /var/mounts/sda1                                           
   public = yes                                                               
   writable = yes                                                       
   printable = no                                                             
   guest ok = yes

Anyone have some ideas about my problem?

---

### Post by dfandrew on 2013-02-10
Anyone can help me? :(:(:(

---

