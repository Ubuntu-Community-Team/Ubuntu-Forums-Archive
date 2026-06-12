---
title: "How to setup home network? Heeeeeeeeeelp!"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by GARoss on 2009-02-07
Newbe question,
I searched over & over & I'm spinning my wheels getting no where fast. It seems most Linux tutorials are for large corp so the setups for networks are more involved than what I need I think. I just want a home network.
Here's what I have;

*Just installed Ubuntu 8.10-64 bit is connected to router cable #2 with Samba installed & a folder marked as shared in my home folder. My Internet connection is good via the router.
*XP Home desktop on router #1
*XP laptop on router #4
*Netgear RP114 Router

I had a 3 on a XP network config before installing Ubuntu on computer 1. The 2 XPs network is still working.

I've tried System/Administration/Network/Network Settings without any luck. In eth0 Properties, Configuration is on Automatic configuration (DHCP). Am I in the right place to begin?
Really lost here; all suggestions are appreciated.
George

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
exactely what do you need to do?

---

### Post by GARoss on 2009-02-07
Thanks for the reply.
3 computers total. Lets call my computer #1 (was XP now is Ubuntu 8.10), my wife's computer #2 (XP) & computer #3 (XP) is a laptop.
All were networked for video, photo & doc sharing (I edit video). XP support is being discontinued soon, so my wife & I are seeking a different OS. 
On computer #1, I decided to put Ubuntu on an unused HD (j) as a test. The other HDs (c & e) are unplug so nothing would be deleted (I lost my nerve). 
Computer #1 needs the network to access the printer which is hooked up to computer #2 via the network, as it was before I installed Ubuntu on it; that's a must. There are also video & Word docs on both computer #2 & computer #3 that need to be shared with computer #1.
Also, once I get Ubuntu working smoothly I'd like to make computer #1 a dual boot with XP but I need to work this out first.
Thanks
George

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
so you just need to share files between the computers? i recommend smb (samba) this is the thing windows uses, just apt-get it.

---

### Post by cariboo on 2009-02-07
You don't need samba to do any of the networking tasks. Ubuntu will automatically connect to windows computers without any extra programs. Go to Places-->Network and you should see a Windows Network Icon, double-click the icon and you should see the workgroup, If you see two workgroups you are going to have to change it.

It is just as easy to change the workgroup on Ubuntu as it is on Windows. Press Alt-F2 and type:

```
gksu gconf-editor
```

type you password when asked. Go to system-->smb in the left pane, then edit the workgroup to match the workgroup name of your workgroup.

Once all the workgroup names are the same you should just have to double-click the workgroup icon and see your shared folders.

To setup you printer, on the computer the printer is connected to make sure that in printer sharing the printer name doesn't have any spaces in it, and it available to everyone.

I would also suggest checking the [OpenPrinting Database]("http:///openprinting.org/printer_list.cgi") to see if your printer is supported. IF your printer isn't supported, you might as well stop trying now.


If you,ve determined that your printer is supported go to System-->Administration-->Printing and add a new printer. From the connection menu select Windows Printer via SMB then click the browse button and select your printer, click the forward button and follow the prompts.

Jim

---

### Post by GARoss on 2009-02-07
> **Til_Valhall_vi_drar! said:**
> so you just need to share files between the computers? i recommend smb (samba) this is the thing windows uses, just apt-get it.
As I said in my 1st post, I have installed Samba.

---

### Post by GARoss on 2009-02-07
> **cariboo907 said:**
> You don't need samba to do any of the networking tasks. Ubuntu will automatically connect to windows computers without any extra programs. Go to Places-->Network and you should see a Windows Network Icon, double-click the icon and you should see the workgroup, If you see two workgroups you are going to have to change it.

It is just as easy to change the workgroup on Ubuntu as it is on Windows. Press Alt-F2 and type:

```
gksu gconf-editor
```

type you password when asked. Go to system-->smb in the left pane, then edit the workgroup to match the workgroup name of your workgroup.

