---
title: "No internet connection (wired)"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by fs_tigre on 2009-05-16
Hi,

I just installed Ubuntu 8.10 in my second laptop (acer Aspire 3680) after successfully installed it on one of my desktops and on my other laptop but for some reason on this one I cannot connect to the internet, I'm using ethernet cable (wired) to connect to the router. I tried to ping my router but nothing no response.

Any idea what do I need to do?

Thanks

---

### Post by Adina on 2009-05-16
Open a terminal and write:

sudo /etc/init.d/networking restart

Then try to ping your router again.

---

### Post by fs_tigre on 2009-05-16
First of all thank you for your quick reply.

I tried what you suggested me to do and tried ping the routing but still no response.

Thanks

---

### Post by Adina on 2009-05-16
Do you have an ip-adress on your computer?

open a terminal and type: ifconfig

post the result.

---

### Post by fs_tigre on 2009-05-16
This is what I got after entering "ifconfig

Thank your help!

> eth0      Link encap:Ethernet  HWaddr 00:16:36:f9:ca:35  
          inet6 addr: fe80::216:36ff:fef9:ca35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5484 (5.4 KB)  TX bytes:2304 (2.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20468 (20.4 KB)  TX bytes:20468 (20.4 KB)


---

### Post by Adina on 2009-05-16
It seems you don't have an ip-adress on eth0.

if you get an ip automaticaly from your router (dhcp) you can try open a terminal and type:

sudo ifconfig eth0 dynamic

and then maybe bring your interface down and up again with:

sudo ifconfig eth0 down

sudo ifconfig etho up

or this again:

sudo /etc/init.d/networking restart

by the way, have you tried looking in any of the ubuntu documentation?


[https://help.ubuntu.com/]("https://help.ubuntu.com/")

---

### Post by fs_tigre on 2009-05-16
I know, I know it me again. I went and read the documentation and found some help. This is what have done.

> IPv6 Not Supported
IPv6 is supported by default in Ubuntu and can sometimes cause problems.

To disable it, open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.

Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.

Reboot Ubuntu.

And now i see good connection to the internet it just doesn't let me browse any pages.

Any idea why?

Thanks

---

### Post by karatedog on 2009-05-17
I also have problems with my network (inside Virtualbox), sometimes it say it is disconnected, and in no way can I bring it up with console commands... 
This solution worked for me:
- right click networking icon
- select "Edit connections"
- select network interface, then Edit
- deselect "Connect automatically" checkbox, click Apply, and close the window
Now repeat this process, but this time select the "Connect automatically" checkbox.
This is working for me, where as "sudo /etc/init.d/networking restart" won't.

---

### Post by H.K.Murmu on 2009-05-17
I have the same problem and always use pppoeconf to connect internet. But now I am able to connect through network manager applet no need to open a terminal.

To connect through ADSL modem you have to configure your modem device by self or take it to your service provider. Once configured then follow the steps
1:-system----adminstration------user and groups

2:-In user setting select user-----properties---check the box "connect to internet using modem" and "connect to wireless and ethernet networks" then close

3:- open network manager applet from panel under DSL ---ADD---Edit DSL connection-----in tab DSL provide internet userid and password and under tab IPv4 setting select "automatic pppoe" and then close(perhaps require restart system, not sure)

4:-In panel left click network manager applet and click the radio button

5-now you are connected to internet through Network manager Applet

Best of luck

---

### Post by fs_tigre on 2009-05-17
Thank you all it is now working, I created a new connection and it did the trick.

Thanks

---

