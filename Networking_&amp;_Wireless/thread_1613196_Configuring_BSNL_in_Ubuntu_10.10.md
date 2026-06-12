---
title: "Configuring BSNL in Ubuntu 10.10"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by aniearendil on 2010-11-04
Hey i'm new to the ubuntu way of life and am having trouble accessing the internet...

pls help me.... much obliged!! :)

---

### Post by aniearendil on 2010-11-04
Hello?!? 

ok what happens is this....

i plug in the ethernet cable, the icon on the panel spins around and then it finally says 

**Wired Connection**

[B]Disconnected

[/B]Now, i followed whatever was given on this page

[http://www.etalkindia.com/computer_software_troubleshooting/how_to_connect_bsnl_internet_in_ubuntu_linuxbroadband-t2538.0.html](http://www.etalkindia.com/computer_software_troubleshooting/how_to_connect_bsnl_internet_in_ubuntu_linuxbroadband-t2538.0.html)

till the **System>Administration>Networking** part.... cos Ubuntu 10.10 that i'm using doesn't have any options like Networking under Administration.... nor does the Network Tools options that IS available contain any such things that is described in that post... 
[COLOR=Blue]

[/COLOR][COLOR=Blue]*_**PLS HELP ME GUYS!!!!**_*[/COLOR]

---

### Post by dineshs on 2010-11-04
There is a network manager icon on top right of the panel.
By the way can you ping modem/router?Please post results of```
sudo lshw -C network
``````
sudo gedit /etc/network/interfaces
```and ```
ping -c3 192.168.1.1
```assuming 192.168.1.1 is your modem IP

---

### Post by aniearendil on 2010-11-06
Thanks a lot,man... am accessing internet frm ubuntu now :-) :-)

---

### Post by aniearendil on 2010-11-07
hey it's stopped working again... AND the network notification icon on  my top right-hand side panel is missing.... when i tried entering the  codes u had given again i nthe terminal, it said network is missing or  something.....

---

### Post by cracker89 on 2010-11-07
> **aniearendil said:**
> hey it's stopped working again... AND the network notification icon on  my top right-hand side panel is missing.... when i tried entering the  codes u had given again i nthe terminal, it said network is missing or  something.....


Please post the output of

```
 lspci -v
rfkill list

```

---

### Post by dineshs on 2010-11-07
Did you run *sudo pppoeconf*?
If yes try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
(After editing /etc/network/interfaces as explained in the link you can either click DSL connection created via NM or run [COLOR="Blue"]sudo pon dsl-provider[/COLOR] commandto connect to internet.Do not run sudo pppoeconf)

---

