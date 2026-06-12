---
title: "Broadcom (4306)"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by obey43 on 2006-06-01
since dapper is out now...

can someone explain the most efficient/correct/updated way to get a broadcom (4306 specifically for me) wireless card up and running??

my only problem i have ever had with ubuntu.

: (

note: i have tried using the firmware .deb at [http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_i386.deb](http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_i386.deb)

it does not work with the current kernel.

i don't have too many options, because of course i have no connectivity on the computer.  

any suggestions?

---

### Post by almahtar on 2006-06-01
I have an HP ZV 6130us laptop with a Broadcom 4306 in it.  To get my wireless working I did this:
```

sudo su
apt-get install ndiswrapper-utils
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
modprobe ndiswrapper

```
Make sure you're in the same folder as bcmwl5.inf (your windows driver) and bcmwl5.sys.

Then verify it installed and worked:

```
ndiswrapper -l
```

Should say something along the lines of hardware detected and supported or whatever.

then, 
```
 nano /etc/modules.d/blacklist
``` (or is it module(no "s").d?)
and add the line "blacklist broadcom43xx" to the end.  Reboot and you should be on your way to glory.

On the side, I'd recommend you install network-manager-gnome (not just the "network-manager" that ships with Dapper).  It works really well with wireless.

---

### Post by kwah on 2006-06-01
There are some [pages on the Wiki]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=broadcom") describing how to cook broadcom wireless cards. You have two options: 1. to use bcmxxx kernel driver or 2. use ndiswrapper + windows driver. 

Personally, I am using the 2nd variant. And yes, NetworkManager is a good stuff (there is an info about it on the wiki pages as well).

---

### Post by spyrakos on 2006-06-01
Dies anyone know if this would also work on a 64bit installation? I've had no luck in the past with ndiswrapper, whatever distro I tried. Since I'm sticking with Dapper 64-bit for now, I'd like to do things properly...

---

### Post by hw-tph on 2006-06-01
I would strongly advice against using ndiswrapper since there is a real driver now (if you use Dapper the bcm43xx driver is installed by default).

```
apt-get install bcm43xx-fwcutter
``` installs the firmware cutting tool which you need. Then you simply type ```
fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys
```

Replace "2.6.15-23-k7" with the name of the kernel you are currently running. The file bcmwl5.sys comes from the Windows Broadcom driver package, which you can get from pretty much anywhere, such as [here](http://prinsig.se/weekee/files/80211g.zip) (from the R3000/ZV5000/nx9105 wiki).

Then simply unload the bcm43xx driver and then load it again. Now you should be able to configure your wireless interface with a *real free driver*. :)


Håkan

---

### Post by derk.d on 2006-06-01
[QUOTE=hw-tph]I would strongly advice against using ndiswrapper since there is a real driver now (if you use Dapper the bcm43xx driver is installed by default).

```
apt-get install bcm43xx-fwcutter
``` installs the firmware cutting tool which you need. Then you simply type ```
fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys
```

Replace "2.6.15-23-k7" with the name of the kernel you are currently running. The file bcmwl5.sys comes from the Windows Broadcom driver package, which you can get from pretty much anywhere, such as [here](http://prinsig.se/weekee/files/80211g.zip) (from the R3000/ZV5000/nx9105 wiki).

Then simply unload the bcm43xx driver and then load it again. Now you should be able to configure your wireless interface with a *real free driver*. :)


Håkan[/QUOTE]


has to be 
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys

It has worked for me, I first used the !! the mistake I made before was that I put the firmware in /lib/firmware/ instead of /lib/firmware/2.6.15-23....

I have a linksys wpc54g ver. 3

---

### Post by Shaggy on 2006-06-01
The above post is very important.  I just got it working by doing this and am currently posting wirelessly, using the bcm module.  Automatically set itself to 11Mb, and is giving me more information and useability than ndiswrapper did.

I didn't have to use the deb package or anything, just a zipped up driver file that I downloaded using the fwcutter help file.  Someone should add that little step in the wiki, it would more than likely help a lot of people.

One thing that I'm worried about though is that once a update to the kernel becomes available that I'll have to recut the firmware into the new path. Which isn't that big of a deal but people should be warned of this as well.

---

### Post by huppy on 2006-06-01
[QUOTE=Shaggy]I didn't have to use the deb package or anything, just a zipped up driver file that I downloaded using the fwcutter help file.  Someone should add that little step in the wiki, it would more than likely help a lot of people.[/QUOTE]

Sorry, could you explain briefly how you did this without the deb package?  I have the driver - bcmwl5.sys - but I have no internet connection without the wireless so have been unable to apt-get anything.  When I try the fwcutter command it is not installed.  How did you do it?

---

### Post by obey43 on 2006-06-01
can someone please post a bcm43xx-fwcutter deb, because i don't have acess to it from the repositories on the computer, but can transfer it from a disk?


also maybe the .inf and .sys files? i cant find them on google

---

### Post by huppy on 2006-06-01
hw-tph provides a link to a zip file containing the .inf and .sys.  As for the .deb, i'm waiting for the same thing!  unless the wizard shaggy's method will work ;)

