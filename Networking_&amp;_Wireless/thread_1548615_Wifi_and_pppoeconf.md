---
title: "Wifi and pppoeconf"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by uptime365 on 2010-08-08
Hi all, 

New here on forums, I have been using ubuntu for a while and thanks for making such a wonderful OS. :)

I have a home PC and a netbook, both installed with ubuntu 10.4 . I am accessing the net through modem wa3002-g1 and it is connected to the main PC in bridged mode. Everything is fine there and I am happy with my PC. On my netbook wifi worked out of box and it was connected to the modem with minimum configuration ( via Network Manager).

Now the issue is when I tries to connect netbook to internet using pppoeconf. I'm able to give my user_name and password and configure it but on plog 'm getting the below error 
----------
Timeout waiting for PADS packets
Unable to complete PPPoe Discovery
----------
I tried pppoe-discovery  and 'm getting 
----------
Timeout waiting for PAD0 packets 
----------

Don't know if 'm doing something wrong..

---

### Post by dineshs on 2010-08-09
Did you try setting the connection via the DSL tab in NM?
After running pppoeconf did you reboot?Is your NM icon still there?
pl try this
[http://ubuntuforums.org/showthread.php?p=9611450#post9611450](http://ubuntuforums.org/showthread.php?p=9611450#post9611450)
Is there any particular reason for using bridge mode?You can configure your modem in PPPoE
see this link=click modem/cpe config
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

### Post by uptime365 on 2010-08-09
Thanks Dineshs,

Yeah the same issue happened after using pppoeconf and rebooting ( NM  disappeared ) and I have restored it with the steps that you have given.

I tried setting the connection with DSL tab, but it is not connecting, I  couldn't find  on NM icon `DSL connection 1' that I have configured to  click and activate it.

With the modem I am using ( wa3002-g1 ) I can't open some sites while it  is configured on PPPoE mode . It is a known issue and I couldn't find a  solution anywhere for that. :(

Thanks for your assistance. Hope you can help me out 

Uptime

---

### Post by dineshs on 2010-08-09
> With the modem I am using ( wa3002-g1 ) I can't open some sites while it is configured on PPPoE mode . It is a known issue and I couldn't find a solution anywhere for that. 
While configuring the modem in PPPoE mode you will see an option for MTU.Set MTU as 1492 first and see(You may also try 1482 or 1462)
> I tried setting the connection with DSL tab, but it is not connecting, I couldn't find on NM icon `DSL connection 1' that I have configured to click and activate it.Did you tick the option `Available to all users' while configuring?

---

### Post by uptime365 on 2010-08-09
>> Have tried different values with MTU on PPPoE mode.. not working still 

>> Yeah `Available to all users' is ticked , I have also tried with/without 'connect Automatically' still couldn't connect 

Thanks,
Uptime

---

### Post by dineshs on 2010-08-09
May be you have tried all these but ...
> I couldn't find on NM icon `DSL connection 1' that I have configured to click and activate it.click on NM icon not right click
Let the modem be in PPPoE mode.Configure NM with these settings(nedd not change IP mask and gateway)

NM right click NM icon-edit conn-wired-eth0-under wired try changing MTU to 1492
under ipv4 Give DNS as 4.2.2.1 then apply
You may restart

---

### Post by uptime365 on 2010-08-14
Hi,

Tried everything  

>> MTU to 1492, 1482 or 1462 
>> stopped modem firewall
>> reset the modem to factory default settings and configured pppoe again
>> reinstalled OS to a 64 bit Linux-Mint and tried with it.

Still not working. Sites like webhostingtalk.com paypal.com and also some pages that require secure login are not working. Thanks for all the help, do anyone have an idea. :(   :confused:

Thanks,
Uptime

---

