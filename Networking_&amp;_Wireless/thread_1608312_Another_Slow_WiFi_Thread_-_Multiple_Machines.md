---
title: "Another Slow WiFi Thread - Multiple Machines"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by Linxuxslate on 2010-10-28
OK, I know it is kinda rude to start another "Slow Wireless" Thread, and  pardon the tone, but I'm very frustrated, and something definitely is  definitely wrong in Ubuntu, not Firefox, my router, or a particular  driver.

I have 2 different modern, decent laptops.  They have 2  different WiFi chips, but the symptoms are nearly identical -- Difficult  to connect -- Won't connect unless the signal is very strong -- VERY  poor speeds if/when I can get connected.

PLEASE Do not tell me to install linux-backports.  I've tried that multiple times on both machines.

PLEASE  Do not tell me to disable IP6 (or do anything else) in Firefox.  It is  NOT a Firefox issue.  VoIP (ekiga and empathy, multiple providers) is  unusable.  Downloading even a small update via Update Manager often  reports it will take SEVERAL DAYS to download the updates.  FTP  transfers are affected too, even on my LAN.

PLEASE Do not tell me to disable IP6 in the kernel.  Tried that.  Also, _performance on both machines is fine to excellent when plugged into Wired Ethernet._

PLEASE  Do not tell me to iwconfig wlan0 power on/off,  rate 54,...  etc.  I  understand iwconfig and the settings, and I have tried everything  logical (and then some).  Same for iw.  (although I do think it *could* be a regulatory domain problem).  Same for MTU -- Been there tried that.

PLEASE  Do not tell me to try compat-wireless.  Tried it.  on the Sony Vaio),  there was some improvement with connecting to AP's/staying connected,  but still have above speed problems.

PLEASE Do not tell me to change DNS settings.  See above.  It's not DNS.

Both Machines have A LOT of difficulty connecting to WiFi AP's.  Here at the house, at my work, and at public WiFi.

Especially  on the Sony, I've been surfing the threads for several months, and  short of ndiswrapper, I have tried almost everything (as evident by the  above)

More Details:

I am not using/trying 802.11n.

I am in the same room as the router (about 2 meters away!!)

Several Android devices Connect fine -- Good speeds.  Other devices work much farther from the router.

The Machines with problems:
Sony Vaio VPCCW21FX
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ath9k (from compat-wireless 2.6.35-1)
Ubuntu 9.10


ASUS  X83Vm-X1 Gaming Laptop
Intel® Wireless WiFi 5100AGN
(Included  Ubuntu Driver.  F/W is same version as on Intel site.  I've tried  compat wireless (did not install driver for some reason), and  backports-no improvement)
Ubuntu 10.10

Both machines have the proprietary NVIDIA Video card drivers. (Should not matter).

At  least on the Sony,  Wifi speeds are good for the first few seconds  after a networking restart, or a reboot.  For example if I go straight  to a typical Youtube video, about 1/8 to 1/4 of it will load ahead of  the play location, and then stop.  Once playback catches up, it will  pause continuously, as the rest is not loading near fast enough to stay  ahead.

No relevant system or kernel messages on the Sony unless it disconnects, I can post logs from the ASUS later in this thread.

Have  not tried ndiswrapper.  I was not successful in finding a trustworthy  source for the Windows Atheros drivers.  I do have them for the  ASUS/intel, and I'll try that when I get time.

I cannot compare w/ Windows on the same machines, as  I do not use  Windows.  Both machines were booted with a Ubuntu Disk the first time  they came out of the box.

Thanks, and I'll be whatever help I can be at solving this.

---

### Post by keymon on 2010-11-28
Hello. 

I solved the problem compiling lastest drivers from [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/). Actually I used [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-11-27.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-11-27.tar.bz2) (See readme to compile it). 

I am using kernel 2.6.32-25-generic (ubuntu) but I suppose newer kernels are ok.

---

### Post by uncaspi on 2010-11-28
sure you've don't been hacked?

---

### Post by pottzie on 2010-11-28
I have the same problem, and I have it using Fedora and Linux Mint as well. I'm trying to get another type of wireless card working right now, that's the reason I'm searching the forum.
 While it's not going to be much help, if you (or anyone) wants to rub more salt in the wound, download and boot a live cd from Vector Linux. You could probably use several others, but Vector is based on Slackware, and uses an ancient kernel. 2.1, or something. You'll have to fuss with wicd to get it to work, but even in the lived cd environment, it will still seem like it's running circles around what you probably have now.  
 I've wanted to complain too, but don't know where to start or what the cause is. I suspect recent kernels and maybe Network Manager. And if that's the case, I'm sure someone's working on it- feverishly, I hope.
 All I can say is it's not an Ubuntu problem per-se, but if it's not a bug then it's sure a drag for us who have to wait (in my case sometimes several minutes for the forum to load!)

---

