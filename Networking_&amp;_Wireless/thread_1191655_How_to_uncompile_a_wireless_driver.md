---
title: "How to uncompile a wireless driver?"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Gemu on 2009-06-19
Is there an easy way to uncompile a driver once you have compiled it? I can't get my WUSB600N working in Ubuntu 8.10. It worked for about half a day and I can't get it going again for nothing. I was wanting to uncompile the driver and try another tutorial I found at linksys. Its working fine in XP right now but not Ubuntu.

---

### Post by Chronon on 2009-06-19
Not as such.  If you compiled it then you should have the source, right?

---

### Post by Gemu on 2009-06-19
> **Chronon said:**
> Not as such.  If you compiled it then you should have the source, right?



 Well "sudo make" compiled it will "sudo make uninstall" uncompile it? I wanted to try this tutorial from linksys at the top of this page - [http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&thread.id=17216&view=by_date_ascending&page=2]("http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&thread.id=17216&view=by_date_ascending&page=2")

---

### Post by Tamara Perera on 2009-06-19
I also use an edge modem for internet connection using PC Card from Sentar. I could not configure it using ubuntu and could not get enough information about it. Now is it possible to configure it?

---

### Post by jhannah on 2009-06-19
I'm not sure exactly what you mean by uncompile. If you followed the instructions on the linksys forum you posted you effectively installed the driver under ndiswrapper. If thats the case, and it's still registered, you can simply remove it with:

```
ndiswrapper -e rt2870
```

You can double check to see what the name of the installed driver is (and if it's actually registered) with:

```
ndiswrapper -l
```

Doing that should effectively uninstall the driver. Of course, if you aren't using ndiswrapper, you can remove it all together with:

```
sudo aptitude remove ndiswrapper-common ndiswrapper-modules-1.9 ndisgtk
```

Does that speak to your concerns?

---

### Post by Gemu on 2009-06-19
> **jhannah said:**
> I'm not sure exactly what you mean by uncompile. If you followed the instructions on the linksys forum you posted you effectively installed the driver under ndiswrapper. If thats the case, and it's still registered, you can simply remove it with:

```
ndiswrapper -e rt2870
```

You can double check to see what the name of the installed driver is (and if it's actually registered) with:

```
ndiswrapper -l
```

Doing that should effectively uninstall the driver. Of course, if you aren't using ndiswrapper, you can remove it all together with:

```
sudo aptitude remove ndiswrapper-common ndiswrapper-modules-1.9 ndisgtk
```

Does that speak to your concerns?


 Yes it does but I haven't actually tryed that tutorial yet. I figured it might conflict with the old one I found here. [http://ubuntuforums.org/showthread.php?t=972060]("http://ubuntuforums.org/showthread.php?t=972060")

  I almost have the tutorial working that I got from here, had it working. Its crazy. My light is on on the USB device and I'm picking up a signal I just can't seem to access the net. In one of those command lines it said that networking was disabled but I have no idea how to enable it with the command line.

---

### Post by Ayuthia on 2009-06-19
If you just did a sudo make, then you have not installed the module.  It is already compiled and the .ko file exists, but it is not in the /lib/modules folder. 

If you did [post 10]("http://ubuntuforums.org/showpost.php?p=6226499&postcount=10"), you will need to remove the entry in /etc/modules and /etc/rc.local.  It will probably be safer to remove it from /lib/modules/<kernel version>/wireless/ also.

---

### Post by Gemu on 2009-06-20
> **Ayuthia said:**
> If you just did a sudo make, then you have not installed the module.  It is already compiled and the .ko file exists, but it is not in the /lib/modules folder. 

If you did [post 10]("http://ubuntuforums.org/showpost.php?p=6226499&postcount=10"), you will need to remove the entry in /etc/modules and /etc/rc.local.  It will probably be safer to remove it from /lib/modules/<kernel version>/wireless/ also.



I also did those too so okay I'll try removing them and doing the other tutorial. Its working right now in WinXP in Infra mode but I lose my signal if I switch to Adhoc. I feel like im recieving a signal in Ubuntu 8.10 but i'm not getting out, I can't ping anything. Its so close to working.

---

### Post by Gemu on 2009-06-20
Okay I have it working with ndiswrapper loading the driver that came with the wusb600n cd for windows finally. I'm still not exactly sure where to edit settings using ndisiwrapper. Its so good to have ubuntu back I want to download something. Its difficult to get the tools you need without web access. Thanks for the replys.

---

### Post by Ayuthia on 2009-06-20
> **Gemu said:**
> I'm still not exactly sure where to edit settings using ndisiwrapper.
What settings do you want to edit for ndiswrapper?

---

### Post by Gemu on 2009-06-20
> **Ayuthia said:**
> What settings do you want to edit for ndiswrapper?

Well I was wondering when I type ifconfig wlan0 mode managed for instance...where does it go that I can see it? Is it editing a page like /grub/menu.lst? From what I gather unless you put it into /etc/network/interfaces it won't load at boot time. The ralink driver that I had before had a page called rt2870sta.dat that you could edit the settings on and I haven't been able to determine where that page is using the ndiswrapper. Is it using the rt2870sta.inf page in the windows driver? I want to be able to pull up a page with all the settings on it.

---

### Post by Ayuthia on 2009-06-21
I see...  I don't have an answer for that one.  Sorry.

---

### Post by Gemu on 2009-06-22
I ended up uninstalling ndiswrapper and going back with the Ralink driver and finanlly have it working. It would not work until I added the essid, IP address, gateway address, subnet mask and mode managed to etc/network/interfaces page and restarting it. I had a signal all day long put could not get out, could not ping a thing.  


Here is an example if it might help anyone. Its so hard to find all the info you need in one place. I got this info from one site but most of the other suggestions and commands didn't work for my set up, only this one nugget.



 /etc/network/interfaces
auto ra0
iface ra0 inet dhcp
wireless-essid   (name of your wireless router)
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed
ip address 192.168.0.2
default gateway 192.168.0.16
net mask 255.255.255.0


 I never could get the computer to shut down cleanly and restart with ndiswrapper installed.

---

