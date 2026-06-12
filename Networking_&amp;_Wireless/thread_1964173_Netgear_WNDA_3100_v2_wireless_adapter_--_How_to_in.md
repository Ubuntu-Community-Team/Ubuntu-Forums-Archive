---
title: "Netgear WNDA 3100 v2 wireless adapter -- How to install?"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by marianlibrarian on 2012-04-23
I searched for days and found several threads with various techniques. 

This one: [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)
This one: [http://ubuntuforums.org/showthread.php?t=1797795](http://ubuntuforums.org/showthread.php?t=1797795)

I really thought I had a solution with the one that said [SOLVED]. My problem is that all of these are from earlier versions of Ubuntu. I just installed 11.10 - **NO SYNAPTIC**. It has been replaced with something called - Ubuntu Software Center. I guess it would be a nice thing if I didn't need to use install drivers for a Netgear N600 Wireless Dual Band USB Adapter WNDA3100v2.

This part of the instructions seemed to work:
sudo su #
cd /tmp
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
mv ar*.fw /lib/firmware

then I went to [http:kb.netgear.com/app/answers/detail/a_id/12115]("http://kb.netgear.com/app/answers/detail/a_id/12115") however, the file on my installation CD was more recent, so did not use this link.

I installed WINE after searching everywhere. Finally found it in the Software Center - don't remember how.

However, the instructions: "Use Wine to browse that C:\ drive and you will find a folder WNDA3100v2." - Does NOT work. Wine is not in a place you can "use" it. I can right click on a "exe" file and select from the drop down menu Open With and then select "Wine Windows Program Loader". -- That's it. 

--- Software Center --- I feel like I just walked into SAMS or Walmart  --- which is where I got the Netgear thing because that was the only USB network adapter they had.

Does anyone know how to get to the "C:\\" that Wine created?

I apologize for posting earlier on one of the above mentioned posts. I did not realize how old it was and that the title had the word [SOLVED].

---

### Post by chili555 on 2012-04-23
I think this is what you need. Post back if you need additional guidance.

These are for usb.id 0846:9020. Please run:```
lsusb
```If that is not your device, don't use these files and post back the result of lsusb.

---

### Post by marianlibrarian on 2012-04-23
Here is result of lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 004 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard

---

### Post by chili555 on 2012-04-23
Hmmm. I don't see a Netgear WDNA 3100 v2 device. Isn't is a USB device? Was it plugged in at the time?

---

### Post by marianlibrarian on 2012-04-23
:oops: It wasn't because I had tried removing the software and it told me to unplug it.

Anyway, here it is now:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 004 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n [Broadcom BCM4323]

---

### Post by chili555 on 2012-04-23
Ahh! Much better. You have 0846:9011, so don't use the files I attached; use these instead. You will want to install bcmn43xx32.inf or bcmn43xx64.inf depending on whether you have a 32-bit or 64-bit system:```
arch
```Again, post back if you need guidance.> I just installed 11.10 - NO SYNAPTIC.If you want it, and I prefer and use it, simply do:```
sudo apt-get install synaptic
```

---

### Post by marianlibrarian on 2012-04-23
result from arch
i686

Downloaded zip. I have put a folder in my home folder to contain the installation cd files and these new ones. There were other folders on the install cd like /bin and /language. I am putting the downloaded files in the same folder as the autorun.exe and setup.ini files.

I uninstalled and will now reinstall.

---

### Post by chili555 on 2012-04-23
> I uninstalled and will now reinstall.With the great and powerful ndiswrapper, correct?

---

### Post by marianlibrarian on 2012-04-23
ndiswrapper - it is installed but I am not sure how to use it. I was using Wine to do the installation process. :oops::oops::oops: very very

I am very lost in this new Software Center. I installed ndiswrapper but it is nowhere in any of the categories in the installed list. Wine is there but it is just a name in a list. Not clickable. I am lost lost lost.

---

### Post by chili555 on 2012-04-23
No problem. You seemed confident and resourceful so I omitted the details. I'll be happy to explain. First, go to the location of the zip file I attached; right-click it and select *Extract Here*.Now open a terminal and change directories to the location of the drivers I attached. For example:```
cd Desktop/some_folder/Broadcom_bcm43xx_USB_32_64bit_v2_amended
```Now we install the needed driver:```
sudo ndiswrapper -i bcmn43xx32.inf
```'i' means to **i**nstall. Now we check to see if it installed:```
ndiswrapper -l
```'l' is for **l**ist. If it says driver installed, device present, we're nearly there. 

Was a wireless interface created?```
iwconfig
```If you have a wlan0, click the Network Manager icon and try to connect.

Post back any errors, warnings, sparks or smoke, if any, and we'll try to fix it.

---

### Post by marianlibrarian on 2012-04-23
I cannot get into my Home directory where my /NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2 directories are. I used to be able to see the path in Synaptic. This is not available in the Software Center.

I am typing:

cd Home/NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2 

result: No such file or directory.

I capitalized the correct letters. I feel none too bright right now. I can't even find a directory:confused::oops:

---

### Post by chili555 on 2012-04-23
The abbreviation for Home/user in Linux is the tiny, cute ~. So try:```
cd ~/NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2 
```Actually, if you are already home, indicated by the ~ on your terminal, you can shortcut with:```
cd NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2
```

---

### Post by marianlibrarian on 2012-04-23
Thank you for your help. 

geneva@geneva-desktop:~/NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present

geneva@geneva-desktop:~/NetGear_CDfiles/Broadcom_bcm43xx_USB_32_64bit_v2$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I went to the "Edit Connections" and added a wireless connection to the Network Connections. 

Is now a good time to restart?

---

### Post by marianlibrarian on 2012-04-23
Hi Chili555, I have to go. The library closed at 17:30. I hope I see you tomorrow. Thank you so much for you kindness and patience. 

Have a nice evening or day (which ever comes first) ):P

---

### Post by chili555 on 2012-04-23
> **marianlibrarian said:**
> Hi Chili555, I have to go. The library closed at 17:30. I hope I see you tomorrow. Thank you so much for you kindness and patience. 

Have a nice evening or day (which ever comes first) ):PSee you then. Post back and I'll see your post. Please include:```
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. See you then.

---

### Post by marianlibrarian on 2012-04-24
Result of last request:

geneva@geneva-desktop:~$ dmesg | grep ndis
geneva@geneva-desktop:~$ 

Good Morning!

---

### Post by chili555 on 2012-04-24
Good morning! Please try:```
sudo modprobe ndiswrapper
dmesg | grep ndis
iwconfig
```I'll only be here for about another hour, so we need to crack this case!!

---

### Post by marianlibrarian on 2012-04-24
Result from previous commands:



:grin::grin::grin::grin::grin::grin:

I just unplugged my ethernet wire and ..... we have lift off!!!

Posting this using our Netgear WNDA 3100 v2 wireless adapter!!

THank you so much. I could not have done this without you.

---

### Post by chili555 on 2012-04-24
Awesome! I'm very glad it's working. Please use thread tools at the top to Mark Solved.

Post back if we can help you again.

---

### Post by marianlibrarian on 2012-05-29
I know this thread says [SOLVED] and it is sort of.... 
because I have to type in the following every time I restart the computer:

sudo modprobe ndiswrapper
--- askes for password

dmesg | grep ndis

iwconfig

It takes a minute or two but then the computer is connected to the network. I haven't waited to see if going to sleep will also cause the same problem.

Any reason why Ubuntu will not save this procedure?:confused:

---

### Post by marianlibrarian on 2012-05-29
I read the middle "sticky" for this forum about ndiswrapper. Very comprehensive. I typed the command lshw -C Network and following is the result:

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: e0:69:95:c6:8a:20
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR=Red]**driver=r8169**[/COLOR] driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 20:4e:7f:f2:7f:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx32 driverversion=1.56+,08/26/2009, 5.10.79.30 ip=192.168.1.109 multicast=yes wireless=IEEE 802.11g
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Hmmm..... driver=r8169 

According to the sticky document, I am supposed to put this driver on a blacklist and instructions are given.

> ndiswrapper won't work until you tell the system not to use the module  that's trying to claim the card.  You can prevent the system from  loading modules by adding them to '/etc/modprobe.d/blacklist'

So I followed the instructions regarding blacklisting. Now I am about to reboot as instructed.

I hope I can come back with [SUPER SOLVED] I will let you know.

---

### Post by marianlibrarian on 2012-05-29
Well I still have to: 
sudo modprobe ndiswrapper

after restart.

Once I do that everything runs just fine.

But when I typed in the above command, I saw the following message in my terminal window:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Does anyone know what that means? I followed the instructions carefully.

---

### Post by chili555 on 2012-05-29
Marian! You're back!!> Hmmm..... driver=r8169

According to the sticky document, I am supposed to put this driver on a blacklist and instructions are given.Nope; that's the ethernet driver, not wireless.> Well I still have to:
sudo modprobe ndiswrapper

after restart.

Once I do that everything runs just fine.Let's get the system to do that for you:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Does anyone know what that means? I followed the instructions carefully. You probably have a file blacklist *AND* a file blacklist.conf in your system. Let's see if we can consolidate. Please show me:```
cat /etc/modprobe.d/blacklist
```We'll fix it up.

---

### Post by marianlibrarian on 2012-05-30
Hi Chili555

I saw your note about the driver not effecting wireless. Since I don't have a wired machine, it made no difference. So I re-edited the file and simply deleted the line and saved it.

When I do cat /etc/modprobe.d/blacklist 

It returns an empty line.

I also:
sudo su echo ndiswrapper >> /etc/modules exitI have not rebooted yet, but will as soon as I post this and let you know.

Thank you for helping me. :)

---

### Post by chili555 on 2012-05-30
> When I do cat /etc/modprobe.d/blacklist

It returns an empty line.Then we might as well delete it and get rid of the warning:```
sudo rm /etc/modprobe.d/blacklist
```

---

### Post by marianlibrarian on 2012-05-30
I rebooted and the wireless makes several attempts to connect and then just stops. I am using a spare laptop to make this post. 

I also did the command to remove the blacklist file. When I entered it, it returned a blank line. So I don't know if it worked or not.

---

### Post by marianlibrarian on 2012-05-30
I rebooted again. It keeps trying and trying and will on occasion ask to verify router password. 

Is there any way to undo the command that was supposed to make ndiswrapper run automatically?

The connection finally came up on the first reboot but it takes 10 plus minutes to finally make a connection. And with this second reboot it still has not made the connection.

This machine is critical to my summer reading program. And I have another machine that I haven't even started on. (it is wired) :-)

Please tell me how to reverse the automatic command. Thanks

---

### Post by chili555 on 2012-05-30
> Is there any way to undo the command that was supposed to make ndiswrapper run automatically?Yes, certainly; however,I'm a bit skeptical that it's the culprit. Let's try:```
sudo gedit /etc/modules
```The last line should be 'ndiswrapper.' Remove it, save and close gedit. Now reboot and load it the way you did before. > Well I still have to:
sudo modprobe ndiswrapper

after restart.

Once I do that everything runs just fine. Does everything work now? There are other things we might try.

---

### Post by marianlibrarian on 2012-05-30
I removed the ndiswrapper reference from the modules file and rebooted.

It does not start ndiswrapper. However, it still does not connect to the network. I am using my laptop to post. It just continually asks for wireless network authentication. After the third or forth time it gives up. So I am back to square one. 

If you can just get me to yesterday's problem I would be very happy.

I did a dmesg | grep ndis command (I am typing what I see)

ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded usbcore: registered new interface driver ndiswrapper

then this line repeated 12 times:

ndiswrapper (iw_set_auth:1602: invalid cmd 12

After typing this, I noticed that it is attempting to access the network again. It has been taking about 2 minutes for it to ask me for the network password / authentication. I click on connect and it just keeps cycling through this procedure.

(1) While waiting I did iwconfig command:

lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.412 GHz Access Point: Not Associated
Bit Rate:300 Mb/s Tx-Power:32dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management:Off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rxinvalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

(2)
ndiswrapper -l
bcmn43xx32 : driver installed
    device (8046:9011) present

---

### Post by marianlibrarian on 2012-05-30
I'm sorry. I thought there would be a solution by now. Unfortunately, like most public libraries we are terribly under staffed. Not only am I the network administrator, I am also the chief potty cleaner (some really bad stories there). I have just spent almost 4 hours trying to search here and google there and I can't shut the library down to devote to this.

I have access to Windows 7. I only use it because I am desperate and have run out of time. Thanks to all who have helped me here. And thank you Chili555 for trying to help with my current problem. 

I'm sure I will be back with some other problem. Until then, take care and have a blessed day.

---

### Post by chili555 on 2012-05-30
> ndiswrapper (iw_set_auth:1602: invalid cmd 12I think there *is* a solution in the next later version of ndiswrapper, which is included in the latest version of Ubuntu.

---

### Post by 2christian23 on 2012-07-04
You might need an open wireless connection.

---

### Post by snv5004 on 2012-07-08
I'm on ubuntu 12.04 and this thread worked for me !!!

Many thanks to marianlibrarian and chili555. I pretty much followed this post throughout and chili555 provided answers to many places where I was stuck.

After installing and using ndiswrapper using the files provided here, and typing iwconfig into the terminal I only had:

lo         no wireless extensions

eth0     no wireless extensions

I then used this set of commands from chili555:

sudo modprobe ndiswrapper dmesg | grep ndis iwconfig

but the modprobe did not work. I did this:

[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)

then reran the previous commands. it worked!

then all I needed to do was add the string "ndiswrapper" to /etc/modules per chili555's suggestion, so that it would automatically use the wireless at start-up.

Thanks again for the advice!

---

### Post by gs44 on 2012-07-22
I too am using ubuntu 12.04 and currenty connected to the internet with my Netgear wnda 3100 V2 with a wireless N Connection!!:D

I read this thread and did what snv5004 posted and his link and BLAM  look out internet me and Ubuntu 12.04 is here!!  LOL!:D

Thankyou all for this post!!

---

### Post by ijulien on 2012-07-30
Hello all,

Thank you very much for all your help, this solved my problem also and the wireless adapter is working fine following your instructions.

One remaining problem: I noticed that I can't detect SSIDs on the 5Ghz frequency. Any suggestion to make WNDA3100v2 work with 802.11n?

Thank you

---

### Post by chili555 on 2012-07-30
> **ijulien said:**
> Hello all,

Thank you very much for all your help, this solved my problem also and the wireless adapter is working fine following your instructions.

One remaining problem: I noticed that I can't detect SSIDs on the 5Ghz frequency. Any suggestion to make WNDA3100v2 work with 802.11n?

Thank youI have none. I'm just glad it's working at all!

---

### Post by Zammael on 2012-08-05
I spent a couple of hours last night reading everything on the internet and trying everything to get my N600 Wireless Dual Band USB adapter to work. 

The funny thing is, I don't know what broke through and allowed my PC to see the wireless network. :D

I use 12.04, and thanks for all the information!

---

### Post by Egonosaur on 2012-08-08
Hello everyone, and thanks for a good thread.

I have managed to with the information provided here to get my new N600 to find the wireless networks available, since i'm using WPA2-PSK security on the network I can't connect, the animated wireless connection symbol will just act like it's trying to connect then after a while the "Enter password or passphrase for the wireless network" box will appear, if I then enter the password passphrase, the animated connection icon starts to blink again and again after a while the password box will appear. 

Does anyone here know if it's possible to connect to a secure wireless network with the N600? 
Or if it's possible to connect to the N600 hardware and change it's settings like you connect to a router?

---

### Post by Zikofski on 2012-08-12
hello,

thank you  this thread has been very helpfull i am a newbie with ubuntu i have managed to install the driver and get this

```
andrew@storage:~$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9011) present
```

but i am clueless on how to connect the device to a network, i want to connect it to a unsecure network and i am using Ubuntu Server 12.04

when i do this

```
andrew@storage:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

