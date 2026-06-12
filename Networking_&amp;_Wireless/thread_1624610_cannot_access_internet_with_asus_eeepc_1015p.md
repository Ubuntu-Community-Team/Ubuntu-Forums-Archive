---
title: "cannot access internet with asus eeepc 1015p"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by goodbyemrevans on 2010-11-17
hello, this is my first post, i'm a total newbie.

i've just installed ubuntu netbook remix 10.10 on my asus eeepc 1015p.  whether i use an ethernet cable or wireless, i *can* establish a connection, but i can't access any websites through firefox or get software via the software manager.

i've attached some terminal screenshots from my attempts at troubleshooting, which i think contain all the relevant hardware info.

i've already searched the forums and see a lot of problems similar to mine, but none seem to involve the same combination of hardware / ubuntu version as me.  since i have no experience, i'm hesitant to try to apply solutions that i don't understand and in which i'm not totally confident.

thank you in advance for your help and i hope this isn't a redundant thread.

---

### Post by dineshs on 2010-11-18
You may first try the wired part .Please connect the cable and post the result of ```
ping 4.2.2.1 -c3
```and ```
route -n
```
Also disable ipv6 following
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by goodbyemrevans on 2010-11-18
please find below a screenshot of the results of the commands you suggested.

i can't get beyond the first step of the disabling ipv6 tutorial...when i type
```

gksudo gedit  /etc/modprobe.d/aliases
```i get what appears to be a blank file...?

---

### Post by goodbyemrevans on 2010-11-18
[IMG]http://img43.imageshack.us/img43/8190/44234843.png[/IMG]

---

### Post by dineshs on 2010-11-18
Please try this
Rightclick the NM icon (on top right of the panel,the two opposite arrows in your case)then click edit connections-click on the wired connection listed,then edit-click ipv4-
method-Automatic DHCP addresses only
Enter DNS as [COLOR="Blue"]4.2.2.1[/COLOR] click apply.
Try if pages are loading (if not you may reboot and try again)
To disable ipv6 (ref [http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can](http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can))
> 
   1. In the Location bar, type about:config and press Enter
          * The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise!, to continue to the about:config page. 
   2. In the Filter field, type network.dns.disableIPv6.
   3. In the list of preferences, double-click network.dns.disableIPv6 to set its value to true. 

---

### Post by goodbyemrevans on 2010-11-19
Thank you very much!  I can now connect via ethernet at my workplace.  I changed the DNS settings and that was enough; i didn't need to disable ipv6

I have a couple questions:

1. will this fix work connecting anywhere, or is it to specific to this one location?

2. for setting up wireless, should i provide screenshots of the results of the same terminal commands as before?

Thanks again

---

### Post by dineshs on 2010-11-20
> 1. will this fix work connecting anywhere, or is it to specific to this one location?
Open DNS should work anywhere.But it is always better to configure NM with the DNS addresses given by your ISP.If you want to enter more than one DNS address put a comma in betweeen.For example [COLOR="Blue"]4.2.2.1,8.8.8.8[/COLOR]
> 2. for setting up wireless, should i provide screenshots of the results of the same terminal commands as before?
Remove your ethernet cable,connect wireless and post the result of ```
iwconfig
``` and ```
ifconfig -a
``` (use the code tag ie # symbol instead of screenshot)

---

### Post by goodbyemrevans on 2011-05-08
i'm going to mark this as solved because the wireless started working 'on its own', before i made any changes...weird, huh?

sorry for the delay

---

