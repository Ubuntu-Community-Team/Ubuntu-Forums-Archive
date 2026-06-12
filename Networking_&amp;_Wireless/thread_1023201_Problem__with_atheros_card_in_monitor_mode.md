---
title: "Problem  with atheros card in monitor mode"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by DeepSeaNautilus on 2008-12-27
Hello. I want to use aircrack to crack my own wireless network (wpa-psk).
The problem I have is that when I put my atheros card in monitor mode, it does not capture any packets.

 The output of the lspci command is:
```
04:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

My is card is an Airlink 101 superG with chipset awlh4130. 
I downloaded madwifi tools using apt-get install and then aircrack from synaptics. 
When I put my card back in managed mode, it detects my AP`s SSID, so in monitor mode it should at least detect it too. The output of iwconfig command in managed mode is:
```

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
 Any help will be greatly appreciated.

---

### Post by pytheas22 on 2008-12-27
Your card is still in managed mode according to the output above.

To put it into monitor mode, try typing:
```

sudo airmon-ng start wifi0
```

I think this will work, but I'm not positive.  If not, try:
```

sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
sudo ifconfig ath0 up
```

The madwifi (Atheros) drivers handle monitor mode in a non-standard way, so if you're following generic aircrack instructions, that's probably what's wrong.  Once you get the card into monitor mode, however, the rest of aircrack should work normally.

To verify that your card is in monitor mode, run the command 'iwconfig' and look for:

```
ath0      IEEE 802.11g  ESSID:"David"  Nickname:""
          **Mode:Monitor**  Frequency:2.417 GHz  Access Point: 00:21:7C:54:9E:31   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:60B4-85DC-78BD-2189-8D91-C432-8CF5-1650   Security mode:restricted
          Power Management:off
          Link Quality=5/70  Signal level=-86 dBm  Noise level=-91 dBm
          Rx invalid nwid:95  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by DeepSeaNautilus on 2008-12-28
Sorry, I originally was in monitor mode, but I had to put it back in managed mode to connect to the internet and write the post and I didn't save the right output. ( I edited my first post with the right output)

I used the commands you told me. When I type 
sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
it creates ath1 interface instead of ath0, I do not know why does that happen.