Once all the workgroup names are the same you should just have to double-click the workgroup icon and see your shared folders.

To setup you printer, on the computer the printer is connected to make sure that in printer sharing the printer name doesn't have any spaces in it, and it available to everyone.

I would also suggest checking the [OpenPrinting Database]("http:///openprinting.org/printer_list.cgi") to see if your printer is supported. IF your printer isn't supported, you might as well stop trying now.


If you,ve determined that your printer is supported go to System-->Administration-->Printing and add a new printer. From the connection menu select Windows Printer via SMB then click the browse button and select your printer, click the forward button and follow the prompts.

Jim

OK. I've looked may times at the Windows Network Icon, double clicked & it is empty!
```
gksu gconf-editor
``` Opened the Configuration Editor & following your instructions, I opened the smb folder. Says, "Workgroup"; that's it. Doubleclicked "Workgroup" & an Edit Key window opened & ask for a value.??? 
On computer #2, the XP network has 2 groups, Ross & Workgroup. From computer #2 (XP) I doubleclicked "Workgroup" & got nothing. Ross is the name of our network & it shows both XP computers but not the Ubuntu (computer #1) nor could it connect to it.
I'll check the printer now. Thanks.
George

---

### Post by GARoss on 2009-02-07
I doesn't look good for my printer! I don't even see it on the list.

*I thought I'd update this.
There are printer drivers & software available for my Canon i950 printer from TurboPrint ([http://www.turboprint.info/whatistp.html](http://www.turboprint.info/whatistp.html)). That's the good news; the bad is it cost about $40 usd. I downloaded a 30 day trial & printed a few things including a high rez photo & it works great. All in all, I think it's worth it. I can't expect every thing to be free!
George

---

### Post by issih on 2009-02-07
Change the workgroup of the ubuntu computer to the same as the two xp ones, i.e. ross. Once that is done you should hopefully begin to get things working.

You need the networking to be working for the printer to stand a chance as it functions via the same protocol.

Hope that helps

---

### Post by GARoss on 2009-02-08
issih,
Typing my name in didn't help either.
See the attached image. Do these settings look right? In the top middle I selected Ethernet & show IP addresses in Properties in the upper right as well as the rest of the settings below. It doesn't work in Auto detect either.
Any ideas? 

[IMG]http://i92.photobucket.com/albums/l10/queenofshines/maries%20auctions/Net.jpg[/IMG]

---

### Post by FishRCynic on 2009-02-08
go to terminal
click applications 
      accessories
      terminal



type in
sudo gedit /etc/samba/smb.conf


search for workgroup=

change to Ross or ROSS or whatever it is exactly on the xp machines

click exit and save file

type in 

sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start

you now should be able to somewhat connect to the xp machines using samba

---

### Post by issih on 2009-02-08
Just to clarify, if you can connect to the internet, and can ping the xp computers via their ip address (note that ubuntu doesn't resolve windows cifs hostnames by default so use ip address in ping) then you can be confident your network settings are fine...this is almost certainly a samba configuration issue. Samba being the windows networking.

Oh, and given how much you blanked out in those images no one could tell you if anything looked wrong anyway :)

I'd agree with the previous post, edit workgroup in smb.conf and try restarting samba. In fact that is something you really should do that after every time you change a setting, as I don't think samba dynamically adjusts, it probably just reads the config when it is launched.

One final thought, as a bug testing measure disable any AV stuff running on the xp machines (you can yoink the phone cable out of the router if you want to be careful during the test) it didn't ought to be causing trouble, but it removes one possible layer of complication for testing purposes.

---

### Post by GARoss on 2009-02-08
I changed the 2nd line in Global Settings to read;
#======================= Global Settings =======================

[global]

[I]## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = Ross
[/I]

...it was called WORKGROUP.
Still nothing.
Any ideas?
George

---

### Post by FishRCynic on 2009-02-08
in order to browse using nautilus with various computers i had to enable
one machine (i used an ubuntu one) to be a wins server

and then change the xp machines to be wins clients using
netbios over tcp

[http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/](http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/)

seems like a lot but its simple and easy to do

---

### Post by issih on 2009-02-08
Can you ping the xp machines?
What happens if you enter:

```
smb://192.168.0.2
```

where you replace the 192.16.0.2 with the ip address of one of the xp machines

into the location bar of nautilus (the file browser)

Oh and what version of ubuntu are you running? I remember that the samba browsing was slightly broken in hardy heron (but may now have been fixed in an update), but it seems fine in intrepid.

---

### Post by GARoss on 2009-02-08
> **issih said:**
> Can you ping the xp machines?
What happens if you enter:

```
smb://192.168.0.2
```

where you replace the 192.16.0.2 with the ip address of one of the xp machines

into the location bar of nautilus (the file browser)

Oh and what version of ubuntu are you running? I remember that the samba browsing was slightly broken in hardy heron (but may now have been fixed in an update), but it seems fine in intrepid.
I'm running v8.10 Intrepid 64bit. The XPs are 32 bit if that matters???
Tried it, it says *No such address*
Should firewall be disabled?
George

---

### Post by issih on 2009-02-08
You got no such address using the ip address of one of your xp boxes? you MUST use your ip addresses not the one I posted as an example..

can you ping the xp boxes? Open a terminal window and enter:

```
ping 192.168.0.2
```

again replacing the example IP 192.168.0.2 with the ip of one of the xp boxes (find this out by going to one of the xp boxes, into network connections and looking at the status of the lan connection)

Lets ensure the basic networking it functioning first of all.

---

### Post by GARoss on 2009-02-08
I did a print out from the XP & used that IP address for the ping test, then adjusted for each possible hub-port #. Went through all 4 with the same response; *No such file or directory*
All 3 computer are using the same hub for the internet so the hub is working.
George

---

### Post by FishRCynic on 2009-02-08
1) xp addresses
and ubuntu addresses are all the same except for

xxx.xxx.xxx.ccc  where xxx.xxx.xxx is the same and .ccc is different?

2) do you have a firewall enabled on the ubuntu machine?