---

### Post by obey43 on 2006-06-01
[QUOTE=derk.d]has to be 
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys

It has worked for me, I first used the !! the mistake I made before was that I put the firmware in /lib/firmware/ instead of /lib/firmware/2.6.15-23....

I have a linksys wpc54g ver. 3[/QUOTE]


so i did this exactly, with no sucess.

iwlist scan and sudo iwlist scan both show no scan results

iwconfig shows the device perfectly.

how else can i troubleshoot this?

---

### Post by gesho on 2006-06-01
**hw-tph**: 
> fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys
would this also work for broadcom 1370?

I upgraded to Kubuntu 6.06 today. 
and big improvment: before I only saw eth0 thernet in Network connection.
now I also see eth1 wireless card - disabled. and when I try to enable it - thing always fails, interface remaicn disabled. any advice?

---

### Post by hw-tph on 2006-06-03
Just for the record - I have had big problems getting WPA authentication working using NetworkManager but found out I only had to create the file /etc/default/wpasupplicant and add the following line:```
ENABLED=1
```
WPA works great now. I'm very impressed with how well this works but I am also more than a tad annoyed that this isn't outlined anywhere that I can see. It should be a huge popup (with the option to disable, of course) if you try to connect to a WPA network without having this simple config file setup.

Håkan

---

### Post by panki on 2006-07-04
You can find the .deb here: [http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/](http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/)  Which is the official ubuntu tree (but instead of apt to it, I http to it) \\:D/

---

### Post by ubunturules on 2006-07-04
This is the easiest way to do it.
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps)

---

### Post by bunnicula on 2006-07-05
I followed the instructions in the second post but when I run "modprobe ndiswrapper", I get the following error:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by ubunturules on 2006-07-05
make sure you did ndiswrapper -m before modprobe ndiswrapper.

---

### Post by Seamus on 2006-07-18
> **hw-tph said:**
> Just for the record - I have had big problems getting WPA authentication working using NetworkManager but found out I only had to create the file /etc/default/wpasupplicant and add the following line:```
ENABLED=1
```
WPA works great now. I'm very impressed with how well this works but I am also more than a tad annoyed that this isn't outlined anywhere that I can see. It should be a huge popup (with the option to disable, of course) if you try to connect to a WPA network without having this simple config file setup.

Håkan

This could be the breakthrough I am loking for, as I also want to use WPA.

Can you confirm if this is configured on a powerbook, without ndiswrapper, and using the BCM4306 wifi card?

---

### Post by GlennB on 2006-09-05
Hi,

> **derk.d said:**
> has to be 
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys



I came unstuck at this point. I'm trying to load the driver for the BCM4318 on a Dell Inspiron 1300. Problem is, I've compiled a new kernel and I don't seem to have the corresponding directory in /lib/firmware.

uname -r give me 2.6.15.7-ubuntu1-glenn. However, /lib/firmware seems to only have entries for the 'stock' kernels, as below:

```
glenn@glenn-laptop:/lib/firmware$ ls -l
total 8
drwxr-xr-x 3 root root 4096 2006-05-31 01:53 2.6.15-23-386
drwxr-xr-x 3 root root 4096 2006-09-02 14:58 2.6.15-26-386

```
Can anyone offer any advice on how I form the correct command line to sort out the firmware? Am I missing something obvious here?

