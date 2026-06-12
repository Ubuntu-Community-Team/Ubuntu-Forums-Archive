---
title: "Wireless &quot;Disabled&quot; w/Dell Inspiron 1150"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by scott092707 on 2010-10-18
I hope someone can help.

I am testing Ubuntu 10.10 (live CD) on my sister's  Dell Inspiron 1150   laptop (which is a bit underpowered (.5G memory, 19G free HD space) but Ubuntu seems to boot OK).

Her Ethernet port seems not to work, so I am trying to use Wireless, which works just fine on the installed Windows 7.

wlan0 is listed as "Disabled", when I run the relevant terminal command.
It looks as if everything is there, but it doesn't work.
The Notification drop-down menu says "Device not ready (Firmware missing)"

I did find out when selecting F2 on boot, that Dell had the Wireless disabled, but I enabled it (and saved the setting) and get the exact same results.
I tried Fn-F2, as I found by searching the internet for Dell Inspiron 1150, and it does nothing (but perhaps Ubuntu steals that key combination?).   From Windows 7, Fn-F2 does turn off the Wireless, but I thereafter cannot get it to come back on...

Since I am not installing Ubuntu (not my computer), just trying out the Live CD, anything that involves making a change and rebooting presumably will not work.

I enclose a cut-and-paste of all commands suggested by Wireless Troubleshooting sites for Ubuntu/Linux.

I hope that I can get this solved - there is no possibility of convincing my sister to let me install Ubuntu on her computer if she would not be able to use the internet (the Ethernet port seems not to work, with Ubuntu or Windows).

Thank you in advance for any help you can give.

---

### Post by garvinrick4 on 2010-10-18
Google broadcom and your card # and Ubuntu. It is a dell thing they have proprietary drivers and as you know ship a seperate disk for there Windows drivers instead of using
the normal drivers shipped with dos kernel. Dell wants you to stay with them it seems
at the cost of even bastardizing the normal Windows Operating Systems disks. There are
drivers out there, I had some fixes but yours must be a little older of a machine. Sending your cards was nice but next time copy and paste whole document and the highlight and hit the # sign in upper right corner of message box and will put in a nice scrolling box to read instead of attachment. Try googling for a while and someone will come around here with your same card and driver and help you out usually.

---

### Post by garvinrick4 on 2010-10-18
Scott, You did look under System/ Admin/ additional drivers?

---

### Post by garvinrick4 on 2010-10-18
Found this for Live CD 

LiveCD/LiveUSB
For temporary use with the LiveCD and LiveUSB environments, simply use the Software Centre or the Synaptic Package Manager to search for and install the bcmwl-kernel-source package. Refer to Step 1 and Step 2 of the instructions above. Just install bcmwl-kernel-source is all Step 1 and 2 were.

```
sudo apt-get install bcmwl-kernel-source
```

Instead of a computer restart, in a terminal issue the following commands:

~$ ```
sudo modprobe -r b43 ssb wl
```~$ ```
sudo modprobe wl
```Note: Allow several seconds for the network manager to scan for available networks before attempting a connection.

They say will work with your card, let me know.

---

### Post by scott092707 on 2010-10-19
[>garvinrick4]("http://ubuntuforums.org/member.php?u=899097") : Scott, You did look under System/ Admin/ additional drivers?
It informed me that there were "no proprietary drivers [installed?]

"sudo apt-get install bcmwl-kernel-source " worked fine (which surprised me, as I had no internet access - it must get it from the CD)

however,
"sudo modprobe -r b43 ssb wl" did not. ---> "FATAL: module ssb is in use."
"sudo modprobe wl" generated no output, so was I guess successful, but perhaps was not useful without a successful previous modprobe.

Result:  fewer items in the notification menu and in the (lshw -C network?) terminal network troubleshooting commands, and of course, no success in finding and connecting with network.

-Scott

---

### Post by TBABill on 2010-10-19
Scott, there is something else with 10.10 causing this. I have yet to find the adequate fix, but this is not a Dell issue at all. If it were, 10.04 would not work either. Mine works fine on 10.04 but I can see networks with the STA driver installed (just like in 10.04), but it will just not connect. Wired works fine. I even tried Mint 10 (based on 10.10) to see if they had fixed this bug before release, but it's there too so they didn't make any changes to Ubuntu that would make a difference.
 
