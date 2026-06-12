---
title: "NFS roaming home"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Whiteice on 2010-02-02
Problem: Share home directory from Ubuntu server to remote system.

I just recently setup a ubuntu server and I wanted to share a home directory much like a windows roaming profile expect my goal was to share it among two computers. I found the best way to do this was to use linux NFS and configure the shares to be invisible on the client machines. I dont know if this was the easiest way to do it but based upon what I was searching for there really was not a good how to article besides the on offered on the ubuntu site.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

**Work to be done ahead of time**
This step just makes it a lot easier for you to config the system. You will need to setup a static IP-address on the server now you can do this 1 of two ways.

**first way easiest** if your router allows you to setup DHCP reservation just log into your router and find your server listed and add it to the DHCP reservation and shutdown pc and restart router, then turn on pc.

**second way** you can manually go into the system and configure a static IP address to do this follow the instructions below.

**step 1: edit /etc/network/interfaces**
sudo nano /etc/network/interfaces

add the following information substituting x for your needs

auto eth0
iface eth0 inet static
address x
netmask x
network x
broadcast x
gateway x

**step 2: then press alt+x to save and quit**

**Work to be done of server side.**

**step 1: open up terminal and run**
sudo apt-get install portmap nfs-kernel-server

**step 2: add shares to /etc/exports**
sudo nano /etc/exports

add the following line anywhere in file however you will need to substitute "" fields for you needs

"Server Directory" "Computer Client" (rw,sync,no_subtree_check)

where server directory was the folder to be shared and the computer client is the name of the client computer

example:
/home/user1/Desktop @linux-client (rw,sync,no_subtree_check)

**step 3: then press alt+x to save and quit**

**step 4: export the shares**
sudo exportfs -ra

**NOTE" run sudo exportfs -ra whenever you modify /etc/exports or the system will not work"**

**step 5: restart nfs kernel** 
sudo /etc/init.d/nfs-kernel-server restart

now you should have successfully configured the server side.

**Work to be done on client systems**

step 1: install portmap 
sudo apt-get install portmap nfs-common

step 2: Lock down portmap on client side
sudo nano /etc/hosts.deny

portmap: All

**step 3: then press alt+x to save and quit**

**step 4: allowing server communication only**
sudo nano /etc/hosts.allow

add the following line anywhere substituting need info for "" text

portmap : "NFS server IP address"

NOTE" NFS server IP address must be numeric or system will not work"

**step 5: then press alt+x to save and quit**

**step 6: test mount system**
sudo mount "ServerIP":"folder on server to be shared" "folder to mount over on client"

substitute  serverIP for your servers IP we first specified and folder information on server and client

example:
sudo mount 192.168.1.100: /home/user1/Desktop /home/user1/Desktop

If everything went ok you will not get any errors and a quick test just make a folder on the desktop and if it appears the folder appears on the server side /home/user1/Desktop you have set it up correctly.

**step 7: auto mount folder on boot**
This step will automaticly mount the folder on login so the user will be able to safe files and they will be saved to the server instead of the system

sudo nano /etc/fstab

add line anywhere in fstab file

"server IP": "folder from server" "folder to be mounted to" nfs rw,hard,intr 0 0

substitute  serverIP for your servers IP we first specified and folder information on server and client

example:
192.168.1.100:/home/user1/Desktop /home/user1/Desktop nfs rw,hard,intr 0 0

**step 8: then press alt+x to save and quit**

**step 9: restart and test**
restart your system and login and create a folder on the desktop on the client and if it works you can see the folder on the /home/user1/desktop on the server.

**Last step almost there**
The last thing that we need to do is make the mount invisable and prevent ubuntu from displaying the mounted drives on the desktop.

run gconf-editor

then select apps>nautilus>desktop

remove volumes_visible checkmark and exit

there you go your done

congrats you just setup a virtual folder and it is sharing between a server and client. you can now follow the steps to create additional shares just remeber you have to add the the information to all the files /etc/exports, /etc/fstab and it should work fine. If you have any questions please ask ill try to answer them the best i can. Good luck and have fun shareing

---

