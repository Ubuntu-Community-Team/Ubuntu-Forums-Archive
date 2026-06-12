---
title: "Linux equivalent of netsh command?"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by UbuKunubi on 2009-11-03
Hello,

Yesterday we suffered an Internet outage.
We called up our ISP (Orange) and were first told "we don't support Linux!"
The operator then repeatedly told us that she was going to send us a new Ethernet cable which would somehow fix our problem. 

When I asked how this would also prevent access via wireless the operator just kept saying the same thing over and over!!!

We DID manage to get a call-back arranged, and the chap was a lot more rational and knowledgeable.
In the interests of achieving our goal of getting back on line we fired up xp on another machine connected to our router (orange livebox).

We were asked to stop the DHCP service, and then type "netsh int ip reset c:\resetlog.txt" into the windows command line (which worked), and my question is this:

Since we wish to be shot of xp, and don't want to run into the buffers again should this problem re-occur, what is the Ubuntu (9.04) equivalent of the same command, and is the reset.txt file generated when this command is run, or (more seriously) does the orange livebox have some way of writing this file to root of xp since no software was used to go online?

As you can image nobody should be forced to run a OS thats not wanted, let alone have to pay in the future for said OS merely to issue a command to the router.

We would really appreciate any help,
Ubu

---

### Post by UbuKunubi on 2009-11-15
bump!

---

### Post by UbuKunubi on 2009-12-02
bump

---

