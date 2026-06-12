---
title: "home network retard"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by gogreenpower on 2009-06-16
ok, heres what i've done over the last few weeks, 

i have installed cat 6 cable all through my house, 

i have my wireless broadband router, one desktop (running ubuntu 9.04), a PS3, one headless machine (running ubuntu server 9.04) supposedly acting as a file server all hardwired into a 5 port gigabit router, plus a laptop (running ubuntu 9.04) connected wirelessly. 

all have access to the internet

but for the life of me i cant figure out how to connect them to my file server, i just want a place to store all my media so i can access it from any one of the above listed items

i have followed guide after guide and i must be missing something really basic???????????? 

i didnt think it would be this hard! im still a noob and alot of the server guides are way over my head.

any advice?

---

### Post by AoSteve on 2009-06-16
Many home routers can't establish file sharing or even much for network clarification between the wlan and the eth connections.   I've found this myself to be a pain in the rear.  Being a CCNA student, real routers don't have these issues.  LOL   

Best way to get them all to be able to see the file server is to use a hub/switch.   You can get a four port switch from linksys for like $30.  Just use the switches wlan port to keep the entire network seeing the wlan, and the switch should take care of the rest.   Just make sure that you have all of your addressing complete or under DHCP so the different systems can communicate.   

I personally had this same problem, so what I did was run a router to my PC's eth0 port and run to a switch through the eth1 port.  It took a bit of playing with the settings (since I don't read manuals too often) and vwala.   My PS3 can see my vista media server on my laptop now, even though it's wired in.  (that was how I learned this problem with a lot of home networking gear...   wireless connections didn't like communications with the wired)

---

### Post by gogreenpower on 2009-06-16
im not so worries about my laptop but everything else is hardwired through a switch.

i've given up on the server edition as i think the command line is too much for my first attempt to set this up, so i've installed the desktop edition and am removing all the stuff a server wont need, open office, gimp, etc.

does anybody know the easiest way of setting this up? do i just share the the harddrive storage with read and write permissions for everyone?

---

### Post by superprash2003 on 2009-06-16
you say that all machines have internet access.. so are the machines able to ping each other??if its a linux only network you could use NFS [http://www.prash-babu.com/2008/11/how-to-setup-nfs-server-and-client-in.html](http://www.prash-babu.com/2008/11/how-to-setup-nfs-server-and-client-in.html)  if your network has windows machines as well then you could go with samba [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by alphacrucis2 on 2009-06-16
> **gogreenpower said:**
> im not so worries about my laptop but everything else is hardwired through a switch.

i've given up on the server edition as i think the command line is too much for my first attempt to set this up, so i've installed the desktop edition and am removing all the stuff a server wont need, open office, gimp, etc.

does anybody know the easiest way of setting this up? do i just share the the harddrive storage with read and write permissions for everyone?

What network file system are you using. As another poster said if linux only then use NFS. If you ever want a mixture of linux and windows then use samba (SMB)

---

### Post by gogreenpower on 2009-06-16
its all linux, just trying NFS now

it seems i dont have the option when i right click share folder, and install it installs samba with no option to change. will try the terminal

---

### Post by alphacrucis2 on 2009-06-16
> **gogreenpower said:**
> its all linux, just trying NFS now


does NFS need to be installed on all computers?

The NFS-common package I think includes the client and server components.

---

### Post by gogreenpower on 2009-06-16
haha, thank you very much i have it working perfectly! theres just one small thing, the mount point has to exist (/home/user/folder) on the client machine so when you do mount it you have a folder icon on your desktop and a drive icon of the same name. is there anyway to get it to mount without having to leave the mount point there? if you can understand what im asking?

ok i put a "." in front of the folder which worked, now my auto mounted location looks like ".server" but i can live with that

---

### Post by puppywhacker on 2009-06-16
If you followed the NFS guide from prash, at the bottom of his page he continues.

If you use a terminal to mount nfs-shares you can umount the shares as well and mount them to a diffent location.

```
sudo mount x.x.x.x:/home/prash/test /home/user/Desktop/share
```

and if you're fully satisfied and want the share to be mounted at startup you add a comment to the /etc/fstab file

```
x.x.x.x:/home/prash/test /home/user/Desktop/share nfs rsize=8192,wsize=8192,timeo=14,intr
```

---

