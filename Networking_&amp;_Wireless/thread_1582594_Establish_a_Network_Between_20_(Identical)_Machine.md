---
title: "Establish a Network Between 20 (Identical) Machines?"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-09-26
Hi All,

I am an Ubuntu newbie, and would greatly appreciate your help with the following:

I would like to set up a network that consists of 20 identical laptops (IBM Thinkpad T60), so that I could SSH from laptop X to laptop Y, run programs on laptop Y, copy files etc. 
 
What is the best / fastest way to do so? is it better to establish a wired network or a wireless one (all machines have a wifi card)?

Thanks,
cSharp.


P.S. all laptops are with the exact same hardware configuration, and empty hard drives (no OS is installed). I plan on installing Ubuntu on all of them.

---

### Post by BkkBonanza on 2010-09-26
Well, wifi is going to be the easiest - no cables. But wired is definitely faster.

If the main use is connecting to the internet and small file xfers, editing, browsing then wifi is plenty fast. 

When you start copying large multi GB files it sure is nice to have 1000 Gbit wired. You could use a combination of both depending on where you think you need more speed.

For wired ethernet you need a switch with a cable going to each laptop from the switch. Then a cable from switch to router. With wifi you just copy configs to each laptop and if lucky they'll all talk to the router. If it's going to be busy then the wifi could be limiting.

---

### Post by SeijiSensei on 2010-09-26
> **csharpplus said:**
> I would like to set up a network that consists of 20 identical laptops (IBM Thinkpad T60), so that I could SSH from laptop X to laptop Y, run programs on laptop Y, copy files etc. 

Perhaps you can tell us a bit about your purpose in devising this setup.  When you say "I" above, do you mean literally just you alone would be running programs on twenty different machines?  Or will you be supporting twenty different people of those machines and want all of them to be able to connect among themselves in the manner you describe?