It's not a driver issue because this is affecting different brands of cards in the same way. Not all cards, but many have posted the identical symptoms. Can you install 10.04 for her instead? It's LTS so it has 3 years of support and works fine with the Broadcom cards (mine is a BCM4312).

---

### Post by johnnytm on 2010-10-19
It looks to me as though you have 2 wireless interfaces installed somehow. One of which relates to no hardware. By the way it would be easier if you could paste your code directly just use [ c o d e ] before what you paste and [ / c o d e ] afterwards. leave out the spaces of course.

---

### Post by johnnytm on 2010-10-19
> **TBABill said:**
> Scott, there is something else with 10.10 causing this. I have yet to find the adequate fix, but this is not a Dell issue at all. If it were, 10.04 would not work either. Mine works fine on 10.04 but I can see networks with the STA driver installed (just like in 10.04), but it will just not connect. Wired works fine. I even tried Mint 10 (based on 10.10) to see if they had fixed this bug before release, but it's there too so they didn't make any changes to Ubuntu that would make a difference.
 
It's not a driver issue because this is affecting different brands of cards in the same way. Not all cards, but many have posted the identical symptoms. Can you install 10.04 for her instead? It's LTS so it has 3 years of support and works fine with the Broadcom cards (mine is a BCM4312).
The BSM4312 works with the sta driver though and has th b43 and ssb both blacklisted. However there is an option to install the b43 instead of the sta when enabling your wireless driver and if you install the b43 chances are real good you will have problems. However I dont know if the same issues exist with the BCM 4306. doing a little research right now.

---

### Post by TBABill on 2010-10-19
I want to clarify my above post. I did NOT intend to say that my BCM4312 does not work with 10.10 and I apologize I confused my adapters...which works and which does not. My Realtek RTL8111 does NOT connect in 10.10. My BCM4312 DOES connect and works fine with the STA driver in Maverick.

My apologies. I just re-read my post and see I was mistaken earlier.

---

### Post by bkratz on 2010-10-19
> **TBABill said:**
> I want to clarify my above post. I did NOT intend to say that my BCM4312 does not work with 10.10 and I apologize I confused my adapters...which works and which does not. My Realtek RTL8111 does NOT connect in 10.10. My BCM4312 DOES connect and works fine with the STA driver in Maverick.

My apologies. I just re-read my post and see I was mistaken earlier.




Here is a whole thread about that. It is known and the bug report which is mentioned later in the posts says the fix was recently released.