obviosly no wlan0 there

---

### Post by chili555 on 2012-08-12
Please run and post:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by Zikofski on 2012-08-12
thank you for quick reply i have this from those commands

```
andrew@storage:~$ sudo modprobe ndiswrapper
andrew@storage:~$ dmesg | grep ndis
[  812.909662] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  813.254367] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  813.803107] usbcore: registered new interface driver ndiswrapper
```

woo it now pops up, so i presume it was the ndiswrapper was not loaded?

---

### Post by chili555 on 2012-08-12
And *now* do you have a wireless interface?```
iwconfig
```Since you are running Server Edition, are you running Network Manager or are you going to set up /etc/network/interfaces?

---

### Post by Zikofski on 2012-08-12
to be honest i havent got a clue, can i get a network manager for server? as have googled connecting to a wifi, and i have managed to scan, just need to connect to one now :P

---

### Post by chili555 on 2012-08-12
Let's make sure ndiswrapper loads automatically:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```So you are saying you do have an interface wlan0? And it scans and sees your network? I am not completely familiar with Server Edition but I think it does not include Network Manager. I doubt you need it in a server.

If you are connecting to an insecure network, which I don't recommend, it should be as easy as:```
sudo iwconfig wlan0 essid mynetwork
sudo dhclient wlan0
```If you connect, I'd then set up /etc/network/interfaces. So you can find your server on the network, I assume with ssh, I recommend you use a static IP address; be sure it is outside the range used for DHCP in your router. Here is a suggested setup:```
sudo gedit /etc/network/interfaces
```Leave the lo and loopback lines untouched. Add lines as suggested here:```
auto wlan0
iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid mynetwork
```Proofread, save and close gedit. Get the system to read and use the changes:```
sudo ifdown wlan0 && sudo ifup wlan0
```Check to see if the address is being used:```
ifconfig wlan0
```Of course, substitute your details here.

Post back any questions.

---

### Post by Zikofski on 2012-08-13
sorry about the delay in replying internet died completly last night :( but i continued playing around

i did what you said with 
sudo su
echo ndiswrapper >> /etc/modules
exit

and check the file using

sudo nano /etc/modules

and it is present there but i did notice that i haft to pull out and re plug in the USB on reboot or it wont pick it up

sadly my internet is a public connection, i have managed to single out an ip for static but it requires login to connect to the internet so i have just noticed w3m which alows me to do this so i shall give this ago and report back

EDIT

yes it worked i followed this website to share the internet a very good in my eyes
[http://www.somewhereville.com/?p=1196]("http://www.somewhereville.com/?p=1196")

the problem was, that ever time i rebooted my server it had to un plug and re plug in my USB stick strange but it works

i did have another problem in with my old setup using my Windows 7 computer as my shared connection i was able to put its ethernet port as the DNS for example 192.168.2.7 as it was at the time my server ip address is 192.168.2.1 putting that as dns on my laptop did not work but putting my actualy ISP dns worked, i probably missing something from the setup there.

also i noticed when i edited the /etc/resolv.conf file it screwed up my whole system, so i did not want to change that file as it says to on the website, i am using static for both, but i may make an image now and play around with dhcp

thank you for your help chili555, but i am sure il be on here again soon :)

---

### Post by rupweb on 2012-08-20
Thanks all - and chili555 - finally got Netgear adaptor working on Fedora Linux using the Windows XP 64 bit bcmn43xx64.inf driver...

The problem I had was trying to install Win7 driver bcmwlhigh6 which does not work on linux. Only the XP driver works.

To install ndiswrapper I got the following packages:

kmod-ndiswrapper-1.57-2.fc17.11.x86_64.rpm                      
ndiswrapper-1.57-1.fc17.x86_64.rpm
kmod-ndiswrapper-3.3.4-5.fc17.x86_64-1.57-2.fc17.11.x86_64.rpm

and stuck them all into a subdirectory. Then ran:

su -c 'rpm -ivh *.rpm --nodeps'

This got ndiswrapper going fine. Then after installing the correct .inf then running iwconfig I get:

$ iwconfig
em1       no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SKY95739"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:30:71:98   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:241  Invalid misc:33355   Missed beacon:0

---

### Post by chili555 on 2012-08-20
> **rupweb said:**
> Thanks all, got Netgear adaptor working on Fedora Linux using the Windows XP 64 bit bcmn43xx64.inf driver...

The problem I had was trying to install Win7 driver bcmwlhigh6 which does not work on linux. Only the XP driver works.

To install ndiswrapper I got the following packages:

kmod-ndiswrapper-1.57-2.fc17.11.x86_64.rpm                      
ndiswrapper-1.57-1.fc17.x86_64.rpm
kmod-ndiswrapper-3.3.4-5.fc17.x86_64-1.57-2.fc17.11.x86_64.rpm

and stuck them all into a subdirectory. Then ran:

su -c 'rpm -ivh *.rpm --nodeps'

This got ndiswrapper going fine. Then after installing the correct .inf then finally running iwconfig I get:

$ iwconfig
em1       no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SKY95739"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:30:71:98   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:241  Invalid misc:33355   Missed beacon:0WARNING! All you searchers take careful note. He got it working on **Fedora** using .rpm packages. Ubuntu and Debian-based distributions need *.deb* packages.

---

### Post by kurt18947 on 2012-08-20
> **rupweb said:**
> Thanks all - and chili555 - finally got Netgear adaptor working on Fedora Linux using the Windows XP 64 bit bcmn43xx64.inf driver...

The problem I had was trying to install Win7 driver bcmwlhigh6 which does not work on linux. Only the XP driver works.


This is  a not-well-known fact with NDISwrapper.  I wonder what's going to happen when XP is no longer supported in 2014?  Presumably there is work in progress to get Win 7 drivers to work.  I haven't heard anything though.

---

### Post by chili555 on 2012-08-20
> **kurt18947 said:**
> This is  a not-well-known fact with NDISwrapper.  It is, however, mentioned in the man page:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Windows  XP drivers and kernel module to load the Windows XP drivers. Both are called ndiswrapper.

---

### Post by khushu11 on 2012-09-18
Hello Chilli555,

I'm running ubuntu 12.04 32 bit on my beagle board without the gui version. I I have your driver files  Broadcom_bcm43xx_USB_32 and tried installing them through ndiswrapper, it said that ndiswrapper command not found.

Then I tried installing the ndiswrapper, by typing 

```
sudo apt-get install ndiswrapper 
```it said > unable to locate package ndiswrapper then I tried installing the ndiswrapper-common, which got installed, (thinking that would have ndiswrapper within it with no luck) 

Then I tried installing ndiswrapper-utils-1.9 it said 

> ndiswrapper-utils-1.9 is not available, but is referred by another package .... has no installation candidate then I installed ndiswrapper-dkms which again got installed but doesn't have ndiswrapper executable within as well... :-( 

What should I try next? Though netgear WNDA 3100 v2 seems to be working fine with windows 7,  I'm stuck at this point on ubuntu... 

It would be really great if you could help me in installing the drivers from here! 

Thank you

---

### Post by chili555 on 2012-09-19
ndiswrapper-utils-1.9 is definitely what you need. I am surprised it didn't install directly. The executable is actually in ndiswrapper-common but won't work if the user-space part is not there. You might try:```
sudo apt-get install --reinstall libc6
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by shabu on 2012-09-19
> **Egonosaur said:**
> Hello everyone, and thanks for a good thread.

I have managed to with the information provided here to get my new N600 to find the wireless networks available, since i'm using WPA2-PSK security on the network I can't connect, the animated wireless connection symbol will just act like it's trying to connect then after a while the "Enter password or passphrase for the wireless network" box will appear, if I then enter the password passphrase, the animated connection icon starts to blink again and again after a while the password box will appear. 

Does anyone here know if it's possible to connect to a secure wireless network with the N600? 
Or if it's possible to connect to the N600 hardware and change it's settings like you connect to a router?
  

Hi ,
I have the same issue after I upgraded to 12.04. Here is the dmesg I got:
 dmesg |grep ndis
[   15.917271] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   16.634290] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   17.183545] usbcore: registered new interface driver ndiswrapper
[   67.698688] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[   83.144693] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
 
repeated many times. I appreciate any help.

---

### Post by chili555 on 2012-09-19
> [ 67.698688] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 83.144693] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)May I see:```
iwconfig
```

My suspicion: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)> When I checked the values of WNA3100, I saw its Tx-Power is around 42 dBm and other parameters are correctly set. 

---

### Post by shabu on 2012-09-20
> **chili555 said:**
> May I see:```
iwconfig
```My suspicion: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

Thanks Chili555 for your help. Here it is:

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Jessica"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 74:31:70:A8:EE:FA   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by chili555 on 2012-09-20
> Tx-Power:[COLOR="Red"]32 dBm[/COLOR] That seems a bit high. Let's try as the link suggests:```
sudo iwconfig txpower 15
```See if it sticks:```
iwconfig
```Now does it connect? If that helps, we can make it permanent.

The command in the link is not quite correct.

---

### Post by shabu on 2012-09-21
> **chili555 said:**
> That seems a bit high. Let's try as the link suggests:```
sudo iwconfig txpower 15
```See if it sticks:```
iwconfig
```Now does it connect? If that helps, we can make it permanent.

The command in the link is not quite correct.

It tries to connect. For some reason it is not getting an IP from the server. Will have to check server then come back . Thanks for your help.
Which command?

I entered :>> iwconfig
.

---

### Post by chili555 on 2012-09-21
> Which command?

I entered :>> iwconfig
.To see if the command sticks, run:```
iwconfig
```Then you ought to see, as you requested:```
wlan0 IEEE 802.11g ESSID:"Jessica"
Mode:Managed Frequency:2.412 GHz Access Point: 74:31:70:A8:EE:FA
Bit Rate=144 Mb/s [COLOR="Red"]Tx-Power:**15** dBm[/COLOR]
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

---

### Post by chridal on 2012-10-06
Thank you so much chili555 for you great assistance.

Everything working here as well now!!

Really appreciate it!

---

### Post by JLundyC on 2012-10-22
After Struggling for several days and trying various suggestions ....and no luck in getting the netgear wnda3100v2 installed on v12.10 ...I did manage to get the windows wrapper routine to import the driver...and it is actually linked to a device.  But the network manager has no clue that the wireless connection is there.  I am ready to start all over again but not sure where to start.

***lsusb says***:
.
Bus 002 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
.

***iwconfig says:***
lo        no wireless extensions.

eth0      no wireless extensions.

lxcbr0    no wireless extensions.

*** ndiswrapper -l says:***

bcmwlhigh5 : driver installed
    device (0846:9011) present

I admit that I am a newbie with a capital N.... but where would be a good place to start in attempting to get the network adapter linked up with 12.10?   Arrg.:mad:

---

### Post by chili555 on 2012-10-22
> **JLundyC said:**
> 
*** ndiswrapper -l says:***

bcmwlhigh5 : driver installed
    device (0846:9011) present

I admit that I am a newbie with a capital N.... but where would be a good place to start in attempting to get the network adapter linked up with 12.10?We all were new at one time; even ole Chili and even Linus! No worries. Are there any interesting messages here?```
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

[http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds)

---

### Post by JLundyC on 2012-10-23
I tried the  dmesg | grep ndis and got no messages back.  (dmesg with out the piping grep ndis filled the screen with various information).  Is that good or bad? :confused:

---

### Post by chili555 on 2012-10-23
Bad. It suggests the ndiswrapper module isn't loading; its footprint ought to appear in *dmesg*. Let's see if there are any interesting messages here:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```The pipe | tells the terminal we don't want to see all of *dmesg*; we only want lines containing 'ndis.' That is, lines relevant to our investigation.

---

### Post by JLundyC on 2012-10-23
oh boy, i am really confused now. The first line keyed into the terminal session resulted in

**FATAL: Module ndiswrapper not found**

I guess that provides a good starting place....

---

### Post by chili555 on 2012-10-23
> **JLundyC said:**
> oh boy, i am really confused now. The first line keyed into the terminal session resulted in

**FATAL: Module ndiswrapper not found**

