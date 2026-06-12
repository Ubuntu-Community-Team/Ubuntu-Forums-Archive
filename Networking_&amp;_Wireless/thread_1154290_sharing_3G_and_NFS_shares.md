---
title: "sharing 3G and NFS shares"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by blackest_knight on 2009-05-09
This is a rather complicated set up so bare with me. 

I've got a hspda modem this is connected to a server/desktop 
and the eth0 is connected to the wan port of a router.
for those interested  to portforward you need to 
edit 
/etc/sysctl.conf
and un comment this line 
net.ipv4.ip_forward=1

this script below would set up ipables for forwarding if run by root. 
and would be reset on a reboot (probably) 
#bin/bash
ifconfig eth0 192.168.2.1
iptables -t nat -A POSTROUTING  -o ppp0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING  -i ppp0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.254
iptables -t nat -A PREROUTING  -i ppp0 -p udp --dport 88 -j DNAT --to-destination 192.168.2.254
iptables -t nat -A PREROUTING  -i ppp0 -p udp --dport 3074 -j DNAT --to-destination 192.168.2.254
iptables -t nat -A PREROUTING  -i ppp0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.254
iptables -A FORWARD -i ppp0 -d 192.168.2.254 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i ppp0 -d 192.168.2.254 -p udp  -m multiport --dports 88,3074 -j ACCEPT

The router wan port is set as static 192.168.2.254 and gateway 192.168.2.1

on the lan side the router sits as 192.168.3.1 and gives out addresses with its dhcp server as 192.168.3.x

printing was solved by connecting to 192.168.3.1:631 and turning on ipp (internet printing protocol)

now for my real problem which is nfs sharing I have most of my media on the pc which is sharing the internet connection to the rest of the lan via my router. 

so what I want to be able to do is mount a share eg 192.168.2.1/media/mymedia 

and mount it at 192.168.3.x/media/myshare

unfortunately i'm rather stuck at this point.
anyone know how to do this?
it's really the reverse of the usual situation where you want to access a share behind a nat'ed router (in which case you just set up port forwarding in the router)

---

### Post by blackest_knight on 2009-05-09
well i sort of managed it via a slightly different method

places>connect to server 
select ssh port 22 and the server address 192.168.2.1
user name and connect it asks for password and opens the remote file system 
I browsed to my media and opened a video its fast enough to watch over the lan with a wireless connection.

not quite what I was trying to do but it lets me do what I want :)
(access my media files)

---

### Post by blackest_knight on 2009-05-10
heres an interesting alternative to nfs 

sudo apt-get install sshfs
sudo adduser $USER fuse (change to your username on local system)


sshfs $user@192.168.2.1:/media/sharedfolder/ /home/$user/anemptyfolder
(mounts the remote folder)
it may hang for a few seconds before asking for your remote users password


fusermount -u /home/$user/anemptyfolder/
(and this unmounts the folder )

the interesting thing is that the remote system isn't on the lan as such as its being used as a internet gateway sharing a 3g usb modem. so the ssh request goes via a router to the wan side and then to the ethernet port on the server. I've seen this done with named servers on a lan but its a lot simpler in this case just to use the ip address. 

Speed wise it's not bad i found with a wireless connection it was possible to watch a divX file stored on the remote system with no speed issues really (vlc dropped a few packets admittedly) 
also note that i picked a folder to mount. If i hadn't I'd have been mounting the whole file system of the remote system and quite possibly i wouldn't be able to read from any hard drives but the one holding root. 
(I think each hdd partition requires a separate mount command)
it's got interesting possibilities since very little needs to be set up in fact it all takes place on the client machine. and as long as ssh server is running on the server you can mount anything any time. 

if you have a few systems you could mount every system you own on to your local systems file system. kind of cool having so much storage on a device with just a few Gb of its own. 

Only failure I found was Amarok was very broken and wouldn't play any mp3's from the network , rhythmbox works nicely and you can start playing once its found a few mp3's and still scanning for the rest. 

Easiest file sharing ever, all done on 9.04 jaunty

obviously if you have ssh access to a remote server on the real internet you can do the same (as long as ssh is port forwarded on the natted remote router it'd work, however it's liable to be subjected to regular attack and if they crack your username and password that system is owned if the password is the same as the sudo password. 


take a look at [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) to see how to use ssh without a password and make this safer.

---

