---
title: "Cannot stop soft block on Atheros AR298X after disabling wireless w/ hardware switch"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by slaminallaeraew on 2012-01-22
[SIZE=4][COLOR=Magenta]***Skip to the large, pink words near the end of ***[/COLOR]             [post=11633202][COLOR=Magenta]***the fourth post in this thread***[/COLOR][/post][COLOR=Magenta]*** for the simple, one-sentence-long solution to this problem.***[/COLOR][/SIZE][COLOR=Magenta][/COLOR]
I am not actually on Ubuntu, but rather Trisquel, a distribution derived from Ubuntu. I am on the latest version, 5.0, which I am almost certain is based upon Ubuntu 11.04 (their releases lag significantly behind Ubuntu's). My laptop is an HP Pavilion dm3-1030us. In case you want this information: ```
dillon@paviliondm3:~$ uname -a
Linux paviliondm3 2.6.38-13-generic-pae #0trisquel1 SMP Wed Dec 21 15:21:53 UTC 2011 i686 athlon i386 GNU/Linux
``````
dillon@paviliondm3:~$ lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:    Trisquel
Description:    Trisquel 5.0
Release:    5.0
Codename:    dagda
```Now, onto the problem.&#8230; On the side of my laptop, there is a button that, when pressed, toggles wireless enabled/disabled. I had used it a couple times before, and it worked fine: press once, disabled, press again, enabled, *et cetera*, although I had never actually left it disabled for more than a few seconds. However, a couple days ago, I disabled it, left it disabled for a while, hibernated, and when I un-hibernated and pressed the button to re-enable wireless, nothing happened. I do not know why leaving the button disabled for a while and/or turning off the computer while it was still disabled should have caused the button to become ineffective, but I just happen to notice that these factors were the only differences in the circumstances between this situation and my previous, successful usages of the wireless toggle button.

I found this <[WirelessTroubleshootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")> (it is a link) that proved to be very useful and informative to detailing the problem. I followed it step-by-step, running the commands, which are very similar to ones that I see being asked for elsewhere to give information about wireless setups, so I will post the relevant sections of their outputs here, in order, as if I was following the [SIZE=1]guide again, complete with the Guide's numbered hierarchy of intructions.[/SIZE]

[SIZE=4][COLOR=DarkRed]2. Quick Check[/COLOR][/SIZE]```
dillon@paviliondm3:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        00:03:7F:8E:BB:A8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```[SIZE=4][COLOR=DarkRed]3. Troubleshooting Steps[/COLOR][/SIZE][SIZE=3][COLOR=Red]
[/COLOR][/SIZE][INDENT][SIZE=3][COLOR=Red]1. Device Recognition and Operation[/COLOR][/SIZE]
[/INDENT][INDENT][INDENT][COLOR=DarkOrange][SIZE=2]2. Check for Device Recognition[/SIZE][/COLOR]
[/INDENT][/INDENT]```
dillon@paviliondm3:~$ sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:03:7f:8e:bb:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-13-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1000000-f100ffff
```[INDENT][INDENT][COLOR=DarkOrange][SIZE=2]3. PCI Devices
[/SIZE][/COLOR][/INDENT][/INDENT]```
dillon@paviliondm3:~$ lspci -nn | grep 0280
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```I don't know if this is also helpful:
```
dillon@paviliondm3:~$ sudo lspci -vnn
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BHB92-H 802.11abgn Wireless Half-size Mini PCIe Card [103c:3041]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```[INDENT][COLOR=Red][SIZE=3]2. Device Drivers
[/SIZE][/COLOR][INDENT][SIZE=2][COLOR=DarkOrange]3. Check[/COLOR][/SIZE][SIZE=2][COLOR=DarkOrange] Driver[/COLOR][/SIZE]
[/INDENT][/INDENT]```
dillon@paviliondm3:~$ lsmod | grep ath9k
ath9k                 103669  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
```This is the first place where the output of my command is significantly different than the expected output as sampled on the Troubleshooting Guide's "Commands" page: ```
dillon@paviliondm3:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```And this is clearly not a desirable output, although that is of course not to say that it was unexpected: ```
dillon@paviliondm3:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```[INDENT][INDENT][INDENT][COLOR=Magenta]**[SIZE=1]3.2. Driver looks ok, device disabled[/SIZE]**[/COLOR]

[/INDENT][/INDENT][/INDENT][COLOR=Black]Now this is where I think things get[/COLOR] interesting. Under this 3.2 heading, the guide says, "Newer laptops come with battery saving features to  disable the wireless radio. Usually this is switched by a FN+Fx key  combo or a specific button for the purpose. It is possible the driver  and connection is ok but the wireless device is disabled and can't be  used. Using the designated key(s) in linux sometimes does not work." This is, in fact, a perfect description of my exact problem. The guide provides three options for identifying if this is the problem. Only the first one has any interesting result, and that first option is to run this command:
```
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```This seemed like exactly what I needed to find to address my problem because as soon as I had begun researching for solutions and found that the wireless adapter and drivers were clearly being successfully detected, I conjectured that the problem must not have been some hardware failure (as, for example, my mom suggested to me) but rather something along the lines of a software communication error. With this command, I found out that, in addition to "hard blocks" (that is, the disabled hardware switch), there are also "soft blocks" (in whatever form that may take). The Troubleshooting Guide's Commands page linked me to the <[online [FONT=Courier New]man[/FONT] page for [FONT=Courier New]rfkill[/FONT]]("http://manpages.ubuntu.com/manpages/natty/en/man8/rfkill.8.html")>, in which I discovered that [FONT=Courier New]rfkill[/FONT] has an [FONT=Courier New]unblock[/FONT] option, with the note "Enable the device corresponding to the given index. If the device is hard-blocked, e.g. via a hardware switch, it will remain unavailable though it is now soft-unblocked." So I tried:
```
dillon@paviliondm3:~$ rfkill unblock all
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```As you can see, the [FONT=Courier New]1: phy0: Wireless LAN[/FONT] device became un-soft-blocked, which was exciting, but the other two remained blocked. So I then tried to un-hard-block my wireless by trying the hardware toggle button again, and was again disappointed after that failed. I tried running [FONT=Courier New]sudo rfkill unblock all[/FONT], but that was not any more successful than the unprivileged [FONT=Courier New]rfkill unblock all[/FONT] had been. As the Guide continues: "So how do you rectify this? It varies so much the  exact solution can't be put here in this document for all the different  models. So... 
[LIST=1]
[*]Look at the <[LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam")> page on the team wiki to see if your laptop is listed with any information.
[*]Do  a google search using terms such as manufacture, model, linux,  wireless, enable, button, radio....etc. When searching and finding  similar pages that don't help, use words that are used in those pages to  help you search.
[*]Go to the <[ubuntu forums]("http://ubuntuforums.org")> and ask, maybe someone else has the same laptop and knows the work around.
[*]Some  laptops have a controller chip on the motherboard that is only  accessible through a different OS.  If you have turned off your wireless  adapter in a different operating system, you may have to boot back into  that OS and enable the card before it is accessible to Linux."
[/LIST]
I tried number one and the closest thing that I found was the <[HP Pavilion DM3-1040]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/HPPavilionDM3-1040")>, but I have the dm3-1030 and I do not know how the information there would help anyway. I had tried some of number two to no avail, now I am trying number three, and number four is inapplicable because Trisquel GNU+Linux is the only bootable operating system that I have installed on my computer and I have not even been into a virtual machine since prior to the toggle-button's failure. Besides, like I said, I have successfully used the wireless hardware switch in GNU+Linux previously. I never even knew what the button was for or paid any attention to its presence until long after I had abandoned Windows. So unless I have not exhausted the information available from number two (which I certainly have not, but please forgive me! :KS I did try looking for solutions before asking), number three is my only hope!

The instructions to             [post=6183681]**HOWTO post a Wireless issue (ticket)**[/post] suggest, in addition to the command outputs that I have already posted, to provide the following information:
```
dillon@paviliondm3:~$ dmesg | grep ath9k
[   11.816304] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.816318] ath9k 0000:08:00.0: setting latency timer to 64
[   15.985123] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.986329] Registered led device: ath9k-phy0::radio
[   15.986455] Registered led device: ath9k-phy0::assoc
[   15.986591] Registered led device: ath9k-phy0::tx
[   15.986743] Registered led device: ath9k-phy0::rx
[24255.863773] PM: restore of drv:ath9k dev:0000:08:00.0 complete after 243.160 msecs
``````
dillon@paviliondm3:~$ sudo /etc/init.d/networking restart
[sudo] password for dillon: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
```Thanks in advance!:popcorn:

---

### Post by slaminallaeraew on 2012-01-22
Just when I was somewhat losing hope because the other related threads had some solutions that seemed to only sporadically work for people, my problem was solved with this series of commands:

```
dillon@paviliondm3:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
dillon@paviliondm3:~$ sudo !!
sudo ifconfig wlan0 up
[sudo] password for dillon: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
dillon@paviliondm3:~$ sudo rfkill unblock all 
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```After I saw this last output, I simply looked at the wireless hardware toggle switch on the side of the laptop, and the light on it was then blue (rather than the orange that it had been for the few days that I had been having the problem). I did not even have to press the button. The entire series of commands transpired so quickly and suddenly, it felt like a fluke, but success felt glorious.

I was inspired to run that particular set of commands while looking for a solution on this post: [http://ubuntuforums.org/showthread.php?t=1781350&highlight=soft+blocked](http://ubuntuforums.org/showthread.php?t=1781350&highlight=soft+blocked)

Thanks, Ubuntu Forums!

---

### Post by slaminallaeraew on 2012-01-22
Nevermind. As I was fiddling around with blocking and unblocking just to double-check my solution and get comfortable with doing it, I ended up back in my previous position in which [FONT=Courier New]rfkill unblock all[/FONT] unblocks [FONT=Courier New]1: phy0: Wireless LAN[/FONT] only. The exact series of commands that I thought had solved my problems last time were unsuccessful this time.

I went back and looked at which commands exactly I used to block myself this time and found something interesting. After the commands posted in the last message, all of my wireless services were turned back on, including Bluetooth, which I usually disable. So I disabled Bluetooth using the applet in the notification area, and then I ran [FONT=Courier New]rfkill list[/FONT] to see if it would indicate that I had turned it off. It did:
```
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```Then, I ran [FONT=Courier New]rfkill unblock bluetooth[/FONT] just to practice using the command to unblock wireless services,  and the Bluetooth applet indeed lit up again so I knew that I was successful. Then, I tried [FONT=Courier New]rfkill block all[/FONT] so that I could then unblock them, and that block soft-blocked all options, as well as hard-blocked [FONT=Courier New]1: phy0: Wireless LAN[/FONT]:
```
dillon@paviliondm3:~$ rfkill block all 
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```I then tried the following to see if I could hard-block the two [FONT=Courier New]hp-*[/FONT] devices and then bring them up, but my attempt to hard-block them made no difference:
```
dillon@paviliondm3:~$ sudo ifconfig wlan0 down
[sudo] password for dillon: 
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```**Now, here is the interesting part. After seeing that the hard blocks were not changing to yes, I decided simply to try to unblock the soft blocks, but instead, the hard blocks went up:**
```
dillon@paviliondm3:~$ rfkill unblock all
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```It was at this point that I decided to try the combination that had seemed to work for me last time, which was [FONT=Courier New]sudo ifconfig wlan0 up[/FONT] followed by [FONT=Courier New]rfkill unblock all[/FONT]:
```
dillon@paviliondm3:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
dillon@paviliondm3:~$ rfkill unblock all
dillon@paviliondm3:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```I tried various combinations of [FONT=Courier New]sudo ifconfig wlan0 up[/FONT], [FONT=Courier New]rfkill unblock all[/FONT], and [FONT=Courier New]sudo rfkill unblock all[/FONT] a few times without any success.

I saw some other people's answers elsewhere referring to removing driver modules and some other stuff. I guess I will try those approaches tomorrow; for now, I should sleep. But even if I find a solution, and even if somebody else does not have a solution to provide to me as an answer, could someone at least explain this weird [FONT=Courier New]rfkill[/FONT] command? What sort of program is this that it will be unresponsive to blocks but respond to an unblock with a block?! I am trying to do more than just solve my problem, but also to understand what I am doing and why.

---

### Post by slaminallaeraew on 2012-01-23
OK, finally solved again! Now I  understand the exact nature of my problem. My confusion was piqued  when I tried to re-approach this problem just now for the first time  today. Last night, just before going to bed, I tried some last-ditch  efforts to re-solve my problem. The last command I ran, and its output,  were: ```
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
     Hard blocked: yes