---

### Post by issih on 2009-02-08
So can you ping them or not?

if you do as I asked and open a terminal and dp ping <ipaddress>
you should either get a set of replies from the host, something like this:

```
PING 192.168.0.2 (192.168.0.2): 56 data bytes
64 bytes from 192.168.0.2: icmp_seq=0 ttl=64 time=1.796 ms
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=2.120 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=1.895 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=2.293 ms
```

or you will get something saying no route to host - that means the test fails.

if you can't ping the xp box then we have no chance whatsoever until we sort your basic networking issues out.

N.B. the ip address has nothing to do with the actual physical ports on the hub/switch/router they are either statically assigned to a computer or assigned by a dhcp server. Typically the first 3 numbers will be the same (especially if you are actually using a hub not a switch, but the final number could be almost anything.

---

### Post by GARoss on 2009-02-08
> **FishRCynic said:**
> 1) xp addresses
and ubuntu addresses are all the same except for

xxx.xxx.xxx.ccc  where xxx.xxx.xxx is the same and .ccc is different?

2) do you have a firewall enabled on the ubuntu machine?

All 3 computers have the firewalls working. Turn off?
George

---

### Post by issih on 2009-02-08
for testing purposes yes, disable all firewalls.

---

### Post by GARoss on 2009-02-08
> **issih said:**
> So can you ping them or not?

if you do as I asked and open a terminal and dp ping <ipaddress>
you should either get a set of replies from the host, something like this:

```
PING 192.168.0.2 (192.168.0.2): 56 data bytes
64 bytes from 192.168.0.2: icmp_seq=0 ttl=64 time=1.796 ms
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=2.120 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=1.895 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=2.293 ms
```

or you will get something saying no route to host - that means the test fails.

if you can't ping the xp box then we have no chance whatsoever until we sort your basic networking issues out.

