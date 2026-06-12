---
title: "Can't connect to wired network."
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by RobertRahm on 2010-06-08
Hi all, I am a rather new Ubuntu user. I have an hp netbook.
 
I got the computer to use as a sort of "total emerssion" tool to learn ubuntu (I really like the idea of Ubuntu and open-source software in general.) So it no longer has Windows on it. When I installed Ubuntu 10.4 I was able to connect to the internet using an ethernet cable. I had to follow some online instrutions to get the wireless set up.
 
 
I had everything set up perfectly and running smoothly. And then I did the unthinkable: I installed some update packages a few days ago. Now, I cannot connect to the internet using either an ethernet cable nor wirelessly. 
 
 
Perhaps there is some hardware problem, I don't know. But I am hoping that one of you guys can help me. 
 
 
When I enter the command "ifconfig' here is what I get:
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:1275 errors:0 dropped:0 overruns:0 frame:0 
TX packets:1275 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:144049 (144.0 KB) TX bytes:144049 (144.0 KB)
 
 
So, this seems odd to me (though I might be wrong) since it isn't even listing ethernet connections.
 
Thanks for the help, guygs.

---

### Post by chili555 on 2010-06-08
Let's begin at the beginning. We'll use the terminal to list your PCI devices.```
lspci -nn
```Omit all the items not related to your ethernet device and post the result here. We'll then have a better idea how to proceed.

---

### Post by RobertRahm on 2010-06-08
01:00.0 PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:
4325] (rev01)
 
 
Thanks.

---

