---
title: "Internet too slow on ubuntu and okay on windows"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by nelson.gurgel on 2011-02-19
Hi all, 

I cannot use the internet on ubuntu because it is too slow. Right now, I am using windows as this forum was taking ages to go from one page to the other on ubuntu. New pages sometimes doesnt load and an error message comes up. On windows, it is working fine. I installed ubuntu last December and up to last week it was working perfect fine. FYI, I connect to the internet through a normal DSL connection.

I am also having the impression ubuntu is slow in general.

Can you guys help me? I really like ubuntu but if I dont fix this issue I will have to give it up.

N

---

### Post by slooksterpsv on 2011-02-19
> **nelson.gurgel said:**
> Hi all, 

I cannot use the internet on ubuntu because it is too slow. Right now, I am using windows as this forum was taking ages to go from one page to the other on ubuntu. New pages sometimes doesnt load and an error message comes up. On windows, it is working fine. I installed ubuntu last December and up to last week it was working perfect fine. FYI, I connect to the internet through a normal DSL connection.

I am also having the impression ubuntu is slow in general.

Can you guys help me? I really like ubuntu but if I dont fix this issue I will have to give it up.

N

Ok so I take it your connecting via Ethernet not WiFi? Also after you boot into Ubuntu, if you powercycle your DSL Modem (unplug it and plug it back in (the power cord)) are you able to connect better after that?

If you open Terminal (Applications -> Accessories -> Terminal) and type in:
```

ping www.google.com

```

Are you able to ping google.com? You should get like reply from xx.xxx.xxx.xxx or something like that.

If not, do this in terminal (type in this command):

```

echo "nameserver 8.8.8.8" | gksudo tee -a /etc/resolve.conf

```

Then try the connection again.

---

### Post by matt_symes on 2011-02-19
Hi

> I am also having the impression ubuntu is slow in general.

That's just crazy talk.

For people to help here though they will need more information.

What version of Ubuntu are you using ? What browser ? Have you disabled IPv6 ? 

You stated the response time was fine until last week. What happened last week ? An update ?

You also stated the browser was giving you an error message. What exactly was the error ?

Are you wired or wireless ?

The more information you can provide the better.

Kind regards

---

### Post by trooperchix on 2011-02-20
> **slooksterpsv said:**
> Ok so I take it your connecting via Ethernet not WiFi? Also after you boot into Ubuntu, if you powercycle your DSL Modem (unplug it and plug it back in (the power cord)) are you able to connect better after that?

If you open Terminal (Applications -> Accessories -> Terminal) and type in:
```

ping www.google.com

```

Are you able to ping google.com? You should get like reply from xx.xxx.xxx.xxx or something like that.

If not, do this in terminal (type in this command):

```

echo "nameserver 8.8.8.8" | gksudo tee -a /etc/resolve.conf

```

Then try the connection again.

I am connecting via wifi.  I run Ubuntu Maverick and Firefox.  I pinged as suggested above, and it wouldn't go through.  I did the follow up suggestion which seemed to take care of the pinging Google issue but I'm still slow as all get out.  My windows system is fast, and my ubuntu laptop always made that windows system look like it is sitting in the slow lane.  So, I'm not sure what is happening. Out of the 4 systems I run in my house, 3 are Ubuntu, and all three are experiencing the same issue.  Methinks a possible issue with an update?  Not sure.  Sure would appreciate help to figure this out.  Thanks.

Edit: I myself am not getting any errors from my browser and have no idea what IPv6 is.

---

### Post by slooksterpsv on 2011-02-21
> **trooperchix said:**
> I am connecting via wifi.  I run Ubuntu Maverick and Firefox.  I pinged as suggested above, and it wouldn't go through.  I did the follow up suggestion which seemed to take care of the pinging Google issue but I'm still slow as all get out.  My windows system is fast, and my ubuntu laptop always made that windows system look like it is sitting in the slow lane.  So, I'm not sure what is happening. Out of the 4 systems I run in my house, 3 are Ubuntu, and all three are experiencing the same issue.  Methinks a possible issue with an update?  Not sure.  Sure would appreciate help to figure this out.  Thanks.

Edit: I myself am not getting any errors from my browser and have no idea what IPv6 is.

Ok so it looks like your system isn't getting any DNS information when querying the modem, which means, we're going to have to go specify DNS servers for your Wireless Connection.

IPv6 is what is going to take over IPv4 - IPv4 is what most websites and computers use to connect to the internet - an address... like 123 Fake st. Fake City, FK 00001 - it tells you where to go to get to websites (google.com is connected to an IP address, the part, google.com, is known as a domain name, which is why you need a DNS to translate the name to an ip address - which the IP address for google (varies) and when I ping google.com it gives me the IPv4 IP of: 74.125.224.19 ).

Anyways, lets set your DNS information first - we can use 8.8.8.8 or 8.8.4.4 - google dns servers - or there are others, or you can call your ISP and get the dns information from them. Now click on System -> Preferences -> Network Connections - Click on the Wireless Tab -> Click on your connection then edit.
Now go to the tab that says: IPv4 Settings -> Change the Method from Automatic (DHCP) to Automatic (DHCP) Address Only
Now in the DNS section put in the DNS Address - like 8.8.8.8 or 8.8.4.4 - as a secondary dns put a space I think and type in a second one (if you used 8.8.8.8 then use 8.8.4.4 for the second one).
Then click on Apply...

You're done for the DNS, now for IPv6 just copy and paste the following into a terminal (Applications -> Accessories -> Terminal):

```

echo "#disable ipv6" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.all.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.default.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.lo.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf

```

After you paste that in, press enter, type in your password when it prompts you to, and reboot.

---

### Post by matt_symes on 2011-02-21
Hi

That is a good response from slooksterpsv. Very well written :)

I had the same problem as you in that FireFox was slow to load a web page. (Everything else was fast BTW). I took the steps outlined above and i also disabled IPv6 from within FireFox so that FireFox itself would not wast any time trying IPv6.

Open FireFox and in the address bar type 

```
about:config
```

You will get a message stating something along the lines of 'here be dragons'. That just a warning. Click the 'I'll be careful, I promise' button. In the filter at the top of the web page enter

```
ipv6
```

This will filter to a value network.dns.disableIPv6. Double click on it to change its value to true.

Lastly, close and reopen the browser.

BTW. I recently read the last block of free IP addresses has been allocated to the regionals so we will have to move to IPv6 at some point soon.

Kind regards

---

### Post by gdshukla on 2011-04-15
Hello [slooksterpsv]("http://ubuntuforums.org/member.php?u=38762"),
thanks. I am not very sure, but I guess your solution worked well.
I was getting the speed of hardly upto 10 KiBps but now I am getting a good speed of 100 KIbps.
one reason could be that its deep in the night and I am very sure no body else is using the net.
but still I guess your solution helped.
[B][COLOR=DarkRed]Just one thing I wanted to bring your attention to.
After I pasted the line you supplied, the terminal never returned back and every time I had to press CTRL + C. [/COLOR][/B]
If end justifies the means, I am getting good speed.
thanks
gdshukla

---

