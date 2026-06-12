---
title: "Biggeners guide to Internet Connection Sharing with 3G"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by Nunu on 2010-02-12
I thought this could be a nice guide help someone to share a 3G internet connection. 

Lets say you have two PC a laptop and Desktop the laptop has an internal 3G card and the desktop no internet. Both PC's has nic's. All you want to do is have both PC's connected to the internet through the 3G card. 

Start by giving both PC an IP address in the same range:

Go System -> Preferences -> Network Connections...

Give each PC a IP address and sub net e.g 10.10.1.2 255.255.255.0 and 10.10.1.3 255.255.255.0

Dont add a gateway or DNS on the PC that has an internet connection. 

The PC that needs connection give it the gateway address of the other pc lets say the one with internet connection is 10.10.1.2 then use that as a gateway. 

The DNS server you can get by right clicking your connection states next to the power options on the main tool bar. go to connection information and select the tab for your 3G card you should see a primary and secondary DNS address use any one of the two as the DNS for your second PC. reboot both afterwards and you should have full internet access on both PC's.

If this guide did not work for you let me know so we can try and resolve it.

---

### Post by Sylslay on 2010-02-12
I just mention , 
If You don.t have working LAN cable ( driver issue or cable is to short),
You may link 2 PC with wi-fi in  Ad-Hoc mode. (wireless LAN between 2 PC)

To set two addapters need:
give then aswell Ip addres , gatway of this pc with 3g connection and DNS, 
Mark as sharing connection for others.

Do need brige coonnection between 3g and wf-fi  or 3g and lan on PC with internet acces?
Scenario with lan and lan-wi-fi on windows or linux OS.

---

### Post by mbuotidem on 2010-05-30
Nunu,  Thanks for this post. I am trying to do exactly what you mentioned - share a 3g internet connection. I followed your steps almost exactly, the only thing I did differently was that I used open dns servers instead of my 3g connection provider's servers and I didn't succeed. I even posted a thread before i found this thread. It's at [http://ubuntuforums.org/showthread.php?p=9383319&posted=1#post9383319](http://ubuntuforums.org/showthread.php?p=9383319&posted=1#post9383319). I plan to try again using my 3g connection providers dns servers but i am not sure that will solve the problem. I use Ubuntu 10.04 Lucid Lynx. And if I succeed in sharing the 3g connection, I plan to connect my nic to the internet port on my  router and then connect my other pc's to the router, since i have more than one pc I would like to share my connection with.


I am wondering if there is any special configuration I would need to make in order for my router to share the internet that it will receive from the pc with the internet connection. 

I observed something strange though. When I set my auth eth0 ip settings, and then I go to network tools, and select Ethernet connection, the setting I just made and applied do not appear. I wonder why that is the case.

---

### Post by Nunu on 2010-05-31
HI mbuotidem.

Thanks for your post, I have not yet had a chance to try your configuration but that does sound a little strange. have you tried connecting to a web site using the sites IP address instead of the URL? usually if its a DNS issue, using the IP address will let you know if it is. All the DNS server does is look at the URL and then point the client machine (Your Comp) to the corresponding IP. By browsing through the IP, you will be able to see if it is indeed DNS or network. You can get a web sites IP by pinging it from the machine that has a working connection. Please let me know what was the outcome of this test. 

Which router are you using, usually there is a little routing configuration that needs to be done on some routers, but this depends entirely on the brand, model, and complexity of the device that your using. I used an old Cisco router that my company turfed, and all I needed to do was clear the old Routing table, add my own little table and reboot. mind you I don't really know why I used a router as it was a simple two peer network... :)

---

### Post by mbuotidem on 2010-05-31
Nunu, thanks for the reply. In my spare time, i will try pinging the ip of a website when I have some extra time on my hands and none of my family members is around. but right now, I am under pressure to get the network going. I managed to convince my family to switch to Ubuntu from Xp and they are about to slaughter me if I don't get them connected to the internet asap. Anyway I tried using the setting **Shared to other computers** on the pc that is acting on my server(auto eth0) and then on my client pc I chose Automatic(Dhcp). Wham! my client was browsing immediately! 

So, hurdle 1 is solved. Hurdle two now is to get my router to share the internet. I tried connecting the cable from my auto eth0 that  was formerly connected to my client to my routers internet port. I then connected the client to one of the routers Ethernet ports. 

As you said, there is some configuration that needs to be done on the router but I am not sure exactly what to do. And I am not sure if what i plan to do is even feasible. Previously, in my windows network, I was sharing my 3g modem from a windows pc and then using my router as a switch. My windows pc with the internet connection was doling out the dhcp and the router was just acting as a switch. Now, I plan to have the router, act as a router- i.e give out the dhcp. The question now in my mind is: Doesn't choosing the option **Shared to other computers** mean that my current server is doling out dhcp? If so, can my router also dole at dhcp at the same time? that is, can there be two devices providing dhcp on the same network? If they can be two devices doing dhcp on the same network, can they be on the same subnet(cos thats how my network is currently configured, my auto eth0 is using the same subnet as my router is)? 

 I have a Linksys Wireles-G Broadband Router- WRT54G2. First of all, I have the option to chose if the router will act as a Gateway or as a Router. It says that if my router is hosting the internet connection, I should chose the Gateway option. But since my router is not hosting my connection (i hope I am right in assuming that) my Server pc is hosting the connection, I chose router. 