### Post by chili555 on 2010-06-08
> 01:00.0 PCI Express Fast Ethernet controller [[COLOR="Red"]10ec:8136[/COLOR]] (rev 02)This device is supposed to use the module *r8169*. Let's load it and see if your ethernet comes alive:```
sudo modprobe r8169
```Is an interface created?```
iwconfig
```If not, please post:```
dmesg | grep 816
```Thanks.

---

### Post by Detonate on 2010-06-08
I think he means ```
ifconfig
```

iwconfig is for wireless devices.

If ifconfig does not show your Ethernet controller run ```
ifconfig -a
```

ifconfig by itself only lists active controllers, if config -a will list all controllers, active and inactive.

---

### Post by chili555 on 2010-06-08
> I think he means
Code:

ifconfig

iwconfig is for wireless devices.Quite correct. Sorry for the error.

---

### Post by RobertRahm on 2010-06-08
OK, I entered the commands, and here is the output:
 
sudo modprobe r8169:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored it a future release. 
 
 
ifconfig (I did this after entering ifconfig eth0 up and ifconfig eth1 up):
eth0 Link encap:Ethernet HWaddr c8:0a:a9:22:e0:e1 
inet6 addr: fe80::ca0a:a9ff:fe22:e0e1/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1975 (1.9 KB) TX bytes:468 (468.0 B)
Interrupt:27 Base address:0x4000 
 
eth1 Link encap:Ethernet HWaddr c4:17:fe:bd:db:31 
inet6 addr: fe80::c617:feff:febd:db31/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:944 errors:0 dropped:0 overruns:0 frame:0
TX packets:944 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:114772 (114.7 KB) TX bytes:114772 (114.7 KB)
 
dmesg | grep 816:
[ 1.068329] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.068374] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.068442] r8169 0000:01:00.0: setting latency timer to 64
[ 1.068603] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[ 774.394366] r8169 0000:01:00.0: PME# enabled
[ 774.821199] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 775.064768] r8169 0000:01:00.0: PME# disabled
[ 779.388164] Synaptics: Clickpad mode enabled
[ 787.192875] r8169 0000:01:00.0: PME# enabled
[ 787.621189] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 787.864775] r8169 0000:01:00.0: PME# disabled
[ 2573.692889] r8169 0000:01:00.0: PME# enabled
[ 2574.121187] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2574.364776] r8169 0000:01:00.0: PME# disabled
[ 2630.536888] r8169 0000:01:00.0: PME# enabled
[ 2630.965192] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2631.208773] r8169 0000:01:00.0: PME# disabled
[ 2851.664889] r8169 0000:01:00.0: PME# enabled
[ 2852.093201] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2852.336774] r8169 0000:01:00.0: PME# disabled
[ 3174.766358] r8169: eth0: link up
[ 3174.766380] r8169: eth0: link up
[ 3369.838238] r8169: eth0: link up
[ 3447.933741] r8169: eth0: link up
[ 3607.754283] r8169: eth0: link down
[ 3629.304951] r8169 0000:01:00.0: PME# enabled
[ 3629.733188] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 3629.881613] [drm] Big FIFO is enabled
[ 3629.976832] r8169 0000:01:00.0: PME# disabled
[ 3629.992154] r8169: eth0: link down
[ 3630.543292] r8169: eth0: link up
[ 3668.066332] r8169: eth0: link up
[ 3728.213553] r8169: eth0: link down
[ 3730.191077] r8169: eth0: link up
[ 4273.839424] r8169: eth0: link down
[ 4284.216945] r8169 0000:01:00.0: PME# enabled
[ 4284.645189] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4284.888830] r8169 0000:01:00.0: PME# disabled
[ 4284.904155] r8169: eth0: link down
[ 4391.712950] r8169 0000:01:00.0: PME# enabled
[ 4392.141187] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4392.384830] r8169 0000:01:00.0: PME# disabled
[ 4392.400152] r8169: eth0: link down
[ 4396.654157] r8169: eth0: link up
[ 4397.346118] r8169: eth0: link down
[ 4398.918372] r8169: eth0: link up
[ 4529.868162] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 4530.016947] r8169 0000:01:00.0: PME# enabled
[ 4530.445197] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4530.688827] r8169 0000:01:00.0: PME# disabled
[ 4530.704152] r8169: eth0: link down
[ 4531.255014] r8169: eth0: link up
 
 
 
I still cannot connect to the internet. 
 
By the way, what does modprobe do? And what does dmesg | grep 816 do? Is there some resource online where I can learn the commands? I know several, things like mkdir, mv, etc., but there are a lot that I don't know and some like chmod 777 that I use, but I don't really understand the syntax or why "chmod 777" makes a file executable. I'd really like to learn as much as I can about Ubuntu and other open-source stuff as I can so I can contribute at some point. So, I'm sorry if some of this stuff is too basic, but I appreciate your help.

---

### Post by Detonate on 2010-06-08
OK, we have established that your network controller, eth0 is present.  Now I want you to follow my instructions in post #7 in this thread.

[http://ubuntuforums.org/showthread.php?t=1494628](http://ubuntuforums.org/showthread.php?t=1494628)

---

### Post by chili555 on 2010-06-08
> I had to follow some online instrutions to get the wireless set up.If he has and uses a wireless connection, why do you suggest he remove Network Manager? If he is a beginner at terminal commands, how is he going to switch to wireless when needed? 

I am skeptical that this is the best solution.

---

### Post by Detonate on 2010-06-08
Once he gets his wired network up and running, I will have him install wicd.  And if my way fails to get his wired network running, we can always reinstall network manager from the CD.

---

### Post by chili555 on 2010-06-08
I will watch with interest.

---

### Post by Detonate on 2010-06-08
I've helped many people having problems with network manager get their networking up and running.  I have posted my "howto" on three different forums and have received many "Thank yous".  I know it works, and it is straight forward and uncomplicated.  I do want to apologize though, for jumping in a thread where you had already started rendering assistance. Bad form on my part.  Won't happen again.

---

### Post by chili555 on 2010-06-08
Please carry on; I will watch with interest.

---

### Post by RobertRahm on 2010-06-08
Ok, I did exactly what you said and I am pleased to say that I am now connected to the internet. Thanks guys.

But, I do have some questions. I just reopened the resolv.conf file and this is what it says:

namesaver 192.168.2.1
domain copeland
search copeland 


I am house sitting for a guy named copeland, and it is his router. I got the ip address simply by using ipconfig in the windows command prompt. So when I want to connect at home to I just need to add :

nameserver <ip address>

to this file?


So, let me see if I understand what I just did:
Some piece of software looks at the interfaces file and the resolv.conf file to connect to the internet and to find websites. I told it the ip address from which I was connecting in this resolv.conf file. Normally this is handled by some GUI ap., but I did it the "manual way." 

Is this close? I am a Math major/ CS minor but I haven't taken many CS courses and no specific networking courses so a lot of this stuff is new to me, but VERY interesting to me. 


So now, I saw something about wcfig or something to connect wirelessly, how do I go about installing this? 

Again, thanks guys for getting me to this point.

---

### Post by Detonate on 2010-06-08
If you are using DHCP, don't worry about the resolve.conf file.  It is automatically rewritten each time you connect.  You only need to edit it and supply the nameservers if you are using a static IP.

Do you intend to use your wireless?  If so now that you are connected, you should install a network manager that handle s wireless connections, and the best one I know of is wicd.

Wicd will also handle your wired connection, but we could not install it before because it is not on the CD, but it is in the repoitories, so all you have to do is:

```
sudo apt-get install wicd
```.

You will then find the icon for it under Applications>Internet.  It is easy to use and if you have any problems figuring it out post back.

---

### Post by eventhorizonof on 2010-06-08
@Detonate I am attempting to follow your directions as I too am having a problem with my wired connection but it seems that I have no way of obtaining my IP address for one of the steps you have outlined. In network tools it is listed as all zeros and I cannot seem to see it using ifconfig. Where should I go from here?

---

### Post by RobertRahm on 2010-06-08
I did it, and it works. Again, thanks a lot guys!

---

### Post by Detonate on 2010-06-08
> **eventhorizonof said:**
> @Detonate I am attempting to follow your directions as I too am having a problem with my wired connection but it seems that I have no way of obtaining my IP address for one of the steps you have outlined. In network tools it is listed as all zeros and I cannot seem to see it using ifconfig. Where should I go from here?

Which step are you having a problem with?  You don't obtain and IP address until you are connected.  Are we getting the cart before the horse?

---

### Post by eventhorizonof on 2010-06-08
the IP I am getting is 169.254.5.245 I am under the impression that this indicates a problem is this correct? Is my hardware being recognized correctly?

---

### Post by Detonate on 2010-06-09
That's a local link.  Where are you getting this from?  Have you run ifconfig?  Please run it and post the results.

---

### Post by Detonate on 2010-06-09
I won't be back tonight.  Past an old man's bedtime.  I'll check back in tomorrow morning.

---

### Post by elliryn on 2010-06-09
Hi, sorry to hijack the thread, but I'm having a similar problem with the original poster so I thought it'd be better to post in this thread instead of starting a new one.
 
I'm using a HP netbook with a Broadcom BCM4312. I've followed all the steps [on here]("http://ubuntuforums.org/showpost.php?p=9378388&postcount=7") up to the final "sudo /etc/init.d/networking restart" command, but this is what I got:
 
```
Listening on LPF/eth0/00:22:64:66:ff:53
Sending on LPF/eth0/00:22:64:ff:53
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
 