```
root@david-desktop:/home/david# wlanconfig ath1 destroy
root@david-desktop:/home/david# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

root@david-desktop:/home/david# wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ath0
root@david-desktop:/home/david# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Anyway, if I choose ath1 instead of ath0 to capture packets, I try to capture packets with command airodump-ng -w file -c2 ath1, ( I know the ap is transmiting in channel 2) 
I capture no packets, just like the output shows:
```
 CH  2 ][ Elapsed: 2 mins ][ 2008-12-28 12:04                                    
                                                                                 
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSI
                                                                                 
                                                                                 
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes   
```
If I try with airodump-ng -w file -c2 wifi0, the same thing happen.
Also, when I am in managed mode, the network icon thats on the left of the volume icon shows the wireless networks option, but when I am in monitor mode, it doesn't.

---

### Post by pytheas22 on 2008-12-28
hmmm, that's strange.  Do you see anything if you just run airodump with:
```

sudo airodump-ng ath0
```

so that it will hop all channels?

Also, before starting airodump, kill Network Manager by typing:
```

sudo killall NetworkManager
```

Sometimes NM can interfere with airodump because it tried to put your card back into managed mode.  This could be the problem here.  (To bring NM back when you're finished with airodump, type 'sudo NetworkManager'.)

Also, did you try using airmon-ng to start your wireless card in monitor mode?

If none of this helps, you may want to install Wireshark to see if you can sniff packets using that program, instead of airodump.  This will help diagnose whether the problem is specific to airodump or a result of a larger problem.

---

### Post by DeepSeaNautilus on 2008-12-28
Yes its really strange. I googled if others had the some problem of getting ath1 instead of ath0, and it results that its a common problem with atheros cards, but in the forums I searched they didnt give a solution for it. the thread is this [http://tinyshell.be/aircrackng/forum/index.php?topic=2044.0](http://tinyshell.be/aircrackng/forum/index.php?topic=2044.0)
At the end a user recommends adding a line to /etc/modules.d/options file, but I don't have it in my system. So I don't know if I should create it or do something else.
They say that when ath1 is created, it does not only changes the name of the interface, but changes the mac of the original card, so this is probably why it cant capture any packets even when it is in monitor mode, what do you think?

I used this commands in monitor mode logged as root:
```
killall NetworkManager
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor

```
( here is where the strange thing happens, if I choose monitor mode, it creates ath1 instead of ath0 in monitor mode, but if I type sta instead of monitor it creates ath0 in managed mode)
Since ath1 was the new interface created I refered to it in the following commands

```
ifconfig ath1 up
sudo airodump-ng ath1
``` ( it keept on multiplexing the channels but could not read any packets)
```
wireshark
```
( the GUI opened and I chose interfaces to select ath1, but it showed that it was not reading any in any interface )
Anyway I chose it and no packets were captured.
I closed wireshark and destroyed ath1 interface, then I used the following commands to use airmon instead of wlanconfig:
```
airmon-ng start wifi0. 
ifconfig ath1
```
( This has the same problem than wlanconfig, it creates ath1 instead of ath0 ) I believe that the reason is that airmon-ng doesn't create the interface by itself, but calls wlanconfig )

Thanks for the help :)

---

### Post by pytheas22 on 2008-12-28
I don't actually think that having the device named 'ath1' instead of 'ath0' is anything to worry about.  I've had that behavior in the past with my Atheros card, but airodump still worked fine.

The only other reason I can think of why you shouldn't see your router is that possibly it is operating in a mode that your card can't see (although I think it should see all modes when sniffing, but I could be wrong).  If it's on 11b or 11n mode, could you try changing it to 11b?  Also, try changing it to channel 6--sometimes there are issues seeing routers operating on the higher channels.

If your computer is portable, can you bring it somewhere with lots of different wifi networks to see if airodump picks up on any of them?

You might also want to try using a distribution built especially for aircrack-related stuff.  I think that the aircrack site has some ISOs, or there are distributions like [Whax]("http://iso.linuxquestions.org/whax-linux/whax-linux-3.0/").  These should come with all the drivers issues sorted out beforehand and optimized for aircrack.  Do you have better luck there?

Also, if this is a problem specific to your particular model of Atheros card, it might be worthwhile to google around for the PCI ID.  To find it, look at the output of the command 'lspci -nn' (the '-nn' flag is important).  The PCI ID is eight hexadecimal characters that look like 1234:ABCD.  What's yours?

---

### Post by 2hot6ft2 on 2008-12-28
> **pytheas22 said:**
> 
You might also want to try using a distribution built especially for aircrack-related stuff.  I think that the aircrack site has some ISOs, or there are distributions like [Whax]("http://iso.linuxquestions.org/whax-linux/whax-linux-3.0/").  These should come with all the drivers issues sorted out beforehand and optimized for aircrack.  Do you have better luck there?
Along those lines you might find an answer here. 
[http://forums.remote-exploit.org/index.php](http://forums.remote-exploit.org/index.php)

I boot BT3 off a 2GB SD card live with changes. For what you're trying to do it may be worth looking into. You could do it using their livecd. I'm not familiar with your card or chipset but I'll bet they are.

Here's their download page. [http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)

---

### Post by al_mckin on 2008-12-28
I'm using the same atheros chip with no problems here in monitor mode.  However, I have seen the card behave strangely from time to time and stop receiving packets.  I usually unload/reload the driver and that seems to work.

I'm using svn revision r3878 rather than the version in linux-modules-restricted (0.9.4) which I think is still the current version.

You're right about airmon-ng, it does use wlanconfig in the same way you talked about.

There is one other thing you can try:

```
sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=monitor
sudo ifconfig ath1 up 
```

This will cause the madwifi driver to create only one interface which will be in monitor mode.  It will not receive and packets until to run ifconfig ath1 up on it.

---

### Post by DeepSeaNautilus on 2008-12-29
My ap is currently in mode 802.11b, since it has a larger radio than 108.11g and my desktop computer is very distant from my ap. I downloaded wifislax and I will see if my card works with it. The pci id for my card is 168c:0013
The ap is currently working with channel 2, I changed it to channel 6 but I lost the signal even in managed mode, and in monitor mode I could not capture any packet.

---

### Post by pytheas22 on 2008-12-29
I'd bet that your AP being in 11b mode has something to do with it.  Did you try switching to 11g just to see?

Also, [according to Wikipedia]("http://en.wikipedia.org/wiki/802.11#802.11g"), both 11b and 11g give the same range (~35 meters).  Are you sure that 11b gives you a better signal?

---

### Post by DeepSeaNautilus on 2008-12-29
> **pytheas22 said:**
> I'd bet that your AP being in 11b mode has something to do with it.  Did you try switching to 11g just to see?

Also, [according to Wikipedia]("http://en.wikipedia.org/wiki/802.11#802.11g"), both 11b and 11g give the same range (~35 meters).  Are you sure that 11b gives you a better signal?
In theory 11b and 11g give the same range, as you say. But in practice Ive noticed that when I`m using 11g my signal is in 5-7%, and when using 11b my signal is 7 - 12%. This is the best I`ve got moving the antenna and the ap in many positions.

---

### Post by pytheas22 on 2008-12-29
> In theory 11b and 11g give the same range, as you say. But in practice Ive noticed that when I`m using 11g my signal is in 5-7%, and when using 11b my signal is 7 - 12%. This is the best I`ve got moving the antenna and the ap in many positions.

I always had issues with madwifi under-reporting signal strength on my card--even if positioned only a few feet from the router and with excellent latency and transfer rates, it never reported signal strength higher than around 60%.  This is just to say that you shouldn't necessarily believe signal-strength readings; the only thing that really matters is whether your data is being transferred at an acceptable rate.

You could also try using ath9k instead of madwifi; maybe it would improve the situation.

I googled around for your PCI ID and couldn't find anyone else having trouble with this card on aircrack.  I really think you should try putting the router in 11g mode to see what happens.

Also, you could probably just take a packet dump in managed mode of an association between your Atheros card and the router.  If all you're trying to do is crack WPA on your own router, you just need to capture the four handshake packets and I don't think you need to be in monitor mode to get those from your own computer.  airodump probably won't allow you to create a dump unless you're in monitor mode, but I think Wireshark will.

---

### Post by DeepSeaNautilus on 2009-01-03
Hello. I downloaded wifislax 3.1 and used it with my atheros adapter. I could succesfully put my card in monitor mode and scan the traffic of three networks, my own wpa-psk network  and two wep networks. But I really prefer using ubuntu to do network tasks instead of using another SO for this sole purpose, so I downloaded the madwifi driver for my netbook and I could put in in monitor mode in ubuntu, for that, I used the following commands:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
wget "http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz"
tar -xzvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3861-20080903
cd scripts
./madwifi-unload
./find-madwifi-modules.sh $(uname -r)
cd ..
make && make install && modprobe ath_pci
```
so I am going to recompile the madwifi driver of my desktop computer to see if this solves it. I am going to come back to post the results.

---

### Post by DeepSeaNautilus on 2009-01-04
Hello again. I compiled the drivers again and the problem of ath1 getting created instead of ath0 is solved. I put my card in monitor mode in ubuntu without problems.
Thanks for the help. ;)

---

