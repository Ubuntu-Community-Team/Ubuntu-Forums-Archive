---
title: "&quot;Network is unreachable&quot; but local network works in 9.04 with Intel 945"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Lantius on 2009-07-13
Hello:

   I have a fresh installation of kubuntu 9.04 in my laptop. 

   I tried to connect to my wireless network and it connect without problems. But when I try to go to [www.google.com](www.google.com) or whichever ip outside of my local network it shows : 

   "Network is unreachable" 

   I can make ping to my local computers without problems. Even I can make ping to the router without problems. 

   I read network-manager can cause problems. So I remove it and I configure it manually through interfaces. 

   auto wlan0
   iface wlan0 inet dhcp
   wireless-essid myessid
    
   After that, I could connect doing ifup wlan0. Nevertheless the same issue, I can connect to my local computers but it doesn't work when I try to make ping to an ip outside my network. 

   My hardware is: 

    toshiba u200 satellite pro 
    Intel pro/wireless 3945ABG

   It used to work without problems in kubuntu 8.04 but I love ext4 !! 


   The network is open, without passwords. Nevertheless it has a mac filter but the laptop's mac is in the list. As I said it worked in other OS. It's a problem with kubuntu 9.04. 

   I have googled it but without results, so anybody know what I can do? 

   Thanks !

---

### Post by superprash2003 on 2009-07-14
post output of **ping 208.67.222.222**

---

### Post by Lantius on 2009-07-15
It's complicated what has happened but I'll try to explain. 

Ok, I was going to check what superprash2003 told me. 

What happened was that It suddenly work. It was not like I was trying to make ping to some not exist IP . Even with ip that he told me it didn't work sometimes. It was totally unstable. 

At the end, I saw that it usually works great without network manager . 

It is said in a lot of threads in internet here is one:

[http://ubuntuforums.org/showthread.php?t=500992](http://ubuntuforums.org/showthread.php?t=500992)

It continues being unstable, nevertheless now it works more times than with network manager. When it works, it goes totally slow. I'm testing to copy some files from a local network pc and it goes at 113KB/s. No problems under XP. 

I was looking for information and there are a lot of people with the same issue, slow connection. You can google it to check it out :

[http://www.google.es/search?hl=es&q=wireless+intel+3945+abc+slow&btnG=Buscar+con+Google&meta=&aq=f&oq=](http://www.google.es/search?hl=es&q=wireless+intel+3945+abc+slow&btnG=Buscar+con+Google&meta=&aq=f&oq=)


Here is a solution I haven't tested it:

[http://clearpixels.net/2008/07/slow-internet-on-3945abg/](http://clearpixels.net/2008/07/slow-internet-on-3945abg/)

Amitava says that It's a problem with the lastest driver iwl3945 so he uninstalled it and used ndiswrapper. 

There are more people who thinks the same : 

[http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html](http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html)

But here comes the most interesting. Check it out or continue reading if you don't have time

[http://ubuntuforums.org/archive/index.php/t-211739.html](http://ubuntuforums.org/archive/index.php/t-211739.html)

The last Post by Helen1950 (THANKS A LOT !!) Say you should change your Access Point configuration to only G devices. I don't understand it at all but I have a D-Link as she said so I changed it. 

I have a DWL-G700AP so I went to the web interface 

Advance -> Mode Settings -> G Mode (It should be on Mixed mode) 

And now it seems to work (1.6MiB), until now without network manager. I'll continue testing.

Greetings, thanks to all post that has made possible to solve this problem.

---

