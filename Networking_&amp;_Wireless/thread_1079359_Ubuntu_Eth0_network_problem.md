---
title: "Ubuntu Eth0 network problem"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by white-devil on 2009-02-24
complete and utter newbie to any kind of linux here so be gentle.

I have problem with autoconnecting to wired networks with the ubuntu on my laptop. I believe this is because I removed the auto eth0 a while back by mistake. I finally got around to try and find a solution for this so I asked my friend who has a bit more experience than me and this is what I got:

Open a terminal, and type "ifconfig eth0"
Copy the sequence after "HWaddr" (should look like 00:1e:68:94:4d 7 or similar)
right click on the network manager icon, select Edit Connections...
In the "Wired" tab, click "Add"
Name it Auto eth0
Set "Connect automatically" and "System setting" to true.
Set the MAC address to the sequence you copied from the terminal
Hit okay

I tried this and the terminal informed me that the device (eth0) could not be found. My friend ran out of ideas and I was forced to scour the internet for a clue thus leading me here.

---

### Post by x1101 on 2009-02-24
First white-devil, welcome to the Linux community. Second, Open up a terminal, type in *ifconfig* and see what all is listed. Specifically you are looking for eth0 (if that is your primary connection, and it usually is). If it isnt there, try this: *sudo ifconfig etho up*
which will bring the interface (network device) online. If you can get it up and running manually from there we can continue work on making this automatic by way of the terminal.

Good Luck.

---

### Post by white-devil on 2009-02-24
Thank you for the warm welcome 1101. : )

This is what I got from the ifconfig command:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:69:49:75:94  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe49:7594/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1784 (1.7 KB)  TX bytes:5762 (5.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-69-49-75-94-35-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

When I tried the *sudo ifconfig etho up* command I got the following error:

etho: ERROR while getting interface flags. The unit doesn't exist.

---

### Post by x1101 on 2009-02-24
white-devil,

Apologies, that was typo on my part, you should use eth0 (zero here not an o). Try that.

---

### Post by white-devil on 2009-02-24
get the same error from that : /

---

### Post by x1101 on 2009-02-24
White-devil,

Just for giggles try the same with eht1 (occasionally the system will call it something different).

---

### Post by white-devil on 2009-02-24
I tried changing the number up to 5 and still got the same error.

---

### Post by x1101 on 2009-02-24
Then it seems that somehow your system does not register that device. What version of Ubuntu are you running?

---

### Post by white-devil on 2009-02-24
8.10

---

### Post by cap'n leaky on 2009-02-24
I'd be interested if anyone has any idea, because I have the same problem.

I had xubuntu 8.04 running fine then I did a upgrade to xubuntu 8.10.

After the reboot, Network Manager showed that there was an error, and I lost my networking.  I'm not at home now, but I did get networking to work by manually editing the /etc/network/interfaces file.  First I went to a static IP and it worked, then I added my gateway router, and DHCP works again.

BUT, nothing I do in Network manager can make eth0 show up.  I too have deleted auto eth0.  I have done what was suggested and made a new entry with the MAC address I got from ifconfig, but even though my network is working, Network Manager is dead.  I would remove it from my panel and ignore it, but it can't be removed.

I think there is a bug in the new Network Manager (.7 by memory, since I'm not on the system right now).  Any help from the gurus would be appreciated.

---

### Post by Airheaded on 2009-02-24
I've tried all of the above.

Please help.

Thxs

---

### Post by Airheaded on 2009-02-24
I've tried all of the above.
Please help

---

### Post by Airheaded on 2009-02-24
Thanks for this discussion.

(Something funny with this site right now, since have tried to post this several times, but just get redirected back to the beginning.)

Then again, i'm a newbie

Am having the same problems as above.

Ubuntu 8.04 LST installs and works just great!    (Thank You!)  (On Dell GX-270 machines).

Ubuntu 8.10 &#8211; well, downloaded using windoze, burned it to disk using nero, it installs, but will not get me on the Web, nor the net.

And have spent at least 10 hours trying.   More like 20.

My current challenge:
I volunteer for a couple of local volunteer organizations here and through a local school have been given 20 Dell GX-270s machines (about 5 years old but still working great) to be placed with same.  Some will be will be given to other, small and underfunded volunteer organizations, in desperate need of getting on the Web, some will be given to elderly people, in need of Netbanks and such, other will be set up as teaching and user machines at the local volunteer central here.

What should I do?

Give them these machines with 8.04 installed, or search for an 8.10 solution?

Thanks again for any suggestions and help.

Z

---

### Post by zika on 2009-02-24
**4 white-devil**
put this in place of */etc/network/interfaces*
(you can do that with Alt-F2 then enter *gksudo gedit /etc/network/interfaces*)
```
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
# The primary network interface DHCP
iface eth0 inet dhcp
``` (if there is any stuff concerning wireless leave it as it is in this file)
then open Terminal window (Alt-F2 gnome-terminal) and type ```
sudo /etc/init.d/networking restart
```to check what happened type (and post here the outcome)```
ifconfig eth0
```(You exit Terminal window with "*exit*")

(disregard possible sign on Network Manager that You are not connected anymore, it is  a blunt lie ... ;))

try Firefox to see if it is working.

once this is done we could go further.

---

### Post by cap'n leaky on 2009-02-24
White Devil - I did what Zika said, and networking does work after the edit to interfaces file.  I guess I'll just live with Network Manager indicating no connection, even though I'm connected.  It is annoying to see the big red X on the icon in my panel, but as long as it works it's no big deal.

Airheaded - If I was you, I would stick with 8.04 LTS on these machines.  The LTS release will give you long term support, which is probably good for these donated machines.  I upgraded to 8.10 just a week or two ago, and to be honest I haven't noted much difference.

---

### Post by white-devil on 2009-02-24
got this when I ran the network restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.

---

### Post by zika on 2009-02-24
> **cap'n leaky said:**
> White Devil - I did what Zika said, and networking does work after the edit to interfaces file.  I guess I'll just live with Network Manager indicating no connection, even though I'm connected.  It is annoying to see the big red X on the icon in my panel, but as long as it works it's no big deal.

there are several ways to resolve even that "red X" ... ;)

