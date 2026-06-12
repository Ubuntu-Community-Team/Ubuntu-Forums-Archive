---
title: "ASUS N13 w/Slow Connect Speeds?"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by Akacheebe on 2013-05-07
OK so I've read over a few threads on this but have found nothing to resolve it.  This computer in question has both Windows XP x64 and Ubuntu 12.04.2 x64 on different hard drives along with an ASUS N13 USB wireless adapter.  On the Windows XP OS I get connect speeds of 144 MBPS but in Ubuntu 12.04.2 it only connects at 57 MBPS?  Kudos to the developers for getting Ubuntu to see the card and automatically configure it but it's way slow at file transfer so I need to get it's connect speed up to at least what Win XP will do.  The router is only good for 150 MBPS wireless so with Windows doing 144 KBPS I figured that was pretty good.  

Here is the output from lsmod that shows this wireless network adapter with an rt2800 chipset.  Most of the info I see on these states that most of these have a rt8169 chipset but few people seem to complain about actual throughput speeds??

```
parport_pc             32867  0 
rt2800usb              22903  0 
rt2800lib              59396  1 rt2800usb
crc_ccitt              12708  1 rt2800lib
rt2x00usb              20809  1 rt2800usb
rt2x00lib              55575  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              555272  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              208382  2 rt2x00lib,mac80211
parport                46563  3 parport_pc,ppdev,lp

```

So can someone tell me how to make this N13 adapter connect as fast in Ubuntu as it does in Windows XP?  Lightning has fried two 1GB wired network cards on this computer so I'd rather not buy another one as sooner or later it's going to fry more than just the network card.  

Thanks

---

### Post by praseodym on 2013-05-07
Please show also:
```

lsusb
dmesg | grp rt2
iwconfig
sudo iwlist scan
```

---

### Post by Akacheebe on 2013-05-08
> **praseodym said:**
> Please show also:
```

lsusb
dmesg | grp rt2
iwconfig
sudo iwlist scan
```

Thanks for your reply.  Here is that info in the order you wrote in your post.

```
Bus 002 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]
Bus 006 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


The Second one seems to be a bad command?

```
dmesg | grp rt2
No command 'grp' found, did you mean:
 Command 'igrp' from package 'irpas' (multiverse)
 Command 'gp' from package 'pari-gp' (universe)
 Command 'grpn' from package 'grpn' (universe)
 Command 'grap' from package 'grap' (universe)
 Command 'gri' from package 'gri' (universe)
 Command 'arp' from package 'net-tools' (main)
 Command 'gip' from package 'gip' (universe)
 Command 'gpp' from package 'gpp' (universe)
 Command 'gpr' from package 'gpr' (universe)
 Command 'gap' from package 'gap-core' (universe)
 Command 'gyp' from package 'gyp' (universe)
 Command 'gcp' from package 'gcp' (universe)
 Command 'grc' from package 'grc' (universe)
 Command 'grn' from package 'groff' (main)
 Command 'grep' from package 'grep' (main)
grp: command not found
```


```
eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:30:44:06:FF:EF   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0
```


```
eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:44:06:FF:EF
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000118e97eae0
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00074D42522D353764
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C101EFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160900030000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340900070000000F000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010696E9C11F1C53C8D8A5707EF7938645E1021000B437261646C65506F696E74102300084D42522D31303030102400024131104200046E6F6E651054000800060050F20400011011000B4D42522047617465776179100800020004

```

---

### Post by praseodym on 2013-05-08
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

---

### Post by Akacheebe on 2013-05-08
> **praseodym said:**
> Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

OK tried this but it's still running about half the speed of Windows XP?  I moved a 775MB movie file from my desktop to my Wife's new Dell Laptop across the wireless Draft N router and it took just over 5 minutes using Windows.  Using Ubuntu it took over 9 minutes?  Any other suggestions?

Thanks,

---

### Post by praseodym on 2013-05-09
Check:
```

dmesg | grep rt2
ifconfig -a
cat /etc/reolv.conf
route -n
```

---

### Post by Akacheebe on 2013-05-10
> **praseodym said:**
> Check:
```

dmesg | grep rt2
ifconfig -a
cat /etc/reolv.conf
route -n
```

Sorry to take so long to reply.  We had a day without rain yesterday and I had a mile long "honey do list"!  

Here's that info you requested.

Oh, and thanks for your help!!

```
mesg | grep rt2
[   21.365681] Registered led device: rt2800usb-phy0::radio
[   21.365725] Registered led device: rt2800usb-phy0::assoc
[   21.365769] Registered led device: rt2800usb-phy0::quality
[   21.365819] usbcore: registered new interface driver rt2800usb

