---
title: "Need Help, Dell Wireless 1490 Dual-Band WLAN MiniCard does not work on Ubuntu 9.10"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Vrodrigu on 2010-02-08
[SIZE=2]Installed **Ubuntu 9.10 Desktop Edition** from the CD on a **Dell Inspiron E1705**, but I'm having problems getting the [/SIZE][SIZE=3][SIZE=2]**Dell Wireless 1490 Dual-Band WLAN MiniCard to work**. I couldnot find any Ubuntu\Linux driver anywhere.

The IP Address set (IP, Mask, Gateway and DNSs), for each interface are already configured. THe NIC is working fine but not the, Wireless Interface. 

If someone could shoot some light on how to get this wireless working or where I could get compatible Ubuntu, driver; please provide your reply? 

Thanks ;)
[/SIZE][/SIZE]

---

### Post by bkratz on 2010-02-08
> **Vrodrigu said:**
> [SIZE=2]Installed **Ubuntu 9.19 Desktop Edition** from the CD on a **Dell Inspiron E1705**, but I'm having problems getting the [/SIZE][SIZE=3][SIZE=2]**Dell Wireless 1490 Dual-Band WLAN MiniCard to work**. I couldnot find any Ubuntu\Linux driver anywhere.

The IP Address set (IP, Mask, Gateway and DNSs), for each interface are already configured. THe NIC is working fine but not the, Wireless Interface. 

If someone could shoot some light on how to get this wireless working or where I could get compatible Ubuntu, driver; please provide your reply? 

Thanks ;)
[/SIZE][/SIZE]




The first thing we must do is determine the wireless card. Often Dell relabels Broadcom devices. If you go to the terminal (Applications>>Accessories>>Terminal)  and type

lspci | grep Wireless

 you will probably see something like BCM43xx. Please copy/paste the output back here or simply what you found.

If you don't see anything with the above command, just try 
lspci

(By the way it is 9.10)

---

### Post by Vrodrigu on 2010-02-09
Hi [bkratz]("http://ubuntuforums.org/member.php?u=821493"),

Thanks for you prompt reply.

Below is my output after running your command. I'm looking forward to learn and try new ideas; so please, feed me with your Expert knowledge. 

[SIZE=1][/SIZE][INDENT][SIZE=1]**03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)**[/SIZE]
[SIZE=1]**0c:00.0 Network controller: [COLOR=Red]Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/COLOR]**[/SIZE]
[SIZE=1]**victor@Victor-Ubuntu-LT:~$ **[/SIZE]

[/INDENT][SIZE=1]Once more, Thanks[/SIZE]. ;)

---

### Post by Vrodrigu on 2010-02-21
[SIZE=2]Installed [/SIZE][SIZE=2]**Ubuntu 9.10 Desktop Edition**[/SIZE][SIZE=2] from the CD on a [/SIZE][SIZE=2]**Dell Inspiron E1705**[/SIZE][SIZE=2], but I'm having problems getting the [/SIZE][SIZE=2]**Dell Wireless 1490 Dual-Band WLAN MiniCard to work**[/SIZE][SIZE=2]. I couldnot find any Ubuntu\Linux driver anywhere.

The IP Address set (IP, Mask, Gateway and DNSs), for each interface are already configured. The NIC is working fine but not the, Wireless Interface. 

I have tried the following suggestion:[/SIZE]
 

 [COLOR=#800000][SIZE=2][B]The first thing we must do is determine the wireless card. Often Dell relabels Broadcom devices. If you go to the terminal (Applications>>Accessories>>Terminal) and type

lspci | grep Wireless[/B][/SIZE][/COLOR][SIZE=2]

[/SIZE][COLOR=#800000][SIZE=2]Below is my output after running your command. I'm looking forward to learn and try new ideas; so please, feed me with your Expert knowledge. [/SIZE][/COLOR] 
 

 [INDENT][COLOR=#800000][SIZE=1]**03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)**[/SIZE]
[SIZE=1]**0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)**[/SIZE]
[SIZE=1]**victor@Victor-Ubuntu-LT:~$ **[/SIZE][/COLOR] [/INDENT] [SIZE=2]I search for the drivers from the Broadcom Corp. I only found a file with codes that needs to be compiled among something else. I have no idea what I need to do. Need urgent help.[/SIZE]
 

 [SIZE=2]If someone could shoot some light on how to get this wireless working or where I could get compatible Ubuntu, driver; please provide your reply? 

Thanks[/SIZE]

---

### Post by jpl888 on 2010-02-21
Maybe you need to enable the closed Broadcom driver in System -> Administration -> Hardware Drivers.

See attached screen shot.

---

