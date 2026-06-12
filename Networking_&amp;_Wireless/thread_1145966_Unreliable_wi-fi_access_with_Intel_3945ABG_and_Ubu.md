---
title: "Unreliable wi-fi access with Intel 3945ABG and Ubuntu 9.04"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by 30rock on 2009-05-02
Hello,

I installed Ubuntu 9.04 (*2.6.28-11-generic i686*) on my Thinkpad X60, which has an *Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)* wireless card.

It correctly finds a series of networks, automatically connects to my WPA2 personal wireless router, but after a while, in a random manner, the Internet connection is lost. I still have 5 bars in the icon tray, but the actual internet connection is lost and I can't ping anything.

The only solution for me is to disconnect and re-connect, but usually I will experience the same problem a few minutes later. It's very frustrating, especially because I'm trying to switch to Ubuntu only on this laptop, and XP gave me no problems whatsoever with the same network controller.

Here are some details:

```
$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"Turing Lab"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <omitted>   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-48 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
$ lsmod | grep iwl3945
iwl3945                97912  0 
mac80211              217208  1 iwl3945
led_class              12036  2 iwl3945,thinkpad_acpi
cfg80211               38032  2 iwl3945,mac80211
```

```
$ dmesg | grep "iwl3945"
[    8.624233] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    8.624237] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    8.624355] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.624371] iwl3945 0000:03:00.0: setting latency timer to 64
[    8.624420] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    8.624705] iwl3945 0000:03:00.0: irq 2297 for MSI/MSI-X
[    8.679522] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.182969] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-1.ucode
[B][  621.892009] iwl3945: Microcode SW error detected.  Restarting 0x2000008.
[  621.894037] iwl3945: Can't stop Rx DMA.[/B]
[B][  741.726461] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  741.726476] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x023B ser 0x0000004B
[  741.730176] iwl3945: Can't stop Rx DMA.
[ 2753.402676] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 2753.402692] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x023A ser 0x0000004B
[ 2753.406350] iwl3945: Can't stop Rx DMA.[/B]
```

Do you have any suggestions?

Thanks.

---

### Post by 30rock on 2009-05-02
Just to be on the safe side, I disabled IPv6. It didn't do any good.

---

### Post by Marsan on 2009-05-03
I have the almost same problem. The cnnection is unstable and disconnects.

I have tried iwl3945 and ipw3945 modules, but their all the same.

---

### Post by rodrigo.toste.gomes on 2009-05-03
Hi I have the same problem.
I believe I found a way to solve it, although I'm not still 100% sure, but it looks promising, since my internet connection hasn't fallen for over an hour now ...
What I did was to set the MTU on NetworkManager to that of my router.
I also read somewhere that the best MTU is 1400, although I don't remember now why.
I really hope this works now, because it got really anoying, and that way, I ended up helping you :P

---

### Post by chili555 on 2009-05-03
I suggest trying:```
sudo ifconfig wlan0 mtu 1492
```If that has no effect, please try 1400. If either fixes it, post back and we can make it permanent.

---

### Post by rodrigo.toste.gomes on 2009-05-05
> **chili555 said:**
> I suggest trying:```
sudo ifconfig wlan0 mtu 1492
```If that has no effect, please try 1400. If either fixes it, post back and we can make it permanent.

It didn't work.
Thanks anyway.
Anyone have any other suggestions?

---

### Post by njtromp on 2009-05-07
Hi, I'm experiencing the same problem. Setting the MTU to 1492 or 1400 did not help much. Although setting the value to 1492 seems to make it possible to stay connected for a couple of hours.
Loosing the connection seems to have some relation with the number of TCP/IP packages send/recieved. When I try to download for example the latest NetBeans beta (which is around 230 MB) the connection is lost within minutes. When I just browse the internet the connection is lost after some hours.

If you need detailed information or me to try something just let me know.

By the way I upgraded my system from 8.10.

Kind regards
Nico Tromp

---

### Post by enza on 2009-05-07
same problem here, it's driving me crazy

