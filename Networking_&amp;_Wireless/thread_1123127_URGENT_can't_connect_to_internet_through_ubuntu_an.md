---
title: "URGENT: can't connect to internet through ubuntu any help appreciated!"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Professor 0110 on 2009-04-11
Hi everyone, 

I have a bit of an urgent problem. I can't connect to the Internet on my ubuntu installation through either wired or wireless. The laptop in question is dual booted with Ubuntu and Windows. 

Now, recently I couldn't connect to the internet but that was because I installed the guarddog firewall. I removed that application, and the Internet worked for a while. But when I booted up today, it wouldn't work. 

I'm using ubuntu 8.10. The router it connects to is a Netgear wirless and wired router which then connects to the internet gateway which is a modem. We are on satellite broadband. 

Any help on troubleshooting this problem will be greatly appreciated! I use ubuntu for work and need the internet restored asap. 

Finally, the other three windows boxes on the network connect to the Internet fine. It's just the Ubuntu OS that's having trouble. 

one more thing; Bluetooth is enabled on ubuntu so I'm not sure of that will have any affect on the Internet connection. 

Sincerely, 

Professor 0110


PS - Shoutouts to Dr Small! I hope he remembers me. I was known as Smeagol or professor Smeagol at one stage on Php Power forums I think.

---

### Post by mrsteveman1 on 2009-04-11
Try checking with the network manager in the upper right corner to see if it is connected to something, and check the connection info to make sure it has an IP address and the right router listed.

If things look fine there, check iptables rules like this:

```
sudo iptables -L
```

there should be 3 empty sections with no rules, if there are they may need to be removed.

Once you have that done, try to ping the following address:

```
ping 4.2.2.2
```

That should tell you if you at least have IP connectivity out to the internet

---

### Post by Professor 0110 on 2009-04-12
Okay, there's a whole bunch of stuff such as "all" and "anywhere" and state RELATED, ESTA" etc. Also, I've confirmed that its a problem related to Ubuntu itself. I tried to connect to another network and received the same problem. 

How can I remove all rules and disable iptables?

Thankyou very much for the help so far, though. :)

Cheers,

---

### Post by aaronp on 2009-04-12
> **Professor 0110 said:**
> Okay, there's a whole bunch of stuff such as "all" and "anywhere" and state RELATED, ESTA" etc. Also, I've confirmed that its a problem related to Ubuntu itself. I tried to connect to another network and received the same problem. 

How can I remove all rules and disable iptables?

Thankyou very much for the help so far, though. :)

Cheers,

I think you can use Firestarter to configure the rules in iptables. May need someone to verify that this is the case though.

hth
Aaron

---

### Post by mrsteveman1 on 2009-04-12
Depending on what is actually writing the rules and adding them into the kernel, it may only require a restart. However that is more of a "how do i uninstall this program" question, i'm not at all familiar with this guarddog program or where it stores the iptables rules if that is indeed the problem.

You might check in /etc/network/interfaces and see if there are any directives having to do with iptables or firewall rules.

If you want to try to remove all the old rules from the **running system** try this:

> # iptables -F
# iptables -X
# iptables -t nat -F
# iptables -t nat -X
# iptables -t mangle -F
# iptables -t mangle -X
# iptables -P INPUT ACCEPT
# iptables -P OUTPUT ACCEPT

That should flush all rules and ensure that your system isn't dropping packets by default. This will be temporary, if you find something goes wrong just reboot and all of that will be undone.

---

### Post by Professor 0110 on 2009-04-12
mrsteveman1, you're a genius! That worked awesome! Thank you very, very much. That was greatly appreciated. I'll have to copy down that command to execute at start-up. 

Cheers,

---

### Post by aaronp on 2009-04-12
you could try writing them into a shell script and then adding that script to your startup programs via Sessions.
you ight find that you don't need to do it again though...

---

### Post by mrsteveman1 on 2009-04-12
I assume that restarting doesn't fix the problem but that set of commands does. That means something is still setting iptables rules at startup. You shouldn't need to run those commands at startup, you would basically be reversing the commands that are already being run by yet another script somewhere else.

Check in /etc/network/interfaces, and also check to see if there is still a script in /etc/init.d for the guarddog program.

---

### Post by Professor 0110 on 2009-04-12
How would I write those commands into a shell script?

Also, I cd to /etc/network/ but I can't access interfaces. How do I access interfaces? When I execute the dir command it informs me that interfaces is there, but I can't access it.

Finally, I can't access the guarddog thing in /etc/init.d

Thanks.

---

### Post by mrsteveman1 on 2009-04-13
The commands i listed were only for testing, they confirmed that firewall rules were the problem. You shouldn't need those going forward. What you actually want is to remove the changes guarddog made. It appears as though there are 2 files that remain after uninstalling guarddog, and you should be able to remove them like this:

> sudo dpkg --purge guarddog

that SHOULD remove the files, so reboot and see if things work. If not you can remove them like this:

> sudo rm /etc/init.d/guarddog
sudo rm /etc/rc.firewall

---