I guess that provides a good starting place....Exactly! With the ethernet hooked up, open a terminal and do:```
sudo apt-get install --reinstall ndiswrapper-dkms ndiswrapper-common ndiswrapper-utils-1.9
```After it's done, do:```
sudo modprobe ndiswrapper
```Did your wireless spring to life? If not, post:```
dmesg | grep ndis
```I think we're close!

---

### Post by JLundyC on 2012-10-23
The system didn't like the first command.... the last lines of the terminal session:

Unpacking replacement ndiswrapper-utils-1.9 ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
Building only for 3.5.0-17-generic
Building initial module for 3.5.0-17-generic
Error! Bad return status for module build on kernel: 3.5.0-17-generic (i686)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...

I have version 12.10 installed on a new (pristine) dual boot ubuntu / windows7 environment.   It would appear that I am stuck. :confused:

---

### Post by chili555 on 2012-10-23
>  It would appear that I am stuck.Maybe. Usually, you aren't stuck until the doc says you're stuck! I suggest you do as it suggests:```
sudo cat /var/lib/dkms/ndiswrapper/1.57/build/make.log
```Perhaps we're just missing a dependency we can install and try again. Let's see before we call the coroner.

---

### Post by JLundyC on 2012-10-23
The following is from the terminal session when the command was issued to
** sudo cat /var/lib/dkms/ndiswrapper/1.57/build/make.log**

DKMS make.log for ndiswrapper-1.57 for kernel 3.5.0-17-generic (i686)
Tue Oct 23 17:00:53 CDT 2012
make -C /usr/src/linux-headers-3.5.0-17-generic M=/var/lib/dkms/ndiswrapper/1.57/build
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  LD      /var/lib/dkms/ndiswrapper/1.57/build/built-in.o
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/crt_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/hal_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ndis_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_io_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/rtl_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/usb_exports.h
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/crt.o
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/hal.o
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/iw_ndis.o
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/loader.o
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/ndis.o
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
make[2]: *** [/var/lib/dkms/ndiswrapper/1.57/build/ndis.o] Error 1
make[1]: *** [_module_/var/lib/dkms/ndiswrapper/1.57/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2

hmmm sounds ominous....:(

---

### Post by chili555 on 2012-10-23
We (me, too!) are the subject of an official bug! [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)

Please take the steps outlined in post #16. Do you need some assistance with how exactly to proceed?

---

### Post by JLundyC on 2012-10-23
Thanks!!! I went through the steps of post #16 (and learned a lot file extraction and movement in so doing).  I am not sure what we just did, but the wireless is now being recognized.  Again, thanks for your help!!!:P

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

### Post by chili555 on 2012-10-24
> **JLundyC said:**
> Thanks!!! I went through the steps of post #16 (and learned a lot file extraction and movement in so doing).  I am not sure what we just did, but the wireless is now being recognized.  Again, thanks for your help!!!:PAwesome! Glad it's working.

---

### Post by sarutahiko on 2012-10-31
Chili, you're fabulous.  Thank you for your continued support in this long thread.

I have the same exactly piece of hardware as the OP, so I downloaded the files you posted (the second time), followed the instructions throughout the thread, and am now at a point where ndiswrapper loads on system load, shows me my driver with hardware found, and I can select and attempt to connect to networks (I also have the iwlwifi driver blacklisted so my onboard card doesn't try to take over).

Problem is, as a few others have stated, it tries to connect for a while, asks me for my credentials, tries to connect for a while, rinse and repeat.

Have you any ideas what might be going wrong?

Thanks. :)

Also, here are my dmesg and iwconfig > files

```
[   19.561868] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   20.087412] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   20.643374] usbcore: registered new interface driver ndiswrapper
[   20.824563] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
```

```
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2012-10-31
Let's see:```
ndiswrapper -l
lsmod | grep -e iwl -e ndis
sudo cat/var/log/syslog | grep etwork | tail -n10
```

---

### Post by sarutahiko on 2012-10-31
```

bcmn43xx32 : driver installed
	device (0846:9011) present

```

```

ndiswrapper           192268  0 

```

```
Oct 31 00:53:18 dragonite NetworkManager[987]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dragonite'.
Oct 31 12:58:35 dragonite NetworkManager[940]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wave'.
Oct 31 21:01:33 dragonite NetworkManager[949]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dragonite'.

```

---

### Post by chili555 on 2012-10-31
> Oct 31 00:53:18 dragonite NetworkManager[987]: <info> Activation ([COLOR="Red"]wlan0/wireless[/COLOR]) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dragonite'.
Oct 31 12:58:35 dragonite NetworkManager[940]: <info> Activation ([COLOR="Red"]wlan1/wireless[/COLOR]) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wave'.
Oct 31 21:01:33 dragonite NetworkManager[949]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dragonite'.I wonder if your blacklist is working. Please run and post:```
dmesg | grep wlan
lsmod
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Thanks.

---

### Post by sarutahiko on 2012-10-31
That may have been because I was tweaking/testing drivers and blacklists over that time.  Notice they're an hour apart.

```


```

```

Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13516  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_codec_hdmi     31775  1 
fglrx                2909855  88 
ir_jvc_decoder         12459  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                86486  0 
snd_hda_codec_idt      60251  1 
serio_raw              13027  0 
snd_seq_midi           13132  0 
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
soundcore              14635  1 snd
rc_rc6_mce             12454  0 
ir_nec_decoder         12459  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ene_ir                 18019  0 
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
video                  19068  0 
wmi                    18744  1 hp_wmi
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
mac_hid                13077  0 
ndiswrapper           192268  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
r8169                  56321  0 

```

```

# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_eda

blacklist iwlwifi

```

---

### Post by chili555 on 2012-10-31
I see.> Oct 31 21:01:33 dragonite NetworkManager[949]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful. [COLOR="Red"]Connected to wireless network 'dragonite'[/COLOR]. It appears that you connected, however, I don't see Stages 3-5. 

Is this a virtual machine? Guest or host?

---

### Post by sarutahiko on 2012-10-31
> **chili555 said:**
> I see.It appears that you connected, however, I don't see Stages 3-5. 

Is this a virtual machine? Guest or host?

No, this is the main (host?) account on a full 12.04 install.

---

### Post by chili555 on 2012-11-01
Your syslog ought to have many, many more lines listed as it's trying to connect. I hope it will offer some clues as to why it's stopping short of connecting. Please reboot so we have a clean slate. Be sure any ethernet cables are detached. Be sure iwlwifi is blacklisted. Try to connect.

Do you see networks?```
sudo iwlist wlan1 scan
sudo cat /var/log/syslog grep -e wlan1 -e etwork -e ndis | tail -n20
```What is not working correctly with your iwlwifi device? Generally, they are superior to any ndiswrapper device.

---

### Post by sarutahiko on 2012-11-01
So somehow when I logged on the computer automatically connected to the guest wifi service.  I didn't touch anything, ran the commands, and then tried to connect to the secured one (and I couldn't).  I had not previously been able to connect to anything, so I don't know how that happened.

Also, the reason I'm using a different one is because my internal card cannot and will not connect to either the unsecured or secured wifi at my school.  It works on every other network I've tried, but not my school one.  And it's really important that I can access the internet at school.  :\  So I bought this Netgear adapter and now .. here we are.  Won't even work at home (dragonite).

```

wlan1     Scan completed :
          Cell 01 - Address: 00:24:6C:C8:04:20
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B160C1218243048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 01088B0C121618243048
          Cell 02 - Address: 00:24:6C:C8:04:21
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:24:6C:C8:13:A0
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:24:6C:C8:13:A1
                    ESSID:"NUwave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 02:2A:B2:20:0E:D7
                    ESSID:"print server 1ED16B"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00137072696E742073657276657220314544313642
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
          Cell 06 - Address: 00:24:6C:C8:0A:00
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:24:6C:C8:0A:01
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:24:6C:C8:0A:40
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:24:6C:C8:0A:41
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000


```

```

Nov  1 10:30:37 dragonite NetworkManager[977]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  1 10:30:37 dragonite NetworkManager[977]: <info> Policy set 'wave-guest' (wlan1) as default for IPv4 routing and DNS.
Nov  1 10:30:37 dragonite NetworkManager[977]: <info> Activation (wlan1) successful, device activated.
Nov  1 10:30:37 dragonite NetworkManager[977]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Nov  1 10:30:44 dragonite kernel: [   39.824068] wlan1: no IPv6 routers present
Nov  1 10:30:49 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: completed -> associating
Nov  1 10:30:55 dragonite NetworkManager[977]: <info> (wlan1): roamed from BSSID 00:24:6C:C8:04:20 (wave-guest) to 00:24:6C:C8:13:A0 (wave-guest)
Nov  1 10:30:55 dragonite NetworkManager[977]: <info> (wlan1): IP6 addrconf timed out or failed.
Nov  1 10:30:55 dragonite NetworkManager[977]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov  1 10:30:55 dragonite NetworkManager[977]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov  1 10:30:55 dragonite NetworkManager[977]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov  1 10:30:59 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: associating -> scanning
Nov  1 10:31:04 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: scanning -> associating
Nov  1 10:31:07 dragonite NetworkManager[977]: <info> (wlan1): roamed from BSSID 00:24:6C:C8:13:A0 (wave-guest) to 00:24:6C:C8:04:20 (wave-guest)
Nov  1 10:31:14 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: associating -> scanning
Nov  1 10:31:19 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: scanning -> associating
Nov  1 10:31:29 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: associating -> scanning
Nov  1 10:31:34 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: scanning -> associating
Nov  1 10:31:44 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: associating -> scanning
Nov  1 10:31:49 dragonite NetworkManager[977]: <info> (wlan1): supplicant interface state: scanning -> associating

```

So I was just using wave-guest to see how stable it was, and it worked for a little bit and then disconnected and failed to reconnect.  I've added the same logs in case that helps at all.

```

wlan1     Scan completed :
          Cell 01 - Address: 00:24:6C:CD:BD:40
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: D8:C7:C8:BC:A1:E1
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:24:6C:C8:0A:40
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:24:6C:C8:0A:41
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:24:6C:C8:0A:00
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:24:6C:C8:0A:01
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: D8:C7:C8:BC:A1:01
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:24:6C:C8:04:20
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E55776176652D6775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:24:6C:C8:04:21
                    ESSID:"wave"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064E5577617665
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000


```
```

Nov  1 10:50:45 dragonite NetworkManager[971]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Nov  1 10:50:45 dragonite NetworkManager[971]: <info> Config: added 'identity' value 'youngren.z'
Nov  1 10:50:45 dragonite NetworkManager[971]: <info> Config: added 'bgscan' value 'simple:30:-45:300'
Nov  1 10:50:45 dragonite NetworkManager[971]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Nov  1 10:50:45 dragonite NetworkManager[971]: <info> Config: set interface ap_scan to 1
Nov  1 10:50:45 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: inactive -> scanning
Nov  1 10:50:50 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: scanning -> associating
Nov  1 10:50:50 dragonite kernel: [  575.544532] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Nov  1 10:50:50 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associating -> associated
Nov  1 10:50:51 dragonite avahi-daemon[1009]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::28e:f2ff:fe7d:667a.
Nov  1 10:50:51 dragonite avahi-daemon[1009]: New relevant interface wlan1.IPv6 for mDNS.
Nov  1 10:50:51 dragonite avahi-daemon[1009]: Registering new address record for fe80::28e:f2ff:fe7d:667a on wlan1.*.
Nov  1 10:50:52 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associated -> disconnected
Nov  1 10:50:57 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: disconnected -> associating
Nov  1 10:50:58 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associating -> associated
Nov  1 10:51:00 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associated -> disconnected
Nov  1 10:51:05 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: disconnected -> associating
Nov  1 10:51:05 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associating -> associated
Nov  1 10:51:07 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: associated -> disconnected
Nov  1 10:51:12 dragonite NetworkManager[971]: <info> (wlan1): supplicant interface state: disconnected -> associating

```

---

### Post by chili555 on 2012-11-01
You have the classic problem. Several access points with the same SSID; either wave or wave-guest. Network Manager roams from one to the other endlessly. You might try selecting the strongest:>  Cell 06 - Address: 00:24:6C:C8:0A:00
                    ESSID:"wave-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    [COLOR="Red"]Quality:64/100[/COLOR]  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:offPut its MAC address in NM and see if it will stay on that access point. Please see attached.

Is that also the issue with iwlwifi at school???

---

### Post by sarutahiko on 2012-11-01
> **chili555 said:**
> You have the classic problem. Several access points with the same SSID; either wave or wave-guest. Network Manager roams from one to the other endlessly. You might try selecting the strongest:Put its MAC address in NM and see if it will stay on that access point. Please see attached.

Is that also the issue with iwlwifi at school???

So is each wireless router then acting as an access point?  And would I need to manually change which one I want to connect to as I move around the school?  I only see one copy of wave and wave-guest in the list of networks.

And I don'w know if *that* is the exact issue with iwlwifi at this school, but iwlwifi is having *some* issue (that's why I'm using this Netgear one).

I'll try it and report back.

---

### Post by chili555 on 2012-11-01
> So is each wireless router then acting as an access point? Yes.>  And would I need to manually change which one I want to connect to as I move around the school? Probably. That's currently a shortcoming of NM. So far, it doesn't lock on to the strongest access point and stay there. Like my ex-girlfriend, it has a roving eye and a fickle heart!

You might try the same technique after you pull out the Netgear and reload iwlwifi at school. If it works, you're all set.

---

### Post by sarutahiko on 2012-11-01
> **khushu11 said:**
> 
Then I tried installing the ndiswrapper, by typing 

```
sudo apt-get install ndiswrapper 
```it said then I tried installing the ndiswrapper-common, which got installed, (thinking that would have ndiswrapper within it with no luck) 


I think maybe you want
```
sudo apt-get install ndisgtk
```

Alternatively you can use the software center.

And to Chili:

As seen attached, I put in the mac address for the strongest access point into BSSID, confirmed that my device mac address matched my wlan0 mac address in ifconfig, and then gave the network the custom name Custom Name.  It didn't appear in the the network list in the upper right - it maintained its old name Wave and wouldn't connect.  Am I missing something?

Thanks. :)

---

### Post by chili555 on 2012-11-01
Isn't 'wave' encrypted with WPA2? Did you also add in the password under 'Wireless Security'?