---

### Post by rodrigo.toste.gomes on 2009-05-07
> **njtromp said:**
> Hi, I'm experiencing the same problem. Setting the MTU to 1492 or 1400 did not help much. Although setting the value to 1492 seems to make it possible to stay connected for a couple of hours.
Loosing the connection seems to have some relation with the number of TCP/IP packages send/recieved. When I try to download for example the latest NetBeans beta (which is around 230 MB) the connection is lost within minutes. When I just browse the internet the connection is lost after some hours.

If you need detailed information or me to try something just let me know.

By the way I upgraded my system from 8.10.

Kind regards
Nico Tromp

Ya I noticed that it was kinda related to the number of packages sent/received.

I have three questions for you all ...
What kind of network are you trying to connect to (A/G/N)?
What's you OS version (64 bit or 32 bit)?

I'm connected to a N network, with the 64 bit jaunty.
I believe this bug has been already reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323622](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323622)
Apparently switching from wireless N in the router (mixed G and N will connect the card to the N) to G will solve the problem (although it's annoying that we can't use N :S). I've tried it now, and it's been stable until now, but it hasn't been long yet. But another option you have is to try what is suggested on the last post on the bug report (haven't had time to try it yet, so if you are successful please tell).

---

### Post by njtromp on 2009-05-08
> **rodrigo.toste.gomes said:**
> Ya I noticed that it was kinda related to the number of packages sent/received.

I have three questions for you all ...
What kind of network are you trying to connect to (A/G/N)?
What's you OS version (64 bit or 32 bit)?

I'm connected to a N network, with the 64 bit jaunty.
I believe this bug has been already reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323622](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323622)
Apparently switching from wireless N in the router (mixed G and N will connect the card to the N) to G will solve the problem (although it's annoying that we can't use N :S). I've tried it now, and it's been stable until now, but it hasn't been long yet. But another option you have is to try what is suggested on the last post on the bug report (haven't had time to try it yet, so if you are successful please tell).

I am connecting to a N network. My laptop is running the 32 bit version of Jaunty. I'll have a look at the bug report and will report later.
The problems started after my upgrade to Jaunty (9.04). The connection while running Ibix (8.10) was quite stable. It was lost only once a month.

Kind regards

Nico

---

### Post by RyanGT on 2009-05-08
I have a strange question/suggestion.  I see a lot of posts about the iwl3945 driver with similar behavior.  Are any of you using static WEP with an ascii key?  I am and was having similar issues.  I think there may be a bug in how the gnome network-manager converts ascii keys to hex.  Mine had one wrong digit.  I used this at the terminal instead:

perl -e 'print unpack("H*", "ascii key here"), "\n"'

and when I pasted that output into the gnome network-manager gui, my problems seem to have gone away (I also changed it to use DHCP, which it wasn't doing by default).  My connection has been working for 30 or so minutes now (way longer than before).

---

### Post by rodrigo.toste.gomes on 2009-05-08
Well, from what I noticed, this problem only seems to occur with N networks, maybe yours is another problem.
Anyway, installed the latest drivers ... it works, and I don't have to ever reconnect (not until now at least), but there are moments where we loose the connection (but it gets back pretty fast, so no downloads are interrupted, and you barely notice it, since it only lasts a few seconds).
Anyway, another issue that I noticed, still happens - network speed. Try seeing the network information, it says 1Mb/s ... this doesn't happen with the G network. I think I'll just wait for this problem to be solved, and until then I'll use G network.
But this is really strange, because this problem wasn't present in 8.10 (unfortunatelly my laptop wouldn't accept 64 bit 8.10, for some unknow CPU issue, that was solved in 9.04).

PS: While I wrote this, the network connection started behaving more erratically. Now, it won't reconnect automatically again :S I advise you to change to a G network if you can.

---

### Post by njtromp on 2009-05-11
> **RyanGT said:**
> I have a strange question/suggestion.  I see a lot of posts about the iwl3945 driver with similar behavior.  Are any of you using static WEP with an ascii key?  I am and was having similar issues.  I think there may be a bug in how the gnome network-manager converts ascii keys to hex.  Mine had one wrong digit.  I used this at the terminal instead:

