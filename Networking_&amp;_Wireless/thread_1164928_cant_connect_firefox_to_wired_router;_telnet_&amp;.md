---
title: "cant connect firefox to wired router; telnet &amp; ping work"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by schober on 2009-05-20
i'm afraid i too cant connect to my router
i'm new to linux and have just installed hardy heron and firefox 3 0 5
i'm using a us robotics 9003 wired router but without a broad band connection (im using dialup now)
1)  i can telnet 192.168.1.1 and get into the router and execute commands like DATE etc
2)  pinging 192.168.1.1 works
3)  BUT .....if i type 192.168.1.1 in the adress bar of firefox nothing happens (according to hte manual it should connect)

how do i get firefox to connect to the  router? 
presumably if  i had a broadband isp i would not be able to connect to the internet because firefox wouldnt connect to the router? so until this issue is resolved it is pointless paying for a broadband connection?
anyone got any suggestions - is the problem with linux or firefox - what is the solution?

Some results..............
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:00:eb:24  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13017 (12.7 KB)  TX bytes:59039 (57.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2276 (2.2 KB)  TX bytes:2276 (2.2 KB)
===================================

-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by dandnsmith on 2009-05-20
Have you tried:
[http://192.168.1.1](http://192.168.1.1)
-there could be something about the firefox settings (and are you sure that the instructions aren't for Internet explorer?)

---

### Post by pro003 on 2009-05-20
I open my router all the time with firefox and the firefox itself its not a problem, it might be some addon or plugin or some settings that are preventing it from opening the page

you should also try openning this i: ===> [http://192.168.0.1](http://192.168.0.1)

---

### Post by schober on 2009-05-20
thanks for replies dan and pro
tried both suggestions - but to no avail!

---

### Post by superprash2003 on 2009-05-20
check to see if firefox is not in offline mode , file->work offline

---

### Post by schober on 2009-05-20
i've tried both online and offline - neither works!
i've tried using lynx and thaat cant connect to the router

so, presumably its not a specific browser problem but the way in which browsers connect to the network chip on the motherboard???

more results - not sure what they mean or what should be there

-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
==========================================
-desktop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:C0:49:C4:61:B2   C                     eth0

---

### Post by netztier on 2009-05-20
> **schober said:**
> so, presumably its not a specific browser problem but the way in which browsers connect to the network chip on the motherboard???


[SIZE="1"]*"Multiple question marks," he went on, shaking his head, "are a sure sign of a diseased mind."* (slightly misquoted from Terry Pratchett's book "Eric", see [http://www.lspace.org/books/pqf/eric.html](http://www.lspace.org/books/pqf/eric.html)). They don't make questions more important or more interesting.[/SIZE]


Back to the question.


A browser has no clue about network chips, and it doesn't "connect" to them. All a browser (or most other network aware application) cares about is getting what is called a "socket", which it requests from the operating system's network stack: "can I please have a TCP (or UDP or ICMP) connection to port XYZ of IP address abc.def.geh.ijk?" 

In your case, the tcp port will be **80** (since 80 is default for http connections) and the IP address will be **192.168.1.1**.

The network stack will then determine which IP interface to use (by looking up the routing table) for that outgoing connection and will then hand down the IP packet to that interface (e.g. eth0). Beneath that interface will be an ethernet/token ring/serial line/FDDI/Infiniband/Myrinet kernel module (whichever network technology is being used), which in turn will know how to talk to the chips and make them send out the stream of digital signals onto the wire or the antenna.

In short: Applications per se are blind to what's going on at the lower network layers, they should only ever talk to the next lower or upper one - so they don't need to be aware of the "chips" in any way.

If you do a telnet, the telnet program does exactly the same thing, but by default, it wants to connect to port 23, not 80. But telnet can be made to connect to other ports than 23: Try a telnet to port 80 of the router's IP address. You should be seeing something like this:

```
user@host:~$ **telnet 192.168.1.1 80**
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'

```

(and nothing more). Now you know that your computer can talk to the router on port TCP/80. Hit <enter> a few times, and you'll probably get a "Connection closed by remote host". If this succeeds, the problem is very probably with the browser(s).

If you get a "Connection refused" or "Connection reset by peer", then the router's IP stack is sending back a TCP RST message meaning: "yeah right, I saw your connection request on port 80, but I don't want to talk to you" (unfortunately not being any clearer than this). Typically, TCP RSTs are sent when there is not service "listening" on a TCP port. In that case, you might want to consult your router's documentation to see how to verify if the built-in web server is enabled and if not, how to enable it.

If however you get an instant "permission denied", then probably there's a firewall running on your computer

To sum it up: I suspect two possible reasons for the problem

[LIST]
[*]built-in web server on the router does not run or is (mis)configured (e.g. it will only accept connections from 192.168.1.2, but not .3)
[*]a firewall on the computer prevents outgoing connections to 192.168.1.1:80
[/LIST]


regards

Marc

---

### Post by schober on 2009-05-21
thanks for your comments netztier
1)   telnet 192.168.1.1 and  telnet 192.168.1.1  23 both have the same effect ie ican log into the router
 2)    telnet 192.168.1.1 80 gives the result

[I]user@host:~$ **telnet 192.168.1.1 80**
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'[/I]

exactly as you described - however, repeated pressing of "enter" had no effect apart from sending the cursor down the screen ie i got a series of newlines.

3)  i did reset the router (poke awire down the little hole at the back wtih the router switched on) a week ago - so it should have the factory defaults?

4)  when you refer to a "built in webserver" do you mean the DHCP server? - its the only reference to a server i can find inthe CLI sectionof the user guide.

5)  no firewall is installed on the computer