### Post by pbrane on 2009-12-02
I haven't worked on windows in years, however I read this:
[http://support.microsoft.com/kb/299357]("http://support.microsoft.com/kb/299357")

It seems that you're just resetting the TCP/IP stack. You may be able to do the same thing on ubuntu by typing **service networking restart** in a terminal.

I take it rebooting the orange livebox didn't help? or that rebooting your computer didn't either.

---

### Post by Lars Noodén on 2009-12-02
Can you explain in regular (not MS-specific) networking terms what netsh is supposed to do?  xp is usually a small subset of functionality in comparison to linux, but one great difficulty is finding out what the MS-specific terms are.

---

### Post by UbuKunubi on 2009-12-03
> **pbrane said:**
> I haven't worked on windows in years, however I read this:
[http://support.microsoft.com/kb/299357]("http://support.microsoft.com/kb/299357")

It seems that you're just resetting the TCP/IP stack. You may be able to do the same thing on ubuntu by typing **service networking restart** in a terminal.

I take it rebooting the orange livebox didn't help? or that rebooting your computer didn't either.
Thanks for the tip about resetting the TCP/IP stack. It was like banging my head against the wall trying to get them to tell me what they were trying to achieve so I could find the equivalent command for Ubuntu, but they are perfect robots, and so would not deviate from their windows fixing scripts.

No, rebooting either the router and the computers did not make any difference, with ifconfig I could the PC transmitting packets to the router, but none where received,

Thanks for your help,
Ubu

---

### Post by UbuKunubi on 2009-12-03
> **Lars Noodén said:**
> Can you explain in regular (not MS-specific) networking terms what netsh is supposed to do?  xp is usually a small subset of functionality in comparison to linux, but one great difficulty is finding out what the MS-specific terms are.

erm, Im not sure who your asking, so I'll respond as if it is addressed to me.

I have no interest in running windows, and my goal is to translate the windows command "netsh int ip reset c:\resetlog.txt", into a command that I can use in Ubuntu terminal (for 9.04)

---

### Post by lykwydchykyn on 2009-12-03
Reading up a bit on that command, it looks like it does more than just restart the tcp/ip stack; it actually defaults all the settings in the registry as well.

I'm not sure if there's a command in Linux to do that.   In the old days it'd be a matter of clearing out /etc/network/interfaces and /etc/resolv.conf, but here in the days of network-manager I'm not really sure where all the information is being stored.

---

### Post by Lars Noodén on 2009-12-04
> **UbuKunubi said:**
> 
my goal is to translate the windows command "netsh int ip reset c:\resetlog.txt", into a command that I can use in Ubuntu terminal (for 9.04)

That's a step closer.  What are the expected results from that command?  

Do you want the route cleared?  Release the dchp lease?   Deactivate the network interface?  Change the IP address(es) for that interface?  Edit the firewall?

---

### Post by gmgj on 2009-12-12
If I do this System - Administration - Network Tools - Devices, and click on one of the Ethernets (I think I have a wired and a wireless eth0 and eth1), I can see the IP address of this machine on my local network.  

How do I get the IP address of this machine so that I can use it in script?

---

### Post by UbuKunubi on 2009-12-12
> **Lars Noodén said:**
> That's a step closer.  What are the expected results from that command?  

Do you want the route cleared?  Release the dchp lease?   Deactivate the network interface?  Change the IP address(es) for that interface?  Edit the firewall?

when I was talking to orange they would not give me a straight answer on what the command does, nor how it affects the router. When a hardware reset/reboot were done our connection problem remained, but when the netsh command was run from a windows machine the problem was rectified.

We do not wish to rely on windows for anything, so being able to find the ubuntu friendly equivalent is the goal.

My guess is that is does a mixture of those things: release the dhcp lease, reset the IP stack for the ethernet card, and such.

Many thanks for getting back,
Ubu

---

### Post by UbuKunubi on 2009-12-12
> **gmgj said:**
> If I do this System - Administration - Network Tools - Devices, and click on one of the Ethernets (I think I have a wired and a wireless eth0 and eth1), I can see the IP address of this machine on my local network.  

How do I get the IP address of this machine so that I can use it in script?

with python my prefered weapon of choice is:

f=op.popen("ifconfig eth0")
data = f.read()
f.close()

and then do all the string crunching held in 'data',
hope this helps,
Ubu

---

### Post by lykwydchykyn on 2009-12-12
This does it, nice bash one-liner:
```

ifconfig eth0|grep "inet addr"|cut -d : -f 2 |cut -d " " -f 1

```

---

### Post by Lars Noodén on 2009-12-13
> **lykwydchykyn said:**
> This does it, nice bash one-liner:
```

ifconfig eth0|grep "inet addr"|cut -d : -f 2 |cut -d " " -f 1

```

Another way is to use one instance of awk to take the place of grep and both instances of cut:

```

# show the address
ifconfig eth0 | awk '/ inet / { sub(/^.*:/,"",$2); print $2 }'

```

The output can be saved in a variable and used elsewwere.

```

# save to environment variable IPADDRESSS
export IPADDRESS=`ifconfig eth0 | awk '/ inet / { sub(/^.*:/,"",$2); print $2 }'`
echo $IPADDRESS

```

---

### Post by UbuKunubi on 2009-12-13
> **lykwydchykyn said:**
> This does it, nice bash one-liner:
```

ifconfig eth0|grep "inet addr"|cut -d : -f 2 |cut -d " " -f 1

```

That is better, and one now added to my list of code snippets.
Thanks!

---

### Post by shairozan on 2009-12-14
Hey everyone

Just for everyone's edification, the netsh command is the driving force behinds the Windows TCP/IP stack and the firewall. Most people will never touch it, but those who do primarily do it when adding firewall rules via command line (as we do where I work through group policy) or, in rare occasions, resetting the networking stack for Windows XP.

When you reset, via the netsh command, what it does is clear out all registry items pertaining to networking. This doesn't affect the router at all, but just sets you back to a clean slate network wise on the Windows machine. This would mean having to re-configure your interface with either the static address or telling it to use DHCP. 

Netsh is a blanket application that includes routing, firewalling and much more, and as far as I know, there is no 1:1 equivalent in Ubuntu. What you may want to look at doing is a simple 

```

sudo /etc/init.d/networking restart
``` as it will force DHCP release and re-acquisition if applicable. 

What would be a different story altogether would be if your **router** is not correctly acquiring it's DHCP address, which could be resolved by restarting it.

---

### Post by UbuKunubi on 2009-12-15
> **shairozan said:**
> Hey everyone

Just for everyone's edification, the netsh command is the driving force behinds the Windows TCP/IP stack and the firewall. Most people will never touch it, but those who do primarily do it when adding firewall rules via command line (as we do where I work through group policy) or, in rare occasions, resetting the networking stack for Windows XP.

When you reset, via the netsh command, what it does is clear out all registry items pertaining to networking. This doesn't affect the router at all, but just sets you back to a clean slate network wise on the Windows machine. This would mean having to re-configure your interface with either the static address or telling it to use DHCP. 

Netsh is a blanket application that includes routing, firewalling and much more, and as far as I know, there is no 1:1 equivalent in Ubuntu. What you may want to look at doing is a simple 

```

sudo /etc/init.d/networking restart
``` as it will force DHCP release and re-acquisition if applicable. 

What would be a different story altogether would be if your **router** is not correctly acquiring it's DHCP address, which could be resolved by restarting it.

Wow, a great well-rounded anser!
Many, many thanks for your post.
From what we could gather from the limited details given by our ISP, releasing the DHCP was the goal, so I can now mark this post as solved!

All the best,
Ubu

---

