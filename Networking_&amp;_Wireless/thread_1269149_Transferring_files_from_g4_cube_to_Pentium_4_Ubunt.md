---
title: "Transferring files from g4 cube to Pentium 4 Ubuntu box question"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by mjp29 on 2009-09-17
I'm installing the latest Ubuntu on an HP Pentium 4 box.  I plan to test it on the pc box and if all goes well (for my needs) then I plan to buy a larger HD for the pc box and start using Ubuntu as my primary desktop.

My question is this:  How can I easily transfer my many years and many gigs of digital photos (and other files) most easily from the g4 cube to the Ubuntu system. Emailing these large files is out of the question and burning DVD's will take too many DVD's and frustrate me.  My backup HD is firewire only and the Ubuntu Pentium box doesn't have firewire.  The G4 cube has usb 1.1 and firewire.  Could I connect the G4 cube to the Ubuntu box via usb cord or ethernet cord and see the G4's HD show up on the desktop of Ubuntu and access my files? 

One additional question - which is faster, the g4 cube (400 mhz) or the Pentium 4 box if I chose to just run Ubuntu on the G4 instead?

---

### Post by mjp29 on 2009-09-17
I'm installing the latest Ubuntu on an HP Pentium 4 box.  I plan to test it on the pc box and if all goes well (for my needs) then I plan to buy a larger HD for the pc box and start using Ubuntu as my primary desktop.

My question is this:  How can I easily transfer my many years and many gigs of digital photos (and other files) most easily from the Apple g4 cube (running os X) to the Ubuntu system. Emailing these large files is out of the question and burning DVD's will take too many DVD's and frustrate me.  My backup HD is firewire only and the Ubuntu Pentium box doesn't have firewire.  The G4 cube has usb 1.1 and firewire.  Could I connect the G4 cube to the Ubuntu box via usb cord or ethernet cord and see the G4's HD show up on the desktop of Ubuntu and access my files? 

Additional info: I have the Westell Versalink 327w for my Verizon dsl

One additional question - which is faster, the g4 cube (400 mhz) or the Pentium 4 box if I chose to just run Ubuntu on the G4 instead?

---

### Post by gordintoronto on 2009-09-17
Connect the boxes by Ethernet, then run an FTP server on one and FTP client on the other.  If I were guessing, I would guess that it's easier or cheaper to set up the FTP server on the Ubuntu machine.

If you have a router, you could plug both computers into the router, if not, get a "null modem" ethernet cable.

---

### Post by mjp29 on 2009-09-17
I have the Westell Versalink 327w for my Verizon dsl

Would I still need the ftp server and client software if connected to this?

---

### Post by tgalati4 on 2009-09-17
Just turn sharing on in OS X for the home directory and it will show up in ubuntu.  Then just drag and drop.  Be sure to test the files that have been copied over before deleting the old ones.

---

### Post by mjp29 on 2009-09-17
Now that's the easy solution I was looking for!

Thanks so much for your help!

p.s. won't be deleting any files from the Apple - will just put it in storage as I know it will be an additional backup of all my files

---

### Post by egalvan on 2009-09-17
> **mjp29 said:**
>   How can I easily transfer my many years and many gigs of digital photos (and other files) most easily from the Apple g4 cube (running os X) to the Ubuntu system.

  My backup HD is firewire only and the Ubuntu Pentium box doesn't have firewire. 
 The G4 cube has usb 1.1 and firewire.  Could I connect the G4 cube to the Ubuntu box via usb cord or ethernet cord and see the G4's HD show up on the desktop of Ubuntu and access my files? 


Firewire cards are available very cheaply these days.
Search ebay with this

[B]Adaptec 3 port Firewire 1394 Fireconnect 4300 PCI Card
[/B]
to see an example... $10 shipped, he has 23 of them...
there are many more... adaptec is a good brand, as is belkin.

Or you can user a cross-over network cable to form a two-machine network...

