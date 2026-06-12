---
title: "Wireless problems with ASUS card"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by Mr. Picklesworth on 2006-04-11
I've been trying for some time now to get wireless working here with my ASUS WL-138G wireless card. In Windows on the same machine, it works fine (probably since I have the real driver...) with the same settings that I'm using in Ubuntu.
In Ubuntu, I've bumped into nothing but trouble.



So, the first thing I found was that there is a thing called ndiswrapper which solves problems with lazy wireless network card manufacturers not supporting Linux.
I properly installed ndiswrapper, and installed the driver for my wireless card without any error messages.

wlan0 appears in the Network Settings.
I noticed that as long as it is enabled, the light on the wireless card will flicker constantly for as long as Ubuntu is running.
I have configured it with a 128-bit WEP key, with static IP address 192.168.1.102. (etc.)

The settings are accepted, and Ubuntu says that the interface is active. (Yay!!)
I noticed at this point that keyboard input was behaving strangely. At random, single key presses would seemingly be registered as around 10... all instantly (no keyboard repeat speeds being taken into account here).

I came back to trying again today, and even 3 weeks later (and I have restarted the computer), it still behaves like this.


I set the default gateway device to wlan0.

Open up the terminal...

Pinging network IPs gives me "Unable to reach destination"... pinging my own wireless IP (192.168.1.102) works.

I go on with some other commands...

Wireless card definietly working:
```
dmccall@Dylan:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:A7:B9:02
                    ESSID:"McCall"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
... (my neighbour's network)
```

ifconfig is as follows... looks right:
```
wlan0     Link encap:Ethernet  HWaddr 00:15:F2:07:4E:BA
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe07:4eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:40100000-4010ffff
```

Looking at iwconfig, it appears that my settings have actually not been set.
```
dmccall@Dylan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:99/100  Signal level:-65 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:787  Invalid misc:696   Missed beacon:0
```

Setting manually through the terminal with iwconfig wlan0 essid "McCall" doesn't give me any error messages, but it still says ESSID:off/any when I type iwconfig.

I then go back into network settings, and try setting my WEP using Hex instead of ASCII.

...Now the keyboard stops working. This exact problem has been reported before.

Pinging 192.168.1.1 through Network Tools still doesn't work.

I go back into network settings (copying and pasting the password, letter by letter...), but even disabling wlan0 does not rescue keyboard input.


So... I have no Internet and no keyboard.
Any ideas?

Has anyone had these problems and solved them?
(Perhaps there is an alternative ndiswrapper for my card?)




Oh yes, and the computer has now frozen (old garbagey machine; probably not completely Ubuntu's fault), so I will have to turn off the computer. I hope that any questions about what's going on have already been adressed. (Sorry... I forgot to check route.).


Thanks in advance!





Edit:
Upon restarting, wlan0 has completely disappeared from my list of network devices and the keyboard works properly.
It doesn't usually disappear, though, so I wonder what has happened...

I will wait for a while before setting it up again.

---

### Post by spd106 on 2006-04-12
Have a look at supported cards on the ndiswrapper website for some clues.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A")

You may be better off compiling the latest version from source. The wiki has a useful [guide]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper").

---

### Post by Mr. Picklesworth on 2006-04-16
Thanks for the help. It worked until I completely killed my installation of Ubuntu in an over-zealous package downloading frenzy (foolishly done without checking drive space).

I have reinstalled Ubuntu with a nice, big partition. This also means, of course, that the wireless settings which were suddenly working as if by magic (thanks anyway!) are gone.

So, I followed a little tutorial that helped me last time ([here]("http://www.linuxresource.co.uk/index.php?module=tutorials&display=36")), and compiled the latest version that I could find from source. (By the way... what is going on with this thing's versioning? I keep seeing mention of versions 1.5 or 1.7, but their Sourceforge page goes up to 1.13-rc2!).
I compiled the latest stable version (1.13) successfully with make and make install, and it seemed to succeed.
The last time I got it working (on the old installation), however, didn't need the latest version... I just used the one from my local package repository. (Same as in packages.ubuntu.com).

Installed my driver... so far so good.
The command ndiswrapper -l tells me that my driver (mrv8k51 for WinXP from CD) is installed and hardware is present.

Typing dmesg, however, gives me something new.
```
dmccall@DylanUbuntu:~$ dmesg
ssid:58): setting essid failed (C0000001)
[4297725.318000] wlan0: no IPv6 routers present
[4297726.825000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297728.433000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297730.041000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297731.649000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297733.257000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297734.865000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297736.473000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297738.082000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297739.690000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297741.299000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297741.299000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297741.299000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297742.908000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297744.517000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297746.125000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297747.734000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297749.342000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297750.950000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
[4297752.265000] wlan0: no IPv6 routers present
[4297752.558000] ndiswrapper (set_essid:58): setting essid failed (C0000001)
...(Same error message repeated 183 times. Numbers on left incrementing as above -- I will give you all 209 lines if you want them)
```

Looks like it still knows wlan0 exists, though, because I can perform iwlist scan with wlan0. I set up iwconfig... so far, nothing totally wrong (except for those obviously very bad errors up above). Then I add my WEP key.
The keyboard problems are back... and this time in full force!

Same stuff as posted above in iwconfig and ifconfig... route gives me nothing.

I am going to take a guess here that my problems are (and were) happening due to ndiswrapper not knowing about my hardware's WEP compatibility and such, which is why it worked properly when I followed that tutorial.
Since I am not willing to take down WEP (I don't feel like arguing with the other nitwits on this network, even if it's replaced with MAC filtering), and I know that it SHOULD work, the best plan here is probably to find a solution.

Perhaps I am missing a package somewhere which I have previously?

---

### Post by spd106 on 2006-04-16
Can you upgrade to all of the latest breezy packages? There may have been some fixes that you need, particularly the kernel updates and related modules.

Also you could try the d-link driver referenced on the ndiswrapper website [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A")

---

### Post by Mr. Picklesworth on 2006-04-17
Yes, I have tried that driver, too.

I noticed suddenly that iwlist is warning me that ndiswrapper has been compiled with version 17 of Wireless Extension, instead of version 18.
I will look for something better there.

A bit of good news, though. The crazy 209 "setting essid failed" messages no longer happens. It has fixed itself, and dmesg tells me that my card is compatible with WEP, etc... I still get that essid error twice (everything else looks fine), and when trying to set an essid I get
```
dmccall@Dylan:~$ sudo iwconfig wlan0 essid "McCall"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
```

So it looks like that is my problem...




Edit:
Ah, of course! Their versioning isn't decimal numbers -- 1.13 is miles above 1.5. That stuff drives me crazy :/
I guess that means that the ndiswrapper version isn't at fault here. I'll see about going back to the one I had at the start.


Edit Again:
Ah, I read that Dapper, apparently, has support for my wireless card out of the box:
[http://ubuntuforums.org/showthread.php?t=144968&highlight=wl-138g](http://ubuntuforums.org/showthread.php?t=144968&highlight=wl-138g)
So I guess I can download the beta and see what happens...

---

### Post by Mr. Picklesworth on 2006-04-17
Sorry about the bump...

I'm noticing something a bit more interesting... then I realized that it was fixed by reverting to compiling ndiswrapper from source... then I gave up and installed Dapper... so this bump is totally unjustified.

---

