---
title: "Can't connect to internet with WEP on, can with WEP off?"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2006-06-09
Hi, I'm trying to get the internet working on my new linux install. With wep disabled on my router and WEP settings left blank on network settings I can connect to the internet. If I turn on WEP on the router and add my WEP key in network settings in dapper the internet won't connect. What am I doing wrong? 

My WEP key is in the form xxx-xxx-xx, is that hexidecimal or ASCII? 
Also i read somewhere when adding the wep key in dapper you should include the dashes, is that correct?

Cheers

---

### Post by rbalfour on 2006-06-09
No dashes. no 0x in the beginning.
In hex format

---

### Post by ????? on 2006-06-09
No dashes. If your key uses only the characters 1234567890ABCDEF then it's hex. If it uses other characters, it's ASCII.

---

### Post by AlexBryan on 2006-06-09
OK, So I still can't get it to connect using WEP. Turn off WEP and its fine. I select my ESSID from the list (or sometimes just type it in the box if the list isn't showing any networks), select Hexidecimal and type in my key without the dashes like in windows xp and keep DHCP selected. I don't understand why it won't connect.
 
One thing I noticed is that on the drop down menu for ESSID, sometimes it will only show one network (HomeConnect), sometimes my network and a bunch of others and sometimes my network twice and a bunch of others. What do the symbols next to the network names mean? Some have a little shield with a signal going off it and some have a little tower with a signal going off it?

---

### Post by rbalfour on 2006-06-11
[QUOTE=AlexBryan]OK, So I still can't get it to connect using WEP. Turn off WEP and its fine. I select my ESSID from the list (or sometimes just type it in the box if the list isn't showing any networks), select Hexidecimal and type in my key without the dashes like in windows xp and keep DHCP selected. I don't understand why it won't connect.
 
One thing I noticed is that on the drop down menu for ESSID, sometimes it will only show one network (HomeConnect), sometimes my network and a bunch of others and sometimes my network twice and a bunch of others. What do the symbols next to the network names mean? Some have a little shield with a signal going off it and some have a little tower with a signal going off it?[/QUOTE]

Your wireless router may not be setup properly or you are using the wrong WEP key. Check the router again and make sure you are using the right key.

The little symbols are for WEP - OPEN - AP wireless points. Depending on how many APs are near you the list will change.

---

### Post by Tiago Cruz on 2006-06-11
Hello guys,

I would like to know if somebody use ASCII password and not HEXA, because with me the Gnome GUI works with HEXA and not with ASCII.

The network-manager doesn't configure very well my interfaces files, I think that it is one bug with spaces, like:

I always need to edit manualy the /etc/networks/interfaces and put my password between cotations ("") to works, example:

The password is **Tiago Cruz**, I open the /etc/networks/interfaces and put my password like **[COLOR="Red"]"[/COLOR]Tiago Cruz[COLOR="Red"]"[/COLOR]** to work.

Can you understand me? Is it a little bug?

Thank you!!! =P~

---

