---
title: "Wicd unable to obtain IP address?"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by LoneWolf_53 on 2010-03-11
First of all hello I'm new both to this forum and Linux.

I have just installed Ubuntu 9.10 (64 Bit) and I'm trying my best to get this Linksys WMP300N wireless adapter to work.

I have searched and gone through a number of threads here with some level of progress but I still can not get this to work.

Adapter info is BCM43XG   [14e4:4329] rev 01

I have installed driver bcmwl5.inf using ndiswrapper and ndisgtk.

I had absolutely no success trying to use network manager applet so uninstalled it and went with Wicd instead which at least sees my SSID network with a strong signal.

My network is encrypted using WPA and I entered the passphrase which seems to pass authentication but it keeps trying to get an IP address until finally it just tosses a failed message.

I feel as though I'm really close but it just won't connect.


iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID : off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management : off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any help would be appreciated but I'll remind you I don't have any experience with Linux to speak of.

Thank You.

---

### Post by LoneWolf_53 on 2010-03-12
I don't know I've been trying to figure this out on my own for almost a week now and about all I've come to feel is that though I like everything else about Linux if people can't easily use wireless connections that's going to be a major stumbling block given the popularity of that kind of connection.

I must be very close as Wicd sees my network and from what I can tell gets past authentication but that's about it.

I've tried whatever other drivers I've managed to find though I have not run across a place to get the wl driver that I saw one person mention in a thread.

Apparently he managed to get the WMP300N going using the wl but so far my search terms haven't produced a good hit.

Could anyone possibly point me at where I could find that?


I can't spend much more time on this so if I don't get it solved soon it's going to be back to Windows.  :(

Oh I also noticed some request PC make and model so if that plays a role some how it's a custom built machine using a DFI X58 LP UT motherboard and Intel 920 CPU along with 6GB OCZ Reaper PC15000 RAM.

Thank you.

---

### Post by LoneWolf_53 on 2010-03-12
OK so after some experimenting with search terms I found the wl drivers.  

I suppose it's been a learning experience in that I didn't realize they are the same ones that show up in hardware upgrade but are called STA in there.

Anyway for some reason I can't figure out the hardware upgrade method failed to work so I did a manual install following steps outlined by Broadcom.

I have managed to get the wireless to work thank goodness.


The only glitch I have left is when I check the network configuration my wireless connection is listed as etho3 instead of the wlan0 that I would prefer.

Would someone care to clue me in as to what the code would be for me to change the eth3 entry to wlan0 please?

---

### Post by LoneWolf_53 on 2010-03-15
My goodness are people always this eager to help at Ubuntu?

---

### Post by Badirca Dorian on 2010-03-16
Hi. i think is a problem with the new kernel. You will have to provide manually the network characteristics. Open terminal and : $gedit /etc/network/interfaces . You should see something like : 

"auto lo
 iface lo inet loopback


 auto eth0
 iface eth0 inet dhcp


 auto ra0
 iface ra0 inet dhcp
"
Ra0 is the name of my wireless device , you will probably have something diferrent . 
So what u need to do so u can connect to a wireless network is to modifiy this file and make it look like this : 
" auto lo
 iface lo inet loopback


 auto eth0
 iface eth0 inet dhcp


 auto ra0
 iface ra0 inet static
 wireless-essid XXXXXXXXXXX
 wireless-key XXXXXXXXXXX
 address 192.168.2.200 
 netmask 255.255.255.0
 gateway 192.168.2.1
"
wireless-ssid is the name of the wireless network witch u can find out with wicd or what u using, and wireless-key is the key for WPA , etc .
Hope this is the answer.

---

### Post by gordintoronto on 2010-03-16
Most people use Network Manager. If you had stuck with that, more people might be able to help you.

I don't understand why you are conerned about a cosmetic change from eth3 to wlan0.

---

### Post by LoneWolf_53 on 2010-03-17
> **gordintoronto said:**
> Most people use Network Manager. If you had stuck with that, more people might be able to help you.

I don't understand why you are conerned about a cosmetic change from eth3 to wlan0.

Well I tried Network Manager at first and had no success whatsoever, then ran across a thread where someone mentioned Wicd working for them so I tried that and got it to work.


Mostly I'm curious why my wireless shows up as eth3 and not wlan0 but you're right it works so I'm not too worried about it.

Being new I don't have much to go on other than what a search turns up but the problem with that is some threads have good info that pertains and others not so much.

Consequently it's very helpful for a rookie to have seasoned ones point him/her in the right direction.

---

### Post by Badirca Dorian on 2010-03-17
Have another look at what i sayd in the earlier thread. if u type in a terminal : $iwconfig you should see what is the name of your wireless card . 
"

catalin@catalin-eee:~$ iwconfig
lo        no wireless extensions.

**ra0**       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