cheers mike

---

### Post by netztier on 2009-05-21
> **schober said:**
> repeated pressing of "enter" had no effect apart from sending the cursor down the screen ie i got a series of newlines.


Should not be of any meaning - it depends on the behaviour of the server program. The two or three routers/hosts I tested against all "threw me out" after two or three <enter>s

> 
3)  i did reset the router (poke awire down the little hole at the back wtih the router switched on) a week ago - so it should have the factory defaults?


That commonly is case - and I would expect that this turns on the built-in web server as well.

> 
4)  when you refer to a "built in webserver" do you mean the DHCP server? - its the only reference to a server i can find in the CLI sectionof the user guide.


Well, if the router has a web based access to it's configuration, there has to be a program running on the router that delivers HTML (Web pages) to an incoming connection (on port 80). In general, programs doing this are called *web servers*. In a nutshell, the well known Apache, lighttpd and Microsoft's IIS do the same thing: run as programs on small or large computers, delivering web content to incoming connections that request the web content.

So if your router has a mini configuration web site, it will have a mini web server program running - that's what I'm referring to. Just like it has a program running that gives out adresses to client computers (using the DHC protol): the DHCP server.


> 
5)  no firewall is installed on the computer


I would assume so - it very probably would've prevented the telnet to port 80 as well. 

Hm. Lets play some more with that web server (or whatever is accepting our connection on port 80). Re-do the telnet 192.168.1.1 80, but this time, try this

```
user@host:~$ **telnet 192.168.1.1 80**
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
[COLOR="Red"]**GET index.html**[/COLOR]
HTTP/0.0 400 Bad Request
SERVER: <some information about the web server program>
CONTENT-LENGTH: 50
CONTENT-TYPE: text/html; charset=UTF-8

<html><body><h1>400 Bad Request</h1></body></html>Connection closed by foreign host.
```

Actually type in **GET index.html** (you might have to type it blindly, it is possible that the typed-in characters are not echoed). At least, we should be getting back some *<html>...</html>* stuff, even if it contains nothing but an error message.

In the user guide, see if there is some option about "HTTP configuration" (which would refer to the built-in web server) and what can be done do activate it. 

While you're at it, also check if there is some restricion on who (read: which IP addresses) is allowed to access the HTTP configuration pages. 
Some vendors at some point in time came up with funny ideas: only the first address given out from the DHCP pool is allowed to connect. Seeing that 192.168.1**.1** is the router's address, and your system has the **.3** address, there is possibly some system around using the **.2** - which incidentally probably is the "first" address from the pool.

Coming to think of it... the other thing might be... hm.

[INDENT][SIZE="1"]Say, does that router box also have an integrated wireless access point? 

Most wireless router models keep their wired and wireless clients in the same subnet and their built-in DHCP servers give them addresses from the same pool/range. Yet, the box disallows access to it's configuration web pages from the wireless part of the network. This is not the worst of ideas, since it prevents your neighbor's kids from reconfiguring your wireless router every sunday morning over the air, if you neglected to implement proper wireless security.

Is that Ubuntu system connected via wireless? If yes, temporarily use a cable and plug it directly to the router...

Hm.. **no**. You already said it was **eth0** being used to connect to that subnet - that's very probably a wired connection.
[/SIZE][/INDENT]

*scratches head* let's first see if you get something back from *GET index.html*.

regards

Marc

---

