---
title: "A LAN between a wifi connected laptop and a wired PC"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Josep CA on 2011-07-09
Hi,
I have an Ubuntu laptop connected by wifi to a Cisco router and a desktop Ubuntu PC conneted by wire to the same router. I would like, if it's possible to connect them without using the Internet (I mean what I want it's not just communicate between them using SSH over the Internet, for instance, but also communicate without connecting to the Internet). My DSL connection it's 4 Mb/s while my router can work up to 100 Mb/s so I would like to take advantage of these 100 Mb/s to transfer files between the two computers instead of using 4 MB/s.
Any help will be appreciated.

Thanks! :KS

---

### Post by spiky001 on 2011-07-09
You can connect via ssh etc without going on the internet, All is done on local lan, I take it that is what you mean?

---

### Post by ajgreeny on 2011-07-09
Judging by my experience, I very much doubt that you will get 100Mb/s using ssh.  I have a fast but never get ssh speeds anywhere near the LAN maximum, and I have seen many, many posts with the same problem.  It is of little consequence to me as I use it so seldom, and speed is not important form what I need to use it, but I gather that using NFS may be much faster, though more of a palaver to set up.

I have never tried NFS, so have no experience of it, nor its speed, but I suggest you read all about it and try that, as well as ssh.

---

### Post by Josep CA on 2011-07-09
Thank you for your replies. I am more interested in a technology like shh than in NFS because I'm interested in being able to log in my computer remotely in my house. However I didn't know about NFS and it's a good resource maybe I try to implement it in the future.
Anyway I've done some research about it and I will try to use ssh and change the routing tables of my router to use it through a LAN I don't know if it will work. I will post the results.

Cheers.

---

### Post by ajgreeny on 2011-07-09
Setting up an Ubuntu only home network
If you just want full access to both machines from each other, this is so easy it`s embarrasing.
```
sudo apt-get install openssh-server openssh-client
```
on both machines.
On each machine right click on the network icon and choose connection information.  Note down the ipaddress of each machine.
Then in your menu, go places > connect to server.
In the top box choose ssh
In the next box type username@ipaddress_of_other_computer.
Put a tick(check) in the add bookmark box.
Choose a name for the other computer.
Click connect.
Type the password of the other machine.
Check the remember password forever box.
Repeat process on the other machine.
You will now have a bookmark in your places menu, on each machine that will give you full access to the complete filesystem of the other computer.

There is also a lot of info on this page about increasing your security when using ssh. [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)  

In fact to make things even safer, I don't even start the ssh-server at boot time.  I have edited the /etc/init/ssh.conf file by commenting out the line ```
[COLOR=Red]#[/COLOR] start on filesystem
```I can then start ssh server when I need it with the command ```
sudo service ssh start
```and stop it with ```
sudo service ssh stop
```both commands having speedy aliases set (ssh+ and ssh-).  Perhaps I'm just a bit paranoid, but I feel happier that way.

I will be very interested to hear what sort of speed of transfer you manage with ssh, so please let us know how it works for you.

---

### Post by Josep CA on 2011-07-10
Thank you for your tips *ajgreeny*! Finally I've created an Open SSH server in my desktop computer and I use my laptop as a client. There has been no need to modify my routing table since all the connections inside my local network are already forwarded in direct delivery. You can check it by typing this in the command line:
```
ip route show
```
I use SSH [keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for greater security . This [tutorial]("https://help.ubuntu.com/community/SSH") has been a great help too.
Everything seems to work fine now.

Your help has been really appreciated ans useful thank you!

Cheers! :popcorn:

---

