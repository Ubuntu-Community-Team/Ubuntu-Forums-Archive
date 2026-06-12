---
title: "BCM4322 monitor mode"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by PIPI on 2011-05-07
I'm using laptop HP6830s with ubuntu 11.04 and broadcom BCM4322 wireless card. When I tried to put my card in monitor mode i get this message

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

``` 

I tried with ndiswrapper, and it says it should work. It's known problem with broadcom bcm43xx cards. I tried with all tutorials for bcm43xx cards and i'm sure they work for other cards, but for this one doesn't. anybody help?

if you need any additional information just ask

---

### Post by triduonghuu on 2011-05-11
Hi,
I have the same issue with my BCM4312, anybody had solution yet?!:confused:
It worked fine on 10.04 and 10.10 with linux-backports-modules-wireless, but i cannot find this type of package on 11.04.

---

### Post by northd_tech on 2011-05-11
> **PIPI said:**
> 
if you need any additional information just ask

I probably won't be able to help with this, but just out of curiosity, what command(s) put a Broadcom 4322 "in monitor mode?"   (I've got a working Broadcom "4321AG"/"4328", and I'm a little curious what is involved with that part...) :confused:

---

### Post by triduonghuu on 2011-05-11
Hi [northd_tech]("http://ubuntuforums.org/member.php?u=938429"),

Monitor mode use for capturing things, such as Kismet or Aircrack-ng. You can test with [B]iwconfig  [interface] mode monitor.

[/B]Once again, anybody work with this on 11.04.

---

### Post by northd_tech on 2011-05-12
> **triduonghuu said:**
> Hi [northd_tech]("http://ubuntuforums.org/member.php?u=938429"),

Monitor mode use for capturing things, such as Kismet or Aircrack-ng. You can test with [B]iwconfig  [interface] mode monitor.

[/B]Once again, anybody work with this on 11.04.

FWIW, my working Broadcom "4328" using the "STA" driver tells me this under Ubuntu 10.04.2 LTS:

> **iwconfig eth1 mode monitor**
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.**ifconfig** tells us this about the "eth1" wireless Broadcom interface:

> eth1      Link encap:Ethernet [...]
          inet6 addr: fe80::221:ff:fe13:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1699755 errors:4023 dropped:0 overruns:0 frame:352135
          TX packets:958347 errors:64 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2430222696 (2.4 GB)  TX bytes:85388023 (85.3 MB)
          Interrupt:19 
Just as a guess- it ***apparently*** does not work for me either (64-bit Ubuntu 10.04.2 LTS).

:(

EDIT:  I also get about the same error as yours with the following command:

> **sudo iwconfig eth1 mode monitor**
[sudo] password for ...:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.


EDIT2:  While the **man** **iwconfig** page has some interesting stuff on it, I don't see any glaring syntax/command errors in the above either:

>        **mode**   Set the operating mode of the device, which depends on the  net&#8208;
              work  topology. The mode can be **Ad-Hoc** (network composed of only
              one cell and without Access Point), **Managed** (node connects to  a
              network  composed  of  many Access Points, with roaming), **Master**
              (the node is the synchronisation master or  acts  as  an  Access
              Point),  **Repeater** (the node forwards packets between other wire&#8208;
              less  nodes),  **Secondary**  (the  node  acts  as  a  backup   mas&#8208;
              ter/repeater), [COLOR=Blue]**Monitor** (the node is not associated with any cell
              and passively monitor all packets on the frequency)[/COLOR] or **Auto**.
              Example :
                   iwconfig eth0 mode Managed
                   iwconfig eth0 mode Ad-Hoc


---

### Post by northd_tech on 2011-05-12
> Just as a guess- it ***apparently*** does not work for me either (64-bit Ubuntu 10.04.2 LTS).
According to post #2 on another thread:

[http://ubuntuforums.org/showpost.php?p=10291616&postcount=2](http://ubuntuforums.org/showpost.php?p=10291616&postcount=2)

> The official Broadcom STA driver does not allow the mode of operation  you want. The open source B43 does, but I will have to look and see if  your particular card is compatible.

Post #3 on that same thread mentions "partially supported" Broadcom chipsets using the "b43" open source driver.  It looks like the "b43" driver *is supposed to* support monitor mode from what I read further on in that thread.

[http://ubuntuforums.org/showthread.php?t=1655021](http://ubuntuforums.org/showthread.php?t=1655021)

---

### Post by triduonghuu on 2011-05-13
Hi northd_tech, with 10.04 x64, it worked with my bcm4312.
You can try it with ppa backports.
**sudo apt-get install linux-backports-modules-wireless-`uname -r`**
Hope that help.

---

### Post by northd_tech on 2011-05-13
> **triduonghuu said:**
> Hi northd_tech, with 10.04 x64, it worked with my bcm4312.
You can try it with ppa backports.
**sudo apt-get install linux-backports-modules-wireless-`uname -r`**
Hope that help.

Thank you tri,

I'm in the process of re-configuring a "b43[xx?]" Broadcom wireless setup (that apparently now needs some firmware to match its new "b43" & "ssb" modules- SURPRISE!! :) )- this after blasting out my **long-term WORKING "STA" setup** just so that I can 'feel the pain of others' (and take some good notes and screenshots on what DID vs. DID NOT work for me on my "4328"/"4321AG" Broadcom wireless in my personal laptop).

Unfortunately, I need to travel about halfway across the state in the morning to help a friend move some furniture for a few days- thanks again for the tip.

(posting from Vista64's WiFi AGAIN- :(),
NDT

---

