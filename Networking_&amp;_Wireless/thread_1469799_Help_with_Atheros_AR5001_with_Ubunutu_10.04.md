---
title: "Help with Atheros AR5001 with Ubunutu 10.04"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by dhblewis on 2010-05-02
I have a samsung N310 (GO) Notebook and installed Ubuntu on it. I used to have fedora but decided to move.

Everything is working perfectly except the wireless. I can connect to the network but it is very buggy & drops connections frequently.

Details from lspci

 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e00c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

---

### Post by GSF1200S on 2010-05-05
> **dhblewis said:**
> I have a samsung N310 (GO) Notebook and installed Ubuntu on it. I used to have fedora but decided to move.

Everything is working perfectly except the wireless. I can connect to the network but it is very buggy & drops connections frequently.

Details from lspci

 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e00c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

It appears you are not alone (assuming you are using 10.04). The following link has a patched kernel that has worked for some, but not for others- might want to take a look at the thread:

[http://ubuntuforums.org/showthread.php?t=1466201]("http://ubuntuforums.org/showthread.php?t=1466201")

---

### Post by Ian Ferguson on 2010-05-06
The patched kernel didn't work for me either, but installing Madwifi did. This thread tells you how. Though it was written for Karmic, it works for Lucid too.

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

:)

---

### Post by zuperman1 on 2010-05-12
This may help someone. I have Atheros AR5001 and I have managed to make my wifi work with the following commands:

sudo apt-get update
sudo modprobe acer-wmi

and it worked for a wile, but after I've updated the kernel, wifi stopped working. After some good hours of research I found that the problem is how the drivers are loaded. It has to be first acer-wmi and then ath5k.
So this are the commands that worked:

sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k

and I've put this in the /etc/rc.local so I don't have to put this commands every time I restart my computer.

---

### Post by Ian Ferguson on 2010-05-12
I may have spoken a bit too soon when I said that Madwifi worked. It's certainly an improvement on what I had before, but my wifi still has an annoying habit of losing the connection, and the only way I can get it back is to reboot.

I've tried Zuperman1's solution, but on entering the command
```
sudo modprobe acer-wmi
```
I get
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
```

---

### Post by lapor on 2010-05-23
I have similar problem. After putting my Toshiba to sleep... I cannot connect to wifi. It just tries to connect, but doesn't. After couple of sleep/waking up, it connects.

---

### Post by drpjkurian on 2010-05-26
Hi

Please install the following packages by synaptic package manager
They are linux-backports-modules-lucid-generic and linux-backports-modules-wireless-lucid-generic. to solve the random blackouts...

---

### Post by Ian Ferguson on 2010-05-27
> **drpjkurian said:**
> Hi

Please install the following packages by synaptic package manager
They are linux-backports-modules-lucid-generic and linux-backports-modules-wireless-lucid-generic. to solve the random blackouts...
I can't find "linux-backports-modules-lucid-generic" on Synaptic. Should this be "linux-backports-modules-headers-lucid-generic"?

---

### Post by drpjkurian on 2010-06-01
> **Ian Ferguson said:**
> I can't find "linux-backports-modules-lucid-generic" on Synaptic. Should this be "linux-backports-modules-headers-lucid-generic"?

Yep

---

### Post by khunphil on 2010-07-22
> **zuperman1 said:**
> 
This may help someone. I have Atheros AR5001 and I have managed to make my wifi work with the following commands:It has to be first acer-wmi and then ath5k.
So this are the commands that worked:

sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k


Thanks, after trying Madwifi without success, trying new kernel that will freeze my laptop, this is the most useful post I read.
For the moment, this works, and if the problem appears again, I will let a note on this forum.
I dont know how you find this, but if this is one of the reason why this card does not work good, the answer is so easy that I am surprised nobody saw it before.
Fingers crossed,
Thanks
Philippe

---

### Post by khunphil on 2010-07-23
... and 1 day after, include reboot, this still works ... not as fast as Ethernet but really good ... I've lost so many weeks looking for the right answer.
Philippe

---

### Post by enzostra on 2010-08-12
I'm glad to confirm that this sequence works very well!
Thank you!:D

---

### Post by alwaystun on 2010-08-15
I have Realtek version. I have tried windows wireless driver and it didnt work.
What do I need to change in this code to make it work?

> **zuperman1 said:**
> This may help someone. I have Atheros AR5001 and I have managed to make my wifi work with the following commands:

sudo apt-get update
sudo modprobe acer-wmi

and it worked for a wile, but after I've updated the kernel, wifi stopped working. After some good hours of research I found that the problem is how the drivers are loaded. It has to be first acer-wmi and then ath5k.
So this are the commands that worked:

sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k

and I've put this in the /etc/rc.local so I don't have to put this commands every time I restart my computer.

---

### Post by ZeroGravity2010cs on 2010-08-15
Hi, 

I installed ubuntu on my fujitsu siemens amilo li2727. And my wifi didnt work at all. So I looked through the net and finally I found this post. And it works :). So I tried to edit it on rc.local but got the respons that im not allowed bla bla bla, something about root. Anyone who can help??

---

### Post by ZeroGravity2010cs on 2010-08-15
:-\"  so all i needed to do was search it and I found it.

Thanks for the script.

---

### Post by LousticLou on 2010-08-20
Thank you, Zuperman1 !!!
I've spent days trying to enable Wifi on an Amilo 1718, without any success, and your simple lines of code have solved it in a minutes.
:D

---

### Post by danny.wilson on 2010-08-20
Hi,
I'm experiencing similar problems on my Mac Mini (Ubuntu Lucid), which uses an Atheros AR5001 wireless adapter. Concretely, the (hardware) wireless connection appears stable (it does not disconnect), but in irregular intervals (every couple minutes) it takes ages to establish new (HTTP / TCP) connections. The browser hangs while "looking up example.com", [FONT=Courier New]dig[/FONT] yields no results for DNS lookups. At the same time I can sometimes [FONT=Courier New]ping[/FONT] my router without packet loss, sometimes with a packet loss, but always in 1-2ms.

> **drpjkurian said:**
> Hi

Please install the following packages by synaptic package manager
They are linux-backports-modules-lucid-generic and linux-backports-modules-wireless-lucid-generic. to solve the random blackouts...

I installed these packages to no avail. What exactly is the problem that is solved by these? Is there hope that the issue will be solved in the near future?

Many thanks for any hints / pointers!

--
Linux mac-mini 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

---

### Post by sanskbn on 2010-10-19
Madwifi driver works for me in lucid and maverick. I followed that french tutorial:

[http://doc.ubuntu-fr.org/atheros_ar5007eg](http://doc.ubuntu-fr.org/atheros_ar5007eg)

What I did:

```