```

```
ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1d:0f:21:1e:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140158 (140.1 KB)  TX bytes:140158 (140.1 KB)

wlan0     Link encap:Ethernet  HWaddr 20:cf:30:a2:02:6b  
          inet addr:192.168.0.190  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fea2:26b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17189698 (17.1 MB)  TX bytes:1082819 (1.0 MB)

```

```
cat /etc/reolv.conf
cat: /etc/reolv.conf: No such file or directory


```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

---

### Post by praseodym on 2013-05-10
Sorry, typo:

cat /etc/re**s**olv.conf

---

### Post by Akacheebe on 2013-05-10
```
cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search workgroup
```

---

### Post by meldroc on 2013-05-10
I've been having problems, using a USB-N13 as well. As far as I can tell, there is a kernel bug in kernel 3.8. The only way I can get the damned thing to work at all is to downgrade to an old kernel - works fine in kernel 3.5.

Is there any news on a fix to this bug yet? There are several threads lurking about complaining about this specific brand of wifi adaptor. The problem is that the kernel driver is broken. How long before an Ubuntu or Linux kernel developer pushes a fix to the repos?

---

### Post by praseodym on 2013-05-11
You can also try the mainline kernel 3.9

---

### Post by Akacheebe on 2013-05-11
> **meldroc said:**
> I've been having problems, using a USB-N13 as well. As far as I can tell, there is a kernel bug in kernel 3.8. The only way I can get the damned thing to work at all is to downgrade to an old kernel - works fine in kernel 3.5.

Is there any news on a fix to this bug yet? There are several threads lurking about complaining about this specific brand of wifi adaptor. The problem is that the kernel driver is broken. How long before an Ubuntu or Linux kernel developer pushes a fix to the repos?

Well, I'm using kernel v3.5.0-28 now and it does work, just at half the speed of what Windows does on the exact same hardware?  This was a clean install done about two weeks ago from the v12.04.2 install DVD and one kernel update was done since then to bring it up to -28.

> You can also try the mainline kernel 3.9   

That's probably not going to happen unless it comes with a regular update!  Reason:  THAT is the reason I had to do the clean install a couple of weeks ago, ie, tried to upgrade from kernel 3.2 to 3.5 and wound up trashing it and had to do a clean install.  Since I'm on metered internet service, (bytes are not unlimited to some of us) there won't be any more clean installs with 500MB of updates/upgrades to download until next month!

And on a positive note, when my wired PCI network card got fried a few days ago I plugged this N13 card in and it worked right away.  It's just slow as a snail is all.  If I can get the speed up to what Windows XP x64 runs it at then I'd be a happy camper!

---

### Post by Akacheebe on 2013-05-13
Ok so are we done here?  Nothing that can be done to fix this problem??:confused:

---

### Post by praseodym on 2013-05-14
Why not trying 3.9? It runs here without problems on 12.04

---

### Post by Akacheebe on 2013-05-14
> **praseodym said:**
> Why not trying 3.9? It runs here without problems on 12.04

So is that the only answer?Meldroc up the page stated he had used his N13 with v3.5 with no problems although I don't know if he actually checked the file transfer speeds to see how they compared to Windows.  If my system wasn't dual boot then I'd likely not know the difference either.  Mine works and is OK for just surfing the web but file transfers are really slow.  

As I mentioned above, I tried to update the kernel from 3.2 to 3.5 on this old hardware and wound up with no video and I couldn't figure out how to get it back.  That was the reason I had to do that recent clean install using v12.04.2.  

I'm also on metered service, ie, USB mobile broadband card that runs off of the local cell tower.  If I run out of bandwidth then it's going to cost me another $40 to make it through the month.  The Wife and I use that same service through a draft N mobile broadband router so it's stretched to the limit most of the time anyway.  If I wind up having to do another clean install because of a failed kernel update then I know those Ubuntu updates will run me out of bandwidth.  FYI, the only other service that's available to me is dialup and I sure don't want to go there again!

So if the kernel update is all that's left to try then I'm done and I'll just have to live with the slow speed.

Thanks

---

### Post by varunendra on 2013-05-15
> **Akacheebe said:**
> So if the kernel update is all that's left to try then I'm done and I'll just have to live with the slow speed.

Can't guarantee if it'll improve the speed or not, but you can try installing the proprietary driver from Ralink if you wish. It's only about 700KB download.

[LIST=1]
[*]Dowonload the driver from here : [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5016](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5016) (use any random name/email to access the download if you don't like to share that info)
[*]Copy it to your desktop and rename it to add ".tar" before ".bz2" in the last. (2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO**.tar**.bz2).
[*]Right-click > "Extract here". This will extract the driver source files to a folder named "2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO"
[*]Go to os/linux folder within the extracted directory and open "config.mk" file.
[*]Edit lines numbers 56 and 60 ("HAS_WPA_SUPPLICANT=**n**" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**n**") and change their value from "n" to "y" ("HAS_WPA_SUPPLICANT=**y**" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y**"). Proofread, save and close the file.
[*]Open a terminal and do the following :
[/LIST]
(hint : just type a few initial characters then press 'Tab' key to auto-complete the rest of the names)
```
cd ~/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
sudo su
modprobe -rfv rt2800usb
[s]cd ~/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO[/s] [COLOR="#FF0000"]# Sorry! Wrong place for the command, thanks to [Expe]("http://ubuntuforums.org/showthread.php?t=2143041&p=12656927#post12656927") for heads up![/COLOR]
make
make install
echo "blacklist rt2800usb" | tee -a /etc/modprobe.d/blacklist.conf
exit
```
Reboot if required.
[INDENT]Notes:
The second command (modprobe -rfv...) will disable your usb wireless, don't worry about that.
The second last command will 'blacklist' the current native driver to make sure it does not get loaded again and there is no conflict. On next reboot, the sta driver should be automatically loaded.[/INDENT]

Watch out for errors while this is being done. Exactly 'one' error during 'make' (regarding tftpboot) is normal and can be safely ignored. Post back if there are more.

---

### Post by Akacheebe on 2013-05-15
[**[COLOR=#DD4814][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")varunendra thanks for your reply as I was thinking that I was done.  Real life will have me busy these next couple of days but I will try this over the weekend.  

Thanks again!!

---

### Post by Akacheebe on 2013-05-20
Finally got around to installing this driver and it seems to be much faster now than before.  I did have a system lockup though so the jury is out as to whether this new driver cause it or not.  Will monitor it over the next few days to see if it keeps happening.  

Oh, and one line of your code was wrong.  Took me about 30 minutes to figure that out but I did get it done in the end.  That error is in line 3 where you show a cd then have `/ in there and it turns out they aren't needed.  I dropped those two characters then it did cd fine.  Yeah I know, I'm slow as I'm not a command line person at all!!  You have to understand that I was brought up on Windows and their GUI.  

