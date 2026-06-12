---
title: "Cannot connect to adobe.com"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Paqman on 2009-07-05
None of the machines on my network can connect to [www.adobe.com](www.adobe.com), and my ISP is being pretty unhelpful.

The problem has been ongoing for several weeks, and is identical on Ubuntu/Windows and in different browsers. I'm guessing this is some kind of DNS weirdness, but my ISP hasn't responded to my requests for help. I don't know squat about this kind of thing, can somebody help me out with troubleshooting my connection?

---

### Post by computer13137 on 2009-07-05
My guess would be that you are using your router's DNS server, which is something I never recommend because it has more problems than anything else.  I would try to change your DNS server on the computers individually to something else.  I've always been a fan of the (4.2.2.1) DNS server, as well as OpenDNS's free DNS on 208.67.220.220.

So, here's how to change your DNS server.

1) Open /etc/dhcp3/dhclient.conf in your favorite text editor. (This must be done as root).
2) Use your text editor's "find" feature to get to the line starting with the word "prepend".
3) Remove the # sign that makes it a comment.
4) Change the numbers that are there (it probably says 127.0.0.1) to your DNS server of choice... I'm going to recommend 208.67.220.220.
5) Save the file.
6) Restart networking.  /etc/init.d/networking restart (This must be done as root).

If it still doesn't seem to help, try rebooting your machine before you ask us here again.

If you have further questions, I'll stay subscribed to this thread.  Oddly, this is the second time in 2 days I've replied to this almost identical problem.

Cheers,
Kirk

---

### Post by prshah on 2009-07-05
> **Paqman said:**
> I'm guessing this is some kind of DNS weirdness,

While the above suggestion is not without merit, it will involve changing the dhclient.conf file on every computer. 

If that is not convenient, it may help to change the DNS settings on the router itself: see [Use OpenDNS (Step 1 of 3: Change DNS settings)]("https://www.opendns.com/start/router/") for step-by-step guides.

Alternatively, you can just edit your /etc/hosts file (on each machine), and add a line to it```

192.150.18.60  www.adobe.com
``` which is the IP address for adobe, as resolved by OpenDNS.

Or you can simply use the above IP address instead of [www.adobe.com](www.adobe.com).

If none of these work, then the problem is probably not DNS.

---

### Post by Paqman on 2009-07-06
No joy from any of those suggestions guys. What on earth could this be?

---

### Post by superprash2003 on 2009-07-06
what happens when you try directly typing 192.150.18.60 in the browser as told by prshah , what error do you face?

---

### Post by prshah on 2009-07-06
> **Paqman said:**
> No joy from any of those suggestions

In that case, I doubt it's a DNS issue. Can you give the following terminal commands and post back the output?```

nslookup www.adobe.com
tracepath www.adobe.com

```

---

### Post by jonobr on 2009-07-06
Also, if you dont mind sharing it,

if you could upload the file created by doing a packet trace 

```
sudo tcpdump -w trace1.pcap -s 1600 -i any port 80
```
The navigate to the page.
Try that and then go to another page and then back to adobe.

Control c the tcpdump and post the trace1.pcap file generated

---

### Post by Paqman on 2009-07-07
> **superprash2003 said:**
> what happens when you try directly typing 192.150.18.60 in the browser as told by prshah , what error do you face?

The browser times out, Firefox's error page is: "Network timeout, The operation timed out when attempting to contact 192.150.18.60."

> **prshah said:**
> In that case, I doubt it's a DNS issue. Can you give the following terminal commands and post back the output?```

nslookup www.adobe.com
tracepath www.adobe.com

```

```

nslookup www.adobe.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	www.adobe.com
Address: 192.150.18.60

```

```

tracepath www.adobe.com
 1:  jaunty-desktop.local (192.168.1.2)                     0.105ms pmtu 1500
 1:  voyager.home (192.168.1.1)                             3.193ms 
 1:  voyager.home (192.168.1.1)                             1.583ms 
 2:  voyager.home (192.168.1.1)                             1.686ms pmtu 1400
 2:  lo99.lon-z-ips.as9105.net (212.74.111.187)            58.567ms 
 3:  ge1-0-7.lon11.as9105.net (80.40.119.162)              66.150ms asymm  4 
 4:  xe-3-1-0-10.lon10.ip.tiscali.net (213.200.79.9)       59.612ms asymm  5 
 5:  so-3-3-0.was11.ip4.tinet.net (89.149.187.138)        140.314ms asymm  6 
 6:  xe-0.equinix.asbnva01.us.bb.gin.ntt.net (206.223.115.12) 139.088ms asymm  7 
 7:  as-3.r20.snjsca04.us.bb.gin.ntt.net (129.250.2.167)  202.921ms asymm 11 
 8:  no reply
 9:  te-5-3.r02.snjsca04.us.ce.gin.ntt.net (128.241.219.86) 200.213ms asymm 11 
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1400
     Resume: pmtu 1400 

