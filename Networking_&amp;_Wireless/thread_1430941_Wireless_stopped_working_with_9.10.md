---
title: "Wireless stopped working with 9.10"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by srajama on 2010-03-16
I got wireless working on ubuntu 9.10 and it was working for the past few months. Last night the battery ran out and when I turned it back on the wireless does not seem to connect to my network.

I can see wireless network card setup as eth1, I can see the network listed, I can see other networks, but if I try to connect to it brings me back to a prompt for WEP key. I can see that I got the WEP key right. And I can connect my second laptop running Vista and an iPhone to the same wireless network. 

What can I try next?

I am running this on a Dell XPS with Broadcomm chipset and Broadcomm STA wireless drivers. I can post the exact details if it will be useful - It'll be a little tricky getting it across a offline laptop.

Edit: I connected a wire from the router to the laptop and found that that connects fine. It looks like it's just the wireless. I have tried restarting the router too.

Posting output of some command after connection with a wire:

$> lspci 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

$> iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

$> ifconfig

eth1      Link encap:Ethernet  HWaddr 00:16:44:b6:b2:bd
          inet6 addr: fe80::216:44ff:feb6:b2bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:2030
          TX packets:10 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2376 (2.3 KB)  TX bytes:3500 (3.5 KB)
          Interrupt:17 Base address:0xc000

---

### Post by srajama on 2010-03-16
I tried turning off wireless security, and it still does not connect to my network.

---

### Post by srajama on 2010-03-16
Ok - I was able to track this down to KDEWallet. I am not sure if this needs to be moved under a new forum. 

I got the wireless working by 

  - Disabling KDEWallet.
  - Disable WEP on the router

I was able to use other apps like Kopete without KDEWallet. But if I turn WEP back on, I am not able connect to the network. Is there something I need to do to keep the network manager from using KDEWallet?

---

### Post by draperdt on 2010-03-16
You should really turn your security on first.

You should really use WPA security instead of WEP

Do you see available networks using network manager?

Are you sure you are putting the right key in the right place to connect in network manager?

I have no idea why KDEWallet will interfere with your wireless connection, but could you include output of following commands in shell. ifconfig, iwconfig, airdriver-ng loaded

---

### Post by srajama on 2010-03-16
> **draperdt said:**
> You should really turn your security on first.


Already have. 

> **draperdt said:**
> 
You should really use WPA security instead of WEP


Yeah - I should. I am just keeping it as WEP for now until this is sorted out, so as to not add another variable in the mix.

> **draperdt said:**
> 
Do you see available networks using network manager?


Yes, I can. 

> **draperdt said:**
> 
Are you sure you are putting the right key in the right place to connect in network manager?


Yes, I am. 

> **draperdt said:**
> 
I have no idea why KDEWallet will interfere with your wireless connection, but could you include output of following commands in shell. ifconfig, iwconfig, airdriver-ng loaded


Yes. It baffles me too. Here are the outputs. eth0 is wired lan and eth1 is wireless.

$> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:7f:15:e8
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe7f:15e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:846649 (846.6 KB)  TX bytes:244281 (244.2 KB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:16:44:b6:b2:bd
          inet6 addr: fe80::216:44ff:feb6:b2bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:569
          TX packets:9 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2464 (2.4 KB)  TX bytes:3150 (3.1 KB)
          Interrupt:17 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)


$> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

The last command? 'airdriver-ng loaded' - I can't find it installed and apt-get install doesn't seem to know the command either. The driver I am using for this machine is Broadcomm STA driver installed from "Hardware drivers".

---

### Post by srajama on 2010-03-18
Bump... 

I tried re-installing everything - KWallet, network manager etc. It does not seem to help.

---

### Post by kid1000002000 on 2010-03-18
could your card be stuck in monitor mode?  try searching google to get it to switch back.  usually this is rectified once you have restarted your computer though...

---

### Post by srajama on 2010-03-18
I tried the following command to set the mode to managed.

$> sudo iwconfig eth1 mode managed

It does not seem to help. I have rebooted the machine several times by now. 

