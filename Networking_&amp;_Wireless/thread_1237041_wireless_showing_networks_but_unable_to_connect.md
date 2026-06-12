---
title: "wireless showing networks but unable to connect"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Phill Traum on 2009-08-10
Hello, i just installed Jaunty onto my hp Dv6500 my wireless card shows as a bcm4311 802.11b/g wlan i'm really new to this and really need help getting my wireless up and running. thanks

---

### Post by RedSingularity on 2009-08-10
So you can see your networks but cannot connect?  Are you choosing the correct encryption protocol?

---

### Post by Phill Traum on 2009-08-11
> **Shadow121 said:**
> So you can see your networks but cannot connect?  Are you choosing the correct encryption protocol?
  correct i can see every wireless network in my building but no luck.  And being so new at linux i'm not sure about the encryption protocol could you help me find out?
thanks

---

### Post by RedSingularity on 2009-08-11
Well if you can.....look under the router.  See if there a WEP key there.  This is of course if you are dealing with your own router.  If it is a companies or your neighbors then you will need to ask them for the encryption method and pass code.

---

### Post by Phill Traum on 2009-08-11
i have the correct password for my network, i've entered it and it tries to connect but says "Wireless disconnected" after a few seconds.

---

### Post by RedSingularity on 2009-08-11
Do you know if it is WEP or WPA?  For example, is the pass code a **word** or does it look like **18017d3eab**?  If it is the latter than you have WEP.  When the box comes up to enter your code make sure you have WEP under the security area.  There are usually two types of security for WEP.  Try them both with the pass code you enter and see which one works.

---

### Post by Phill Traum on 2009-08-11
well i put in the password the first time i tried to connect, now it does not prompt me to input anything before attempting and failing.

---

### Post by RedSingularity on 2009-08-11
Right click the network connections icon on the panel and "Edit connections".  There you can edit everything you need to.

---

### Post by Phill Traum on 2009-08-11
first i want to thank you for being so helpful =D! i've tried to edit the password and settings (both WPA personal and WEP) but when ever i put in the passphrase (it's a word not numbers) and apply.  still no luck and when i go back to edit connections my password is not the same as i put in.. instead its 8f7bcd...ect.

---

### Post by RedSingularity on 2009-08-11
Happy to help.

If the phrase is a word then it is WPA or WEP (Passphrase) not the general WEP (Hex).  There is WPA and WPA2.  Then again it could be WEP (Hex) as well.  I am not sure what your network uses and thats the problem.  You should try them all with the same pass-phrase and see what works.  If nothing works i would suggest we try another network manager.

---

### Post by john stiles on 2009-08-11
May I quickly check if the wireless connection works without any encryption?

---

### Post by Phill Traum on 2009-08-11
ok i tried all of the WEP and WPA & WPA2 Personal still nothing.  Perhaps my router is acting up... i can connect to someone else's wireless (one that's not security enabled) but no luck on my own. what other network manager did you have in mind?

---

### Post by RedSingularity on 2009-08-11
I was thinking Wicd.  Thats what i use on all my computers.  Personally i think it is nicer to use than the network manager.  You would need Internet to install it though.  Connect to an available network, go to synaptic package manager, search for wicd.  When you find it click to install.  It will remove gnome manager automatically during the install process.  If you decide you dont like it you can just as easily remove it.

You are saying you can connect to others though.  Makes me wonder if it is your router.  Can you turn off security for a minute and try to connect to it?

---

### Post by Phill Traum on 2009-08-11
ok when trying to connect with wicd it stalls at the Obtaining ip address step.

---

### Post by RedSingularity on 2009-08-11
Ok so its not the Network manager.  If you want you can install the default one again.  In synaptic it is called network-manager.  Looks like its you router.  Can you remove the security for a brief time and try to connect?

---

### Post by Phill Traum on 2009-08-11
i will. i've got to get to sleep tonight. if you don't mind telling me what i should do once i turn off the security on the router i will try after work tomorrow. thanks again.

---

### Post by RedSingularity on 2009-08-11
Well once you remove your security just try and connect to your router again.

---

### Post by a94060 on 2009-08-12
sorry if it sounds like i am hijacking thread, but I am also having the same problem. I am able to connect to the wep enabled network, and it stalls at obtaining ip address.

---

### Post by RedSingularity on 2009-08-12
WEP (Passphrase) or WEP (HEX)?  Make sure you are choosing the correct one.

---

### Post by a94060 on 2009-08-12
I am using WEP(passphrase) and am typing in the correct passphrase. I think as someone posted before, I have also tried it with wep off, and have tried someone else's network too. I previously had the ip as static,but this didnt work. Now I am getting stuck at Obtaining DHCP address. The connection works fully in windows.

EDIT-I am getting a "No DHCPOFFERS on network, switching to persistant database" in the wicd.log which is weird because I am sure that dhcp is working.(My XP install uses DHCP to get an address.

---

### Post by RedSingularity on 2009-08-12
Did you try Wicd at all?  I find it much more user friendly.

---

### Post by a94060 on 2009-08-12
> **Shadow121 said:**
> Did you try Wicd at all?  I find it much more user friendly.

Everything I have previously posted has been the result of using wicd. I just enabled the debugging feature. The dhcp thing was coming from the wicd.log file. Nothing was being told by the wicd gui except not connected.

---

### Post by RedSingularity on 2009-08-12
It sounds like some of the internal settings are off.  Did you try reinstalling wicd or even network-manager?  That may reset some of the default settings so we can start from scratch.

---

### Post by 0xdeadc0de on 2010-03-06
I was troubleshooting this same problem with a broadcom card and ndiswrapper.
The trouble isn't the network manager application, it appears to be something to do with iwconfig. I had the same problems with gnome nm applet/kde nm applet/AND wicd, but I managed to get wicd to finally work by taking a hint from another website.. 
For wicd on ubuntu 8.10 from the repo's, i edited the file /usr/share/wicd/wicd/wnettools.py , commented out lines 845-847 and now my wifi finally gets passed the obtaining ip address stage. something to do with running iwconfig (device) essid (essid) . I blame iwconfig.
It worked in 8.04 for me without this modification, with it it's working very well now. :popcorn:

---

