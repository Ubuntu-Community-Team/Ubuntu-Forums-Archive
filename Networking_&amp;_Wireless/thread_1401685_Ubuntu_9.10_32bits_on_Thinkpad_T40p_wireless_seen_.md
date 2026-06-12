---
title: "Ubuntu 9.10 32bits on Thinkpad T40p: wireless seen but not working"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Sylvain Prévost on 2010-02-08
I installed Ubuntu 9.10 32bits on my IBM Thinkpad T40p (2373-G1G)
I am using the Wireless network icon to choose the network (the SSID is not hidden) and give my password. There is no other option (the wireless security list only contains one entry: "WPA & WPA2 Personal). After a few minutes during which the network icon shows a search activity, I am getting back the window asking for my password (but without any error message such as "wrong password")

I am not making a mistake with the password (checked) and the wireless is OK (currently 2 other computers seeing and using it).

I am normally using WPA-TKIP (pre-shared key). My router can also use WPA2 (AES), but selecting this option on the router did not help for my laptop.

I believe that previously I had to install a proprietary driver to have it working. With this 9.10 version I am not getting any suggestion for proprietary driver (even not the ATI card). I do remember that using ArchLinux with opensource drivers, a year ago or so, it was not working as well.

Among many other things, "sudo lshw -C network" gives that:
product: AR5211 802.11ab NIC
vendor: Atheros Communications Inc.
physical id: 2

I believe I have this card:
[http://www.thinkwiki.org/wiki/IBM_Dual-Band_11a/b_Wi-Fi_Wireless_Mini_PCI_Adapter](http://www.thinkwiki.org/wiki/IBM_Dual-Band_11a/b_Wi-Fi_Wireless_Mini_PCI_Adapter)

Chipset: Atheros AR5001X
IEEE Standards: 802.11a, 802.11b
PCI ID: 168c:0012

Thanks in advance for the help!

---

### Post by chili555 on 2010-02-08
Let's see which driver is being used. Please do:```
lsmod | grep ath
```We hope it is *ath5k*. Also, let's verify if your card and driver are actually capable of WPA. Please do:```
ifconfig
```Is your wireless interface ath0 or wlan0? Whichever one it is, please do this command:```
sudo iwlist wlan0 auth
```Substitute your interface if it's ath0. It will then tell you what your card can do with its current driver.

---

### Post by skuli.arnlaugsson on 2010-02-09
Hi!

I'm experiencing the exact same problem on the exact same kind of computer (T40p 2373 G1G). My wireless worked fine on 8.10, but then I updated to 9.10 and I can no longer access my home WPA network (using airport extreme to manage my wireless).

I ran the commands you mentioned, and its ath5k, and my wlan0 can authenticate WPA, WPA2 and more. 

Any ideas how to fix this?

---

### Post by chili555 on 2010-02-09
Please try:```
sudo rmmod -f ath5k
sudo moprobe ath5k nohwcrypt=1
```Does the behavior improve?

---

### Post by skuli.arnlaugsson on 2010-02-09
> **chili555 said:**
> Please try:```
sudo rmmod -f ath5k
sudo moprobe ath5k nohwcrypt=1
```Does the behavior improve?

No, I am afraid not. I still timeout while trying to connect to my WPA network. Any more ideas?

---

### Post by skuli.arnlaugsson on 2010-02-09
Chilli555: Do you think these directions will assist me? [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by chili555 on 2010-02-09
> **skuli.arnlaugsson said:**
> Chilli555: Do you think these directions will assist me? [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)In Linux years, that's about 50 years old!> Posted by Admin on October 20th, 2006 I certainly would try this step to start:```
sudo apt-get install wpasupplicant
```I suspect this is really more a function of the *ath5k *driver, although I can't quite figure what.

---

### Post by Sylvain Prévost on 2010-02-10
Sorry for the delay. I am listing here the results of the suggested commands.

lsmod | grep ath
ath5k                 124260  0 
mac80211              181140  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,thinkpad_acpi

ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:05:4e:41:97:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1363 (1.3 KB)  TX bytes:1898 (1.8 KB)

sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Authentication algorithm :
        open

I tried 
sudo rmmod -f ath5k
(accepted with no message)
then
sudo moprobe ath5k nohwcrypt=1
not accepted, with the message:
sudo: moprobe: command not found

Since then the network icon does not offer the wireless connection anymore.

>skuli.arnlaugsson, did you have such message and effect when trying the command?

the command
sudo apt-get install wpasupplicant
only resulted in a message informing that the latest version of wpasupplicant was already installed.

---

### Post by chili555 on 2010-02-10
> sudo moprobe ath5k nohwcrypt=1My spelling is getting a bit rusty, isn't it. Sorry. Please try:```
sudo rmmod -f ath5k
sudo mo[COLOR="Red"]d[/COLOR]probe ath5k nohwcrypt=1
```Please let us know if connecting is easier.

---

### Post by Sylvain Prévost on 2010-02-11
YES! It does work now. Thanks a lot Chili555.

Now I do have a question: what was the problem exactly, and should I consider this as a bug and try and inform for this bug?

Also, totally unrelated to this topic but as skuli.arnlaugsson has exactly the same computer as me I would like to know if he had the same problems, and it probably does not deserve a new topic:

- when installing Ubuntu 9.10, at first Linux would not boot after Grub, and the disk ID was "not found". When re-installing, I saw that the boot loader would be installed on (hd0) by default, and I instead selected /sda. It worked.
- I really have the feeling that the graphics are significantly slower that it used to be, either on Linux or on Windows. I might simply have forgotten (I did not use this computer for quite some time), but I do believe this effect is real. Here I am using no "Visual effects", and still when moving windows there is some latency. With visual effects activated, it is even worst.

PS: How do I indicate that the thread is solved?

---

### Post by chili555 on 2010-02-11
> what was the problem exactly, Some wireless chipsets do encryption in the chipset; some rely on software, that is, the operating system, to handle all those details. Obviously, those that are capable of hardware implementation have the option of *either* hardware or software. Sometimes, for reasons I don't quite understand, unless it's a hardware defect, one or the other doesn't quite work correctly. Another identical computer, with the same chipset, works perfectly. If you look at:```
modinfo ath5k
```you will see there are several parameters that can be set and hardware encryption is one of them. Whenever the driver loads and fires up an interface but won't actually connect, that's one thing I suggest be tried.

Is it a bug? I'm not sure. Perhaps your card has a defect. We are lucky it can be worked around.

As you will no doubt discover, upon reboot, these changes will be ineffective. Unless you take some steps, you will have to issue these commands every boot. Please do:```
sudo su
echo options ath5k nohwcrypt=1 >> /etc/modprobe.d/ath5k.conf
```Post back if you get stuck.> I really have the feeling that the graphics are significantly slower that it used to be, either on Linux or on Windows. Which video driver do you use, radeon? This is probably better answered in Multimedia & Video.

---

### Post by Sylvain Prévost on 2010-02-14
Thanks again chili555, it works smoothly included after reboot with this line file added to etc.

I could nt yet find out how to indicate that the thread is now solved?

---

### Post by zorrocket on 2010-03-23
Hello,

I just installed Ubuntu 9.10 2 days ago. I am using the same system as you Sylvain (T40p 2373-G1G) and I have gone through the step you have recommended, chili555, but it still does not work for me, as the symptoms remain, even after disabling hw encryption with the command suggested. Any other thoughts, by any chance?

Also, being a total (linux) newbie, I am just in the process of reading entry-level documentation to make myself familiar with Ubuntu and GNU/Linux, so please keep it simple for now. :p

Any help will be much appreciated on this.

---

### Post by chili555 on 2010-03-23
Let's be sure it's the same. Please post:```
sudo lshw -C network
```Does Network Manager see your network but just fail to connect?

---

### Post by zorrocket on 2010-03-25
Hello,

thank you for your reply, that is very nice of you. I now subscribed to the thread, so I should be faster responding the next time!

Ok, when I posted my reply 2 days ago, my wireless adapter was activated and would offer a list of wireless networks to connect to. When I picked any of my networks (both WPA2 encrypted), provided the password, it was trying to connect for a little while, until the windows prompting for the password came up again ; from that perspective, a very similar issue to the one reported earlier in this thread. I tried the few commands suggested, but it did not solve the problem for me.

Right now, my wireless adapter does not seem to be activated, as the connection manager only offers the option of wired connections (the one I'm using right now to post this).
You are probably not interested in the output from the command 
sudo lshw -C networkyou suggested, since it woudl report information from my eth0 adapter (wired), and not wlan0 (wireless).

Now I'm trying to find out how to reactivate my wireless adapter. Google, here I come! But if you want to help on this, you're welcome! ;-)

---

### Post by chili555 on 2010-03-25
> sudo lshw -C networkyou suggested, since it woudl report information from my eth0 adapter (wired), and not wlan0 (wireless).Why? Does it not show up at all? Even if it is disabled it should appear. It is a PCI or miniPCI device, I assume.

---

### Post by zorrocket on 2010-03-25
Here's the output:

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:b0:0d:3e
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=xx.xxx.xx.x latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0240000-c024ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: memory:c0210000-c021ffff

Thoughts?

I'm checking exact info for wireless device. It is a miniPCI.

---

### Post by zorrocket on 2010-03-25
Allright. Now, after 2 reboots, I'm back to where I was 2 days ago. Wireless adapter is activated and can see networks. When I choose mine, I'm prompted for the WPA2 password, which I enter (correctly). Next, the connection manager icon in the panel spins for a minute or so, until it prompts me again for the password.

Running your command gives me this now:

  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:05:4e:40:70:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11ab
       resources: irq:11 memory:c0210000-c021ffff

---

### Post by chili555 on 2010-03-25
First, lets' get the driver module to load on boot:```
sudo su
echo ath5k >> /etc/modules
exit
```Network Manager is designed to use your wired ethernet to the exclusion of wireless. Please detach the ethernet cable and reboot and let us know if you see any improvement.

---

### Post by zorrocket on 2010-03-25
Done and done. No visible change though.

Also, I have to point out that I'm running Ubuntu that is installed on the same partition as windows XP. Could that cause problems (I installed XP first, Ubuntu after) ?

---

### Post by chili555 on 2010-03-25
Did you try the fix in post #4  above?

---

### Post by zorrocket on 2010-03-25
I did, then rebooted, but it did not the issue.

I'm considering doing a fresh install on another, single partition, linux-only hard drive, to see whether that does the trick. I can report the status then.

---

### Post by zorrocket on 2010-03-29
Hi again,

I hope you had a nice week-end, chili555 :-)

So, I have a fresh ubuntu 9.10 install, single partition, linux only.

I have tried the command lines suggested in this thread, without any luck.

I wanted to test wireless connectivity and deactivated any encryption on the router (it is not connected to anything else for now), and even then, it would not let me connect and get a local ip.

I can see the ssid, select the network to try to connect, but it still doesn't work. I feel a bit lost here... I really love ubuntu, as it runs very nicely on my old thinkpad otherwise, and I really would like to keep using it, but the wifi is a bit of a deal-killer...

Right now, I am checking other ubuntu forums related to wifi troubleshooting, but I welcome any piece of advice !

---

### Post by chili555 on 2010-03-29
How about letting me take a peek at:```
iwconfig
sudo iwlist wlan0 scan
```This thing ought to leap to connect!

---

### Post by zorrocket on 2010-03-29
Sure!

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11ab  ESSID:"BClink"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and for iwlist wlan0 scan : there are about 40 wireless networks (it's a highrise), and when I do the scan, my network does not show up... Any idea about how to get mine in the list ?

Thanks

---

### Post by zorrocket on 2010-03-29
Never mind, here it is 

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:36:B8:B9
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"BClink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000519f9e218e
                    Extra: Last beacon: 6396ms ago
                    IE: Unknown: 000642436C696E6B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

:)

---

### Post by chili555 on 2010-03-29
> I wanted to test wireless connectivity and **deactivated** any encryption on the router (it is not connected to anything else for now)Are you sure?> Never mind, here it is

wlan0 Scan completed :
Cell 01 - Address: 00:0F:66:36:B8:B9
Channel:8
Frequency:2.447 GHz (Channel
Quality=67/70 Signal level=-43 dBm
Encryption keyn
ESSID:"BClink"
--- snip ---
IE: [COLOR="Red"]WPA[/COLOR] Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSKAre you sure your card does WPA? I notice it's an 802.11ab card; not G and nevermind N, so it may not.```
sudo iwlist wlan0 auth
```

---

### Post by zorrocket on 2010-03-29
thank you for your reply.

Well, I have two identical routers (linksys WRT54G w tomato firmware), and one of them (ESSID bcguest) has no security:

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:45:FE:9C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"BCguest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000000095b5195
                    Extra: Last beacon: 2128ms ago
                    IE: Unknown: 000742436775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: DD06001018020000



and my adapter should be ok for encryption, since 
sudo iwlist wlan0 auth

returns: 

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Authentication algorithm :
        open

Regardless of those capabilities, it does not make sense to me why the connection would fail, even without any security activated on the wireless AP...

This is a bit annoying. I really like Ubuntu otherwise!!! Any chance this problem disappears with the next release end of April?

---

### Post by chili555 on 2010-03-29
I noticed in your other thread that both ath5k, ath_pci and ath_hal are loading. I wonder if they are conflicting. Please do:```
sudo rmmod -f ath_pci
sudo rmmod -f ath_hal
```Any change in your ability to connect? If so, we can blacklist those two.> Any chance this problem disappears with the next release end of April? I haven't heard; you might download and run the live CD and find out. Post your experience so all the searchers will know. I sure hope so!

---

### Post by zorrocket on 2010-03-29
Good thinking but unfortunately it does not help...

I just finished burning the Live CD for Lucid Lynx beta 1, and will report here how things go. *fingers crossed*

---

### Post by chili555 on 2010-03-30
Do you not have */etc/modprobe.d/blacklist-ath-pci_conf* on your system?> # For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pciIf not, you might just put one there and reboot and see what happens.

---

### Post by zorrocket on 2010-03-31
Hi again,

more news about my wireless "situation".

- tried Lucid Lynx alpha 1, and it did not make a difference in my case (it looks very nice, though)
- tried a different router (2wire 2700hg-e that I had lying around), and I manage to establish a wireless connection using WPA (YEAH !!)

It is good news, and probably means drivers included in ubuntu are not responsible for my initial difficulties, but I still have problems :
- wireless AP association / communication does not work beyond approx 2 ft with the 2wire
- wifi still does not work at all with other APs, hence this question: what is the difference between this AP and my other ones, and causing the problem?

Any help welcome, as usual! :)

---

### Post by davidyu on 2010-04-03
I have the same issue in Karmic and Lucid.
My wireless card is Atheros 5211.
Every time I have reinstall Ubuntu, the default ath5k never worked. Pretty sad.
My workaround : 
      To download classic madwifi driver :  madwifi-trunk-r4099-20090929.tar.gz
Anyway, i still try to find any solution to use new ath5k.

---

### Post by chili555 on 2010-04-03
> Anyway, i still try to find any solution to use new ath5k.I believe it is included in *linux-backports-modules-karmic-generic* which is installable through Synaptic.

---

### Post by wyhteagle on 2010-09-15
I know this is a really old post but I just wanted to say THANK YOU!!!! I have been searching forever for the correct command to get this stupid wireless card to work and it finally does!

---