I don't see that MAC, xx:2E:31, in any of your scans, I assume you've moved around or that I need to clean my glasses.

---

### Post by sarutahiko on 2012-11-01
> **chili555 said:**
> Isn't 'wave' encrypted with WPA2? Did you also add in the password under 'Wireless Security'?

I don't see that MAC, xx:2E:31, in any of your scans, I assume you've moved around or that I need to clean my glasses.

Ah! I'm sorry.  I should have told you I put the Netgear piece away and am now trying this on my onboard card (just in case this would solve that problem).

I am currently posting this from wave on my Ubuntu side.  So that's awesome!  Yes, it is encrypted by I have all of that input properly.  My only concern at this point is that it's a fluke since the change of name (to Custom Name) is not reflected in the list of networks - it still says wave.  Is there any way to really confirm that I've done it properly and I'm not experiencing a fluke (other than waiting it out)?

Other than that - thank you so much for all of your help.  You're fantastic and I really really do appreciate it.

---

### Post by chili555 on 2012-11-01
You can run:```
iwconfig
```It will show the SSID and its MAC and you can confirm you are connected to the right access point.

After you wait it out, I'll be interested in your report.

---

### Post by sarutahiko on 2012-11-01
It was connected to the correct one.  But it still could have been a coincidence, so this is what I did:

I scanned again, found an access point at half the quality, opened Network Connections, picked 'wave', edited it to the new mac address, and then selected 'wave' again from the list in the upper right (where you select the wireless network).  It asked me for my credentials (which I told it to keep) and reconnected to the higher quality one.  I checked Network Connections and now I have wave and wave1.  And again, if I rename a connection Custom Name I don't see that in my list in the upper right.  How do I connect to one that I add or edit on Network Connections? :\

---

### Post by chili555 on 2012-11-01
>  But it still could have been a coincidenceYou think it's a coincidence that you asked it to connect to 'wave' and *ONLY* to the 'wave' with the MAC, xx:2E:31 address and it connected to it? As skeptical as I sometimes can be about Network Manager, I doubt it is a coincidence.>  How do I connect to one that I add or edit on Network Connections? :\ Just exactly like you did. However, if your question is actually how can I rename 'wave' xx:2E:31 to, for example, dorm and have it show up as 'dorm' in the network list, the answer is, you pprobably can't. The network list is the available cells names as seen in iwlist scan.

As of yet, NM still has some shortcomings. 

With some fiddling, you could probably do it without NM by setting up aliases in /etc/network/interfaces; something like wlan0-dorm. From *man interfaces*:>  mapping eth0
            script /usr/local/sbin/map-scheme
            map HOME eth0-home
            map WORK eth0-work

       iface eth0-home inet static
            address 192.168.1.1
            netmask 255.255.255.0
            up flush-mail

       iface eth0-work inet dhcp

...etc....It would take some time and experimentation. Don't neglect your usual university duties: adult beverages, dating, WoW and studies!

---

### Post by Green_Bean on 2012-11-21
I had the exact same problem and the same wireless adapter. This worked for me, thanks so much for the  drivers chili555, the ones I was using before didn't work. I used the GUI (go to menu at top of screen:  System > Windows Wireless Drivers, then choose your inf file).

---

### Post by cowtownchemist on 2012-11-29
> **chili555 said:**
> Ahh! Much better. You have 0846:9011, so don't use the files I attached; use these instead. You will want to install bcmn43xx32.inf or bcmn43xx64.inf depending on whether you have a 32-bit or 64-bit system

Thank you chili555!  You just saved me from banging my head in frustration for days!  Its all about the driver!  I was using bcmwlhigh6 and received the following error: 

[ 1664.891846] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh6'
[ 1664.891922] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh6'

All because I was using the wrong driver.  bcmn43xx32.inf worked for me!:)

---

### Post by chili555 on 2012-11-29
Let's all say that again louder so the searchers will hear it: *_Its all about the driver! _*

The driver has to match your architecture; that is 32- or 64-bit and the .inf file must list your usb.id, in a case above *0846:9011* and, finally, it must be the Windows *XP* files. Not Vista, not 7, not 98SE but XP.

There are lots of versions running around, so check and be sure. If in doubt, stop and ask.

As an example, if you have the device I mentioned above and you can't see this in the .inf file, you have the wrong file:> ;-----------------------------------------------------------------
; x86 - Win9x, Win2K, [COLOR="Red"]WinXP[/COLOR]
;
[BROADCOM]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9011[/COLOR]

;-----------------------------------------------------------------


---

### Post by MonNeric on 2012-12-02
Hi guys,

Another poor soul lost with its WNDA 3100 v2 adapter. I'm on Linux Mint 14 (based on Ubuntu 12.10).

The good news is I followed the various advices in this forum post + followed some links and I managed to fix: the modprobe fatal error, install the driver and get the WNDA 3100 v2 adapter recognised.

Problem is it doesn't work as expected (note: it obviously works perfectly under windows XP or 8). It doesn't show me all the available networks at home and even shows some which I cannot detect with any other device (I've got 3 different WiFi devices at home including a WiFi scanner on my smartphone which works flawlessly). In addition the WNDA3100v2 is a dual band adapter and under linux it can only see the 2.4 GHz SSIDs, none of the 5 GHz networks are detected. So in fact I couldn't really test if the adapter is actually working (by the way as soon as I run the modprobe command, the LED on the adapter goes off).

Obviously my network is one of the not detected networks (both in 2.4 GHz and 5 GHz), so my goal is:
1 - Fix the detection of the 2.4 GHz networks so I can at least detect mine and have a connection to internet (might this be because I'm using channel 13? It worked under windows...)
2 - Make the 5 GHz capability work so I can connect to my 5 GHz network, it is important as the 2.4 GHz band is quite saturated at my place (big building, lots of networks, lots of interference).

Thx for the help already provided in the earlier replies of this post and looking forward for more info.

Cheers

---

### Post by nenenes on 2012-12-05
HI My name is Nenene and I'm fairly new to Linux. This is wonderful, that is what I comprehend of it. Thank you Chili.

I have followed this thread as far as I can trying to install the WNDA3100V2 dongle. 

I get this result

fuzzer@zeferis:/etc/tmpinst$ dmesg | grep ndis
[ 2621.698982] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 2621.723199] usbcore: registered new interface driver ndiswrapper

The dir ahown a where the broadcom files are

iwconfig still shows no wireless extensions. I do not have wine installed but do have the Broadcom files extracted and in a dir where I can get to them. I'm not sure what to do next.  I also have a bit of a problem with comprehension because of a disability.  Makes it harder to understand what you're writing but I muddle through.

I'll check back tomorrow.

---

### Post by chili555 on 2012-12-05
I will try to explain carefully and thoroughly. Stop me and ask again if I go a bit too fast. Let's see how far you've gotten and try to fix it from here. Please open the termnal and run and post:```
ndiswrapper -l
```That's an L for 'list'; it will give us some diagnostic clues. Thank you.

---

### Post by nenenes on 2012-12-06
> **chili555 said:**
> I will try to explain carefully and thoroughly. Stop me and ask again if I go a bit too fast. Let's see how far you've gotten and try to fix it from here. Please open the terminal and run and post:```
ndiswrapper -l
```That's an L for 'list'; it will give us some diagnostic clues. Thank you.

Some questions first please. 

I live in a dorm. and this computer is a project of sorts. Right now I have to take it to the day room to access the network hardwire.  If I try to boot the computer in my room is waits about a minute and a half looking for the network which isn't there. Everything else here is wifi.

Last night I took the CPU downstairs to the net connection there and did and update.  Is it possible to do this without having to be hooked to the hardwire?  I can ask questions from my netbook and do the work on the desktop. 

Oh yes I'm running 12.04.


"Ah yes, she can be taught." - My brother 

And you can go a bit faster. The problem is comprehension, not thinking. :p :lolflag:

I'm going to boot the desktop and see if I can do it here. Hopefully Chili is around.

---

### Post by nenenes on 2012-12-06
Sorry double post. I should have gotten my results before I posted. 

*ndiswrapper -l* gives me two results. 

First is Command... is avail... in /usr/sbin/ndiswrapper. Command not located because /usr/sbin is not in path environment variable. Likely cause lack of admin privileges.   I'm sure you know what the entire error says. :) 

I've run into this before and have yet to work out how to change either the user privs or the environment variable. I'm having problems with users and privileges. There is only one user on my desktop.

Second result was *sudo ndiswrapper -l  *That just dropped me back to the command line. 

Thank you.

---

### Post by chili555 on 2012-12-07
> Last night I took the CPU downstairs to the net connection there and did and update. Is it possible to do this without having to be hooked to the hardwire?Absolutely.> Second result was sudo ndiswrapper -l That just dropped me back to the command line. That typically means there is no ndiswrapper driver installed at all.> do have the Broadcom files extracted and in a dir where I can get to them. I'm not sure what to do next.Let's make sure we install the files appropriate to your setup. First, we need to make sure what device you have; please run and post:```
lsusb
```Feel free to trim away everything that isn't your Netgear. Second, we need to be sure if you have a 32- or 64-bit system. Please run:```
arch
```32-bit will return i686 and 64-bit will return x86_64. Therefor, we'll need to be sure to install the 32- or 64-bit Windows XP files matching.

What files do you have in your Broadcom files? What are the names of the folders?

---

### Post by jomasdf on 2012-12-12
Sup, just thought I would share some since I just spent 7 hours trying to fix this thing and finally made it.

I tried all guides imaginable. Nothing worked at all.

I gave up trying to make it run on 64 bit since people said it was rubbish and unstable, that was the first step.

I made a complete reinstall of ubuntu, from there I downloaded ndiswrapper from the software center + the sources. (I allways tried the developers website the other times).

Then downloaded the drivers (I'm so sorry that I lost the source for this :()

Launched ndiswrapper from the dash, loaded the drive and it worked perfectly. I was reaaally surprised this worked since all other advanced ways (yes, i'm new to this) had failed.

Anyway, this is a complete mystery to me. But I guess that I would recommend people to try the easy ways first, it might work with no effort at all. And dont bother with the 64 version.

I will try to look up the source again.

I want to thank the site for all the great people trying to help tho, keep it up!

---

### Post by wayneman on 2012-12-15
Hey guys!

I'm also new to linux and this problem with the wnda3100 v2 has been driving me mad.

I have tried quite a few things already and now I'm already at the stage that the device is recognised with the driver and I also have the wlan0 interface. Still, it's not showing me any network.

I'm running xubuntu 64 bit. My outputs are:

```

$lsusb

Bus 002 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

```
```

$ndiswrapper -l

bcmn43xx64 : driver installed
    device (0846:9011) present

``````

$dmesg | grep ndis

[    7.074658] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[    7.583067] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[    7.839771] usbcore: registered new interface driver ndiswrapper

```and finally:

```

$iwconfig

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I would be very grateful for any help. I was a complete computer noob until just a few months ago, now using my few days off for setting up Xubuntu and still struggling with understanding all these things. But it'll be worth it I hope. :p

---

### Post by chili555 on 2012-12-15
> **wayneman said:**
> Hey guys!

I'm also new to linux and this problem with the wnda3100 v2 has been driving me mad.

I have tried quite a few things already and now I'm already at the stage that the device is recognised with the driver and I also have the wlan0 interface. Still, it's not showing me any network.Looking good so far! Does it scan?```
sudo iwlist wlan0 scan
```Is the wireless switch on or off?```
rfkill list all
```Any interesting news here?```
nm-tool
```

---

### Post by wayneman on 2012-12-15
Thank you for your help!

Results:

```

$ sudo iwlist wlan0 scan

wlan0     No scan results


$ rfkill list all


$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        20:4E:7F:F1:C1:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:16:E6:DD:EA:75

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             195.202.138.3
    DNS:             195.202.128.3
    DNS:             62.40.128.2


```

---

### Post by chili555 on 2012-12-15
Network Manager will disallow the less secure, slower wireless if wired ethernet is available as yours is. Please detach the ethernet, give NM a few moments to notice the change in state and try again:```
sudo iwlist wlan0 scan
```If there are still no scan results, let's do some diagnostics:```
dmesg | grep -e ndis -e wlan
```If there are scan results, click the NM icon and connect.

---

### Post by wayneman on 2012-12-15
Here it is:

```

$ sudo iwlist wlan0 scan

wlan0     No scan results


$ dmesg | grep -e ndis -e wlan
[    7.074658] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[    7.583067] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[    7.837261] wlan0: ethernet device 20:4e:7f:f1:c1:e6 using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[    7.839140] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[    7.839771] usbcore: registered new interface driver ndiswrapper
[    7.852701] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.853000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  866.580983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

---

### Post by chili555 on 2012-12-15
We wonder why wlan0 is not ready, obviously. If there are any wlan0 settings in /etc/network/interfaces, that would prevent Network Manager from handling wlan0, so let's check:```
sudo gedit /etc/network/interfaces
```It ought to look like this:> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopbackThe comments, prefaced by #, might be different or missing, but the declared interface should be lo only. If there is any reference to wlan0, remove it. Proofread, save and close gedit. Now let's check NM's conf file:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```It should read:> [main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=falseMake sure that managed=false. Proofread, save and close gedit. Now restart networking:```
sudo service network-manager restart
```Any errors or warnings? Any improvement?

---

### Post by wayneman on 2012-12-16
The outputs look exactly like you described. Restarting didn't help ...

But I have to add, strange things are happening here. Just to be sure, I decided to check the adapter again on Windows 7 (I have both OSs on different partitions installed) - suddenly Windows was complaining that the driver for the USB adapter didn't install correctly (it worked before) and my wireless settings were messed up. Some not working "native wifi default profile" that I could not change was giving itself priority over the normal wireless profile that was still working as it should. I read on some other discussion boards that this was due to the driver software so I went for deinstallation and reinstalling. And now even the Windows software (installed from the CD) isn't recognising my adapter anymore.

I don't know if the two things have anything to do with each other. Is it possible that all the things I have been trying for getting a driver on Xubuntu changed something in that respect?

I'm utterly confused and think I will now just go for buying this very long ethernet cable so I can connect to my router directly.

---

### Post by chili555 on 2012-12-16
> Is it possible that all the things I have been trying for getting a driver on Xubuntu changed something in that respect?I would never say it's impossible, because nothing is impossible, but I'd say it's very, very unlikely. My suspicion is that the device is, in some way, electrically defective.

---

### Post by wayneman on 2012-12-16
Oh well. Thank you anyway. Ill keep trying a bit and post if theres a positive turn of events. :-)

---

### Post by kurt18947 on 2012-12-16
> **wayneman said:**
> Oh well. Thank you anyway. Ill keep trying a bit and post if theres a positive turn of events. :-)