perl -e 'print unpack("H*", "ascii key here"), "\n"'

and when I pasted that output into the gnome network-manager gui, my problems seem to have gone away (I also changed it to use DHCP, which it wasn't doing by default).  My connection has been working for 30 or so minutes now (way longer than before).

I use WPA2 with a 64 hex password generated by [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm). So I don't think that's the problem. I am writing this response using Jaunty. 

After changing the network to only operate as a b/g network connectiong to it took quite a while. At first it looked prertty good. Then I decided to start downloading a large file (JBoss-5.0.1.GA which is around 100MB) and lost the connection after a few minutes :-(.

---

### Post by njtromp on 2009-05-11
> **njtromp said:**
> I am connecting to a N network. My laptop is running the 32 bit version of Jaunty. I'll have a look at the bug report and will report later.
The problems started after my upgrade to Jaunty (9.04). The connection while running Ibix (8.10) was quite stable. It was lost only once a month.

Kind regards

Nico

Changing my AP to a b/g only network did not work :-(

After changing the network to only operate as a b/g network connectiong to it took quite a while. At first it looked pretty good. Then I decided to start downloading a large file (JBoss-5.0.1.GA which is around 100MB) and lost the connection after a few minutes :-(.

---

### Post by penchev on 2009-05-12
Hello people - I also have problem with Intell 3945 ABG wifi on HP Pavillion dv6000 32bit
with fresh install of Ubuntu 9.04

```
  
[   24.106993] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   24.231163] Registered led device: iwl-phy0:radio
[   24.231186] Registered led device: iwl-phy0:assoc
[   24.231245] Registered led device: iwl-phy0:RX
[   24.231265] Registered led device: iwl-phy0:TX


```

---

### Post by Godzemo on 2009-05-22
I'm having the same problem, running Ubuntu 9.04 on a Vostro 1500. It's all kinds of irritating.

Edit: Just to note, I used Wicd rather than network-manager.

---

### Post by Haschmi on 2009-05-22
The same problem here with a HP NX6310 and Intel 3945. I can connect to the WLAN but after a few minutes i can't ping my router anymore. The icon of the network-manager still shows five bars. With my IBM T42 there is no problem with Ubuntu 9.04 and WPA2 to the same access point.

---

### Post by stingx on 2009-05-28
I have same problem..  My Os is Ubuntu 8.04, but it seems, that problem exists on all iwl3945 driver versions... In my case, microcode upgrade done the job. Now, WiFi works perfectly and didn't lose connection any more.
All you need to do is to download latest microcode from [www.intellinuxwireless.org](www.intellinuxwireless.org) and put new microcode instead of current.

You can do this simple steps:
```

wget http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz
tar -xzf iwlwifi-3945-ucode-15.32.2.9.tgz
cd iwlwifi-3945-ucode-15.32.2.9
sudo cp -f iwlwifi-3945-2.ucode /lib/firmware/`uname -r`/iwlwifi-3945-1.ucode
sudo chmod 644 /lib/firmware/`uname -r`/iwlwifi-3945-1.ucode

```
After this, you can reboot you PC or do:
```

sudo ifconfig wlan0 down
sudo rmmod iwl3945
sudo modprobe iwl3945
sudo ifconfig wlan0 up

```
After this, you should apply all your wireless settings.

Hope, this will help

---

### Post by Godzemo on 2009-05-28
Thanks for the tip. I'll give that a try now, report back in a few hours if it worked :)

---

### Post by Godzemo on 2009-05-31
At least partial success! I've been using the microcode update for a few days and I haven't had to reconnect. I haven't done any heavy traffic use yet, though.

---

### Post by njtromp on 2009-06-04
> **Godzemo said:**
> At least partial success! I've been using the microcode update for a few days and I haven't had to reconnect. I haven't done any heavy traffic use yet, though.
Sounds good. I'll give it a go once I'm back home. There is a small difference in names of the microcode so I probably have to fiddle with that.

UPDATE: Jun 5, 2009
I was able to download about 93 MB (from a total of 163 MB) and then the connection was lost again.

The microcode allready precsent was named [lbm-iwlwifi-3945-2.ucode] so I renamed the microcode from the tar-ball.

---

### Post by Godzemo on 2009-06-04
Yeahhhh so heavy traffic, such as bittorrent or even running update-manager for more than few MB of patches, still kills the connections and requires me to reconnect. At least now it lasts a couple hours of regular use, rather than a couple minutes.

---

### Post by Billingd on 2009-06-04
Hi

I've tried to upgrade the Intel microcode as recommended by Stingx above. Unfortunately I get an "operation not permitted" during the last command. Everything else previous to this line ran correctly. As my Ubuntu is vers 9.04, is there a slight difference required to the script ?

Thanks



David

---

### Post by Godzemo on 2009-06-04
Yep. The last line is missing a 'sudo' at the start :)

---

### Post by FSHero on 2009-06-05
Hi all, I'm about to contribute to this thread a bit later, but I wanted to point some people to a different thread:

[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Some of these guys found installing linux-backports-modules-jaunty solved their problem.

Maybe you guys would like to converse with them?

---

### Post by FSHero on 2009-06-05
I am using Kubuntu 9.04 amd64 on my Dell Inspiron 1525. I did a fresh install of Jaunty, and I am very impressed. I cracked the problem of getting HDMI audio and video output, for instance (both of these were seemingly impossible in Kubuntu 8.04!).

Wireless also appeared to work out-of-the-box... until I noticed problems very similar to those described in this thread:

* Wireless stays connect for unpredictable periods of time: yesterday, I watched a whole episode of Eastenders (30 mins long) on BBC iPlayer, then did other stuff. Later on, after a fresh reboot I connected the laptop to my TV, and the wireless connection cut out within minutes.

* After the wireless connection drops, it is impossible to reconnect. When I click on the Network Management on the Task Manager, I can see my wireless router's SSID. When I click on it, it asks for the WPA-PSK key. (This procedure is so far identical to the one when connecting to the wireless after a fresh reboot). But then it keeps 'working' (circular animation keeps rotating), and this lasts for minutes. I.e. no connection appears to be established.

* Occasionally, the computer hangs: I can move the mouse across the screen, but I the keyboard doesn't appear to work (capslock doesn't do anything) and I can't switch to a console using Ctrl+Alt+F1 or Ctrl+Alt+F2. This hasn't happened when I connect by wired ethernet to my router.

* I think this is related: if the wireless switch at the side of the laptop is 'on' and/or I'm connected to my wireless network, when I shut down the computer, I cannot shut down. It goes past the loading bar to a black screen with white text saying something like "* Will now halt", but the power does not turn off. Luckily, I can tap Ctrl+Alt+Del to restart it, then I just power down the comp using the power button when I reach the grub screen.

Here is the o/p of {dmesg |grep iwl}:

```

minesh@minesh-ins1525:~$ dmesg |grep iwl
[   11.414332] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.414334] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   11.414439] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.414452] iwl3945 0000:0b:00.0: setting latency timer to 64
[   11.414503] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   11.417015] iwl3945 0000:0b:00.0: irq 2298 for MSI/MSI-X
[   11.473420] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.474266] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   21.104912] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   21.222897] Registered led device: iwl-phy0:radio
[   21.222914] Registered led device: iwl-phy0:assoc
[   21.222967] Registered led device: iwl-phy0:RX
[   21.222982] Registered led device: iwl-phy0:TX

```

Then, I tried downloading the microcode from Intel's website, as per the instructions in the current thread (direct link: [http://ubuntuforums.org/showpost.php?p=7363959&postcount=18](http://ubuntuforums.org/showpost.php?p=7363959&postcount=18)). This didn't improve the situation, however. See also the below output of dmesg |grep "iwl3945":

```

minesh@minesh-ins1525:~$ dmesg |grep "iwl3945"
[   11.337885] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.337888] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   11.338000] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.338013] iwl3945 0000:0b:00.0: setting latency timer to 64
[   11.338073] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   11.344840] iwl3945 0000:0b:00.0: irq 2298 for MSI/MSI-X
[   11.401289] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.139699] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[ 1123.002766] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 1123.002790] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000074
[ 1123.004882] iwl3945: Can't stop Rx DMA.
[ 2717.797879] iwl3945: Radio Frequency Kill Switch is On:
[ 2718.210127] iwl3945: MAC is in deep sleep!
[ 2718.210267] iwl3945: MAC is in deep sleep!
[ 2718.210361] iwl3945: MAC is in deep sleep!


```

Some background:
* I haven't messed around with any MTU settings.
* My router is set up as a b/g network, and accepts connections by either of WPA or WPA2.
* My laptop was fine with Kubuntu 8.04 amd64.
* In fact, I specifically bought this laptop for its combination of Intel graphics and Intel wireless, as I thought they would both work out-of-the-box in Linux. (I even phoned up Dell to avoid putting their Dell/Broadcomm chipset, reading about people in forums struggling to make it work.) This makes our situations especially tragic!

Anyone figured it out? I'm going to try to enable backports later, then install the appropriate package.

---

### Post by FSHero on 2009-06-05
Afterthought: I wonder why I am getting the microcode error in dmesg **after** I untar-ed the file into /lib/firmware/`uname -r`/	? Perhaps it's inappropriate for my wireless card?

---

### Post by stingx on 2009-06-07
> **Billingd said:**
> Hi

I've tried to upgrade the Intel microcode as recommended by Stingx above. Unfortunately I get an "operation not permitted" during the last command. Everything else previous to this line ran correctly. As my Ubuntu is vers 9.04, is there a slight difference required to the script ?

Thanks



David

Yep.. I forgot "sudo" before command..

---

### Post by stingx on 2009-06-07
I don't know why you get such error... As for me, wireless worked about 24 hours w/o any problems...

Here is my dmesg output:
```

# dmesg |grep iwl
[   49.965130] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   49.965134] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   49.965323] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   49.492129] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   49.494594] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

```

Maybe, you should try older microcodes from intel??

---

### Post by njtromp on 2009-06-08
Disabling IPv6 seems to help, at least in combination with the latest micro-code as mentioned above. I managed to download about 200 MB and was able to ping a remote server all night long :p.

For disabling IPv6 see [Disbabling IPv6 in Jaunty]("http://webupd8.blogspot.com/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html").

Now it starts to look like a problem in the IPv6 stack :(.

Tonight I will try my old micro-code and the disabled IPv6.

CYa l8r

---

### Post by Godzemo on 2009-06-08
I'm going to give disabling IPv6 a try as well.

---

### Post by Sum Guy on 2009-06-08
Just so you know, after digging around having trouble in 9.04 and 8.10, I saw a problem with this card in another thread, and this code was mentioned (I think this was it) by a member, forgot who:
```
ifconfig wlan0 down
rmmod iwl3945
modprobe iwl3945
ifconfig wlan0 up
```

with sudo before each if you haven't already gotten root access yet, as also mentioned by stingx.

After scripting this for boot up (as is, no sudo command needed) and rebooting, I had a connection.

---

### Post by Godzemo on 2009-06-08
Sum Guy, that will only help if you're having problems with connecting at all due to some issue with the driver at runtime. I think most of us on this thread are talking more about being able to connect, but getting randomly disconnected (and then being able to reconnect, but the disconnect is annoying).

---

### Post by Sum Guy on 2009-06-08
OK, my mistake.

---

### Post by FSHero on 2009-06-10
Here is an update on my progress... unfortunately, I didn't make notes during my messing around (I felt lazy :S), but the below is largely correct.

I installed linux-backports-modules-jaunty. I didn't notice any improvement in wireless reliability, and my computer still failed to shut down when commanded to. However, I did notice the following in dmesg (extract below):

```

[   21.105077] iwl3945 0000:0b:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   21.159273] iwl3945 0000:0b:00.0: loaded firmware version 15.28.2.8
[   21.202297] Registered led device: iwl-phy0::radio
[   21.202314] Registered led device: iwl-phy0::assoc
[   21.202367] Registered led device: iwl-phy0::RX
[   21.202381] Registered led device: iwl-phy0::TX
[   21.224561] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

So it looked like it was loading the firmware. Now, I decided to update the firmware. KPackageKit reveals that the file lbm-iwlwifi-3945-2.ucode is located in /lib/firmware/2.6.28-11-generic. Therefore, as per [these instructions]("http://ubuntuforums.org/showpost.php?p=7363959&postcount=18") I copied the firmware into this location (and renamed it: I added "lbm-" to the beginning).

After restarting (so loading the new firmware), the dmesg extract said:
```

[   17.514734] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9 

```
Now, when I told my laptop to shut down, it **did** shut down successfully. I was thus tempted to finish here... but I think I was still experiencing dropouts of connection -- I think that after the computer woke up from a standby, it wouldn't list any access points, or failed to connect if it did list.

After reading around, I decided to try WICD, an equivalent to NetworkManager. I installed the repository version. And, 'touch wood', things seem fine now! I haven't experienced a drop out yet AFAIR(emember). My computer can shut down, and I feel I have more control over the network adaptors using WICD (e.g. I can disconnect from a wireless -- I could not see any such option in the KDE NetworkManager plasmoid).

If I still have connection problems, I'll disable ipv6 as others have.

This is puzzling... if using WICD fixed my problem, but disabling ipv6 fixed everyone else's problem, then does that mean my problem with my wireless card was fundamentally different??

---

### Post by Godzemo on 2009-06-10
Not necessarily. I got improvements when I switched to Wicd... but the improvements weren't good enough :p

Everything I've done so far (installing Wicd, disabling IPv6, updating the microcode) has improved my connectivity, but I still get dropouts... just, more sparsely.

---

### Post by FSHero on 2009-06-12
@Godzemo: did your wireless work fine in any previous versions of Ubuntu? Because mine worked pretty much fine with Hardy...

---

### Post by Godzemo on 2009-06-12
Mine's been on and off over versions... I had the same problems with Hardy though, iirc. I don't trust my memory on this, though, so neither should you :p

---

### Post by guitodd on 2009-06-13
Wow.. I'm on a Hardy LTS upgrade and am having the random disconnect issue too.  Spent hours searching forums and Intel's bugzilla.. depressing.  All threads lead to no solid solutions and each person seams to be having a slight variation of the same issue.

---

### Post by rbond on 2009-06-28
Posting in case this helps someone. I have been following a few wifi related threads because I had problems with wifi after upgrading to Jaunty.

In the past I had manually setup my wifi WPA settings in the /etc/network/interfaces file. Then I started using the Gnome Network Manager. My manual settings did not cause a problem until I upgraded to Jaunty. Just for the heck of it I removed the manual settings from my file and it fixed the problems that I had. 

I know that for some people this is a kernel issue, but for me it turned out to be a problem with Gnome Network Manager not liking my config settings.

If you are having problems and you had previously manually configured settings, back up your current copy and try to revert to only auto settings such as this....

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface wlan1 inet dhcp

auto wlan1

```Hope this helps someone.

Forgot to note this: For the newbies - the eth1 and wlan1 values may be different on your machine. Use the network interface names for your machine.

---

### Post by GunsNRoses on 2009-07-20
Hello guys, I just wanted to say thank you, updating the firmware did the trick for me. Interestingly enough I didn't have the problem with versions prior to 8.04, after upgrading wireless at work started disconnecting. I also disabled ipv6 and installed linux-backports-modules-jaunty, but I'm pretty sure the firmware fixed the problem. Again thanks for the invaluable help, this thread is a gold mine.

---

