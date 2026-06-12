---
title: "Intel Centrino Ultimate -N 6300 AGN disabled - no network"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Niels_dk on 2010-08-31
Hi 
 
Im trying to get ubuntu running from a USB stick on my Company HP Elitebook 8540W. I'm not allowed to use dual boot, so I have to use Pendrive Linux. 
 
This works OK, but I cant get the networking up running. I have the above network card (Intel Centrino Ultimate N 6300 AGN). 
 
I only have access to wireless, and since the wireless don't work (not direct cables where I live) I can't use Apt-Get -install
 
The network card seem to be disabled, but the right firmware seem to be there: 
"iwlwifi-6000-4.ucode". I found an entry somewhere asking me to install "linux-backports-modules-karmic". But not being able to use Apt-Get -install I don't know how to do this (I downloaded something, but don't know what to do with it)
 
Can anyone please help me figuring out how to enable the card? I can access the network when I boot the PC in Vista, so I can download stuff and get it into Ubuntu.
 
I folowed the instructions elsewhere in the forum, for how to report wireless problems. The output of the commands are below:
 
>>>>>>>>>>>>> Begin Test <<<<<<<<<<<<<<<<<
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lspci -nn | grep WiFi
44:00.0 Network controller [0280]: Intel Corporation WiFi Link 6000 Series [8086:4238] (rev 35)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ iwconfig wlan0
wlan0 IEEE 802.11abgn ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=off 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsmod | grep WiFi
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ dmesg | grep WiFi
[ 34.611531] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 34.611723] iwlagn 0000:44:00.0: Detected Intel Wireless WiFi Link 6000 Series 3x3 AGN REV=0x74
ubuntu@ubuntu:~$ sudo lshw -C network
*-network 
description: Ethernet interface
product: 82577LM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 06
serial: 70:5a:b6:b1:66:f0
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.12-3 latency=0 link=no multicast=yes port=twisted pair
resources: irq:35 memory:d7500000-d751ffff memory:d752a000-d752afff ioport:6020(size=32)
*-network DISABLED
description: Wireless interface
product: WiFi Link 6000 Series
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:44:00.0
logical name: wmaster0
version: 35
serial: 00:24:d7:21:ee:a4
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:36 memory:d3300000-d3301fff
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsb_release -d
Description: Ubuntu 9.10
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ uname -mr
2.6.31-14-generic i686
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... [ OK ] 
ubuntu@ubuntu:~$ 
 
>>>>>>>>>>>>>>End Test <<<<<<<<<<<<<<<<<

---

### Post by DavidOfLondon on 2010-08-31
Brother, you've asked the one question I see more times than ANY other on ALL Linux forums. It is the MOTHER of ALL linux distro questions and you are in for a world of pain.

I strongly suggest you locate this document online (I can't find the link, apologies) - "wifi-backtrack_2038". It's a PDF written by two Microsoft guys who from the start vent their frustration at trying to connect a network in Backtrack distro.

It's a f---ing nightmare.

I eventually just gave up completely on all Backtrack distros because FOUR PCs would not connect to wifi using Backtrack even though all four were compatible AND ran seemlessly with other linux systems.

Your read out is similar to mine and the "AP Not Associated" is the crucial part. I accidentally managed to get my AP associated on wlan0 after playing with every single iwconfig and ifconfig and script network manager prompt under the sun. I then rebooted and bingo, it was gone again, and I couldn't remember how I'd achieved it first time. A million posts to forums got me nowhere - contrary to the myth, linux users are no more magnanimous than windows users and they're often a far more condescending crowd, even though you do meet some truly wonderful souls here. One of the actual founding fathers of Backtrack got back to me and said "Go use something else" - wow...and they celebrate "2 million downloads" of their product when "2 million downloads" actually equates to a gigantic dropout rate once people realise it is about as user-friendly as a kick in the gonads...and yes, yet again, they cannot be bothered to write proper manuals for new users. Why? Because the guys who set it up are making money running online courses and selling books about how to use Backtrack!

"Free" ? Hmm....

I have scoured the internet for months and I am yet to see a single one of these supposedly community-oriented, peace-love-and-understanding linux experts write and publish a FULL free guide to what is easily the most blatant and absurd flaw in Linux OSs - a computer that can't even log onto to a cable or wireless network?! In the 21st century?! You can make a desktop stick to a 3d cube and spin around but you can't write a full pdf on setting a wireless network up?!?! No wonder so many people go back to Windows and Apple Mac.

I'm fortunate - my Ubuntu 10.04 install was seemless and I adore it. I have no issues. Backtrack, on the other hand? Well they can go and do a certain thing to themselves :)

The doc I pointed you to gives an excellent description of networking in linux and I am telling you here and now that if you don't read up on it you won't be able to even ask the questions you're gonna need to ask.

Have you tried changing the ifconfig/iwconfig modes? I've seen a lot of folk say that switching it from "mode managed" to "mode auto" suddenly changed everything. 

In a terminal type "man" before any command and it'll list all the possible variables.

The thing is, linux is free and it is fast and it makes windows look like Aesop's tortoise, but it also involves some effort. My advice is to simply start treating these problems as projects - you're setting out on a project. I assure you - there is a solution for your networking problem.

For example, I wanted to use several features in Backtrack 4 to logon to my wireless and change settings etc, but the damned thing wouldn't even let me ENABLE wifi!! So I said, "Hey...I'll find a way to use their stuff on Ubuntu". I got the apps installed and spent THREE days trying to get it to work. In the end, I read the manual ("man" command) and thought, "Well to hell with the advice, I'm changing this option to number -3" and by Jesus, it worked.

I shouted so loud my flatmate ran upstairs thinking something awful had happened.

Moral? If you find the way through, come back and edit your original post so others can see your solution - long-term users hardly ever bother to help new people.

PM me and let me know how you get on.

Dave.

---

### Post by relay_man on 2010-08-31
At the command line, enter "sudo ifup wlan0"  (without the quotes)

and post the output

---

