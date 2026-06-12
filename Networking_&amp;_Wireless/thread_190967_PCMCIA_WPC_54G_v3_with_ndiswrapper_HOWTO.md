---
title: "PCMCIA WPC 54G v3 with ndiswrapper HOWTO"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by nzruss on 2006-06-06
Added Sunday 27 May 07, 1:22pm:

I'm totally tired of the Linksys WMP54G and have had nothing but headaches getting it to use WPA each time i've set it up. In Feisty this card is recognized off the bat, but will not do WPA without some massaging, which usually breaks network manager in the process. 

I highly recommend **getting the D-link WDA-1320** instead. I've switched all my Ubuntu machines to this card, and it works with WPA out of the box, albeit with a restricted driver, but there is no setup beyond entering your wpa passphrase. I manged to get the D-link WDA-1320 for $39. I'd even mow lawns to earn the $39 before I'd spend another second on the WMP-54G. Until Linksys open their drivers and provide good linux wpa support, i'm steering clear of their products. 


The how-to below might still be of some use if you're into a bit of self inflicted punishment. 

-------------------------------------------------

After I wrote the origional how-to, I did a fresh install and found that there is an easier way to get wireless up and running, and this way offers WPA, WEP etc, by using the Network managar which makes things super easy.  

First enable your universe and multiverse repositorys, by clicking > system > administration > Synaptic Package Manager. Then click the Settings tab, and select all the available repositorys. Click OK and exit. 

Wait a few seconds and you might get a few updates. Update your system.

Now click "applications > "add/remove", and in the search box type "network manager". Look for Network manger (for gnome), then 'check' it and click "Apply". It should have a few dependencies which will install automatically. 

Once installed, you should see the network managers icon in your task bar. (If not, you may need to reboot (i think i did) - save this page to your desktop first) 

When you click the new network manager icon you should see "wired network" and "wireless networks". If you have already installed your wireless driver, it should show up and allow you to select it. 

My system detected my wpa network, and once selected asked for the pass phrase. Either type your pass-phrase, or paste the pre-shared key. (Make sure you note the first and last characters of your PSK before and after the paste. When I pasted, an exta non-ascii character appeared at the end, that I simply deleted). 

You may also need to enter a password for your "key-ring", and your done. 
[B]
[COLOR=Red]* THAT IS IT!!!!!*[/COLOR][/B]
-----------------------------------------------------------------------------------------------------
If it doesnt detect your wireless card, you can do the following: 

Try rebooting, or install the wireless card using ndiswrapper (a clever piece of software that uses your windows driver on your ubuntu system)
 
Ok, heres the steps:

This will blacklist bcm43xx, and load ndiswrapper. (If you aren't sure what any of the commands are, just type 'whatis ' followed by the name of the command, such as "whatis gedit").  This will work for any Linksys PCMCIA wireless card, you will just need to change the driver name in the steps below. Should work for other brands of card, but you can always check the forum for a better way....

Stick the Linksys CDROM for your wireless card in your CDROM drive and Browse to the /Driver/NT folder. There should be two or three files in there (your looking for the .inf and .sys files). Drag the whole NT folder to your Desktop.

Next we will open the terminal and blacklist the broadcom driver, and also remove it from the kernel. The last line unloads any ndiswrapper that you might already have running from previous attempts.

```

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper

``` 
Next, we make sure your sources.list has all the universe and multiverse repo's enabled, if you havent done so already:

```
  
sudo gedit /etc/apt/sources.list

``` 
Remove the '#' next to the universe and muliverse repo's, save and exit.   

Then we make sure everything is up to date; and add ndiswrapper.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ndiswrapper-utils

``` 
Next we will get your .inf files that should be on your ~/Desktop/NT folder and load them to ndiswrapper. My ".inf" file was called "**LSBCMNDS.inf**" but yours may be different (so change the filename and created directory in the next step accordingly). 

We are about to navigate to the directory, load the .inf to ndiswrapper, and then navigate to the created driver files, and do this by:

```

cd ~/Desktop/NT/
sudo ndiswrapper -i **LSBCMNDS.inf**
cd /etc/ndiswrapper/**lsbcmnds**/

``` 
During that you should have seen something about forcing RadioState (four lines)
 
Now that we have ndiswrapper configured, we can load it to the kernel by:

```

sudo modprobe ndiswrapper

``` 
We also want to add ndiswrapper to load at startup. I found the standard append command wouldnt work so I did it the 'long way' by:

```

sudo gedit /etc/modules

``` 
Type "ndiswrapper" at the end of the file (after mouse and cp)

You can check that its scaning ok by:
```

sudo iwlist **wlan0** scan

``` 
I rebooted, and my network manager recognized my wifi card!!! 

**[COLOR=Red] Hope that helps!!!  - fill in the survey at the top![/COLOR]**



There is always the [https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

---

### Post by mozetti on 2006-06-10
Excellent How-to, and it got my WPC54G v3 PCMCIA card working with zero troubles. Very easy to follow, and it changed my mind about using ndiswrapper. Some of the other walk-throughs seemed pretty tedious, but it turns out it wasn't so bad.

Thanks!

---

### Post by corrinewinslow on 2006-06-23
Thanks. 

The default installed BCM43xx driver did not work.

With Ubuntu 6.06 (with updates) and a WPC54G v2 your instructions worked perfectly. I also loaded wpa_supplicant and was able to connect wirelessly with WPA TKIP.  Much appreciated, you got my vote.

---

### Post by TFX360 on 2006-06-23
Hello all! Poster,

What often is missed is the wpa_supplicant configuration. Especially in Ubuntu because eth0 is seen as wlan0 (At least here it is? Kernel?). I haven't used WEP since the middle ages. If anyone is having problems with wpa_supplicant after this very good walkthrough feel free to ask. I do not know if there already is a walkthrough for this. I'll be happy to write one.  Most forget to blacklist bcm43xx, wich without it just won't work, good job!

My Hardware:
WPC54G v1.2

Ndiswrapper (didn't work for you?):
sudo -i (the command won't work without this!!)
echo ndiswapper >> /etc/modules

sudo modprobe ndiswrapper (where is this saved?)

Driver version 2.0 (use this one for ver 1.2!!!): lsbcmnds.inf / bcmwl5.sys

Updates & Kernel: 2.6.15-25-386 
code: sudo apt-get update; sudo apt-get upgrade; **sudo apt-get dist-upgrade ** (last one is Kernel afterwards needs reboot!) code: sync; sleep 10;shutdown -r now)

iwconfig eth0 (wierd eh should be wlan0!?)

eth0      IEEE 802.11g  ESSID:"Secrett"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:XX:XX:XX:XX:XX
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-46 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan:

(Configured through wpa_supplicant, wpa_passphrase; /etc/wpa_supplicant.conf (last one is created by yourself)

eth0      Scan completed :
          Cell 01 - Address: 00:XX:XX:XX:XX:XX
                    ESSID:"Secret"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-29 dBm  Noise level:-256 dBm                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Have a slight problem.. after hybernate/suspend it doesn't come up again.


Hope it helps someone!


Greetings,


TFX.

---

### Post by nzruss on 2006-06-24
[QUOTE=TFX360]

What often is missed is the wpa_supplicant configuration. [/QUOTE]

I hear what your saying, but when you install network manager, it installs wpa_supplicant as a dependency and configures it for you. (the network manager simply asks for your wpa passphrase, and wa-la its done. 

There is no need to configure wpa_supplicant manually unless your having some serious issues.

---

### Post by TFX360 on 2006-07-02
[QUOTE=nzruss]I hear what your saying, but when you install network manager, it installs wpa_supplicant as a dependency and configures it for you. (the network manager simply asks for your wpa passphrase, and wa-la its done. 

There is no need to configure wpa_supplicant manually unless your having some serious issues.[/QUOTE]


Missed that, very good! Will install networking tools! Should be standard in Ubuntu anyways, wireless is hard enough for most people.

Edit: I installed it, rebooted, reinstalled ndiswrapper config/drivers, configged, internet is working again, network manager says No network connection?! Should I completely remove ndiswrapper? And then reconfig?

Thanks for this great walk through! :D

---

### Post by Meshuggah27 on 2006-07-02
Omfg!!!!!!!!!!!!!!!!!!!!!!

You Are God My Friend!!!!!!!!!

*bows* *bows*

Thank You So Much This Guide Is Great!

---

### Post by Meshuggah27 on 2006-07-02
Still doing the same thing for me.  Detects my wireless network but now it doesnt even show up in the network manager but it shows up in the network config.  and ndiswrapper says its present.  Now the link light on the card is actually blinking too.  WTF! :(

Also,  It freezes in the ubuntu startup when 'Configuring network interfaces.  It just locks up,  I gave it like 3 minutes to try and load.  It also locks up alot if i get into ubuntu.

---

### Post by Meshuggah27 on 2006-07-02
Tried my netgear wifi card again and it worked perfectly.  Doesnt show up in the network manager but it works with WEP.  Weird o.o

If someone can tell me how to make it show up in network manager,  It would be greatly appriciated ^^

---

### Post by TFX360 on 2006-07-02
[QUOTE=Meshuggah27]Tried my netgear wifi card again and it worked perfectly.  Doesnt show up in the network manager but it works with WEP.  Weird o.o

If someone can tell me how to make it show up in network manager,  It would be greatly appriciated ^^[/QUOTE]


Can't do anything for you without some output.

Version of your WPC? Driver version have you downloaded?
iwconfig
dmesg
ndiswrapper -l

I have version 1.2 with driver version 2.0 working without network manager. Network manager says No Network Connection. So that doesn't work for me (either).


Greetings,


TFX

---

### Post by oss_monkey on 2006-07-28
You are a god! Thank you so much for this really easy HowTo!

I was so worried when the fwcutter method didn't seem to work for me. All I did was follow your instructions and bam! WiFi is here to stay! One less cable for this laptop. :)

On a side note, I'm using XFCE so I didn't have NetworkManager, but something called Networking in Applications -> System. Maybe some other people can benefit from this tidbit of experience. I did install network-manager, though. I just couldn't seem to encounter the dialog any which way. :)

Thanks again.

---

### Post by dweasel79 on 2006-08-05
Worked for me.  The bottom half that is.  But none the less still wireless :D

---

### Post by ghackett on 2006-08-07
The bottom half worked like a charm for me.  I just did a fresh net install on an IBM Thinkpad 240, and the bottom half got my linksys WPC54G v3 working like a charm except for one thing. I haven't been able to get Network Manager working.  It show my available hotspots, but can't connect.  So I went into System/Administration/Networking, and it said that wlan0 was not active.  I hit properties, chose my access point (from another list of availible ones), chose DHCP and BAM, wireless up and running. Hope this helps people that might be stuck.

---

### Post by Praxidike on 2006-08-07
^^ never mind, got it working, finally! :)

---

### Post by OlaNordmann on 2006-08-17
Thank you so much :D

> I haven't been able to get Network Manager working. It show my available hotspots, but can't connect.
I had the same problem, untill after I read this thread:
[http://ubuntuforums.org/showthread.php?t=192220]("http://ubuntuforums.org/showthread.php?t=192220")

---

### Post by quartz on 2006-08-27
Great job with this howto. This worked like a charm with my wpc54g v3. Thank very much for sharing this info. Awesome job dude! :) Now all we need is for it to be automated into Ubuntu somehow and we are golden!

---

### Post by 1image on 2006-08-28
Complete Newbie! no experince with new Os's and very comand shy
thanks for the help, by the way my card is rt5200 running ubuntu 6.0 Lts
on a p4. You got me 2 3rd's of the way and the networking tool in (System-administration-networking) did the rest.

The only thing that seems a bit out of place is the blue thingy-ma-jig flying around the 2 dots it's still flying as we speak hope that's not an issue 8-[

---

### Post by wylde342 on 2006-08-28
I just tried all this on a HP nx9010 and it seems the driver is crashing my pc?  Even when I boot it, it hangs.  

Any suggestions?  I followed all the instructions w/ ndiswrapper and nada...

---

### Post by TFX360 on 2006-08-30
Dear wylde342,


Try making a new topic. This one is old and probably abandoned.

---

### Post by k94382 on 2006-09-25
Can someone please explain me how to get the card working on a server install with only CLI and no internet at all???

---

### Post by Scooter061 on 2006-09-26
Russ, I gotta hand it to ya=D> ... I was on the right track with the NDISWrapper thing :-k ...but you're instructions and script made it a piece of cake.  Thanks to you I'm still a U-noob and not a former one.\\:D/ 

Scott
Covington, WA

---

### Post by njohn858 on 2006-09-27
Thank you so much. This walkthrough has saved me many hours of trouble getting my wireless card to work. :-D

---

### Post by clapper65 on 2006-09-27
AWESOME.  I can now connect using WPA and a TKIP password.  Is there any way to save the network settings so I don't have to type them in every time?  I would be nice that when my system boots and finds the wireless card that it automatically connects to the network.

---