```

I'd actually finally got a reply from my ISP and they had me do nslookup (among other things) on a Windows machine, which seemed to hit adobe.com with no errors, so at least this is progress.

> **jonobr said:**
> Also, if you dont mind sharing it,

if you could upload the file created by doing a packet trace 

```
sudo tcpdump -w trace1.pcap -s 1600 -i any port 80
```
The navigate to the page.
Try that and then go to another page and then back to adobe.

Control c the tcpdump and post the trace1.pcap file generated

I don't mind sharing it, if you can quickly explain why I might not want to. I'm not worried too much about privacy if it means it'll stop you guys helping, but i'm obviously not going to post anything that's a security risk.

As you can tell, my entire knowledge of networking would probably fill a thimble. I really should get off my butt and learn how this stuff works, it's pretty crucial in a networked world.

---

### Post by Crafty Kisses on 2009-07-07
Have you checked to see if ECN is on? You can do this by running:
```
cat /proc/sys/net/ipv4/tcp_ecn
```
If that returns the number one, then you need to shut it off, you can do this by running the following:
```
echo 0 > /proc/sys/net/ipv4/tcp_ecn
```
Once you have done this, try and visit Adobe's website again. See if you have any luck.

---

### Post by prshah on 2009-07-07
> **Paqman said:**
> The browser times out, Firefox's error page is: "Network timeout, The operation timed out when attempting to contact 192.150.18.60."
```

tracepath www.adobe.com
 1:  jaunty-desktop.local (192.168.1.2)                     0.105ms pmtu 1500
 1:  voyager.home (192.168.1.1)                             3.193ms 
 1:  voyager.home (192.168.1.1)                             1.583ms 
 2:  voyager.home (192.168.1.1)                             1.686ms pmtu 1400
 2:  lo99.lon-z-ips.as9105.net (212.74.111.187)            58.567ms 
 3:  ge1-0-7.lon11.as9105.net (80.40.119.162)              66.150ms asymm  4 
 4:  xe-3-1-0-10.lon10.ip.tiscali.net (213.200.79.9)       59.612ms asymm  5 
 5:  so-3-3-0.was11.ip4.tinet.net (89.149.187.138)        140.314ms asymm  6 
 6:  xe-0.equinix.asbnva01.us.bb.gin.ntt.net (206.223.115.12) 139.088ms asymm  7 
 7:  as-3.r20.snjsca04.us.bb.gin.ntt.net (129.250.2.167)  202.921ms asymm 11 
 8:  no reply
 9:  te-5-3.r02.snjsca04.us.ce.gin.ntt.net (128.241.219.86) 200.213ms asymm 11 
10:  no reply
11:  no reply
*<snip>*
31:  no reply
     Too many hops: pmtu 1400
     Resume: pmtu 1400 

