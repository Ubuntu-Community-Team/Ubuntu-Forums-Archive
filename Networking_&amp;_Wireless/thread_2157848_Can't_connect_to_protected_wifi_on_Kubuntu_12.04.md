---
title: "Can't connect to protected wifi on Kubuntu 12.04"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by firekage on 2013-06-27
Hi.

I would like to ask for your help. I can't connect to protected wifi on Kubuntu 12.04. I see that nm-applet shows me detected not hidden wifi networks but whenever i type in "hidden section" my ssid, and give the password (when i type ssid network manager opens up with managing connection wizard) nothing happens. I type password in wifi network set up, and if i close it and open it again, the password is not stored.

I deleted nm-applet, tried to do it with /etc/network/interfaces and NetworkManager.conf but i did not succeed. Can you help me? I have always have problems with connecting to network, wired and wireless on KDE - no matter which system has it (Kubuntu, Slackware). Ubuntu or other see my network right from the boot even with live cd - Kubuntu doesen't. 

I don't know how to connect to internet, how to set up. I can't install wicd because i don't have connection at all.

Please, help.

---

### Post by SeijiSensei on 2013-06-27
I'm not sure what you mean by "protected" here.  Do you mean connecting to a router with a hidden SSID?  What happens if you change the router setting to advertise its SSID?

I never hide SSID as it provides essentially no real security at all.  For that I rely on WPA2.  I have had occasional issues connecting with Kubuntu, but usually it has to do with driver problems, not KDE itself.

---

### Post by firekage on 2013-06-27
> **SeijiSensei said:**
> I'm not sure what you mean by "protected" here.  Do you mean connecting to a router with a hidden SSID?  What happens if you change the router setting to advertise its SSID?

I never hide SSID as it provides essentially no real security at all.  For that I rely on WPA2.  I have had occasional issues connecting with Kubuntu, but usually it has to do with driver problems, not KDE itself.


Problem is not with the hidden setup, rather with WPA2 because when i type my password, nothing happens. I removed nm-applet and now changing settings of router won't affect it at all because, in order to connect, i have to manually set up it in /etc/network/interfaces, and i don't know how to do it.

I don't understand why on Ubuntu, Xbuntu, Mint and other oes my wired and wireless network is found and work, in Kubuntu, or rather with KDE, my network either doesen;t work at all, or can't connect to it.

Edit: it seems that you are right. I changed settings to show my ssid and connected...

---

### Post by firekage on 2013-06-29
It doesen't change the fact, that it is something broken. I want to have my wifi hidden - with Kubuntu, i can't.

---

### Post by firekage on 2013-06-29
What do you mean by "protected to prevent"? Protected - with wpa password and being hidden which means that my ssid is hidden. With this i can't connect, if i unhide ssid, my network is visibile, i can connect on Kubuntu. On other distros, like Ubuntu, Mint, i can have hidden ssid and connect.

---

### Post by claracc on 2013-06-29
ckuvynub45 is a spamer, not take into account any of his advices (if any).

I suppose it would be removed soon

---