Thanks,

Glenn.

---

### Post by JackTheKnife on 2006-09-05
> **kwah said:**
> There are some [pages on the Wiki]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=broadcom") describing how to cook broadcom wireless cards. You have two options: 1. to use bcmxxx kernel driver 

I went through that installation and finally Ubuntu can use wifi card (Linksys WPC54G), but I have still problems to get to the Internet.

After reboot network icon shows that everything is OK (strenght 100%, etc), but DHCP doesn't resolve settings. Event when I put static IP after reboot I need to go to System->Administrator->Networking and do something with wifi card (for ex. deactive and active again or change some numbers for static IP) to get connected to the Internet.  

Any idea what is wrong? Thanks.

---

### Post by Paul133 on 2006-09-05
The best tutorial I know of, which worked very well for me, is this one: [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902) Good luck!

---

### Post by JackTheKnife on 2006-09-05
How I can use 'ndiswrapper' instead of 'cm43xx-fwcutter'which I already using. I want to check if I will get those same problems with ndiswrapper.

---

### Post by Kaneda_help_me on 2006-09-06
> **obey43 said:**
> so i did this exactly, with no sucess.

iwlist scan and sudo iwlist scan both show no scan results

iwconfig shows the device perfectly.

how else can i troubleshoot this?

yea, i'm having the exact same problem.

---

### Post by pratik5705 on 2006-09-15
I have a Dell Inspiron 8600 with the broadcom wireless card. I read  this post and the two conflicting methods. I tried the one with ndiswrapper first, it did not work. Then i tried the fwcutter approach. Guess what, it worked... 

Thanks to Hakan. I think there should be a wiki for this. It was really easy to do. Only thing is that, i had to use sudo bcm43xx-fwcutter instead od sudo fwcutter. Thanks to derk.d for pointing this out. 

I had tried Ubuntu earlier, the previous version and removed it because i wasnt able to get wireless working.  Then I tried Suse, although i got wireless working using ndiswrapper, there were a lot of other issues. I think ubuntu is what is says, linux for the rest of us.

---

### Post by Ubuntop on 2006-09-15
HP pavilion zd7000 (zd7010us) with BCM4306 (rev 02) wireless radio working.

I am posting this because it caused me many hours of troubleshooting.  First off, I agree with Håkan, in that I should be using the BCM43xx driver native to Ubunto Drake.  In my trials, I was never able to get it working though, even using fwcutter and many different bcmwl5.sys files.  I thank Håkan for pointing out the correct location for the firmware files; in this post.  I also tried using several versions of the bcmwl5.inf 'wrapped' by ndiswrapper to no avail.

Here is what I did:

Get rid of ndiswrapper.
```
 sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper 
```

If you have previously blacklisted the bcm43xx driver, remove it from /etc/modprobe.d/blacklist

Incidentally, I installed the rfswitch-1.1 (though I doubt it helps on this laptop) found here:
[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)
It does turn the radio light on though.

I believe the key to my final success was the location of the firmware files.  There are several Ubuntu articles that show that you put the files under /lib/firmware, when you should actually place them under /lib/firmware/'kernal version'. 

to find your version
```
 uname -r
```

Now simply follow  Håkan's instruction.  After doing so, your card should immediately connect, although subsequent connections can take up to a minute to get an IP (on DHCP); though you can force a DHCP request.

to scan for access points use:
```
 iwlist scan 
```

> **hw-tph said:**
> I would strongly advice against using ndiswrapper since there is a real driver now (if you use Dapper the bcm43xx driver is installed by default).

```
apt-get install bcm43xx-fwcutter
``` installs the firmware cutting tool which you need. Then you simply type ```
fwcutter -w /lib/firmware/2.6.15-23-k7 /path/to/bcmwl5.sys
```

Replace "2.6.15-23-k7" with the name of the kernel you are currently running. The file bcmwl5.sys comes from the Windows Broadcom driver package, which you can get from pretty much anywhere, such as [here](http://prinsig.se/weekee/files/80211g.zip) (from the R3000/ZV5000/nx9105 wiki).

Then simply unload the bcm43xx driver and then load it again. Now you should be able to configure your wireless interface with a *real free driver*. :)