### Post by schober on 2009-05-21
thanks for suggestion marc
1)  i tried 

[I]user@host:~$ **telnet 192.168.1.1 80**
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
[COLOR=Red]**GET index.html**[/COLOR][/I]

it typed in fine (echoed to screen) but nothing happened!

2)  there is no wireless capability on the router or computer

3)  only one computer is connected to the router; the router is not connected to the phone line.
 4) i telneted int o the router and tried this - not sure what it tells me though

[I][root @ home]$ ifconfig -o eth0
eth0: flags=a863<UP,BROADCAST,b6,RUNNING,SIMPLEX,LINK1,MULTICAST> mtu 1500
    inet 192.168.1.1 netmask 0xffffff00 broadcast 192.168.1.255
    ether 00:c0:49:c4:61:b2 [/I] 

 5)  i cant find any reference to http configuaration, mini web server  or any thing similar - perhaps there isnt one? 
the manual says

[I]Accessing the Web User Interface
Your router includes the SureConnect ADSL Web Utility. This Web utility displays after you
complete installation.
To access the Web User Interface, follow these steps...
  1. Install your router according to the Quick Installation Guide.
  2. Connect the router to the Ethernet or USB port on your PC.
  3. Open a Web browser and go to IP address [http://192.168.1.1](http://192.168.1.1). (Otherwise, go to the
      LAN IP designated for the router's management port.)
  4. At the prompt, type in your user name and password. The default user name is "root."
      The default password is "12345." (Don't type the quotation marks or period.)[/I]

could it be that the software provided on the installationcd (which i dont have) translates the info from a web page generated by the computer into telnet commands?

cheers mike

---

### Post by schober on 2009-05-23
well, tried using tcpdump

**successful telnet**

mike@mike-desktop:~$ sudo tcpdump -nn host 192.168.1.1 and port 23
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
09:21:14.154303 IP 192.168.1.3.40602 > 192.168.1.1.23: S 133172743:133172743(0) win 5840 <mss 1460,sackOK,timestamp 1584888 0,nop,wscale 6>
09:21:14.157148 IP 192.168.1.1.23 > 192.168.1.3.40602: S 299188166:299188166(0) ack 133172744 win 17376 <mss 1460,nop,wscale 0,nop,nop,timestamp 4787 1584888>
09:21:14.157219 IP 192.168.1.3.40602 > 192.168.1.1.23: . ack 1 win 92 <nop,nop,timestamp 1584889 4787>
09:21:14.158491 IP 192.168.1.3.40602 > 192.168.1.1.23: P 1:28(27) ack 1 win 92 <nop,nop,timestamp 1584889 4787>
09:21:14.158965 IP 192.168.1.1.23 > 192.168.1.3.40602: P 1:8(7) ack 1 win 17376 <nop,nop,timestamp 4787 1584889>
09:21:14.159005 IP 192.168.1.3.40602 > 192.168.1.1.23: . ack 8 win 92 <nop,nop,timestamp 1584889 4787>
09:21:14.161063 IP 192.168.1.1.23 > 192.168.1.3.40602: P 8:11(3) ack 28 win 17349 <nop,nop,timestamp 4787 1584889>
09:21:14.161126 IP 192.168.1.3.40602 > 192.168.1.1.23: . ack 11 win 92 <nop,nop,timestamp 1584890 4787>
09:21:14.161307 IP 192.168.1.3.40602 > 192.168.1.1.23: P 28:31(3) ack 11 win 92 <nop,nop,timestamp 1584890 4787>
09:21:14.163170 IP 192.168.1.1.23 > 192.168.1.3.40602: P 11:14(3) ack 31 win 17346 <nop,nop,timestamp 4787 1584890>
09:21:14.203133 IP 192.168.1.3.40602 > 192.168.1.1.23: . ack 14 win 92 <nop,nop,timestamp 1584901 4787>
09:21:14.204665 IP 192.168.1.1.23 > 192.168.1.3.40602: P 14:38(24) ack 31 win 17376 <nop,nop,timestamp 4787 1584901

**failed http**
mike@mike-desktop:~$ sudo tcpdump -nn host 192.168.1.1 and port 80
[sudo] password for mike: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
09:35:10.714678 IP 192.168.1.3.47968 > 192.168.1.1.80: S 358910494:358910494(0) win 5840 <mss 1460,sackOK,timestamp 1794028 0,nop,wscale 6>
09:35:10.717841 IP 192.168.1.1.80 > 192.168.1.3.47968: S 403097030:403097030(0) ack 358910495 win 17376 <mss 1460,nop,wscale 0,nop,nop,timestamp 6450 1794028>
09:35:10.717920 IP 192.168.1.3.47968 > 192.168.1.1.80: . ack 1 win 92 <nop,nop,timestamp 1794029 6450>
09:35:10.718259 IP 192.168.1.3.47968 > 192.168.1.1.80: P 1:380(379) ack 1 win 92 <nop,nop,timestamp 1794029 6450>
.
.  keeps resending hte 92 byte sized packet until terminated by firefox ie me
.

09:36:02.735144 IP 192.168.1.3.47968 > 192.168.1.1.80: P 1:380(379) ack 1 win 92 <nop,nop,timestamp 1807034 6450>
09:36:10.735038 IP 192.168.1.3.47968 > 192.168.1.1.80: F 380:380(0) ack 1 win 92 <nop,nop,timestamp 1809033 6450>
09:36:10.736508 IP 192.168.1.1.80 > 192.168.1.3.47968: . ack 381 win 17376 <nop,nop,timestamp 6569 1794029>

**Conclusion** 
1) 3 way handshake works on http
2) router fails to respond to info pushed to it by firefox - so, its the wrong info in the packet or the router cant act on the info recieved

