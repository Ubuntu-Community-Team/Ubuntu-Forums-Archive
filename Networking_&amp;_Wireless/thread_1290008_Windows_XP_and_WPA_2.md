---
title: "Windows XP and WPA 2"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2009-10-13
Howdy All,

So this is going to be a bit of a heretical post for this site, but I was hoping there might be some network admins out there or something that work on Windows XP boxes as well as Ubuntu.

I am running dd-wrt on my Linksys 54g router. I was using WEP encryption for wireless access for the longest time until I finally got paranoid enough to update to a secure network. That being said, I changed my encryption scheme over to WPA-2. The WPA 2, Personal, AES only encryption standard to be specific. I input an 11 character ascii key for the shared key on the router then applied the settings.

Once I finished, I rebooted my Ubuntu computer and used wpasupplicant to generate the corresponding hex code for the ascii key I input. This went into my /etc/network/interfaces file and my Ubuntu box connects perfectly to the router.

However, my roommate uses a Windows XP laptop and it is being a brat. Again, the computer had been configured to work on the WEP encrypted network previously. Now when I boot it and try to connect to our network it simply asks for a password. When I input the 11 character ascii password that I put into the router it gives me the following message:

> 
The network password needs to be 40bits or 104bits depending on your network configuration. This can be entered as 5 or 13 ascii characters or 10 or 26 hexadecimal characters


So, I did some googling and in every help forum on windows networking I can find the posters are usually told, "Well, it means you have to us a 13 character password."

My question is, does such an arbitrary standard really exist on Windows systems and does anyone have a single f***ing clue as to why such a stupid distinction would be made? The 11 character password works just fine using wpasupplicant on my system, so I see no real reason it can't work on Windows.

I am suspecting that what actually happened is that some kind of value got locked into the OS telling my roomie's system that it is supposed to be a WEP key when it is now a WPA key. If that, or something similar, is the case, does anyone know if I can fix that? Also, if the problem is that I need to create a hex key like I did with my ubuntu box, does anyone know how I got about doing that in windows? 

So far, all I could find was a lot of Microsoft astroturfing of a networking hotfix (which I don't know how to download to a CD and install on my roomie's computer if that's the problem) and what seems to be a lot of unhelpful nonsense on the microsoft help forums. Does anyone know what the WPA key issue might be caused by?

Thanks in advance, sorry for posting about microsoft on here, I love Ubuntu and am trying to get my roomate to convert ><

---

### Post by BJ_Covert_Action on 2009-10-13
I went into his network configuration utility thingy and found that the network was listed on his preferred networks list with WEP encryption as the defacto encryption. I deleted it from the list (as there seemed to be no way to add WPA2 as an encryption scheme) and tried reconnecting with the WPA2 password.

I also installed the Windows hotfix/patch/whatever that is supposed to enable WPA2 capability via networking just in case he didn't have it. It seemed to have installed cleanly. 

After a reboot, when I try to connect to the WPA2 network now, I can put in any password without getting an error message complaint from Windows. However, it seems to start to connect ('Acquiring Network Address') but then stops trying with not error message or warning. It remains unconnected.

I am pretty sure now that I need to create some kind of computer-specific hex key for the WPA shared key on the router (like I did with supplicant on my Ubuntu box) but I don't know how to do this in Windows. Does anyone know if that's correct? And if so, how to go about doing so?

Thanks ahead for the help,
Brady

---

### Post by prshah on 2009-10-13
No the problem has nothing to do with your WPA key.

Pre-SP2 Windows XP Home did not have support for WPA networks. Though this support was added in later through SP2 / Hotfix packs, many vendors shipped drivers that did not have WPA capabilities.  (Case in point: My Fujitsu P5010)

You have to download a later version of the WINDOWS DRIVER for the WLAN card. You should be able to get it pretty easily.

The new driver, in addition to the Hotfix / SP2 / SP3 will allow XP Home to connect to WPA networks.

If your driver does not support WPA, adding the Hotfix alone will not help; it will not even show WPA as an option.

Post back with details if you need help with locating the Windows driver.

Additionally, I would STRONGLY NOT recommend dropping back to WEP.

---

### Post by BJ_Covert_Action on 2009-10-13
Hmmmm, I will take a look for new drivers for the networking card. The card seems to recognize the network as WPA2 (its in parentheses next to the SSID in the network manager GUI). But I will be sure to update the driver just to be sure.

I will let you know if that doesn't work out. Thanks for the info.

---

### Post by BJ_Covert_Action on 2009-10-13
Hmmm, well I found a bit of a workaround for now. I installed the version 3.0.2 drivers from [here](http://support.packardbell.com/uk/item/index.php?i=7406030000&ppn=pb46c00101) and that didn't seem to allow the card to connect to the network. I couldn't find a later version of the driver so if anyone else can find one for the RT2500 driver for windows XP I would be much obliged.

For now I switched the network over to WPA2 Mixed instead of simply WPA2 which, so far as I can tell, means it will also back-support WPA and WEP. That being said I am pretty sure this configuration still is not very secure so I would bring it back up to WPA2. Does anyone know what the latest RT2500 driver version number is and whether or not it supports WPA2 or not?

Cheers,
Brady

---

### Post by prshah on 2009-10-14
> **BJ_Covert_Action said:**
> The card seems to recognize the network as WPA2 (its in parentheses next to the SSID in the network manager GUI)

let me clarify; I have a fujitsu lifebook P5010 that comes with an inbuilt intel 2100 wifi lan card, and Windows XP Home SP1, and a drivers disc,

Windows XP SP1 did not connect to a WPA network. In manual setup, there was no option to connect to WPA. While SSIDs were detected, I could not connect to them. The letters WPA did not appear anywhere.

In Ubuntu however, I could smoothly connect to WEP / WPA / WPA2 networks out of the box.

I upgraded XP Home to SP2... no WPA. SP3.. no WPA. I tried manually applying the WPA hotfix; it failed stating that it needed a Pre-SP2 to install.

I then upgraded the driver... the P5010 had no further driver updates available (it's a very old notebook), and the next model had the same Intel wlan card, so I downloaded the drivers for it and took a shot. The Windows drivers installed smoothly, and immediately (after a reboot) WPA networks were connect-able. Automatic and manual both worked fine, WPA was indicated next to the network SSID.

If your [friend's] Windows does not detect WPA, then either XP is Pre-SP2, or the driver is old, or both.

What is the make and model of your notebook and wlan card? It will help when suggesting updated drivers. Please also check the version of the wlan driver in use: open Start-Run, give the command ```
devmgmt.msc
``` Expand the networking section, select your wlan card and choose properties; one of the tabs will show the version of the driver in use, AND the date of the driver. 

Please post back all the above information to help suggest a suitable driver.

Running a mixed WPA/WEP network is as bad as running a WEP network.

---