Apparently it's still not working - any idea why? ):

---

### Post by Detonate on 2010-06-09
The instructions are for a wired (Ethernet)  connection, not wireless.  Hook up your computer with a wired connection, and install wicd.  It should handle your wireless problems.

---

### Post by eventhorizonof on 2010-06-09
results of ifconfig:


ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet6 addr: fe80::4261:86ff:fe8e:9a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205226 (205.2 KB)  TX bytes:4447 (4.4 KB)
          Interrupt:26 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet addr:169.254.6.168  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by Detonate on 2010-06-09
The IP address you see is produced by the avahi-daemon to identify resources on the local network.  It is part of the Zero-Config utility that is loaded by default in Ubuntu.  If you don't need it, which you don't if you already have all of your network resources identified and mounted, kill it and remove it from startup.  My favorite tool for managing processes, to stop, start, and remove from startup is webmin.  

Follow my instructions referred to earlier, and you will be up and running.

---

### Post by elliryn on 2010-06-09
> **Detonate said:**
> The instructions are for a wired (Ethernet) connection, not wireless. Hook up your computer with a wired connection, and install wicd. It should handle your wireless problems.
 
Actually, the problem is neither works for me - wired or wireless, which is why I was trying to get the wired connection working first. I guess that's not how it goes then? :confused:

---

### Post by eventhorizonof on 2010-06-09
I followed your directions and am still unable to connect.

interfaces file:

auto lo
iface lo inet loopback
address 169.254.5.245
netmask 255.255.0.0

auto eth0
iface eth0 inet dhcp


resolv.conf file:

# Generated by NetworkManager
nameserver 68.87.64.150      # Primary DNS comcast phila
nameserver 68.87.75.198      # Secondary DNS comcast phila
nameserver 192.168.100.1     # Motorola SB 5120

Did i do something incorrectly?

---

### Post by DavorC on 2010-06-09
> **Detonate said:**
> I've helped many people having problems with network manager get their networking up and running.  I have posted my "howto" on three different forums and have received many "Thank yous".  I know it works, and it is straight forward and uncomplicated.  I do want to apologize though, for jumping in a thread where you had already started rendering assistance. Bad form on my part.  Won't happen again.

It would be nice if you explained what your instructions do because they do not fix the problem with the Network Manager that the user is having, but essentially blow it out of the way and replace with an alternate way of managing the networking. 

And given that NM is the default way for handling networking in recent versions of Ubuntu, I would think it's better to a) stick with it if possible, because the rest of the system integrates with it; and b) diagnose its bugs so we can report them back to Ubuntu and get them fixed.

