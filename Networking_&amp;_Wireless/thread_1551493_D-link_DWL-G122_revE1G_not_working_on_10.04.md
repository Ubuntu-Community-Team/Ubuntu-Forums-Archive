---
title: "D-link DWL-G122 revE1G not working on 10.04"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by Trazan on 2010-08-12
Hey all i got problem connecting my usb adapter to 10.04...spent last couple of days trying different fixes but with no luck.

lsusb shows it
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c0f D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:72:90:a3  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe72:90a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14215746 (14.2 MB)  TX bytes:1226320 (1.2 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:bd:b9:82:1c:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

lsmod | grep rt2800usb
```
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
crc_ccitt               1339  2 rt2800usb,irda

```

im on a new and updated version nothing done or installes atm [fecked kernel up yesterday ;) ]
and besides that blacklisting rt2800usb aint working either just removes entire wlan from ifconfig. need help and please explain like im a seven year old kid ;)

---

### Post by bkratz on 2010-08-12
I think this may be worth looking at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

---

### Post by Trazan on 2010-08-12
thx for the swiftness

although what i can see its intended for "ID 07d1:3c0d" and my id is "07d1:3c0f" might not be a biggie but ill give it a go

worst case new install ;)

---

### Post by Trazan on 2010-08-12
Nope didnt work either i followed and swapped "0d" to "0f" blacklisted drivers and ended up having no netcard again in ```
hwinfo --netcard
```