I just noticed something else too: The wireless icon get stuck in 'activating' for a while and I get back a prompt for the WEP key. the 'Key' entry seem to be filled with a lot of characters. If I click on "show password" it's a alphanumeric sequence. Here are the first few chars... 63793e09844(...). It looks like some form of encrypted string. If I cancel this dialog, go to 'manage connections' and eventually click on 'Show password' I see my correct WEP key...

---

### Post by kid1000002000 on 2010-03-18
hmm.  I have this same problem.  I have two wireless cards, and my wireless will work with one but not the other.  What I know is that my router shows DHCP was not issuing properly and there were like fifty requests that didn't go through.  Perhaps this is the same for you and could serve as a good starting point??

---

### Post by srajama on 2010-03-18
The thing is - until the whole confusion started two days ago, I was able to use the same machine just fine. I have a second laptop and an iPhone which are also DHCP. And faulty machine connects if I turn off WEP. So, I don't think it is the DHCP.

My guess is the WEP key is stored as an encrypted string somewhere and the network manager is confused about how to decrypt it and it is sending the encrypted string as is. The question is - where the heck is this encrypted string coming from?

---

### Post by srajama on 2010-03-19
I changed my wireless security from WEP to WPA-2, deleted my wireless profile and recreated a new profile and it connected (and there was much celebration - yay...). 

Maybe I should've to draperdt's sound security advice earlier... :)

---

### Post by JakartaDean on 2010-03-25
I am having the same problem, and have for a while.  I just installed the 10.04 beta, and it still exists.  With all due respect, I don't think should be marked solved.  In my case, for example, the office wireless network uses WEP and I can't connect.  A workaround requiring changes to other infrastructure isn't a solution IMO.

Other computers can connect to this network and this computer can connect to unsecured networks.

Hardware:  Asus EeePC 900 (Atheros AR5001 Wireless Network Adapter)
OS:  kubuntu 9.10 and ubuntu 10.04 beta

---

### Post by tsk1979 on 2010-03-25
I also had to struggle, but with knetworkmanager and kwallet combo I was able to make it work.
However, I was not happy with having password stored and also wireless now working when I am not using the window manager(sometimes I just login to terminal for ssh sessions).
Then I discovered wicd.
Put the wicd applet in autostart of kde.
When system boots up, wireless is already connected, and when kde starts wireless is there in the applet.
So if wireless goes down, its not a problem, since wicd autoconnects once the router comes back up.

BTW I am on kubuntu

I suggest you apt-get install wicd from the terminal.
It will uninstall other stuff, and make wicd your default stuff.
Other instructions can be found on their FAQ page

---

### Post by thesenu on 2010-03-25
thank for information:popcorn:

---

### Post by JakartaDean on 2010-03-27
Thanks.  I've downloaded wicd but no joy so far, but I'll keep trying.

Cheers,
Dean

---

### Post by tsk1979 on 2010-03-29
I installed 10.04 beta kubuntu, and got wicd.
It works fine, and I can see the SSID
But when I select authentication as WPA-PreSharedKey(WPA-PSK) in my router, it fails authentication.
Network is working fine in windows though!
Any updates or something?

---

### Post by jdeal on 2010-04-07
I am having the same type of issue.  Dell 1525 running 9.10 fully updated.  Worked fine with 8.04.  Works fine with the dual booted Vista.  Can not get any security to work, either WEP or WPA personal.  Works if you take all security off which is basically unacceptable.  I first ran into this problem in January.  Very fustrating.

---

### Post by jdeal on 2010-04-07
I spoke too soon.  Does not work in no security mode.  Very fustrating.  I hope 10.4 fixes this.  If not, I may just go back to 8.04.

---

### Post by tsk1979 on 2010-04-08
Do this.
Uninstall network manager(or knetworkmanager)
Get wicd and wicd-curses
go to terminal, and use wicd-curses
Configure WPA-PSK or whatever.
You are good to go.
It works like this in 9.10 and 10.04 both!
I have tried it

---

### Post by Plumcrazy10 on 2010-04-08
I also have this problem. Ubuntu 9.10, no security wireless works fine. With WPA, I can connect and obtain IP from DHCP but cannot browse/ping internet.
 
This is very frustrating to a Linux newbie like me!

---