Or you can remove the drive from the external enclosure and install it directly to your HP machine,
I don't know if Linux has a native driver for the filesystem Apple used, though.

Or you can use a USB-USB network cable, and see how long your beard grows as you transfer "gigabytes of files" over a USB1.1 connection :lolflag:  sorry... :)

---

### Post by Zero++ on 2009-09-17
You could buy a hard drive enclosure that has both USB and firewire or get one that the Mac cube drive will fit in to that has a USB connection and just pull your mac drive and put the files you want on your Linux box directly.

---

### Post by seshomaru samma on 2009-09-18
or if both boxes are behind a router you can run apache on osx and share the files with ubuntu
setting apache on osx is super easy

---

### Post by mapes12 on 2009-09-18
I haven't got a Mac box myself but it appears you can run SSH on it: [http://www.google.co.uk/#hl=en&source=hp&q=osx+ssh&btnG=Google+Search&meta=&aq=f&oq=osx+ssh&fp=65a6334453af9707](http://www.google.co.uk/#hl=en&source=hp&q=osx+ssh&btnG=Google+Search&meta=&aq=f&oq=osx+ssh&fp=65a6334453af9707)

In which case you should be able to adapt my following guide to connect the two machines together over your LAN or crossover cable. To connect two UBU boxes it goes like this but make the changes to suit your Mac box configuration. It looks a lot of text but it's super easy:

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```is a meta package and will install both applications

2.) Find out the IP addresses of the computer you want to connect to.

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

> One additional question - which is faster, the g4 cube (400 mhz) or the Pentium 4 box if I chose to just run Ubuntu on the G4 instead?Speed is not just CPU speed. It's M/B bus speed, HDD speed and everything else. The slowest component will be the common denominator that everything runs at. Once you have rescued your critical data why not install Ubu on both machines and compare the two.

Hope this helps.

---

### Post by mjp29 on 2009-09-19
> **seshomaru samma said:**
> or if both boxes are behind a router you can run apache on osx and share the files with ubuntu
setting apache on osx is super easy


Someone in Apple forum here said one could open file sharing in mac os x and do it that way

I'll be trying that now to see if I need apache or not

is apache free?

---

### Post by mjp29 on 2009-09-19
ok, i turned personal file sharing on in Mac os x system preferences.  Now, the question is where does it show up on ubuntu

---

### Post by mjp29 on 2009-09-19
ok I need to get serious about this so that I can transfer my photos and other files from my mac (os x) to my Ubuntu box

after starting personal file sharing and making sure appletalk is turned on (on the mac) I can't get Firefox on the Ubuntu box to locate the Mac's ip address

read my post in the link below too please

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

link was reported to not work so please also try

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

---

### Post by mjp29 on 2009-09-19
ok I need to get serious about this so that I can transfer my photos and other files from my mac (os x) to my Ubuntu box

after starting personal file sharing and making sure appletalk is turned on (on the mac) I can't get Firefox on the Ubuntu box to locate the Mac's ip address

read my post in Apple forum link below too please.  I am suppose to be able to pull this off without installing server software on the mac (like Apache), etc...

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

link was reported to not work so please also try

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

---

### Post by Soley on 2009-09-19
Why not just ssh into the OS X box? It should mount on your Ubuntu desktop after that & you'll be able to drag & drop via nautilus.

---

### Post by mjp29 on 2009-09-19
ok I need to get serious about this so that I can transfer my photos and other files from my mac (os x) to my Ubuntu box

after starting personal file sharing and making sure appletalk is turned on (on the mac) I can't get Firefox on the Ubuntu box to locate the Mac's ip address

read my post in the link below too please

[http://discussions.apple.com/thread....50492#10250492](http://discussions.apple.com/thread....50492#10250492)

link was reported to not work so please also try

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)


mjp29 is online now Report Post   	Edit/Delete Message

---

### Post by movieman on 2009-09-19
BTW, that link doesn't work.

---

### Post by mjp29 on 2009-09-19
sounds like a plan

questions:  what is ssh and nautilus you refer to (are they preinstalled in my ubuntu 9.04 somewhere).

what you are suggesting is a different approach than what I am trying (but I will try that if I have to)  I was hoping I could simply access the Mac's files through my ethernet cables (connected from both computers to the dsl modem).

Was hoping I could just use Firefox browser to access the Mac's files (like anyone would be able to access them on the internet anywhere with a browser if Mac's file sharing is turned on).

---

### Post by mjp29 on 2009-09-19
link was reported to not work so please also try

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

---

### Post by tgalati4 on 2009-09-19
The mac file sharing works if two machines are on the same local area network.  If you don't have a 4-port hub to plug into, then you don't have a network.

You can transfer files point-to-point using a CAT5 cross-over-cable, but it takes some work to set up.

The mac file shares show up when you select "Network" in Nautilus.

---

### Post by mjp29 on 2009-09-19
sorry and thanks for reporting that to me

please also try

[http://discussions.apple.com/thread.jspa?messageID=10250492#10250492](http://discussions.apple.com/thread.jspa?messageID=10250492#10250492)

---

### Post by highfructose327 on 2009-09-19
I use rsync+ssh to back up my wifes photos to a ubuntu box where we keep our backups.From my wifes mac I run  ```
rsync -avz -e ssh /Volumes/Photography/  highfructose327@ubuntu.local:/media/backup/photography
``` I know there are quite a few good tutorials for mac and ubuntu for rsync+ssh. Hope this helps




[http://ubuntuforums.org/showthread.php?t=15082&highlight=crontab+for+backups]("http://ubuntuforums.org/showthread.php?t=15082&highlight=crontab+for+backups")

[http://sial.org/howto/rsync/]("http://sial.org/howto/rsync/")

---

### Post by digitaladdictions on 2009-09-19
This is how I would do it. I am not sure what the appletalk support is like in Linux as I have never tried. I would just use samba which is well established and supported. 

On your mac go to System Preferences -> Sharing 

Check File Sharing and click on Options. Check Share Files and Folders using SMB (Windows) and make sure that your user account has a checkbox next to it.  Click done. 

On ubuntu create a new folder to mount the share on.

from the command line issue the follow command

sudo mount -t cifs //<your-ip>/<yourshare> /your/mount/folder -o username=<your-mac-username>,password=<your-mac-password>

so for example if your mac's IP was 10.20.30.1 and your username was mjp29 and your password was ubuntu and you wanted to mount the folder at /home/mjp29/mymac you would issue:

sudo mount -t cifs //10.20.30.1/mjp29 /home/mjp29/mymac -o username=mjp29,password=ubuntu

You can now go to your home folder and go to mymac to see the contents of your mac. 

If you need a list of the shares on your mac to choose from you can issue the following command from ubuntu to get a list of the shares. One of them should just be your username and this will give you full access to all your stuff.  

smbclient -L <your-mac-ip> -U <your-mac-username>

---

### Post by egalvan on 2009-09-19
> **tgalati4 said:**
> The mac file sharing works if two machines are on the same local area network.
  **If you don't have a 4-port hub to plug into, then you don't have a network.**

The mac file shares show up when you select "Network" in Nautilus.

You can transfer files point-to-point using a CAT5 cross-over-cable, **but it takes some work to set up.**


I don't use Mac machines, so I can't comment on them,

But I can dispel some errors in this post...

You don't need a 4-port hub to have a network. Or even a Local Area network (LAN).

A cross-over cable connecting two machines is the smallest LAN you can have (barring virtual machines).
Just make sure the addresses have the same subnet, or that masking is set up to compensate.
192.168.0.10
192.168.0.11
are two addresses that will form a LAN when connected correctly.

Setting up a network  with a cross-over cable is not very difficult.
give one machine the 192.168.0.10 address,
give the second machine the 192.168.0.11 address.

Admittedly the easiest way is with a  router set up to do DHCP,
as almost all computers come set up to accept DHCP.

And concerning cross-over cables...
almost all Ethernet hardware is capable of detecting the  type of connection,
 and automatically setting itself to the proper send/receive mode.
 No special cables needed these days.
I haven't had to use one in over four years, give or take.

ErnestG

---

### Post by mjp29 on 2009-09-19
They are both connected to my Verizon dsl Westell Versalink model 327W which has 4 ethernet ports in the back and both the Mac and Ubuntu are plugged into 2 of those 4 (and both using the internet from this)

But from my understanding the Mac personal file sharing should work over the internet if the other person on the net is supplied with the i.p. address of the Mac (even if they are using Windows on the net far away).

One thing that has come across my mind is perhaps I haven't told the Mac what to use as my personal file sharing folder on the Mac (so perhaps my Mac has no defined personal file sharing folder which would obviously not allow anyone to access something that isn't defined yet).

hmmm

will sleep on this and work on it more tomorrow (which includes me trying to use software to make it work even though I was under the belief it could be pulled off from both systems as is).

---

### Post by 3rdalbum on 2009-09-19
> **mjp29 said:**
> sounds like a plan

questions:  what is ssh and nautilus you refer to (are they preinstalled in my ubuntu 9.04 somewhere).

Ssh is a program that allows you to log into a Unix, Linux or OS X machine's command-line from another computer. I'm not sure if the SSH server is preinstalled on OS X, maybe it is?

SSH can also be used as a de facto file server.

Nautilus is your file browser on Ubuntu.

---

### Post by 3rdalbum on 2009-09-19
> **mjp29 said:**
> One thing that has come across my mind is perhaps I haven't told the Mac what to use as my personal file sharing folder on the Mac (so perhaps my Mac has no defined personal file sharing folder which would obviously not allow anyone to access something that isn't defined yet).

By default the OS X personal firewall should block port 80 incoming, assuming that this is the port that the web sharing uses (it should be, port 80 is the HTTP port).

---

### Post by XCan on 2009-09-20
Yes apache is free, and OSX does come with a built in webeserver that only needs to be enabled. How useful that is on the other hand is debatable, as you will have to click on every single file to download them.

For simplicity I would go along mapes12's suggestion, but perhaps setup ssh server on your Ubuntu machine. Then you can simply connect to it with a graphical application that supports sftp (most ftp apps). 

For speed, use a proper FTP server.

---

### Post by 3rdalbum on 2009-09-20
> **mjp29 said:**
> One additional question - which is faster, the g4 cube (400 mhz) or the Pentium 4 box if I chose to just run Ubuntu on the G4 instead?

The P4 will be faster. Also note that most proprietary software (Skype, Google Earth, 3D graphics drivers, Flash Player, plus Wine) isn't compiled for the G4's PowerPC CPU architecture and will not work. You're better off sticking with Ubuntu on the P4 rather than installing it on the G4.

---

### Post by mapes12 on 2009-09-20
> but perhaps setup ssh server on your Ubuntu machine. Then you can simply connect to it with a graphical application that supports sftp (most ftp apps).In my experience once you have open-ssh installed you don't need anything else installed. The standard Nautilus file browser will do the GUI bit for you. As for speed, then this is only limited by your LAN connections. I can happily achieve approx 4MB/s second over both wired and wifi on my LAN using SSH. More than enough for moving music, video and any other large files in a short time.

EDIT: If you experience a slow file transfer speed and by that I mean a rapid drop down to about 60KB/s then the problem will be with a wifi driver loosing packets. I've filed a bug report. If this happens then connect via an ethernet cable, otherwise you may grow old waiting for stuff to be transferred..........

---

### Post by tgalati4 on 2009-09-20
Control-Click the Mac folder you want to share and turn sharing on for that folder.  It should then show up in "Network" when you click on it in the file manager (nautilus).

---

