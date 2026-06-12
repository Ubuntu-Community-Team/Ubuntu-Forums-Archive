---
title: "[Urgent] NetworkManager - WPA option disappears"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by Vinze on 2006-06-11
Hey, I'm really desparate now, having spent in total many, many hours (think 30+) on trying to get internet, but still no result...
We have a WPA encryption, because the (...) friend of my mother is really paranoid, anyway, I can't get that to work.

Now I brought my computer to my dad's where I got wired internet, but I have to take it home this afternoon again, that's why it's urgent.

So, I updated my whole computer and then (because of [this](http://ubuntuforums.org/showthread.php?t=179643) thread) installed Network Manager, which gave me some hope I would get WPA encryption. It didn't work, as nm-applet only had three WEP-type options. Then I followed [this thread](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=network+manager+wpa), thinking maybe my computer did not include WPA support somehow. Well, it didn't work. Still no WPA option in nm-applet.

Then in Synaptic I saw knetworkmanager. I installed it, and to my great joy when I clicked to add another wireless network, it had a WPA option! However, when I tried to connect it did not work. Then I did as the first thread stated, comment out everything in /etc/network/interfaces except for lo, rebooted and then it recognised the network I wanted to be on, and it recognised my network adapter. So I clicked it and -crap!- no WPA option... ](*,) 

I'd be very, very grateful if finally somebody would be able to solve this problem for me, because it's really frustrating.

Thanks in advance.

---

### Post by Vinze on 2006-06-11
I made some screenshots so you can see my problem.

noWPA3.png is knetworkmanager when I clicked "Connect to Other Wireless Network", then it showed noWPA4.png, which disappeared on 28% on which it said "NetworkManager is now disconnected".](*,) 

Please help!

---

### Post by Princey on 2006-06-11
What wireless card are you using and what chipset does it have? That's important because presently, not all network cards support WPA under linux.

---

### Post by Vinze on 2006-06-11
[QUOTE=Princey]What wireless card are you using and what chipset does it have? That's important because presently, not all network cards support WPA under linux.[/QUOTE]

Chipset is intersil prism as you can see in noWPA3.png, I'm not sure about the card, it's from SMC and it says EZ connect g. 
Anyway, intersil prism should use the hostap driver if I'm correct, I believe networkamanager tries to use prism54.

---

### Post by aanderson on 2006-06-11
I'm having basically the same results you mention:  I have a Dell Insp. using ndiswrapper which works (mostly) with WPA, but I have been unable to get an
HP transport v1000 working, which uses the intersil prism2/2.5 (rev 01) . 

I don't know whether NM tries prism54, but I just spent a couple of days trying to get wpa_supplicant to work by itself using hostap. It is interesting that the capablities listed from wpa_cli are identical between the two laptops, but on scan,scan_result the HP shows my AP as [WEP], while the Dell shows the same AP as [WPA...], and NM behaves accordingly, so I suspect some deficiency in the hostap (it does the same thing using orinoco as well) or in the firmware.

I changed the AP to WEP, but still couldn't get them both working, so there is still some cockpit error involved. 

 Anyway if anyone can shed light on this I will appreciate it.

---

### Post by Vinze on 2006-06-12
Well, I found out that mine uses the prism54 driver (by running NetworkManager --no-daemon), which does not support WPA... Crap.

Anyway, I guess you will have to try to find out if and how you can manually set  the driver to use. I asked for it on these forums but got no reply.

---

### Post by Princey on 2006-06-14
My chipset is different, so I'm not sure how much help this would be to you. But one thing I did to get mine working was to configure the wpasupplicant file. If you haven't yet done so, please let me know and I'll give you a few pointers how to get it running as it does involve some manual tweaking around.

---

### Post by dinub1 on 2006-06-15
I am having the same problem. Works with WPA2 but not with WPA. Like yours, it gets stuck at 28% of network configuration. I was very happy at the beginning, though it refused to work with WPA. I was able to work with WPA2 which is even stronger...
but lately it does not recognize my network adapter anymore, though it is active and I can use it with WEP with Ububtu built in network application. I do not know what's happening... I susupec it is a buggy application.

---

### Post by dinub1 on 2006-06-15
[QUOTE=Princey]My chipset is different, so I'm not sure how much help this would be to you. But one thing I did to get mine working was to configure the wpasupplicant file. If you haven't yet done so, please let me know and I'll give you a few pointers how to get it running as it does involve some manual tweaking around.[/QUOTE]
My wpa_ssuplicant.conf file was configured before and running it under terminal it connects. However knetworkmanager refuses to see the wireless adapter lately and disregards it. It inly sees the wired adapter. I am using a card (D-Link) based on Atheros chipset. I don't know what's happening.

---

### Post by Joe on 2006-06-16
Similar problem.  I finally got network manager working connected to my wpa network via ndiswrapper so I decided to do an upgrade in Synaptic.  After the upgrade I restarted my computer and now network manager can't find any wireless signals out there.  I can enter in the info for a specific access point but the wpa option has disappeared leaving only the 3 wep options.  Extremely frustrating.

---

### Post by Princey on 2006-06-16
[QUOTE=dinub1]My wpa_ssuplicant.conf file was configured before and running it under terminal it connects. However knetworkmanager refuses to see the wireless adapter lately and disregards it. It inly sees the wired adapter. I am using a card (D-Link) based on Atheros chipset. I don't know what's happening.[/QUOTE]