N.B. the ip address has nothing to do with the actual physical ports on the hub/switch/router they are either statically assigned to a computer or assigned by a dhcp server. Typically the first 3 numbers will be the same (especially if you are actually using a hub not a switch, but the final number could be almost anything.

Sorry, issih. I know you're trying to help me. As I said I'm a newbe & very slow. 
I had to install the db software. Once finished I tried to ping as you said & got,

[I]george@george-desktop:~$ dp ping 192.168.0.4
dp: no vocab file specified[/I]

I repeated the next 3 as well with the same response.
George

---

### Post by issih on 2009-02-08
ah....my fault, no the dp was a typo for do all you type is :

```
ping 192.168.0.2
```

replacing the 192.168.0.2 with the ip address of one of the xp machines

don't worry about being new, we all are at some point :)

---

### Post by GARoss on 2009-02-08
> **issih said:**
> ah....my fault, no the dp was a typo for do all you type is :

```
ping 192.168.0.2
```

replacing the 192.168.0.2 with the ip address of one of the xp machines

don't worry about being new, we all are at some point :)

Thanks,
Bingo! Plus similar results on the other 3 ports as well.

george@george-desktop:~$ ping 192.168.0.4
PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.
64 bytes from 192.168.0.4: icmp_seq=1 ttl=128 time=4.45 ms
64 bytes from 192.168.0.4: icmp_seq=2 ttl=128 time=0.273 ms
64 bytes from 192.168.0.4: icmp_seq=3 ttl=128 time=0.290 ms
64 bytes from 192.168.0.4: icmp_seq=4 ttl=128 time=0.273 ms
64 bytes from 192.168.0.4: icmp_seq=5 ttl=128 time=0.269 ms
64 bytes from 192.168.0.4: icmp_seq=6 ttl=128 time=0.273 ms
64 bytes from 192.168.0.4: icmp_seq=7 ttl=128 time=0.276 ms

couldn't stop it so I closed.
George

---

### Post by kevdog on 2009-02-08
ping is a little bit different in ubuntu than windows

ping -c4 <ipaddress> will limit the pings to 4.  If you dont put in a number, it will go on forever -- use cntl-c to break.

---

### Post by issih on 2009-02-08
I really don't understand what you mean by getting the same on the other 4 ports...as I say the ports on the hub have nothing to do with the IP address.

Anyway, that is good, you have at least got basic network connectivity between the ubuntu machine and the xp machine.

Now what happens if you open a file browser and enter:

```
smb://192.168.0.4
```

in the address bar?

---

### Post by BLTicklemonster on 2009-02-08
I can ping the xp box across the room, but when I click on the network icon, I see windows network, and when I click that, I get nothing. When I try to see this machine (with a shared folder), I see nothing at all.

And what's this mean?

```

bill@bill-desktop:~$ sudo /etc/init.d/samba stop
 * Stopping Samba daemons 
start-stop-daemon: warning: failed to kill 18744: No such process


```

---

### Post by GARoss on 2009-02-08
> **issih said:**
> I really don't understand what you mean by getting the same on the other 4 ports...as I say the ports on the hub have nothing to do with the IP address.

Anyway, that is good, you have at least got basic network connectivity between the ubuntu machine and the xp machine.

Now what happens if you open a file browser and enter:

```
smb://192.168.0.4
```

in the address bar?
Here it is;
Could not open location 'smb://192.168.0.4/'
No application is registered as handling this file

---

### Post by BLTicklemonster on 2009-02-08
> **GARoss said:**
> Here it is;
Could not open location 'smb://192.168.0.4/'
No application is registered as handling this file

do 

ping 192.168.0.4

instead.

---

### Post by issih on 2009-02-08
I suspect you did that in a web browser. You need to open a file browser (e.g. go to places->home folder) and enter that line into the location bar.

---

### Post by Osamabingandhi on 2009-02-08
Firstly check the firewall. I've got firestarter and it is a bit strange sometimes. I type sudo firestarter in the terminal and turn it off...

The other thing you should check is your router. Log into it and see what adress your ubuntu machine has.

You've seem to have samba and made the share right so you should see your ubuntu machine in windows if you have the right workgroup.

To use a Windows folder in ubuntu is a bit tricky, not at all as easy as in windows, there you only make a shortcut and you're done. One thing i've done to make it usable as an drive in ubuntu is to edit and mess around in fstab....

an example: 

sudo gedit /etc/fstab

Then i've added: 
//192.168.0.101/bURN/ /home/ubuntu/WindowsFiler/bURN  cifs  iocharset=utf8,file_mode=0777,dir_mode=0777,udf,iso9660,auto,user,rw,uid=1000,umask=000,utf8  0 0
//192.168.0.101/Spel/ /home/ubuntu/WindowsFiler/Spel  cifs  iocharset=utf8,file_mode=0777,dir_mode=0777,udf,iso9660,auto,user,rw,uid=1000,umask=000,utf8  0 0

It's important to have the caption right on the names! And you have to make the folders in ubuntu. Ive put Windowsfiles/Spel and Windowsfiler/bURN in my homefolder in ubuntu.

After you've edit it you save and write mount -a. If it works you get shortcuts on the desktop. And hopefully everytime you start ubuntu. I have to type mount -a everytime i restart....

---

### Post by GARoss on 2009-02-08
> **BLTicklemonster said:**
> do 

ping 192.168.0.4

instead.

PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.
George

---

### Post by BLTicklemonster on 2009-02-08
> **Osamabingandhi said:**
> Firstly check the firewall. I've got firestarter and it is a bit strange sometimes. I type sudo firestarter in the terminal and turn it off...



Sheesh. How did my firestarter get turned on?

I never would have even considered that. I had no idea it was still running.

Odd thing is, it was installed after my network failed. So I probably fixed the networking a long while ago, and it's been able to work ever since, but the firewall was stopping it from working.

Thanks.

Eeek, not that fast. I can see mshome, but I'm the only one I see in it. I know the other three machines in the house are up and sharing files.

---

### Post by Osamabingandhi on 2009-02-08
Again, usually it is those miserable firewalls, don't you have virus/firewall programs on the windowsmachines?

---

### Post by BLTicklemonster on 2009-02-08
We're behind a router, I don't keep a firewall on on them.

I can see this computer now from one of the xp boxes upstairs, the other one is the entertainment machine connected to the tv, and it's presently being used by her royal highness princess gumdrop who is watching disney... Okay, the one across the room connects to this one, but I can't see it.
The printer is networked now, that's the biggest thing I have been after since the networking stopped.

---

### Post by Osamabingandhi on 2009-02-08
So you're windows machine can connect to your ubuntu machine? 

But ubuntu can't connect to the windows computer? You have the same mshome on both. So you haven't got a firewall/virus software on your windowsmachine? You are brave....I use some free stuff on my media-windows computer. 

Three days ago microsoft shut windows down for me and asked me for money or else!!!I like the maffia....Soon soon windows will be gone from that computer too....

---

### Post by GARoss on 2009-02-09
Good news!
From computer #2, which is 100% XP, I can connect to a shared folder in my my Ubuntu computer. 
I'm still not, however, able to see way to connect from my Ubuntu computer to the XP, computer #2. Whats the trick?
Still need help!
Thanks
George

---

### Post by jonandrews on 2009-02-09
Check out my basic step by step guides to home networking between Windows & Ubuntu pc's:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by GARoss on 2009-02-09
> **jonandrews said:**
> Check out my basic step by step guides to home networking between Windows & Ubuntu pc's:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

Very nice, Jon! 
I pasted this portion because when I click on the 'Windows Network' icon as you suggest, I see nothing. Here's a newer thread I started today; [http://ubuntuforums.org/showthread.php?t=1064763](http://ubuntuforums.org/showthread.php?t=1064763)

Maybe this is where my problem is. Please take a look.
George

[I]Quote from **Ja's Ubuntu Guides-Sharing experience**
Step 1 - Install Ubuntu 8.10 [http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm)

After a basic install while connected to your pre-existing Windows network, internet access from the Ubuntu PC should work straight away.

Internet access by the Ubuntu PC is essential to this process. Do not proceed unless it is working.

By default, a lot of networking capability on the Ubuntu machine is already working:

On the bar at the top of the Ubuntu desktop, in Places > Network,  you will see the 'Windows Network' icon.- see note 1

You will also see icons for each of the pc's on your network.

D/clicking on the icon of a pc will display it’s shared folders.[/I]

---

### Post by Osamabingandhi on 2009-02-09
Have shared your folders in windows? That is all you need, then you should see the foldes in ubuntu.

---

### Post by GARoss on 2009-02-09
There are shared, but, not see from Ubuntu computer.
George

---

### Post by issih on 2009-02-09
have you done as I asked yet and put:

```
smb://192.168.0.4
```

into the address/location bar of a FILE browser yet?

File browser not web browser, I'm pretty certain from the error you posted last time that you were using a web browser..

Also have you ensured that all firewalls on all pc's are off, in order to minimise possible sources of trouble?

---

### Post by GARoss on 2009-02-09
I'm a newbe. I believe I did the other check with the terminal, not Firefox. I hope I did this right this time.
***Deleted photo-seemed to cause a problem.***



It says 0 items.
George

---

### Post by GARoss on 2009-02-09
issih,
I think I've got it right this time.
It shows folders on XP computer! I'm not sure what to do next but I'll see if I can connect & get my printer to work.
Thanks,
George

---

### Post by issih on 2009-02-09
Excellent, at this point I don't really know why you can get it to work that way but don't see anything if you just click on network...

As I said earlier, I know that there were issues with this very feature in hardy, but I thought they had been fixed in intrepid. Either way make sure you have all the updates.

I'm a bit stuck for suggestions at this point, but at least you have a workaround.

Oh and sorry if I came across as irritated, I wasn't having a go, just trying to be clear :)

---

### Post by jfwall on 2009-03-11
Thanks-Thanks-Thanks!!!
 
After a 3-months of trying to see hostnames from windows to linux and vice-versa, this finally makes my Ubuntu system "pingable" by hostname from my Windows systems.

I have "visiting" windows clients so can't use lmhosts or hard IP addresses.

(P.S. - I can't think why installing Samba and activating a share has to be done to do make Netbios/Winbind work, but I know the same type of thing has to be done on Windows sometimes - as a last resort you "enable file sharing" and all the netbios hostnames start to be visible - setting all the NetBios options per the doc doesn't always seem to work without the file-sharing thing)
 
Does anybody know how netbios really works? (Did anybody ever know? - It's at least 20 years old - somebody at/from MS or Netware should still be around to write it down!)

---

### Post by GARoss on 2009-03-14
I'm glad this thread helped you.
I can only give you my take on Samba which I have limited experience. Samba emulates Windows file sharing software, making Linux file sharing "Windows like". Therefore, your Windows network recognizes your Ubuntu as one of there own. At least, that's my take.;)

---

### Post by crono141 on 2009-03-14
OK I am having the exact same problem as GARoss.  The only difference is, I used to have a linksys router and I could see all my windows (vista and 7) shares in the places->network.  I recently upgraded to a NETGear router, and the network location has been empty ever since.  I followed the troubleshooting in this forum and was able to open up my windows share by typing smb://ipaddress/, but I still get "Unable to Mount Location" when trying to open the workgroup from the file browser.  Anyone have any more ideas?

Even more odd, I just tried to add my network printer (attached to the Win7 box) through the printer configuration menu, and all the share names of the attached computers showed up in it's samba browser (no printer though, but thats a different issue).

---

### Post by BLTicklemonster on 2009-03-14
I'm good now for the most part, but only on my partitions. I can't share anything from my main Ubuntu and this includes the printer not being printed. I wonder what to change in smb.conf to allow this? I know in the olden days if you shared anything an entry was made to smb.conf and you could actually see it. This does not happen any more, I wonder why?

---

