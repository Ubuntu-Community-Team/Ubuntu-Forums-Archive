---
title: "MythTV remote telnet port for frontend"
date: 2009-05-18
forum: Mythbuntu
---

### Post by BjBlaster on 2009-05-18
Hi guys,

I can't see to work out why I can access the mythfrontend remote from local host but not on my home network using another PC or my iphone using the "MyMote" app.

If I ssh in remotely to the frontend machine I can control it ok as local host and I have the tick in the box to enable remote control like this:

```
bj@MythTV-Lounge:~$ telnet localhost 6546
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
MythFrontend Network Control
Type 'help' for usage information
---------------------------------
# 

``` 

but if I go directly to the IP address of the machine it doesn't have the port available.

```
bj@bj-laptop:~$ telnet 192.16.0.3 6546
Trying 192.16.0.3...
telnet: Unable to connect to remote host: Connection timed out
bj@bj-laptop:~$ 

```

open ports on frontend:

```
Starting Nmap 4.62 ( http://nmap.org ) at 2009-05-18 22:19 WST
Interesting ports on 192.168.0.3:
Not shown: 1712 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
6547/tcp open  powerchuteplus

Nmap done: 1 IP address (1 host up) scanned in 10.908 seconds

```

As you can see there is no access to remote port 6456, but there is if you are directly attached to the box in terminal or using ssh.

Is there some bind address or firewall settings in mythbuntu I am not aware of? ufw is disabled.

Thanks

Bj

---

### Post by tji on 2009-05-18
That's odd,  mine works fine with Ubuntu + Myth and Mythbuntu.   Checklist of items to verify:

- Make sure remote control port is enabled, it's off by default (obviously yours is on, because you can connect to it localhost)

- Make sure mythfrontend is actively running when you try to connect.  The control socket goes to the frontend, and is gone when the frontend exits.

- Check listening ports on local machine via "netstat -an | grep LISTEN".  There should be a line saying "tcp        0      0 0.0.0.0:6546            0.0.0.0:*               LISTEN".   In your case, this should definitely be there, because you can connect locally.  The 0.0.0.0:6546 is important, this means it's listening on all interfaces.   If it shows as 127.0.0.1:6546, it's only listening for localhost.  But, this should not be the case for the control socket, because it's inherently needing to accept remote connections.

- Is a firewall enabled on the frontend host?  "sudo iptables -L" will list the firewall rules.   The "INPUT" chain should be set to accept, if not, or if there is a complex policy, this could be blocking access.

---

### Post by BjBlaster on 2009-05-18
Thanks for the reply.

Well that is interesting the netstat shows:

```
$ netstat -an | grep LISTEN
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6546            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6547            0.0.0.0:*               LISTEN  

```

Which is good, and the iptables are:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

But when the frontend is running I still can't connect to it, and an nmap doesn't show this port as open still?!

Any other ideas?

Thanks

Bj

---

### Post by cschuhen on 2012-05-11
I'm not sure if you ever found the solution, I found this thread while trying to fix the same problem. After looking at the myth source code I realised that the answer was in the BackendServerIP. 

One would think that BackendServerIP would specify the backend server IP, but no, for the frontend, this parameter dictates what interface it listens on for a few services, including the remote network interface. I changed it to the the IP of the ethernet device on the front end and it all started working. From the code, I think that just deleting the parameter would have worked also.

As for where to edit/delete the parameter, you could edit the mysql database directly but I used mythweb instead. Go to settings(The key+spanner icon)->MythTV. You also need to make sure that you select which host you are editing the settings for.

---

### Post by Zorbitz on 2012-05-14
Thank you for bringing this old thread back to life, as it helped me getting mythmote to work. Instead of editing the DB directly, I used MythTV Backend Setup and edited both Local Backend IP and Master Backend IP.

I run a single frontend/backend machine, so these fields were set to 127.0.0.1. Changing them to my eth0 device IP made mythfrontend listen on both interfaces:

> 
tcp        0      0 192.168.1.3:6546        0.0.0.0:*               LISTEN      13183/mythfrontend.
tcp        0      0 127.0.0.1:6546          0.0.0.0:*               LISTEN      13183/mythfrontend.
I wonder why the frontend would listen on the loopback interface at all, except for testing purposes. Perhaps there should be an option in the frontend setup where you activate the network remote feature, that would allow you to tell what interface to listen on.

Anyway, all's well now, so thanks again. :)

---

### Post by nickrout on 2012-05-14
yeah i think it is quite annoying that myth defaults to localhost for almost everything. It makes it much harder when sopmeone who has been succesfully running a combined BE/FE system wants to run a remote FE.

