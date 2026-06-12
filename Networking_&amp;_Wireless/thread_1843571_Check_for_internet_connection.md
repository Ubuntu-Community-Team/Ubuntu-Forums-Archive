---
title: "Check for internet connection"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2011-09-13
Hello,

  Is there some way to check if your computer is connected to the internet(or a LAN network) using any of the network devices on the computer?

---

### Post by IWantFroyo on 2011-09-13
You can open a terminal, and type:
```
ping -c 3 google.com
```

If it says something about packets being sent, you have a connection.

If it says "Host not found," you don't.

---

### Post by jsvidyad on 2011-09-13
> **IWantFroyo said:**
> You can open a terminal, and type:
```
ping -c 3 google.com
```

If it says something about packets being sent, you have a connection.

If it says "Host not found," you don't.

Does that check to see if there is a network connection over any of the network devices?

 Is there a command specifically for checking if the computer is connected to the internet?

---

### Post by IWantFroyo on 2011-09-13
If your computer is connected to the Internet, that will work. If it isn't, it won't.

This is the accepted (in general) method to testing your connection.

---

### Post by jsvidyad on 2011-09-13
But, if that command gives the output "Host not found", can't that also indicate some problem with DNS resolution rather than the lack of a connection to the internet? Isn't it possible to get that message even when you are connected to the internet?

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> But, if that command gives the output "Host not found", can't that also indicate some problem with DNS resolution rather than the lack of a connection to the internet? Isn't it possible to get that message even when you are connected to the internet?


yeah it can.

Ping a few domains to test. or ping a remote IP that way DNS doesnt come into it, such as the resolved google.com or a DNS server that you use

you can also check the light on your router ;-)

---

### Post by IWantFroyo on 2011-09-13
I was using Google as an example. Of course, if it doesn't work, you should ping a few other websites, too.

---

### Post by jsvidyad on 2011-09-13
Hello,

  I wanted to make something clear. What I want to check is if any of the network devices on my computer are connected to a network(whether it be LAN or the internet). I just want to check and see if any network device has made any connection to an outside network. So, checking the router is not a good way. Because, I could still be connected to the LAN, right?

   Isn't there a magic bullet(i.e. a specific command) for this??

I'd like to thank the people who took time to respond to this post.

---

### Post by IWantFroyo on 2011-09-13
If you have an internet connection through **anything**, Ubuntu will detect that and use that network hardware.

There isn't a "magic bullet," because you don't need one. The command I posted earlier works fine. It's the tried-and-true method of testing a connection (check multiple sites, if you want to be sure).

Edit- Also, this isn't checking the router. It's checking the Internet. Of course, if your router doesn't work, this won't, either.

---

### Post by jsvidyad on 2011-09-13
So, is there any way to check if I'm connected to a LAN, but not to the internet?

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> So, is there any way to check if I'm connected to a LAN, but not to the internet?

ping a device on the lan such as your router

---

### Post by jsvidyad on 2011-09-13
> **haqking said:**
> ping a device on the lan such as your router

How do I do that?

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> How do I do that?

is it your lan ?

if so you should know the IP address of the gateway/router.

same as before 

ping name or ip address

probably 192.168.0.1 or 192.168.1.1 if its a home/private lan

[see here for more info]("https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html")

[URL="https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html"]
[/URL]

---

### Post by garvinrick4 on 2011-09-13
Just a couple of easy commands to get quick info. Might come in handy for some.

```
cat /etc/resolv.conf
```

