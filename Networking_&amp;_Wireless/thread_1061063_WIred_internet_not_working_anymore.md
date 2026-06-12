---
title: "WIred internet not working anymore"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by shorty28898 on 2009-02-05
The wireless works fine, but the wired does not, when i plug it into my inspiron 1525, the green light is on, but the other one that usually blinks does nothing, nor do any pages load.

---

### Post by NoReflex on 2009-02-05
Hello!

Do you have DHCP on the wired LAN? You can check if your computer has been assigned a valid address using the **ifconfig** command.

Best wishes,
NoReflex

---

### Post by odium1 on 2009-02-05
i have an inspiron 1501 running 8.10 and last night i was at my girlfriends and i had connected to the neighbors wireless network and my computer said there were some updates available, so i clicked ok, yada yada, and after the updates finished i shut my computer down. well, this morning i got up and hooked my computer up to my wired network and now it won't connect. i tried connecting to the neighbors wireless network and it won't do that either.. so i would suppose we're probably having similiar problems.

i know it's not my connection because right now i'm on my ibook (running dapper) and my wired connection is fine.

---

### Post by shorty28898 on 2009-02-05
When i did ifconfig this shows up
eth0      Link encap:Ethernet  HWaddr 00:21:9b:dd:76:60  
          inet6 addr: fe80::221:9bff:fedd:7660/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18936 (18.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:e2:80:c9:4e  
          inet addr:172.16.29.22  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21f:e2ff:fe80:c94e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36001 errors:0 dropped:0 overruns:0 frame:79684
          TX packets:34813 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33042809 (33.0 MB)  TX bytes:10085131 (10.0 MB)
          Interrupt:17 Base address:0xc000

---

### Post by 5BallJuggler on 2009-02-05
> **odium1 said:**
> i have an inspiron 1501 running 8.10 and last night i was at my girlfriends and i had connected to the neighbors wireless network and my computer said there were some updates available, so i clicked ok, yada yada, and after the updates finished i shut my computer down. well, this morning i got up and hooked my computer up to my wired network and now it won't connect. i tried connecting to the neighbors wireless network and it won't do that either.. so i would suppose we're probably having similiar problems.

i know it's not my connection because right now i'm on my ibook (running dapper) and my wired connection is fine.

what linux kernel are you running? if it's the latest one, i believe there is a issue with the wired connection.

try booting up with a previous kernel and see if the problem is still there.

---

### Post by shorty28898 on 2009-02-05
2.6.27-11-generic

---

### Post by odium1 on 2009-02-05
> **5BallJuggler said:**
> what linux kernel are you running? if it's the latest one, i believe there is a issue with the wired connection.

try booting up with a previous kernel and see if the problem is still there.

yeah it is the latest one. i just tried the two older kernals and it didn't help :/

---

### Post by stormtrooprdave on 2009-02-05
I am having the same problem.  My wireless works perfectly however the wired connection will only connect to google domain sites.  It is not a dns issue as I can ping any site in the terminal ( for more details see [this thread]("http://ubuntuforums.org/showthread.php?p=6683038#post6683038"))

results from ifconfig -

eth0 Link encap:Ethernet HWaddr 00:50:8d:98:57:25
inet addr:192.168.1.69 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::250:8dff:fe98:5725/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:459 errors:36 dropped:0 overruns:0 frame:36
TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:141928 (141.9 KB) TX bytes:53759 (53.7 KB)
Interrupt:19 Base address:0xdead

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)

---

### Post by Wolfhere on 2009-02-05
I had the same problem. The update did the same thing to my interfaces file as the upgrade from 8.04 to 8.10.

at the terminal: sudo gedit /etc/network/interfaces

remove the auto eth0 and edit the line at inet eth0 to:

auto eth0 inet dhcp

(or if you are statically assigning ip:

auto eth0 inet static

reboot and wired should be there again.

---

### Post by stormtrooprdave on 2009-02-05
> **Wolfhere said:**
> I had the same problem. The update did the same thing to my interfaces file as the upgrade from 8.04 to 8.10.

at the terminal: sudo gedit /etc/network/interfaces

remove the auto eth0 and edit the line at inet eth0 to:

auto eth0 inet dhcp

reboot and wired should be there again.

Mine says:

auto lo
iface lo inet loopback

I changed it to:

auto eth0
iface eth0 inet dhcp

Once I did this it refused to boot. I had to use the livecd to change it back.  I was given that advice in other threads. So should it just be one line saying:

auto eth0 inet dhcp?

---

### Post by shorty28898 on 2009-02-05
mine say:
auto lo
iface lo inet loopback


i dont want the same problem and nto have ubuntu boot..  what exactly should i be changing this too?

---

### Post by shorty28898 on 2009-02-06
ok i re-installed ubuntu, but have not updated it yet, does anyone know the update that i should not check off so i dont download it??

---

### Post by odium1 on 2009-02-06
yeah i'm wondering the same thing because i'm re-installing in the morning. i can't remember what the updates were exactly, but I hope i remember when i see it. i think it had something to do with 'kernal headers' or something. I'm still pretty new to linux so i ask as many questions as i can so i'll learn lol.

---

### Post by delboy1 on 2009-02-07
I cannot get my wired ethernet working at all. I have looked through various threads and tried altering /etc/network/interfaces with the 2 lines

auto eth0
iface eth0 inet dhcp

but it made no difference

I then tried just the one line

auto eth0 inet dhcp

and it still made no difference

---

### Post by odium1 on 2009-02-07
I finally got mine to work by booting into a previous kernel, which i did a few times yesterday and the day before and had no luck, but today i was messing around with it and it worked. i booted into -9 instead of -11 and it connected but the speeds were super slow. it took a good 60 seconds to load google :/ I'm backing everything up now so i can re-install and update up until -11 and just not update that kernel. Then i'm just going to ride it out until the development team works the bug out.

---

