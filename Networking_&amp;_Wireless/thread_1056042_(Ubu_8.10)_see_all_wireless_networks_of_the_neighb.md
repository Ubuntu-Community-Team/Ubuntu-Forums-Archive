---
title: "(Ubu 8.10) see all wireless networks of the neighbourhood except mineI"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by carlosroot on 2009-01-31
Hello fellows.
I have a acer laptop 5920G. I used the Ubuntu 7.10 for more of one year without problems with the network, actually it worked better than the Vista (I have dual boot).

Now I upgraded for the new version and I have a lot of problems! 
I have wireless D-link rotter configured with WPA - PSK. The label name for the connection is and always was "dlink". I can see easly the network in windows vista but I cant see it in the linux. But the interesting thing is that I can see all the other networks in the city, except mine, even if I distance 50 cm from the router. 

I dont know if this new version has some problem with the WPA or the there is some bug trigged by the name of the connection "dlink"(may be is  some internal name for some driver...), but this name I can not change now.

Has someone experienced similar problem?

Thank you in advance
Carlos

---

### Post by vegetarianshrimp on 2009-01-31
Do you have the network set up in vista? if not, you might need to click on the [NetworkManager]("http://projects.gnome.org/NetworkManager/images/wireless-at-tealuxe.png") in the Notification Area and click "Create New Wireless Network".

If you DO have it set up in vista, you might have set it up as a hidden wireless network. In that case, click the NetworkManager again, and click "Connect to hidden wireless network"

Hope that helps!

---

### Post by carlosroot on 2009-01-31
(solved)
Do you mean that I could have configured the network as a hidden one? I dont think so. And yes, I have done exactly what you suggest concerning the network manager in task bar. This wireless network worked well before on Ubuntu 7.1. And since I installed the 8.1 I have this strange problem.

Anyway, I just asked for a change of the  SSID name. And ONLY this string was changed from "dlink" to "galleria", and now I CAN SEE IT!

I dont understand what is happening. I would like to change again the name to "dlink" just to see if the problem come back. I need to wait some moment when nobody is using the net.

Thanks 
Carlos

---

### Post by Baeckman on 2009-01-31
Hi

I just registered to this forum to second carlosroot problem. Just like carlosroot i have a D-Link (DIR-635) wireless router. My desktop computer runs Ubuntu 8.10 with a wireless D-Link DWA-140 usb stick (Ralink chipset i think). My work laptop runs Windows (unfortunately) with an Intel wireless chip. As a third computer i have a Acer Aspire One 110L netbook which also run Ubuntu 8.10 with madwifi drivers for the Atheros 5424/2424 (as demsg reports).

Right now i have the same problem as carlosroot with my netbook. It worked yesterday but today it refuse to work. It does not connect at all. It can't even see my network. I use visible SSID (baeckman) with WPA-PSK2. Using "sudo iwlist scan" list some 25-30 network but not my own. I also had this problem a week or two ago but then it disappeared when i removed the "auto baeckman" under "Network Connections". This does not work this time.

Today my router also got crazy not letting any computer stay connect. It kept restarting it self.  Normally my router is very good and stable. A reset fixed that problem and the desktop and work computer can now connect without a problem.

regards
Stefan Bäckman 

I am not completely sure but i think i ave had this problem on my desktop computer too.

---

### Post by Baeckman on 2009-02-03
Bump...

Anyone???

I have tried to clear out the settings for Network Manager with the gconftool-2 tool but i suspect the problem is not with Network Manager. I guess it has to do with the wireless-tools package.

There must be somewhere my own ssid is listed to be excluded. I base the conclusion from the fact that iwlist show a lot of other networks and that two other computers at home (windows and ubuntu) CAN see my ssid. Therefore, I suspect that iwlist reads a list from somewhere and exclude my ssid from the list of available networks.

/Bäckman

---

### Post by carlosroot on 2009-02-04
> Anyone  ??
yes Im still here.

News.

I have been away but I can back today. And the problem reappeared. Again I can see all the networks around but I cant see the mine. I wonder what my network has different from the others. The signal is the strongest, the encryption is WPA, but I can see other WPA networks... It is hard to understand.