Item (a) is important, because when I had a similar problem to the OP, I initially solved it like Detonate and hacked my /etc/network/interfaces to get back online. But then Firefox would start in offline mode, for example. Fixing the real problem in the Network Manager also fixed Firefox, not to mention that I now have a nice "you're online" icon now in the panel!

In my case, the problem was that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

(But don't do this if you've already started modifying your /etc/network/interfaces, NM won't interfere if you started managing them manually.)

---

### Post by Detonate on 2010-06-09
> **elliryn said:**
> Actually, the problem is neither works for me - wired or wireless, which is why I was trying to get the wired connection working first. I guess that's not how it goes then? :confused:

Well, actually that is how it goes.  But in your original post you referred to your BCM4312, which is your wireless device.

---

### Post by Detonate on 2010-06-09
> **DavorC said:**
> It would be nice if you explained what your instructions do because they do not fix the problem with the Network Manager that the user is having, but essentially blow it out of the way and replace with an alternate way of managing the networking. 


OK, I agree with that.  I am going to edit the post to add a paragraph at the beginning to clarify.

---

### Post by kaufmed on 2010-06-09
@RobertRahm

**modprobe** is a utility on linux that loads/unloads modules into your system. Think of modules like performance parts on a car (but don't focus too much on the "performance" part). Without the extra parts, your car will still run, but it will run in a different way (e.g. use more gas, not accelerate as fast, etc.). Each part is a module in that it can be added removed at will.

Let's assume, for the sake of this description, that your intake manifold was welded on. You would not be able to remove it. Some feature of linux are built in to the kernel (the engine of your computer). This makes your engine heavier/bigger (and the same goes for the kernel). Modules allow you to remove functionality from your kernel that you don't need, much the same way you can remove/add parts to you car.

**dmesg** is a utility for viewing the system log file.

**grep** is a pattern matching utility used to search for a particular string/pattern in a line of a file.

In his/her post, chili555 had you pipe ( | ), or reroute, the results of executing the **dmesg **utility to **grep**. **grep **was used to only print the lines which had the string "816" in them. This kept you from having to search the whole file.

>>  I don't really understand the syntax or why "chmod 777" makes a file  executable

See: [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

For any commands you are not familiar with (but know the name of), you can usually do a "man [command name]" to see the utility's "man page", or manual. When viewing the man page, you can hit "q" to exit. Also, not every utility has a man page, but I believe most do.

As far as learning commands you don't know the name of, that typically comes from experience (and [insert favorite search engine here]'ing). I would recommend a good book to you, but I've never read any myself. Everything I know about Linux has come from school and (mostly) the web.

---

### Post by kaufmed on 2010-06-09
>>  This kept you from having to search the whole file.

By this I mean kept you from having to scan (with your eyes) the entire contents of the result of executing **dmesg **for the string in question.

---

### Post by eventhorizonof on 2010-06-09
I still can't get on the internet, any one know what the problem is? What should I do please help.

[http://ubuntuforums.org/showthread.php?t=1500702](http://ubuntuforums.org/showthread.php?t=1500702)

---

### Post by Detonate on 2010-06-09
Go thru my instructions one step at a time, don't skip any steps. When you hit a problem, post back.

---

### Post by eventhorizonof on 2010-06-09
I will detail everything I have done in this post. If you could kindly point out my error(s) that would be greatly appreciated.

After uninstalling NM the results of the ifconfig command are:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet6 addr: fe80::4261:86ff:fe8e:9a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205226 (205.2 KB)  TX bytes:4447 (4.4 KB)
          Interrupt:26 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet addr:169.254.6.168  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


Next I proceed by editing the interfaces file:


auto lo
iface lo inet loopback
address 127.0.0.1      
netmask 255.255.0.0    

auto eth0
iface eth0 inet dhcp

# what exactly is the address in this file?
# my netmask has an extra 255 im assuming yours doesnt?

next I proceeded to edit the resolv.conf file to:

# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.100.1   # my router address motorola SB 5120

I then ran the networking restart code and got:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1594
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:8e:9a:08
Sending on   LPF/eth0/40:61:86:8e:9a:08
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:8e:9a:08
Sending on   LPF/eth0/40:61:86:8e:9a:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                      



The internet still wont connect what have I done wrong? Thank you.

---

### Post by Detonate on 2010-06-09
You are using dhcp with that interfaces file.  So, no need to edit you resolv.conf file, it will be overwritten by dhclient anyway.  Just rename the file for now.

Change your netmask to 255.0.0.0

Then run in a terminal:

sudo rm /var/run/dhclient.eth0.pid

If you get an error message, let me know.

Then restart the network again.

---

### Post by eventhorizonof on 2010-06-09
I did those things. Here is the output upon restarting the network:

 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:8e:9a:08
Sending on   LPF/eth0/40:61:86:8e:9a:08
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:8e:9a:08
Sending on   LPF/eth0/40:61:86:8e:9a:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Detonate on 2010-06-09
Are you sure you have your cable connected to the correct port on your computer?  Do you know the IP address to the gateway of your router?  If not post back the exact make and model of your router and I will find out what it is for you.  If you know it, ping it.

```
ping (router address goes here)
```

---

### Post by eventhorizonof on 2010-06-09
the router is a motorola surfboard model SB5120

[http://broadband.motorola.com/consumers/products/sb5120/](http://broadband.motorola.com/consumers/products/sb5120/)

I tried pinging it earlier to no avail

this is the address I think it is:

192.168.100.1

---

### Post by eventhorizonof on 2010-06-09
pinging this address is actually giving the following:

connect: Network is unreachable

I have confirmed that this is the correct modem address. I am using the same connection on a windows machine so the connection is good. Any reason why I wouldnt even be able to ping in ubuntu?

---

### Post by Detonate on 2010-06-09
192.168.100.1 is the correct address.  If you can't ping it using that, your problem is hardware related.  We know eth0 is installed correctly and active, so either the modem itself is not working, or you have a bad cable.  I repeat my earlier question "Are you sure the cable is plugged into the correct port on your computer".  I think your computer would have two ports, one for eth0 and one for eth1.

---

### Post by elliryn on 2010-06-09
> **Detonate said:**
> Well, actually that is how it goes. But in your original post you referred to your BCM4312, which is your wireless device.
 
Ahh, sorry about that. Not too good with this :p
 
I seem to be having the exact same responses that eventhorizonof is getting, but I'm certain that my cable is working fine because it's the same cable I'm using for my PC, which connects just fine. There's no second port to plug the cable in either, so the port I'm using has to be it, I think.
 
This is my resolv.conf file. I don't think I'm using a router...?
 
```
nameserver 218.186.1.58
nameserver 202.156.1.48
nameserver 218.186.1.88
```

---

### Post by Detonate on 2010-06-09
elliryn, are you trying to establish a connection with dhcp, or do you desre a static connection?  Are you hooking up to a router, or to a cable/dsl modem?

Please run the following commands an post back the results.

```
ifconf
```

then ```
ifconfig -a
```

---

### Post by elliryn on 2010-06-09
I'm trying to establish a connection with DHCP, and I believe I'm connected to a router.
 
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet6 addr: fe80::222:64ff:fe66:ff53/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257952 (257.9 KB)  TX bytes:40757 (40.7 KB)
          Interrupt:17 
eth0:avahi Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet addr:169.254.8.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63168 (63.1 KB)  TX bytes:63168 (63.1 KB)

```
 
 
ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet6 addr: fe80::222:64ff:fe66:ff53/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257952 (257.9 KB)  TX bytes:40757 (40.7 KB)
          Interrupt:17 
eth0:avahi Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet addr:169.254.8.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63168 (63.1 KB)  TX bytes:63168 (63.1 KB)
pan0      Link encap:Ethernet  HWaddr be:10:3b:ed:d1:24  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:23:4d:2f:25:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by eventhorizonof on 2010-06-09
I am using the same cable connected to a windows machine and I am on the internet with no problem. I cannot ping the router in ubuntu it is coming back as network unreachable. I am positive the cable is connected to the right port.

---

### Post by Detonate on 2010-06-10
chili555,are you still watching this thread?  I need some help here.  I believe that both eventhorizonof and elliryn's problem is that the avahi-daemon has grabbed their eth0 and established a local IP address for eth0 and that is the reason they can't get a dhcp offer from the router.  Your thoughts?

---

### Post by chili555 on 2010-06-10
> the avahi-daemon has grabbed their eth0 and established a local IP address for eth0 and that is the reason they can't get a dhcp offer from the router.That happens when the ethernet card and driver don't correctly communicate with the router and the router doesn't offer an IP address. I could be a driver problem or otherwise. In both cases, I'd love to see:```
sudo ethtool eth0
```We hope we are not seeing:> Link detected: no

I'd also love to see what the kernel says about the driver. Each should determine what driver the ethernet card is using with *sudo lshw -C network*. Then run and post:```
dmesg | grep <driveryoufound>
```Here is an example from my computer:> description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 99:16:41:66:cb:88
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=e1000e[/COLOR] > $ [COLOR="Red"]dmesg | grep e1000e[/COLOR]
[    0.840716] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.840719] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.840768] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.840790] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.840834] e1000e 0000:02:00.0: setting latency timer to 64
[    0.841054] e1000e 0000:02:00.0: irq 30 for MSI/MSI-XFinally, I'd love to know if these machines are dual-booted.

---

### Post by Detonate on 2010-06-10
OK guys, run the commands posted by chili555 and let's see the results.

I also want you to run

```
sudo stop avahi-daemon
```

and 

```
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf
```

This will stop the avahi-daemon and prevent it from restarting at boot.  Copy and paste that second command to avoid any chance of a typo.

---

### Post by eventhorizonof on 2010-06-10
So the ethtool command did not work, possibly because NM was removed??  I am NOT running a dual boot machine. I am on the internet using a separate windows machine with the same wired ethernet connection. I built a second computer for use as a linux only machine. Attached is a file with the commands and the resulting output I will also cut and paste here

```
sudo ethtool eth0
[sudo] password for william: 
sudo: ethtool: command not found
```


 ```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:8e:9a:08
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:d800(size=256) memory:feaff000-feafffff memory:fdffc000-fdffffff(prefetchable) memory:feac0000-feadffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 05
       serial: 00:1b:21:62:31:89
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:16 memory:febe0000-febfffff memory:febc0000-febdffff ioport:ec00(size=64) memory:c0400000-c041ffff(prefetchable)
```


```
dmesg | grep e1000
[    0.711077] e1000 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.974193] e1000: 0000:03:00.0: e1000_probe: (PCI:33MHz:32-bit) 00:1b:21:62:31:89
[    1.146431] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
```




```
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf
# avahi-daemon - mDNS/DNS-SD daemon
#
# The Avahi daemon provides mDNS/DNS-SD discovery support (Bonjour/Zeroconf)
# allowing applications to discover services on the network.

description	"mDNS/DNS-SD daemon"

#start on (filesystem
#	  and started dbus)
stop on stopping dbus

expect daemon
respawn

pre-start script
    [ -d /sys/module/apparmor ]  || exit 0
    [ -x /sbin/apparmor_parser ] || exit 0
    /sbin/apparmor_parser -r -W /etc/apparmor.d/usr.sbin.avahi-daemon || true
end script

script
	opts="-D"
	[ -e "/etc/eucalyptus/avahi-daemon.conf" ] && opts="${opts} -f /etc/eucalyptus/avahi-daemon.conf"
	exec avahi-daemon ${opts}
end script
```

---

### Post by Detonate on 2010-06-10
Now restart the computer and see if you can get a connection.  Again post the results of ifconfig.

---

### Post by eventhorizonof on 2010-06-10
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet6 addr: fe80::4261:86ff:fe8e:9a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41506 (41.5 KB)  TX bytes:1152 (1.1 KB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```


```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet6 addr: fe80::4261:86ff:fe8e:9a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133792 (133.7 KB)  TX bytes:4471 (4.4 KB)
          Interrupt:26 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:62:31:89  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:8e:9a:08  
          inet addr:169.254.6.168  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


```


I really appreciate everyone for the help it means alot thanks.


I will be heading to school now so I wont be able to work on this anymore until the afternoon.

---

### Post by chili555 on 2010-06-10
The interface eth2 is shown as disabled and no link. eth0 has a link and I assume, that is where the ethernet cable is attached. May we see:```
dmesg | grep r8169
```Thanks.

---

### Post by eventhorizonof on 2010-06-10
```
[    0.707628] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.707644] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.716235] r8169 0000:02:00.0: setting latency timer to 64
[    0.716292] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    6.383517] r8169: eth0: link down
[   21.603005] r8169: eth0: link up
```



I have two ethernet ports. One is from the mobo (eth0) where I have been attempting to connect. The other is from an NIC PCI card (eth2).

---

### Post by Detonate on 2010-06-10
Move the cable to the other port (eth2).  Modify the /network/interfaces file to read eth2 in the places it now reads eth0.  restart the network and see what happens.

---

### Post by eventhorizonof on 2010-06-10
same deal....

sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth2/00:1b:21:62:31:89
Sending on   LPF/eth2/00:1b:21:62:31:89
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                              
```


I have a router that I may attempt to use to connect through to the modem. I just don't have another ethernet cable. Would this be worth trying?

---

### Post by Detonate on 2010-06-10
Yes it would.  Although I am beginning to suspect that your modem has some kind of setting that prevents connection from your Ubuntu computer.  Could be a MAC address filter  that only allows your other computer to connect.

---

### Post by eventhorizonof on 2010-06-10
OK so here is the deal. I am moving out of my apartment in ~ 20 days. Therefore when I move home to start graduate school I will be using a different modem/router. I will attempt the router 'route' tomorrow but and if it is unsuccessful I will let everyone know.

So here is my situation. I have ubuntu on a 500gb seagate that I bought while my WD 1TB was being RMA'd. I will receive the replacement WD 1TB (which is the drive I really wanted to use for this ubuntu machine) this weekend. I intend to return the seagate (which I really have no use for with a functional WD 1 TB). Now, should I wait for a different release in the fall (10.10?) and install the OS then (while keeping an eye on the forums for any fixes to this problem) or should I attempt to again install 10.04 LTS using a different modem/router etc at home? I wanted to have the computer running for this summer but don't really NEED it until the fall. I am just disappointed I thought this process was going to be fairly effortless. Any ideas would be appreciated.

---

### Post by elliryn on 2010-06-11
Looks like this is kind of complicated...
Thanks a lot for the help guys, really appreciate it (:
My situation is exactly as eventhorizonof said - not running a dual boot, using linux on a separate machine (a HP netbook in this case) on the same wired ethernet connection (wireless doesn't work either).
 
*sudo ethtool eth0* returned a
```
sudo: ethtool: command not found
```
*sudo lshw -C network* returned
```
driver=sky2
```
*dmesg | grep sky2* returned
```
[    2.218020] sky2 driver version 1.25
[    2.218083] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.218099] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.218127] sky2 0000:02:00.0: setting latency timer to 64
[    2.218192] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    2.218378] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    2.220467] sky2 eth0: addr 00:22:64:66:ff:53
[   12.808966] sky2 eth0: enabling interface

