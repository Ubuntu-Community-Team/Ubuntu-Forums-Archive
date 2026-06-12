---
title: "The address ubuntu.com cannot be found"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by sham08 on 2009-10-09
Hello.This is my first thread on the forum and as a new user of Ubuntu 9.04.Last week after thoroughly thinking I made up my mind to change my previous (Win XP) OS to Linux/Ubuntu environment.I made a fresh installation and deleted all the related to Microsoft whatever from my PC.It went all well (my hardware drivers updated and the Internet connection, connected) without any single problem within configuration process.Whilst I was on Win XP OS,I frequently used p2p services (BitComet) for downloaded torrent and due to my conversion (from Win XP to Ubuntu 9.04) I found out that Transmission (the default application for torrent on Ubuntu 9.04) fulfill my need.So,as how I treated Bitcomet on my recent OS (find a static IP and do the port forward process),I intended to do the same on Transmission.I made my own search on 'Google' and found several tips and tutorials related and I performed it (assigned a static IP) on my PC via script command though I realized (assuming of my limited knowledge of the new OS) that I'll ended facing trouble.But I couldn't stop this enthusiasm.So,I restarted my network and trying to access the Internet but to no avail. Shiretoko via Google said "Server not found" and using my Network Tool trying to 'ping' came back with result "The address Ubuntu.com cannot be found".I've tried Ubuntu Help Center (the only help and option that I had) right now,but seems didn't helped much.I'm really in the dark right now.Anyone out there please lend me a hand.Thanks in future for any response.

---

### Post by Iowan on 2009-10-09
If you changed to static address, you may need to check */etc/resolv.conf* to verify your nameservers are properly entered.  DHCP usually attends to this detail - and Network Manager might (if it knows where to look). Did you assign static address via Network Manager manual configuration, or by editing */etc/network/interfaces* file?

---

### Post by Maheriano on 2009-10-09
Ya, paragraphs are overrated anyway.

---

### Post by sham08 on 2009-10-14
Thanks guys for responding,and sorry for late replies.As I mentioned before,right now I'm totally disconnected from the Internet.Luckily,my little brother is back for his weekend,so I'm able to check my thread using his HP notebook.Back to my problem, I've tried before connecting to the Internet using my brother HP notebook with the problematic modem (the modem I used when I first installed Ubuntu 9.04,recently) still failing.I just make it to the modem web interface (IP :192.168.1.1)but don't have any idea to make any changes on its setting.But on my PC (with Ubuntu 9.04 OS that I changed the DHCP configuration to static IP),I couldn't even reached my homepage with a message appeared 'Cannot connecting to the server'.And to be more specific,changes I've made (from DHCP to static IP) were via script command not the GUI interface.So I'm really in big trouble right now,and really need someone to show me the solution.It really a disappointment for not being able to access the Internet for almost a week.Please help!

---

### Post by sham08 on 2009-10-14
> **Iowan said:**
> If you changed to static address, you may need to check */etc/resolv.conf* to verify your nameservers are properly entered.  DHCP usually attends to this detail - and Network Manager might (if it knows where to look). Did you assign static address via Network Manager manual configuration, or by editing */etc/network/interfaces* file?Thanks Iowan for your reply.I've checked the /etc/resolv.conf as you've stated above and there no other than avahi-daemon (what is it?).Is that the folder or whatever that I should do something about?And yes,I assigned the static address via editing /etc/network/interfaces file,because I couldn't make it installed the Network Manager. Hope to hear from you soon.Thanks.

---

### Post by sham08 on 2009-10-14
I'm sorry for the problems above,posted the same issue thread many times.It's because I'm on a wireless Internet connection and its really 'a pain in the ***'.Thought and feared my thread didn't reached the forum,I kept clicked the 'submit thread',without realizing the thread successfully posted.So sorry to the moderators and other users.I just remember that I didn't provided enough information related to my problematic Internet connection. I use a wired Ethernet router (DSL-520B) and on Ubuntu 9.04 OS. Really hoping to hear from you guys and thanks in advance.

---

