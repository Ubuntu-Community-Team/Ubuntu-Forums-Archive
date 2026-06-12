---
title: "HOW TO: Easy Folder Sharing For Noobs"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-05-06
Hello i had a big problem which i solved over time it was, 

I had 2 breezy boxes with ethenet cards in them going to a hub and i wanted to share folders and whole hard drives i have solved it and this is a very easy How to.

1. getting the right software go onto synaptic package manager if you dont no how it is  System--Administation--Synaptic then type your password in and go Networking then look for openssh-server NOT the client if it is not there which is wasnt for me i when in synaptic settings--repositories--Add--then tick comunity maintaned universe then click ok it should then reload if it doesnt click reload then look for openssh-server and it should come up mark it for installation then when its finished let it install then quit synaptic.
F
2 Now to assign Ip addresses open up a terminal and type

sudo ifconfig eth0 down

then

sudo ifconfig eth0 192.168.0.100 up

ok from now on this computer has an ip address of 192.168.0.100 and i will call it box 1 

now for the second computer which i will call box 2
type in a terminal

sudo ifconfig eth0 down

then

sudo ifconfig eth0 192.168.0.101

now lets try to contact each other on box 1 type ping 192.168.0.101
while its pinging lines should be apearing and looking simular to this

broadband@Broadband:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.130 ms
64 bytes from 192.168.0.101: icmp_seq=2 ttl=64 time=0.130 ms
64 bytes from 192.168.0.101: icmp_seq=3 ttl=64 time=0.129 ms
64 bytes from 192.168.0.101: icmp_seq=4 ttl=64 time=0.126 ms
64 bytes from 192.168.0.101: icmp_seq=5 ttl=64 time=0.126 ms
64 bytes from 192.168.0.101: icmp_seq=6 ttl=64 time=0.185 ms

let it do about 5 or 6 to see if it is working then do the same on box two but instead of typeing ping 192.168.0.101 do 192.168.0.100 and it should look about the same.

3 Now you have a link you have to set the folder sharing on the computer without openshh server which should be box 2 go Places--Connect to Server
and fill it out like this

Change Server type to ssh 
where server is type 192.168.0.100
Port:22
Folder For Starting off type: /home then you can make another one to share a different file when you have finished
Name For Connection:Name that whatever you want to call it i did Lan.
Then Click connect then a box should come up and you click log in anyway
or it might just come up type your password and type your password for the computer you are trying to access if nothing comes up when you click connect go to the desktop and a icon will be there it will be called whatever you called it and you just double left click on it and then that should be everything.

Ok thats my thread on folder sharing for noobs and questions just reply and i will try and help you

,Cameron Calver

---