Ennywho, thanks for your help and I'll go ahead and mark this solved.  If I have problems with more system lockups then I may revisit it again to maybe go back to the old driver.

---

### Post by varunendra on 2013-05-20
I'm very pleased you made it, and that it is delivering better speeds. I don't think it might cause any trouble about system freezes, but things that I didn't know or experienced keep coming everyday :).

And..
> **Akacheebe said:**
> Oh, and one line of your code was wrong.  Took me about 30 minutes to figure that out but I did get it done in the end.  That error is in line 3 where you show a cd then have `/ in there and it turns out they aren't needed.  I dropped those two characters then it did cd fine.
No, it wasn't a mistake. I intentionally put it there. It makes 'Extra sure' that the user gets 'Into' the Desktop before executing the rest of the commands. The "~/" part, while executing, gets replaced by the user's 'Home' path.

In case your current working directory in terminal is not your 'Home' directory (say, for example, you accidentally or while doing something else switched to a different one) you will get an error if directly starting the path with "Desktop/....". But if there is a "~/" in the beginning, it is treated as a full path (/home/<user>/), thus never failing :)

If you got an error due to that, most probably you were typing a wrong character (as apparent in your post). The "~" key is on the same key as backquote ("`", above "tab", before "1" on my US-104 type keyboard), but is typed with "Shift" key.

Anyway, if you happen to face any problems with the driver again, please let us know. It'll be a good idea to post back, along with a description of the problem, a full diagnostics report that you can generate with "Wireless Script" following its link in my signature :)

---

### Post by Akacheebe on 2013-05-20
Well, I copied and pasted everything from your post into terminal so it it was wrong, then it was written that way to begin with.  When I tried to cd to the desktop it kept giving me a "not found" error, or something to that effect??  When I removed the ~/ it finally did go ahead and I could "make".

Anyway, this thing has locked up 4 times since I marked this problem solved so I'm going to have to go back to that other driver.  

