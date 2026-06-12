---
title: "Network-manager and disabled SSID broadcast?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by coffeecat on 2006-06-27
I've had a bad day. I've had a very, very bad day. :(

A simple question: Is there a problem with disabling (hiding) the SSID broadcast with network-manager-gnome?

I have a Sony Vaio laptop (Intel 2200BG wireless chipset) running Dapper. I can connect using WPA encryption reliably. The only issue is having to put my keyring password in at every boot and, yes, I have discovered the excellent howto/thread for fixing that but after today...... I'll give it a little while before trying it out. ;)

Well - I thought I would improve security by disabling the SSID broadcast, changing the SSID identifier and changing my WPA key. Perhaps I should have done one thing at a time. Oh dear. Oh dear, oh dear, oh dear, oh dear!

I won't bore you with all the details, but even after reverting back to my original SSID and key, and re-enabling the SSID broadcast, network-manager wouldn't connect, or couldn't find a network device - and all sorts of other things. After **much** fiddling about I've got it working again (several fingers crossed), but it's left me feeling very weary and very mystified.

Two other questions:

Why, after I had changed the SSID name, was it still showing me the original SSID name which was no longer being transmitted? Very odd. Neighbours' SSIDs appear and disappear quite regularly, presumably as they switch their routers on and off.

Has anyone had experience of changing their SSID without hiding it, and did you have any problems? I would like to do at least that, but I don't want to go through what I went through today.

Aaaaarghh!

---

### Post by Personatech on 2006-06-27
I'm not that familiar with NM (I did try it and never could get it to work properly so I stick with the Gnome Network Panel) but many of these utilities remember every network they've ever seen (this is certainly the case with Windows Wireless Connection).  Perhaps there's some way to clear those networks short of doing a complete reinstall...

---

### Post by coffeecat on 2006-06-27
What's odd is that there's a folder (~./.gconf/system/networking/wireless/networks/*SSIDname*) which contains a .xml configuration file. At one point I tried moving this to the wastebasket, and **still** the old SSID kept appearing when I clicked on nm panel icon. :-k

---

### Post by coffeecat on 2006-06-30
Bump.

Does anyone know the answer to my main question? Is there a problem with hiding/disabling SSID broadcast in Linux and/or network-manager?

Thanks.

---

### Post by wieman01 on 2006-07-03
[QUOTE=coffeecat]Does anyone know the answer to my main question? Is there a problem with hiding/disabling SSID broadcast in Linux and/or network-manager?[/QUOTE]

I have used NM and I could not get it to work with "hidden" ESSIDs on my Sony Vaio VGN at all. So I chose a manual approach by making the necessary changes in the "/etc/network/interfaces" file. Similar to this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

It definitely works with hidden ESSID and WPA2 encryption (if you need DHCP your settings will look slightly different) on my Sony laptop.

Let me know if you need a hand.

He

---

### Post by coffeecat on 2006-07-03
[quote=wieman01]I have used NM and I could not get it to work with "hidden" ESSIDs on my Sony Vaio VGN at all.[/quote] 
Thanks - that confirms what I had suspected, that it is a network manager rather than a Linux issue. My laptop is the Sony Vaio VGN-FS215B, and what I didn't say in my original post (so as not to make it too long) is that I have set up a quad boot  which also includes SuSE 10.1, Fedora Core 5 and Windows. I'm relying on NM in SuSE and Fedora as well, and I experienced more or less the same runaround in Fedora with a hidden SSID. Took me ages to get them both to work properly again.

Thanks for the link. I'll read it through carefully and have a think before I do anything because I have three Linux installations to consider. I do use Ubuntu most often though.

But of course! :) :wink:

---

### Post by wieman01 on 2006-07-03
NetworkManager is a good tool and a step in the right direction, however, as you & I know it is far from being perfect. Hidden ESSID's and static IP addressing are an issue so let's hope for the best in terms of future development.

The link I have posted here should work for systems using wpa-supplicant v0.4.8. I hope this also applies to your other distributions but of course I cannot tell since it's a fairly long time that I last used SUSE and Redheat, respectively.

Let me know if it works out.

Cheers / He

---

### Post by it.henrik on 2006-07-20
Confirming issues with hidden ESSID. NetworkManager is a step in the right directon but there are lots of bugs. If you check the connectivity with iwconfig during connecting to a hidden essid you will find that it does connect... and disconnects .. several times. How hard can it be to make the connection phase stop when the connection with the accesspoint is set up. Well .. lets wait and see.. until then I recommend wifi-radar. It works flawless.

---