``` Directly after that, I left the terminal open  and hibernated. After un-hibernating, the first thing I did was to run  the command again, in the same terminal, without having made any changes  (or so I thought): ```
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
``` This was the same state that the blocks had been in directly before running the [FONT=Courier New]sudo rfkill unblock all[/FONT] that initially solved the problem the first time around, so I ran [FONT=Courier New]sudo rfkill unblock all[/FONT]  again, and it again solved the problem. I could not fathom why the hard  blocks had somehow unblocked themselves, enabling me to then unblock  the soft blocks and bring all wireless devices back into action.

Soon  enough, however, I realized that this was related to my repeated  pressing of the hardware switch button. Throughout this entire process  of trying to solve this issue, I have periodically pressed the wireless  toggle button, usually several times, sometimes frantically in  frustration. When doing so, I only thought to see if the light on the  switch would turn from orange to blue, which it never did. As long as  the light remained orange, I assumed that the hard block remained  active. In the absence of any visual cue that pressing the button had done anything whatsoever, I assumed that it had done nothing whatsoever. However, I now decided to press the switch, run [FONT=Courier New]rfkill list[/FONT], press the switch again, run [FONT=Courier New]rfkill list[/FONT] again, and see what the difference was, if any.

This was with everything enabled and fixed correctly, with blue light and everything:
```
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
18: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
dillon@paviliondm3:~$ rfkill block all 
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```The switch light turned orange after [FONT=Courier New]rfkill block all[/FONT], despite the hard block on 0 and 2 being no. I now pressed the switch, which remained orange, and ran:
```
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

