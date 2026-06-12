---
title: "Can't see Ubuntu laptop on Lan from Vista"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Innova on 2009-09-17
I have a web server and network share set up on my Unbuntu 9.04 laptop.  I can not ping, or connect to the share or the web server from another laptop (Vista) on the LAN.

I can ping and connect to the web server from a ubuntu desktop that is on the lan.  When I do a smbclient -L //192.168.0.4 I can see the shared folder.

However, a net view \\192.168.0.4 on the Vista laptop does not work (system error 53).

It seems like there is some firewall in place, but only for the vista machines?

Any ideas on what to check next?

---

### Post by Iowan on 2009-09-17
> **Innova said:**
> It seems like there is some firewall in place, but only for the vista machines?

Any ideas on what to check next?Perhaps the firewall is on the Vista machine.  If you can find the command prompt (I'd have to check my laptop to find how), you should be able to **ping** the Ubuntu machine.

---

### Post by Innova on 2009-09-17
I can't ping the ubuntu machine either.

---

### Post by Innova on 2009-09-17
I turned the firewall off on the vista machine.  This is what I see when I try to ping the ubuntu machine:

```
Pinging 192.168.0.4 with 32 bytes of data:

Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.

Ping statistics for 192.168.0.4:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

```
I'm not sure why they reply is from a different IP than the ping?

---

### Post by MaindotC on 2009-09-18
That could indicate the presence of a foreign node on your network.  If I were you I'd be very sure that no one is breaking into your network.  If someone loaded a root kit on your machine the only way to get rid of it is with a nice, fresh, clean install.

---

### Post by Innova on 2009-09-18
Any other ideas?  How could I check that out?

---

### Post by philcamlin on 2009-09-18
> **Innova said:**
> Any other ideas?  How could I check that out?

try rk hunter to see if you have any rootkits :popcorn:

---

### Post by Innova on 2009-09-18
```
Rootkit checks...
    Rootkits checked : 113
    Possible rootkits: 0

```

I got a couple warnings, mostly about commands being replaced with scripts.  (ldd, groups, which, lwp-request, adduser).  But besides that everything checked out ok.

How do i debug the network problem?

---

### Post by badger_fruit on 2009-09-18
I am betting this is a Vista problem, it sucks at most things and cross-platform networking is no exception.

What is 192.168.0.5? is that the machine you're trying to PING from?

I see something similar in Suse when I ping an unknown host or bad IP; the "reply" comes from the machine trying to do the ping.
You're going down the wrong path with the checking of rootkits and so on I think ... goto Control Panel > System Security or whatever it's called, turn off AV, Firewall and any other things that are turned on.

Try again.

Success?

---

### Post by Innova on 2009-09-18
I didn't have AV on, I turned off the firewall and windows defender, still getting the same response.

And yes, the machine that I was pinging from was 192.168.0.5.

What's the next thing to check?

---

### Post by badger_fruit on 2009-09-18
> **Innova said:**
> I didn't have AV on, I turned off the firewall and windows defender, still getting the same response.

And yes, the machine that I was pinging from was 192.168.0.5.

What's the next thing to check?

Thanks; the next thing to check is to see if you can ping ANYTHING from the Vista machine; I would try internal network first - for example, can it ping your router or default gateway?

I don't know if this will work for Vista but I use it fine on XP when I have network troubles, seems to restore it to good health again, might be worth a try:-

```

netsh interface ip delete arpcache
ipconfig /flushdns
ipconfig /registerdns
NBTSTAT.exe -R
nbtstat.exe -RR

```

(run those in order from the command line)

---

### Post by Innova on 2009-09-18
I'll try this when I get home.  I did also have a W2K laptop, that could not see the ubuntu machine.

---

### Post by Innova on 2009-09-28
I got sidetracked with other things, and didn't get to try this until just now.

However, it still doesn't work.  I'm not sure if I mentioned it earlier, but the Vista machine can connect to a linux Desktop that is connected to the router with cat5.  It can not connect to the linux laptop that is wirelessly connected.

---

### Post by MaindotC on 2009-09-28
It seriously sounds like someone is taking control of the firmware on your router.  We talked about this in a security class once.  Have you experienced anything weird like unwanted pop-ups or site redirections?

---

### Post by Innova on 2009-09-28
Nope, I really don't think that is the issue.  We live in the country...someone would have to park in our driveway to do it.  The more likely scenario is that it is a crappy router...it is a modem/router that was supplied to us by our phone company.

It looks like it is an Actiontec GT704-WG.  Does anyone have any experience with them?

---

### Post by MaindotC on 2009-09-29
I was thinking more along the lines of someone is controlling r3m0t3ly, not on your local network.

---

### Post by Innova on 2009-09-29
Well, I plugged the ubuntu laptop in to a cable, instead of using the wireless card, and now I can connect to it.

Is there different security on the wireless connection vs the wired?

---

### Post by Saghaulor on 2009-09-29
> **Innova said:**
> I turned the firewall off on the vista machine.  This is what I see when I try to ping the ubuntu machine:

```
Pinging 192.168.0.4 with 32 bytes of data:

Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.

Ping statistics for 192.168.0.4:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

```
I'm not sure why they reply is from a different IP than the ping?

When you try to ping a host that cannot be reached, the host you are on will respond back. Hence your 192.168.0.5 responding that 192.168.0.4 is unreachable.

Are you sure that it is the correct address? Confirm the address of your Ubuntu host with

```
ifconfig
```

Also, are you sure that the subnets are the same?

Is your router implementing something like virtual subnets for security purposes? Some routers have this feature, which makes all the computers invisible to each other, as if they were on their own private network.

I second that it's unlikely there is foul play at work. Although make sure to firewall your server because ever instance of a server app only opens holes for the bad guys to come in.

---

### Post by Saghaulor on 2009-09-29
> **Innova said:**
> Well, I plugged the ubuntu laptop in to a cable, instead of using the wireless card, and now I can connect to it.

Is there different security on the wireless connection vs the wired?

You probably have some sort of virtual subnet feature enabled.

I think it's an option for wifi security on most routers. If you turn it off it should work as if wired, although slower.

---

