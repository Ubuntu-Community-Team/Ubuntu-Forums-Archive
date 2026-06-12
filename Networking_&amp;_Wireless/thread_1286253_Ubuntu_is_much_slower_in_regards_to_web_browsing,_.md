---
title: "Ubuntu is much slower in regards to web browsing, how come?"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by Waveridr85 on 2009-10-08
I had a dual boot pc, wx/ubuntu.  both were using firefox and the ubuntu boot was much slower web browsing.  I have a wireless connection. 

Speedtest shows a download rate of 3.81, upload with a 1.73 and a ping of 45 ms

on my laptop I am getting 14.1 download and about 5 upload. 

What gives?  i even tried using different routers with no luck

Thanks, Sorry if its a newbie question

---

### Post by jeremyswalker on 2009-10-08
I'm guessing you have a driver issue. Is the wireless connection the one experiencing the slow speeds?

---

### Post by Waveridr85 on 2009-10-09
> **jeremyswalker said:**
> I'm guessing you have a driver issue. Is the wireless connection the one experiencing the slow speeds?

Both of the connections are wireless.  I was under the assumption you did not need drivers for linux.  As far as the router goes its a liksys and the wireless card is one of the buffolo extreme g ones.

---

### Post by PrePenguin on 2009-10-09
ubuntu seems to have issues with wireless speeds compared to windows for some reason I have several systems running wireless cards all are sub-par its something that needs attention or maybe i just have not seen a work around myself yet.

---

### Post by t0mppa on 2009-10-09
One simple thing to check that might or might not be the throttling factor is open up a terminal and run **iwconfig**, you'll get something along the lines of: ```
wlan0     IEEE 802.11bg  ESSID:"xxx"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-38 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Now, as you can see, bit rate on my 802.11g network connection is 1 Mb/s. This is because by default the system uses an auto rate, which means it picks up the strongest signal and goes with that. Said behaviour is useful in that it doesn't reconnect all the time due to the strong signal and even the occasional 1 Mb/s is quick enough for web surfing. Whenever I need to DL something bigger, I'll just force the bit rate to something larger through **sudo iwconfig <wireless_logical_name> rate <desired_amount>M**. You can do a **iwlist <wireless_logical_name> scan** to find out the supported rates of your AP.

> **Waveridr85 said:**
> I was under the assumption you did not need drivers for linux.

As wonderful as the idea might be, there's no magic involved with Linux - it still needs software just like Windows or OS X to tell the hardware what to do.

---

### Post by Waveridr85 on 2009-10-09
> **t0mppa said:**
> One simple thing to check that might or might not be the throttling factor is open up a terminal and run **iwconfig**, you'll get something along the lines of: ```
wlan0     IEEE 802.11bg  ESSID:"xxx"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-38 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Now, as you can see, bit rate on my 802.11g network connection is 1 Mb/s. This is because by default the system uses an auto rate, which means it picks up the strongest signal and goes with that. Said behaviour is useful in that it doesn't reconnect all the time due to the strong signal and even the occasional 1 Mb/s is quick enough for web surfing. Whenever I need to DL something bigger, I'll just force the bit rate to something larger through **sudo iwconfig <wireless_logical_name> rate <desired_amount>M**. You can do a **iwlist <wireless_logical_name> scan** to find out the supported rates of your AP.



As wonderful as the idea might be, there's no magic involved with Linux - it still needs software just like Windows or OS X to tell the hardware what to do.



Well looks as if I may have solved my problem. Heres what I did.  I went to the following link and changing the conflicting plugins.
> **lovinglinux said:**
> [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

> **lovinglinux said:**
> [COLOR=#cc0000][SIZE=4]Removing Conflicting Plugins[/SIZE][/COLOR]

Ubuntu comes with swfdec plug-in, but it doesn't work on several sites. Installing the version from Adobe might solve this problem and improve performance. 

To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

 	Code:
 	sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 

[COLOR=#cc0000][SIZE=4]Flash Tweaks[/SIZE][/COLOR]

Some people [reported]("http://ubuntuforums.org/showpost.php?p=7279173&postcount=14") improvements doing this ([original source]("http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html")):

 	Code:
 	sudo mkdir /etc/adobe
*echo* "*OverrideGPUValidation*=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/ 


Then i rebooted, restarted fox, and it prompted me to reinstall adobe flash, i did so and now I am getting a download rate of 13.3 mbps and an upload of 2.

Back on track :)

---