Where do i go from here - any suggestions?
cheers mike

---

### Post by schober on 2009-05-31
stillno joy!

1) i can ping  192.168.1.1

2) i can  telnet 192.168.1.1
[COLOR=Blue]mike@mike-desktop:~$  telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
login: root
Password: 
[root @ home]$ exit[/COLOR]

3)  and execute CLI things like date, version 
[COLOR=Blue][root @ home]$ version
AD6489  Security Gateway Software20030403 43E2EA8A AnnexA[/COLOR]

4) i can reach the ftp server
[COLOR=Blue]desktop:~$ ftp 192.168.1.1
Connected to 192.168.1.1.
220 Welcome to U.S.Robotics SureConnect ADSL Ethernet/USB Router update FTP server v1.0.
Name (192.168.1.1:mike): mike@mike-desktop:~$ [/COLOR]

5) with  192.168.1.1 in the adress bar of firefox, i am unable to connect with the router in order to use the wui interface - the browser cant connect to the router ([http://192.168.1.1](http://192.168.1.1) doesnt work either)

6) from wireshark i get ...................

[COLOR=Blue]3    10.877803    192.168.1.3    192.168.1.1    TCP    53346 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=2989327 TSER=0 WS=6

4    10.881133    192.168.1.1    192.168.1.3    TCP    http > 53346 [SYN, ACK] Seq=0 Ack=1 Win=17376 Len=0 MSS=1460 WS=0 TSV=1048 TSER=2989327

5    10.881240    192.168.1.3    192.168.1.1    TCP    53346 > http [ACK] Seq=1 Ack=1 Win=5888 Len=0 TSV=2989328 TSER=1048

6    10.881378    192.168.1.3    192.168.1.1    HTTP    GET / HTTP/1.1 
[/COLOR]
line 6 is then repeated indefinatly

line 6 decoded contains

[COLOR=Blue]   ..I.a... ...$..E.
   ..=|@.@. xv......
  ...b.P.. .v..!...
   .\...... ...-....
   ..GET /  HTTP/1.1  ..Host:  192.168.1.1..User-Agent: Mozilla /5.0 (X11; U; Linux i686 ; en-GB;  rv:1.9. 0.10) Gecko/2009 042513 Ubuntu/8. 04 (hard y) Firefox/3.0.1 0..

Accept: text/ html,application /xhtml+x ml,application/x ml;q=0.9 ,*/*;q=0 .8..
Acce pt-Language: en- gb,en;q= 0.5.
.Acc ept-Encoding: gz ip,deflate.
.Accept-Charset: ISO- 8859-1,u  tf-8;q=0 .7,*;q=0 .7..
Keep -Alive:  300..
Connection:       keep-alive.... [/COLOR]

Conclusions
0) computer can communicate with router through port 80 (as shown by lines 3 4 5)
either 1) the request in line6 has an error
or 2) the router has no web server or it has a fault
or 3) the web server in the router has been disabled ( the manual has no mentionof this!)

Anyone care to comment?


[SIZE=1][COLOR=Blue]
[/COLOR][/SIZE]

---

### Post by Samwise Hamfast on 2009-06-01
I seem to have the same problem as many others with 9.04 - there are quite a few posts about Firefox not getting any HTML although the wireless connection is present. I'm writing this on a(nother) machine that is running 8.10 (upgraded from 8.04). I can't do clever things like telnet and ping (I can't even get a smilie into this message!) but I can look at the Error thingy in Firefox and this is what it says:

Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIChannel.contentType]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: file:///usr/lib/xulrunner-1.9.0.8/components/FeedProcessor.js :: FP_onStartRequest :: line 1440"  data: no]
Source File: file:///usr/lib/xulrunner-1.9.0.8/components/FeedProcessor.js
Line: 1440

So I'd put a confused smilie here if I could and also one that showed frustration.

Can anyone translate the above message please? I'd be grateful for any suggestions as to how to get the (other) machine to work - perhaps I should install 8.04?

Hope someone can help,

Samwise Hamfast

---

### Post by netztier on 2009-06-02
> **schober said:**
> 

Anyone care to comment?

Strange.

We see a HTTP request ("GET /") going to the router. But there is no return code ("200 OK") nor some of the 4xx or 5xx return codes from the web server that would indicate a problem or an error. It just gives back no answer at all - bar the TCP handshake, of course.

My impression: web server function of that router is b0rken. If this was about any incompatibilities between Firefox and the content (some weird java script stuff, like some Linksys Devices have that makes them only Internet Explorer compatible), that would come later, *after* the web server would've started to deliver some content back to the browser, but it doesn't even do that.

Possibly, the web service gets confused by the information FF sends along when submitting the request to identify itself and what kind of information it accepts.

Two ways to do a browserless blank test:

[LIST]
[*]install (well, if you can, of course...) **wget** and run ```
wget http://192.168.1.1/
```
If I do this against one of my linksys switches, the output looks as follows. Interestingly, wget instantly gets redirected (Code 302) to another URL and then downloads what comes from there.
```
user@host:/tmp$ **wget http://172.20.125.5/**
--2009-06-02 17:34:40--  http://172.20.125.5/
Connecting to 172.20.125.5:80... connected.
HTTP request sent, awaiting response... [COLOR="Red"]302 Redirect[/COLOR]
Location: [COLOR="DarkRed"]http://172.20.125.5/config/log_off_page.htm[/COLOR] [following]
--2009-06-02 17:34:40--  http://172.20.125.5/config/log_off_page.htm
Connecting to 172.20.125.5:80... connected.
HTTP request sent, awaiting response... [COLOR="SeaGreen"]200 OK[/COLOR]
Length: unspecified [text/html]
Saving to: `log_off_page.htm'

  [<=>] 5,219       --.-K/s   in 0.05s  2009-06-02 17:34:40 (110 KB/s) - 

`log_off_page.htm' saved [5219]

```
[*]Retry the telnet test I suggested already, but this time, issue the HTTP command as **GET /** instead of the GET index.html I suggested earlier, that was a stupid suggestion by me, because it is bound to fail. Like this, you don't submit any information whatsoever to the server, and it has to default to something and hopefully deliver something back.
[/LIST]

best regards

Marc

---

### Post by schober on 2009-06-02
thanks for the suggsetions marc; unfortunaltely to no avail!

[COLOR=RoyalBlue]mike@mike-desktop:~$ wget [http://192.168.1.1/](http://192.168.1.1/)
--21:38:11--  [http://192.168.1.1/](http://192.168.1.1/)
           => `index.html'
Connecting to 192.168.1.1:80... connected.
HTTP request sent, awaiting response... [/COLOR]

resulted in a long wait while nothing happenend

[COLOR=RoyalBlue]mike@mike-desktop:~$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
login: root
Password: 
[root @ home]$ get/
Command not found.
[root @ home]$ [/COLOR]

this was unsurprising as GET is not a command listed by the router
cheers mike

---

### Post by netztier on 2009-06-03
> **schober said:**
> 
[COLOR=RoyalBlue]mike@mike-desktop:~$ wget [http://192.168.1.1/](http://192.168.1.1/)
--21:38:11--  [http://192.168.1.1/](http://192.168.1.1/)
           => `index.html'
Connecting to 192.168.1.1:80... connected.
HTTP request sent, awaiting response... [/COLOR]


Hm. Well, the webserver in that router must be b0rken, halfway deactivated or something. 

> 
[COLOR=RoyalBlue]mike@mike-desktop:~$ telnet 192.168.1.1
[/COLOR]

this was unsurprising as GET is not a command listed by the router


Er, the telnet should've gone to port 80, of course. The shell won't understand the GET command, but the HTTP server should. Looking at the result of the wget test above, I very much doubt that you'd be seeing any response at all.

regards

Marc

---

