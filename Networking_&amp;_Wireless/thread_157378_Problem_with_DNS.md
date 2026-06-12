---
title: "Problem with DNS?"
date: 2006-04-09
forum: Networking &amp; Wireless
---

### Post by nodyl on 2006-04-09
so I did the stuff on that sticky post and everything works except for when I try to ping the internet by name.  Anyways, here's some info.  How can I fix this?

~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

mapping hotplug
            script grep
            map eth0

iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp
wireless-essid Henry

auto eth1

~$ ifconfig eth0
eth0     Link encap:Ethernet   HWaddr  00:12:3F:CF:6B:5A
           inet addr:  192.168.1.100  Bcast:  192.168.1.255  Mask: 255.255.255.0
           inet6:  fe80::212:3fff:fecf:6b5a/64   Scope: Link
           UP BROADCAST MULTICAST   MTU:1500  Metric:1
           RX packets:71 errors:0 dropped:0 overruns:0 frame:0
           TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0  txqueueulen:1000
           RX bytes:193034 (18.5 KB)   TX bytes:13448 (13.1 KB)
           Interrupt:18

~$  route -n 
Destination      Gateway          Genmask            Flags  Metric  Ref  Use Iface
192.168.1.0     0.0.0.0            255.255.255.0    U        0        0     0    eth0
192.168.0.0     0.0.0.0            255.255.255.0    U        0        0     0    eth1
0.0.0.0           192.168.0.1      0.0.0.0              UG      0        0     0    eth1
0.0.0.0           192.168.1.254   0.0.0.0              UG      0        0     0    eth0

~$ cat /etc/resolv.conf
search lmdaca.adelphia.net
nameserver 67.21.15.5
nameserver 67.21.15.21

So anyways that's all the relevant stuff, I think.  Also is it dangerous for me to put all those addresses?

---

### Post by bscbrit on 2006-04-09
A couple of questions - which might simply be me clutching in the dark.....

Where is the configuration of eth1?

What is in /etc/hosts?  If resolv.conf cannot resolve 'lmdaca.adelphia.net' how can it search that domain for a name resolution? (I think you can see what I mean...?)

And I'm not sure about this one, but here goes.  Doesn't the 'gateway' provide access to all addresses that are not on the local network and, if so, why do you specify 2 different ones.  Surely, only one points to the rest of the world, or do you have 2 separate feeds to the outside? (Might just be me talking c~~p again).

---

### Post by nodyl on 2006-04-09
well, eth1 is my wireless card, but it works.  What does it mean to resolve something (I'm not a linux newbie, but I've never done my own networking before or had to set this system up before).

I didn't specify the wireless gateway; my comp did that on its own.  To get the gateway ip for the land line I just looked on the other comp hooked up to the router.

---

### Post by bscbrit on 2006-04-09
The internet uses numerical addresses to identify the 2 network cards that are communicating to each other.  For example, the network cards in your computer have the addresses 192.168.0.? and 192.168.1.?.  You might be trying to download information from a website e.g. 123.234.100.1.  But humans don't like numbers - we much prefer names.  So the address 123.234.100.1 might actually be [www.nosuchplace.com](www.nosuchplace.com) or whatever.  The computer needs to be able to convert, or 'resolve' the names that we type into the actual addresses that the computer needs to communicate.  For this, we use Dynamic Name Servers (DNS) and these are often standalone computers owned by the ISPs - for example, you  are using nameservers at 67.21.15.5 and 67.21.15.21.  These are the addresses that you can feed a name to ([www.nosuchplace.com](www.nosuchplace.com)) and they will return the numeric address to use to communicate to it.

In your system, the first entry in resolv.conf is lmdaca.adelphia.net - which is a nice name understandable to humans.  So to convert it, it has to be resolved, and so your computer is told to look first at Imdac.adelphia.net to get an answer.  But this is a nice name understandable to humans. So to convert it, it has to be resolved, and so your computer is told to look first at Imdac.adelphia.net to get an answer.  But this is a nice name.......  Do you see a problem here?

Now if lmdaca.adelphia.net is actually your computer is will not matter - hence the reason I asked what is in /etc/hosts.  /etc/hosts might simply tell your computer that lmdaca.adelphia.net is the same as your own computer.  But, if it doesn't say that, then you might be stuck in a loop.  If you are, you will not be able to access the internet by name.  Which, not too surprisingly, is **exactly** the problem that you are experiencing.

So, if you can post the contents of /etc/hosts it will help me solve the problem - maybe;) 

However, reading your last reply has confused me.  Basically it sounds as though this computer is set up for both ethenet (wired) connection and wireless connection simultaneously.  While this can be done, it does confuse the picture somewhat.  Can you please clarify what we are trying to connect to where...?

Edit:  Resolving names is not linux specific - every computer on a network must have some way of solving this problem.  In linux though, you have far more control over what, where and how things are achieved - Windows simply does it one way and you have to live with it, whether it is what you want or not.  So what we are currently doing is trying to fine-tune the name resolution in your computer so that it does what _you_ want, _when_ you want it and in the method that _you_choose.

Edit 2:  Of course, I am not a network whizz, perhaps someone will turn up and tell me that I'm talking rubbish again...

---

### Post by nodyl on 2006-04-09
So this is what's in hosts:

127.0.0.1 localhost.localdomain localhost nodyl

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0  ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.100 nodyl

Right now I am  trying to connect to the wired landline; I use the wireless at school (which works).

---

### Post by bscbrit on 2006-04-09
Right, the first thing to do is to comment out the 'lmdaca.adelphia.net' in resolv.conf.

Secondly, if you have a firewall installed then temporarily disable it.  There is no firewall installed by default so, unless you have deliberately set one up this shouldn't be an issue. (But if you DO have a firewall, then it might give you confusing indications during testing.)

Then try accessing the internet by name from the command line e.g. ping -c 5 [www.mandscunningham.com](www.mandscunningham.com) (thats my domain so I do not mind you testing against it, just don't abuse it please - its also pretty boring but it does its job for me)

If you still cannot ping by name then I suspect that your computer is getting confused about whether it should be connecting by wire or by wireless.  Do you have networkmanager installed?  On the other hand, if everything works and you had a firewall installed, turn it back on and see if everything _still_ works.  Let us know how you get on.

---

### Post by nodyl on 2006-04-09
I commented it out and I still cannot ping by name.  So I disabled eth1 to see if that would work.  Then I did a /etc/init.d/networking restart 
Still doesn't work.

---

### Post by bscbrit on 2006-04-09
So let me get this right, and please check these as we go through them:

You can ping by address:  i.e. ping -c5 82.211.81.86 works.

You cannot ping by name i.e. ping -c5 [www.mandscunningham.com](www.mandscunningham.com) doesn't work.

Therefore the problem is name resolution.

---

### Post by nodyl on 2006-04-09
so I checked to see if what I had in resolv.config was the same on this computer and it is so I'm confused.  Does it help if I say also that gaim doesn't connect?

---

### Post by bscbrit on 2006-04-09
No, that didn't help, you now seem to be talking about 2 computers - I only thought we were working on one!

Can you please try both the suggestions that I made in my last post and confirm that they do or do not work using the commands exactly as I have typed.

---

### Post by bscbrit on 2006-04-09
Nodyl

Any luck?

---

### Post by nodyl on 2006-04-09
I can ping by number but not by name.  I am not talking about two computers.  It is the same computer that can't connect to gaim or ping by name.

---

### Post by nodyl on 2006-04-09
Just out of curiosity, why does it sound like two computers?

---

### Post by nodyl on 2006-04-09
Okay so I can ping the second two numbers in resolv.config, but not the first.  What should I do about that?

---

### Post by mips on 2006-04-10
Try disabling IPv6, might do the job.

---

### Post by nodyl on 2006-04-10
I tried this in mozilla.  It didn't help.

---

### Post by mips on 2006-04-10
Disable it system wide, not only in mozilla.

---

### Post by mips on 2006-04-10
[http://www.ubuntuforums.org/showthread.php?t=151013](http://www.ubuntuforums.org/showthread.php?t=151013)

---

### Post by bscbrit on 2006-04-10
Nodyl - I see that mips is giving you a hand.  He knows far more than I do!  The IPv6 is a fairly frequent cause of similar problems on this forum.  (I'm not quite sure why they simply don't disable it as default because nobody actually needs it yet.)

The reason that I thought that you were referring to 2 computers is when you said "so I checked to see if what I had in resolv.config was the same on this computer" - the same as what?  I thought that you were comparing the contents of resolv.conf on 2 separate computers.  Obviously my mistake - sorry.

Which numbers can you ping, and which can you not ping?  Your resolv.conf should now contain simply

nameserver 67.21.15.5
nameserver 67.21.15.21

and nothing else.

---

### Post by nodyl on 2006-04-11
Mips, I disabled the ipv6 using the mv command and it still doesn't work is there a time I can aim you?

bscbrit, my resolv.conf has "search" at the beginning.  Is that okay?  Also, the numbers have changed, but I have erased the numbers I can not ping.  Do you know what's going on?

---

### Post by mips on 2006-04-11
[QUOTE=nodyl]Mips, I disabled the ipv6 using the mv command and it still doesn't work is there a time I can aim you?

bscbrit, my resolv.conf has "search" at the beginning.  Is that okay?  Also, the numbers have changed, but I have erased the numbers I can not ping.  Do you know what's going on?[/QUOTE]

I have a new Dapper install and havent installed any messaging software yet. When I do I must remember my passwords...

Did you restart the PC after disabling IPv6 ?

What router (make&model) do you have ???

---

### Post by nodyl on 2006-04-11
I restarted.  Still doesn't work.  Also resolv.conf doesn't stay edited when I reboot.

I have a linksys befsx41

---

### Post by mips on 2006-04-11
Could you try it with a static IP address and see what happens ?

---

### Post by nodyl on 2006-04-11
it doesn't like that either

---

### Post by nodyl on 2006-04-11
perhaps this information will also be helpful:  under windows, I never had a problem connecting to the internet (lots of other problems, but not that one).  However, when I took the info off my computer, I used knoppix.  Knoppix could not access the internet through my computer either.  

As for the static ip, the same thing happens: I can ping by number, but not by name.

---

### Post by nodyl on 2006-04-12
I have resolved the issue.  In /etc/resolv.conf I took out everything except the last line and it worked.  Thank you everyone for your help.

---