```
*suo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf* returned
```
# avahi-daemon - mDNS/DNS-SD daemon
#
# The Avahi daemon provides mDNS/DNS-SD discovery support (Bonjour/Zeroconf)
# allowing applications to discover services on the network.
description "mDNS/DNS-SD daemon"
#start on (filesystem
#   and started dbus)
stop on stopping dbus
expect daemon
respawn
pre-start script
    [ -d /sys/module/apparmor ]  || exit 0
    [ -x /sbin/apparmor_parser ] || exit 0
    /sbin/apparmor_parser -r -W /etc/apparmor.d/usr.sbin.avahi-daemon || true
end script
script
 opts="-D"
 [ -e "/etc/eucalyptus/avahi-daemon.conf" ] && opts="${opts} -f /etc/eucalyptus/avahi-daemon.conf"
 exec avahi-daemon ${opts}
end script

```
After the reboot, *ifconfig* returned
```
eth0      Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet6 addr: fe80::222:64ff:fe66:ff53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24214 (24.2 KB)  TX bytes:2304 (2.3 KB)
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```
*ifconfig -a* returned
```
eth0      Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet6 addr: fe80::222:64ff:fe66:ff53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28148 (28.1 KB)  TX bytes:5182 (5.1 KB)
          Interrupt:17 
eth0:avahi Link encap:Ethernet  HWaddr 00:22:64:66:ff:53  
          inet addr:169.254.8.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
