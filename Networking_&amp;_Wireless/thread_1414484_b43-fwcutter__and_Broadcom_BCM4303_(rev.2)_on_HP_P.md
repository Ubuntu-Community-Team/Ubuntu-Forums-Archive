---
title: "b43-fwcutter  and Broadcom BCM4303 (rev.2) on HP Pavilion ZV5000"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by maycom on 2010-02-23
Can't get my WiFi to work on my HP.
My WiFi chip is bcm4303 (rev. 2)
(PS! this is a new thread from [http://ubuntuforums.org/showthread.php?t=1400427&page=4](http://ubuntuforums.org/showthread.php?t=1400427&page=4) )

So, I reinstalled Ubuntu (fresh install)

Activated the Broadcom b43leagacy Wireless driver.

When rebooting, the WiFi LED on the On/Off switch blinks.

Status right now:
```

**~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:06:1d:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.9.50.199  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5877866 (5.8 MB)  TX bytes:364464 (364.4 KB)


**~$ rfkill list**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

**~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


[B]
~$ cat /etc/modules[/B]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


**~$ lsmod | grep b4**
b43legacy             117752  0 
mac80211              181236  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
b44                    28684  0 
mii                     5212  3 b44,8139too,8139cp
ssb                    35300  2 b43legacy,b44



```I cant give up!!! :)
Ubuntu looks so great!

---

### Post by pdc on 2010-02-23
why the legacy driver?

in this post

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

N Allen says

>  Broadcom BCM4301/03/06/09 Hardware (B43 driver):
NOTE: IF YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES B43*LEGACY*. **_ALL OTHER MODELS USE B43_**. 

---

### Post by bkratz on 2010-02-23
> **pdc said:**
> why the legacy driver?

in this post

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

N Allen says

If you look at his iwconfig you will see he has the "B" only version.

---

### Post by bkratz on 2010-02-23
@maycom


Did you ever try the statements in the other posting regarding rfkill?

"Originally Posted by chili555  
Please let us see, in order:"

rfkill list
sudo iwconfig wlan0 txpower auto
rfkill list

to see if it has any effect.



and also from the same thread

   Originally Posted by chili555
Hard blocked: yes


Does your laptop have both a Fn key combination and a hardware switch, like mine does? When the hardware slider goes to 'off' on my lappy, rfkill shows Hard blocked: yes and it changes to Hard blocked: no when I slide it back to 'on.'

---

### Post by maycom on 2010-02-24
> **bkratz said:**
> @maycom


Did you ever try the statements in the other posting regarding rfkill?

"Originally Posted by chili555  
Please let us see, in order:"

rfkill list
sudo iwconfig wlan0 txpower auto
rfkill list

to see if it has any effect.



and also from the same thread

   Originally Posted by chili555
Hard blocked: yes


Does your laptop have both a Fn key combination and a hardware switch, like mine does? When the hardware slider goes to 'off' on my lappy, rfkill shows Hard blocked: yes and it changes to Hard blocked: no when I slide it back to 'on.'

Hi bkratz :)
Yes, I've done the
```

rfkill list
sudo iwconfig wlan0 txpower auto
rfkill list

```
with no success...

My laptop does only have a push-button for switching the WiFi On/Off LED blinking once on booting the system. (Works fine when running MS Windows, so the hardware is OK I guess...)
I think my problem/situation is the same as "AlDo__71", post #12, in this [thread]("http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill&page=2")

---

### Post by benburkard on 2010-02-24
I'm having a similar issue. I just installed Ubuntu 9.10 on an Acer Laptop with Wireless card BCM4318 I think. When I click on the wireless icon in the top panel (where the choice of wireless and wired networks should be) it simply says:

**Wired Network**
disconnected

**Wireless Networks**
device not ready

I'm a total newbie. I've searched for literally hours to try and find a fix but can't. I got ubuntu 9.10 on my Dell and it all just slotted into place with no troubles at all. Now I've converted a friend to it and it won't work! All help much appreciated

---

### Post by bkratz on 2010-02-24
@maycom--I will do some more searching on the phenomena, and hopefully will come back with something useful; unless someone sharper than me jumps in.

@benburkard--I don't suspect you are suffering from the same issues-you really should start a new thread detailing your condition and copy/paste the output of (probably only the first request)

 lspci -nn 

from the terminal in your posting. That is (LSPCI in lowercase). The terminal can be found at Application>>Accessories>>Terminal.

Not knowing your model--perhaps something useful here
[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

---

### Post by capybara! on 2010-02-24
Hi, I had similar problems with a broadcom BCM4315 wireless card on a lenovo netbook. I looked through a lot of  threads and there were various solutions explained... none of them worked for me... 

Then I just installed the alpha version of Ubuntu lucid lynx, disabled the b43 driver and took the STA driver instead.. this did it for me

---

### Post by maycom on 2010-02-24
> **bkratz said:**
> @maycom--I will do some more searching on the phenomena, and hopefully will come back with something useful; unless someone sharper than me jumps in.


Thanks alot [bkratz]("http://ubuntuforums.org/member.php?u=821493") :)
I'm a bit stuck here...

---

### Post by maycom on 2010-02-25
Will I ever get this to work??

---

### Post by bkratz on 2010-02-25
> **maycom said:**
> Will I ever get this to work??

Well it depends on the work input, in all honesty it looks like it might be a lot easier to get a newer card.  I found these threads regarding your card and the solutions were very long ( so was the thread!) and required a lot of rebuilding of modules. Anyway, here they are:

[https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html](https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html)

[http://ubuntuforums.org/showthread.php?t=1368106](http://ubuntuforums.org/showthread.php?t=1368106)

The first shows an invalid certificate when you go there, but it seems safe to proceed and  I read the whole! thread. It is about the BCM4303 specifically and has a few developers involved in it. Worth reading though.


I will continue to look though, just in case.

---

### Post by maycom on 2010-02-25
> **bkratz said:**
> Well it depends on the work input, in all honesty it looks like it might be a lot easier to get a newer card.  I found these threads regarding your card and the solutions were very long ( so was the thread!) and required a lot of rebuilding of modules. Anyway, here they are:

[https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html](https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html)

[http://ubuntuforums.org/showthread.php?t=1368106](http://ubuntuforums.org/showthread.php?t=1368106)

The first shows an invalid certificate when you go there, but it seems safe to proceed and  I read the whole! thread. It is about the BCM4303 specifically and has a few developers involved in it. Worth reading though.


I will continue to look though, just in case.

HI:)
I've read the threads.... seems like really hard chip to get up and running in Ubuntu. My push button is working in MS Windows, and is shortly blinking when booting in Ubuntu.... hmmm....

should I test this NDIS- thing??

---

### Post by bkratz on 2010-02-25
> **maycom said:**
> HI:)
I've read the threads.... seems like really hard chip to get up and running in Ubuntu. My push button is working in MS Windows, and is shortly blinking when booting in Ubuntu.... hmmm....

should I test this NDIS- thing??

Do you have the win xp drivers for the device still?  (.inf and .sys)

---

### Post by bkratz on 2010-02-25
Just found this (the beginning is kinda old, but the later posts are about your card).  May not be any help, but at least worth reading before we go the ndiswrapper route.

[http://ubuntuforums.org/showthread.php?t=780692&highlight=BCM4303&page=8](http://ubuntuforums.org/showthread.php?t=780692&highlight=BCM4303&page=8)

---

### Post by maycom on 2010-02-26
> **bkratz said:**
> Just found this (the beginning is kinda old, but the later posts are about your card).  May not be any help, but at least worth reading before we go the ndiswrapper route.

[http://ubuntuforums.org/showthread.php?t=780692&highlight=BCM4303&page=8](http://ubuntuforums.org/showthread.php?t=780692&highlight=BCM4303&page=8)

Didn't work ....](*,)

---

### Post by bkratz on 2010-02-26
> **maycom said:**
> Didn't work ....](*,)




Haven't found anything else, and run out of ideas.  Are you comfortable with ndiswrapper? Do you have the .inf and .sys files? If you try the ndiswrapper direction, the easiest way is to start with ndisgtk which loads all the dependency files. If you want to try, I use ndiswrapper on mine and can help.

---

### Post by maycom on 2010-02-26
Hi bkratz :)
NDIS wrapper is OK i think.... tester ndisgtk last night (with no results)
Yes, I've the .inf and .sys files for Windows XP....
Thanks for your support bkratz :)

---

### Post by bkratz on 2010-02-26
> **maycom said:**
> Hi bkratz :)
NDIS wrapper is OK i think.... tester ndisgtk last night (with no results)
Yes, I've the .inf and .sys files for Windows XP....
Thanks for your support bkratz :)


Good Luck! I hope we don't run into the same blocking problems with ndiswrapper ( but I don't think we will with the windows drivers, since you already successfully use those on your system).

---

### Post by maycom on 2010-02-26
> **bkratz said:**
> Good Luck! I hope we don't run into the same blocking problems with ndiswrapper ( but I don't think we will with the windows drivers, since you already successfully use those on your system).

Ok... guess I've to remoe all this b43-stuff first?
tkanks again!

---

### Post by maycom on 2010-02-26
So.... I follow the instruction on [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") page. When adding the .inf file I get a message; "Unable to see if hardware is present." Click OK, and the status shows; "bcmwl5 - Hardware present: Yes"

But now I don't have any wireless alternative in my Network Manager.... :|
And pressing my WiFi-button doesn't change anything....

geeeee....

---

### Post by bkratz on 2010-02-26
> **maycom said:**
> So.... I follow the instruction on [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") page. When adding the .inf file I get a message; "Unable to see if hardware is present." Click OK, and the status shows; "bcmwl5 - Hardware present: Yes"

But now I don't have any wireless alternative in my Network Manager.... :|
And pressing my WiFi-button doesn't change anything....

geeeee....


Looks promising so far..

Let copy/paste the output of:

iwconfig
sudo lshw -C network
sudo iwlist scan

and the long one

lsmod

use the code tags for that one!

back here.
So we can see what drivers have control of the card now, and actually see if it is really working with the third command.

---

### Post by maycom on 2010-03-02
I'll be away for a while.... Will return on this :)

---

### Post by shrinkydink on 2010-03-06
I have the same laptop. Try adding 

SUSPEND_MODULES="b43"

to /etc/pm/config.d/00sleep_module.

---

### Post by maycom on 2010-03-25
> **shrinkydink said:**
> I have the same laptop. Try adding 

SUSPEND_MODULES="b43"

to /etc/pm/config.d/00sleep_module.

Hi! Long time.....
This was no success for me :(

But after installing Ubuntu on a Dell Inspiron 1720 everything seems to work perfect!! :)

(except the mic line in... only the integrated mic in the lid is workin I'm searching for a solution.....)

---