So would you please give me what I need for terminal commands so I can activate the old driver and blacklist or remove this new one?

Thanks

---

### Post by varunendra on 2013-05-20
> **Akacheebe said:**
> Well, I copied and pasted everything from your post into terminal so it it was wrong, then it was written that way to begin with.
Hmm.. it must have got substituted during the copy-paste for some reason (as evident in your post - it is "`" instead of "~").


> Anyway, this thing has locked up 4 times since I marked this problem solved so I'm going to have to go back to that other driver.  

So would you please give me what I need for terminal commands so I can activate the old driver and blacklist or remove this new one?
The recommended way is to just run-
```
sudo make uninstall
```
from within the same directory where you ran 'make' and 'make install'.

If you deleted it, you can simple re-extract it and run the 'make uninstall' command there. Reboot and check -
```
lspci -nnk | grep -iA2 net
```
The last line should show your native driver loaded. If not, we can manually do it all.

But I strongly recommend you run the diagnostics first and post back the report so we can see if there is something obvious that can be easily fixed. This driver is usually not problematic and runs smooth.

---

### Post by Akacheebe on 2013-05-20
oops

---

### Post by Akacheebe on 2013-05-20
> **varunendra said:**
> Hmm.. it must have got substituted during the copy-paste for some reason (as evident in your post - it is "`" instead of "~").

But I strongly recommend you run the diagnostics first and post back the report so we can see if there is something obvious that can be easily fixed. This driver is usually not problematic and runs smooth.

The ` instead of ~ was simply a type "O" in my post.  The copy and paste went in exactly as it was written from your post?

So what diagnostics do you want run?

---

### Post by Akacheebe on 2013-05-20
[SIZE=3][FONT=times new roman]Just had a hard crash, ie, in Windows we'd call it a BSOD.  Last line error message from the text on the screen was (Kernel Panic - not syncing: Fatal Exception interrupt)?

EDIT:  [SIZE=5]Never mind as I'm done now.[/SIZE]  

I uninstalled that new driver and then figured out how to remove the default driver from the blacklist.  Hopefully the system crashes will stop now!

Note to anyone reading this thread and wanting to get this N13 USB LAN adapter up to speed??  Forget it!!  It's not worth the trouble.  


[/FONT][/SIZE]

---

### Post by varunendra on 2013-05-20
> **Akacheebe said:**
> The ` instead of ~ was simply a type "O" in my post.  The copy and paste went in exactly as it was written from your post?
Not sure what is going on here, may be a keyboard layout or regional language settings difference, but it never happened before with anyone I was assisting.

If you are copy-pasting from a different machine or different OS on the same machine (like maybe from windows to Ubuntu), it is recommended to use the most basic text editor to store the copied text. Sometimes the 'Over smartness' of advance programs like ms-office or libre-office creates a mess.

I haven't changed the code in my original post, and a copy-paste from it is just fine here :)


> So what diagnostics do you want run?
Follow the instructions in this post : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Apart from the diagnostics report it creates ("netinfo.txt" file), you may also find some hints about the crash in syslog.1 and dmesg.0 files in /var/log/ directory immediately after a crash. These files contain important messages from the previous session (if the current session has just started fresh).

---

### Post by Expe on 2013-05-21
I also tried the drivers but had issues with soft and hard locking. Thanks for trying to help though, varunendra. Have attached netinfo.

I did notice it seemed to be trying to use the rt5370sta driver, is this correct?

```

$lsmod | grep rt
rt5370sta             801414  1 
parport_pc             28152  1 
parport                46345  3 lp,ppdev,parport_pc

```

