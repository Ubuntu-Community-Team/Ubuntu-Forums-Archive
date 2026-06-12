---
title: "Atheros AR5B93 Wireless Laptop connection not recognized 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by harry003 on 2010-05-07
I have been living with, for about a week, an on-again, off-again ethernet connection on my nice new Acer 5534 laptop with Atheros AR5B93 internal wifi card.

I really need to be able to connect wirelessly in Ubuntu, but it just ain't happenin.

This is a software problem, not hardware, because I can connect properly, either way, when I boot into Windows, but not here.

I have scoured this forum and stumbled through various "fixes" but none worked. I check Update Manager every few days to see if a wireless fix is forthcoming, but nothing yet.

If you post a reply, I would appreciate it if you would explain each step to a Ubuntu newbie, I am starting to see the light but it is still foggy.

thanks in advance.

---

### Post by chili555 on 2010-05-08
Perhaps this will help you: [http://ubuntuforums.org/showthread.php?t=1414590&highlight=AR5B93](http://ubuntuforums.org/showthread.php?t=1414590&highlight=AR5B93)

See posts number 4, 5 and 6.

Simply hook up an ethernet cable, connect and then open System > Administration > Synaptic. Under Settings > Repositories, enable everything under Downloadable from the internet. Press Reload.

Now search for and install linux-backports-modules-wireless-generic and linux-backports-modules-lucid-generic. Several dependencies will be added. Install and reboot. Give us your report so the searchers will also learn.

---

### Post by harry003 on 2010-05-08
Chili - 

Thank you so much for your reply. Unfortunately, I have been there and done that. Along with several other "solutions" that did not work.

Here are a couple of other items:

occasionally, when I first boot up, I get a black rectangular "dialogue box" in the upper right of the screen that says something like "wireless connection available - click here to connect" but when I move my mouse over it, it just blurs out and nothing happens.

Under Systems/Preferences/Network Connections the "wired" connection shows auto eth0, but all the other tabs are blank. Under the "Wireless" tab I can click "add", and under that "connect automatically" is checked but there is never anything there.

I have followed other instructions to do "makes" "gets" "installs" etc for Madwifi and others, but nothing ever seems to work. I hate the idea of having dead installation garbage all over my hard drive, one of the reasons I want to get away from Windows, but for now I just need a wireless connection.

Have you got any more suggestions?

ps- I am a big vinyl fan, too.

---

### Post by chili555 on 2010-05-08
I read no mention of your Network Manager icon. Please see here: [http://ubuntuforums.org/showpost.php?p=8784752&postcount=5](http://ubuntuforums.org/showpost.php?p=8784752&postcount=5)


PS - Vinyl roolz! Especially on my Linn Axis/Origin Live Silver/Ortofon 2M Bronze.

---

### Post by harry003 on 2010-05-08
Days ago that icon was there, but it is gone now. I do have an icon that is obviously the ethernet plug, but not the wireless one. 

I followed the 2 listings you gave, but neither of them brought it back.

The wireless works perfectly in windows, so I know that this is a linux driver or installation problem.

*****

I wish I had a really nice table. I have several hundred jazz and rock records that I collected mostly in the 60s, 70s and 80s, and I love the sound. I have a late-80s Technics direct drive with a pretty decent Audio Technica cartridge.

---

### Post by chili555 on 2010-05-08
> I do have an icon that is obviously the ethernet plug, but not the wireless one.I think the ethernet plug icon is the Network Manager icon; it looks like an ethernet plug when the ethernet is plugged in and, I believe, has an IP address. Unplug it and let the system notice a change of state and then left click the icon and see if you see wireless networks.

--------------

Those old Technics have a new cult following, especially the SL-1200. Spin a few tonight and we'll fix your wireless.

---

### Post by jon zendatta on 2010-05-08
yes I have the same laptop as Harry & the same problem. Managed to get updates using an ethernet cable, but was never able to connect to the internet & open web pages.:mad:

---

### Post by jon zendatta on 2010-05-08
Ignore that last post. My problem is solved, after all updates I forgot the final ingredient -> reboot:KS

---

### Post by harry003 on 2010-05-08
Chili - 

I took your advice and things are moving - in the wrong direction!

After unplugging the ethernet cable and refreshing, the 2 TVs with the red X did indeed come on to replace the plug icon. And in the network connections dialogue, as always, the "wireless" tab was blank. Clicking "add" gave me nothing, even though it says it is going to automatically connect.

Worse, now my ethernet connection is dead too, and its tab is also blank where it used to show auto eth0.

Rebooting into Windows 7 gives me a clean fast connection as always, that is how I am here, and so any new attempts will require reboots, etc.

I wish I COULD listen to some records tonight. I am stuck out of state on a long-term business deployment (why I bought the laptop - all I have is a good collection of MP3s to play on laptop speakers or moderately OK Sony headphones!) and am at the mercy of hotel networks and connections.

You got any more ideas for Jon and me?

I really appreciate your time and concern.

---

### Post by harry003 on 2010-05-08
Unlike Jon, I have been updating (or asking to) every 2-3 days, as well as running sudo apt-get update and apt-get upgrade regularly.

I have had the laptop for almost a month and the wireless has never worked under Ubuntu, but never any problem under Windows. Windows 7 came installed, and I carved out a 20GB partition for 10.04 (then beta) to dual-boot.

It did seem like around the time of the final release (April 29 was it?) it slowed down and seemed more fussy, but the hotel connection is flaky, too.

---

### Post by harry003 on 2010-05-08
is ndiswrapper something that I should try if I can connect again?

can I run it directly from Synaptic?

---

### Post by jon zendatta on 2010-05-10
Once again I cannot access the Internet, but can update with apt-get and install software using Synaptic. 
Chili55 could you please be more specific regarding **linux-backports-modules-wireless-generic** & **linux-backports-modules-lucid-generic**. As one of these fixed my system two days ago, but one also borked my system. As unfortunately I had to reinstall 10.4 so I don't know which package was the culprit.

---

### Post by chili555 on 2010-05-10
I would try *linux-backports-modules-lucid-generic* first. See if it kicks your wireless to life and you can always remove it from recovery mode if it is detrimental.

---

### Post by jon zendatta on 2010-05-10
Oh and **resolvconf** doesn't resolve anything. May have to test some other distro's today

---

### Post by jon zendatta on 2010-05-10
Just noticed your post chili555, I'll take a look & reply in an hour:KS

---

### Post by chili555 on 2010-05-10
> **jon zendatta said:**
> Oh and **resolvconf** doesn't resolve anything. May have to test some other distro's todayWhat does it say?```
cat /etc/resolv.conf
```

---

### Post by harry003 on 2010-05-10
harry@harry-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 4.2.2.1
nameserver 172.16.0.1
harry@harry-laptop:~$

It looks like the forums are swamped with 10.04 wireless problems. I am going to be in a position to not have to worry about it for a week or so, is there a chance that this global problem will see some light in that time?

---

### Post by chili555 on 2010-05-10
> is there a chance that this global problem will see some light in that time?There are quite a few, but it's hardly global. For example, I have four different wireless cards; all connect easily in either of my Lucid laptops. A buddy stopped by yesterday and bet me I couldn't connect in two minutes or less with an unknown USB dongle which he pulled out. I won the bet.

It is difficult to know if it's the driver, Network Manager or:> the hotel connection is flaky, too. Your /etc/resolv.conf looks pretty normal; it confirms that you have actually connected. I did notice that the 4.2.2.x entries are pingable; 172.x is not. I wonder if it may be contributing to your flakiness. You might try commenting it out:```
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 4.2.2.1
#nameserver 172.16.0.1
```See if anything improves.

I also suggest you wait until you get to a known good signal and we continue troubleshooting.

---

### Post by harry003 on 2010-05-10
Those instructions did nothing but return "command not found"

To clarify:

I have never connected wirelessly on this computer under Ubuntu. In System/Preferences/Network Connections the "wireless" tab has always been empty, and "add" does not add. 

Ethernet connection is OK, when I refer to the hotel being flaky I mean that their ethernet goes down every couple of days and I have to call the front desk and ask them to reset the modem. I must be about the only one using a wired connection because the wireless network is faster (blazingly fast - compared to my Bellsouth DSL on my monster desktop at home).

All the stuff I have done the last couple of days has added a 2nd wired connection (auto eth1 and Auto eth1 - only the capital A is different, go figure) but no wireless connection.

In Windows these are all the classic symptoms of a bad or missing driver.

I'm sorry that the timing of our Q&A is bad, I can only work on this during the early hours of the evening.

---

### Post by jon zendatta on 2010-05-11
```
/etc/resolv.conf
# Generated by Network Manager
nameserver 10.1.1.1
```

---

### Post by chili555 on 2010-05-11
> **jon zendatta said:**
> ```
/etc/resolv.conf
# Generated by Network Manager
nameserver 10.1.1.1
```May I assume that is your router?

---

### Post by harry003 on 2010-05-11
Chili - 

In post 18 you said that I had indeed connected.

Where/how do I make this mean something? If I unplug my cable, every message tells me that I am not connected (even after rebooting). The button on the computer does not seem to turn the antenna off and on.

Systems/Preferences/Network Connections does not list a wireless connection under the wireless tab.

I feel like I am extremely close to having a working system, and I know the hardware is good because it works perfectly in Windows.

What else can I try?

---

### Post by chili555 on 2010-05-11
I think you were connected with the ethernet and not wireless. Let's get back to basics. Please post:```
iwconfig
dmesg | grep ath
```Thanks.

---

### Post by harry003 on 2010-05-11
Here is what I get:



harry@harry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harry@harry-laptop:~$ dmesg | grep ath
[    1.305188] device-mapper: multipath: version 1.1.0 loaded
[    1.305192] device-mapper: multipath round-robin: version 1.0.0 loaded
harry@harry-laptop:~$ 



I am plugged in to the ethernet and this works fine in general.

---

### Post by jon zendatta on 2010-05-11
very weird. my problem is solved by changing web browser, so I'm now accessing the internet via konqueror instead of firefox. must of been some gui issue

---

### Post by harry003 on 2010-05-11
I have used Firefox for a few years after IE since I started with Windows over a decade ago.

Generally I have been happy and have not felt any need to change.

Mostly I would be irritated at having to climb yet another learning curve to circumvent an unnecessary software inadequacy. But why am I complaining, this is all free stuff and these are all selfless volunteers just trying to help pitiful newbies like me.

---

### Post by chili555 on 2010-05-11
No module is loading automagically; I wonder why. Let's load it by hand and see what, if any complaints we get from the kernel:```
sudo modprobe ath9k
dmesg | grep ath
iwconfig
```

---

### Post by harry003 on 2010-05-11
way over my head. does this tell you anything?



harry@harry-laptop:~$ sudo modprobe ath9k
[sudo] password for harry: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blackllist, it will be ignored in a future release.

harry@harry-laptop:~$ dmesg | grep ath
[    1.305188] device-mapper: multipath: version 1.1.0 loaded
[    1.305192] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 6130.768563] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6130.768579] ath9k 0000:02:00.0: setting latency timer to 64
[ 6131.205466] ath: EEPROM regdomain: 0x65
[ 6131.205470] ath: EEPROM indicates we should expect a direct regpair map
[ 6131.205478] ath: Country alpha2 being used: 00
[ 6131.205481] ath: Regpair used: 0x65
[ 6131.260125] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 6131.261403] Registered led device: ath9k-phy0::radio
[ 6131.261434] Registered led device: ath9k-phy0::assoc
[ 6131.261462] Registered led device: ath9k-phy0::tx
[ 6131.261492] Registered led device: ath9k-phy0::rx

harry@harry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
harry@harry-laptop:~$

---

### Post by chili555 on 2010-05-11
> wlan0 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power ManagementffIt created a wireless interface. Can you detach the ethernet cable and try to connect?

Let's get the module to load on boot:```
sudo su
echo wl >> /etc/modules
exit
```

---

### Post by harry003 on 2010-05-11
I truly appreciate the time ad effort you have devoted to this, but still no dice.

I did what you said, and rebooted, but no connection until I plugged in again.

Am I the only one having this problem? I do not want to end up like Jon and change to a new browser from Firefox just to get a wireless connection.

I'm done for the night. Maybe tomorrow.

Thank you again.

---

### Post by Carsten_Franz on 2011-03-27
Well thanks a lot! This procedure worked on my Acer 1830TZ with the named wireless hardware!

---