```
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by jsvidyad on 2011-09-13
> **garvinrick4 said:**
> Just a couple of easy commands to get quick info. Might come in handy for some.

```
cat /etc/resolv.conf
```

```
cat /var/lib/NetworkManager/NetworkManager.state
```

What does that second command do??

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> What does that second command do??


do it and you will know ;-)

it will show you the state of networking etc

```
man networkmanager 
```

for more information on it

---

### Post by Slim Odds on 2011-09-13
the command that you want is ifconfig

as in:
```
ifconfig
```

that will tell you about the network connection on each device.

Then to check for connectivity to the outside world you can use ping, etc.

---

### Post by jsvidyad on 2011-09-13
> **haqking said:**
> do it and you will know ;-)

it will show you the state of networking etc

```
man networkmanager 
```

for more information on it

So, it will show if there are any active network(internet/LAN)  connections?

---

### Post by haqking on 2011-09-13
> **Slim Odds said:**
> the command that you want is ifconfig

as in:
```
ifconfig
```that will tell you about the network connection on each device.

Then to check for connectivity to the outside world you can use ping, etc.
[I]
Ifconfig[/I] will show information about the interfaces, not whether they are connected or have working connectivity or not, it is used to show information or configure an interface

---

### Post by Slim Odds on 2011-09-13
> **haqking said:**
> [I]
Ifconfig[/I] will show information about the interfaces, not whether they are connected or have working connectivity or not, it is used to show information or configure an interface

Which is exactly what I said.

When it comes to things like networking there are a lot of layers. So you need to check each one. You can't get an Internet connection until you are connected to the LAN. ifconfig will tell you if you're LAN connected. Otherwise ping is useless.

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> So, it will show if there are any active network(internet/LAN)  connections?


OK im confused as to what you want to know ?

ping a local ip address will tell you if you are connected locally, if no other hosts then ping your router

ping a remote address to test internet (wan connectivity)

ifconfig will show you information about your interfaces (eth, wlan etc)

```
cat /var/lib/NetworkManager/NetworkManager.state
``` 

will show you a connections state

as i said see 
```

man networkmanager
```

You can check to see if a cable is connected to a machine, seeif the light is active on the NIC where the cable goes

check lights on router

check wireless LED on laptop or PCI card on desktop machine or USB

again check wireless lights on router.

This all covers it just about

---

### Post by jsvidyad on 2011-09-13
so, if the command 'ifconfig -a' doesn't show an ip address for any device, does that mean that the computer is not connected to any network(internet or LAN) ?

---

### Post by haqking on 2011-09-13
> **Slim Odds said:**
> Which is exactly what I said.

When it comes to things like networking there are a lot of layers. So you need to check each one. You can't get an Internet connection until you are connected to the LAN. ifconfig will tell you if you're LAN connected. Otherwise ping is useless.


IFCONFIG on its own will show your network interfaces.

For example, i am connected with connectivity via wireless, but it will show etho as well as it is up but not connected

It doesnt prove network connection to a LAN

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> so, if the command 'ifconfig -a' doesn't show an ip address for any device, does that mean that the computer is not connected to any network(internet or LAN) ?

if there is no IP address then likely the connection is not connected or has problems

however it can still show an IP address and not have connectivity which can be confusing if you dont know what your looking for

---

### Post by haqking on 2011-09-13
What are you wanting to achive exactly ?

do you actually have an Internet connection issue you need to troubleshoot ?

or a LAN one ?

or wanting to know for other reasons ?

cos we are throwing different commands at you without really understanding what you need to do.

---

### Post by haqking on 2011-09-13
> **Slim Odds said:**
> Which is exactly what I said.

When it comes to things like networking there are a lot of layers. So you need to check each one. You can't get an Internet connection until you are connected to the LAN. ifconfig will tell you if you're LAN connected. Otherwise ping is useless.


by the way, im not arguing or saying you are wrong.

Far from it, ifconfig is invaluable for sure and one of the first things along with physical layer to check when troubleshooting.

I was just saying it doesnt prove network connectivity thats all.

perhaps i misread you ;-)

peace

---

### Post by jsvidyad on 2011-09-13
> **haqking said:**
> What are you wanting to achive exactly ?

do you actually have an Internet connection issue you need to troubleshoot ?

or a LAN one ?

or wanting to know for other reasons ?

cos we are throwing different commands at you without really understanding what you need to do.

I just want to have a definite way of saying whether my computer is or is not connected to a network using any of the network interfaces on my computer.

---

### Post by haqking on 2011-09-13
> **jsvidyad said:**
> I just want to have a definite way of saying whether my computer is or is not connected to a network using any of the network interfaces on my computer.


if its has a cable in it then its connected, but doesnt mean you have aactive connectivity.

if its wireless then you can use your wireless network manager, network manager gui, lights on the machine etc to see if your connected

none of this proves connection to internet.

only way to do that is as said before ping a remote host or browse for a page.

or login to your router and check connection

or check lights on router

or check state of networking locally for LAN connectivity

or click your networkmanager applet and choose connection information (see image)

---