edit the file */etc/NetworkManager.nm-system-settings.conf* to have ```
[ifupdown]
managed=false
```as it was written in [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054/comments/24](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054/comments/24)...

that is if You do need Network Manager to handle Your wireless. if You do not need it for that You can switch it off in Your session with *System->Preferences->Sessions->untick Network Manager*.

there are the ways of getting it out of the memory of Your machine (not uninstalling it!) via *sysv-rc-conf*, but about that only if You are interested in that. above is enough to make You happy ... for now ... ;) do not follow suggestions in aforementioned link on how to deal with Network Manager in init.d since they are brutal and You will, some day, regret it ... :)

**4 white-devil **You could try also changing the file */etc/NetworkManager.nm-system-settings.conf *as suggested above so that wireless interfaces stay managed (if they are not mentioned in */etc/network/interfaces *and eth0 get unmanaged, since it is in that file. You might also want to try comment out *lo* interface from */etc/network/interfaces* to get it managed by NM, I'm not sure about that... a reboot might help, to get *eth0* somehow awaken. I'm not sure how You managed to get it out, I hope it is there ... :) **please backup and note all the changes You've made so that You could undo all the stuff we tried.**

---

### Post by cap'n leaky on 2009-02-24
Thanks, zika.

I will try your suggestions when I get back to my machine.  I don't need Network Manager, this is a desktop machine with wired ethernet; no wireless or need to connect to other networks.

It just bugged my that after the upgrade I had these problems when everything worked great in 8.04.

Thanks again.

J

---

### Post by zika on 2009-02-25
> **cap'n leaky said:**
> Thanks, zika.
I will try your suggestions when I get back to my machine.  I don't need Network Manager, this is a desktop machine with wired ethernet; no wireless or need to connect to other networks.
It just bugged my that after the upgrade I had these problems when everything worked great in 8.04.
Thanks again.
J
then also do ```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```go down to the line with "Network Manager" and untick (with Space) all the "x"-s (2 3 4 5). (note the state before) and exit (with "q"). now the Network Manager is put to sleep. as an added bonus now with all this done, ever since You've changed */etc/network/interfaces*, You have network as soon as the boot starts, not when You log-on in X. also, You have not unistalled anything ... You can go back to "initial" state whenever You want.

---

### Post by Airheaded on 2009-03-04
> **cap'n leaky said:**
> 

Airheaded - If I was you, I would stick with 8.04 LTS on these machines.  The LTS release will give you long term support, which is probably good for these donated machines.  I upgraded to 8.10 just a week or two ago, and to be honest I haven't noted much difference.

Thanks Cap - am determined to make this work, may follow your suggestions, but at the same time will try all the suggestions above.

Be back in a week or three - have a couple of months to complete this.
Sincerely,
AH

[SIZE="1"]([COLOR="Navy"][SIZE="2"]PS:
AAArrgghhh:

These machines were delivered with WinXP already on them.  
Of course, this being a school, everything (including XP multi-user license)  was installed again via RIS (Remote Installation Service) from/to a central server.

So now the option may be to deliver the machines with XP on it, just delete everything else, including MS Office, install OpenOffice 3.1, make sure the mail works, Firefox works, maybe install T-bird.

It would probably make my life a little easier, save some volunteer time for other things  - BUT - I don't really like this option.

Why should people, including folks older than self - who have never ever used a PC before, start using Microsoft - when they have equal or better options?

ds)
[/SIZE][/COLOR][/SIZE]

---