And if you do end up replacing your device, there are 'friendlier' choices than the wnda3100v2.

---

### Post by jmeyer18 on 2012-12-19
I can't "configure network" in "wireless network drivers" It says "could not find a network config tool". Even though i was able to get my Netgear WNDA3100v2 to work with the Broadcom hybrid driver and ndiswrapper. I had some of the previous problems in this post, and the answers here fixed them.  

I don't have any sort of internet connection to the machine with ubuntu.

I tried sharing my phone connection to my laptop and then share that connection to the machine with ubuntu. All it would do is surf the net but never download the nm-tool with "apt-get install network-manager", just sit at 0%. 

lsusb
Bus 001 Device 002: ID 0846:9011 Netgear, Inc. WNDA3100v2 802.11abgn (Broadcom BCM4323)

ndiswrapper -l
bcmn43xx32 : driver instaled
                device (0846:9011) present

iwconfig
lo                        no wireless extension
wlan0                 IEEE 802.11g  ESSID: off/any
                          Mode: Managed      Frequency: 2.412 Ghz   Access Point : Not-Associated
                          Bit rate: 300 Mb/s        tx-power: 32 dBm
                          power Management: off ........ etc 

eth0                  no wireless extensions.

sudo modprobe ndiswrapper
dmesg | grep ndis
[      7.352616] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[      7.957350] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[      8.213398] usbcore: registred new interface driver ndiswrapper





Do i need a network manager or how to i connect to a network i see when i scan???


sudo iwlist wlan0 scan

gives me over 10 networks all with various ESSIDs and info. 

Under Wicd Network Manager it says No wireless networks found. There are no options to mess with for wireless in here either.

---

### Post by chili555 on 2012-12-19
> Under Wicd Network Manager it says No wireless networks found. There are no options to mess with for wireless in here either.Let's try to figure out why. First,there is a possibility that Network Manager is actually installed and interfering with Wicd. Let's check:```
ps aux | grep -i network
```If you see, among other things, something like this:> root      1050  0.0  0.0  33176  5504 ?        Ssl  11:16   0:01 [COLOR="Red"]Network[/COLOR]Manager...then both are installed and no doubt conflicting. I'd see if there is an applet at the top right of your desktop like attached. Try to click the icon, see your network and connect. 

Please post back your findings.

---

### Post by jmeyer18 on 2012-12-20
Thank you for such a quick response. When i tried ps aux | grep -i network

root         18835   0.0  0.0   3368     748 pts/1    S+    08:25   0:00  grep  --color=auto  -i network

And i dont have an applet in the top showing connectivity of any sort. I'm running off of Backtrackr5 dualboot.

---

### Post by chili555 on 2012-12-20
Excellent. Network Manager is not running and probably not installed. In Wicd > Preferences > General Settings, is there an option for wlan0? What is the WPA supplicant driver? In most cases, wext is preferred.

[http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

---

### Post by jmeyer18 on 2012-12-20
No option for wlan0. Under Network Interfaces/ Wireless interface: nothing is written. under wired says "eth0". 
WPA Supplicant driver is wext.

---

### Post by chili555 on 2012-12-22
Let's be sure there are no extra settings in /etc/network/interfaces:```
sudo gedit /etc/network/interfaces
```If there are any listings there related to wlan0, please remove them. Proofread, save and close gedit.

Wicd requires your user name to be listed in the netdev group; check:```
groups jmeyer  [COLOR="Red"]<--or whatever your actual user name is[/COLOR]
```It should list something like:> username : username adm cdrom sudo dip plugdev lpadmin [COLOR="Red"]netdev[/COLOR] sambashare If netdev is not listed, add it:```
sudo usermod -aG netdev jmeyer [COLOR="Red"]<--or whatever your actual user name is[/COLOR]
```Are there any interesting clues here?```
cat /var/log/syslog | grep -i wicd | tail -n20
```

---

### Post by jkvt265 on 2012-12-23
when trying to run the exe file got this message:Archive:  /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe
[/home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe or
          /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe.zip, and cannot find /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe.ZIP, period.

---

### Post by jmeyer18 on 2012-12-23
Had to dl gedit apt. Some reason my phone connection dl'd this and not the nm-tool earlier. so i tried to dl nm-tool again and it did, but it was a nmgnome dl i think. i have KDE. When i run nm-tool it says state: unknown.  error: could not connect to NetworkManager.
When I ran sudo gedit /etc/network/interfaces there was wlan0 listed, so i did the latter of instructions.
groups daemon just showed daemon: daemon
so i added netdev. Now it says daemon: daemon netdev.
The last code cat /var does nothing.

Still cant configure network under wireless network drivers and wicd shows no wireless networks even tho a wlan0 scan does. Although i have gedit and nmtool for gnome now

---

### Post by chili555 on 2012-12-24
> **jkvt265 said:**
> when trying to run the exe file got this message:Archive:  /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe
[/home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe or
          /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe.zip, and cannot find /home/bill/Downloads/WNDA3100v2GENIE_Setup_V2.0.0.1_20111226-signed/Setup.exe.ZIP, period.The Windows .exe isn't going to run on Linux. You need ndiswrapper and the Windows XP .inf and .sys files. There are numerous copies posted on this forum; I know because I posted them!

Linux and Windows are two completely different things. Aside from ndiswrapper using the Windows .inf  and .sys files and two or three other minor examples, there is no similarity and no compatibility.

---

### Post by chili555 on 2012-12-24
> When i run nm-tool it says state: unknown. error: could not connect to NetworkManager.Probably because you don't have Network Manager installed. You need to work with Network Manager *OR* Wicd, not both. > groups daemon just showed daemon: daemonYour user name is actually *daemon*? Interesting and fascinating. When you open a terminal, it says???```
[COLOR="Red"]daemon[/COLOR]@ubuntu:~$
```Is that correct?

Can you actually type in wlan0 in the empty space in Wicd? Please see attached.

---

### Post by shane8492 on 2012-12-25
hey yall.  i am running backtrack 5 r3 as the only system on my laptop.  i have a netgear wnda3100v2.  i have the drivers installed finally. when i do the    ```

# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```   it registers the netgear card. when i go to     ```
ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present

```      it says the driver is installed and present.   when i go to     ```

iwconfig
wlan0     IEEE 802.11bg  ESSID:"AndroidTether"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B0:EC:71:AB:14:A8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

eth0      no wireless extensions.

``` that wlan0 is my internal card but it sucks balls and i dont want to use it if i can get this netgear up and running. when i go to ```
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

``` .   when i went to my windows wireless drivers and pulled up my drivers from my win xp install (through my eternet networking) it tells me that i dont have ndiswrpper installed???????   so i went to ```
sudo apt-get install --reinstall ndiswrapper-dkms ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-dkms

```  it tells me E:couldnt find package ndiswrapper-dkms. ?!?!?!  so i opened up my synaptic and reinstalled ALL ndiswrapper software and when i went to ```
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

``` i get    FATAL:module ndiswrapper not found    still.   please help me. please please please.. i am completely new to all of this.  i have only been using the linux system for a few days now but i really want to learn it.also im running ubuntu 10.04 (lucid)

[SIZE=4]**UPDATE**[/SIZE]
ok. i found out the problem was with the ndiswrapper.  what i did was completely uninstalled ALL ndis wrrapper components then rolled back to the kernal ndiswrapper-1.58rc1, of couse i had to compile the tarball.for instructions on how to rollback kernal versions and compile .tar files read this [http://bbs.archbang.org/viewtopic.php?pid=17440#p17440](http://bbs.archbang.org/viewtopic.php?pid=17440#p17440)
if you do an update you will have to recompile your ndiswrapper because it causes it to ,for lack of a better term "break". after doing that i uninstalled my built in wlan chipset and then rebooted linux.  after everything started back up i went to ```
iwconfig
wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```   after seeing the wlan2 on there i knew that my netgear card was installed and registering.  so i went to my wicd network manager and went in to prefrences and changed my wlan prefrence to wlan2. then saved that and went to refresh. badda bing badda boom my netgear card was up and running.   SWEET.  the crazy thing is that i have never used linux system before five days ago and with all the problems that i had i got it figured out before anyone could reply to my post.  BUT, i couldnt have done it without the support of Chilli555's older posts. so, thank you very much. you are positively brilliant with the linux wireless system.  thank you thank you thank you.  good luck everyone else with your netgear problems, they really are a bitch. just remember, any questions just go to the search part of the forums and type in general problem and odds are someone else had that problem already and its somewhere. if that fails GOOGLE. good luck everyone.

---

### Post by chili555 on 2012-12-26
> badda bing badda boom my netgear card was up and running. Awesome! Glad it's working. Thank you so much for posting the solution. I am quite sure Google will find it and you will have helped quite a few searchers. Thanks.

In short, searchers, ndiswrapper is a bit buggy right now and you must compile ndiswrapper-1.58rc1 for source.

---

### Post by shane8492 on 2012-12-27
> Awesome! Glad it's working. Thank you so much for posting the solution. I am quite sure Google will find it and you will have helped quite a few searchers. Thanks.

In short, searchers, ndiswrapper is a bit buggy right now and you must compile ndiswrapper-1.58rc1 for source.
yeah no problem. i couldnt have done it without your earlier posts though.  what really pisses me off though is my usb card is the v2 and the v2 doesnt support packet injection. i looked and looked and it just wont do it. i took it out of my computer when i found out and got pissed off and beat it with a hammer. that sucked.  so i went out and bought a new card, the netgear N900 WIRELESS DUAL BAND USB ADAPTER, model WNDA4100 with a Ralink-based chipset.  then i had to modify two of the files in the driver folder, but all and all it was much easier than the Netgear WNDA 3100 v2 wireless adapter.  plus the new one supports packet injection.  so thanks again for all your help.

---

### Post by stnicholas on 2013-01-05
I am attempting to install the Netgear WNA wireless adapter on an older HP Compaq Computer and have Ubuntu 10.04 installed. I am new to Ubuntu and have liked what I have seen and do not want to uninstall Ubuntu unless absolutely necessary. It is a HP Compaq dc 7100 SFF. Any assistance will be great even if I need to get a different wireless adapter.

---

### Post by chili555 on 2013-01-05
St. Nick! How come I didn't get that Rolex I asked about? Was I bad?

Please tell us about your adapter:```
lsusb
```> even if I need to get a different wireless adapter. There are lots of easier adapters, however, this one can be installed fairly easily if you are willing to take a few steps and, most of all, persevere.

---

### Post by stnicholas on 2013-01-06
It is a N300 Wireless usb adapter WNA 3100 with a usb cable and adapter cradle. The issue I am having when I put the resource cd in the computer drive is that is does not seem to recognize the cd and will not do the auto run. I do not mind having to do the install without the cd, but will need step by step instructions to do it. Also I plan to update Ubuntu to the current one version 12. I appreciate all your patience an d assistance on this. 

PS What is a Rolex? How about a Timex.

---

### Post by chili555 on 2013-01-06
>  I do not mind having to do the install without the cd, but will need step by step instructions to do it.The CD is built for Windows, Linux is not Windows. Oranges are not apples. I am quite ready to give you step-by-step instructions, notwithstanding your Rolex breach. Let's start by inserting the device in the USB slot and running this terminal command:```
lsusb
```Either post all of it or, if you can readily tell, just the wireless details. Once we know the result, we'll craft an installation strategy and proceed.

[http://images.askmen.com/fashion/watch/rolex-submariner_2.jpg](http://images.askmen.com/fashion/watch/rolex-submariner_2.jpg)

---

### Post by stnicholas on 2013-01-06
Ok the wireless I have is a MiFi device through a local provider Etex, which uses Verizon's towers. The device I am using is a Novatel MiFi 2200. How do I do this terminal command you mentioned in your last reply? Let me know what else you need to know if I missed anything.

---

### Post by chili555 on 2013-01-06
> **stnicholas said:**
> Ok the wireless I have is a MiFi device through a local provider Etex, which uses Verizon's towers. The device I am using is a Novatel MiFi 2200. How do I do this terminal command you mentioned in your last reply? Let me know what else you need to know if I missed anything.
???

I thought you said you have a WNA3100. No?

---

### Post by stnicholas on 2013-01-06
Yes I do, but the computer I am trying to install the WNA 3100 does not have a wireless card installed. That is why we purchased the wireless adapter to access the internet with it. It is an older extra computer we have that I have the Ubuntu installed on to check it out and maybe use it on other computers in the future.

---

### Post by chili555 on 2013-01-06
Walk over to the older computer you have Ubuntu installed on and stick the WNA3100 in its USB slot. Open a terminal Ctrl+Alt+t and run the command:```
lsusb
```Attached is a sample from my own computer. One of the items listed will be the Netgear wireless device details including the all-important USB.ID, something like 1852:7022 in my example. Obviously, yours will be very different. Write down the details on a postit or any scrap of paper and come back to the computer you are answering these posts with and tell me exactly what it says.

Do you still have the Ubuntu install CD? It may have some packages we need on it. Also, do you have a USB key or similar so we can possibly transfer some packages?

---

### Post by stnicholas on 2013-01-06
On the back of the Netgear usb is the model #, serial #, FCC #,MAC #and the ICC #. I have the Ubuntu install cd handy, and a usb flash key with me to save any info I need to.  This is what came up when I did the command. Bus Device 003 and ID: 0846:9020 Netgear Inc.

---

### Post by stnicholas on 2013-01-06
On the back of the Netgear usb is the model #, serial #, FCC #,MAC #and the ICC #. I have the Ubuntu install cd handy, and a usb flash key with me to save any info I need to. This is what came up when I did the command. Bus Device 003 and ID: 0846:9020 Netgear Inc.

---

### Post by chili555 on 2013-01-06
> ID: 0846:9020 Netgear Inc.At last! 

You need ndiswrapper and the Windows XP .inf and .sys files. Load the Ubuntu install CD in the tray of the older computer you have Ubuntu installed on and browse the files to pool > main > n > ndiswrapper. Drag and drop the two files, ndiswrapper-common and ndiswrapper-utils to your desktop. Right-click each and select Install with Ubuntu Software Center. Now download the attached file to a USB key and then to the desktop of the older computer you have Ubuntu installed on and right-click and select Extract Here. Now open a terminal Ctrl+Alt+t and do:```
cd Desktop/wna3100drivers
sudo ndiswrapper -i bcmwlhigh5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Your device should now be working.

These instructions are for a 32-bit installation, which I assume you have on an older computer. Verify:```
arch
```A 32-bit install will return: i686. If it's 64-bit: x86_64. If you have 32-bit, please proceed; if 64-bit, stop and post back.

---

### Post by ski98033 on 2013-01-07
Just wondering if anyone has managed to the the 5GHz working on 64bit 12.10?  I can get 2.4Ghz working (although it is slow) using either the bcmwlhigh5.inf or the bcmn43xx64.inf drivers and ndiswrapper, but it doesn't see the 5Ghz networks.  I would really like to find some usb nic that works with linux and 5GHz networks.

thanks

ski

---

### Post by koumorileo on 2013-01-18
hello chili555 (mad props to you chili555 i wouldn't have gotten this far with out your guidance in this thread )  and everyone else here ... ok so i have installed the driver ... installed the windows driver installer ... found the adapter ... got on the router ...(10.0.0.1) got an ip address (10.0.0.15) accessed the web ( several sites including this one) but when i try to run the included torrent program or access dlna (w/rygel and the rygle config) so access media files, the adapter dies ... i have used my ps3 and an app called skifta for android and they both knock the adapter off and no date can be sent or received .... i have opened the required port 8200 and made the ip static and forwarded the ip ...i had this working via hard wire .....    i did notice in the gui adapter status info the broadcasting ip was a crazy number (10.0.0.252 something like that i'm on my win 7 partition right now ) is this what is not allowing me to stream from my computer ? it only happens when i try to play a media file on the respective player (ps3 or my android  ) if there is more info you require please let me know and if this is the wrong place please direct me to where i should be asking this question ... 

ok so its a router issue its set to 802.11i and not a-g but i cant find the setting for that so i just went back to wired connection .... i still want to give props to chili555 and everyone on this thread it worked tho the first post should be a compile of all the steps as i went through each page of the thread seemed like all solutions were narrowed down to ndiswrapper and the driver (32bit or 64bit)

---

### Post by kaprial on 2013-01-20
i get 
couldn't find SourceDisksFiles section - continuing anyway...
when  trying to install 
then when I run ndiswrapper it says the driver is install and device present but I stiil dont have the wlan0 interface

---

### Post by kaprial on 2013-01-20
> **chili555 said:**
> Good morning! Please try:```
sudo modprobe ndiswrapper
dmesg | grep ndis
iwconfig
```I'll only be here for about another hour, so we need to crack this case!!
FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2013-01-20
> **kaprial said:**
> FATAL: Module ndiswrapper not found.Let's try the easy way first:```
sudo apt-get install ndiwrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common*
sudo apt-get install --reinstall ndiswrapper-utils*
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by Edris on 2013-02-24
> **chili555 said:**
> Good morning! Please try:```
sudo modprobe ndiswrapper
dmesg | grep ndis
iwconfig
```I'll only be here for about another hour, so we need to crack this case!!

Thank you guys for this forum topic!!!

After a whole week of looking for solutions this solved my problem!
My setup:
ASUS G75VX
    onboard WiFi available but not working in Ubuntu 12.04 amd64 bit
         ```
:~$ arch
:~$ x86_64
```Bought:
NETGEAR WNDA3100-100NAS

In UBUNTU:
here is what I did:
1. get synaptic
2. install ndiswrapper
3. install WINE
4. reboot
5. downloaded your second attachment [  Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip   ]

6. I cd into directory and:
    ```
sudo ndiswrapper -i bcmn43xx64.inf
sudo modprobe ndiswrapper

```reboot and it WORKED:popcorn::p:D:)