```



See [ Re: Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution. 

Basically, it involved changing the MTU on the router, to 1492 (or something below 1500). The MTU change will not affect Windows machines. 

I suspect this because of a similar traceroute in the above linked thread.

I suggest you can go through the entire thread (2 pages) for a quick picture, or just apply MTU change (as per the linked post) and check.

it is DEFINITELY NOT a DNS issue.

---

### Post by Paqman on 2009-07-07
> **Codename said:**
> Have you checked to see if ECN is on?

I have now, it's not.

> **prshah said:**
> See [ Re: Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution. 

Basically, it involved changing the MTU on the router, to 1492 (or something below 1500). The MTU change will not affect Windows machines. 

I suspect this because of a similar traceroute in the above linked thread.

I suggest you can go through the entire thread (2 pages) for a quick picture, or just apply MTU change (as per the linked post) and check.

it is DEFINITELY NOT a DNS issue.

His failure mode was different to mine, he was having trouble with lots of websites randomly, i'm having consistent trouble with the same one (although there's likely more...)

However I did try changing the MTU just in case, no result.

---

### Post by jonobr on 2009-07-07
Hello


Your skeptism is to be commended.

Anyway.  info below, but a comment first.

Could you try putting 192.150.18.117 into your browser and see what happens

And more info

*********


You should be watchful about posting anything and running commands.

What this command does is it invokes tcpdump.

This is a utility which does packet snipping and is controlled by the options you place after it.

-w trace.pcap generates a file that can be read in a program called wireshark.

-s 1600 changes the defaul packet capture size to 1600 and does not truncate the packets your capturing.

-i any says trace on any interface thats on the machine

port 80 means just look at web traffic.

The information that will be in the tcpdump will show the packets and responses.
The information in your tracepath actually shows (at a high level) a lot of the ip information that will show up in this packet trace.

You could open the file in wireshark and see whats captured before posting, and if your still not happy, thats ok.

---

### Post by Paqman on 2009-07-10
Ok, [here's]("http://www.andyduffell.com/trace1.pcap") the trace file.

---

### Post by jonobr on 2009-07-10
Thansk a mill for your traces, it was very useful

Im inserting a graphic of what you sent me.

ON the top is my trace to adobe.com and on the bottom is yours.

On yours you can see in the filter bar, I have filtered out http as thats all I need to see.

With that done, I have a good comparison.

In mine I have also blackened out my source IP, I hope thats ok.

You will see from the left hand side in columns and to explain what you are seeing, 

No= packet number
Time= timestamp packet was received
Source= where the packet was from
Destination = where its going to
Protocol= In this case I filtered http only
Info= High level info on the packet


On the top you can see I got to adobe.com marked 1 (sorry for the bad drawing IM terrible with Gimp) The dotted line shows where this is going.
This is my machine going to the ip address (adobe) and doing http get, I.e. send me the webpage


Then (marked 2) I get a response from the website saying permanently moved.
This tells my browser, this has moved to another place and will supply the new IP address in that same packet.


Marked 3 and dotted is the new IP address (which is where it was moved to).
You can see its the same get command, just to the new IP address.

On your trace,
you can see the same request from the IP address.
Next you see my question mark where your not sent a permanently moved, your sent a 302 found and then you continue on your own way passing traffic
which is obviously not working.

This kinda tells me a few things and makes me wonder also

1- Its definitely not anything to do with DNS
2 - The adobe website is responding differently to your browser then it is to mine. Im using seamonkey. You know the way websites know when your using firefox and say we dont support your browser, I think this is doing the same but screwing it up
3- if you do w3m adobe.com on a terminal window I get the feeling you will see the adobe web page.
4- Could you install seamonkey and try with that?
5- Could you try 

Thanks

Jonobr

---

### Post by Paqman on 2009-07-11
> **jonobr said:**
> 
1- Its definitely not anything to do with DNS


From what others have said, I agree. I'm looking suspiciously at my router, or maybe my ISP.

> 
2 - The adobe website is responding differently to your browser then it is to mine. Im using seamonkey. You know the way websites know when your using firefox and say we dont support your browser, I think this is doing the same but screwing it up


I've already got the same result in two copies of Linux Firefox across two different versions, Windows Firefox and IE, so I don't think it's browser-specific.

> 
3- if you do w3m adobe.com on a terminal window I get the feeling you will see the adobe web page.


Sadly not. It just times out as well.

> 
4- Could you install seamonkey and try with that?


Done, no result.

> 
5- Could you try 


???

---

### Post by jonobr on 2009-07-11
You failed in point number 5, 
that was  mind reading test.......


I find the most interesting results to be w3m and the test with seamonkey.

They work in my scenario.

Are there any updates outstanding specifically for web stuff or the tcp/ip stack?

Im think you have a very unique problem there

---

### Post by Paqman on 2009-07-12
> **jonobr said:**
> 
Are there any updates outstanding specifically for web stuff or the tcp/ip stack?


Nope, and remember the problem is identical across a Jaunty machine, an Intrepid one, Vista and XP. This isn't anything to do with the OS.

---

### Post by jonobr on 2009-07-12
Ok, heres the only thing I can suggest 

you need to take a machine where it does not work and move it to a completely seperate network and verify that there is something in your network not working.

If this is OS independent and  multi browser for you, then I think adobe would know about this issue, so again , move to a seperate network if you can (i.e. laptop to a free wifi spot)

---

### Post by chiqafj2 on 2011-01-15
> **Paqman said:**
>  Originally Posted by **Codename** [](showthread.php?p=7574734#post7574734" rel=nofollow) Have you checked to see if ECN is on?  I have now, it's not. Originally Posted by **prshah** [](showthread.php?p=7574855#post7574855" rel=nofollow) See [Re: Firefox/Epiphany/Lynx not loading certain websites](http://ubuntuforums.org/showpost.php?p=4514356&postcount=12) for a possible solution. Basically, it involved changing the MTU on the router, to 1492 (or something below 1500). The MTU [[COLOR=#000000]change[/COLOR]](http://www.changeformat.net/change-divx-format/change-divx-to-iriver-b20.html) will not affect Windows machines. I suspect this because of a similar traceroute in the above linked thread.I suggest you can go through the entire thread (2 pages) for a quick picture, or just apply MTU change (as per the linked post) and check.it is DEFINITELY NOT a DNS issue.  His failure mode was different to mine, he was having trouble with lots of websites randomly, i'm having consistent trouble with the same one (although there's likely more...)However I did try changing the MTU just in case, no result.I've got the same problem, Is there an rignt answer for the problem?

---