[http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

---

### Post by scott092707 on 2010-10-22
>Can you install 10.04 for her instead?
It appears not...  I downloaded and burned it on her desktop computer, but
when I tried to boot it, it stayed a long time on the Ubuntu logo with colored dots
underneath that changed color left to right (to give us something to look at), and
then a blank screen with absolutely no disk activity...
Short of an unsuccessful burn, it appears 10.04 will not boot on her Dell Inspiron 1150.

I will take a look at those bug report links now...

Thanks anyway.

---

### Post by RJARRRPCGP on 2010-10-22
Was the hardware made after Lucid Lynx was in feature freeze?

---

### Post by scott092707 on 2010-10-23
>Was the hardware made after Lucid Lynx was in feature freeze?
I think not...
1. "Designed for Microsoft Windows XP"
2. "Intel Inside - Celeron"
3. .5G RAM,
4.  30G Hard drive

---

### Post by johnnytm on 2010-10-23
There are a couple of things you can try with Dell's. 
try the following codes
```
sudo su
``````
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
``````
exit
```can't guarantee but it has worked for a few others with this same situation. 
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

---

### Post by scott092707 on 2010-10-25
While I have not so far had success in fixing this problem, I believe I am closer.

While using the Live-CD of Ubuntu 10.10, I was looking around, and noticed the program to display log files.
In looking at the log file for dmesg, I found two clues:
1.  two files that it did not find:
    'b43/ucode5.fw' and   'b43-open/ucode5.fw'  (fw-->firmware?)
2. a note that I should go to 'wireless.kernel.org/en/users/Drivers/b43#devicefirmware'

I did so, and it said that the one needs to install firmware for the Broadcom, and that I should first 'lspci  -vnn | grep 14e4' and compare the number displayed after '14e4' with the list they provide.
I found that the number was '4320', and that the 4306 chip was rev. 3, meaning that it is supported, and that I should use the b43 driver (which appears to be what Ubuntu is trying to use).
It said I should get the driver (which I found in a code snippet could be found at 'http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 ') and then use b43-fwcutter to remove the firmware file(s).
I downloaded the tar.bz2 file and the b43-fwcutter file onto my Windows desktop, and then booted the Live-CD, but then found I had not needed to get the fwcutter, as I was able to 'sudo apt-get install' it from the Live-CD.

I tried to use the archive manager to extract the driver files, but for some reason it greyed out the file. I figured I would have to use the terminal instead, so I 'man tar'd, but did not see anything about compression, so figured I would have to uncompress  it first.
Here is where I hit my roadblock...
When I did 'bunzip2 -k  <the driver  tar.bz2 file>', it replied that the file "has 1 other link".
This does not give me a clue as to what is wrong or what to do...

If someone knows what this message means, please let me know.

-Scott

---

### Post by johnnytm on 2010-10-25
Have you tried to build the driver yet?
Once the tar file in decompressed you should find a readme file in there that will give you instructions to build the file to install . Tar files generally are not ready for direct install if u have never done it before U will have to make sure u know exactly what directories u have your files in because you need to change directories in terminal in order to build the file. its really not that complicated. If u can somehow get a wired connection to work u can use these instuctions [http://ubuntuforums.org/showthread.php?t=1598309](http://ubuntuforums.org/showthread.php?t=1598309) in post 5 to install terminal in your folders. eliminates the need to change directories.

---

### Post by scott092707 on 2010-10-25
> [johnnytm] Have you tried to build the driver yet?

Uh, no.  I would use tar to un-archive the files, but the file must be un-compressed first, and as I said, bunzip2 gave me an error message...

Also, I think the driver is there, somewhere, already. Ubuntu, in various commands, displays the driver as b43, which appears to be the right driver.  It just seems not to have the firmware (or perhaps it is there, but in the wrong place: the right place apparently being "/lib/firmware").

---

### Post by Cathhsmom on 2010-10-25
My mother's Dell XPS laptop has been giving her the same message lately, all this week.  She has Vista only.  She has been using the Dell Lan Utility to enable, and it works for a while, then we get the message again that her card is not enabled.  Could it be a Windows issue?

---

### Post by Darkmagic on 2010-10-25
```

```
Hello Everyone,

I have the same issue here. I have a Dell Inspiron 1150, which also runs the b43 driver. Like Scott, Ubuntu displays the same message under the network connections (firmware missing).

If you guys have any leads, please let us know.

---

### Post by johnnytm on 2010-10-26
Scott using the tar file is not as simplle as decompressing the file. Generally once the tar file has been decompressed, whatever is in the file needs to be built. Decompressing the file should be as simple as right click and press extract here. which will create a new folder inside the folder you saved the original tar file to. If you open that folder you should see a few other files in there, one of which should be a read me file, which gives very clear instructions on how to continue with the make, build and install of the tar files contents. generally the only files you download that are capable of direct install would be .deb files. I'm sorry if there is a misunderstanding, but it appears to me as though you are trying to install the tar file without first building it. Am I wrong in assuming this? Also is there any way at all you are able to connect via a wired connection? I hate to sound pessimistic but I have never had any success with the b43 driver or fwcutter. If you post the details of 
```
sudo lshw -C network
```it will show what if any driver is installed

---

### Post by scott092707 on 2010-10-26
>[johnnytm] it appears to me as though you are trying to install the tar file without
> first building it. Am I wrong in assuming this?

Yes.   'wireless.kernel.org/en/users/Drivers/b43#devicefirmware' said that I should use a file called 'b43-fwcutter' to remove the firmware file(s) from the driver, which should be in the tar file, which I so far cannot access, as it is part of a tar.bz2 file, and thus must be decompressed by bunzip2, which as I said, fails to decompress, saying that the file "has 1 other link".  This message I do not understand, which is why I left my last two messages.

>Also is there any way at all you are able to connect via a wired connection?
No.  As I said in an earlier post, the ethernet port appears not to function (did not work in trying to connect to my sister's other computer, or later to a different computer - with Windows 7, or with the Live-CD Ubuntu 10.10).  When I used Ubuntu 9.10 on a completely different computer in Germany, the wired connection (eth0) worked just fine, with no effort from me).

I will try the command you suggested, and then report back the results.

---

### Post by scott092707 on 2010-10-26
Here is the result from 'lshw':

[This looks familiar -  I think it is part of the large set of output I attached to my original post...
So, based on  my research, Ubuntu is using the right driver - b43 - but apparently does not have the firmware.  Shouldn't the firmware be part of the driver?  It would have to be, no, or b43-fwcutter wouldn't be supposedly able to extract the firmware from the driver.  If the driver is there, then if I could find out where the driver file is, I could use b43-fwcutter on it and get the firmware and store it to /lib/firmware.  Any idea where?]

-------------------------------------------------------------


ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:5e:82:64
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:7 memory:fcffe000-fcffffff memory:fd000000-fd003fff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:fcffc000-fcffdfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:08:ef:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by johnnytm on 2010-10-26
your whole network setup looks to me like a mess. First I have never seen a network:0 network:1 and so on like that. It is usually just *-network .Do you have a total of 3 network adapters in your machine? Thats what i see listed, however the last 2 appear more like 1 network adapter jumbled up into 2. If that's the case, I would delete any connections I have in network manager, uninstall network manager completely, delete any and all broadcom entries in synaptic, boot from the live CD again and allow it to re-install. If you can get that far when you go to add the broadcom wireless driver, try to choose the broadcom sta driver instead of b43 and try that. right now the driver is definately there, but I think it's kinda confused between 2 different cards, If you tried earlier to instal the bcmwl package and got anywhere with that there is also a chance you blacklisted the b43 driver. check the folder etc/modprobe.d if there is a blacklist-bcm43.conf file that will definately cause issues. You can open a terminal and enter ```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
``` just put a # at the beginning of every line and hit save when it opens. bear with me some here I'm trying to think of some other thing I could be missing.

---

### Post by scott092707 on 2010-10-27
>your whole network setup looks to me like a mess
This is what is set up by the Live-CD.

>Do you have a total of 3 network adapters in your machine?
I'm guessing 2 or maybe one, if one can do both Ethernet and Wireless
If you notice, there are only 2 Physical IDs.

>boot from the live CD again and allow it to re-install
This is not installed - only Live CD.  [if I cannot solve this Internet problem, then there is no point in installing the OS.]

>If you tried earlier to instal the bcmwl package and got anywhere with  that
> there is also a chance you blacklisted the b43 driver.
No, and No.

Just the Live-CD, plus whatever commands that have been suggested.

If the sta driver is on the Live-CD, I suppose I could try that (or download from somewhere with Windows 7, store it on the hard drive, and then do something with it after booting with the  Live-CD.)  I don't know how to remove the b43 driver and install the sta driver, but...

>I would delete any connections I have in network manager, uninstall  network manager 
>completely, delete any and all broadcom entries in  synaptic, boot from the live CD 
>again and allow it to re-install.
Ignoring whether these ideas would work, wouldn't they all be completely undone  if one booted from the Live-CD and let it re-install...?

---

### Post by johnnytm on 2010-10-27
Everything doesn't always get uninstalled when u reinstall something different. For example the b43 driver and the sta driver are not dependant on one another, therefore installing one will not remove the other. The reason I suggested that was to try starting all your networking again from scratch, if there is nothing else installed, there is nothing to conflict with a fresh install, that was my only reasoning for recommending that. The sta driver should be on the live cd. If u insert the live cd and go to synaptic hit settings and repositories then. put a check in the official cd box close the window and press the reload button then do a search for bcmwl-kernal-source and install that. If its not there use bcmwl-sta-common. also both my ethernet and wireless connections show the same physical address of 0 If you really want to try and install the actual broadcom driver they have it on their website along with a readme file on how to install it, which includes instructions for removing all old versions and the b43 as well I could point you to that if u are interested. It is the most relaible way, but not necessarily the easiest

---

### Post by Darkmagic on 2010-10-29
If you use Puppy linux, the wireless internet would work, surprisingly. Does anybody know why?

I tried that on my Dell 1150 and the wireless worked.

---