I do have a D-Link card and that's what I'm connected to using posting here. It's the D-Link Airplus DWL-G510 Rev.B. It uses the atheros chipset. I will outline the steps I took to get mine working here so someone might have the remote chance of getting theirs up using my steps. I had to read several posts and documentaries to come up with my own method. Here's what I did.

1. I edited my /etc/network/interfaces to look like this: > auto wlan0
iface wlan0 inet dhcp
wpa-conf /home/emmjay/.wpa/wpa_supplicant.conf
 Note, I copied just the part relating to my network card. So, you'll have to substitute whatever it is you in the place of 'wlan0'. Also note, that the folder /.wpa/wpa_supplicant doesn't exist by default. So, on to step two.

2. Go to your home directory, make sure "show hidden files" is checked if you're using KDE in Konqueror (I can't remember the settings in gnome--haven't used it for a long while but I'm sure you can find it). Create the folder '.wpa'. Make sure that the period/fullstop preludes the wpa.

3. Type the following at the terminal: > wpa_passphrase xxxxx yyyyyyyyyyyyyy where xxxxx is your ESSID and yyyyyyyyy is your passphrase. Please make sure that if your ESSID contains two words there's no space between them. The only space is between the ESSID and the passphrase. Copy the information in the terminal(for me it was easier to highlight using my mouse, then selecting, Edit-Copy from the menu list.

4. Type ```
sudo gedit
``` and paste the information in there. Make sure your file looks like this > 

# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
        key_mgmt=WPA-PSK
        proto=WPA2
        pairwise=TKIP
        ssid="yournetworkname"
        #psk="yourpassphrase"
        psk=somelongfunnykey
}

Of course, yournetworkname should be the name of your network making sure it's in inverted commas, same as the passphrase. The somelongfunnykey you should have received from the output from step 3.

5. Save the file in the .wpa folder as wpa_supplicant.conf (NB. This step is important as saving it elsewhere you'll have to redirect the /etc/network/interfaces file to point to that and seeing we've already directed it, it's just a matter of saving it to the right spot. 

Unlike other posts that asked to comment out other lines, I didn't. Never touched my /etc/network/interfaces file save for the extra line I added as outputted in step 1

6. Make sure network manager is installed. I'm using Kubuntu so for me it was knetworkmanager. Type ```
knetworkmanager
``` at the prompt. Use the gnome equivalent if you're running gnome or if you prefer you could install knetworkmanager. It's your choice. You should now get a prompt to save the info in your wallet. Reboot, your wireless should be up and running.

---

### Post by Vinze on 2006-06-18
Well, I configured wpa_supplicant. I've come to the conclusion that my network adapter does not use the driver I was told it uses, and this driver (prism54) does not support WPA. Luckily, there's a new network here in the neighbourhood which has no encryption,woohoo!

---

### Post by Princey on 2006-06-18
[QUOTE=Vinze]Well, I configured wpa_supplicant. I've come to the conclusion that my network adapter does not use the driver I was told it uses, and this driver (prism54) does not support WPA. Luckily, there's a new network here in the neighbourhood which has no encryption,woohoo![/QUOTE]

Sorry to hear that, Vinze, but did you try my above method? Remember, you must have both installed and as I said, I didn't go uncommented entries in the /etc/network/interfaces file. I left them as is. My only addition was where to look for the wpa_supplicant file.

---

### Post by Vinze on 2006-06-18
I haven't tried them, though they looks a bit similar to some things I've already done. However, if prism54 does not support WPA, then your method too won't work, right?

---

### Post by Princey on 2006-06-18
[QUOTE=Vinze]I haven't tried them, though they looks a bit similar to some things I've already done. However, if prism54 does not support WPA, then your method too won't work, right?[/QUOTE]

I'm not entirely sure where does the prism54 chipset fits in. But according to [this]("http://hostap.epitest.fi/wpa_supplicant/") document, prism chipsets are supported. I'll do some poking around and update you as to what I find. 

_Update_
I did find out that the prism54 chipset is supported, at least in fedora core 5. I may be wrong, but it might just work in Ubuntu. Don't take my word as Bible, but you can give it a try.

---

### Post by lewdvig on 2006-08-11
I can not get Network Manager to pop up. I tried installing it but it is already installed. I only have Network Monitor - which works for WEP networks but not WPA.

---

### Post by Princey on 2006-08-11
> **lewdvig said:**
> I can not get Network Manager to pop up. I tried installing it but it is already installed. I only have Network Monitor - which works for WEP networks but not WPA.

Can you please give more details in terms of what you did and what you didn't do? Chipset/network card etc? Just saying it didn't work doesn't give us anything to go by that we can help out.

---

### Post by helmut_hed on 2006-08-13
For those of you who "only get WEP options" when you select your WPA network, try this instead:

Select "Connect to other wireless network"
In the popup, type the name of your wireless network, click "use encryption", then select WPA Personal (and use the radio button for WPA1 or WPA2), and enter your passphrase.

Whenever I directly select my wireless network, NetworkManager thinks it's WEP, but things work fine when I use the above procedure.  I think this is a bug, but at least I can work around it.

Jeff
PS: I have a Intersil Prism2.5 chipset, using the hostap driver (instead of the default orinoco).  I had to upgrade the firmware as well to get WPA to work.

---

### Post by Vinze on 2006-08-17
> **lewdvig said:**
> I can not get Network Manager to pop up. I tried installing it but it is already installed. I only have Network Monitor - which works for WEP networks but not WPA.

Try running nm-applet manually.

---