```Pressing the switch had toggled the hard block on 0 and 2. I pressed the switch again, and it remained orange. Previously, I would have assumed that the action had accomplished nothing since the light remained orange, but now I ran:
```
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
dillon@paviliondm3:~$ rfkill unblock all 
dillon@paviliondm3:~$ rfkill list 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
19: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Despite the indicator light on the hardware switch making no change in color, it internally toggles the hard block on 0 and 2. [FONT=Courier New]rfkill block all[/FONT] and [FONT=Courier New]rfkill unblock all[/FONT] toggle the soft block on 0, 1, and 2, as well as the hard block on 1; but they do this only if hard block on 0 and 2 are no. If not (that is, all blocks are yes), they toggle only soft block on 1:
```
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
dillon@paviliondm3:~$ rfkill unblock all
dillon@paviliondm3:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```In addition, if hard block on 0 and 2 are no, [FONT=Courier New]rfkill unblock all[/FONT] opens an [FONT=Courier New]hci0: Bluetooth[/FONT] device with number incremented from the number of the last such device open (at least on my computer).

So what was causing blocks to be lifted seemingly randomly and unexpectedly was that I was randomly pressing the wireless toggle button in moments of frustration, without considering that action to be of any particular significance or noticing its correspondence with changes in command outputs. The first time that I successfully re-enabled wireless connectivity, my success was only a result of my having recently pressed the button in frustration again and that press had coincidentally toggled the hard blocks to no. When the commands were unsuccessful, the hard blocks were coincidentally yes as the result of having recently pressed the wireless toggle button again. But now, knowing the behavior of the [FONT=Courier New]rfkill[/FONT] commands in relation to the behavior of the toggle button, all wireless devices can be disabled and enabled easily, reliably, and at will.

[SIZE=4][COLOR=Magenta]Long story short, the solution to the original query is to toggle the hardware switch until [FONT=Courier New][font=courier]rfkill list[/FONT][/font] shows that the hard blocks on whichever devices the hardware switch is allowed to unblock are indeed unblocked (to determine which blocks should be unblocked, 1) run [FONT=courier]rfkill list[/FONT], 2) toggle the hardware switch, 3) run [FONT=courier]rfkill list[/FONT] again and notice where "no" changed to "yes" or vice versa between the two outputs of [FONT=courier]rfkill list[/FONT]. The ones that changed should now be "no"; if they are "yes", toggle the hardware switch once again to change them back to "no".), and then simply run [FONT=Courier New][font=courier]rfkill unblock all[/FONT][/font], which will disable all other blocks&#8212;hard and soft&#8212;on all devices that are available.[/COLOR][/SIZE][COLOR=Magenta]
[/COLOR]
That is all.

---

