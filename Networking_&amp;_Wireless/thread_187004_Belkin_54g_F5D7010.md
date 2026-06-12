---
title: "Belkin 54g F5D7010"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by jhuff on 2006-06-02
[FONT=Arial][SIZE=2]Here is how I got my Belking 54g F5D7010 Wireless card working at 54g under Dapper.  I use Network Manager and it works great!  I borrowed these steps from other howto's.
[/SIZE][/FONT][FONT=Arial]
[/FONT] [FONT=Arial][SIZE=2]Black List the bcm43xx driver with the following command:

[/SIZE][/FONT] [LEFT][FONT=Arial][SIZE=2]```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```[/SIZE][/FONT][/LEFT]
            [FONT=Arial][SIZE=2]
Install “ndiswrapper-utils” using Synaptic Package Manager[/SIZE][/FONT][FONT=Arial][SIZE=2]

Copy the windows drivers into a new folder named “windows_drivers”

[/SIZE][/FONT][FONT=Arial]Make sure you copy the following two files into [/FONT][FONT=Arial][SIZE=2]“windows_drivers”[/SIZE][/FONT][FONT=Arial]:[/FONT][INDENT][FONT=Arial]bcmwl5a.inf
bcmwl5.sys
[/FONT] [/INDENT][FONT=Arial][SIZE=2](I have attached the drivers below)

Open a terminal window.

[/SIZE][/FONT][FONT=Arial][SIZE=2]Install the Windows driver with the following command:[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial]```
sudo ndiswrapper -i ~/windows_drivers/bcmwl5a.inf
```[/FONT][FONT=Arial][SIZE=2]

Now create and alias for wlan0 into module configuration file so that this module is used whenever the wireless interface is started:

[/SIZE][/FONT][FONT=Arial]```
sudo ndiswrapper -m
```[/FONT][FONT=Arial][SIZE=2]

load the new module in the running kernel:[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial]```
sudo modprobe ndiswrapper
```[/FONT][FONT=Arial][SIZE=2]