pan0      Link encap:Ethernet  HWaddr be:e1:50:9e:86:79  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:23:4d:2f:25:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
 
Chili555 mentioned potential driver problems which could be possible. I installed Ubuntu offline, and when I open Hardware Drivers it comes up totally blank. I tried one of the guides in installing the driver for Broadcom BCM4312 (when I was trying to get the wireless connection working), and I ran into some gcc error.

---

### Post by radwajshalik on 2010-06-11
Hi..,

I'm using a wired LAN or cable and still won't connect. but it's working  in my other laptop when i transfer the cable.

---

### Post by Detonate on 2010-06-11
Just curious, what ISP are you guys using?  The reason I ask is that I have  run into problems like these with Comcast.  When ordering Comcast internet service, you have to specify that you will be using more than one computer on the network.  There is an extra charge for this. They have their modem setup to only allow one connection.  I don't know exactly how they do this, but I suspect that when you run their install program in Windows it uses the MAC address of the Windows computer to set up a filter.  Other ISP's may do the same.  So if you could access the web interface from your Windows computer you might could look to see if you can find out what's going on.  The other possibility is that they have the DHCP available addresses limited to one.  These are just wild guesses.

---

### Post by chili555 on 2010-06-11
> **eventhorizonof said:**
> ```
[    0.707628] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.707644] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.716235] r8169 0000:02:00.0: setting latency timer to 64
[    0.716292] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    6.383517] r8169: eth0: link down
[   21.603005] r8169: eth0: link up
```



