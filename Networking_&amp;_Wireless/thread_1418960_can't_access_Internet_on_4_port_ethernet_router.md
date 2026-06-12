---
title: "can't access Internet on 4 port ethernet router"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by sham08 on 2010-03-01
Hello.Recently I changed to a 4 port ethernet router (D-Link DSL-2542B Adsl2+)with intention to share Internet access with my brother (he's on Vista).Initially it all went well,but 3 days ago there were connection problems occured on the part of the ISP.Without realized the problem,I had reset the router.This morning I've been informed by the ISP that the connection has been re-established.So,I accessed the Internet via the 4 port router but failed to do so (server not found).Suspecting that the problem was from the 4 port router,I reverted to my old Adsl router (DSL-520B single port) and without any problem I managed to access the Internet back.I really need help to configure back the 4 port ethernet router to its initial state.Please help and thanks in advance for your help.

---

### Post by Iowan on 2010-03-01
Did you need to do any configuration when you originally set up the 4-port (that may not have survived the reset) like userid, password, etc?

---

### Post by pricetech on 2010-03-01
Never met a dlink that was more than a paperwieght, but:

Most routers have a "wizard" that steps you through the initial configuration.  Some include software they expect you to burden your winders machine with, but it shouldn't be necessary.

Just make sure you know the username and password for your DSL account and you should be good.

---

### Post by sham08 on 2010-03-01
Thanks Iowan and pricetech for the response.As I recalled back,it was an easy set-up (the 4 port router).My brother just plug-in all the cables and even without used the installation CD,we were on-line.However,I managed to log-in to the 4 port routers web interface ([http://192.168.1.1](http://192.168.1.1)) and tried the quick set-up (DSL Router Auto-connect).It came back with these messages "The DSL Router Auto-connect process cannot start.The ADSL connection is down.Assign VPI/VCI manually".But the DSL led light in front of the router is green.So,am I missed something on the configuration or any other problem of the ISP? Thanks for any responses.

---

### Post by sham08 on 2010-03-02
I just re-configure the 4 port router using the installation CD on my laptop (on Vista),because I can't do it via my PC (on Ubuntu 9.04).In the process that made via Vista,I get this message,said "Internet connection fail.Check with your ISP".However,oddly, I managed to get back the green led light (Internet led light) on the router.Normally (according to my last experience),if that green led light lit,means I should successfully accessed the Internet.But still,to no avail and again with this irritating message "Server not found".I really,desperately need someone on this forum to show me the right path.Please.

---

### Post by efflandt on 2010-03-02
For DSL you usually need a username and password for the PPPoE connection.  Resetting it may have cleared that back to original factory settings.  It is not clear if you made sure that the proper username and password are set for PPPoE on the modem/router.

Also you usually cannot have more than one DSL modem connected at the same time or neither one will work.  So make sure that you disconnect the other one from the phone line when attempting to use this one (merely turning it off the other one is not good enough, it must be disconnected from the phone line).

---

### Post by sham08 on 2010-03-02
Thanks efflandt for your reply.You get me wrong.I only had a single Internet connection that shared by a laptop (run Vista) and a PC (run Ubuntu 9.04) through a 4 port router.Before this I used a single DSL router to go on-line.So there's no issue on connecting both modems at the same time.The problem arised after I reset the 4 port router to factory setting,and I couldn't accessed the Internet.But if I switched back to my old DSL single router,I manage to get back on-line without any problem.About the username and password,I'm sure that I've entered it correctly. Because I was able to lit up the Internet connection led (to green) on the 4 port router using the Vista (laptop).Hope to hear from you again.Thanks

---

### Post by pricetech on 2010-03-02
It almost sounds like your dlink has gone bad.  Is it new enough that you can return it as defective ??  Perhaps instead of a router you could get a switch and keep using your single port router, unless it has some sort of bizarre configuration that doesn't allow for more than one client, which it shouldn't.

---

### Post by sham08 on 2010-03-02
Thanks pricetech.Not sure if my Dlink has gone crazy,because I had used it for 2 weeks.And as I mentioned above,I've managed to get the Internet led light,green again through my laptop (on Vista) and used the original 4 port router installation CD. According to the router manual "a solid green light indicates the WAN IP address from IPCP or DHCP and DSL is up or a static IP address is configured and PPP negotiation has been successfully completed".Unfortunately,I've failed to complete the set-up via Vista and the CD until I reached a message "Internet connection fail.Check with your ISP".Then I switched back to my Ubuntu PC.Ignored the green led light,I log-in to the router web interface and find out that the "Quick set-up" page has been gone and replaced by the summary table that pointed the current status of DSL connection of the 4 port router :
Line rate - Upstream (Kbps) : 512
Line rate - Downstream (Kbps) : 2048
LAN IP Address      : 192.168.1.1
Default Gateway     : 1.1.1.1
Primary DNS server  : 192.168.1.1
Secondary DNS server: 192.168.1.1
So,before I declare that this router is defective,anybody who have any last opinion, please help me out.Thanks.

---

### Post by pricetech on 2010-03-02
Does it show you a WAN IP ??  LAN looks OK except for Default Gateway, which should be the same as the router's IP.

---

### Post by sham08 on 2010-03-02
Here's the latest connection status on the router web interface using my laptop (Vista).WAN info : 
Port / VPI / VCI   : 0 / 0 / 35
Con.ID             : 1
Category           : UBR
Service            : pppoe_0_0_35_1
Interface          : ppp_0_0_35_1
Protocol           : PPPoE
Igmp               : Disabled
QoS                : Disabled
State              : Enabled
Status             : Up
IP Address         :2.2.2.52
Another new development that I just realize in the Diagnostic page,while the other diagnostics are all 'PASS',the 'Ping primary Domain Name Server' is 'FAIL'.Any clue? And again,Thanks.

---

### Post by pricetech on 2010-03-02
You don't appear to be getting a DNS server from your ISP.  At least it's not listed.

You should be connecting though, just may not have a DNS server.  Try manually entering DNS servers in your router and see if that helps.

208.67.222.222 and 208.67.220.220 are Open DNS

---

### Post by sham08 on 2010-03-02
Actually my ISP had provided primary DNS (202.188.1.5) and secondary DNS (202.188.0.133),and I've entered it through the router web interface in the DNS server configuration section.I unchecked the "Enable Automatic Assigned DNS" and then entered the DNS provided by my ISP.After that the router needed to reboot.But I found out after the reboot process,the "Enable Automatic Assigned DNS" box,back to its initial state (check again).Seems that the router didn't recognized the DNS.What should I do? Thanks.

---

### Post by pricetech on 2010-03-02
Short answer; return it.  It's looking more and more like you got a bad router.

---

### Post by redmk2 on 2010-03-02
> **sham08 said:**
> ... "Quick set-up" page has been gone and replaced by the summary table that pointed the current status of DSL connection of the 4 port router :
```
ine rate - Upstream (Kbps) : 512
Line rate - Downstream (Kbps) : 2048
LAN IP Address      : 192.168.1.1
Default Gateway     : 1.1.1.1    [COLOR="Red"]<-- should be 192.168.1.1[/COLOR]
Primary DNS server  : 192.168.1.1
Secondary DNS server: 192.168.1.1  <-[COLOR="Green"]<-- Use the ISP dns server IP here[/COLOR]
```
So,before I declare that this router is defective,anybody who have any last opinion, please help me out.Thanks.

I believe you need to have the default gateway set correctly.  See my above note in red.  

There are 2 interfaces on a typical router .  The LAN side (the gateway interface) and the WAN side (the DSL connection.  The 4 ports are also the LAN side.  make sure none of your computers use the LAN address 192.168.1.1.  DO MAKE SURE that they are all addressed with 192.168.1.*some number between .2 and .254*.  Can you tell me what is the WAN side IP address?

Edit: you should also add the ISP dns server address the secondary dns listing.

---

### Post by sham08 on 2010-03-02
Thanks redmk2 for your good opinion.Could you show how I should act to perform the action as you state in your thread.I'm quite new in Ubuntu and still in the learning stage.Worst part is networking and Internet connection make me a big headache.Please!

---

### Post by sham08 on 2010-03-02
> **pricetech said:**
> Short answer; return it.  It's looking more and more like you got a bad router.Thanks for your side of opinion.But I should view other possibilities before I return it and ask for  replacement.

---

### Post by redmk2 on 2010-03-03
> **sham08 said:**
> Thanks redmk2 for your good opinion.Could you show how I should act to perform the action as you state in your thread.I'm quite new in Ubuntu and still in the learning stage.Worst part is networking and Internet connection make me a big headache.Please!

This is not really an Ubuntu problem, but rather a D-Link config exercise.  But, for me that is no problem.  Fortified with enough coffee anything is possible.  :-)  

The D-Link device is distributed primarily in the Euro zone.  Are you in Europe?  The manual for this device is available [_[COLOR="Navy"]here[/COLOR]_]("ftp://ftp.dlink.co.uk/dsl_routers_modems/dsl-2542b/manual.pdf") if you do not have one already.

This explanation will get long winded but is is important the you understand a little of what you are doing before you start this.  I will explain as we go along.

As I stated earlier there is a WAN (ISP) side and a LAN (local (your network)) side.  I can't help you with the WAN side settings, but you ISP can.  The original device has the same WAN side setting too.  The device should have a web interface. You could look there for the info. 

> I really need help to configure back the 4 port ethernet router to its initial state

I believe the router is fine.  I think your Ubuntu host needs configuration.  I need some information from that host.  Can you provide me the output for the following command```
ifconfig -a
```.

Now let's see that we have the router's basic configuration set  correctly.  Take a look at page 26 of the manual (Section 3) titled LAN setup.  See the directions at the top of the page to start.```
To access the LAN Setup window, click the **[COLOR="Red"]LAN Setup button[/COLOR]** in the Setup directory.
``` 

The first section is ***router Settings***.  This is where you put the LAN side IP address of the router.  That is 1[FONT="Courier New"]92.168.1.1 [/FONT]and in the second box we put the subnet mask.  I will assume it is [FONT="Courier New"]255.255.255.0[/FONT].  This is as it is listed in the manual.

Next question;  Were (are) you using DHCP to assign IP addresses to you computers?  The only other option is to manually set up that information.  If you are using DHCP then the Ubuntu host needs to be setup to ask for the IP addresses automatically.  DId you do that through Network manager?   If so is the router still setup do provide a pool of IP addreses.  That is what the rest of the page (26) in the manual is discussing.

If you are using DHCP (from the router) then it will automatically supply the correct default gateway for you (see the last paragraph on page 26).

The DHCP server will also supply the correct DNS servers for you.  But only if you supply the IP addresses.  See the instructions on page 27.  Note the following *[COLOR="DarkOrchid"]"You may also configure DNS settings when using the Router in DHCP mode (Advanced > DNS Setup)"[/COLOR]*.

The last thing is to check the computer settings.  You can use the Vista host for this.  look at the TCP/IP settings.  You can find those in the Control Panel>>Network Settings section.  Check whatever interface you are using to see if the settings are configured automatically.

I'm sure that you will have more questions, but this is a start.

Let me know what you find.

One last thought -- If you would have purchased a simple 4 or 8 port switch and connected the original DSL router into one of the ports along with your computers into the other ports, you would have the same as the router you purchased.  The new router just has the 4 port switch integrated into the DSL router.  Just something for you to think about.

---

### Post by sham08 on 2010-03-03
Thanks redmk2 and sorry for late reply.The Internet connection still have problems.I'm from Malaysia,and you can imagine how the third country standard of providing Internet connection to their users (including me). About the manual,yes,I've got it.It came along with the installation CD.  Its totally different from the version that you recommended.But still the same contents.For the command that you asked,here is it:
sam1430@sam1430-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8d:bc:28:3b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:febc:283b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154959 errors:0 dropped:10 overruns:0 frame:0
          TX packets:119193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176572812 (176.5 MB)  TX bytes:10705251 (10.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208 (208.0 B)  TX bytes:208 (208.0 B)

pan0      Link encap:Ethernet  HWaddr b2:9b:a8:8b:05:15  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
Still not finished with all the configurations that you recommended (in progress).Yes,I'm using DHCP initially and unfortunately about Network Manager,I had switched to WICD.The problem is I can't open the WICD GUI. Every time I clicked the WICD icon that still appeared on my desktop,no single thing happened.It has been in that state for quite along time. In fact,I've posted a thread related to the WICD on this forum and till now, the problem never near to be solved.So,I decided to let it be,because it never interrupted every time I wanted to access the Internet.Okay,time to get back to work.I'll keep you in touch on the progress.See you later.

---

### Post by dineshs on 2010-03-03
If it is a DNS problem I think editing the file /etc/resolv.conf will solve it
```
sudo gedit /etc/resolv.conf
```
add this line
```
nameserver 4.2.2.1
```
save the file and close

---

### Post by sham08 on 2010-03-04
I'm sorry to take such a long time to respond to all your help guys.Still there's problem on my side to access the Internet.For redmk2,my bad.I've posted wrong information on the command ifconfig -a.It make so confusing,to plug-in and plug-out every moment when I have to access the Internet.So this is the right information from the command :
sam1430@sam1430-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8d:bc:28:3b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:febc:283b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:742 (742.0 B)  TX bytes:5579 (5.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208 (208.0 B)  TX bytes:208 (208.0 B)

pan0      Link encap:Ethernet  HWaddr 9a:b9:75:0b:56:db  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
There are several development that I should inform.Eventually I managed to fill in the provided ISP DNS in the problematic router web interface. The latest device info are:
LAN IP Address    :192.168.1.1
Default Gateway   :1.1.1.1
Primary DNS server   :202.188.0.133
Secondary DNS server :202.188.1.5
In the Routing - Default Gateway page I realized that the box on "Use Default Gateway IP Address" is checked with 1.1.1.1 is the IP.Another development that I should mention also are in the "Diagnostic" area, still "ping the Domain Name Server" came with "FAIL" result.
I'm hoping all this details provided should give you guys a better picture of my router state.And please don't give up on me.I really appreciate all your efforts.Thanks.

---

### Post by sham08 on 2010-03-04
> **dineshs said:**
> If it is a DNS problem I think editing the file /etc/resolv.conf will solve it
```
sudo gedit /etc/resolv.conf
```
add this line
```
nameserver 4.2.2.1
```
save the file and closeThanks dineshs to give up your time and look over my problem.I've ran the command and add the line,but so far its didn't make any changes.Hope to hear other thoughts from you again.

---

### Post by dineshs on 2010-03-04
Open firefox, type 192.168.1.1 as the web address and hit enter.This will open your modem page.Contact your ISP and ask them how to configure your modem.Normally an ADSL connection has a username and password.If you are not able to open 192.168.1.1 then configure network as follows.Open terminal
```
sudo gedit /etc/network/interfaces
```
copy and paste the following into the file
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
```
save and close the file then try

---

### Post by redmk2 on 2010-03-04
> **sham08 said:**
> ...In the Routing - Default Gateway page I realized that the box on "Use Default Gateway IP Address" is checked with 1.1.1.1 is the IP.
The *Default Gateway *should be 192.168.1.1.

> 

Another development that I should mention also are in the "Diagnostic" area, still "ping the Domain Name Server" came with "FAIL" result.

Try pinging the router address (192.168.1.1).> 
I'm hoping all this details provided should give you guys a better picture of my router state.And please don't give up on me.I really appreciate all your efforts.Thanks.

---

### Post by pricetech on 2010-03-04
> **sham08 said:**
> Thanks for your side of opinion.But I should view other possibilities before I return it and ask for  replacement.

Your call, but I honestly think there is something wrong with it.

As to hard coding your DNS in Ubuntu, that might work, but it's something you shouldn't have to do.

To reiterate, it does not appear to be a problem with Ubuntu, but with the router itself.

Your Default Gateway should be the same as the router's IP.  In your case this is 192.168.1.1.  If your router shows anything else, that simply makes no sense.  It should "know" that it is the default gateway.

It's assigning itself as your DNS server. Most of the time this works since most routers can forward DNS requests to, and some even cache responses from, your ISPs DNS servers.  That doesn't appear to be working so I would change the DNS server IN THE ROUTER, NOT ON YOUR COMPUTER to a known valid set of DNS servers.  I've listed a few below.
208.67.222.222 , 208.67.220.220 , 4.2.2.1 , 4.2.2.2
Those are Open DNS and Verizon's public DNS servers respectively.

I'm more interested in what your router shows on the WAN side.  If it isn't able to connect properly, then nothing behind it will connect either.

I don't think that manually assigning the IP on your computer will help since you do seem to be getting an IP from your router, else you would not be able to "talk" to it.  Let us know what shows on the router's WAN side and we'll go from there.

---

### Post by sham08 on 2010-03-05
> **redmk2 said:**
> The *Default Gateway *should be 192.168.1.1.

Try pinging the router address (192.168.1.1).This is the result when I ping 192.168.1.1 via terminal :
sam1430@sam1430-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.963 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.867 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.880 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.869 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.875 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.883 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.855 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.876 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.882 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.889 ms
^C
--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 0.855/0.883/0.963/0.048 ms
Thanks redmk2 for your continuous replies.

---

### Post by sham08 on 2010-03-06
> **dineshs said:**
> Open firefox, type 192.168.1.1 as the web address and hit enter.This will open your modem page.Contact your ISP and ask them how to configure your modem.Normally an ADSL connection has a username and password.If you are not able to open 192.168.1.1 then configure network as follows.Open terminal
```
sudo gedit /etc/network/interfaces
```
copy and paste the following into the file
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
```
save and close the file then tryThanks dineshs for your consult.Frankly,before this I went a lot of trouble to configure my PC (Ubuntu) from DHCP to static IP.Instead,I've never made it.I give you here my present /etc/network/interfaces file :
# The loopback network interface
auto lo
iface lo inet loopback

# isp
auto eth0
iface eth0 inet dhcp
This is the configuration that go well on my modem but problem on the 4 port router mentioned.So,is it possible to run DHCP on 2 separate PCs via a 4 port router (that goes well initially)?Hope to hear from you again.

---

### Post by sham08 on 2010-03-06
> **pricetech said:**
> Your call, but I honestly think there is something wrong with it.

As to hard coding your DNS in Ubuntu, that might work, but it's something you shouldn't have to do.

To reiterate, it does not appear to be a problem with Ubuntu, but with the router itself.

Your Default Gateway should be the same as the router's IP.  In your case this is 192.168.1.1.  If your router shows anything else, that simply makes no sense.  It should "know" that it is the default gateway.

It's assigning itself as your DNS server. Most of the time this works since most routers can forward DNS requests to, and some even cache responses from, your ISPs DNS servers.  That doesn't appear to be working so I would change the DNS server IN THE ROUTER, NOT ON YOUR COMPUTER to a known valid set of DNS servers.  I've listed a few below.
208.67.222.222 , 208.67.220.220 , 4.2.2.1 , 4.2.2.2
Those are Open DNS and Verizon's public DNS servers respectively.

I'm more interested in what your router shows on the WAN side.  If it isn't able to connect properly, then nothing behind it will connect either.

I don't think that manually assigning the IP on your computer will help since you do seem to be getting an IP from your router, else you would not be able to "talk" to it.  Let us know what shows on the router's WAN side and we'll go from there.Thanks pricetech to keep on responding.Maybe its true as you said earlier,its the router defection. But at the moment I also shouldn't rule out other possibilities.As DNS solution that you provided,I've tried earlier as recommended by dineshs (4.2.2.1).But returned with no improvement.However,this is the present WAN info as stated in the router web interface :
Port / VPI / VCI        : 0 / 0 / 35
Con . ID                : 1
Category                : UBR
Service                 : pppoe_0_0_35_1
Interface               : ppp_0_0_35_1
Protocol                : PPPoE
Igmp                    : Disabled
Qos                     : Disabled
State                   : Enabled
Status                  : UP
IP Address              : 2.2.2.11
Hoping for your next reply.Thanks.

---

### Post by dineshs on 2010-03-08
I am not an expert But I think the default gateway seen in the modem is the public IP allotted by a network element maintained by your ISP.If that is the case then the only reason for not getting internet is NAT.Access your modem menu, enable NAT,enable default route,then save and reboot modem

---

### Post by pricetech on 2010-03-08
OK.  Your router is getting an IP from your ISP, but no gateway for it is listed.  It has to have a default gateway too, plus DNS servers.

Is there another screen that give you more IP information ??

---