### Post by sham08 on 2009-10-16
I'm
sorry for the problems above,posted the same issue thread many
times.It's because I'm on a wireless Internet connection and its really
'a pain in the ***'.Thought and feared my thread didn't reached the
forum,I kept clicked the 'submit thread',without realizing the thread
successfully posted.So sorry to the moderators and other users.I just
remember that I didn't provided enough information related to my
problematic Internet connection. I use a wired Ethernet router
(DSL-520B) and on Ubuntu 9.04 OS. For more specific details : My
current ifconfig (type via terminal): eth0 Link encap : Ethernet Hwaddr
00:50:8d:bc:28:3b inet addr :192.168.0.150 Bcast :192.168.0.255 Mask
:255.255.255.0 Up Broadcast Multicast MTU : 1500 Metric : 1 RX Packets
:0 Errors :0 Dropped :0 Overruns :0 Frame :0 TX Packets :0 Errors :0
Dropped :0 Overruns :0 Carrier :0 Collisions :0 Txqueuelen :1000 RX
bytes :0 (0.0B) TX bytes :0 (0.0B) Interrupt :17 lo Link encap : Local
Loopback Inet addr :127.0.01 Mask :255.0.0.0 inet6 addr : ::1/128 Scope
:Host UP LOOPBACK RUNNING MTU :16436 Metric :1 RX Packets :92 Errors :0
Dropped :0 Overruns :0 Frame :0 TX Packets :92 Errors :0 Dropped :0
Overruns :0 Carrier :0 Collisions :0 txqueuelen :0 RX bytes :7088
(7.0KB) TX bytes :7088 (7.0KB) Changes I've made in the interfaces
(/etc/network) folder : auto lo iface lo inet loopback (the default
value before the problem), and I add : # The primary network interface
auto eth0 iface eth0 inet static address 192.168.0.150 netmask
255.255.255.0 network 192.168.0.255 gateway 192.168.1.1 I'm really
hoping someone could help me on this issue,and thanks in future for any
response.Thanks.

---

### Post by sham08 on 2009-10-17
Sorry guys for my impatience,but I left only 24 hours to solve my above problems.Tomorrow my brother will get back to work and so this HP Notebook.Without it (his HP)I'll not able to solve the problem because the only Internet connection that I had is the problematic modem.So I'm really hoping if there by any chance someone of you on this forum could shade me some lights.I'm really in the dark right now.I've tried searching by myself online,but the more I read all of the tips or tutorials that were available,the more I get confused.For more information and convenience,below are the present state of my connections:[LIST]
[*]eth0
[/LIST]Link encap:Ethernet  HWaddr 00:50:8d:bc:28:3b               inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0       inet6 addr: fe80::250:8dff:febc:283b/64 Scope:Link                           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1               RX packets:1708 errors:0 dropped:17 overruns:0 frame:0           TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txquelen:1000                                       RX bytes:392383 (392.3 KB)  TX bytes:175923 (175.9 KB)           Interrupt:17                                                     [LIST]
[*]lo
Link encap:Local Loopback                                        inet addr:127.0.0.1  Mask:255.0.0.0                              inet6 addr: ::1/128 Scope:Host                                   UP LOOPBACK RUNNING MTU:16436 Metric:1                           RX packets:3853 errors:0 dropped:0 overruns:0 frame:0            TX packets:3853 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0                                        RX bytes:1086515 (1.0 MB)  TX bytes:1086515 (1.0 MB)             [LIST]
[*]pan0
Link encap:Ethernet  HWaddr 1a:22:f9:c7:89:a3                    inet6 addr: fe80::1822:f9ff:fec7:89a3/64 Scope:Link              UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1                 RX packets:0 errors:0 dropped:0 overruns:0 frame:0               TX packets:1189 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0                                        RX bytes:0 (0.0 B)  TX bytes:402054 (402.0 KB)                   [LIST]
[*]pan0:avahi
Link encap:Ethernet  HWaddr 1a:22:f9:c7:89:a3                    inet addr:169.254.9.189 Bcast:169.254.255.255 Mask:255.255.0.0   UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1                [LIST]
[*]and in the interfaces (/etc/network) folder :
auto lo                                                          iface lo inet loopback                                           # The primary network interface                                  auto eth0                                                        iface eth0 inet static                                           address 192.168.0.150                                            netmask 255.255.255.0                                            network 192.168.0.0                                              broadcast 192.168.0.255                                          gateway 192.168.1.1                                              Any response are greatly appreciated.[/LIST][/LIST][/LIST][/LIST]