Some other messages:
```

[    5.690479] /home/expe/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[    5.691104] /home/expe/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[    6.261865] 6:1:1: cannot get freq at ep 0x1
[    6.264817] 6:1:1: cannot get freq at ep 0x1
[    6.287669] 6:1:1: cannot get freq at ep 0x1
[    6.290328] 6:1:1: cannot get freq at ep 0x1
[    6.309276] 6:1:1: cannot get freq at ep 0x1
[    6.311897] 6:1:1: cannot get freq at ep 0x1

[   76.141726] INFO: rcu_sched self-detected stall on CPU { 2}  (t=15000 jiffies g=2124 c=2123 q=72503)
[   76.141730] sending NMI to all CPUs:
[   76.141733] NMI backtrace for cpu 2
[   76.141733] CPU 2 
[   76.141736] Pid: 1262, comm: whoopsie Tainted: PF          O 3.8.0-19-generic #30-Ubuntu System manufacturer System Product Name/P8P67-M PRO
[   76.141737] RIP: 0010:[<ffffffff813531b2>]  [<ffffffff813531b2>] __const_udelay+0x12/0x30
[   76.141741] RSP: 0018:ffff8802118899c0  EFLAGS: 00000046
[   76.141742] RAX: 0000000001062560 RBX: 0000000000002710 RCX: 0000000000000004
[   76.141743] RDX: 0000000000ca13d8 RSI: 0000000000000100 RDI: 0000000000418958
[   76.141744] RBP: ffff8802118899d8 R08: 000000000000000a R09: 0000000000000000
[   76.141745] R10: 0000000000000501 R11: 0000000000000002 R12: ffffffff81ce74a0
[   76.141746] R13: ffff88021ed0ee60 R14: ffffffff81c3f6c0 R15: 0000000000011b37
[   76.141747] FS:  00007fa94ad1e800(0000) GS:ffff88021ed00000(0000) knlGS:0000000000000000
[   76.141749] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   76.141749] CR2: 0000000000fb8000 CR3: 00000002123ff000 CR4: 00000000000407e0
[   76.141758] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   76.141759] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   76.141760] Process whoopsie (pid: 1262, threadinfo ffff880211888000, task ffff8802118545c0)
[   76.141760] Stack:
[   76.141761]  ffff8802118899d8 ffffffff81039c0a ffffffff81c3f6c0 ffff880211889a38
[   76.141763]  ffffffff810f237d ffff8802118545c0 ffff88020ff8dd80 ffff880211889a30
[   76.141765]  0000000000000002 ffff880211888000 ffff8802118545c0 0000000000000002
[   76.141767] Call Trace:
[   76.141771]  [<ffffffff81039c0a>] ? arch_trigger_all_cpu_backtrace+0x6a/0x90
[   76.141773]  [<ffffffff810f237d>] rcu_pending+0x2cd/0x5b0
[   76.141775]  [<ffffffff810f46ab>] rcu_check_callbacks+0x9b/0x120
[   76.141778]  [<ffffffff8106a7a8>] update_process_times+0x48/0x90
[   76.141781]  [<ffffffff810b379e>] tick_sched_handle.isra.8+0x2e/0x70
[   76.141782]  [<ffffffff810b392c>] tick_sched_timer+0x4c/0x80
[   76.141785]  [<ffffffff81081729>] __run_hrtimer+0x79/0x1c0
[   76.141786]  [<ffffffff810b38e0>] ? tick_sched_do_timer+0x40/0x40
[   76.141788]  [<ffffffff81082027>] hrtimer_interrupt+0xe7/0x220
[   76.141791]  [<ffffffff816d55d9>] smp_apic_timer_interrupt+0x69/0x99
[   76.141793]  [<ffffffff816d451d>] apic_timer_interrupt+0x6d/0x80
[   76.141796]  [<ffffffff81044ab5>] ? __ticket_spin_lock+0x25/0x30
[   76.141799]  [<ffffffff816cb1aa>] _raw_spin_lock_bh+0x1a/0x20
[   76.141802]  [<ffffffff815b629a>] lock_sock_nested+0x2a/0x60
[   76.141804]  [<ffffffff8160b6a2>] tcp_recvmsg+0x32/0xce0
[   76.141818]  [<ffffffffa0784a92>] ? RTUSBBulkOutDataPacketComplete+0x52/0x120 [rt5370sta]
[   76.141821]  [<ffffffff81044b49>] ? default_spin_lock_flags+0x9/0x10
[   76.141823]  [<ffffffff816326eb>] inet_recvmsg+0x6b/0x80
[   76.141825]  [<ffffffff815b0a86>] sock_aio_read.part.7+0x126/0x140
[   76.141832]  [<ffffffffa07851b8>] ? RTUSBBulkOutDataPacket+0x378/0x8b0 [rt5370sta]
[   76.141834]  [<ffffffff815b0ac9>] sock_aio_read+0x29/0x40
[   76.141836]  [<ffffffff81193b17>] do_sync_read+0xa7/0xe0
[   76.141838]  [<ffffffff8119434d>] vfs_read+0x15d/0x180
[   76.141840]  [<ffffffff811943c2>] sys_read+0x52/0xa0
[   76.141842]  [<ffffffff816d37dd>] system_call_fastpath+0x1a/0x1f
[   76.141843] Code: 89 e5 ff 15 69 3b 92 00 5d c3 66 66 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 8d 04 bd 00 00 00 00 65 48 8b 14 25 98 3e 01 00 <48> 8d 0c 12 48 c1 e2 06 48 89 e5 48 29 ca f7 e2 48 8d 7a 01 ff 
[   76.141862] NMI backtrace for cpu 3
[   76.141864] CPU 3 
[   76.141867] Pid: 0, comm: swapper/3 Tainted: PF          O 3.8.0-19-generic #30-Ubuntu System manufacturer System Product Name/P8P67-M PRO
[   76.141868] RIP: 0010:[<ffffffff8108cbc0>]  [<ffffffff8108cbc0>] sched_feat_write+0xb0/0xb0
[   76.141871] RSP: 0018:ffff88021ed83df8  EFLAGS: 00000046
[   76.141872] RAX: 00000000224c224c RBX: ffff88021316dd00 RCX: 000000000000224c
[   76.141873] RDX: 000000000000224c RSI: ffff88021316dd00 RDI: ffff88021ed93f40
[   76.141874] RBP: ffff88021ed83e48 R08: 0000000000000000 R09: 0000000000000000
[   76.141875] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000003
[   76.141876] R13: ffff88021316e314 R14: 0000000000000004 R15: ffff88021ed93f40
[   76.141877] FS:  0000000000000000(0000) GS:ffff88021ed80000(0000) knlGS:0000000000000000
[   76.141878] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   76.141879] CR2: 00007fd84d408000 CR3: 00000001ea60d000 CR4: 00000000000407e0
[   76.141880] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   76.141881] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   76.141882] Process swapper/3 (pid: 0, threadinfo ffff880213182000, task ffff88021317c5c0)
[   76.141883] Stack:
[   76.141884]  ffffffff8108f148 ffff88021ed83e10 ffff88021ed83e30 000000018134f974
[   76.141886]  0000000000000082 ffff880213173e78 ffffffff81c403e8 ffffffff81c403d0
[   76.141888]  0000000000000000 0000000000000003 ffff88021ed83e58 ffffffff8108f242
[   76.141890] Call Trace:
[   76.141891]  <IRQ> 
[   76.141891]  [<ffffffff8108f148>] ? try_to_wake_up+0x1b8/0x2a0
[   76.141896]  [<ffffffff8108f242>] default_wake_function+0x12/0x20
[   76.141898]  [<ffffffff8107dc52>] autoremove_wake_function+0x12/0x40
[   76.141899]  [<ffffffff81086655>] __wake_up_common+0x55/0x90
[   76.141901]  [<ffffffff81089eb8>] __wake_up+0x48/0x70
[   76.141904]  [<ffffffff81572bc0>] ? centrino_target+0x370/0x370
[   76.141906]  [<ffffffff810f19f8>] force_quiescent_state+0xe8/0x130
[   76.141907]  [<ffffffff810f297b>] rcu_eqs_enter_common.isra.48+0x31b/0x530
[   76.141909]  [<ffffffff810f3d2d>] rcu_irq_exit+0x6d/0xa0
[   76.141912]  [<ffffffff81061173>] irq_exit+0x73/0xb0
[   76.141914]  [<ffffffff816d55de>] smp_apic_timer_interrupt+0x6e/0x99
[   76.141915]  [<ffffffff816d451d>] apic_timer_interrupt+0x6d/0x80
[   76.141916]  <EOI> 
[   76.141917]  [<ffffffff81573608>] ? cpuidle_wrap_enter+0x58/0xa0
[   76.141920]  [<ffffffff81573660>] cpuidle_enter_tk+0x10/0x20
[   76.141921]  [<ffffffff81573255>] cpuidle_idle_call+0xa5/0x260
[   76.141924]  [<ffffffff8101d5af>] cpu_idle+0xaf/0x120
[   76.141927]  [<ffffffff816b4e5e>] start_secondary+0x1e0/0x1e5
[   76.141928] Code: 33 14 25 28 00 00 00 75 17 48 8b 5d e8 4c 8b 65 f0 4c 8b 6d f8 c9 c3 48 c7 c2 ea ff ff ff eb d7 e8 36 ba fc ff 66 0f 1f 44 00 00 <66> 66 66 66 90 55 48 89 e5 48 83 ec 10 48 89 5d f0 4c 89 65 f8 
[   76.141947] NMI backtrace for cpu 0
[   76.141949] CPU 0 
[   76.141951] Pid: 0, comm: swapper/0 Tainted: PF          O 3.8.0-19-generic #30-Ubuntu System manufacturer System Product Name/P8P67-M PRO
[   76.141952] RIP: 0010:[<ffffffff8108071c>]  [<ffffffff8108071c>] run_posix_cpu_timers+0xac/0x780
[   76.141955] RSP: 0018:ffff88021ec03df8  EFLAGS: 00000046
[   76.141957] RAX: 0000000000000000 RBX: ffffffff81c15440 RCX: ffffffff81c15440
[   76.141957] RDX: ffff88021ec13f40 RSI: 0000000000000000 RDI: ffffffff81c15440
[   76.141958] RBP: ffff88021ec03e78 R08: 0000000000000000 R09: 0000000000000000
[   76.141959] R10: 0000000000000005 R11: 0000000000000004 R12: ffff88021ec03e28
[   76.141960] R13: 0000000000000000 R14: ffff88021ec0e800 R15: 00000011be96ec3f
[   76.141961] FS:  0000000000000000(0000) GS:ffff88021ec00000(0000) knlGS:0000000000000000
[   76.141962] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   76.141963] CR2: 00007fd84d3f0000 CR3: 000000000ec0d000 CR4: 00000000000407f0
[   76.141964] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   76.141965] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   76.141967] Process swapper/0 (pid: 0, threadinfo ffffffff81c00000, task ffffffff81c15440)
[   76.141967] Stack:
[   76.141968]  0000000000000086 0000000000000000 ffff88021ec03e40 ffffffff81099add
[   76.141970]  ffff88021ec13f40 0000000000000000 ffff88021ec03e28 ffff88021ec03e28
[   76.141972]  ffffffff81c15440 ffff88021ec03e78 ffffffff8108de3e ffffffff81c15440
[   76.141974] Call Trace:
[   76.141974]  <IRQ> 
[   76.141975]  [<ffffffff81099add>] ? trigger_load_balance+0x5d/0x210
[   76.141980]  [<ffffffff8108de3e>] ? scheduler_tick+0x10e/0x140
[   76.141982]  [<ffffffff8106a7d4>] update_process_times+0x74/0x90
[   76.141984]  [<ffffffff810b379e>] tick_sched_handle.isra.8+0x2e/0x70
[   76.141985]  [<ffffffff810b392c>] tick_sched_timer+0x4c/0x80
[   76.141987]  [<ffffffff81081729>] __run_hrtimer+0x79/0x1c0
[   76.141989]  [<ffffffff810b38e0>] ? tick_sched_do_timer+0x40/0x40
[   76.141990]  [<ffffffff81082027>] hrtimer_interrupt+0xe7/0x220
[   76.141992]  [<ffffffff81572bc0>] ? centrino_target+0x370/0x370
[   76.141994]  [<ffffffff816d55d9>] smp_apic_timer_interrupt+0x69/0x99
[   76.141996]  [<ffffffff816d451d>] apic_timer_interrupt+0x6d/0x80
[   76.141996]  <EOI> 
[   76.141997]  [<ffffffff810f279d>] ? rcu_eqs_enter_common.isra.48+0x13d/0x530
[   76.142000]  [<ffffffff81573608>] ? cpuidle_wrap_enter+0x58/0xa0
[   76.142002]  [<ffffffff81573660>] cpuidle_enter_tk+0x10/0x20
[   76.142004]  [<ffffffff81573255>] cpuidle_idle_call+0xa5/0x260
[   76.142006]  [<ffffffff8101d5af>] cpu_idle+0xaf/0x120
[   76.142008]  [<ffffffff816a94d2>] rest_init+0x72/0x80
[   76.142011]  [<ffffffff81d06be9>] start_kernel+0x3d1/0x3dc
[   76.142012]  [<ffffffff81d0666e>] ? do_early_param+0x8e/0x8e
[   76.142014]  [<ffffffff81d06355>] x86_64_start_reservations+0x130/0x133
[   76.142015]  [<ffffffff81d06458>] x86_64_start_kernel+0x100/0x10f
[   76.142016] Code: 00 41 8b 85 30 01 00 00 85 c0 0f 85 17 03 00 00 48 83 c4 58 5b 41 5c 41 5d 41 5e 41 5f 5d c3 48 8b 87 30 04 00 00 48 85 c0 75 0a <48> 83 bf 38 04 00 00 00 74 c5 48 8b 93 b0 03 00 00 48 8b 8b b8 
[   76.142035] NMI backtrace for cpu 1
[   76.142037] CPU 1 
[   76.142039] Pid: 0, comm: swapper/1 Tainted: PF          O 3.8.0-19-generic #30-Ubuntu System manufacturer System Product Name/P8P67-M PRO
[   76.142041] RIP: 0010:[<ffffffff813b7b08>]  [<ffffffff813b7b08>] intel_idle+0xa8/0x100
[   76.142045] RSP: 0018:ffff880213177e18  EFLAGS: 00000046
[   76.142046] RAX: 0000000000000020 RBX: 0000000000000008 RCX: 0000000000000001
[   76.142047] RDX: 0000000000000000 RSI: ffff880213177fd8 RDI: 000000000ec0d000
[   76.142048] RBP: ffff880213177e40 R08: 0000000000000068 R09: 00000000000020ce
[   76.142048] R10: 0000000000000000 R11: 0000000000000e19 R12: 0000000000000003
[   76.142049] R13: 0000000000000020 R14: 0000000000000003 R15: ffffffff81572bc0
[   76.142051] FS:  0000000000000000(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
[   76.142052] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   76.142053] CR2: 0000000000bb1040 CR3: 000000000ec0d000 CR4: 00000000000407e0
[   76.142054] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   76.142055] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   76.142056] Process swapper/1 (pid: 0, threadinfo ffff880213176000, task ffff880213179740)
[   76.142056] Stack:
[   76.142064]  0000000113177e28 ffff88021ec9a470 ffffffff81c7a960 00000011be90c718
[   76.142066]  0000000000000003 ffff880213177e50 ffffffff81572bd9 ffff880213177eb0
[   76.142068]  ffffffff815735f9 7735940000000001 00000000000113e0 0000000000000000
[   76.142070] Call Trace:
[   76.142072]  [<ffffffff81572bd9>] cpuidle_enter+0x19/0x20
[   76.142074]  [<ffffffff815735f9>] cpuidle_wrap_enter+0x49/0xa0
[   76.142076]  [<ffffffff81573660>] cpuidle_enter_tk+0x10/0x20
[   76.142085]  [<ffffffff81573255>] cpuidle_idle_call+0xa5/0x260
[   76.142086]  [<ffffffff8101d5af>] cpu_idle+0xaf/0x120
[   76.142089]  [<ffffffff816b4e5e>] start_secondary+0x1e0/0x1e5
[   76.142089] Code: 28 e0 ff ff 83 e2 08 75 22 31 d2 48 83 c0 10 48 89 d1 0f 01 c8 0f ae f0 48 8b 86 38 e0 ff ff a8 08 75 08 b1 01 4c 89 e8 0f 01 c9 <85> 1d 32 31 8c 00 75 0e 48 8d 75 dc bf 05 00 00 00 e8 f2 a1 cf



```