---

### Post by MikalMirkas on 2013-02-24
I'm having this issue as well - freshly installed Ubuntu 12.04 (64bit) with ndiswrapper - I have no access to the internet through the desktop I have Ubuntu installed on - only a cellular device which can post and act as a USB drive (which is how I got ndiswrapper installed).
[SIZE=1](Also, [SIZE=1]it looks like partial thread hijacking is [SIZE=1]ok[SIZE=1] in this forum[SIZE=1].[SIZE=1] Moving on...)
[SIZE=3][SIZE=2][SIZE=2][SIZE=2]I have the exact same adap[SIZE=2]ter [SIZE=2](WDNA3100v2). Starting from the first posts:

[SIZE=2]lbusb states that I have [SIZE=2]an a[SIZE=2]dap[/SIZE]ter with the ID 0[SIZE=2]846:9011 [SIZE=2]- I have downloaded Chili's .[SIZE=2]inf/sys that w[SIZE=2]ere provided on the first page of the thread.

[SIZE=2]I installed n[SIZE=2]dis[SIZE=2]wrapper-common and ndiswrapper-util[SIZE=2]s[SIZE=2] - I can[SIZE=2]'t install ndisgtk [SIZE=2]without an internet connection[SIZE=2].
[SIZE=2]I get [SIZE=2]an error regarding p[SIZE=2]ython-glade2, and when I try to install that package, I get a ton of d[SIZE=2]ependancy er[SIZE=2]r[SIZE=2]ors, so I've given up on that route.

[SIZE=2]I installed the provided [SIZE=2].inf[SIZE=2] [SIZE=2]with ndiswrapper.
[SIZE=2]-l gives me:
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
```

bcmn43xx64 : driver installed
device (0846:9011) present
```iwconfig gives me:

```
eth0 no wireless extensions.

lo no wireless extensions
```dmesg | grep ndis gives me no output.

sudo modprobe ndiswrapper gives me the following error:
```
FATAL: Module ndiswrapper not found.
```Don't know where to go from here. Tried installing the ndiswrapper-dkms as previously mentioned in the thread but I get another dependancy error.

The aforementioned computer has a Win7 partition with the working adapter that I can download packages with. I do not have WinXP installed.

---

### Post by chili555 on 2013-02-24
> Don't know where to go from here. Tried installing the ndiswrapper-dkms as previously mentioned in the thread but I get another dependancy error.You'll probably need to do this: [http://ubuntuforums.org/showpost.php?p=12527981&postcount=122](http://ubuntuforums.org/showpost.php?p=12527981&postcount=122)

---

### Post by MikalMirkas on 2013-02-24
> **chili555 said:**
> You'll probably need to do this: [http://ubuntuforums.org/showpost.php?p=12527981&postcount=122](http://ubuntuforums.org/showpost.php?p=12527981&postcount=122)

Well, aren't you speedy. ;)

Going to do a fresh reinstall before I do this. I do believe I may or may not have modified one of the core system files while trying to fix my adapter. I have all my .debs backed up along with that Sourceforge download.

Going to reinstall ndiswrapper and whatnot.
=
Post-install edit:

Back at the backup I made.

Installing the other packages - I had a ton of Clock skew errors, but regardless: 

```
FATAL: Error inserting ndiswrapper (/lib/modules/3.5.0-23-generic/misc/ndiswrapper.ko): Operation not permitted
```Doing sudo modprobe ndiswrapper gave me no output, but without the sudo command, it's the above error.

dmesg | grep ndis outputted three lines regarding registering new interfaces.

I also now have a wlan0 source in iwconfig. Tx-Power's at 32dBm though, might be a bit too high.

However, the problem is still here. I can't connect to my router - I inputted my WPA key and it's hung at connecting.

EDIT: Added ndiswrapper to /etc/modules - problem seems to have fixed itself.

Thank you.
[SIZE=1]i love you
[SIZE=1]Just have to get used to the interface [SIZE=1]now, woo[SIZE=1] reduced Windows dependancy.

[SIZE=1]Edit: Do you know if this plays "nice" with Win7?

[SIZE=1]I still need to use [SIZE=1]it - a reboot [SIZE=1]of Win7 [SIZE=1]reset my [SIZE=1]system clock to [SIZE=1]the year 2070 and some [SIZE=1]system icons are now gone.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE] [/SIZE]

---

### Post by chili555 on 2013-02-24
> Doing sudo modprobe ndiswrapper gave me no outputWhich means, roughly, 'command executed as ordered and I have no errors or warnings to report.'> but without the sudo command, it's the above error.Loading a module requires administrative priveleges, aka 'sudo.' Hence, the Operation not permitted.

Glad it's working!

---

### Post by MikalMirkas on 2013-02-24
> **chili555 said:**
> Which means, roughly, 'command executed as ordered and I have no errors or warnings to report.'Loading a module requires administrative priveleges, aka 'sudo.' Hence, the Operation not permitted.

Glad it's working!

I don't think I'm quite done yet.

Rebooting the OS causes the driver to shut off again... and I get the Fatal error from using modprobe on the ndiswrapper module.

Do I have to reinput everything upon reboots?

---

### Post by chili555 on 2013-02-24
> and I get the Fatal error from using modprobe on the ndiswrapper module.Please repeat the process I linked above, except the download of course, and let me have your report.

---

### Post by MikalMirkas on 2013-02-24
> **chili555 said:**
> Please repeat the process I linked above, except the download of course, and let me have your report.
Reproducable, but still tedious.

Everything works, but I still have to input those five lines every time I want to reboot my OS.
[SIZE=1]and getting certain programs [SIZE=1]to work with 64bit sometimes crashes Ubuntu :|[/SIZE][/SIZE]
Is there any way to automate it?

