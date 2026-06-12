---
title: "I need to know how to folder share"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-05-05
Hey i have to comuters with 1 ethanet card each and a cable going to a hub and i need to share a folder i dont have a clue where to start can any1 help me

---

### Post by encompass on 2006-05-05
There are lost of ways to share your files...
SAMBA
FTP
SSH
NFS

I use ssh because it is secure and I don't care what one person or the other see's when they log me in.  But you will want to try SAMBA
Try this....
[http://ubuntuforums.org/showthread.php?t=114322&highlight=howto+samba](http://ubuntuforums.org/showthread.php?t=114322&highlight=howto+samba)

---

### Post by Herman on 2006-05-05
G'Day, Cam, Here's how I have my [SSH network ]("http://www.users.bigpond.net.au/hermanzone/p11.htm")set up with a router, I don't know whether it'll be much different with just a hub or not but I'd imagine it'll be much the same. Give it a go and let me know how you get along.
:D Regards, Herman

---

### Post by CameronCalver on 2006-05-06
hey i dont have openssh server in synaptic i only have the client? and im trying both your ideas

---

### Post by Slim Odds on 2006-05-06
[QUOTE=CameronCalver]hey i dont have openssh server in synaptic i only have the client? and im trying both your ideas[/QUOTE]

Add the "universe" repository

---

### Post by CameronCalver on 2006-05-06
Hey herman i get up to the bit where it says

 If I don't know the IP address for the computer I want to connect to, I can find out easily by typing the following command in 'terminal' of that computer.

 ifconfig

but when i type ifconfig this is what it says
broadband@Broadband:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:3B:E9:41
          inet6 addr: fe80::20f:eaff:fe3b:e941/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:70182 (68.5 KiB)  TX bytes:51257 (50.0 KiB)
          Interrupt:21 Base address:0xa000
it does not say the ip??

---

### Post by CameronCalver on 2006-05-06
nah every time i go to network then change it from dhcp i cant get internet so how do i share folders????? i dont think any1 can help me lol all i want to do is have a file called share and have it so both computers can add files and delete files

---

### Post by neouser99 on 2006-05-06
how about some more information shall we?

are the computers connected to the internet? or are they just two standalone connected to a hub?
what os are they both running?

-neo

---

### Post by Herman on 2006-05-06
ifconfig doesn't give you an IP address? Well I what happens if you give both computers a static IP address then?
I'm not sure if you'll be able to use your LAN and have internet access at the same time or not under those conditions. I'm a bit spoilt having a router. Maybe you'll need to unplug the internet and set static IPs every time you want to use your LAN?
Then go back to DHCP when you plug into the internet again?
Maybe someone else with a switch can chime in here and tell us how they do it..
Or just try a few ideas like that find out. It shouldn't be too hard.
Regards, Herman.:D

---

### Post by neouser99 on 2006-05-06
[QUOTE=Herman]ifconfig doesn't give you an IP address? Well I what happens if you give both computers a static IP address then?
I'm not sure if you'll be able to use your LAN and have internet access at the same time or not under those conditions. I'm a bit spoilt having a router. Maybe you'll need to unplug the internet and set static IPs every time you want to use your LAN?
Then go back to DHCP when you plug into the internet again?
Maybe someone else with a switch can chime in here and tell us how they do it..
Or just try a few ideas like that find out. It shouldn't be too hard.
Regards, Herman.:D[/QUOTE]

umm... yea, this is quite confusing and you lost me.

-neo

---

### Post by CameronCalver on 2006-05-06
ok then here is the info
the internet box
Running breezybadger has a etho card and a network cable going to a 8 port ethenet switch(hub) it has a eternal modem 28.8k dial up and i would like to share a folder and internet does not matter if i cant share both at same time though it would be better

other computer

runnimg breezybadger has etho card and a network cable going to the hub i want this computer to be able to access the share folder and internet 

and thanks ever1 for helping out it is appriciated (if thats how you spell it )

---

### Post by neouser99 on 2006-05-06
ok, so what we need to do is get a static ip address setup on the two computers so that they can talk to each other. you should be able to share the files and possibly even the internet (this could get complicated, so we will worry about it later).

on the two machines, find out what eth card they are using (eth0), then type this command in
```

ifconfig eth0 down
ifconfig eth0 192.168.0.100 up

```
change the ip to 192.168.0.101 for the other computer. once we have this done, lets try to ping each other, so from 192.168.0.100 type
```
ping 192.168.0.101
```
and vice versa.

let me know if we get this far and we can keep going.

-neo

---

### Post by CameronCalver on 2006-05-06
lol it did not work this is what came out

broadband@Broadband:~$ ifconfig eth0 down
SIOCSIFFLAGS: Permission denied
broadband@Broadband:~$ ifconfig eth0 192.168.0.100 up
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
broadband@Broadband:~$

---

### Post by neouser99 on 2006-05-06
my bad...

tack on a sudo before each command

-neo

---

### Post by CameronCalver on 2006-05-06
this is the output

broadband@Broadband:~$ sudo ifconfig eth0 down
Password:
broadband@Broadband:~$ sudo ifconfig eth0 192.168.0.100 up
broadband@Broadband:~$

---

### Post by neouser99 on 2006-05-06
yep, and if you were to type just plain ifconfig it would show the ip of eth0

so do it on the other machine, change the ip address (increment it), and see if they will ping eachother.

-neo

---

### Post by CameronCalver on 2006-05-06
hey we will call the internet machine box 1 and other machine box 2 ok now what do i do on box 2

---

### Post by neouser99 on 2006-05-06
ok, run those same commands on box two using the ip 192.168.0.101

then use the commands that i put above on how to ping each other.

-neo

---

### Post by CameronCalver on 2006-05-06
hey i did that thing on box 2 and it did the same as box 1 exept instead of 192.168.0.100 i did 192.168.0.101 and then i ping each other and they both said send ing 64 kb blah blah and heaps of lines kept apearing now what

---

### Post by neouser99 on 2006-05-06
cool... so what method do you want to share stuff with??

the easiest (possibly) would be to just use nautilus and connect to everything using ssh, assuming that you have ssh installed. if you go to Places -> Connect to Server and choose ssh, then enter the ip address of the other box, so if you are on box1 enter box2's ip, and the login information is the same that you would use on box2.

-neo

---

### Post by CameronCalver on 2006-05-06
hang on i had something to eat im just doing that connect server thing

---

### Post by CameronCalver on 2006-05-06
is this right for box 1

serice type ssh

port : what do i type for port
folder /home/share
username:cameron
name:calvers lan 

do i do the same for box 2 or not and what do i do for port

---

### Post by neouser99 on 2006-05-06
the port is optional and only used if it is outside the default (22). did it connect?

-neo

---

### Post by CameronCalver on 2006-05-06
Hey at first this thing came up so i clicked log in anyway so i wrote the password in then it came up

Couldn't display "sftp://cameron@192.168.0.101:22/home/share".

im going for the night be back on 2  morrow still write back because i might check it

---

### Post by neouser99 on 2006-05-06
cool, it looks like it might be a permissions issue now, but were almost there. try changing the permissions on the 192.168.0.101 box of the /home/share folder to give cameron ownership, see what happens then
```
chown -R cameron /home/share
```

-neo

---

### Post by CameronCalver on 2006-05-06
i dont get what you meen to you meen go to the box 2 and set permissions of /home/share to write on all 3 things and go on the box 1 and do

 chown -R cameron /home/share 

say that last thing again coz i didnt get what you meant

---

### Post by CameronCalver on 2006-05-06
i forgot to say i want the shared folder to be on the box 1 (192.168.0.100) not box 2 so will i do the connect to server thing on the computer i want to have the shared file on or on the computer that is accessing the shared folder eg if i want the shared folder to be on the 192.168.0.100 do i do the connect to server thing on that computer or on the 192.168.0.101

---

### Post by Herman on 2006-05-06
Whichever computer you want the shared folder to be in (box 1 or 192.168.0.100 you say), should be the one with 'openssh-server' and 'ssh' transitional package installed with Synaptic.  All Ubuntu computers already come with ssh client software already, so you can connect any Ubuntu computer up to any server.

The server computer doesn't have to do anything, it just has to sit there and be available.
The client computer, (box 2 in your case), is the one you make the connection from, you just click 'Places', 'Connect to Server', in box 2, and fill out the fields.

Why don't you try filling them out this way and see what happens:
Service type: SSH
server: 192.168.0.100
Port: 22
folder: /home
username: cameron      (if that's your username for that computer)
name to use for the connection: calvers lan

I would think it easier to just try to establish a connection like that first and then worry about the shared folder later maybe.

---

### Post by CameronCalver on 2006-05-06
Yes Thanks Success!!!!!!!!

Thank you all for helping me now i am sharing yes 

one thing when i restart the computer i always have to write sudo ifconfig eth0 down then sudo  ifconfig eth0 192.168.0.10(0 or 1 depending on the computer) then it is right is there a way of saving it or so it sets that on startup

now for the bad part i need some help sharing external dial up internet (ppp)

so can some1 tell the the first step then ill do it then ill tell oyu how it  went and so on

---

### Post by Herman on 2006-05-06
> one thing when i restart the computer i always have to write sudo ifconfig eth0 down then sudo ifconfig eth0 192.168.0.10(0 or 1 depending on the computer) then it is right is there a way of saving it or so it sets that on startupWell mine always gets the icons on the desktop on each reboot and all I have to do is click them and type in my password. As long as you don't do a re-install or change the IP address or something that's all you need to do. Just don't delete your icons, leave them there and they should re-appear on every start-up.

If you ever do make a  major change to one of them, just delete your .ssh folder by clicking 'View', 'show hidden files', in your /home/username folder, and delete the .ssh folder, and delete it out of your rubbish bin too to make sure it's really gone. A new one will automatically be created for fresh connections to be made. You might have to repeat just some of what you just did then.

As for sharing your intenet connection, all I used when I had dial-up was get another bit of old spare telephone type wire and plug both computers into the phone line with a three way joiner from the local hardware store. Those only cost a couple of bucks and are quite common. You'd need a dial-up modem in both computers, but most computers come with those anyway. Maybe yours isn't working or something? I'm getting sleepy now, I'll think some more and see if I have any ideas unless someone else does before me. I'll check in the morning and see how you're going, all the best with it. Regards, Herman.

---

### Post by neouser99 on 2006-05-06
[quote=CameronCalver]Yes Thanks Success!!!!!!!!

Thank you all for helping me now i am sharing yes 

one thing when i restart the computer i always have to write sudo ifconfig eth0 down then sudo  ifconfig eth0 192.168.0.10(0 or 1 depending on the computer) then it is right is there a way of saving it or so it sets that on startup

now for the bad part i need some help sharing external dial up internet (ppp)

so can some1 tell the the first step then ill do it then ill tell oyu how it  went and so on[/quote]

yes, you can setup the computer to have the static ip set after reboot, without typing the command line in. you have to set it up on the /etc/network/interfaces. unfortunately i am on my winblows box right now and and unsure of the syntax. if someone else coule post how to do a static ip, that would be great, otherwise i'll get back to you the next time i boot into ubuntu.

-neo

---

### Post by CameronCalver on 2006-05-06
This is what it says what do i change

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp



iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0

---

### Post by Herman on 2006-05-06
>  if someone else coule post how to do a static ip, that would be great, Cameron should be able to see that if he looked in the link I gave back in [post#3]("http://www.ubuntuforums.org/showpost.php?p=988182&postcount=3")
of this thread, there's an illustration and everything, (see fig5).
I just wasn't sure if it'd be much different without a router, but so far the procedure seems much the same.
However, with a router he'd be able to connect both computers to the internet if he had broadband. I don't know yet if both computers have a dial-up modem that works or not, but at least now he can share whatever files through SSH that he might download and pass them from one box to the other.
I have heard of people setting up a Linux gateway computer or server for use something like a router only better but I think the posts I've seen asking for help with that had broadband and I think they needed two ethernet cards for that but I'm not sure. Maybe there is a way to get box2 access to box1's dialup modem? 
I'll start a forum search for info on that now, but if both computers have a working dial-up modem, Cameron, they should be able to be teed together with the p0hine wires very easily, using standard hardware store wiring fittings. But that would be no challenge and not as much fun as trying to see if we can do it the hard way. :D Regards, Herman

---

### Post by CameronCalver on 2006-05-06
I dont get it all i want is so it remembers all the stuff after each boot like the 102.168.0.100

---

### Post by Herman on 2006-05-06
Yeah, it's real *simple* just look at the picture, you go 'System', 'Administration', 'Networking', and then on the 'Network settings' panel, like it shows in the picture in t[his link here]("http://www.users.bigpond.net.au/hermanzone/p11.htm") (again), see figure 5, and just set it to 'Static IP', and your IP address. Easy!

Now what I'd like to know for sure is what happens if you type in the other computer (box 1's IP in the field for 'gateway IP')?
 So far I have discovered that it will change your file that you had open already, (the /etc/network/interfaces one). 
I'm not sure as I haven't tried this before myself, but for me, I type the IP to my router in that field. I want to look this up in a forum search and see if that's what other people do or not first though, unless neo knows. That might be how to make your box2 connect to the inernet through box1 like we want.
 :D Regards, Herman.

---

### Post by CameronCalver on 2006-05-06
Nah if i change it from dhcp to static ip it does not let me access the internet so i must have to type those things in every time

---

### Post by CameronCalver on 2006-05-06
Ok Now for internet sharing neo can you help or any1 can help as long as the know what they are doing

---

### Post by Herman on 2006-05-06
[Here's a thread]("http://www.ubuntuforums.org/showthread.php?t=167616&highlight=set+gateway+IP+address") for something like this but for making a Ubuntu computer connect through a WIn XP box with dial-up, that's not too Much different form what we're tyring to do and setting the gateway field to the box1's IP seemed to be the answer in that one.
[ Here's another thread]("http://www.ubuntuforums.org/showthread.php?t=148392&highlight=share+dial-up+connection") with the same question but a completely different solution that worked! This one uses firestarter to select' share the internet connection, see Alamba's post, (#7) in that thread.
I'm still searching, but those are some encouraging results so far.

---

### Post by CameronCalver on 2006-05-06
you know how you said set the ip and the gateway do i do that on the computer with the internet or the comouter that wants the internet

---

### Post by CameronCalver on 2006-05-06
hey i set up firestarter on both comps and every now and then i get 0.1kbs from etho but i still can get the intenrte on mozilla?

---

### Post by Herman on 2006-05-06
> you know how you said set the ip and the gateway do i do that on the computer with the internet or the comouter that wants the internet We set up the one that connects to the internet with the SSH Server software because it's the one that can connect to the internet to download and install the software into.
Now it's a bit of a problem because the SSH Server needs a Static IP for the LAN but for the internet connection you need DCHP for your ISP's roving IP to the outside world.
Hmmm...
Maybe we'll need to set box 1 back to DCHP for now, and sort out the internet sharing first by trying alamba's solution (post#7) in the  second link my last post, then when box 2 has internet access install SSH Server in box2 and then just have a static IP for that one.
> Ok Now for internet sharing neo can you help or any1 can help as long as the know what they are doing Sorry to be mucking you around a bit, I'm trying to help, but I don't know it all yet, I'm learning at the same time. We're getting there aren't we? (I hope) Regards, Herman

---

### Post by CameronCalver on 2006-05-06
ok so box 1 has internet it has the ssh server and it has dhcp and box two wants to get internet it has static it and i set the gateway 192.168.0.100 which is the internet boxes ip and on box 2 firestarter is saying active connections 

192.168.0.101 as source destination 192.168.0.100 which is right then port 22 then service ssh but has another connection 
source127.0.0.1 destination 127.0.0.1service ipp when i click look up hostnames instead of 127.0.0.1 it is localhost.localdomain and it says that on box 2 aswell is that anything

and box 1 has the internet it has the ssh but i cant download open ssh server on box 2 coz it doesnt have the internet but i i set the static ip

---

### Post by CameronCalver on 2006-05-06
Yes i have internet on both comps yes i had to change the dns on box to to my isp ip

---

### Post by CameronCalver on 2006-05-06
thank you all i have made a thread for file sharing called HOW To-File sharing for n00bs and  i would like to find out how to make it a sticky

and all i need now is it so it saves the network settting so i dont have to ifconfig eth0 every time

---

### Post by Herman on 2006-05-06
> Yes i have internet on both comps yes i had to change the dns on box to to my isp ipGood, okay, now we're getting there! 
Now that you have the internet on box 2, if you want install SSH Server in box2 now instead. Just forget about the SSH Server in box1, leave box1 as DCHP and set box2 with the static IP number and make your SSH connection from box1 to box2 instead.
So you should then have internet access and SSH Network as well then I hope. (fingers crossed). Regards, Herman. :D
Oh, and thanks for your patience, and thanks to neo too.

---

### Post by CameronCalver on 2006-05-06
Ok i have ssh and internet but what do i have to to so it saves and when i reboot i will not haveto write it all in again i meentheifconfigsuff

---

### Post by Herman on 2006-05-06
Okay, box 1 is the one you are connecting to the internet with so it has DCHP now, and it's the SSH client. You make the SSH connection from box 1 to box2, which is now the SSH Server, right so far?
So there's an icon on your box1 desktop called 'calvers lan', if you don't delete that it should re-appear there at each re-boot automatically.

Now, it took all three of us to sort all this out, neo's method was one way to do things, by editing the files directly, that's the right way to do things, and shows he knows what he's doing.
My way of doing things, using the GUI tools to alter the files for me, is just another way of doing the same thing, but I don't necessarly really know what I'm doing exactly, using GUI is a cheat's way. If you look at your /etc/network/interfaces file before you set your static IP address by the GUI method I suggested and then again afterwards, you will see what you could have typed in there to do it manually, which is what neo was about to suggest. I didn't know about the /etc/network/interfaces file before. As long as the information is written and saved on that file your SSH icon should be usable after each re-boot, it doesn't matter whether you do that by the GUI method or manually. But it should re-appear each re-boot regardless of whether it's any good or not.

What I'd like to know is what files get changed with alamba's firestarter solution to the internet connection sharing problem.

---

### Post by CameronCalver on 2006-05-06
no thats  not right ok the intenet connection is on box 1 and i have the ssh server on box 1 because thats our main computer and i have the lan icon on box 2 but even if i restart the computer it is still there but when i click on it it will say could not find //192........ so to get it to work i have to go ifconfig eth0 down then ifconfig eth0 192.168.0.10X on both computers then it will work

---

### Post by Herman on 2006-05-06
> click on it it will say could not find //192........ so to get it to work i have to go ifconfig eth0 down then ifconfig eth0 192.168.0.10X on both computers then it will work We originally installed SSH Server on box1 because at the time, box1 was the only one that could connect to the internet in order to install the SSH Server software, and we hadn't planned ahead far enough to realize that it would interfere with box1's connection to the internet, which must be DCHP in order to connect up to your ISP, which gives you a roaming IP address for the internet.

Now that we have the internet connection part of things solved, we need to scrap the idea of having box1 set up as the SSH Server, (because that requires a static IP as opposed to DCHP for your ISP's roaming IP address). Box1 will have to be the SSH client from now on, and we'll need to make box2 the SSH Server now instead.
Now that you can access the internet with box2, (via box1), if you can install SSH Server through synaptic in box2. We didn't know how to do that before. Box 2 doesn't need DCHP, because it doesn't connect to the internet directly. So set box2 with the static IP. You'll be able to make a new SSH connection from box1, (Your new SSH Network icon will appear in box 1, you can 'unmount the volume' by right-clicking the icon in box 2 and it will go away).
Then you should be right. :D Regards, Herman.

---

### Post by CameronCalver on 2006-05-06
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

and i dont get all the download eg in thegames i get barley any and nroamlly you get heaps

---

### Post by CameronCalver on 2006-05-06
whats this error mean in synaptic

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

and i dont get open ssh server

---

### Post by Herman on 2006-05-06
Have you got an internet connection from box 2 for everything else? Like normal internet use I mean?
If you have a normal internet connection you should be able to get SSH Server and SSH transitional package without even enabling extra repositories, but by the looks of what you've just posted, you aren't able to connect to very much at all. At least not as far as repositories go. I've never seen that happen before except with the internet unplugged.

:confused: (Herman)

---

### Post by CameronCalver on 2006-05-07
when i copy files it says permision denied so i went on the computer i was accesing and when onto the home folder and set permissions to write for owner and group and unclicked all of the things on others

Then when i restart then i log in and these are the errors

Your home directory listas as /home/broadband but it does not appear to exist do you want to log in with the (root) directory as your home directory

then i click yes and this comes up

your $home/.dmcr file has incorrect permissions and is being ignored this oresent the default session and launguage from being saved.
File should be owned by user and have 644 permissions

then a thing comes up saying this session lasted less then 10 seconds i read the error it says
gnome-session 8139 lib gnome ufs warning unable to create ~/.gnome2 directory permission denied /home/broadband.gnome2. permission dennied

i can only log into the terminal only does any1 know what i should do to fix it

---

### Post by Herman on 2006-05-07
I'm not sure I understand exactly what you are doing. Which computer are you connecting to and which are you making the connection from?
Did you get access to the internet and especially the repositories okay yet from box 2?
Are you connecting from box 1 to box 2 by SSH? 

I have no idea what a /home/broadband directory would have to do with anything or a $home/.dmcr file, I don't have those in any of the computers I have here. Please explain more so someone will know how to help, thanks.
:confused: (Herman)

---

### Post by CameronCalver on 2006-05-07
ok i could not acces some of the files on box 2 the one with ssh client to i changed the permissions of /home on box 1 and now on box 1 i cant login it  says this

Your home directory listas as /home/broadband but it does not appear to exist do you want to log in with the (root) directory as your home directory

then i click yes and this comes up

your $home/.dmcr file has incorrect permissions and is being ignored this oresent the default session and launguage from being saved.
File should be owned by user and have 644 permissions

then a thing comes up saying this session lasted less then 10 seconds i read the error it says
gnome-session 8139 lib gnome ufs warning unable to create ~/.gnome2 directory permission denied /home/broadband.gnome2. permission dennied

is there nay way i can keep all my stuff and reinstall ubunty but keep all partitions and all my stuff

---

### Post by Herman on 2006-05-07
There are lots of ways to rescue files. The easiest would have been if you had SSH Server installed in box 2 already, you could run a Live CD and mount box 1's filesystem and make an SSH connection to box 2 and transfer all your files to box 2 that way.

What about booting box 1 in resue mode? If you are not dual booting you might not normally see a grub menu. See fig 1 on [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") to see a picture of what I mean. You should be able to get a grub menu by pressing your 'Esc' at the right instant during boot-up. You might have to be quick, and you might need to try several times to catch it.
From the GRUB menu, select 'recovery mode', (the second line down usually). 
The main  idea is to get one of those black screens like a terminal with white typing and a #_ prompt (root prompt).
If you type ```
# cd /
```from the root prompt, and then ```
/# ls
``` you should see all your main directories.  

Try doing ```
/#ls -l /home
``` and that should tell you what file permissions you have set for /home/cameron if that's what you call your /home/username folder. 
Mine has: > drwxr-xr-x 54 herman herman 4096 May 7 17:09 herman Yours should be something similar, but not the same. 

 To try to make it have the same 'drwxr-xr-x', part,try this, ```
/# chmod 0755 /home/cameron
```and then try the ls -l command again to see if that did anything. If it works, exit and reboot and see if that fixed it. I hope that helps, I'm not an expert with this. Here's a nice link about the [chmod command]("http://en.wikipedia.org/wiki/Chmod") too, in case it's any help.

---

### Post by CameronCalver on 2006-05-11
hey until today i could not even get past the grub it said error 16 so i did a reinstall but when i try to connect to internet from dial up modem it says 

Gnomepp stderr  ppp negotiation started
""          ""          starting ppd at thurday may 11 17:58:00 2006
""         ""            pid of pppd:8776
""        ""            pppd:z
""        ""            using internface ppp0
""       ""            ppd:z
""       ""           ppd:z
""       ""           ppd:z
""       ""           ppd:z
""       ""           ppd:z
""       ""           ppd:z
""       ""          disconecting at thur may..........
""       ""          the ppp daeman has died:authentication error
""       ""          we failed to athenticate ourselves to the perr
""       ""          mabe nad account or password (exit code:19)
""       ""           man ppd explans pppd error codes in more detail
""       ""           i gues thats it for now,exiting
""       ""           the ppp daeman has died (exit code = 19

does any1 know how to fix that

---

### Post by encompass on 2006-05-11
according to the error, it sounds like you don't have the username and pass correct.  Did you double check that?

---

### Post by CameronCalver on 2006-05-13
yes

---

### Post by encompass on 2006-05-14
And did that fix the problem?  or not...

---

### Post by CameronCalver on 2006-05-16
no doesnt matter im getting broadband

---

### Post by CameronCalver on 2006-05-18
Hey i have another problem ok

i got broadband recently and  it is a zyxel p660ru and i can get it to work if i click dhcp in networking but i cant get it to with static so what do i do to get it to work with static ip

---

### Post by encompass on 2006-05-18
First thing... um, I think your post like this would be more effective if you started a new post about it.
Secondly, you have a network router that you got with your service? if so, and what ever it is... it has an instruction manual.  It would probably work alot better to read that, then to try to ask us.

---

### Post by CameronCalver on 2006-05-19
ok thanks for the advice but it does not say that in it

---

