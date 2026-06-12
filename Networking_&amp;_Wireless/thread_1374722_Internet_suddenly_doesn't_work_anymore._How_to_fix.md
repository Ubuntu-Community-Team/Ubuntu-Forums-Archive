---
title: "Internet suddenly doesn't work anymore. How to fix?"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by kramer65 on 2010-01-07
Hello,


I've got Ubuntu 8.04 working perfectly for about 1.5 years now. More than a week ago, my internet suddenly stopped working though. I first thought it was the fault of my ISP, but I just plugged the cable in the Windows Vista laptop of my sister and that works perfectly (writing on it now).

I wouldn't know where to start searching for the problem. Could anybody help me out..

---

### Post by lotharmat on 2010-01-07
> **kramer65 said:**
> Hello,


I've got Ubuntu 8.04 working perfectly for about 1.5 years now. More than a week ago, my internet suddenly stopped working though. I first thought it was the fault of my ISP, but I just plugged the cable in the Windows Vista laptop of my sister and that works perfectly (writing on it now).

I wouldn't know where to start searching for the problem. Could anybody help me out..


Please can you post the output of 

```
ifconfig
```

and 

```
lshw -C network
```

---

### Post by kramer65 on 2010-01-07
I couldn't copy-paste the outputs since they are on the pc without internet. So I took a photo using my phone and hereby upload the pictures. I hope it tells you anything, since it is like Greek to me.

---

### Post by Methuselah on 2010-01-07
Did you try restarting your router?

---

### Post by kramer65 on 2010-01-07
Yes, I also did a reset of the router (with the reset button), restarted ubuntu multiple times, and unplugged and replugged everything. I presume you don't see anything wrong from the photos I took?

---

### Post by Methuselah on 2010-01-07
> **kramer65 said:**
> Yes, I also did a reset of the router (with the reset button), restarted ubuntu multiple times, and unplugged and replugged everything. I presume you don't see anything wrong from the photos I took?

Network stuff isn't really my forte but I didn't see anything out of the ordinary.
In particular, eth0 seems to have an ip address that I assume was handed out by your router's dhcp.

I guess Firefox will not work but can you ping anything?

```

ping -c4 www.google.com

```

or failing that

```

ping -c4 64.233.169.106

```

At the end, it shoudl tell you how many packets were lost, if any.

---

### Post by kramer65 on 2010-01-07
It says, "network is unreachable"..

---

### Post by Methuselah on 2010-01-07
Try 

```

sudo iconfig eth0 down
sudo ifconfig eth0 up

```

Then do **dmesg**.

At the end of long output, tt should talk about the interface going down and up.
But if you see any additional possible error output near the end please note it down.
Also, try pinging stuff again.

I can't really say "this is happening because" but hopefully there will be some clue eventually.

---

### Post by zine92 on 2010-01-07
hey anyway, my problem is the exact opposite. Dual booting, windows wifi failed me but ubuntu save me. Maybe if you have another os/live cd pop it in and try using the internet. If it works maybe it is something with what you installed.

---

### Post by kramer65 on 2010-01-07
I did what you asked. Attached is the image of the last part of the dmesh command. Does that give you any clues?

One more thing. It is not only firefox which is not working. I also tried to connect to the internet using Epiphany, Google Chrome, Transmission, and Filezilla, but none of them could connect.

---

### Post by kramer65 on 2010-01-07
No ideas anymore..?

---

### Post by bapoumba on 2010-01-07
Moved from ABT to Networking. Maybe you'll get other people to help you around here.

Have you checked your cables and tried with another one?
Would you have setup a proxy somewhere for some reason?

---

### Post by Iowan on 2010-01-07
Can you ping the router? Might also be useful to see results of **route -n** and contents of */etc/resolv.conf*.

Looks like the link is going up and down a lot.

---

### Post by kramer65 on 2010-01-08
I recently did a port-forward in order to use a vnc-viewer to see my ubuntu desktop (which is btw really cool to see my Ubuntu desktop from my Android phone!), but for the rest I didn't set up any proxy or anything.. 

**route -n** gives:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

And the file **/etc/resolv.conf** contains the following:
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5778
#
### END INFO

search lan


nameserver 192.168.1.254
```

I was just connected to my router with my vista laptop using wifi and had my Ubuntu desktop connected using the cable (using the cable on my vista laptop also works, so that's not the problem). But when I had the two connected, my vista laptop suddenly said that it was assigned the same ip as "another pc on the network". Is that maybe a hint to anything?

I also tried to log into my router (192.168.1.254) using Ubuntu and it says the same as when I want to connect to a random website; Error while connecting. Firefox Can't make a connection with the server at 192.168.1.254. Although the website seems to exist, firefox can't connect to it. (this text is freely translated from Dutch..). But using my vista laptop I can connect and log into the router without any problem..

Does this whole story make sense..?

---

### Post by llawwehttam on 2010-01-08
A while back my computer did somthing similar where the router could see the computer and had given it an IP and looked fine but no data was going through.

On closer inspection the pet rabbit had taken a fancy to the cable and gnawed a bit of it away so some of the wires were cut/ shorted but it could still assign an IP.

You don't have pets do you ?lol

anyway on a more serious note what router are you using and how long have you had it? Also have you had two laptops connect to it using wifi before?

---

### Post by kramer65 on 2010-01-08
I have no pets indeed.. ;)

I think the wire is actually also fine, because when I put the same wire into my vista laptop and disable wifi it also works perfectly. I have never had two laptops connect to this router at the same time. I did have it working before with my Ubuntu pc connected by wire, and this vista laptop connected by wifi.

The router I'm using is a Thomson st780 wl..

Anymore tips? I am about the get mad here.. Isn't it easier to just install the latest Ubuntu..? (it would create *a lot of* work, but if that would give me internet back..)

---

### Post by bapoumba on 2010-01-08
Please make sure you are using dhcp with wifi and let the router assign IPs to both computers.

---

### Post by Iowan on 2010-01-08
There is no default gateway listed - internet-bound traffic doesn't know how to get there. This information *should* come from DHCP server... although (as I recall) Network Manager lets you specify one.

---