prob i see it is noone knows for sure what chipset 07d1:3c0f uses :(

---

### Post by bkratz on 2010-08-12
Sorry, when I googlubuntu (useful search engine) it came back with that site. Reading through it post 7 refers to you particular ID number.


Although expired, the user never continued the info, here is another one. Perhaps you can search for this user and see what the problem was.

[https://bugs.launchpad.net/ubuntu/+source/rutilt/+bug/587093](https://bugs.launchpad.net/ubuntu/+source/rutilt/+bug/587093)

---

### Post by bkratz on 2010-08-12
Lot of information in other languages, here is one look specifically at the last post on page two

[http://translate.google.com/translate?hl=en&sl=sv&u=http://ubuntu-se.org/phpBB3/viewtopic.php%3Ff%3D103%26t%3D47460&ei=RSVkTKjyM5CknQe_jZhe&sa=X&oi=translate&ct=result&resnum=8&ved=0CD0Q7gEwBzgK&prev=/search%3Fq%3D07d1:3c0f%26start%3D10%26hl%3Den%26sa%3DN](http://translate.google.com/translate?hl=en&sl=sv&u=http://ubuntu-se.org/phpBB3/viewtopic.php%3Ff%3D103%26t%3D47460&ei=RSVkTKjyM5CknQe_jZhe&sa=X&oi=translate&ct=result&resnum=8&ved=0CD0Q7gEwBzgK&prev=/search%3Fq%3D07d1:3c0f%26start%3D10%26hl%3Den%26sa%3DN)

---

### Post by Trazan on 2010-08-12
thx bkratz for taking yer time....the one on swedish i already tried and dint work...only makes usb dong completely disappear =? no solution :(

launchpad bug seems interesting and will try and lookup on that gguy to see if i can get some answeres

---

### Post by Trazan on 2010-08-12
hmmm no luck finding the user since he havent been active since he posted that bug.....

although some googling later i found a link bout the dong
[http://www.modem-help.co.uk/D-Link/DWL-G122-AirPlus-G-11bg-WLAN-USB-Adapter--rev-E-.html]("http://www.modem-help.co.uk/D-Link/DWL-G122-AirPlus-G-11bg-WLAN-USB-Adapter--rev-E-.html")

which tells me something bout using a chipset called RT3000U WLAN-N
search continues...

---

### Post by Trazan on 2010-08-12
UPDATE (20 cup of beans later)

i downloaded DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.tar.bz2 from ralink corp
compiled etc etc
then added in /etc/modprobe.d/blacklist.conf
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
```

made a new dir in /etc/Wireless/ called RT2870STA
copied and renamed file /etc/Wireless/RT3070STA/RT3070STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat

added RT3070STA in /etc/modules

restarted and now i can see network with iwlist ra0 scan

:P finally beeing able to get wireless up and running...thx bkratz

will try and make a better explanation what i di after the coffe wears off

---

### Post by bkratz on 2010-08-12
> **Trazan said:**
> UPDATE (20 cup of beans later)

i downloaded DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.tar.bz2 from ralink corp
compiled etc etc
then added in /etc/modprobe.d/blacklist.conf
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
```

made a new dir in /etc/Wireless/ called RT2870STA
copied and renamed file /etc/Wireless/RT3070STA/RT3070STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat

added RT3070STA in /etc/modules

restarted and now i can see network with iwlist ra0 scan

:P finally beeing able to get wireless up and running...thx bkratz

will try and make a better explanation what i di after the coffe wears off

Wish I could have done something useful--you did all the work, but I did just find this before seeing your last post

[http://translate.googleusercontent.com/translate_c?hl=en&sl=de&u=http://www.modem-help.co.uk/D-Link/DWL-G122-AirPlus-G-11bg-WLAN-USB-Adapter--rev-E-.html&prev=/search%3Fq%3D07d1:3c0f%26start%3D20%26hl%3Den%26sa%3DN&rurl=translate.google.com&usg=ALkJrhjGZsWbqk2Lto6FUSkhbvcwFip8JA](http://translate.googleusercontent.com/translate_c?hl=en&sl=de&u=http://www.modem-help.co.uk/D-Link/DWL-G122-AirPlus-G-11bg-WLAN-USB-Adapter--rev-E-.html&prev=/search%3Fq%3D07d1:3c0f%26start%3D20%26hl%3Den%26sa%3DN&rurl=translate.google.com&usg=ALkJrhjGZsWbqk2Lto6FUSkhbvcwFip8JA)

You seem to be right about the chipset driver.

---

### Post by Trazan on 2010-08-12
Working or atleast must be since im using it now hehe
sometimes banging yer head helps...i'll try to clean this up and make a little guide tomorrow how i solved it

many thx still kbratz im still rusty on ubuntu been away for too long i guess

---

### Post by narcisgarcia on 2010-09-02
Completing the Trazan's steps:

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)

2. Unpack the tar & bz2 source package, be careful to don't leave spaces in the extracted directory name, open a terminal and go to contents' directory

3.
```

cp RT2870STACard.dat RT3070STACard.dat
cp RT2870STA.dat RT3070STA.dat
cp common/rt2870.bin common/rt3070.bin
sudo make
sudo make install
```

4. Add to /etc/modprobe.d/blacklist.conf
```

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta

```

5. Make a new dir and copy a RT2870 file in it:
```

sudo mkdir /etc/Wireless/RT2870STA
sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

```

6. Add RT3070STA in /etc/modules

7. Restart the system

As I see, Ralink corp published a RT2870 driver fo RT3070, that must be corrected and adapted to work with RT3070 USB device.

---

### Post by heke on 2010-09-03
Yes indeed.

The Dlink Dwl-g122 rev.E1 drivers seem to be in disorder. The kernel regognizes this particular wlan stick and sets up a driver but that particular driver just don't work. 

I would like to set the right driver up in my xubuntu 10.04, according to the trazan-narcisgarcia -procedure, but I can't do it at the moment.  It is because the xubuntu distro doesn't contain some necessary files in the /lib/modules/2.6.32-24-generic/build directory. 

If anybody knows their whereabouts I would be rather happy. I wont install any full ubuntu because my laptop is very old 700Mz 256Mb computer.

---

### Post by narcisgarcia on 2010-09-03
If you have the "linux-generic" package installed, then try to install the "linux-headers-generic" also.

The "build-essential" package may help too.

---

### Post by heke on 2010-09-05
Thank you all for the help. At this moment I am connected through the dwl-g122 rev.E1 wireless usb adapter. It seems to work and so my problem is solved.

In xubuntu I had toi load the ccg compiler and the exactly same version of headerfiles as the kernel version I have before I was able to follow the peculiar prosedure of installing a working driver.

I did encounter a small error at the following command

sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
there was no such file (RT3070STA.dat) in the from directory, and so I just copied the one there was.

---

### Post by jaapkroe on 2010-09-20
Thanks!! It works!

One small note, I think the module name should not be capatalized.
So add rt3070sta instead of RT3070STA to /etc/modules

At least
```
sudo modprobe rt3070sta
```
worked for me (didn't reboot yet).

Thanks again, I can finally remove the mess of cables running trough my room :)

---

### Post by jtirila on 2010-10-12
OK, some 10.10 specific initial results. It seems to work, but only after some tweaking, and honestly, I don't know if what I did was right.  

I tried the procedure described by narcisgarcia on 10.10, and run into some problems during the build process. I don't have the error message(s) at hand, but the functions usb_buffer_alloc and usb_buffer_free have something to do with the issue. 

("Implicit declaration of usb_buffer_alloc" or something like that, and exiting with code 2.)

From quick googling I concluded that those two functions have been renamed in the recent versions of the Linux kernel to usb_alloc_coherent and usb_free_coherent. 

Those function names are used in DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/os/rt_linux.h. I simply changed usb_buffer_alloc into usb_alloc_coherent and usb_buffer_free to usb_free_coherent (lines 1014-1015) and retried make && make install. With this addition to narcisgarcia's instructions I got it working and am using it right now. 

HOWEVER, this is all based on very brief experimentation so I'd love to see someone more educated confirm that right things are being done here. 

I'm half guessing that the issue relates to changes in ther Linux kernel somewhere between versions 2.6.32 and 2.6.35, and not to Ubuntu alone.

(Update: rephrased a bit for clarity)

---

### Post by Magic_Spehar on 2010-10-13
Hi Jtirila,

Your suggestion is correct.  The kernel is the problem with Ubuntu 10.10.  My D-link DWL G-122 adapter is working fine since I changed my grub. 

Now the 32-kernel is loaded instead of the default 35-version. With the 35-version the adapter is detected but there's no connection.

---

### Post by jtirila on 2010-10-15
> **Magic_Spehar said:**
> 

Your suggestion is correct.  The kernel is the problem with Ubuntu 10.10.  My D-link DWL G-122 adapter is working fine since I changed my grub {to use kernel 2.6.32}. 

Yeah, so it seems. I considered that, too, but the newer kernel enables suspend for me so that's why went into modifying the DWL-G122 driver sources.

It really seems to work fine after those two simple text edits and a rebuild.

---

### Post by melancholia101 on 2010-11-27
I had exactly the same problem with 10.04 but the above solution didn't work. After many hours I gave up and decided to try installing 10.10 and it worked right off the bat. 

Makes me wonder if the labelling of these wireless adapters is different from country to country (I bought mine in Spain).

Anyway if your having problems with 10.04 try a copy of 10.10 as it may fix your problems.

---

### Post by baubas101 on 2011-01-24
hi there ;) 

so for me neither any of the methods dont work... first i tried ndiswrapper on 9.04 then 9.10 then 10.04 no chance. this method also dont work... what i do wrong ? :( ... rrr dlink rrrrr. and the problem is that i have hp nx6125, this lap dont have wifi card inside,,, and even i tried to put inside some card but it dont work (i found that i need to remake+update bios, but its still little to hard for me :( maybe ome day ) so maybe someone have an idea how to get taht dlink work, now hardware drivers shows that the driver is loaded but not in use... 
thanks ;)

tried on win- adapter itself work
ipconfig no info about wifi
no light blink etc on adapter
lsusb
Bus 001 Device 003: ID 07d1:3c0f D-Link System

---

### Post by Samutheus on 2011-02-25
> **narcisgarcia said:**
> Completing the Trazan's steps:

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)



I downloaded this driver from Ralink but couldn't get it to work. It seems to be an updated version compared to the one Trazan built his instructions around.

However, the driver attached to [narcisgarcia's post]("http://www.backports.ubuntuforums.org/showpost.php?p=9796983&postcount=12") brought my DWL-G122 E1 back on-line.

---

### Post by Jean-Claude Tergal on 2012-01-12
Great! It works for me!:D
You're a real McHouse Narcis!

> **narcisgarcia said:**
> Completing the Trazan's steps:

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)

2. Unpack the tar & bz2 source package, be careful to don't leave spaces in the extracted directory name, open a terminal and go to contents' directory

3.
```

cp RT2870STACard.dat RT3070STACard.dat
cp RT2870STA.dat RT3070STA.dat
cp common/rt2870.bin common/rt3070.bin
sudo make
sudo make install
```4. Add to /etc/modprobe.d/blacklist.conf
```

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta

```5. Make a new dir and copy a RT2870 file in it:
```

sudo mkdir /etc/Wireless/RT2870STA
sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

```6. Add RT3070STA in /etc/modules

7. Restart the system

As I see, Ralink corp published a RT2870 driver fo RT3070, that must be corrected and adapted to work with RT3070 USB device.

---

### Post by Jean-Claude Tergal on 2012-01-22
Hi,

A few days later, my Dlink does not work anymore.
I suppose it's the consequence of an update.
The solution is to update the blacklist.

If you have the same problem, follow this step (obviously, you have to apply the solution of narcisgarcia before):

Identify the loaded driver:
```
$lsmod | grep rt
```You will find something like this:
```
rtxxxxsta             602849  1 
```For example rt5370sta

Unload this module:
```
$sudo rmmod rt5370sta
```Load the compiled module
```
$sudo modprobe rt3070sta
```Try you're key! It's work?
So add rt5370sta to /etc/modprobe.d/blacklist.conf

---

### Post by Jean-Claude Tergal on 2012-01-27
Hi guys !
The solution above works fine but doesn’t work long! ;)
Since I’ve upgraded to the kernel 2.6.32-38, my DLink doesn’t work anymore. :(
 
So, no  driver is loaded at startup.
If I type :
```
sudo modprobe rt3070sta
```It returns:
```
 FATAL :Module rt3070sta not found.
```If I restart with the previous kernel (2.6.32-37) , it works fine.
 
It seems that the new kernel don’t know the path /etc/Wireless ? Am I right ?
 
Does anybody know how solve this problem please ?
Thank you

---

### Post by Jean-Claude Tergal on 2012-01-28
It's seems that the "etc/Wireless" directory is created by compiling/installing the driver.
I can't imagine recompile the driver each time I'm upgraded to the newer kernel.
Should I do that?

---