ppp0      no wireless extensions.
"
So for me **ra0** is the name of my wireless interface, your is wlan0 maybe or what name the driver gave it.  Remember the name and then type in terminal : $sudo gedit /etc/network/interface . Look again at my earlier thread and read again and see that u will have to manually provide these characteristics( name of interface , dhcp or static , ip , mask , etc ) . Hope this helps you.

---

### Post by LoneWolf_53 on 2010-03-17
Thank you for you input.

BTW my mother was born in Timisoara.  :)

---

### Post by Elludium_Q-36 on 2010-03-18
There are now a good number of trolls in these forums.  Also many scoff at GOOD free advice, so people are not inclined to offer such.

I had 8.04 and it worked great.  I wanted Barry and that was only packaged for 9.04 and later.  The troubles I have now began with 9.04 and 9.10 is assumably more of what comprises 9.04.

I have Kubuntu and some updates were less than helpful.  My knetworkconf package is gone and updates screwed up my network manager.

After I had trouble, I tried Wicd but it did not make any difference and I returned to the troublesome manifestation of gnome / kde network management and it did not change.

I've tried to get help here: [http://ubuntuforums.org/showthread.php?t=1431461](http://ubuntuforums.org/showthread.php?t=1431461)  but no one has come foward thusfar.

There seem to be problems, starting from 9.04 and "Badirca Dorian" suggests there may be kernel trouble.

I'm going to run the update to the 2.6.28-18 kernel packages which synaptic has indicated and see what that does...

I still don't know what happened to package knetworkconf, package networkstatus...  
```

netdiscover -f

```
found my linksys router's IP but eth0 doesn't seem to be quite right...

---

### Post by LoneWolf_53 on 2010-03-18
Well that's too bad if people have been turned off and lost the desire to help out.

The places I frequent that isn't the issue nor was it at PCLOS forums but I went with Ubuntu this time because I wanted a 64bit operating system.

Though I have managed to get the wireless working it isn't what I'd consider 100% and just the way Ubuntu has been behaving with some things unresponsive and such I wouldn't be surprised if there is some sort of kernel problem.

I also recall that upon installation of Ubuntu it threw up an error that had something to do with network manager so I wasn't surprised that it didn't work for me.

I know I've read enough to see that some of the glitches reported in regards to wireless were marked as addressed yet I still saw the errors in question even though I've updated through Synaptic to all the latest items it offers.

Someone told me there's supposed to be a new release coming soon so I may just wait for that and see if things run smoother.

If they don't I'm inclined to go back to PCLOS as in all honesty I prefer the layout of it a bit more than Ubuntu.

---

### Post by Badirca Dorian on 2010-03-18
You can try the new kernel ( [http://www.kernel.org/](http://www.kernel.org/) ) if you want but it isn't officially released yet. I think we need to have a little trust ( i know i have ) in the ideea of an open source project. There are a lot of people that are working to solve all these problems we are havving. In the page i just linked above u can search about bug fixez , etc . Also u can just patch a kernel , not fully install it ( [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) ) . Put 2.6.33.1 and tell me if your problems were solved . I am patching mine as we speek :)

---

### Post by davec_48 on 2010-03-18
The &quot;Unable to obtain IP address&quot; message may be misleading.  After wasting a lot of time trying various options, I discovered that I had mistyped my WPA2 key, and wicd had not actually authenticated successfully to the access point. If authentication fails, dhcp automatically fails as there is no reply from the access point to the DHCPDISCOVER messages.  Try ticking the &quot;Enable debug mode&quot; box in Wicd Network Manager -> Preferences -> Advanced settings, and check the results in /var/log/wicd/wicd.log.

---

### Post by LoneWolf_53 on 2010-03-19
> **davec_48 said:**
> The &quot;Unable to obtain IP address&quot; message may be misleading.  After wasting a lot of time trying various options, I discovered that I had mistyped my WPA2 key, and wicd had not actually authenticated successfully to the access point. If authentication fails, dhcp automatically fails as there is no reply from the access point to the DHCPDISCOVER messages.  Try ticking the &quot;Enable debug mode&quot; box in Wicd Network Manager -> Preferences -> Advanced settings, and check the results in /var/log/wicd/wicd.log.

I have managed to get Wicd to successfully obtain an IP address.

In my case the problem appeared to be the wireless adapter driver.

The only issue I have left now is that on a reboot the connection is lost and I noticed I can restore it by running the modprobe command.

---

### Post by LoneWolf_53 on 2010-03-19
> **Badirca Dorian said:**
> You can try the new kernel ( [http://www.kernel.org/](http://www.kernel.org/) ) if you want but it isn't officially released yet. I think we need to have a little trust ( i know i have ) in the ideea of an open source project. There are a lot of people that are working to solve all these problems we are havving. In the page i just linked above u can search about bug fixez , etc . Also u can just patch a kernel , not fully install it ( [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) ) . Put 2.6.33.1 and tell me if your problems were solved . I am patching mine as we speek :)

Thank you.

Since I have things more or less working now I think I'll just wait for the official release.

---

