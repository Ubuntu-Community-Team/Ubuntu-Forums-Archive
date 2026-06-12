---
title: "Please help! Wifi doesn't work in Oaxaca, Mexico"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by potion on 2013-06-10
Hi, I'm in Oaxaca, Mexico, for a month, and I can't connect to any wireless networks here. I've tried connecting to three different routers, and the same thing always happens... I can see the network, and when I try to connect it asks for a password, which I give. Then it shows that I'm connected, but neither Firefox nor Chrome can find a server, and eventually it times out. Other people are able to connect to all of these networks.

My wifi was working before I arrived here. Unfortunately, I don't have access to any of the routers as they're at cafes offering free wifi. I don't know if this will help any, but it seems like most places here connect through the same ISP. When I look at available networks, they almost all say Infinitum, and I believe the ISP is Telmex. I've tried searching, and it seems like other Ubuntu users have had trouble connecting to Infinitum/Telmex, but I haven't found any solutions anywhere.

I can post any specific info from iwconfig, ifconfig and the like, but I can't easily copy and paste, since I can only get online using other computers, not my Ubuntu laptop.

Thanks for any help you can give!

---

### Post by chili555 on 2013-06-10
This is kind of a stab in the dark. Please run:```
iw reg get
```I am assuming the country code is either blank or something other than MX for Mexico. If so, try setting it to Mexico:```
sudo iw reg set MX
```Now does it connect?

---

### Post by potion on 2013-06-10
Hi chili555, thank you for replying! I've just run the commands. At first the country code showed as 00, and now it's MX. The number ranges have changed as well. I'll try to connect and report back. (I can only get online at an Internet cafe that's a couple blocks away from the nearest wifi...) Thanks very much for your help! I'll be back on shortly to post if it worked or not.

---

### Post by potion on 2013-06-10
No luck, I'm afraid. I turned off my laptop to walk over to the place with wifi, and when I turned it back on, the region had reset to US. I changed it back to MX (although it looks like the US setting has all the ranges of the MX setting plus a couple more), but either way it did the same thing... Said I was connected but then Firefox couldn't find a server. I tried pinging [www.google.com](www.google.com) from the terminal and that didn't work either.

Anything else I could try? Thanks again for your help, chili555!

---

### Post by chili555 on 2013-06-10
> when I turned it back on, the region had reset to US. Until we make some permanent changes, it will revert. There is no need, yet, to make a change until we know it helps.>  I tried pinging [www.google.com](www.google.com) from the terminal and that didn't work either.Didn't work meaning what? It just hung there, or it came back to 'ping: unknown host'? There is a difference and the results suggest different problems.

Does it ping by number, suggesting a DNS nameserver problem?```
ping -c3 8.8.8.8
```I wonder if it's a captive portal, the system where you log on and agree to terms and conditions before you can get to the internet. It forces you to agree to a set of terms and conditions by automatically redirecting you to a site discussing them and not allowing any other connections until you agree. These are sometimes a bit tricky with Firefox and Ubuntu.

Please run:```
nm-tool
```Can you ping the gateway?```
ping -c3 10.0.0.1  [COLOR="#FF0000"]<--or whatever the gateway IP is[/COLOR]
```Do you see other bebedor de café accessing a splash page?

---

### Post by potion on 2013-06-10
Hi chili555, thank you so much for working with me on this!

So actually, two of the three connections I've tried were at cafes with free wifi, and the third is at a friend's place where I'm staying. At my friend's place, I also don't have access to the router, because it's in a different apartment, and my friend has the password and permission and everything, but I'd feel awkward asking to go into the other apartment.

But this is a great place to be troubleshooting, because here I can have my laptop open and trying to connect, and meanwhile post from my friend's Mac, which can connect no problem.

So let's see...

> [QUOTE]when I turned it back on, the region had reset to US.
Until we make some permanent changes, it will revert. There is no need, yet, to make a change until we know it helps.[/QUOTE]

Don't know if this matters, but I'll just mention that when I turned my computer back on just now, it was set to MX. When it reverted before, that was at the cafe. I guess it varies depending on the network?

> [QUOTE]I tried pinging [www.google.com](www.google.com) from the terminal and that didn't work either.
Didn't work meaning what? It just hung there, or it came back to 'ping: unknown host'? There is a difference and the results suggest different problems.[/QUOTE]

At both the internet cafe and here at my friend's place, it takes about a minute, and then it returns "ping: unknown host www.google.com".

> Does it ping by number, suggesting a DNS nameserver problem?
```
ping -c3 8.8.8.8
```

Yes, that seems to work!

```
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
```

(Let me know if there's anything in particular I should quote... Wish I could copy and paste!)

> Please run:
```
nm-tool
```

I'll quote the info that seems most relevant... Please let me know if I've skipped anything important!

```
State: connected (global)

...

Device: wlan0 [INFINITUMaass]
Type: 802.11 WiFi
Driver: ath9k
State: connected
Default: yes
HW Address: 00:25:D3:9A:F0:57

...

Wireless Properties
WEP: yes
WPA: yes
WPA2: yes

Wireless Access Points (* = current AP)
*INFINITUMaass: Infra, 08:63:61:23:C6:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

(And then it lists three other routers in the area, all of them also Infinitum for what it's worth)

IPv4 Settings:
Address: 192.168.1.77
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.254
DNS: 192.168.1.254
```

> Can you ping the gateway?
```
ping -c3 10.0.0.1  <--or whatever the gateway IP is
```

Yes! This returns something similar to when I pinged by number earlier...

```
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
```

Here again, I can quote more of what was returned if it might help.

> Do you see other bebedor de café accessing a splash page?

I didn't notice, but I can ask mañana. :)

Thank you again for your help! I really, really appreciate it.

---

### Post by potion on 2013-06-10
YES!!! It works! Your mention of it seeming like a DNS nameserver problem led me to search for those terms, and I ended up [here]("http://askubuntu.com/questions/34983/troubleshooting-wireless-network-connection-dns-not-working"). I looked at my /etc/resolv.conf, which seemed to have some old stuff in it having to do with my connection at home in the US. Then I tried this...

```
$ sudo dhclient -r
$ sudo dhclient
```

...and it rewrote /etc/resolv.conf. And now everything's working! Can't tell you what a difference it will make to be able to get on the Internet here in Oaxaca, or at the very least here at my friend's place. I hope I'll be able to use the cafe wifi as well. Wonder if it'll work now or if there will still be issues.

Anyway, I can't thank you enough, chili555! I had never heard of any of those terms before and would have never been able to resolve the problem on my own. Muchísimas gracias!!!

---

### Post by chili555 on 2013-06-11
Usted es muy agradable. Me alegro de que está funcionando.

I hope Google translate got that right! As I say, too often, I'm glad it's working by whatever means.

---