```
sudo su
cd ~/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
```
I think that's trying to go to the root desktop. So it should be:

```
cd /home/<user>/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
```

---

### Post by varunendra on 2013-05-21
> **Expe said:**
> ```
**[COLOR="#FF0000"]sudo su[/COLOR]**
cd **[COLOR="#FF0000"]~/[/COLOR]**Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
```
I think that's trying to go to the root desktop.
Oh my..! That was a huge mistake on my part!! Thanks for the heads up!
Obviously, the user becomes "root" after sudo su. So "~/" becomes the home of "root", not that of the logged in user.

So yes, either add the full path like you suggested, or just remove the "~/" part like Akacheebe did. Or just "cd.." BEFORE doing "sudo su" - the correction I made to my original post.

I owe a big sorry to Akacheebe, for arguing about the validity of the command when the actual error was on my part :(


As for -
> **Expe said:**
> I did notice it seemed to be trying to use the rt5370sta driver, is this correct?
Yes that is correct. Ralink drivers have this weird nature of showing multiple names in different outputs (ra0, RT2870STA, RALINK,....) while the actual module name being completely different (rt5370sta in your case) :)

The netinfo.txt file you uploaded seems okay to me. Was the locking you mentioned just the wireless switch or a total system freeze like Akacheebe was experiencing?

I found the other thread you posted in : [http://ubuntuforums.org/showthread.php?t=2139032&p=12624596#post12624596](http://ubuntuforums.org/showthread.php?t=2139032&p=12624596#post12624596)
Did you try the newer kernel like mentioned in the bug report page?

---

### Post by Expe on 2013-05-22
The lockups were sometimes a CPU core getting stuck at 100% load, wifi would be unresponsive but I could still use commands in terminal. Other times it would lock up completely.

I did try the 3.9 kernel. Instead of failing to connect all of the time, it would sometimes connect. The connection was very unstable when it did connect.

---