---

### Post by zribiahmed on 2012-06-08
Hi,

I have the same problem with my iphone and Mymote application it dosen't connect to frontend.

In mymote application, the application discover automatically my backend and I entered the pin code (0000 in my case and it configured in backend interface), it can't connect to frontend.

Note: I use mythbunto distribution (mythtv 0.25)
backend and frontend are in the same server.

```
telnet 192.168.1.249 6546
Trying 192.168.1.249...
Connected to 192.168.1.249.
Escape character is '^]'.
MythFrontend Network Control
Type 'help' for usage information
---------------------------------
# help
Valid Commands:
---------------
jump               - Jump to a specified location in Myth
key                - Send a keypress to the program
play               - Playback related commands
query              - Queries
set                - Changes
screenshot         - Capture screenshot
message            - Display a simple text message
exit               - Exit Network Control

Type 'help COMMANDNAME' for help on any specific command.
``````

netstat -an|grep LISTEN|grep :6546
tcp        0      0 192.168.1.249:6546      0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:6546          0.0.0.0:*               LISTEN
tcp6       0      0 ::1:6546                :::*                    LISTEN

```Thanks in advance

---

### Post by fforw on 2013-04-26
Just for the sake of other people with this or a similar problem.

The problem seems to be that the network control is listening on the wrong port, it only listens on 127.0.0.1 and the ::1, which will then make it not react to access from the local IP. (192.16.0.3 in this case).

For some reason, this seems to be connected to the mythbackend settings. I had the same problem which I solved by changing the IP settings in mythtv-setup. If I define the backend IP and master backend IP to by my local IP (192.16.0.3 in this case), the mythmote network control starts to listen on all three of 127.0.0.1, ::1 and the local IP. Then I can access it normally from other computers / mobiles in my LAN.

---

### Post by nickrout on 2013-04-26
Just another reason why friends don't let friends run mythtv on localhost :)

---

### Post by linuxhippy on 2013-05-29
that's interesting...I've been having problems with mythmote not being able to access my mythbuntu 12.10 and now 13.04 machine.  It worked fine in mythbuntu 11.10, though.  So I need some particulars.  How do you specify that it listens on 3 addresses?  Since you have 2 fields, do you just separate 127.0.0.1 with a comma in the backend so it looks like this (my local IP is 192.168.2.3):

127.0.0.1, 192.168.2.3

And leave the next field as ::1??

---

### Post by nickrout on 2013-05-29
You don't need it listening on localhost at all.

---

### Post by linuxhippy on 2013-05-29
Didn't work for me.  My backend and frontend are on the same computer.  When I take out 127.0.0.1 from the backend setup then the frontend gives a bunch of error about how it needs 127.0.0.1.  Maybe I could put 2 IP addresses in that field separated by a space or a comma like this:

127.0.0.1 192.168.2.3

---

### Post by nickrout on 2013-05-30
You need to set the frontend to use the real ip address as well.

---

### Post by purza on 2014-04-17
FYI:  w/ Mythbuntu/ MythTV Frontend/ Backend same PC IP 127.0.0.1 I couldn't telnet 127.0.0.1 6546 until I set the Security Pin to "0000" on the backend under **Host Address Backend Setup**.  Connection was refused otherwise and the port didn't show up as "Listen"

 [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup)

---

### Post by purza on 2014-04-17
Linux noob (on an almost vertical climb - taking a breather) 

Anybody Still Looking at this thread? - when I change all the IP addresses on my My backend and frontend from 127.0.0.1 (Frontend/Backend same pc) to my reserved (on router) 192.168.0.19 have errors when rebooting and Frontend won't see Backend etc
If I change it back it works normally, but I can't get MythRemote on my iOs 5s to connect and I can't - telnet 192.168.0.19 6546

name@MyHTPC:~$ telnet 192.168.0.19 6546
Trying 192.168.0.19...
telnet: Unable to connect to remote host: Connection refused

Though as posted above I can telnet to the loopback interface.

I'm running clean install Mythbuntu 0.25 Ubuntu 12.04 precise LTS w/ Ceton infiniTV PCIe 4

Any Assistance would be greatly appreciated.

---

### Post by linuxhippy on 2014-04-17
here's what I did in the mythtv backend host address backup screen (general):

Find out the IP address your router gives mythtv with ifconfig.  Mine is defined in my router to give a static address of 192.168.2.9 and then enter it.

IP address: 192.168.2.9
IPv6 address: ::1
Port: 6543
Status port: 6544
Security PIN: 0000
Master Backend
IP Adress: 192.168.2.9

I think I just had to change the IP address in 2 places on that page.

Port: 6543