The command 'ssh -X remote.example.com' builds a tunnel to enable you to run X-Windows programs on remote hosts and display the results on your local display.  (This is a long-standing feature of X-Windows; using ssh makes it easier to handler authentication.)  Try logging in to another machine with the -X switch, then running a lightweight X program like xterm from the remote command prompt.  You should see the xterm window appear on your screen.  (If it doesn't, type 'xhost +' on your *local* machine before running ssh to grant remotes access to your desktop.)

If you're thinking about some kind of parallel-processing application where you're using all 20 machines to perform some heavy computational task, you should look into [clustering]("https://help.ubuntu.com/community/Clustering") technologies like Beowulf.

So could you describe your purpose in a bit more detail?

---

### Post by csharpplus on 2010-09-26
> **BkkBonanza said:**
> Well, wifi is going to be the easiest - no cables. But wired is definitely faster.
 
If the main use is connecting to the internet and small file xfers, editing, browsing then wifi is plenty fast. 
 
When you start copying large multi GB files it sure is nice to have 1000 Gbit wired. You could use a combination of both depending on where you think you need more speed.
 
For wired ethernet you need a switch with a cable going to each laptop from the switch. Then a cable from switch to router. With wifi you just copy configs to each laptop and if lucky they'll all talk to the router. If it's going to be busy then the wifi could be limiting.
 
Thanks BkkBonanza. Since I don't need a shared internet connection (rather, transfer many files), the 'wired' solution would probably work better, as you suggest.

---

### Post by csharpplus on 2010-09-26
> **SeijiSensei said:**
> Perhaps you can tell us a bit about your purpose in devising this setup. When you say "I" above, do you mean literally just you alone would be running programs on twenty different machines? Or will you be supporting twenty different people of those machines and want all of them to be able to connect among themselves in the manner you describe?
 
The command 'ssh -X remote.example.com' builds a tunnel to enable you to run X-Windows programs on remote hosts and display the results on your local display. (This is a long-standing feature of X-Windows; using ssh makes it easier to handler authentication.) Try logging in to another machine with the -X switch, then running a lightweight X program like xterm from the remote command prompt. You should see the xterm window appear on your screen. (If it doesn't, type 'xhost +' on your *local* machine before running ssh to grant remotes access to your desktop.)
 
If you're thinking about some kind of parallel-processing application where you're using all 20 machines to perform some heavy computational task, you should look into [clustering]("https://help.ubuntu.com/community/Clustering") technologies like Beowulf.
 
So could you describe your purpose in a bit more detail?
 
First off, thank you SeijiSensei for your detailed reply.
 
My goal is to be able to run 20 different/independent applications on 20 machines. rather than physically move from one computer to another (and start an application, watch the results etc), I prefer to use one 'main' machine, access all other machines using 'SSH', run their intended application and see the results from within the 'main'. Once a day or so, I would also need to copy the output / results of these applications (10-20 [GBs] per machine) to a central hard drive for backup.
 
Given the above answer, it seems like a wired network is the way to go. 
 
Can you describe in more detail the actual process of building this network, from ubuntu's perspective? are there any special settings / configs I need to take care of (in addition to connecting the physical cables)?

---

### Post by BkkBonanza on 2010-09-27
In general it should be fairly straight forward. Unless you have special needs like booting from a OS image over the LAN to each machine. If not internet then you won't even need a router (for a single LAN). Just switch port to each machine.

It sounds like you're making a typical server farm. You may want to just use regular mainboards as that will be much cheaper and they'll run way, way faster than laptops as far as CPU processing. They don't even need cases - just power and hard disks. Or if not disk intensive then stick a USB flash stick in each one. I read a good article once about this being how Google built out their server farms because it was the very best bang for buck. You would cut your cost by half or double your CPU power easily.

They had rows of shelfs with bare mainboards hooked to power supplys, all networked together. You can fit a lot of systems, cheaply on a single shelf unit. They used Celerons at that time because they were best CPU/$$ at that time.

I'll see if I can google the article for you and add it here if I find it.

You will also likely want to explore pssh (parallel ssh) for executing the same commands at same time on multiple systems. You give it a file listing all IPs and then fire a command that gets done on every one.

Either assign static IPs to each machine or run **dnsmasq** on the "main" machine to auto-assign IPs using DHCP. Managing the tasks on all the machines is way more trouble than wiring them up.

Oh well, there's always the [Wikipedia]("http://en.wikipedia.org/wiki/Google_platform").

[Great photo]("http://www.vintage-computer.com/images/vcf8/debic.jpg")

[This]("http://news.cnet.com/8301-1001_3-10209580-92.html") isn't the one I read but it's interesting and more modern.

---

### Post by csharpplus on 2010-09-27
> **BkkBonanza said:**
> In general it should be fairly straight forward. Unless you have special needs like booting from a OS image over the LAN to each machine. If not internet then you won't even need a router (for a single LAN). Just switch port to each machine.
 
It sounds like you're making a typical server farm. You may want to just use regular mainboards as that will be much cheaper and they'll run way, way faster than laptops as far as CPU processing. They don't even need cases - just power and hard disks. Or if not disk intensive then stick a USB flash stick in each one. I read a good article once about this being how Google built out their server farms because it was the very best bang for buck. You would cut your cost by half or double your CPU power easily.
 
They had rows of shelfs with bare mainboards hooked to power supplys, all networked together. You can fit a lot of systems, cheaply on a single shelf unit. They used Celerons at that time because they were best CPU/$$ at that time.
 
I'll see if I can google the article for you and add it here if I find it.
 
You will also likely want to explore pssh (parallel ssh) for executing the same commands at same time on multiple systems. You give it a file listing all IPs and then fire a command that gets done on every one.
 
Either assign static IPs to each machine or run **dnsmasq** on the "main" machine to auto-assign IPs using DHCP. Managing the tasks on all the machines is way more trouble than wiring them up.
 
Oh well, there's always the [Wikipedia]("http://en.wikipedia.org/wiki/Google_platform").
 
[Great photo]("http://www.vintage-computer.com/images/vcf8/debic.jpg")
 
[This]("http://news.cnet.com/8301-1001_3-10209580-92.html") isn't the one I read but it's interesting and more modern.
 
 
BkkBonanza,
 
Thank you for your detailed reply. I learned a lot.
 
Assuming I use a switch to connect all the machines together. what is the easiest way to 'give a name' to each machine so that I could do things like:
 
'ssh machine1' --> this will 'ssh' into 'machine1'
'ssh machine2' --> this will 'ssh' into 'machine2'
'ssh machine3 --> this will 'ssh' into 'machine3'
 
I figure this would be easier than writing the whole ip address.  
 
also, can you recommend on a switch (say, with 8-ports) that works well with ubuntu?

---

### Post by BkkBonanza on 2010-09-27
For 20 machines you'll need either a 24 port switch or 3 x 8 port switches with cables between them (and this way you have no spare ports!). Probably the 24 port switch is better. Any switch will work fine with Ubuntu.

I was going to suggest a TrendNet switch but looking on Amazon (for good prices) they seem to only have 100 MBit for all ports and GBit on 2 ports (unless you spend $199 for the full GBit one). Well, any of the well known names will do fine. Read the ads carefully as they sure mix up the 100/1000 specs a bit. I've never used a 24 port one myself but I've had good success with the Trendnet 8-port Green series one. They had them on for $25 some time ago but they appear to be about $40 now. So 3 of those puts you in the same range as a $160 24 port switch. I couldn't say which is the better choice. This [Dlink]("http://www.amazon.com/D-Link-24-Port-Rackmountable-Gigabit-Switch/dp/B0002TPFTA/ref=sr_1_1?s=gateway&ie=UTF8&qid=1285597236&sr=8-1") one seems to have good reviews by many.

You can set the hostname on each machine. Whether you can use the names on other machines depends on if you configure DHCP with DNS functions, as suggested with dnsmasq ( a good idea ), or if not then enter names manually in /etc/hosts for each machine. Well, that's not so bad as you just copy the file to each one. But DHCP kind of makes this all painless and flexible. I'd recommend that.

BTW, if this isn't a "long term" project requiring you actually keep machines around for months/years, then you might look at running your tasks on [Amazon EC2]("http://aws.amazon.com/ec2/"). You can start 20 servers ("in the cloud"), get an ssh connection to each one, in a matter of minutes, run your apps, collect your data and be done with it. No need for buying anything - you just pay for hours used and data xfer'd in/out. I've used EC2 quite a bit so if you have questions about that just ask. Depending on how long your project runs that could be much cheaper and easier to get going too.

---

### Post by csharpplus on 2010-09-27
Thank you BkkBonanza for your continued help.
 
> 
You can set the hostname on each machine. Whether you can use the names on other machines depends on if you configure DHCP with DNS functions, as suggested with dnsmasq ( a good idea ), or if not then enter names manually in /etc/hosts for each machine. Well, that's not so bad as you just copy the file to each one. But DHCP kind of makes this all painless and flexible. I'd recommend that.

 
If I choose to enter the names manually (in ' /etc/hosts '), do I need a router or can I just use a switch?  can I then access any computer in the network by 'SSH COMPUTER_NAME'?

---

### Post by BkkBonanza on 2010-09-27
You can just use the switch. A router is for joining between two different networks. If you connect to the internet you need a router.

Make a hosts file with all the names+IPs, then copy it to every machine that needs to know other machines by name. When you use a name your system will look at the /etc/hosts and translate to an IP, then send out packets using the IP. This is the most simple way to do it.

---

### Post by csharpplus on 2010-09-27
> **BkkBonanza said:**
> You can just use the switch. A router is for joining between two different networks. If you connect to the internet you need a router.
 
Make a hosts file with all the names+IPs, then copy it to every machine that needs to know other machines by name. When you use a name your system will look at the /etc/hosts and translate to an IP, then send out packets using the IP. This is the most simple way to do it.
 
perfect. thank you, BkkBonanza.
 
the question now becomes: how do I know what is the ip address of every machine? will this ip address be permanent from the moment I create the network (plug the cables to the switch)?

---

### Post by SeijiSensei on 2010-09-27
> **csharpplus said:**
> the question now becomes: how do I know what is the ip address of every machine? will this ip address be permanent from the moment I create the network (plug the cables to the switch)?

Yes, if you configure each machine with a static address.  Otherwise you'd need to make one of them a DHCP server that the others would use to get their configurations.  You can then create a table in dhcpd.conf that maps from Ethernet MAC addresses to specific IPs so that each machine always gets the same IP address at boot.

---

### Post by BkkBonanza on 2010-09-27
When you install the OS on each machine you will give it an IP address. It doesn't get it from the switch or anywhere else, unless DHCP is running - then the DHCP server gives them out according to the config settings you set.

Just choose a normal range like 192.168.0.1 .. 192.168.0.20 and sequentially set each machine. If you're cloning from one master OS image then you'll need to make sure each one gets a different IP. It's usually set in the /etc/network/interfaces file.

---

### Post by csharpplus on 2010-09-27
BkkBonanza, SeijiSensei,
 
Thank you so much for your help. It is greatly appreciated!

---

### Post by csharpplus on 2010-09-27
BkkBonanza, SeijiSensei,
 
I just thought of the following: there is a chance I might be interested to install condor as well. given your expertise, which 'configuration route' {DHCP / static IPs} would work best?
 
Would both be OK for condor?

---

### Post by BkkBonanza on 2010-09-27
I had to go look up Condor... but a brief read indicates it likely won't matter whether you use static or dynamic addresses. But I've never used it.

DHCP is going to make life easier if you add/remove computers fairly often.

---

### Post by csharpplus on 2010-09-28
Thanks!

---

### Post by caseman7 on 2011-01-12
Hey all - on the topic of linking a gazillion computers together:

Just wondering if any of you could guide me to some answers to a simple  question: I am fascinated with the concept of Beowulf clusters, and would  like to build one. I have read a lot of material on the subject, but  can't find any solid information on applications/software that one can  use on the beowulf setup. What I mean is: is there any way to have a  beowulf (or similar cluster) utilize/run regular linux software (such as  blender, kino, audacity etc.) for processor/memory heavy tasks, or does  one have to utilize software/programs specifically designed to run in  paralell computing environments? If the latter is the case, is there a  list or repository somewhere that showcases the available software?

Sorry to thow this question in if this is the wrong place to do so, but seeing the thread topic is quite similar I thought one of you you may be able to point me in the right direction?

Cheers, 

Casey

---