Håkan

---

### Post by toosweetnitemare on 2006-09-15
root@master-laptop:/home/master/Desktop# uname -r
2.6.15-26-386
root@master-laptop:/home/master/Desktop# apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@master-laptop:/home/master/Desktop# fwcutter -w /lib/firmware/2.6.15-26-386 /home/master/drivers/bcmwl5.sys
bash: fwcutter: command not found



anyone else get this error? any ideas on how to fix it?

---

### Post by greyash99 on 2006-09-15
Where can you find what kernal your using?

---

### Post by Ubuntop on 2006-09-16
> **toosweetnitemare said:**
> root@master-laptop:/home/master/Desktop# uname -r
2.6.15-26-386
root@master-laptop:/home/master/Desktop# apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@master-laptop:/home/master/Desktop# fwcutter -w /lib/firmware/2.6.15-26-386 /home/master/drivers/bcmwl5.sys
bash: fwcutter: command not found



anyone else get this error? any ideas on how to fix it?


use bcm43xx-fwcutter as the command, not just fwcutter.

---

### Post by pdc4342 on 2006-09-30
Hi, I have been following this excellent thread and had an immediate success and WiFi was available from by Belkin card on ad AMD based desktop using the following:
# Copy the bcmwl5.sys and bcmwl5.inf files used in Windows to new directory ~/bcm4306
apt-get install bcm43xx-fwcutter
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-26-386 ~/bcm4306/bcmwl5.sys
sudo rmmod bcm43xx 
sudo modprobe bcm43xx 

I just needed to set the WEP code and got sensible output from iwlist scan and iwconfig although the speed seemed to be at 11mbs. 

Now came the problem which has baffled me as a relative newbie. When I rebooted eth1 was lost and count not be reactivated. 

After many trials I restarted with an earlier kernel and repeated with the kernel suitably changed and again instant success till a reboot with no access which is where I am now. I have tried removing and reistalling bcm43xx to no effect. The only hint is that  /et/network/interfaces does not contain the wep code which was there at some point (in plain text!)

I am at a loss as the card driver is obviously workins as iwlist scan gives output which comes and goes depending on whether eth1 is activated and again changes when I turn the router/Wifi off. iwlist output is
....
eth1      Scan completed :
          Cell 01 - Address: 00:0D:54:F9:7D:F0
                    ESSID:"53RG87EA"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-158 dBm
                    Extra: Last beacon: 96ms ago

and 
iwconfig
...
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"53RG87EA"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can anyone help pls?

---

### Post by jeffreycreel on 2006-09-30
I originally had problems with this too. I tried the FW cutter, but could not get eth1 to configure, and when I used ndiswrapper, I could not get wlan0 to show up as an interface. for a couple of days I searched and searched for fixes, deleting the FW directory, purging this and that. Eventually I just reinstalled dapper. From the fresh install I used the ndiswrapper method and it worked perfectly!

---

### Post by pdc4342 on 2006-10-01
I also tried the ndiswrapper route with even less success. I will now wait until I have to do a reinstall or somebody I get any further suggestions. It was only pride really as I have a working ethernet connection which I normally used anyway.

If anybody wants some light entertainment the trials of a newbie to Ubuntu (although one with 40 years round computers) can be found at [www.pcurtis.com/ubuntu.htm](www.pcurtis.com/ubuntu.htm). Overall I have been very impressed by both Ubuntu Linux and the community spirit - I hope as I go up the learning curve to have something to offer in return. There is no way back now.

---

### Post by bluefuse on 2006-10-01
I have a compaq presario 2210US with the broadcom 4306, I had had poor results with the fwcutter, in order to remove this and all of the configuration simple open a terminal and say: sudo apt-get remove bcm43XX-fwcutter (this is the broadcom firmware cutter)

now I had great luck with the ndiswrapper, here's how I setup my broadcom 4306.

sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i (installs the driver, you should place the .sys file from your driver cd on the desktop right click and paster to desktop)

then