(Yes, it still works - I thought I broke something on the reboot because the drivers weren't working.)

---

### Post by chili555 on 2013-02-25
Please reboot so we have a clean slate. Is the wireless working? If not, please do:```
sudo modprobe ndiswrapper
```Now is it working or do you get a fatal error? If it loads and the wireless works fine, then let's automate:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

---

### Post by MikalMirkas on 2013-02-25
> **chili555 said:**
> Please reboot so we have a clean slate. Is the wireless working? If not, please do:```
sudo modprobe ndiswrapper
```Now is it working or do you get a fatal error? If it loads and the wireless works fine, then let's automate:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

I put ndiswrapper in /etc/modules... I get a Fatal error when I don't make install, etc, etc.
However, I find myself having to make install and whatnot every reboot. Is this natural?

---

### Post by chili555 on 2013-02-25
> However, I find myself having to make install and whatnot every reboot. Is this natural?No way, no how! What I'd like you to do is run this sequence after a reboot, copy and paste from the terminal to a text document and paste it here so I can examine it to see what is going on. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Then give me the link that's created when you do the paste.```
sudo modprobe wl
```I assume this will be an error, but let me see it anyway.```
cd Desktop/ndiswrapper-1.58
make
sudo make install
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by MikalMirkas on 2013-02-26
> **chili555 said:**
> No way, no how! What I'd like you to do is run this sequence after a reboot, copy and paste from the terminal to a text document and paste it here so I can examine it to see what is going on. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Then give me the link that's created when you do the paste.```
sudo modprobe wl
```I assume this will be an error, but let me see it anyway.```
cd Desktop/ndiswrapper-1.58
make
sudo make install
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

Ubuntu has a pastebin subdomain? Neat.

I'll edit this post in an hour (posting from my Win7 partition at the moment) with the results from the sequence and then the results from the first code block.

Edit:
Ok, now the driver seems to want to boot on startup.
As well, I get the following output (Don't even need Pastebin):
```
FATAL: Module wl not found.
```

---

### Post by chili555 on 2013-02-26
> As well, I get the following output (Don't even need Pastebin):I'd appreciate it. My focus is not that it fails on boot; we know that. My focus is what does or doesn't work as expected when you re-install the driver that we need to fix. So, once again, pastebin, please.

---

### Post by MikalMirkas on 2013-02-26
> **chili555 said:**
> I'd appreciate it. My focus is not that it fails on boot; we know that. My focus is what does or doesn't work as expected when you re-install the driver that we need to fix. So, once again, pastebin, please.

I'm confused to what you need.
Do you want the output that you requested, the entire output given, or the entire terminal copied?
The driver now (for some reason) boots on launch, where it didn't before, even with ndiswrapper in /etc/modules.

---

### Post by robertaLRP on 2013-05-25
Hi, I run an usb-installer of Backtrack5 on a notebook with Intel Centrino Advanced -N 6230 but it doesn't recognize it. I tried with an external usb Netgear network card (WNDA3100) but nothing happened. I wanna use it in live mode only, so I can't install anything. Could I add network card driver packages on some Bcktrack folders in my usb?

Thank you.

---

### Post by jubjub727 on 2013-06-06
i dont get wlan0 when i do it

---

### Post by chili555 on 2013-06-07
> **jubjub727 said:**
> i dont get wlan0 when i do itAre there any errors or warnings?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by Dave W on 2013-06-23
Thank you, chili555.

I went through this thread for nearly a day, playing around with a whole host of variables.
And Bob's your Aunty - it's working.
One relieved user here!

Thank you! :D

---

### Post by Dave W on 2013-06-23
Oh, by the way, my distro is 12.10 Quantal Quetzal, not 10.04,

The 25-post restriction was implemented since last editing my profile!

---

### Post by Dave W on 2013-06-23
Delete.

---

### Post by chili555 on 2013-06-23
>  it's working.
One relieved user here!
Music to my ears. Awesome!

---

### Post by WhyAlwaysSte on 2013-06-24
Hey,

I tried a few guides on here where others have been helped. My Ubuntu keeps saying ndiswrapper is not a command.

I presumed I had to then install this ndiswrapper, which i attempted through the Terminal and it failed.

So how can I install the drivers for WNDA 3100 v2?

I can't access the Router on the Pc with Ubuntu as it's downstairs, so the pc has no internet connection.

Please help. I hate Windows and don't want to reinstall as the pc is mainly a HTPC and i just want it for XBMC (tried openelec but found the installation process too complicated)

Thanks.

Steven

---

### Post by chili555 on 2013-06-25
There are two ways to install ndiswrapper if you don't have internet connectivity. The first and easiest is to get out the install CD with which you installed Ubuntu. Drop the CD in the tray and navigate to pool > main > n > ndiswrapper. Right-click both ndiswrapper packages and select 'Open with Ubuntu Software Center' and install the packages.

The other way is to go here and search for ndiswrapper-utils and ndiswrapper-common appropriate to your Ubuntu version; quantal, precice, oneric, etc., and appropriate to your architecture; 32- or 64-bit. Find out here:```
lsb_release -d
arch
```Download the packages on some connected computer and transfer them on a USB key or similar to the desktop of your Ubuntu machine. Then open a terminal and do:```
cd Desktop
sudo dpkg -i ndis*.deb
```[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

After you have finished installing ndiswrapper, post back your progress and we'll be happy to help.

---

### Post by WhyAlwaysSte on 2013-06-30
Hello,

Apologies for the late reply. Family.

Ok, I installed the common ndiswrapper file with no problem through the terminal.

Went to install the file bcmn43xx64.sys and i received this error:

dpkg-deb error: 'bcmn43xx64.sys' is not a debian format archive

Failing miserably to install this USB wifi adapter :(

---

### Post by chili555 on 2013-06-30
> **WhyAlwaysSte said:**
> Hello,

Apologies for the late reply. Family.

Ok, I installed the common ndiswrapper file with no problem through the terminal.

Went to install the file bcmn43xx64.sys and i received this error:

dpkg-deb error: 'bcmn43xx64.sys' is not a debian format archive

Failing miserably to install this USB wifi adapter :(You need to be installing the .inf file; the .sys will take care of itself:

```
sudo ndiswrapper -i bcmn43xx64.inf
```You're getting there; please be patient.

Please try again.

---

### Post by WhyAlwaysSte on 2013-07-02
Hello,

I tried to install the .inf file and i got this error:

Error: unable to find a version of ndiswrapper !

I have however successfully installed ndiswrapper-common_1.58-0ubuntu1_all.deb  and ubuntu says i have in the software centre.

---

### Post by chili555 on 2013-07-03
Please show us the exact result of these commands from the terminal:```
ndiswrapper -v
sudo dpkg -s ndiswrapper-common | grep Status
sudo dpkg -s ndiswrapper-utils-1.9 | grep Status
ndiswrapper -l
```Thanks.

---

### Post by Peert on 2013-07-05
Want to thank you Chili, using this as a guide I finally got my WNA3100 working on my old ThinkPad T41 :)

---

### Post by pc-athome on 2013-08-06
Glad you got things sorted, however for those who prefer a graphical method, install the following 5 ndiswrapper packages via synaptic as indicated in the attachment.

Then browse to your respective .inf file - if you don't have them to hand - here is where I posted them:

[https://www.ultimateeditionoz.com/forum/viewtopic.php?f=25&t=5217](https://www.ultimateeditionoz.com/forum/viewtopic.php?f=25&t=5217)

---

### Post by zack3 on 2013-08-16
Thanks for the helpful thread so far.  I got up to the drive install and it says its there. However when i use iwconfig, I get 
```

zack-All-Series Broadcom_bcm43xx_USB_32_64bit_v2 # iwconfigeth0      no wireless extensions.


lo        no wireless extensions.

```
Any idea what I might be missing?  I'm using the exact same adapter as marianlibrarian.  This is my first go with linux so I would appreciate as explicit directions as possible.  FYI I'm on Mint 15 if that makes a difference.

Thanks,
Zack

---

### Post by chili555 on 2013-08-16
> **zack3 said:**
> Thanks for the helpful thread so far.  I got up to the drive install and it says its there. However when i use iwconfig, I get 
```

zack-All-Series Broadcom_bcm43xx_USB_32_64bit_v2 # iwconfigeth0      no wireless extensions.


lo        no wireless extensions.

```
Any idea what I might be missing?  I'm using the exact same adapter as marianlibrarian.  This is my first go with linux so I would appreciate as explicit directions as possible.  FYI I'm on Mint 15 if that makes a difference.

Thanks,
ZackWhat do these diagnostics tell us?```
dmesg | grep ndis
ndiswrapper -l
uname -r 
arch
```

---

### Post by Cobaltikus on 2013-08-18
I just finished reading this entire thread. Can anyone, preferably chili555, confirm or deny the ability for WPA2-PSK on the Netgear WNDA 3100 v2 wireless adapter? I have followed the instructions and can see my network and scan and all that, but it always fails to connect after prompting for the password. All other devices on my wireless network are connected. The network is an 802.11n, but iwconfig displays 802.11g. My txpower was 40 something but I changed it to 15 as suggested with no change in results. (It actually shows 16 after the change, as opposed to 15)

---

### Post by chili555 on 2013-08-18
> **Cobaltikus said:**
> I just finished reading this entire thread. Can anyone, preferably chili555, confirm or deny the ability for WPA2-PSK on the Netgear WNDA 3100 v2 wireless adapter? I have followed the instructions and can see my network and scan and all that, but it always fails to connect after prompting for the password. All other devices on my wireless network are connected. The network is an 802.11n, but iwconfig displays 802.11g. My txpower was 40 something but I changed it to 15 as suggested with no change in results. (It actually shows 16 after the change, as opposed to 15)I can't confirm positively; however, this is the first such complaint I recall. If you change the router to WPA instead of WPA2 or WEP or open, does it connect seamlessly?

---

### Post by bmather9 on 2013-09-24
I am trying to set this up on Ubuntu server 12.04 64bit to connect to a WPA2 secured network. Everything seems to work and I can connect to my SSID with the following command:

> sudo wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant.conf -Dwext

Output from iwconfig shows I'm connected to my network "Legendary"

> bmather9@bmather9:~$ iwconfigas0t1     no wireless extensions.


lo        no wireless extensions.


as0t0     no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"Legendary"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:29:67:7A:23
          Bit Rate=300 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:7814   Missed beacon:0


as0t3     no wireless extensions.


eth0      no wireless extensions.


as0t2     no wireless extensions.



Unfortunately I can't seem to get an IP address.  I've tried using the dhclient command, but it just hangs and never gives me an IP.  I don't think the router is the problem as every other device connects without problems to it. 

Here is the output of ifconfig, you can see I don't get an IPv4 address for wlan0:

> bmather9@bmather9:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr b8:97:5a:06:d6:26
          inet addr:192.168.9.10  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::ba97:5aff:fe06:d626/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:685917 (685.9 KB)  TX bytes:1100580 (1.1 MB)
          Interrupt:42 Base address:0xa000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2375609 (2.3 MB)  TX bytes:2375609 (2.3 MB)


wlan0     Link encap:Ethernet  HWaddr 4c:60:de:ed:c0:99
          inet6 addr: fe80::4e60:deff:feed:c099/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26216 (26.2 KB)  TX bytes:41620 (41.6 KB)


bmather9@bmather9:~$




So what is my problem?  I honestly don't know anything about network config in linux.  I tried editing the /etc/network/interface file, but it didn't seem to do anything.  I also tried to set a static IP address using this interface file, but nothing changed.  Any help is greatly appreciated!

---

### Post by chili555 on 2013-09-25
Aren't you using Network Manager? It ought to do all this for you and without the terminal command:> sudo wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant.conf -Dwext Moreover, NM is designed to disallow an IP address for wireless if you have one for ethernet, which you do:> [COLOR="#FF0000"]eth0[/COLOR] Link encap:Ethernet HWaddr b8:97:5a:06:d6:26
[COLOR="#FF0000"]inet addr:192.168.9.10[/COLOR] Bcast:192.168.9.255 Mask:255.255.255.0
inet6 addr: fe80::ba97:5aff:fe06:d626/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1I suggest you detach the ethernet, click the NM icon and try to connect.

---

### Post by bmather9 on 2013-09-25
It's a headless server so the gui is not installed. Can I still use network manager? I'll try to round up a keyboard and monitor so I can try to configure with the ethernet unplugged; I've been doing everything over ssh so far.

---

### Post by chili555 on 2013-09-25
Ahhh, a server. I suggest you amend /etc/network/interfaces to something like:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.0.87
netmask 255.255.255.0
gateway 192.168.0.1
wpa-ssid your_ssid
wpa-psk your_password
dns-nameservers 8.8.8.8 8.8.4.4

```Then get the system to see the change:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Assuming there are no errors, I'd think you could safely detach the ethernet and ssh to the wlan0 address.

---

### Post by bmather9 on 2013-09-25
> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo eth0
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp
	post-up iptables-restore < /etc/iptables.up.rules


auto wlan0
iface wlan0 inet static
address 192.168.9.12
netmask 255.255.255.0
gateway 192.168.9.1
wpa-ssid Legendary
wpa-psk ********
dns-nameservers 8.8.8.8 8.8.4.4

I set my interfaces file as above then ran the command:

> bmather9@bmather9:~$ sudo ifdown wlan0 && sudo ifup -v wlan0ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 17663).
wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "Legendary" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.9.12/255.255.255.0 broadcast +        dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.


Looks like I'm still connected to my network.  

> bmather9@bmather9:~$ iwconfigas0t1     no wireless extensions.


lo        no wireless extensions.


as0t0     no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"Legendary"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:29:67:7A:23
          Bit Rate=300 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:8439   Missed beacon:0


as0t3     no wireless extensions.


eth0      no wireless extensions.


as0t2     no wireless extensions.


Wlan0 doesn't show up in ifconfig


> bmather9@bmather9:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:97:5a:06:d6:26
          inet addr:192.168.9.10  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::ba97:5aff:fe06:d626/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4311957 (4.3 MB)  TX bytes:1042762 (1.0 MB)
          Interrupt:42 Base address:0xa000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:483319 (483.3 KB)  TX bytes:483319 (483.3 KB)






What's next?

---

### Post by chili555 on 2013-09-26
```
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
```I am not yet sure it has much to do with the issue, but may we see:```
cat /etc/wpa_supplicant.conf
```As always, please disguise the WPA key. Do verify, however, that it is correct in every respect and exactly matches that in the /etc/network/interfaces file.

---

### Post by bmather9 on 2013-09-26
> bmather9@bmather9:~$ cat /etc/wpa_supplicant.conf
network={
   ssid="Legendary"
   psk="**********"
 } 

I originally had the psk in quotes and in hex, but have now changed it to normal ASCII characters still with quotes. Doesn't seem to affect anything either way when trying to bring up wlan0.

My original attempt shown below also gives invalid arguments:

> bmather9@bmather9:~$ sudo wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant.conf -Dwext
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument


---

### Post by chili555 on 2013-09-28
> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo eth0
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp
post-up iptables-restore < /etc/iptables.up.rules


auto wlan0
iface wlan0 inet static
address 192.168.9.12
netmask 255.255.255.0
gateway 192.168.9.1
wpa-ssid Legendary
wpa-psk [COLOR="#FF0000"]********[/COLOR]
dns-nameservers 8.8.8.8 8.8.4.4 What is here? It ought to be the key in clear text; that is, the exact key you put in the router. For example, if the key you put in the router's fill-in for the WPA key is ihatewarmbeer, then the interfaces file should be:> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo eth0
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp
post-up iptables-restore < /etc/iptables.up.rules


auto wlan0
iface wlan0 inet static
address 192.168.9.12
netmask 255.255.255.0
gateway 192.168.9.1
wpa-ssid Legendary
wpa-psk ihatewarmbeer
dns-nameservers 8.8.8.8 8.8.4.4 Is that what you have?

---

### Post by bmather9 on 2013-09-28
Yea, I have the WPA password in plain text (not hex) in the interfaces file. I double and triple checked it now.

---

### Post by bmather9 on 2013-09-30
I still don't have it working, is there something wrong with my basic networking settings that could cause this?

---

### Post by speed32 on 2013-11-18
Hi all. Thanks for the helpful thread. Chili I have read all the posts up the last page, however I am unable to get the wifi working.    I have reached up to the point where I type:      sudo modprobe ndiswrapper  dmesg | grep ndis       sudo modprobe ndiswrapper : does not show any feedback.     ```
dmesg | grep ndis
```: shows the following message:     ```
 [    4.416256] ndiswrapper version 1.58 loaded (smp=yes, preempt=no) [    5.302329] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded [    6.365597] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 [    6.365602] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) [    6.365607] ndiswrapper (mp_halt:254): device efc26480 is not initialized - not halting [    6.365609] ndiswrapper: device eth%d removed [    6.365644] ndiswrapper: probe of 1-1:1.0 failed with error -22 [    6.365660] usbcore: registered new interface driver ndiswrapper [ 2288.663526] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded [ 2289.752714] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 [ 2289.752721] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) [ 2289.752728] ndiswrapper (mp_halt:254): device eff7d480 is not initialized - not halting [ 2289.752731] ndiswrapper: device eth%d removed [ 2289.752855] ndiswrapper: probe of 1-1:1.0 failed with error -22 [ 2332.900735] usbcore: deregistering interface driver ndiswrapper [ 2332.907244] ndiswrapper version 1.58 loaded (smp=yes, preempt=no) [ 2332.912087] usbcore: registered new interface driver ndiswrapper [ 2562.663483] usbcore: deregistering interface driver ndiswrapper [ 2562.667807] ndiswrapper version 1.58 loaded (smp=yes, preempt=no) [ 2564.000503] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded [ 2565.080920] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 [ 2565.080927] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) [ 2565.080935] ndiswrapper (mp_halt:254): device eff7b480 is not initialized - not halting [ 2565.080937] ndiswrapper: device eth%d removed [ 2565.081004] ndiswrapper: probe of 1-1:1.0 failed with error -22 [ 2565.081793] usbcore: registered new interface driver ndiswrapper 
```

---

### Post by chili555 on 2013-11-18
> **speed32 said:**
> Hi all. Thanks for the helpful thread. Chili I have read all the posts up the last page, however I am unable to get the wifi working.    These are very tricky to get going. Any clues here?```
ndiswrapper -l
uname -a 
```Probably 40% of my forum activity, much of it unsuccessful, has been devoted to this one device.

---

### Post by speed32 on 2013-11-18
ok :) thanks for your quick reply, i got the following from that command:  ```
 root@bt:~# ndiswrapper -l bcmn43xx32 : driver installed 	device (0846:9011) present root@bt:~# uname -a Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux 
```

---

### Post by chili555 on 2013-11-18
Hmmm. It ought to say:> # ndiswrapper -l bcmn43xx32 : driver installed 
[COLOR="#FF0000"]device (0846:9020) present[/COLOR]I hope the device was inserted when you ran this?!? May we see:```
lsusb
```

---

### Post by speed32 on 2013-11-18
sure that code returns the following:      

```
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by chili555 on 2013-11-18
I don't know exactly where you got the .inf and .sys files, but would you try these instead? If you need guidance as to how to proceed, please post back.

[https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip](https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip)

---

### Post by speed32 on 2013-11-18
thanks, i downloaded those drivers, uninstalled the current one and installed the new one with the following code:

```
sudo ndiswrapper -i bcmn43xx32.inf
```

but I checked again using ndiswrapper -l, and get the following:

```

bcmn43xx32 : driver installed
    device (0846:9011) present
```

---

### Post by chili555 on 2013-11-18
> **speed32 said:**
> 

```

bcmn43xx32 : driver installed
    device (0846:9011) present
```Awesome! And now, after a reboot, does it work? Any clues here?```
dmesg | grep ndis
```

---

### Post by speed32 on 2013-11-18
i just rebooted, but it's not working, I get the same message as before with the code above:

```
[    4.602145] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[    6.619012] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[    7.641422] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[    7.641430] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[    7.641439] ndiswrapper (mp_halt:254): device ef163480 is not initialized - not halting
[    7.641443] ndiswrapper: device eth%d removed
[    7.641504] ndiswrapper: probe of 1-1:1.0 failed with error -22
[    7.641536] usbcore: registered new interface driver ndiswrapper

```

---

### Post by speed32 on 2013-11-18
i am using vmware, and have enabled the usb device as can be seen by lsusb.

---

### Post by chili555 on 2013-11-18
So you installed Backtrack in a virtual machine so you can use ndiswrapper and a dodgey USB device to do penetration testing, injection, hacking, cracking and what all?? Frankly, and I'm sorry to say this, I have no other suggestions.

---

### Post by speed32 on 2013-11-18
yes i wanted to test a few things if possible - mostly for learning etc. 

anyway i have posted a code on the previous page that returned the same result. 

it's very frustrating as i've searched for a solution for days to no avail.

---

### Post by wildmanne39 on 2013-11-18
speed32 first this topic is not supported on the forum, your best option is the aircrack or backtrack forum.

This device is not the device you want to use because it is hard to get it working properly without adding penetration testing.

Also you have added more issues trying to setup a wireless device in a virtual machine while it is not impossible it can be more difficult.
Thanks

---

### Post by fredrik.k91 on 2013-11-22
Thanks alot Chili555 for all help. I managed to get it running with your first few posts, but WPA2-PSK isn't working so I use a open network for now. 

Whenever I download something >100 MB the connection is terminated, which is very frustrating. The only way to fix it is to physically reconnect the adapter.

 Anyone got it running stable?

---

### Post by auriganexus on 2013-11-29
Hi chili555, I just want to say on behalf of everyone, thanks for all the advice.

I downloaded the driver files earlier as you said and used terminal to install ndiswrapper and the drivers, etc.

I got to the point where
```
root@aurgia-base:~# ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present

```

worked, but could not find wlan0 interface with 

```
root@aurgia-base:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


```

I rebooted, tried again with the above, no dice. Then I ran

```
root@aurgia-base:~# dmesg | grep ndis
root@aurgia-base:~# modprobe ndiswrapper
root@aurgia-base:~# dmesg | grep ndis
[  225.348271] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  225.654968] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  226.194145] usbcore: registered new interface driver ndiswrapper
root@aurgia-base:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

as you can see modprobing ndiswrapper did the trick. However I'm not in the clear yet. After that I looked on the network manager in the gui, and several wifi networks were shown including my own. However, when I attempted to connect to my wireless, it asked for my password then stalled. After about 5 minutes it asked for my password again. From the looks of it, it's kicking me off because of an incorrect wifi password.

This means that either:

A) The password has been changed recently without my knowledge

B) I'm typing it wrong

or

C) something is screwing up with the authentication.

Or at least those would be viable options, only

A) My other system with Windows 7 has and continues to connect automatically with the same password;

and

B) There is no way in hell I am typing it wrong since it hasn't changed in 4 years.

Which leaves some other issue with the authentication... but what?

I should also mention that I am actually running 64bit Backbox Linux, and not Ubuntu proper. However I'm guessing for the most part, an Ubuntu fix will work with Backbox since a lot of Backbox code was "borrowed" from Ubuntu. It has so far with the wireless drivers, as well as the Nvidia VGA driver issues I was having prior that prevented the GUI from booting (but that's another story.)

---

### Post by chili555 on 2013-11-29
> Which leaves some other issue with the authentication... but what?The issue that this is one of the most difficult and tricky devices in Linux to get going; that it is especially so in 64-bit; that ndiswrapper uses Windows XP drivers, not exactly the most robust drivers and undoubtedly not updated or maintained for many years. 

The general process of installing and using a wireless device in ndiswrapper is the same for all the Linux distributions I'm familiar with, although I might except Gentoo. Everything about it is weird. It might as well be Klingon!

You might try with your router set to WPA2 only, not mixed-mode WPA and WPA2. You might try with N speeds disabled. You might also set the router to a fixed channel, not Auto. [http://community.starhub.com/t5/image/serverpage/image-id/1180i6D43DB1C60D35BCA/image-size/original?v=mpbl-1&px=-1](http://community.starhub.com/t5/image/serverpage/image-id/1180i6D43DB1C60D35BCA/image-size/original?v=mpbl-1&px=-1) Channel 11 works well for me.

If that doesn't help, I am out of ideas. I am very willing, however, to 'fix' it to the rear wheel of my car while I go shop for a simpler, supported device!

---

### Post by finem on 2013-11-29
Hey, im getting stuck when connecting to my wifi. I actually made it work the first time and then it stopped working. Now I usually get Bad password when connecting to wifi, sometime i cant even connect my wifi adapter and make it work. Anyone that could help me out?

---

### Post by apollothethird on 2013-11-29
> **finem said:**
> Hey, im getting stuck when connecting to my wifi. I actually made it work the first time and then it stopped working. Now I usually get Bad password when connecting to wifi, sometime i cant even connect my wifi adapter and make it work. Anyone that could help me out?

I have the exact NIC.  I spent many hours initially trying to get it working.  When I finally got it working, I tested the bare steps on a couple of physical and virtual machines.  It works the first time every time with these steps:

How to set up the Netgear WNA3100 Wireless Adapter:
[http://faq.apollo3.com/ljames/ubuntu/networksupport](http://faq.apollo3.com/ljames/ubuntu/networksupport)

I'd be glad if you would test the steps to help me see if I'm missing something.  The card is very inexpensive and I have bought a few of them to have ready on my bench when working with various clients.  I hope to have very simple and easy to follow steps that will work every time.

Again, the steps are easy for me, if my writing is confusing to you, I'd like to know that also.  I just revisited the link when posting it for you and noticed some misspelling and typos of which I'm going to address now.

By the way, I had used this thread as well as countless others when I was spending the hours trying to get it working.  What was very complicated to me before appears to be simple right now.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by finem on 2013-11-29
> **apollothethird said:**
> I have the exact NIC.  I spent many hours initially trying to get it working.  When I finally got it working, I tested the bare steps on a couple of physical and virtual machines.  It works the first time every time with these steps:

How to set up the Netgear WNA3100 Wireless Adapter:
[http://faq.apollo3.com/ljames/ubuntu/networksupport](http://faq.apollo3.com/ljames/ubuntu/networksupport)

I'd be glad if you would test the steps to help me see if I'm missing something.  The card is very inexpensive and I have bought a few of them to have ready on my bench when working with various clients.  I hope to have very simple and easy to follow steps that will work every time.

Again, the steps are easy for me, if my writing is confusing to you, I'd like to know that also.  I just revisited the link when posting it for you and noticed some misspelling and typos of which I'm going to address now.

By the way, I had used this thread as well as countless others when I was spending the hours trying to get it working.  What was very complicated to me before appears to be simple right now.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

I reinstalled ndiswrapper but cannot find the ndiswrapper-dkms. Looked in synaptic and software center. Any ides where I can get it?

---

### Post by apollothethird on 2013-11-29
> **finem said:**
> I reinstalled ndiswrapper but cannot find the ndiswrapper-dkms. Looked in synaptic and software center. Any ides where I can get it?

Will you give me the output of:

```

$ sudo apt-get install ndiswrapper-dkms ndisgtk ndiswrapper-common

```

I don't recall doing anything special with any of my test machines, just typing in the commands listed in the FAQ.  While I wait for your response I'll try to identify why the command installed the drivers for me in each case and doesn't for you.

I tried to be particular careful in each case not to install anything special to ensure a simple solution that would be easy to duplicate.  It's possible that I might have inadvertently installed something.

I believe I ran the following commands on each machine:

```

$ sudo apt-get update
$ sudo apt-upgrade

```

But I don't recall anything else.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by finem on 2013-11-29
> **apollothethird said:**
> Will you give me the output of:

```

$ sudo apt-get install ndiswrapper-dkms ndisgtk ndiswrapper-common

```

I don't recall doing anything special with any of my test machines, just typing in the commands listed in the FAQ.  While I wait for your response I'll try to identify why the command installed the drivers for me in each case and doesn't for you.

I tried to be particular careful in each case not to install anything special to ensure a simple solution that would be easy to duplicate.  It's possible that I might have inadvertently installed something.

I believe I ran the following commands on each machine:

```

$ sudo apt-get update
$ sudo apt-upgrade

```

But I don't recall anything else.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

I managed to reinstall ndiswrapper again and still getting the same problem. Bad password when connecting to my network. 
Lsusb tells me that the wifi adapter is there. So nothing wrong there.

---

### Post by apollothethird on 2013-11-29
> **finem said:**
> I managed to reinstall ndiswrapper again and still getting the same problem. Bad password when connecting to my network. 
Lsusb tells me that the wifi adapter is there. So nothing wrong there.

Thanks for verifying that the simple install steps works.  I had went back to fresh computers and studying the history and found that, as I mentioned above, there were no other commands or installs involved with setting up the NIC.

Is it possible that you can try to create a very simple and easy password to be sure it's not mistyped and see if you're able to connect with that one?

Does other devices connect okay with the password using currently using?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by finem on 2013-11-29
> **apollothethird said:**
> Thanks for verifying that the simple install steps works.  I had went back to fresh computers and studying the history and found that, as I mentioned above, there were no other commands or installs involved with setting up the NIC.

Is it possible that you can try to create a very simple and easy password to be sure it's not mistyped and see if you're able to connect with that one?

Does other devices connect okay with the password using currently using?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

Yes, I just connected my Iphone to the network using the same password. Im doing a fresh copy of backtrack on virtualbox while i wait for a fix.

---

### Post by apollothethird on 2013-11-29
> **finem said:**
> Yes, I just connected my Iphone to the network using the same password. Im doing a fresh copy of backtrack on virtualbox while i wait for a fix.

I know it appears not to matter, and probably doesn't, but did you test changing the password?  I have had similar problems as this and changed the password and it worked.  I changed it back to the original one for all the other devices and the issue went away with the wireless nic I was having problems with.

It wasn't the 3100, that was some years ago.

I also had the problem with Windows and tested changing the password to something else and the problem was resolved.

This isn't a technical solution, and again, the changing of the password probably didn't make a difference.  But as I mentioned, performing the steps helped me to be ensured what I was inputing on both the server and the adapter.

While you test that (if you do) I'll be studying other solutions.

While you're testing virtual machines, doesn't the NIC work under a virtual windows machine?  I've seen rare occasions where I spent a lot of time on a bad NIC.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by tom-burnham on 2014-01-21
Another problem with this darn Netgear adapter...
I've gone through as many solutions as I can find, and have gotten through a lot of the problems.  Tryin' to get Ubuntu 13.10 to play nice with this N600 WNDA3100 adapter.  I have gotten this far:
> p:~$ ndiswrapper -lbcmn43xx64 : driver installed
    device (0846:9011) present
So that's good.  Then "sudo modprobe ndiswrapper" runs without error.  Then I hit a wall.
> :~$ dmesg | grep ndis[   11.697588] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   11.698294] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   12.758635] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   13.012165] usbcore: registered new interface driver ndiswrapper
[   84.447548] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  312.806290] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  336.564846] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  607.140280] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  652.316686] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 4174.877138] ndiswrapper: device wlan0 removed
[ 4720.233483] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 4766.258044] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 5214.357540] ndiswrapper: device wlan0 removed
[ 5657.177535] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded

I don't know how to fix the module verification (pardon noobiness), let alone the other stuff, despite a couple days research.
Here's some other info I hope helps.  The adapter is at least passively functional; I can scan for networks and even attempt to connect through the GUI.  But to no avail.  It doesn't successfully connect and just repeatedly asks for the password.
When I use term to connect it used to spit out "essid: host unknown".  Now it says my password is an invalid argument.
Help a noob?

---

### Post by cjsnow1 on 2014-03-17
After reading through this thread I hit the same 'authentication error' wall that others have been running into. I'm using WPA-PSK2 and am unable to change the authentication as the router belongs to my roomamte.

Help in getting this working would be greatly appreciated.

---

### Post by Oscar_Gardea on 2014-04-25
.

---

### Post by link2 on 2014-05-19
FIXED!! I was looking online for three days. Page 2 had the solution from page 1. This was the final step,  Thank you!!

---