svn checkout [http://svn.madwifi-project.org/madwifi/branches/madwifi-dfs/](http://svn.madwifi-project.org/madwifi/branches/madwifi-dfs/)

cd madwifi-dfs
make 
sudo make install
sudo modprobe ath_pci

echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "ath_pci" | sudo tee -a /etc/modules

```

Restart the computer

---

### Post by bigfootnmd on 2010-10-20
I had the same exact problem with my Acer Aspire One A0751h in 10.04.  However, I switched to 10.10 NBR and the problem does not exist at all. This is because 10.10 has NATIVE Atheros drivers.
With 10.10 there is no need to install backports or the NDSWRAPPER and windows drivers.  

You can check this by downloading Ubuntu 10.10 NBR and making a startup USB.  Boot off of the USB and let 10.10 load.  You should be immediately told that Wireless networks are available and you can then select your WIFI connection and put in your key.

Under 10.10 with the included Atheros drivers I discovered that when using WPA shared pass key encryption that things work better with AES rather than TKIP.  Also, my signal strength (at least as far as Network manager is concerned) has increased from the average of 45% to 70%.  My Netbook connects every time. Lastly the WIFI inicator LED on my Netbook lights up and flashes like a Christmas tree light.

Please understand that I am providing this information as an alternative to the methods for 10.04 and in no way intend to demean the good Doctor or this solution under 10.04.

Good luck.

---

### Post by RainKap on 2010-10-21
Hmm, yes, but... I agree that with Ubuntu 10.10 wireless networking works "out of the box" on my Aspire One ZG5, *but* it's abysmally slow (and I don't go a bundle on the user interface, either). I rapidly decided to revert to 10.04 with Madwifi.

To the reason for my investigating this thread: my "big" laptop (a Clevo, also with Atheros AR5001) started to suffer from frequently dropped wireless connections after I'd updated to kernel 2.6.32-25 (and re-compiled Madwifi). Dr Kurian's solution of installing the backports modules seems to have fixed this problem. Thanks again Dr K!

Ian

---

### Post by RainKap on 2010-11-15
Back in the mire again :(

After making the mistake of accepting an update to kernel version 2.6.32-26 (which crashed part way through) on my "big" laptop, it became unbootable, so I rebuilt with Ubuntu 10.04, and spent ages last night trying to get wireless networking going again. Downloaded the latest stable version of Madwifi, adjusted the blacklist.conf and blacklist-ath_pci.conf and /etc/modules files as per the good doctor's recipe, installed the backports and still no joy. Wicd shows the wireless as attempting to authenticate, and eventually giving up with a bad password (which I *know* is false, 'cos it's worked with the exact same password!). I have to go to a meeting tonight (and use the laptop to take the minutes) but I think I might try Ubuntu 10.10...

Ian

---

### Post by sanskbn on 2010-11-15
> **RainKap said:**
> Back in the mire again :(

After making the mistake of accepting an update to kernel version 2.6.32-26 (which crashed part way through) on my "big" laptop, it became unbootable, so I rebuilt with Ubuntu 10.04, and spent ages last night trying to get wireless networking going again. Downloaded the latest stable version of Madwifi, adjusted the blacklist.conf and blacklist-ath_pci.conf and /etc/modules files as per the good doctor's recipe, installed the backports and still no joy. Wicd shows the wireless as attempting to authenticate, and eventually giving up with a bad password (which I *know* is false, 'cos it's worked with the exact same password!). I have to go to a meeting tonight (and use the laptop to take the minutes) but I think I might try Ubuntu 10.10...

Ian

Before reinstalling Ubuntu, I would give a try to the compat-wireless drivers. You can find the download file for your kernel version and the installing instructions here:

[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

---

### Post by fooljd on 2011-05-12
Sweet Thanks,
Used this without the 
sudo modprobe acer-wmi
it worked, have a toshiba satellite and am new to ubuntu.
Thanks

> **zuperman1 said:**
> This may help someone. I have Atheros AR5001 and I have managed to make my wifi work with the following commands:

sudo apt-get update
sudo modprobe acer-wmi

and it worked for a wile, but after I've updated the kernel, wifi stopped working. After some good hours of research I found that the problem is how the drivers are loaded. It has to be first acer-wmi and then ath5k.
So this are the commands that worked:

sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k

and I've put this in the /etc/rc.local so I don't have to put this commands every time I restart my computer.

---

