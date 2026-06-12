---
title: "Systematic browser HTTP timeout request and failure with several websites"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by BlackLight01 on 2012-06-07
I've suddenly started to experience a weird issue with the load of several HTTP pages. Among these:

[LIST]
[*] **Facebook**. If I'm not logged in (or I've manually removed the cookies), and I go to [www.facebook.com]("http://www.facebook.com"), everything works flawlessly and the page loads. Once I log in, the page gets stuck on "Waiting for www.facebook.com" forever, until I have an error message. Same if I try to open the page when I'm already logged in
[LIST]
[*] This issue occurs with:
[LIST]
[*] Firefox (13.0)
[*] Chromium (18.0)
[*] Opera
[/LIST]
 
[*] But not with (weirdly):
[LIST]
[*] surf
[*] vimprobable
[*] jumanji
[/LIST]
 
[/LIST]
 
[*] **YouTube**. In this case, the page loads correctly, but once I try to start a video, the streaming gets stuck as "waiting" while Firefox notifies "Waiting for o-o.<something>.youtube.com" indefinitely
[LIST]
[*] This issue occurs with:
[LIST]
[*] All the browsers I've tested
[/LIST]
 
[/LIST]
 
[/LIST]

**** My configuration ****

[LIST]
[*] Toshiba Satellite laptop
[*] Ubuntu 12.04 - 64 bit
[/LIST]

**** What I've already tried ****

[LIST]
[*] The problem randomly started to occur two days ago. I used Ubuntu 11.10. I've tried to do a fresh install of Ubuntu 12.04, and the problem still occurs
[*] I've tried, in case of Firefox, to copy "~/.mozilla" somewhere else, restart Firefox, and then use the new fresh profile (no settings, cookies, addons and cache at all). Still no luck
[*] I've tried to create a brand new system user, log in with that user, and use both Firefox and Chrome for surfing to Facebook and Chromium. Still nothing
[*] I've tried to change /etc/resolv.conf. It uses by default my router's IP address as DNS. I've tried both with OpenDNS and Google DNS. Still no luck
[*] I've tried to install Flash-Aid for Firefox and let it download the latest official version of Flash. Still no luck
[*] (Of course) I've tried to restart the system
[/LIST]

Weirdly, the problem only happens on Ubuntu. Restarting my system on Windows 7, everything works fine. Same at my office's computer.

**** HTTPS debugging ****

I've tried the following sequence:

[LIST]
[*] Start Wireshark
[*] Open a new tab in Firefox
[*] Open [http://www.facebook.com](http://www.facebook.com) from there when the problem occurs
[/LIST]

This is what I've sniffed on the cable. It looks like the SSL handshake fails for some reason (why??), I see several TCP retransmissions from my side, after a change cipher specification request, then an "encryption alert from my side", and finally a duplicated ACK message from Facebook's side, and then nothing else. Why does this happen?

```

192.168.1.4    31.13.72.4    TCP    42225 > https [SYN] Seq=0 ...
31.13.72.4    192.168.1.4    TCP    https > 42225 [SYN, ACK] Seq=0 Ack=1 ...
192.168.1.4    31.13.72.4    TCP    42225 > https [ACK] Seq=1 Ack=1
192.168.1.4    31.13.72.4    TLSv1        Client Hello
31.13.72.4    192.168.1.4    TCP    https > 42225 [ACK] Seq=1 Ack=398
31.13.72.4    192.168.1.4    TLSv1        Server Hello, Change Cipher Spec, Encrypted Handshake Message
192.168.1.4    31.13.72.4    TCP    42225 > https [ACK] Seq=398 Ack=134
192.168.1.4    31.13.72.4    TLSv1        Change Cipher Spec, Encrypted Handshake Message
192.168.1.4    31.13.72.4    TLSv1        Application Data
31.13.72.4    192.168.1.4    TCP    https > 42225 [ACK] Seq=134 Ack=445
192.168.1.4    31.13.72.4    TLSv1        [TCP Retransmission] Application Data
192.168.1.4    31.13.72.4    TLSv1        [TCP Retransmission] Application Data
192.168.1.4    31.13.72.4    TLSv1        [TCP Retransmission] Application Data
192.168.1.4    31.13.72.4    TLSv1        [TCP Retransmission] Application Data
192.168.1.4    31.13.72.4    TLSv1        Encrypted Alert
31.13.72.4    192.168.1.4    TCP        [TCP Dup ACK 97#1] https > 42225 [ACK] Seq=134 Ack=445

```Any help would be really, really useful. I can't figure out what's going on, why it started all of a sudden, why it also won't go with a fresh Ubuntu installation and with another user, why it only happens with Facebook and YouTube, why it doesn't happen on Windows...in the meantime, I can't use these websites at all :(

Thanks,
Fabio

***** EDITED *****

I've tried to post this message here from my Ubuntu installation before, and the form submission failed as well, in the same way. Posting it from Windows is working now. This means that this systematic HTTP problem occurs more often than I expected.

---

### Post by poolet on 2012-06-07
Usually dup acks are from packet loss. Check your speed and duplex(full or half?). Are you going from GIG to 100MB with a device ??  Have you looked at the port stats on the device?? Are there duplex links?? Check for places that are forced 100/f on one end and left auto on the other.. 100% the results are not the proper.. If you had sniff it, try and get captures from two locations at once. Then you can see if you're actually dropping data somewhere...For example try as close to the cc terms as possible..!! If you see data egress the cc terms and don't see it on the modem/router/switch link you know that you have got a problem. If not try again from outside of modem/router(set filters). If you're dropping data you will have an idea of where comes... 

::**Note**:: I had almost the same problem. I had remove my browser and installed an old one.. For example try to use older versions of firefox.. At the end flush dns cache, at any time do not capture or sniff network without clear your cookies and dns cache is wrong(you can do it only to check differences )...  The captures identify your older cookies and log cache and capturing according with that, with result to get wrong details of determining the problem..!!

Something that I forget to say: Can you give as more details about your network topology ?? Seems that something is going wrong with the modem, get the default gateway and login as root, call your ISP to get user and pass, login via telenet and make "**show run**" command, check the details and talk with customer service.. you can also run "**debug**" to be more helpful...!!

---

### Post by BlackLight01 on 2012-06-08
Hi,

Thanks for your reply. I've done another test by using an internet key, instead of my home connection, and in this case it looks like everything works. The cause of the problem seems then to be related to some ISP problem. Anyway, what is weird is that the problem occurs both connecting through ethernet cable and through WiFi connection. What is even more weird in my opinion, is that all the other devices I have here at home (a tablet, a smartphone, another laptop) do not seem to experience this problem. Same for this machine itself if I start it from Windows. Why does only Ubuntu seem to have this problem with my ISP? And even more weird, why some very minimalistic browsers (e.g. surf and jumanji) seem to be less impacted by this problem than Firefox, Chrome and Opera?

Thanks,
Fabio

---

### Post by poolet on 2012-06-09
Thats not weird!!! Windows have a lot of vagaries that can affect a whole network..  A very similar problem and strange is power safer.!! Check The link for the the specific problem, especially if your smart phone is windows mobile.. This problem has an explanation, you can check the link below:: 

[http://support.microsoft.com/kb/928152](http://support.microsoft.com/kb/928152)

Another problem is with firewall, Are you sure that windows machine doesn't used any firewall without realizing it??  Check what programs runs on startup windows, use the following link to help you::  Try also to disable windows firewall, 

[http://support.microsoft.com/kb/929135](http://support.microsoft.com/kb/929135)

We want to check the network mode of windows, Try to stared windows via "save mode with network" check the link below:: Results ?? 

[http://windows.microsoft.com/en-US/windows7/Advanced-startup-options-including-safe-mode](http://windows.microsoft.com/en-US/windows7/Advanced-startup-options-including-safe-mode)

Familiar problem with that is the following::  if you do the tutorial of this part make sure that if you don't have improve after that to delete the registry entry of windows:: 

[http://www.pctools.com/guides/registry/detail/899/](http://www.pctools.com/guides/registry/detail/899/)

More links that may are help below::: 
[http://support.microsoft.com/kb/956196](http://support.microsoft.com/kb/956196)
[https://supportforums.cisco.com/thread/2044610](https://supportforums.cisco.com/thread/2044610)
[http://windows.microsoft.com/en-US/windows7/Why-is-my-Internet-connection-so-slow](http://windows.microsoft.com/en-US/windows7/Why-is-my-Internet-connection-so-slow)

**::Note::  **If your problem isn't fixed, check step by step the whole problem, start capture your network without connected only ubuntu machine after 1-2 hours start connect each machine that you have, (smart phone etc) and see the respond of your destinations check the ACK's again by set a value of filtering and coloring on wireshark to be more easier to you to determine the troubleshooting, if isn't help you, start a capture with all your machines connected leave it for 20-30 min and save the capture file, attach the captures file here to see a exactly the path of your network until is reach the duplication ..

Good luck hope that you fixed it..!! :)

---

### Post by BlackLight01 on 2012-06-09
The point is that I have no Windows machines connected to my network,  except for this one that experiences the problem on Ubuntu, and also  both of my tablet and smartphone run Android, not Windows. I've also  tried by disconnecting all the other devices from the network and  leaving only my laptop with Ubuntu connected, but still not luck, same  for resetting my router to its factory settings. I really don't know  anymore what to do now :(

---

### Post by poolet on 2012-06-09
:) ok just to be clear... 

Please let us know your network topology as your network is working correctly (if it's works)

//***for example***//
cloud -> modem ->  pc1 -> pc2-> smart_phone -> printer 
209.xx.xxx.xx        //cloud
192.168.10.254    //modem
192.168.10.1       //pc1
192.168.10.2      //pc2  
192.168.10.3     //smart_phone
192.168.10.4    //printer 

now you can also let us know the network topology as **isn't** working proper..
At the end please open up a new terminal and type the following, also please paste the output here:: 


  //flush dns ```

sudo aptitude install nscd   
sudo /etc/init.d/nscd restart
``````
/sbin/route
/sbin/route -n
```  //display routing table


// active internet connections and open ports ```
 netstat -nat
sudo netstat -tulp       
**or**
sudo netstat -tulpn

``` //active/established connection ```
netstat -e
netstat -te
netstat -tue
```// insterface stats, RX,etc```
netstat -i
```

---

### Post by BlackLight01 on 2012-06-09
This is the topology of my network (where things fail):

```
[blacklight@gauss ~] $ sudo nmap -sP 192.168.1.0/27 

Nmap scan report for 192.168.1.1 [--> My router]
Host is up (0.00061s latency).
MAC Address: 00:24:89:45:F5:52 (Vodafone Omnitel N.V.)

Nmap scan report for 192.168.1.2 [--> My roommate's Android tablet]
Host is up (0.083s latency).
MAC Address: C8:60:00:27:43:01 (Unknown)

Nmap scan report for 192.168.1.3 [--> My Ubuntu box]
Host is up.

Nmap scan report for 192.168.1.4 [--> My Android tablet]
Host is up (0.071s latency).
MAC Address: 8C:77:12:5E:0C:70 (Unknown)

Nmap scan report for 192.168.1.5 [--> My Android smartphone]
Host is up (0.13s latency).
MAC Address: 98:0C:82:B4:A2:D4 (Unknown)
Nmap done: 32 IP addresses (5 hosts up) scanned in 5.16 seconds
```

When things work, I just disconnect from my network and use my Vodafone USB internet key, so I'm connected directly to my provider's 3G network in that case, not at my home network.

I've also tried to flush the DNS cache through nscd and also the route table looks ok:

```
[blacklight@gauss ~] $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.128 U     1      0        0 eth0
```

This is the list of active and established connections:

```
[blacklight@gauss ~] $ sudo netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1022/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1140/cupsd
tcp        0      0 127.0.0.1:54464         0.0.0.0:*               LISTEN      3319/beam.smp
tcp6       0      0 :::22                   :::*                    LISTEN      1022/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      1140/cupsd
tcp6       0      0 :::6600                 :::*                    LISTEN      14797/mpd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           22230/dhclient
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1050/avahi-daemon:
udp        0      0 0.0.0.0:46870           0.0.0.0:*                           1050/avahi-daemon:
udp6       0      0 :::41300                :::*                                1050/avahi-daemon:
udp6       0      0 :::5353                 :::*                                1050/avahi-daemon:
```

```
[blacklight@gauss ~] $ sudo netstat -tue
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode
tcp        0      0 gauss.local:53142       testing.bitlbee.or:6668 ESTABLISHED blacklight 394090
tcp        0   3364 gauss.local:37320       www-01-03-lhr2.fa:https FIN_WAIT1   root       0
tcp        0   3334 gauss.local:37311       www-01-03-lhr2.fa:https FIN_WAIT1   root       0
tcp        0      0 gauss.local:55621       mil01s17-in-f1.1e10:www ESTABLISHED blacklight 400269
tcp        1      0 109.112.66.128:57420    sumac.canonical.com:www CLOSE_WAIT  blacklight 105511
tcp        0      0 gauss.local:60885       mil01s17-in-f16.1e1:www TIME_WAIT   root       0
tcp        0   4927 gauss.local:37323       www-01-03-lhr2.fa:https ESTABLISHED blacklight 400336
tcp        0      0 gauss.local:59070       85.205.31.48:https      ESTABLISHED blacklight 400102
tcp        0   3416 gauss.local:37321       www-01-03-lhr2.fa:https ESTABLISHED blacklight 400287
tcp        1      0 109.112.66.128:53096    papeda.canonical.co:www CLOSE_WAIT  blacklight 105512
tcp        1      0 gauss.local:52208       mil01s17-in-f19.1:https CLOSE_WAIT  blacklight 60886
tcp        0   3364 gauss.local:37315       www-01-03-lhr2.fa:https FIN_WAIT1   root       0
tcp        0      0 gauss.local:60883       mil01s17-in-f16.1e1:www TIME_WAIT   root       0
tcp        0      0 gauss.local:50362       mil01s17-in-f17.1e1:www TIME_WAIT   root       0
tcp        0     37 109.112.66.128:44556    fa-in-f108.1e100.:imaps ESTABLISHED blacklight 114327
tcp        0   3336 gauss.local:37331       www-01-03-lhr2.fa:https ESTABLISHED blacklight 404228
tcp        0      0 gauss.local:40338       mil01s17-in-f6.1e10:www ESTABLISHED blacklight 400270
tcp        0      0 gauss.local:50360       mil01s17-in-f17.1e1:www TIME_WAIT   root       0
tcp        0      0 gauss.local:46779       grape.canonical.c:https ESTABLISHED blacklight 364665
tcp        0      0 gauss.local:36765       mil01s17-in-f0.1e:https ESTABLISHED blacklight 368963
tcp      328      0 gauss.local:47175       195.24.233.55:www       CLOSE_WAIT  blacklight 401471
tcp        0      0 gauss.local:35247       mil01s17-in-f18.1e1:www TIME_WAIT   root       0
tcp        1      0 109.112.66.128:52704    barbadine.canonical:www CLOSE_WAIT  blacklight 105517
tcp        0      0 gauss.local:50363       mil01s17-in-f17.1e1:www TIME_WAIT   root       0
```

And this is the list of the interfaces:

```
[blacklight@gauss ~] $ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0    119907      0      0 0         82574      0      0      0 BMRU
lo        16436 0     35743      0      0 0         35743      0      0      0 LRU
wlan0      1500 0        49      0      0 0            59      0      0      0 BMU
```

Thanks for the support,
Fabio

---

### Post by poolet on 2012-06-09
Ok. Ubuntu machine is on virtual box or something ??
Doesn't matter the answer I just want to know if yes what kind of network mode your using...
Before you continue try to delete the ubuntu machine from your router and add it at the end of your network, instead of 192.168.1.3, set the ubuntu machine 192.168.1.4 or whatever other ip except the old one that use to it.. 
if isn't help try to add static IP address for the ubuntu machine::

```
sudo gedit /etc/network/interfaces
```add the following lines and save::

> auto lo
iface lo inet loopback
iface eth0 inet static
 address 192.168.1.3
 netmask 255.255.255.0
 network 192.168.1.1     //should be like that 
 broadcast 192.168.1.0   // the same for broadcast
 gateway 192.168.1.1::**Note**:: For broadcast and network check your own ip's probably is as I have 
added but I am not sure since may differ from mine..!!! 

```
sudo /etc/init.d/networking restart
``````
sudo gedit /etc/resolv.conf
```set the following lines:: 

> # Generated by NetworkManager
domain lan
search lan
nameserver 192.168.1.1

---

### Post by BlackLight01 on 2012-06-10
Ubuntu runs on its own, no virtual box. I've also tried to force the IP  address to 192.168.1.10, both through DHCP reservation on the router and  static IP, but still no lock. Same for configuring 192.168.1.1 in  resolv.conf (it was already like that, before that I used OpenDNS).
 
 What is weird is that now the problem also occurs on my tablet and on my  roommate's tablet (only through browser, in both the cases). It's quite  clear now that the issue is not on Ubuntu's side, my ISP is going to  listen to me now. Do you have any further suggestions for a possible  workaround in the meantime?
 
 Thanks,
 Fabio

---

### Post by poolet on 2012-06-10
Before you continue to call customer service of your ISP  follow the steps:: I am pretty sure that you have problem with your modem or something is going wrong with tcp/ip protocol outside. 

**First**: download wirehare from here and install it:: [http://www.wireshark.org/](http://www.wireshark.org/)
(::note:: search on google for the installation details)

**Second**: Configure the wireshark to capture the interfaces of your machine (prefer one machine that **is works** fine and after 15 min of capture, select other machine that **isn't works** and capture the network again for 15 min) check the link below for more information:::  [http://wiki.wireshark.org/FrontPage](http://wiki.wireshark.org/FrontPage)

**Third**: After capture save the two files on your machine and I am pretty sure that you can share it as attach here to see whats really happens with your external network.

**At the end**: another problem that may occurs your tcp/ip is routing table seems a little bit strange as for the metric and summarization of mask..(A whole story to explain now!!) Also when you will try to capture your network that isn't works try to load (as you capture) the default website of your modem...

if you haven't patience :) contact directly with your customer services!!! 

::**NOTE**:: I have noticed that you used OpenDNS for what reason?  You must forwarding a whole situation with port to ip address if your connect with some kind of opendns, dyndns etc!!!  Let us know more information about that!!! 

Good luck!!

---

### Post by BlackLight01 on 2012-06-12
I already know Wireshark, and quite well, I've already used it for  providing the packets dump in the first message, when I've noticed the  weird TCP retransmissions :P anyway, in attachment you can find the dumps for both the cases, when things fail (on eth0, the interface connected to my router) and when things go the right way (on ppp0, the interface for my internet key).

With regard to my routing table, what's wrong with it? Don't worry, I'm not a complete outsider when it comes to networking XD

With regard to OpenDNS, I set it as DNS in resolv.conf (208.67.222.222) long ago because my ISP's default DNS was unable to resolve some hostnames properly. Since that problem is gone now, I can safely use again 192.168.1.1 I guess.

Thanks again,
Fabio

---

### Post by poolet on 2012-06-12
[LEFT]Thats really problem.. Let us know something.. Did you even try to bypassing your router??? If yes you have serious problem with router seems that your problem starts from cdp checking sum.. Even if you are use your vodafone services and you have try to change mac address of interface for some reason or you have try to bypassing your router with any malicious way, probably you fail checksum of your IPS, more specific the ICMPv4, that is a part of IPS... forwarding an IP datagram first decrements the time to live  field in the IP header by one. if the results of TTL is 0 the packet is discared and an ICMP time to live exceeded in transit message is sent to the datagram's sourece address... Now to be more clear.. Your using vodafone as a part of verification and your internet connection works fine.. After that when you try to connect and forwarding with your OpenDNS, your get a 2 very important errors: 1st cdp.checksum = error ,2nd you get a tcp.analysis.flags = bad TCP and with that the things get serious and you have a dup ACKs... 
[/LEFT]
 
Explanation::: When you try to forwarding DNS there are some basic thoughts that you should need.. 
a. summarization of routing table
b. tcp/ip translations/forward - ports/network
c. OSI model, check the 7 layers to be more easier to get an idea of whats going on with transport layer and network layer, 

Now whats going on with your problem. If you aren't try to bypass your router, and also your didn't set up a custom firmware(strange things happens with your dump files, thats the reason I am refer it), your problem comes from openDNS,  believe me or not, I am not so experience with networks as you may think :/ but I have work with large companies and still until today it was an issue to contact with the ISP to set the proper values to the racks to be able to connect without delay into a part of DNS or VPN tunnel especially that some companies have l2tp that is supported only by NAT-T..... Now back on your problem seems that your network fail tcp/ip by the checksum...1 packet in 1.100 and 1 packet in 32.000 fails the TCP checksum, even on links where link-level CRCs should catch all, but 1 in 4 billion errors. We try to investigate why so much are observed, when link-level CRCs should catch nearly all of them.. We can collect nearly 500.000 packets which failed the TCP or UDP or IP checksum.. After of years analysis we conclude that the checksum will to detect errors for 1 in 16 million to 10 billion packets, another conclusion is that it's difficult to understand the problem that comes from checksum failure.Your dup ACK's comes with that, doesn't make sense, (except if your had already play with your router firmware or computer interfaces) if your problem is fixed with other services. Service to service differ thats I want to conclude!! My opinion?? Contact with your provider, is the best way to fixed your problem, I am really sorry but I don't have time to re-analysis the checksums byte-by-byte..You can try starting with your SSL certification that seems a dump..But it will take a long time to understand whats happening... Another good try that I would suggest to you is to disconnect your modem from your connection (doesn't matter if it's cable or ADSL just shut it down for 30 min) refresh all of your machines, starting with ubuntu (with other words get default settings without openDNS connect) Connect 2 machines **without** **network** with a piece of cable. see if your interfaces responds by ping the 2 machines together.. Continue to connect one machine with your network and use it for half an hour, each hour connect a new machine proper and correct, search on google for more informations.. The same for static IP if your using static IP for some of your machines.. At the end search on google how to forward my network with openDNS or any kind of these dyndns etc.. Find a good tutorial and make sure that you have complete correctly.. After all these if your problem still insist try to contact with your ISP (provider) customer services. Make sure that you will talk with someone from tech support(not telephone or sales department) explain exactly whats going wrong with your ACK's and TCP failure..  They probably fixed your problem faster than me and everyone else here.. 

Good Luck!! :)

---

### Post by BlackLight01 on 2012-06-15
Ok, the problem has been solved in a simple way...after 3 calls to my  ISP, and after speaking to 3 different call center operators, I  requested to speak to a technician. It's been enough to explain him the  situation, for having everything solved within 10 minutes (yes, it was a  problem from their side). Thanks again for the support.

---

### Post by poolet on 2012-06-15
> **BlackLight01 said:**
> Ok, the problem has been solved in a simple way...after 3 calls to my  ISP, and after speaking to 3 different call center operators, I  requested to speak to a technician. It's been enough to explain him the  situation, for having everything solved within 10 minutes (yes, it was a  problem from their side). Thanks again for the support.


Good for you.!! :) I Told you these kind of problem usually comes from
providers, or hardware issues!!

---

