---
title: "Wireless with ndiswrapper- Unable to autostart at boot."
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by chrismyers on 2006-05-10
Hi there.

I have an INEXQ MR054G PCMCIA wireless network card that works fine with ndiswrapper in Ubuntu Breezy (WEP).

I just cant seem to get this to start up during boot. I've scoured the forum, but everything I have tried has been without success.

I manually run this little script which gets my card up & running:

sudo iwconfig
sudo iwlist wlan0 scan
sudo iwlist wlan0 mode Managed
sudo iwconfig wlan0 key restricted MYKEY
sudo iwconfig wlan0 essid MYESSID
sudo ifconfig wlan0 up
sudo dhclient wlan0

My question is. How do I get this to autostart?

I've tried editing my /etc/network/interfaces with the above info, but It just wont work for me.

Is there anyone who can translate the above script into a valid interfaces file?

Many thanks.

---

### Post by Titus A Duxass on 2006-05-11
Put ndiswrapper in /etc/modules.
That should clear your problem.

Have you got the line:

auto wlan0

in your /etc/network/interfaces file?

---

### Post by az on 2006-05-11
[QUOTE=chrismyers]

Is there anyone who can translate the above script into a valid interfaces file?
.[/QUOTE]


If the ndiswrapper module is loaded, you should see a wireless device in the gnome networking tool.

Just click to configure it and enter the essid and wep values.  It will edit the interfaces file for you.

---

### Post by chrismyers on 2006-05-14
[QUOTE=azz]If the ndiswrapper module is loaded, you should see a wireless device in the gnome networking tool.

Just click to configure it and enter the essid and wep values.  It will edit the interfaces file for you.[/QUOTE]

Cheers.. It's fixed. 

I'd allready tried the Gnome menu & I assumed it wasn't working. Because of your post I delved deeper.

Just to summarise:
It worked in WindowsXP
It worked in Ubuntu from the manual script.
It didn't work from the Gnome config menu.

I went back to my router & found that I was using a 10 digit ascii key.

I switched it to a 13 digit key & Everything worked! The Gnome config menu must be a bit twitchy about key lengths.

Many thanks. :D

---