After choosing Router, there are some other configurations I have to make.Under the Advanced routing tab of my router,  there is RIP which is currently disabled and I don't think I need it.
Operating  Mode: Router(other option is gateway)
Dynamic Routing:  RIP : Disabled
Static Routing: Select Set No. 1
Enter Route name [Blank ]
          Destination  LAN IP:
           Subnet  Mask:
           Default  Gateway:
           Interface:  [LAN &  Wireless]{other options are  and  WAN(Internet)}                                                                                                                                                                                                                                                                   
Show routing table: (clicking this option gives me the following table)

**[FONT=Arial][COLOR=#0000ff]Routing Table Entry List[/COLOR][/FONT]**                   [FONT=Arial]Destination  LAN IP[/FONT]         [FONT=Arial]Subnet  Mask[/FONT]                   [FONT=Arial]Gateway[/FONT]                     [FONT=Arial]Interface[/FONT]               
                                                        0.0.0.0                 0.0.0.0                    10.82.83.1             WAN  (Internet)    
                                                     10.82.83.0         255.255.255.0              10.82.83.11           WAN  (Internet)                    
                                                  192.168.1.0         255.255.255.0              192.168.1.1           LAN  & Wireless                                     

I don't know where 192.168.1.0 comes from, i guess its my routers IP. 
10.82.83.0 is the IP address of my Server pc, the one getting the internet. 
255.255.255.0 is also the net mask of my server pc. 
I don't know where 10.82.83.11 comes from.  


That all from the Advanced Routing tab of my Router. 
Then the basic Setup Tab :


                 Automatic Configuration - DHCP ( The other options are Static,  IPPPPoE, PPTPL, 2TP, Telstra  Cable)[B]
Optional  Settings[/B][SIZE=2][B]
(required  by some ISPs)
[/B][/SIZE][FONT=Arial][SIZE=2]Router Name: 
[/SIZE][/FONT]                                                                                        [FONT=Arial][SIZE=2] Host Name: [/SIZE][/FONT]                                                       [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] Domain Name: [/SIZE][/FONT]                                                       [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] MTU:[/SIZE][/FONT]           **     Auto (**other option is **Manual             **                                            [SIZE=2])
[/SIZE]                                 [SIZE=2]Size:[/SIZE]                                                                                                                                                                                                                                                                [SIZE=2]**[FONT=Arial][COLOR=#ffffff]Network Setup[/COLOR][/FONT]**[/SIZE]
[SIZE=2]**Router  IP**[/SIZE]                                 [SIZE=2] Local  IP Address:[/SIZE]            192.168.1  .1                                             [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] Subnet Mask:[/SIZE][/FONT]                                                     255.255.255.0                         [SIZE=2][B]
Network  Address[/B]
**Server  Settings (DHCP)**[/SIZE]                                 
[SIZE=2] DHCP  Server:[/SIZE]           **Enable**  **Disable**                                            [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] Starting IP  Address:[/SIZE][/FONT]            **192.168.1.**100                                            [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] Maximum  Number of  DHCP Users:[/SIZE][/FONT]                                                        [SIZE=2]
[/SIZE]                                 [FONT=Arial][SIZE=2] Client Lease  Time:[/SIZE][/FONT] 0 minutes  (0 means one day)                          [SIZE=2]
[/SIZE][FONT=Arial][SIZE=2] Static DNS 1: [/SIZE][/FONT]  .  .  .   [SIZE=2]208.67.222.22
[/SIZE][FONT=Arial][SIZE=2]Static DNS 2: [/SIZE][/FONT]  .  .  .   [SIZE=2]172.30.1.241[/SIZE]
[FONT=Arial][SIZE=2] Static DNS 3: [/SIZE][/FONT]  .  .  .                       [SIZE=2]66.178.2.25[/SIZE]
                                 [FONT=Arial][SIZE=2] WINS:0 [/SIZE][/FONT]             0.  0.0  .                                                                                                                                                                                                                                                      

[SIZE=2]**Time  Setting**[/SIZE]                                 [SIZE=2] Time  Zone:[/SIZE]                                                        [SIZE=2]
[/SIZE]                                 

I don't know if I disabled dhcp my clients which are connected to the routers ethernet ports will work and I am about to try that. I also don't know if perhaps i should be using the gateway setting instead of the router setting.

wow. i've typed so much and i hope i have not inadvertently confused anyone. 

will keep you guys posted.

---