I have two ethernet ports. One is from the mobo (eth0) where I have been attempting to connect. The other is from an NIC PCI card (eth2).I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984)> A workaround is currently to issue the 'ethtool -s eth0 autoneg off' command, after installing ethtool downloaded from another system. Once autonegotiation is turned off, signal is properly detected and as such, network-manager for example will see a connection and attempt to get an address from DHCP.Can you please try that? Here is ethtool: [http://packages.ubuntu.com/lucid/ethtool](http://packages.ubuntu.com/lucid/ethtool)

Be sure to get the i386 or 64-bit version as needed.

If it works, we can create a file to make the command permanent.

---

### Post by elliryn on 2010-06-11
I'm from outside of the USA, and my ISP doesn't have any restrictions on having more than one computer on the network. I have 2 computers and 2 laptops running on the same network at home, and one of them is a Macbook, so I don't think that's the problem.
 
I'm going to reinstall Windows XP on the netbook to make sure that I can actually connect to the internet in the first place, and then try reinstalling Ubuntu again to see if there's any difference in case I unwittingly did something wrong the first time round. If not, I guess I'll have to give Ubuntu a miss this time ):
 
In any case, thank you very much for your time and effort Detonate! Very much appreciated.

---

### Post by Detonate on 2010-06-11
Try chili555's workaround before you say goodbye.

---

### Post by eventhorizonof on 2010-06-14
PROBLEM SOLVED.


So today I was looking at my windows vista home premium network and sharing icon and it had a computer with a red 'X' through it. I had never really given too much thought to this problem as I could readily browse the web with no issues. Today I tried opening the network and sharing center and it freezes repeatedly. So I went searching for forums such as this with the tagline of "network and sharing center slow or freezes" and found a simple fix. Upon implementing this I figured I would give one last shot at attempting to connect to the internet via ubuntu 10.04 LTS. Well I am proud to say I am writing this post using my linux machine!!! Apparently the network settings in windows had some effect on the router settings which did not allow other computers to connect. If anyone has any more insight into this problem it would be beneficial for others. I just wanted to share the good news and let everyone know the problem has been resolved.

---

### Post by Detonate on 2010-06-14
Please share with us exactly what you changed in Windows.  This could be the root of other posters problems.

---

### Post by eventhorizonof on 2010-06-14
[http://www.xoxideforums.com/networking/76388-vista-giving-you-server.html](http://www.xoxideforums.com/networking/76388-vista-giving-you-server.html)

I followed the instructions here in the 11th post from the top (docinventor)

Then rebooted. I then used a ethernet cable to connect to a netgear router that is connected to my modem. NOTE: I tried connecting my linux machine to the router BEFORE the commands were run in windows to no avail, so the fix is a direct result of reconfiguring the network and sharing icon in vista home premium.

---

### Post by electech on 2010-07-05
Just wanted to post my workaround as I was having the same problems. I have a dell latitude with no nic, so was using a lan card with ethernet adaptor. I followed every instruction on this thread until I got to the ethtool bugfix. I installed ethtool and typed in ethtool -s eth1 autoneg off (didn't have eth0) and got a message saying operation not permitted not setting autoneg and something about cannot get wake-on-lan settings(sorry I didn't note down what it was exactly which is really stupid of me.) 

At this point I took out my 3com lan card and threw it across the room. Then I decided to try a cheap usb to lan adaptor I had lying around (this one [http://cgi.ebay.co.uk/High-Speed-USB-2-0-RJ-45-LAN-Card-Socket-Adapter-/200491922136?cmd=ViewItem&pt=UK_Computing_LaptopAccessories_PCMCIACards&hash=item2eae3ff2d8](http://cgi.ebay.co.uk/High-Speed-USB-2-0-RJ-45-LAN-Card-Socket-Adapter-/200491922136?cmd=ViewItem&pt=UK_Computing_LaptopAccessories_PCMCIACards&hash=item2eae3ff2d8) ) and immediately saw a light on the router where the cable was plugged in, which simply wouldn't show before. I think you can guess where this is heading! There was still no internet connection so I went back to Detonate's instructions back on post #8 of this thread. eth0 was now showing instead of eth1 so I edited the interfaces command as described and then sudo /etc/init.d/networking restart. Am very pleased to say it works beautifully now, and I didn't even have to install any driver for the usb lan adaptor. I couldn't work out why it all worked fine in windows but not in ubuntu, so I think that's why I kept trying to persist in making the lan card work when it just wasn't going to play along.

Thanks so much for all the information on this thread, it was actually a really great learning experience all in all.

---

### Post by Detonate on 2010-07-05
Happy you got it working, and pleased I was able to be of help.

---

### Post by Alabaster on 2010-07-09
Detonate, thanks for your clear instructions. After struggling with Network-Mangler for a while, you HowTo got me working!

You win one free internets

---

