---
title: "WPA for wireless, and Using multiple networks??"
date: 2004-10-25
forum: Networking &amp; Wireless
---

### Post by brschmid on 2004-10-25
In a given week i use 4 or so different wireless networks with my laptop; My apt, work, school, and my other job.

is there a way to enable WPA for my home network??

but i also need to be able to connect to the other networks, which are non-secure. 

how can i do this, thanks :)

---

### Post by brschmid on 2004-10-26
anyone????

---

### Post by kingnubian on 2004-10-26
I am also looking into this and so far this is what I've found out. When using a Linux kernel supported wirless card, usually based on the Atheros or the Prism chipsets, Ubuntu will have little or no problem recognizing and setting up the card. The user will now have to deal with the encryption options. WEP is supported and the key can be entered with Gnome GUI tools or by command line (iwconfig), but with WPA things get sticky. It seems that a "Supplicant" is needed to get WPA to work, presently at least, with the kernel supported cards. The necessary files and howto is located here.....[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/).

Seems like a lot of work to get things going but that's the way it is for now. I also have read that with DriverLoader  WPA support only depends on the windows native driver used but I'm for a Linux only solution.

I also understand that the Native Atheros chipset driver is moving along well and experimental WPA support may be included in an upcoming release but don't quote me here.

---

### Post by brschmid on 2004-10-27
[QUOTE=kingnubian]I am also looking into this and so far this is what I've found out. When using a Linux kernel supported wirless card, usually based on the Atheros or the Prism chipsets, Ubuntu will have little or no problem recognizing and setting up the card. The user will now have to deal with the encryption options. WEP is supported and the key can be entered with Gnome GUI tools or by command line (iwconfig), but with WPA things get sticky. It seems that a "Supplicant" is needed to get WPA to work, presently at least, with the kernel supported cards. The necessary files and howto is located here.....[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/).

Seems like a lot of work to get things going but that's the way it is for now. I also have read that with DriverLoader  WPA support only depends on the windows native driver used but I'm for a Linux only solution.

I also understand that the Native Atheros chipset driver is moving along well and experimental WPA support may be included in an upcoming release but don't quote me here.[/QUOTE]
 thanks for the info. 

any idea on how to get it to automatically detect and link up to different networks, without me having to change the SSID every time?

---

### Post by kingnubian on 2004-10-27
I know that you can sdetup profiles with the Gnome network widget but I think it only supports dealing with WEP and its necessary keys. As for multiple WPA enabled networks I have no idea.

---

### Post by brschmid on 2004-10-28
[QUOTE=kingnubian]I know that you can sdetup profiles with the Gnome network widget but I think it only supports dealing with WEP and its necessary keys. As for multiple WPA enabled networks I have no idea.[/QUOTE]
 i can live without WPA because only 1 network has it (mine in my apt) and i can disable that, 

the rest of them are wide open access points.

---

### Post by bazder on 2006-11-02
I had hoped Edgy would have fixed this but after an
initial peak at it last night it seems not - however
I can still connect to my WPA wireless network by
using KNetworkManager. check it out - I can't get it
to use a passphrase (just a 64 characater hex string
cut & pasted from a text file).  ugly but it works.

---

### Post by horatiub on 2006-11-02
I kinda have the same problem. My home network and work network have WPA enabled, and I would like to have 2 profiles, so i can connect to them. How can I do that? So far, I setup my home connection with WPA, by editing the wpa_supplicant.conf and it works fine, but when I go to work, I have to change the SSID and the password again in order to connect.

---

### Post by darkhatter on 2006-11-02
i believe if you click connect to a network option it lets you enter a wpa connection I'm not 100% sure

---

### Post by horatiub on 2006-11-02
> **darkhatter said:**
> i believe if you click connect to a network option it lets you enter a wpa connection I'm not 100% sure

hmm, in edgy I can't seem to get that

---

### Post by T8y8 on 2006-11-03
NetworkManager 0.6.3 (and maybe 0.6.0) will work with wpa_supplicant to use multiple WPA networks. It stores the keys in the keyring. You just click the applet, and it shows you the networks, you pick one, and put in the key.

That's the setup I've got going. I just apt-got wpa_supplicant, and put my key into network-manager. This is with an Intel 2915, on native drivers.

If I can find the guide I used, I'll throw it up

---