Carlos

---

### Post by Kane_Ftw on 2009-02-04
I have the exact problem, and I'm using a D-Link router aswell.

My network has some form of WEP key (Not sure which type), and I can also easily access through Windows(XP).

I guess i'll try change the SSID see if anything changes.

(Sorry for not really helping :P)

EDIT: Changing SSID didn't do anything, if you find how to resolve this problem, please let me know via PM or something ;D.

---

### Post by Baeckman on 2009-02-06
Kane_Ftw: You help by telling the community that there is a problem. You also verified that changing SSID did not help. My guess is that the problem is connected to the MAC address, not the SSID name. But a good test anyway.

I still have not been able to get around the problem. I have submitted more information in a bug report at Launchpad/Ubuntu/Wireless-tools. You can read more about it here: [https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/312443]("https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/312443")

My next move is to remove and reinstall the wireless-tools package. I will try to do it this weekend.

regards
Stefan Bäckman

---

### Post by carlosroot on 2009-02-07
Ok. I have set the option in my Dlink-624 router called Super G Mode.
There are three options: disable, enable and enable with dynamical turbo.

I change from disable to enable with dynamical turbo. Now the network is visible again. But i dont know how long it will remain like this. The other time, when I changed the SSID name, the network was visible for two days, and then, mysteriously disappeared. Let's see what happen now... I did this modification yesterday, I will wait more 5 days and then I will give a return for you.

Thanks
Carlos

---

### Post by c-m on 2009-02-08
I have an acer aspire one and have exactly the same problem.

I can see every network in my street expect my own. 

In windows there is no problem, but in ubuntu the network is just there. However if I use an external wifi card I can see it.

There must be a driver problem.

My router is a netgear DG834GT.

---

### Post by carlosroot on 2009-02-10
It is still working for me!
Try to find some similar option in the wireless router!
Let me know
Carlos

---

### Post by squire_uk on 2009-02-10
hiya, I had a similar problem with my wireless (netgear) when i installed ubuntu, terns out it was to do with the channel I was using to broadcast my wifi on. i w using channel 13, ubuntu's only set to read the Usa standard channels, and their's don;t go up to 13.

this sound about right to you? - so 1 option is to broadcast on a lower channel or follow instructions in my post, to enable all the available channels.

>  Re: wireless problems
Quote:
Originally Posted by squire_uk View Post
Wireless Network
Name (SSID): 1234bethan
Region: Europe
Channel: 13
Mode: g & b
As I suspected. From my earlier link

Quote:
To work around this, add the following line to the /etc/modprobe.d/options file if you use this driver and need to use European wireless channels:

Code:

options cfg80211 ieee80211_regdom=EU

So:

Code:

sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bkp
gksudo gedit /etc/modprobe.d/options

Add at bottom of this file (and then save):
Code:

#Add European wifi channel support for Intel chipsets
options cfg80211 ieee80211_regdom=EU

Then reboot.



looking at these instrutions again, it was the intel intergrated wifi card that wan't configured for all 13 channels....


hope this helps. have fun!!

---

### Post by c-m on 2009-02-11
The problem is the channels. 

Some drivers will only allow the wireless card to see 11 channels. My router was set to channel 13. Changing that down to below 11 meant the network was immediately visable

---

### Post by 7Hawkeye on 2010-01-16
Hello to all! I am a complete Linux newbie, and I am experiencing the exact same problems other members have mentioned on this thread.

The difference being that I am running Kubuntu 9.10, my router is a D-Link 825 (dir-825) dual band,  and I'm using a Trendnet TEW-664UB USB wireless adaptor. The trendnet chipset is Ralink.

My channels are all on North American frequencies (2.4 GHz -11, 5 GHz  - 36), but the trendnet adaptor sees every SSID in the neighbourhood except my own which are broadcasting from two feet away.

My machine is an XP dual boot, and there's no problem with the adaptor in XP.

Please help!!!! Thousand thank yous in advance!

---

