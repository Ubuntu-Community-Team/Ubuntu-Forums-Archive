---
title: "connecting to wireless router in ubuntu"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by shizumasa14 on 2009-03-31
I read somewhere online to go to Preferences>Administration>Network.  There is nothing that says network....  how do I connect?  Unfortunately I don't know what kind of router it is because it is my dad's and he won't let me near it.  Or tell me about it.  I just know that it worked in Windows.

1. How were you trying to get online? Ethernet wired, and wireless router.

2. What hardware are you using?  I am using an Acer Aspire 4720z.  The modem that I bought for myself a while ago is an ARRIS.

3. Who is your Internet Service Provider?  Comcast Cable in the United States.

4. Which version of Ubuntu are you using?  Ubuntu 8.10 Intrepid Ibex.

5. Can you get online with any other method?  No.  I have tried using an ARRIS cable modem, but it doesn't work either.

6. How are you getting online to post on this forum?  My mothers Compaq Presario SR1650NX desktop computer running Windows XP.

7. For wifi - what encryption are you using? Have you tried an open network? What wifi channel do you use?  I have no idea.  What does this mean?

8. Do you dual-boot with Windows? Nope

9. Include the output from the following commands from Terminal.

```

ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com

```

I will do #9 later.

---

### Post by BkkBonanza on 2009-03-31
You probably want to use Network Manager. 
It allows you to manage your wifi connection.
I no longer have it as I use Wicd (better!) but I think it used to be on the System, Administration menu.

Output from ifconfig and iwconfig will certainly help if there is a problem. 

Don't worry about encryption until you actually have a list of access points. Your Dad is smart so he's using WAP2 and you won't be able to get in unless you can guess his password - and if you can guess then, well, not so smart.

---

### Post by shizumasa14 on 2009-03-31
How do I get to network manager?  In the Administration menu there is an option called network tools.  Is that what you want?  Also, what do I do once I get there?

---

### Post by shizumasa14 on 2009-03-31
```

shizumasa14@shizumasa14-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:d7:2a:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:330280736 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB) 

shizumasa14@shizumasa14-laptop:~$ 

```



```

shizumasa14@shizumasa14-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

shizumasa14@shizumasa14-laptop:~$ 

```

---

### Post by freonchill on 2009-04-01
is it not on your panel by default?

what version are you running? < 7.04/7.10

---

### Post by BkkBonanza on 2009-04-01
Your ifconfig output doesn't show a wifi card. You can run 

ifconfig -a

and if that does show a wifi card then you need to start up the wifi card. If so then try,

sudo ifconfig wlan0 up

(assuming the wifi card shows as wlan0 - it may be something else)

If you don't get any additional cards that look like wifi in the output from above then it means you don't the wifi card enabled/installed.

---

### Post by shizumasa14 on 2009-04-06
I am running 8.10 and no it is not in my panel by default.  

I tried the ifconfig -a but didn't see anything....

I know I have a wireless card because I was able to connect to my dads router on the same computer while running Vista.

---

### Post by BkkBonanza on 2009-04-06
I would guess you have an Intel wireless card. It may help if you know what it is. The Intel one usually gets installed and setup by default in recent Ubuntus. I know this because I have an Acer 4920 with an Intel 4965 card. It was ready to use after I installed Ubuntu. So it's a bit strange that it isn't showing up.

I guess you could try to load the drivers for it (if you have Intel that is),

sudo modprobe iwlagn

I removed Netowrk Manager so I can't say off hand where it was but it may have been on menu Applications, Internet. Network Tools is not what you want. You could try using Synaptic to check that Network Manager is installed. If you did a normal install I don't know why it wouldn't be.

---

