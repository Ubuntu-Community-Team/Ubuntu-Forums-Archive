---
title: "Firewall stopping HTTP POST requests"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by veggen on 2012-03-27
For some bizarre reason, ufw is *sometimes* preventing HTTP POST requests. GETs work normally, but POSTs hang forever. I know it's ufw because everything goes back to normal if I turn it off. Also, if I restart networking, it solves the problem temporarily. I don't have to do anything to ufw for it to start misbehaving. It can work normally for days before it starts blocking POSTs for no good reason.

Any clue what it might be?

Thanks.

---

### Post by veggen on 2012-04-03
Local Apache is unaffected. POSTs to it work normally.

---

### Post by veggen on 2012-04-05
*bump*

---

### Post by Vishal Agarwal on 2012-04-06
try enabling lo traffic in iptables

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

---

### Post by veggen on 2012-04-07
Hey, thanks for taking the time to help me out!
Can you please give a little more insight into what the above commands are doing? I know what iptables is, but I don't really get what is being enabled here...

---

### Post by veggen on 2012-04-10
Didn't help :(
Anyone has any more ideas? Would be very greateful.

---

### Post by cybpabeofm on 2012-04-10
Could you give us more information? What data are you sending to servers exactly?
What port do you use and what packet type when you POST?

When it stops your POST run this command and please post up the output.

sudo ufw status

This will tell us what ufw is blocking and allowing

---

### Post by veggen on 2012-04-11
Well, I'm just doing a simple form submission. Take posting this response here on the forum for example. I had to disable ufw to do it.

While it was still on (and this post was still hanging indefinitely), the status returned this:

51413/tcp                  ALLOW       Anywhere
51413/udp                  ALLOW       Anywhere
51413/tcp                  ALLOW       Anywhere (v6)
51413/udp                  ALLOW       Anywhere (v6)

51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere (v6)
51413/udp                  ALLOW OUT   Anywhere (v6)

The rules you see are the predefined Transmission specific ones.
The screenshot of the ufw window is attached.

Does this help at all?

Thanks for putting time into this.

---

### Post by veggen on 2012-04-16
*bump*

---

### Post by sourchier on 2012-04-25
Try the following:

sudo su -

ufw allow http
ufw allow https

ufw disable && ufw enable

This should enable http (port 80), and https (port 443).

I hope this works for you.

---

### Post by Ms. Daisy on 2012-04-25
I think you would benefit from a [tutorial ]("http://ubuntuforums.org/showthread.php?t=1876124")I found helpful regarding UFW.
 
BTW, someone recommended using iptables above. That's a good recommendation, however, it's an either-or situation. You can run ufw or iptables, but if you enable both they will conflict.

---

### Post by haqking on 2012-04-25
> **Ms. Daisy said:**
> I think you would benefit from a [tutorial ]("http://ubuntuforums.org/showthread.php?t=1876124")I found helpful regarding UFW.
 
BTW, someone recommended using iptables above. That's a good recommendation, however, it's an either-or situation. You can run ufw or iptables, but if you **enable** both they will conflict.

well its not the **"enabled"** thing

As UFW requires IPTables so it has to be enabled ;-)

IPTables rules can cause havoc if using both to create your rules.

It is also better if you remove UFW if using IPTables directly.

```
sudo apt-get remove ufw gufw
```

---

### Post by Ms. Daisy on 2012-04-25
Yes, thanks for the clarification. What I meant was if you are running UFW and you modify iptables like the previous poster recommended, then you'd end up with a mess. 
 
But haqking said it much better than I.

---

### Post by haqking on 2012-04-25
> **Ms. Daisy said:**
> Yes, thanks for the clarification. What I meant was if you are running UFW and you modify iptables like the previous poster recommended, then you'd end up with a mess. 
 
But haqking said it much better than I.

I was just being pedantic ;-)

Peace

---

### Post by Ms. Daisy on 2012-04-25
What? You??? No. I'll never believe it :P

---

### Post by veggen on 2012-05-23
Thanks to all who chipped in.

Just discovered that similar problems occur when I connect to VPN (pptp), even when firewall is down. Sometimes the effect is the same, and sometimes no HTTP or SSH is possible at all, but ping will work just fine. So, starting the firewall and connecting to VPN both trigger *something* that messes up my network... Does this make any sense to anyone?

---

