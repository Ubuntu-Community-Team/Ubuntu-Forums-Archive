---
title: "Please Help"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by anvith on 2010-08-21
Guys im posting this again since i never got a response for this,Guys plez help me with this

Im working wiht Ubuntu 10.04 Edition ,as such I intially noticed that mozilla was unable to connect to the internet, further still ANy other applications were also unable to do so;Bt ya theres one exception I was able to download packages using the [COLOR=Blue]terminal [/COLOR]which quite obviously suggests [COLOR=Blue]that its able to connect[/COLOR].

Further still as far as my assumption goes ,the[COLOR=Black] other ports wud hav been blocked[/COLOR](quite rare) but when i ping, I get a response.

Further still I dint have such problems with previous versions till 9.04,post 9.04 ive been experiencing this problems,To confirm the same I reinstalled 9.04 version and things go gr8 as usual and im able to connect.

Im not able to figure out the problem plez post a response guys.Thanx in adv

--------------------------------------------------------------------------------------------------------
                  ---"Its never too l8 to **Help**, **Realize** and **Correct**":razz:

---

### Post by linux18 on 2010-08-21
if your connected to an ethernet cable:

ifconfig eth0 up
dhclient eth0

---

### Post by silbak04 on 2010-08-21
what is your output when you type this in the terminal ```
$ cat  /etc/network/interfaces 
``` it should look some thing like this  ```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.x
gateway 192.168.1.x 
``` where 'x' is some number according your ip address, netmask, and gateway...typically you want your ip to be static...especially when down the road you may want to ssh into your computer from work or something...you don't want to have an ip that always changes, which is what dhcp does...

then type this in the terminal after fixing up your 'interfaces' file ```
$ sudo /etc/init.d/networking restart
```

---

### Post by prshah on 2010-08-21
> **anvith said:**
> 
Im working wiht Ubuntu 10.04 Edition ,as such I intially noticed that mozilla was unable to connect to the internet,[/COLOR].


> **silbak04 said:**
> ```
$ sudo /etc/init.d/networking restart
```

@silbak: From 10.04 onwards, please use the new "service" command, eg```
sudo service networking restart
``` The init.d method is going to be deprecated in future releases.

@OP: You can possibly have the following issues:

a) DNS servers are not correct: Please post the output of "/etc/resolv.conf" file to check this. Or try to browse to [http://209.85.231.104](http://209.85.231.104) (google) and see if Google opens up. If it does, then it's a DNS (or MTU) issue, please post back for details on how to resolve.

b) Check the MTU: 
See [ Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution.

Summary hint: Change the MTU (to 1492, or so)

c) Ensure that in Firefox, File-Work Offline is not checked (ticked).

Please post back with results, or for more details if you need them.

---