---

### Post by Iowan on 2009-10-17
Which is easier to read/debug? > **sham08 said:**
> [list]and in the interfaces (/etc/network) folder :
auto lo iface lo inet loopback # The primary network interface auto eth0 iface eth0 inet static address 192.168.0.150 netmask 255.255.255.0 network 192.168.0.0 broadcast 192.168.0.255 gateway 192.168.1.1 [/list]or 
```
auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static 
   address 192.168.0.150 
   netmask 255.255.255.0 
   network 192.168.0.255 
   gateway 192.168.1.1
```The static address (and network) should be in the same subnet as the gateway (192.168.1.X) - and static address should be outside the range of your DHCP server.

---

### Post by sham08 on 2009-10-17
> **Iowan said:**
> Which is easier to read/debug? or 
```
auto lo 
iface lo inet loopback 

# The primary network interface
auto eth0
iface eth0 inet static 
   address 192.168.0.150 
   netmask 255.255.255.0 
   network 192.168.0.255 
   gateway 192.168.1.1
```The static address (and network) should be in the same subnet as the gateway (192.168.1.X) - and static address should be outside the range of your DHCP server.What do you mean by 'to read/debug? The gateway is on default state because I have reset the modem by pressing the reset button (on the modem).

---

### Post by Iowan on 2009-10-17
Maybe I'm missing something... 
If the machine has an address in the 192.168.0.X subnet, then the gateway should be in the 192.168.0.X subnet. If the gateway is supposed to be 192.168.1.1, then the machine should be in the 192.168.1.X subnet. 
I've been wrong more times than I can count, I don't think work to have the machine in 192.168.0.X subnet with 192.168.1.1 gateway.

---

### Post by sham08 on 2009-10-17
I've made several configuration from the last time I posted the thread,based on several tips and solution I found online.But still to no avail.But right now (presently) the ~$ ifconfig -a shows :   inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0.      And in my modem web interface (192.168.1.1),the default gateway IP number is not there.

---

### Post by sham08 on 2009-10-17
Thanks for keep responding.I really appreciate your efforts.Right now,is there any chance that can I just return the configuration back to DHCP?And how to achieve it?I just want to be able accessing the Internet back.Help me.

---

### Post by Iowan on 2009-10-19
If Network Manager is still lurking in the background, returning to DHCP *should* be as easy as commenting out everything in */etc/network/interfaces* EXCEPT the first two lines (which set up "lo"). Then, restart or reboot. (I usually reboot to avoid complexities of restarting networking and NM in proper sequence)

---

### Post by sham08 on 2009-10-20
Hello Iowan.Sorry for not responding early.I wasn't able to log into the Internet.But today I've made some progress,using the problematic modem (the one that I used on my Ubuntu PC).I successfully accessing the Internet but using my brothers HP Notebook (on Vista).I assume the modem is back to normal/usable condition.For the next action,I guess I'm going to connect back the modem to my Ubuntu 9.04 (clean installed) PC.I'll get back to you later.Thanks for keep responding.

---

### Post by sham08 on 2009-10-27
Hello Iowan.Sorry for being lost for long time,as I've mentioned before I was unable to be on line.This evening was historical (just for me),eventually after a gruelling 2 weeks I successfully managed to solve the problem.As a proof,here I am,writing this post.All that I did was,deleted all the /etc/network/interfaces folder that exists and then I wrote a new script :                                  #  The loopback network interface
auto lo
iface lo inet loopback

#  The primary network interface DHCP
auto eth0
iface eth0 inet dhcp 

then I typed sudo /etc/init.d/networking restart,and 'wooila' I was browsing again.I knew that I'm on DHCP right now and not the 'static IP' as I was trying to accomplish initially.But with this result,I feel so grateful.And I still determine to configure a 'static IP', surely not now.Anyway,I really appreciate for all the solutions and help that you had provided.Thanks Iowan.You really a big help.

---

### Post by Iowan on 2009-10-27
Today, I've been preaching (probably too much) the benefits of setting up your router(DHCP server) to issue a static lease (based on MAC address). Machine always gets the same address, but reaps other benefits of DHCP address (like DNS servers). Some devices call it a "fixed" address.  It should be outside the range of your DHCP server (but still within the subnet).

---