You should be able to check whether the driver was loaded successfully now and whether the hardware has been detected or not.[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial]```
sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
```[/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
You also may need to add the ndiswrapper module to the startup modules so Ubuntu can setup the device when your machine starts. You need to add ndiswrapper to the end of the /etc/modules file. You can do this by:

[/SIZE][/FONT][LEFT][FONT=Arial]```
sudo gedit /etc/modules
``` [/FONT][FONT=Arial][SIZE=2]

Add ndiswrapper to the end of this, save and close. (Make sure you leave a blank line at the end of the file.) When your machine reboots, it will find the Wireless Adaptor and start it up.[/SIZE][/FONT][/LEFT]

---

### Post by gozel on 2006-06-06
Hey jhuff!  Great, easy to follow how-to, but my machine is throwing out problems.  I've got the F5D7010 as well, but when I follow your steps, I get a Segmentation Fault when I try to modprobe it.  What the heck is happening?  Can you lend me some help, brother?

-Gozel

---

### Post by ubunta_pr0 on 2006-08-10
:-({|=

---

### Post by SeaSky on 2006-08-17
I have the Belkin F5D7010 card and i have tried ***everything*** and it will not seem to work. I can get the light to come one but thats about it. I am using U! 6.06 on a HP DV5140US Notebook (has broadcom as well! DOH! )
Will these cards work or not??? At this point I am about to purchase a d-link. Whats a good card that works out of the box?
:-({|= :-({|=

---

### Post by jeffreydavidson on 2006-08-17
It seems like I have tried it all as well. My window drivers are different than those, just a Belkin driver. Wireless access is the only thing keeping me from dumping Windows entirely.

JLD

---

### Post by spd106 on 2006-08-18
It would be useful if you could please say which revision of the card you have and whether it works on not with ndiswrapper or bcm43xx.

I have a Belkin 54g F5D7010 v1314uk and I have tested it working with ndiswrapper-utils and the supplied bcmwl5.inf and .sys files.

I must admit that I have passed it on to a windows stalwart and bought a replacement atheros based d-link card.

---

### Post by dgrafix on 2006-08-19
Ive got one too but cant get the files needed. I tried this guide with the default rt2500.inf/sys that i found online for this card (they were ot on the cd :(

Everything went smoothly and an ndiswrapper -l says all installed and working. 

But No lights and no joy.

Is it legal for someone to email me the required files??

I have no rev number on it it simply says Belkin wireless G 54G F5D7010

although there is a small sticker with version3000DE

---

### Post by jhuff on 2006-08-19
I can email you the driver files I used if you would like.

---

### Post by SeaSky on 2006-08-20
still no luck here, internal broadcom is firmware 4319, 
then i have the belkin f5d7010 version 1
on an HP-DV5140US notebook

windows drivers on hp.com are for 32 bit windows and i used 64 bit ubuntu 
will that be an issue?

i installed 32 bit ubuntu and give it another try

---

### Post by dgrafix on 2006-08-22
Yes please Jhuff.


I in stalled the cd that came with it on a windows pc and swiped the driver files from the installation.

they are the same as i had b4 rt2500.inf/sys but different size.

After getting all excited, it didnt work and back to square 1.
](*,) ](*,) ](*,)

---

### Post by Troy Shanahan on 2006-08-24
Hrm, I seem to have the same problem as grafix here, those files just don't seem to exist in the driver version I have, would you mind emailing them to me as well?

I'm trying to get into linux, but it's the first time I've tried it in any seriousness and the lack of internet on my laptop is getting on my nerves a bit...

---

### Post by dgrafix on 2006-08-24
i think i kind of got it working...

basically, not using wifiradar and network manager.

install the ndis wrapper drivers (i unpacked them on a windows pc, run the install program, but before it finishes, get the dog called 'totalwasteofmem' to sniff out for rt2500.inf/sys 
do the ndiswrapper dance (instructions around here somewhere)

Configure the network settings using the default gnome thingy. I only got NONE/WEP working as there is no place here for WPK. Also disable the lan adaptor(from tick inside properties, not from the disable button!!)

reboot the pc and do an 
ndiswrapper -l

if it says:
rt2500 driver present
or:
rt2500 driver present hardware present

now heres the clever bit....(drumroll)=D> 

pull the card out and plug it in again 3 times with mabe a 2-3 sec pause each time(or until the lights go on!)
3 times works for me like clockwork.

LOL!:roll: 

pain in the bum but works.... half works anyway.

Itd be nicer to have wpk and be able to use network manager though.

PS Email me if you want the files i extracted from windows theyre for V3.000DE

---

### Post by jhuff on 2006-08-24
I have attached the drivers I used.

IF you are are using Network Manager.  Don't use "Network
Settings" to attempt to set up the wireless card.  the following link
describes what you need to do:

[https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28network%29%7C%28Manager%29](https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28network%29%7C%28Manager%29)

---

### Post by Troy Shanahan on 2006-08-26
Urk, okay, I downloaded the files and such (cheers for that by the way) but my machine is spewing out multiple errors.

firstly, it point blank refuses to allow me to modprobe the ndiswrapper, stating an invalid argument.

secondly, even though it installed the driver nice and dandy, it claims it to be invalid when i run the check.

anyone drop me a line here? if i could ge this to work i could ditch windows pemanently.

---

### Post by nothi on 2006-08-30
Hi, i followed all steps from first post. There are drivers in the system, they'r installed, and hardware is also present. But there is nothing 'bout this card in /etc/network/interfaces ... And i don't have any idea how to do my Belkin F5D7011 works? ):

Please help my anybody. Thank u in advance.

PS. I forgot to add, that the power light is on. (:
This is my interfaces file.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp

auto eth1
```

---

### Post by jhuff on 2006-08-30
Are you trying to use Network Manager?  (I would recommend you do, I use it and it works great.)  If you are running Network Manager you need to comment out (#) all the lines except the following:
```
auto lo
iface lo inet loopback
```

Once you edit the /etc/network/interfaces file as described above and installed Network Manager let me know how things are.

Good Luck

---

### Post by JuniorNA on 2006-09-04
I'm so happy you guys had this thread out there. I just installed ubuntu, and this was the first thing I was looking for. LOL. I barely know what the hell I'm doing or even looking at...but these instructions were nice and easy. Now i can learn and get used to linux via wireless!

Thanks so much.

---

### Post by edo152 on 2006-09-04
I am brand new to Linux, ie today.  I have an old laptop which couldn't run XP so I've taken the opportunity to put Ubuntu on to it and it runs like a dream. However, the Belkin F5D7010 is giving me real headaches.  My problem now is, that I've found an explanation of how to install it at the Belkin site, but due to my newness it is genuine IT gibberish.  If anyone would care to look at the link below and translate this into some other language, preferably English for me, it might help a few people.

[http://web.belkin.com/support/kb/kb.asp?a=1512](http://web.belkin.com/support/kb/kb.asp?a=1512)

---

### Post by JuniorNA on 2006-09-04
> **edo152 said:**
> I am brand new to Linux, ie today.  I have an old laptop which couldn't run XP so I've taken the opportunity to put Ubuntu on to it and it runs like a dream. However, the Belkin F5D7010 is giving me real headaches.  My problem now is, that I've found an explanation of how to install it at the Belkin site, but due to my newness it is genuine IT gibberish.  If anyone would care to look at the link below and translate this into some other language, preferably English for me, it might help a few people.

[http://web.belkin.com/support/kb/kb.asp?a=1512](http://web.belkin.com/support/kb/kb.asp?a=1512)
edo, I just started using linux today as well. I am MCP/MCDST/MCSE for XP and windows 2000 and linux is like chinese to me. Installing ubuntu made it easy for me and i was able to understand it. I followed the EXACT instructions on the very first post on this thread, and had my card working in less than 3 minutes. It was easier to set up the card on ubuntu than it was for XP for me :) 

I can't assist you with anything other than telling you that the first post has all the information to make it work. Follow it line by line, and make sure the card is in when you type in the command at the prompt to see if the drivers are valid and the hardware is available. Then you have to activate the card in network settings which I dont think was explained by the original poster. 

Hope this helps. 

post back your progress after you go thorugh it again and I or someone else will definately try to help.

---

### Post by edo152 on 2006-09-04
I got as far as the sudo modprobe ndiswrapper command and it came back with this:

FATAL: Error inserting ndiswrapper (/lib/modules/2.16 15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): invalid argument

Hey Ho

---

### Post by edo152 on 2006-09-04
I checked the status of my drivers and is saying "bcmwl5a invalid driver!"  I checked that the drivers are in the windows_drivers file, and they are.  Completely stuck now, I may have to revert back to windows to get the wireless running, or buy a new wireless card that works.

Benny.

---

### Post by JuniorNA on 2006-09-04
> **edo152 said:**
> I checked the status of my drivers and is saying "bcmwl5a invalid driver!"  I checked that the drivers are in the windows_drivers file, and they are.  Completely stuck now, I may have to revert back to windows to get the wireless running, or buy a new wireless card that works.

Benny.
edo, 

NO way. Do not buy a new card. Chances are something is not setup correcty or you're doing something wrong. Your card works perfectly fine with ubuntu. I am living proof and a few others can confirm it works fine. I would not go out and buy a new card since you will have to go through the same config anyway. 

just something for you to see. I have my working G card in right now, and im using ubuntu as we speak. I did a few speed tests and I'm downloading at normal high speeds. 1.5 MB (yes, MEGABYTES) a  second. Which is 15mb (megabits per second). 

Just to show you that I'm still seeing errors when I use those commands, but the card works fine. 

Take a look at this error I get when i check the hardware. 

> installed ndis drivers: BCMWL5A invalid driver!

I am still getting those errors  but everything is working fine. 

Go to system > administration > Networking - tell me what protocols and hardware you see listed there. 

Get back to us.

---

### Post by edo152 on 2006-09-05
I went through the whole thing but got an error of some kind at almost every point.  Re-booted but laptop still can't see the F5D7050.

I've tried to use the Wireless Utility, but that can't see any usable wireless devices.  The Network Manager can only see my Ethernet driver and the modem.

I'm going to keep trying, because this must work.

Benny.](*,)

---

### Post by edo152 on 2006-09-05
I'm probably on the wrong thread here, but I've managed to get the system to see the 7050.  The drivers seem to have installed but I can't make it connect to my router (a D-Link DI-624). 

When I click on the wireless network connection and click on wireless name it goes off to connect but fails.

When I use the System | Administration | Networking It tells me that wlan0 is active and the properties seem OK (no WEP etc.)

The Applications |Internet | Wireless Assistant tells me that I have insufficient permissions... and asks "Did you run it using 'sudo'?".  It then sees the router but when you click on the router it says 'connection failed'.

And that is where I am right now.

---

### Post by edo152 on 2006-09-05
I don't know what is going on here, but this is starting to become a personal blog!  Although the little network icon says I'm not connected and that there are no network connections, I am now connected wirelessly via the Belkin f5d7050 USB device to the outside world.

I wish I could tell you how....

---

### Post by outofdiskspace on 2006-09-08
J, could you help a nOOb out and explain the "Install “ndiswrapper-utils” using Synaptic Package Manager" part of your post?  Does Synaptic Package Manager come with ubuntu or is this an add-on?

I downloaded ndiswrapper-utils on a Windoze machine but I'm not sure what to do with it.  Assuming I can use a memory stick to copy it to my Linux box, do I just run it like:  ./filename.deb ?  Or is there another process to install it?

Thanks!
Mark

---

### Post by dgrafix on 2006-09-08
YEEEEEESSSSSSSSS!

Thanks to Jhuf and his drivers

Re: Belkin 54g F5D7010 V3.00DE

Working fine with normal networking not network manager. For some reason it only works with a static ip not DHCP (its not my router as my win pc gets one just fine) hence cant use network manager.

Works great with wep now lights go on on every boot.


WoooHooo now i can drink my ubuntu in the garden :)

---

### Post by cdgrocott on 2006-09-08
I'm with you dgrafix! After trying to set up this card at least 5 times already (and 2 re-installs, I completely messed it up the 3rd time around) using as many different methods as I could find I was still no closer to sucess. I was just on the verge of giving up when I found this (I hadn't found it sooner becasue Google wasn't throwing it up! :confused: )

Jhuf's method worked perfectly first time. :D I can't thank you enough! Now I can enjoy Ubuntu without tripping over the 10m cable on my way downstairs!!!

---

### Post by Fitzcarraldo on 2006-10-07
The procedure my brother had to use to get the Belkin 54g wireless F5D7010 PCMCIA card working with his notebook PC is documented in the following thread:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

Hope it helps someone avoid the hassle he had to go through.

---

### Post by tmarios on 2006-10-19
I have the the Belkin 54g F5D7010. On the back it says version 1100 and also broadcom BCM94306CB. 
I installed xubuntu and when i insert the card I can see it under System > Networking. Its using the BCM43xx drivers but I cant get it to connect to the  wireless network. 
I get this message when i restart the network service

SIOCSIFFLAGS: No such file or directory
Failed to bring up eth0.

I tried disabling the WEP encryption on the router but still the same. 

I have read places where people said it works without the need to do anything and other that have failed using the ndis drivers. Since there are so many versions of this card.

Anyone has any experience with this particular model?
or any ideas on why I can see the card but cant get it to run?

Thanks a lot for any replies.
:):)

---

### Post by dgrafix on 2006-10-20
after struggling for months with the belkin, i finaly got it working un-reliably.

My advice, save yourselves the bother and go out and buy a netgear WG511T for about 30 quid. It worked first time no hassle with network manager

---

### Post by tmarios on 2006-10-22
I finally got it to work after few days of trial and error, 
I followed the steps that i found here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
in my case since i use ubuntu edgy i continue with the dapper documentation and i did the bcm43xx installation ( without the ndis driver) i did the package install.

Note: make sure you configure the
essid, encryption key ( if you use ) and the channel to match your access point using the iwconfig.

---

### Post by TrueJk7 on 2006-10-22
dgrafix,

So I know you've been having the same problem I've had with this card. And now you said you use the netgear one and it works just fine. Did you use the NDISwrapper route or just plug it in and go? PLEASE let me know man. I am looking to get a wifi working.

Thanks again!

---

### Post by dgrafix on 2006-10-23
I just plugged it and it went no probs.

For WPA-psk though you need to do this:
I disabled all cards in system > admin > networking (this is important)

Then installed wpasupplicant and network-manager from synaptic
I think you may need madwifi too as i think its atheros based chipset(i dont think it hurts to install it anyway)

rebooted

plugged in the card

rebooted again

nm icon should appear in top right

click this and choose your network

type in your wpa key and you should be in buisiness

MAKE SURE YOU GET THE WG511T as there are some other variations of this card that wont work without fiddling.

---

### Post by tmarios on 2006-10-23
It works ok with the bcm43xx drivers,.
The only thing with the network-manager is that it does not have an interface unde xfe which is used by xubuntu, it has one for gnome. 
but the intructions on 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 
worked very well on my computer undex xubuntu.
i got some disconnectes but i think it has to do with my router and a lot of noise and not the driver.

---

### Post by TrueJk7 on 2006-10-23
IT WORKS! The belkin card works!! That is amazing! I did the folow up and then on /etc/init.d/bootmisc.sh I added "modprobe bcm43xx" and it works every time now! Woo hoo! Thanks again tmarios and dgrafix! 5 Days of drivers and configs and now it works no problem! 

PEACE!

---

### Post by seidleroni on 2006-11-04
Hi everyone,

I'm in the same boat as most of the people here, but I cant get my system to work.  I'm using the Belkin 54G FD7010.  I cant get the light on the system to turn on.  When I do the 'ndiswrapper -l' it gives me:

Installed ndis drivers:
bcmwl5a driver present, hardware present

However, the light for the card doesnt turn on when the machine starts.  Also, I could not edit the interfaces file because its read-only.  How do I get around this? Once I can edit it, can I just comment out all the lines but 'auto lo' and 'iface lo inet loophack'?  Is there any other files I need to edit? I think there was another file in modprobe.d that I needed to edit, but I cant edit that either (its read only, too!).  How can I edit these files.

Essentially, I *think* that hte driver is installed properly, and it recognizes my hardware, but is not turning on my card?

I am quite a linux noob, but am trying to get it all to work.

Thanks!

---

### Post by TiredBird on 2006-11-05
Seidleroni,

You might look at [this 'howto post']("http://www.ubuntuforums.org/showpost.php?p=1707809&postcount=1") I did recently. Your model number is different but the driver file you are using is the same one so it might apply. Anyway, it won't cost anything, (except a little time), to see if it can fix your problem.

Regarding editing those files: if you use the command line with 'gksudo' preceding the edit command, (as I show in that 'howto'), it'll probably work. Unless you've altered them, they're not read-only but they are owned by root so they get reported as 'read-only' when an unprivileged user tries to edit them.

If you follow everything in sequence you should get all the necessary files edited. The 'howto' should also answer your questions regarding the extra interfaces in /etc/networking/interfaces (or whatever it's called).

Good luck and post back as to the results you got. I'm curious as to whether it will also work with '7010'.

---

### Post by seidleroni on 2006-11-05
Hi,

I am following the directions that the previous poster linked to.  I got to the line 'sudo modprobe ndiswrapper', but when I send that line, I get the error:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.27-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid Arguement"

according to the directions, I should STOP and wait for help.  What should I do?  Should I keep going with the directions or should I try something else?  I checked to make sure that my command was spelled properly.

Eagerly awaiting some help/feedback!

---

### Post by TiredBird on 2006-11-06
Sorry, but I didn't see that error message when I was running through that sequence. Hopefully, someone else will know what it means. I sure don't. As far as going ahead. You might try it. But if you get to the end and it hasn't worked, don't forget to clean things up again before trying something else. Sorry I can't be more help. I know how frustrating it is.

---

### Post by seidleroni on 2006-11-06
Here's what I did to get around that "FATAL ERROR".  I googled a bit and found I had to enter these three lines:

sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper

Once I did that, I continued with the tutorial you gave me and it worked!  Well, almost, the static IP didnt work, so I used auto DHCP and that worked great.  I'm looking at Slashdot on the laptop now.  Thanks for all your help everyone!  I am now (mostly) Windows free!

---

### Post by TiredBird on 2006-11-06
So you just needed a different version of ndiswrapper. The best part is you got it working.

Congratulations!

---

### Post by elementskaterbla on 2007-02-17
this is kind of hard... the whole reason we are trying to set up wireless internet, is because we dont have internet on our computers, so that makes its sort of FU**ING impossible to do this unless you supply all the files like the ndiswrapper utility to download, because to use synaptic, i need the internet, and that is the whole fu**ing reason i came here duh!

---

### Post by dgrafix on 2007-02-17
Give up guys!

 and get a netgear wg511, i did.

At the end of the day, 22 pounds is worth all the hassle. It worked first time out of the box (although i think i installed madwifi before) , with no ndis wrappers and no messing about. 

Its 100% reliable now.

---

### Post by penquin on 2007-03-01
You know if you are trying to get this wireless devise to work try going to another computer download ndiswrapper1.8, depackage it, and use that ndiswrapper to install the inf file.  this is what you do.
$ sudo ndiswrapper -i blkwgn.inf
$ sudo ndiswrapper -di
$ sudo ndiswrapper -de
$ sudo ndiswrapper -m

during this process have the device install in your laptop then after the last line is entered remove then reinstall it the little green light should be on.

---

### Post by jlh13 on 2007-07-28
> **jhuff said:**
> I can email you the driver files I used if you would like.

could you email those drivers to me also? i tried to download them, *but* the right files did not come with the download, only an .EXE file
my email address is [email]nuts_in_a_nutshell@yahoo.com[/email]

---

### Post by jlh13 on 2007-07-28
okay. after a few hours of messing with it, i think i figured it out...
i really dont know why, but it only works with static IP
follow that steps in the begginning of this thread.
go to system--->administration--->networking.
click properties.
put in your network SSID and WEP code.
under connection settings at the bottom, click the drop-down menu that says DHCP and change it to Static IP Address.
put in your IP address, subnet mask and default gateway.


this is the process that worked for me, anyway

---

### Post by santana on 2007-12-03
thanks for the original post, the steps work for ubuntu 7.10 Gutsy and belkin drivers which came on cd.

---

### Post by mikesalt on 2008-01-09
Cheers, this tutorial got me up and running in next to no time. I thought Belkin adapters would be an absolute no-hoper. You have shown us the way! Ubuntu for the win!

---

### Post by steveguy on 2008-02-05
Just thought I would contribute the following:

I have the Belkin 7010 revision 7 - which has Realtek chipset. I pulled my hair out trying to get this to work under Gutsy, but finally got it working instantly on Hardy. Hardy came with a newer (1.9) ndiswrapper which happily accepted the Belkin WINXP driver on the CD - lights work and everything. My ndiswrapper under Gutsy (1.7) always reported that the card wasn't present.

---