---

### Post by purza on 2014-04-17
Linuxhippy,  thanks for the quick reply.  I essentially did just that and received errors on boot up and then Front end doesn't see Back end.

[SIZE=2][FONT=arial][COLOR=#000000]IP address: 192.168.0.19
[/COLOR][COLOR=#000000]IPv6 address: ::1
[/COLOR][COLOR=#000000]Port: 6543
[/COLOR][COLOR=#000000]Status port: 6544
[/COLOR][COLOR=#000000]Security PIN: 0000
[/COLOR][COLOR=#000000]Master Backend
[/COLOR][COLOR=#000000]IP Adress: 192.168.0.19

On my front end I entered the same IP 192.168.0.19

When I reboot I believe I was prompted for "Language" (big colorful screen) - chose "english"

Then the next screen, I believe, was the Database setup screen for the MythFrontend, but not totally sure.  I thought I recalled some sort of "ping" test.  I will have to check it again when I get a chance.  ( feel like one of my customer -  me, "did you write down the error code on the screen?"  Customers, "No, you need that?" :) )

[/COLOR][/FONT][/SIZE]

---

### Post by linuxhippy on 2014-04-17
sorry that didn't work.  The only thing I can think of that you may need updates.  I actually re-installed my entire system a couple months ago to 12.04.4 a couple months ago...previously I just had 12.04 which maybe u have now?  To get things back the way they were, just put the local address of 127.0.0.1 in the same place in the backend in two spots on that screen.

---

### Post by blm-ubunet on 2014-04-17
> [SIZE=2][FONT=arial][COLOR=#000000]When I reboot I believe I was prompted for "Language" (big colorful screen) - chose "english"
[/COLOR][/FONT][/SIZE]
This means mythtv can not contact mysql server.

Possible reasons:
- The contents of /home/mythtv/.mythtv/config.xml file are important; used to find mysql server, credentials etc.
The FE user can (obviously) have a different home folder.
If this file is missing myth looks into /etc/mythtv somewhere..

- mysql server is not running (not likely)
- mysql server is not setup to listen on external (non link local) IP addresses.

The initial mythtv configuration of combined BE-FE on link-local IP just leads to so many problems.

Strictly, the remote control port is not "telnet".
Can just use netcat.

---

### Post by purza on 2014-04-17
linuxhippy, Sorry, couldn't remember entire release, but I am runing 12.04.04 LTS.  I haven't done any of updates yet, afraid it may break the system more than it is now.  I did change the IP addresses back and it is working.  Thanks again.

---

### Post by purza on 2014-04-17
[FONT=arial][SIZE=3]blm-ubunet,

Thanks for the info.  This is probably the root of the problem.  Now for some more climbing up the learning curve.[/SIZE][/FONT]

---

### Post by purza on 2014-04-17
Below is the copy and paste of my directory /.mythtv and the cat of the config.xml file after changing the ip address back to the loop back.  Is the problem with the user and group privileges and/ or the fact that the IP address doesn't change in the config.xml file when I change it in the back end setup?  I won't be able to check this until I have free time on Sat EDT-US

- very, very much appreciate all that actually help in these forums.  I hope to contribute more and more in the future once I learn how to walk better.   

```
pixpurz@MycroftHTPC:/home/mythtv/.mythtv$ ls -latotal 32
drwxr-xr-x 8 mythtv mythtv 4096 Apr 16 20:44 .
drwxr-xr-x 5 mythtv mythtv 4096 Mar 24 18:25 ..
drwxr-xr-x 2 mythtv mythtv 4096 Mar 17 21:45 3rdParty
drwxr-xr-x 4 mythtv mythtv 4096 Mar 17 21:44 Cache-mythbackend-MycroftHTPC
drwxr-xr-x 4 mythtv mythtv 4096 Apr 16 20:44 Cache-mythfilldatabase-MycroftHTPC
drwxr-xr-x 2 mythtv mythtv 4096 Mar 17 21:45 channels
lrwxrwxrwx 1 root   root     22 Mar 17 21:29 config.xml -> /etc/mythtv/config.xml
lrwxrwxrwx 1 root   root     21 Mar 17 21:29 mysql.txt -> /etc/mythtv/mysql.txt
drwxr-xr-x 2 mythtv mythtv 4096 Mar 17 21:45 themes
drwxr-xr-x 4 mythtv mythtv 4096 Apr  2 19:01 tmp
pixpurz@MycroftHTPC:/home/mythtv/.mythtv$ cat config.xml
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <!--
Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.


NO TWO HOSTS MAY USE THE SAME VALUE
-->
        <DBHostName>127.0.0.1</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>DQ7HJ8HA</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>



```

---

### Post by blm-ubunet on 2014-04-19
I think the file /home/<user>/.mythtv/config.xml is only automatically generated from the first time mythtv-setup is run..

AFAIK If mythtv combined FE/BE is setup on link-local IP addresses then the FE remote control port will not work from external IP.

If you want to use remote FE (or slave BE) you have to get mysql server to listen on real IP addresses (& not just link-local).
You have to ensure the correct mysql DB (mythconverg) privileges are granted to appropriate IP ranges.
Then you can reconfig mythtv to real IPs.
- stop mythbackend
- run mythtv-setup
- check contents of config.xml

---

### Post by purza on 2014-04-20
I re-configured Myth FE and BE for my local IP 192.168.0.19 (which I have reserved on my Motorola Surfboard Cable Modem Router).

FE - Setup - General - pg 1/2 Hostname: 192.168.0.19 

BE - General - Local BE (MycroftHTPC) IP Address: 192.168.0.19 -- Master BE IP Address: same 192.168.0.19

I checked my /home/.mythtv/config.xml file and the IP address was changed correctly.

```
pixpurz@MycroftHTPC:~/.mythtv$ cat config.xml<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.19</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>DQ7HJ8HA</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
    <UDN>
      <MediaRenderer>{c7cb8016-b747-410e-8651-bab3245274c</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>
pixpurz@MycroftHTPC:~/.mythtv$ 
```

Next, went into FE to recheck and the received message below.

"could not connect to Master BE server. Is it running? Is the IP address set for it in mythtv-setup correct?"

It then disappeared on it's own.  Went into Live TV - it works.  Expected to get "tuner cards are busy" or something to that extent.  I could watch a live channel no problem (FYI:  using Ceton infiniTV PCIe Card [http://www.mythtv.org/wiki/Ceton](http://www.mythtv.org/wiki/Ceton) ).  I then went back into my BE and the IP addresses were changed back to 127.0.0.1!!!

Re-ran BE setup - changed IP addresses again.  Exited.  I haven't been running Mythfilldatabase.

Went back into FE and checked IP address - stayed the same.  No error message about IP address.  Checked livetv again and again it worked.  Rechecked IP addresses in BE they stayed the same 192.168.0.19.

(sorry, for the long reply - this is the way I troubleshoot at work - I figure -detail, detail, detail)

I haven't rebooted yet - I'm going to try telnet(ing) into the 192.... addr and port to see if it works now.

---

### Post by purza on 2014-04-20
It's working...

```
pixpurz@MycroftHTPC:~/.mythtv$ telnet 192.168.0.19 6546Trying 192.168.0.19...
Connected to 192.168.0.19.
Escape character is '^]'.
MythFrontend Network Control
Type 'help' for usage information
---------------------------------



```

Tried some key codes -  SUCCESS!!!

Grabbed my iPhone - launched "Mythremote"  .... It Connected!!!  tried some commands - Success!!!

I am afraid to reboot...   I'm afraid to do updates etc...

Thanks All for your Help.  Especially, ubm-ubunet and linuxhippy.  (how do you guys know so much about the internal workings? )

I don't understand why the BE Ip addresses changed back to the loop back.  And it took a couple of tries to get it to take.  Fyi here's my setup

I'm using a wireless card (haven't) ran an cat5e to 6 cable yet.
 *-network
       description: Wireless interface
       product: RT3062 Wireless 802.11n 2T/2R
       vendor: Ralink corp.
MB:    ASUS A88X-PRO Socket FM2+ ATX AMD Motherboard
GPU:    Integrated AMD Radeon™ R/HD8000/HD7000 Series Graphics in the A-Series APU 
    Multi-VGA output support : HDMI/DVI/RGB/DisplayPort ports 
    - Supports HDMI with max. resolution 4096 x 2160 @ 24 Hz / 1920 x 1200 @60Hz*1
    - Supports DVI with max. resolution 2560 x 1600 @ 60 Hz
    - Supports RGB with max. resolution 1920 x 1600 @ 60 Hz
    - Supports DisplayPort with max. resolution 4096 x 2160 @ 60 Hz 
    Maximum shared memory of 2048 MB
    AMD® Dual Graphics technology support *2
CPU:      A6 6400K Black Edition 3.9GHz Dual-Core Socket FM2     Boxed     Processor
RAM:     8GB, Kingston 240-pin DIMM, DDR3 PC3-12800 memory module         KHX1600C9D3K2/8GX
GRAPHICS CARD:  Zotac Nvidia geForce GT 610 (installed because unable to get the onboard GA to stop "tearing", etc.
CASE:     SILVERSTONE Black Aluminum / Steel Grandia Series SST-GD07B ATX Media Center
KYBRD:  Logitech K400 WRLS
PWRSUP: CORSAIR 600W CXMOD 80+BRZ ATX PSU
HD:     Sda:     BOOT DISK: SanDisk SDSSDX-120G-G25
    Sdb:     HARDDISK 1:  1 TB WD Green WD20EZRX
    Sdc:    HARDDISK 2:  1 TB WD Green WD20EZRX
TUNER:  Ceton InfiniTV 4 PCIe - 4-channel Internal Cable TV Tuner Card for CableCARD
TVProv:    Comcast/ Xfinity
Region:    Philadelphia
Country:USA
Remote: None
CD:      Pioneer BDR-208DBK 15x Internal Blu-ray Burner
ACCY:     Sabrent 7 slot 75 in 1 Int Card Reader

Clean install of Mythbuntu version (MythTV 0.25)
Ubuntu: 12.04.04 precise LTS

---

### Post by blm-ubunet on 2014-04-20
You need to stop all FE & BE before running "mythtv-setup"..
I would guess that a different sequence leads to problems.

Some of the old versions of "mythtv-setup" failed to stop the BE.
I have a habit of always stopping BE manually (sudo service mythtv-backend stop).

You should always run mythtv-setup after updates/upgrades before any BE starts.
This is not so easy to do for pre-packaged distros.

You can get 0.27+fixes for 12.04-LTS from mythbuntu ppa.

---

### Post by purza on 2014-04-21
So I thought when I get the dialog "Do you want to stop the BE" it was seriously stopping it.  I tried upgrading to .27 through the Mythbuntu control center back around St Patrick's Day and panicked when I received the FE dialog about the IP address was incorrect.  That was a Mythbuntu install based on the Lubuntu distro.  That's how I wound up with a clean install of Mythbuntu.

So you would recommend upgrading and upgrading like this:

From: [http://askubuntu.com/questions/201435/how-do-i-use-the-mythbuntu-repository-on-a-headless-server](http://askubuntu.com/questions/201435/how-do-i-use-the-mythbuntu-repository-on-a-headless-server)
[COLOR=#333333][FONT=UbuntuRegular]The way we do the repos is by MythTV major version number, and the command to add it would be[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]```
apt-add-repository ppa:mythbuntu/<MythTV Version number>
```[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So for 0.26 it would be[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]```
apt-add-repository ppa:mythbuntu/0.26
```[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Note that any point releases (such as 0.26.1) would still be the 0.26 version.[/FONT][/COLOR]

---

### Post by blm-ubunet on 2014-04-21
The "askubuntu" question was about changing from the stock ubuntu packages (of mythtv) to the mythbuntu repositories ppa using terminal cmds. (the answer was from a mythbuntu team dev)

A std mythbuntu install is already connected to that ppa..
You only need to manipulate which packages (& versions) that are installed from that ppa.
Can do with "apt-get" or synaptic package manager.

But you have the "mythbuntu-control-centre" app to control/config versions/upgrades.
This app should have been able to configure your system to use real IP addresses.

I would make sure all & any FEs and BEs are stopped before updating (0.27+fixes).

---

### Post by purza on 2014-04-21
Great!  Thanks for the info.  I've been creating system images ever since I did the clean install, mainly due to the dozens of tweaks to get the Ceton card to work etc.

---

### Post by purza on 2014-04-22
My power went out last night, so I checked on my Mythbuntu box.  First of all it didn't reboot to Mythbuntu automatically and went I did turn it back on I had the same problem.  Color dialogue with Language selection then the Myth FE IP address page.

All the IP addresses were correct - FE an BE and still received message about not communicating with BE.  I ran "top" and didn't see any instances of Myth BE or FE.  I tried "sudo service mythtv-backend stop" but it didn't recognize command/ file.

Finally, I went into the BE setup and re-entered the IP addresses and it took.   When I restarted FE everything worked.

I'll try running updates and upgrade plus try looking at logs.  Though kind of hard to understand logs when there isn't any explanation of them that I can find etc.

---

### Post by drink1297 on 2014-05-04
You need to edit the /etc/mythtv/config.xml file on the frontend....

Right after the <Frontend> tag, enter
<LocalHostName>add your lan IP</LocalHostName>

you can also make sure you add an entry for the routing tables...

sudo iptables -I INPUT -p tcp -dport 6546 -i [+] -j ACCEPT

Then I restarted the frontend, unchecked the allow remote connection box, restarted the frontend, rechecked the box, and restarted the frontend one last time, and it worked on all my frontend boxes.

---