sudo ndiswrapper -l ( it will then say hardware present/driver present )

sudo modprobe ndiswrapper

then goto system > admin > network, you must activate the WAN that is there if not you will have to do this all over again!!!

set you setting, dhcp or static....etc and reboot

then open up a terminal and I think its ( sudo ndiswrapper -m )

you might want to look into..... wifi-radar

---

### Post by bluefuse on 2006-10-01
here's how I did it.

sudo ndiswrapper -i /media/cdrom0/swsetup/bcmlw5.inf
sudo ndiswrapper -l
driver found, hardware present
sudo modprobe ndiswrapper
goto "administrator" goto "Network" goto "Wireless Adapter" then "Activate"

"reboot"

sudo ndiswrapper -m

"reboot"

you should now be up and running

---

### Post by alecjw on 2006-10-01
> **obey43 said:**
> since dapper is out now...

can someone explain the most efficient/correct/updated way to get a broadcom (4306 specifically for me) wireless card up and running??

my only problem i have ever had with ubuntu.

: (

note: i have tried using the firmware .deb at [http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_i386.deb](http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_i386.deb)

it does not work with the current kernel.

i don't have too many options, because of course i have no connectivity on the computer.  

any suggestions?

I have one. I bought a more compatable card instead.

---

### Post by kikos on 2006-10-01
I have my 4306 working rock solid using ndiswrapper.  NDISWRAPPER IN EDGY IS BROKEN.  But THERE IS A FIX.  This fix follows:
1.  Make sure the ndiswrapper-utils and ndiswrapper-common packages are installed.
2.  ```
sudo rm /usr/sbin/ndiswrapper
```
3.  ```
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

Credit for the fix goes to discord at [https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983)

Once you have fixed that issue, then you can do the whole process of installing the broadcom drivers.  Look at the other how-to's for more thorough steps as this is just an overview:

1) Make sure you add ndiswrapper to the /etc/modules file if it's not already there
2) modprobe ndiswrapper to make sure it's loaded
3) ```
sudo ndiswrapper -i ~/bcmwl5.inf
```
4) make sure your /etc/network/interfaces is set correctly
5) make sure bcm43xx is NOT blacklisted in /etc/modprobe.d/blacklist
6) modprobe bcm43xx

At this point your broadcom 4306 should be able to see wireless access points.  Post a reply if you can now see the access points, but cannot connect.

---

### Post by pdc4342 on 2006-10-02
Thanks for all the helpful postings.

I have followed the concensus and changed from the fwcutter approach to the ndiswrapper one. The various instructions wereslightly inconsistent and had to be modified slightly - the following may help those following.
1. sudo apt-get remove bcm43XX-fwcutter did not remove the module as eth1 was still present after a reboot in System _> administration -> Network
2. rmmod bcm43xx seemed to remove the old driver as eth0 disappeared after a reboot.
3. sudo apt-get install ndiswrapper-utils
4. sudo ndiswrapper -i bcmwl5.sys should read sudo ndiswrapper -i bcmwl5.inf as I eventually found as I had an invalid driver when I did a ndiswrapper -l (ndiswrapper -e removes faulty drivers) 
5. sudo modprobe ndiswrapper alone did not produce the eth1
6. sudo ndiswrapper -m and "reboot" produced eth1
7. Set up and Activated - everything worked at this point and I could activate/deactivate eth1 and eth0 with no problems - light on card goes on and off etc. and I kept it up and running for a long period on the internet.

I then Rebooted and eth1 could no longer be activated (other than the light going on and off) - as far as I can tell the situation is absolutely identical to that from the fwcutter approach. I am now even more baffled than before - I seem to be good at creating work once systems!!

How do I find out what is actually being loaded?
I did a dmesg and I extract the following bits of interest
pcurtis@triton-ubuntu:~$ dmesg | grep 43xx
[17179589.140000] bcm43xx driver
pcurtis@triton-ubuntu:~$ dmesg | grep ndis
[17179597.896000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
pcurtis@triton-ubuntu:~$

Do I need to add anything to a blacklist having done a rmmod bcm43xx ?
What does the Network Configuration at boot - is it the same as the Network Manager and what control files exist for either/both? Are there any more tools/diagnostics other than iwconfig iwlist and ifconfig ?
Peter

---

### Post by kikos on 2006-10-02
On my computer I need to have both ndiswrapper and bcm43xx modules loaded.  This means that bcm43xx is not blacklisted on my computer (i.e. no entry for bcm43xx in the blackist file).  Otherwise, the wireless interface will not work.

Also, try this command to restart your network without rebooting the computer.  It ouputs to the screen so you can see what's going on as the computer tries to restart the network.

```
/etc/init.d/networking restart
```

Finally, try to comment out any references to your ethernet interface in /etc/network/interfaces.  i.e:

```
#iface eth0 inet dhcp
#auto eth0
```

For some reason, having both ethernet and wireless interfaces simultaneously activated on my laptop causes wireless connection problems.

---

### Post by pdc4342 on 2006-10-03
> **kikos said:**
> On my computer I need to have both ndiswrapper and bcm43xx modules loaded.  This means that bcm43xx is not blacklisted on my computer (i.e. no entry for bcm43xx in the blackist file).  Otherwise, the wireless interface will not work.

I found that out the hard way - the machine froze during boot whilst configuring the network and I had to get in from the ActiveCD

> **kikos said:**
> Finally, try to comment out any references to your ethernet interface in /etc/network/interfaces.  i.e:

```
#iface eth0 inet dhcp
#auto eth0
```

For some reason, having both ethernet and wireless interfaces simultaneously activated on my laptop causes wireless connection problems.

It made no difference in my case

I tried wifi-radar as suggested above which only worked once after which it would not get an IP address. It is great on the lap-top however and fills in another shortfall.

I am begining to think I will have to live with a cable although I have learned a lot (but have a lot more to learn)

---

### Post by Pieterjan on 2007-06-29
Thanks hw-Ttph,

I've got an acer aspire 1500 with a broadcom4306 wireless adapter. Finally I found someone that knows Ubuntu . I installed the previous version of ubuntu but the wireless adapter was an obstacle. Because Ubuntu is new for me, I had some troubles with the commands.   

You wouldn't believe how may hours I've spent on ndiswrapper. On every forum that exists, I've been searching for an solution. 

Today I saw your post from 2006 and I tried the command for fwcutter . Problem was solved.I didn't even had to unload the driver . Just a reboot.

Thanks a lot. And now I can ban windows from my laptop.


Grtz,


Pj

---

### Post by John Jason Jordan on 2007-07-06
Ubuntu Feisty, amd64, upgraded from Edgy, upgraded from Dapper, upgraded from Breezy, upgraded from Hoary. All amd64, and ever since Hoary I have had my Broadcom 4306 working with ndiswrapper. System is completely up to date.

Yesterday I was at the university and discovered that the wireless was not working. It was as if the wireless network was down, i.e., no signal. But everyone else in the room had no problems connecting to the university wireless network. I tried various things, but could not get it to see a signal. The previous time I used it was two weeks earlier, and it worked fine then. I am at home now where I use ethernet, but I can always still see signals from the neighbors. However, something is still wrong because I do not see any signals at all.

Here is what I did at the command line:

jjj@Devil5:~$ uname -a
Linux Devil5 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
jjj@Devil5:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
netbc564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
jjj@Devil5:~$ sudo ndiswrapper -v
utils version: 1.9
driver modinfo: could not open ndiswrapper: No such device
jjj@Devil5:~$ sudo modprobe ndiswrapper
jjj@Devil5:~$ 

I checked to make sure bcm43xx is still blacklisted, and it is. 

I can't figure out why ndiswrapper -l shows everything is fine, but ndiswrapper -v says there is no such device. I also do not understand why ndiswrapper -l shows the bcm43xx as an alternate driver, when it is blacklisted. I also get the following:

jjj@Devil5:~$ sudo modprobe bcm43xx
jjj@Devil5:~$ sudo rmmod bcm43xx
jjj@Devil5:~$ sudo modprobe bcm43xx
jjj@Devil5:~$ 

How can I modprobe a module that is blacklisted, and even after removing it?

I hope someone has some suggestions, 'cause I'm out of ideas.

---

