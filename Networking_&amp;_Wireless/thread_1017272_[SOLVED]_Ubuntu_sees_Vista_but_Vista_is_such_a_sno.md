---
title: "[SOLVED] Ubuntu sees Vista but Vista is such a snob (wired internet sharing)"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by cabbiinc on 2008-12-20
EDIT ---- To save someone some reading I'll give the single most useful hint here. Create a restore point in Vista before you start so you have something to fall back on if things go awry.
In Vista, click Start > Network > click Network and Sharing Center > click Manage Network Connections > 
Now, on my screen I can see the DSL modem and the two connections that I want to bridge , and a thing that says Network Bridge. Right click on one of the two ports you want to bridge and "Add to Bridge". Do the same to the other port.
Now, right click on the bridge icon > Properties. You should see both your connections, make sure they are checked and click "configure..."
Click the driver tab > update driver > search online for a better driver. If your lucky it will find one. For me M$ found an unsigned driver so I installed it. That made everything work for me once I had everything else configured. It simply refused to work until I had the updated driver installed. 
END EDIT



Hello, and apologies if this topic gets covered a lot.

I have installed Ubuntu onto an older computer that I built and I am trying to network it through my Vista computer. Ubuntu has finally seen Vista but Vista acts as if it's not even there. I've even gone so far to disable my firewall on the Vista machine and no dice.

I did have the older computer networked to my wifes XP computer. My older computer had Win 98se on it at the time. This is using the same cable and nic card.

I've read forums and elsewhere for 3 days and am more confused than when I started. I see a whole lot of posts simply stating "run Samba". While I'm sure that's what needs to be done the poster never actually says "run Samba on the Ubuntu computer". :confused: 

Any help at all would be greatly appreciated.

---

### Post by albinootje on 2008-12-20
> **cabbiinc said:**
> 
I have installed Ubuntu onto an older computer that I built and I am trying to network it through my Vista computer. Ubuntu has finally seen Vista but Vista acts as if it's not even there. I've even gone so far to disable my firewall on the Vista machine and no dice.

You tried -> Places -> Connect to server ?
Or what did you do ?

---

### Post by cabbiinc on 2008-12-20
> **albinootje said:**
> You tried -> Places -> Connect to server ?
Or what did you do ?

Ok, I clicked Places -> Connect to server, but I don't know what protocol to try to connect under.

---

### Post by albinootje on 2008-12-20
> **cabbiinc said:**
> Ok, I clicked Places -> Connect to server, but I don't know what protocol to try to connect under.

"Windows share"

---

### Post by cabbiinc on 2008-12-20
Ok, I clicked "Windows Share" and put in my Vista's name. Now I can see the Vista computer under places and I can see the files too, but still no internet. Do I need to configure Firefox? Is there something special about Vista that I need to do that doesn't require explosives?

---

### Post by jerome1232 on 2008-12-20
How is your network setup? If this is a typical setup and you can access local networking services you should be able to reach out to the internet.

does pinging work?

Application-Accessories-Terminal; type "ping -c 2 google.com" without the quotes

---

### Post by albinootje on 2008-12-20
> **cabbiinc said:**
> Ok, I clicked "Windows Share" and put in my Vista's name. Now I can see the Vista computer under places and I can see the files too, but still no internet. Do I need to configure Firefox? Is there something special about Vista that I need to do that doesn't require explosives?

Ah, okay.
Please start a new thread with a proper title (Something like "Giving internet access to an Ubuntu machine through a Vista machine.) describing your setup, and the things that you'd like to achieve.

GL!

---

### Post by cabbiinc on 2008-12-20
> **jerome1232 said:**
> How is your network setup? If this is a typical setup and you can access local networking services you should be able to reach out to the internet.

does pinging work?

Application-Accessories-Terminal; type "ping -c 2 google.com" without the quotes

Pinging Google returns an unknown host error.

---

### Post by cabbiinc on 2008-12-20
> **albinootje said:**
> Ah, okay.
Please start a new thread with a proper title (Something like "Giving internet access to an Ubuntu machine through a Vista machine.) describing your setup, and the things that you'd like to achieve.

GL!

Vista still refuses to acknowledge that the Ubuntu machine even exists. i.e. the snob reference of the title.

---

### Post by jerome1232 on 2008-12-20
> **cabbiinc said:**
> Vista still refuses to acknowledge that the Ubuntu machine even exists. i.e. the snob reference of the title.

Well you probably don't have a samba server installed and working, Try to share a file that will get it installed, once it's installed then try sharing a file again it should start working.

ps to share a file just right click a file/folder and select sharing options, then enable the sharing.

---

### Post by jerome1232 on 2008-12-20
> **cabbiinc said:**
> Pinging Google returns an unknown host error.

Try "ping -c 2 74.125.19.103", that's google's ip address.

If that doesn't work can you post the output of 

```
ifconfig
route
```

If it does work then please post the output of (that means internet is working; just dns isn't)
```
cat /etc/resolv.conf
```

---

### Post by cabbiinc on 2008-12-20
> **jerome1232 said:**
> Well you probably don't have a samba server installed and working, Try to share a file that will get it installed, once it's installed then try sharing a file again it should start working.

ps to share a file just right click a file/folder and select sharing options, then enable the sharing.

Ok, I did that and get a "Sharing services are not installed" error. When I check either the NFS or Samba service or both the same error pops up.

---

### Post by jerome1232 on 2008-12-20
> **cabbiinc said:**
> Ok, I did that and get a "Sharing services are not installed" error. When I check either the NFS or Samba service or both the same error pops up.

oh yeah right, your not connected to the internet thus it won't let you download and install samba (which allows you to create windows shares)

We will need to get you online before we can continue with the samba installation.

---

### Post by cabbiinc on 2008-12-20
> **jerome1232 said:**
> oh yeah right, your not connected to the internet thus it won't let you download and install samba (which allows you to create windows shares)

We will need to get you online before we can continue with the samba installation.

I already have Samba downloaded to this computer, I then put it on a thumb drive and tried to put it on the Ubuntu computer but it already appeared to be there.

I can download files to this computer and take them to Ubuntu.

---

### Post by cabbiinc on 2008-12-20
> **jerome1232 said:**
> Try "ping -c 2 74.125.19.103", that's google's ip address.

If that doesn't work can you post the output of 

```
ifconfig
route
```

If it does work then please post the output of (that means internet is working; just dns isn't)
```
cat /etc/resolv.conf
```

[IMG]http://farm4.static.flickr.com/3096/3124463882_4c004b2f11_o.jpg[/IMG]

This is the screenshot I came up with.

---

### Post by cabbiinc on 2008-12-21
(Bump, I hate doing that but you know).

So today I wake up, turn on the computers and now neither is seeing each other. What's up with that?

---

### Post by cabbiinc on 2008-12-21
So what do I need to do to get internet through the Vista computer?

I have Samba, how do I configure it?
What do I need to do on the Vista computer?

---

### Post by dacorr on 2008-12-21
are you trying to use the vista machine as a gateway to the internet for the ubuntu machine?

if so you will need to set the ubuntu machine network settings to use the vista machines IP as its default gateway

Dac

---

### Post by cabbiinc on 2008-12-21
> **dacorr said:**
> are you trying to use the vista machine as a gateway to the internet for the ubuntu machine?

if so you will need to set the ubuntu machine network settings to use the vista machines IP as its default gateway

Dac

Yes, I would like to use Vista as a gateway. If I can only use the Ubuntu machine to surf the web and not be able to file share with Vista I am ok with that. I can always email whatever I need to do.

How do I get the Vista machines IP? And which IP do I use, the one going to the modem or the nic card to the Ubuntu machine?

---

### Post by jerome1232 on 2008-12-21
> **cabbiinc said:**
> (Bump, I hate doing that but you know).

So today I wake up, turn on the computers and now neither is seeing each other. What's up with that?

----edit---- if you are using Vista as the gateway then most of this is wrong, make sure you have ICS turned on in the vista machine and everything should just work.

Based on what I'm looking at your not getting an ip address. Your computer is just assigning itself one. You don't have a default route or anything.

Possibly try staticly assigning your information?
Right click you network applet, select edit connections, Select your connection in there (auto eth0) and select edit, click on the IPv4 settings tab, in the "method" drop down box select manual, click add, 

(now I'm assuming that since I see a nameserver of 192.168.0.1 that your router is acting as a caching dns server for you, so I'm assuming these numbers based on your router being 192.168.0.1, hopefully I'm right)
for an address type in 192.168.0.43   netmask would be 255.255.255.0    gateway 192.168.0.1

dns servers will be the same as you see for name servers in that screenshot you have up there. Ok out of everything and see if you can connect.

---

### Post by dacorr on 2008-12-21
does the vista machine directly connect to the modem or via a router?

---

### Post by cabbiinc on 2008-12-21
> **dacorr said:**
> does the vista machine directly connect to the modem or via a router?

No, the Vista machine is plugged directly into an Actiontec GT701 via USB cable. The Ethernet cable from the Vista machine is running to the Ubuntu machine via a 50' crossover cable.

So to sum up:
Actiontec DSL modem -> Vista -> Ubuntu

---

### Post by Frak on 2008-12-21
> **cabbiinc said:**
> No, the Vista machine is plugged directly into an Actiontec GT701 via USB cable. The Ethernet cable from the Vista machine is running to the Ubuntu machine via a 50' crossover cable.

So to sum up:
Actiontec DSL modem -> Vista -> Ubuntu
You may want to instead swap to an ethernet method. 50' (15 metres) of USB cable is 10 metres too long without an active repeater. Ethernet (cat5, cat5e, and cat6) can span to 300ft with no ill-effects.

---

### Post by cabbiinc on 2008-12-21
> **jerome1232 said:**
> ----edit---- if you are using Vista as the gateway then most of this is wrong, make sure you have ICS turned on in the vista machine and everything should just work.

Based on what I'm looking at your not getting an ip address. Your computer is just assigning itself one. You don't have a default route or anything.

Possibly try staticly assigning your information?
Right click you network applet, select edit connections, Select your connection in there (auto eth0) and select edit, click on the IPv4 settings tab, in the "method" drop down box select manual, click add, 

(now I'm assuming that since I see a nameserver of 192.168.0.1 that your router is acting as a caching dns server for you, so I'm assuming these numbers based on your router being 192.168.0.1, hopefully I'm right)
for an address type in 192.168.0.43   netmask would be 255.255.255.0    gateway 192.168.0.1

dns servers will be the same as you see for name servers in that screenshot you have up there. Ok out of everything and see if you can connect.

I changed the adress to 192.168.0.1, netmask to 255.255.255.0, and gateway to 192.168.0.1 on the Ubuntu machine. I tried to ping -c 2 74.125.19.103 and it returned no packets.

---

### Post by cabbiinc on 2008-12-21
> **Frak said:**
> You may want to instead swap to an ethernet method. 50' (15 metres) of USB cable is 10 metres too long without an active repeater. Ethernet (cat5, cat5e, and cat6) can span to 300ft with no ill-effects.

It is a cat5 cable with the appropriate wires switched to make it a crossover cable. I used to use this same cable in a different setup and it worked well there(win 98se to XP), although I didn't have high speed internet at the time. With dialup, its all slow to begin with right.

---

### Post by cabbiinc on 2008-12-21
And I have tried multiple times to turn on ICS in the Vista machine, always returns with an 

"Network error
Windows has detected an IP address conflict

Another computer on this network has the same IP address as this computer. Contact your network administrator for help resolving this issue. More details are available in the Windows system event log."

I don't know how to view the event log or I would post that as well.

---

### Post by Frak on 2008-12-21
> **cabbiinc said:**
> It is a cat5 cable with the appropriate wires switched to make it a crossover cable. I used to use this same cable in a different setup and it worked well there(win 98se to XP), although I didn't have high speed internet at the time. With dialup, its all slow to begin with right.
Aye, sorry, I thought you were stating you had a crossover USB cable running from your Vista box to your Ubuntu box =X.

---

### Post by cabbiinc on 2008-12-21
> **Frak said:**
> Aye, sorry, I thought you were stating you had a crossover USB cable running from your Vista box to your Ubuntu box =X.

It's probably my fault for calling it a crossover cable and not a cat5 crossover cable. You didn't used to have to differentiate the two until recently thanks to M$ and Vi$ta.

---

### Post by Frak on 2008-12-21
> **cabbiinc said:**
> And I have tried multiple times to turn on ICS in the Vista machine, always returns with an 

"Network error
Windows has detected an IP address conflict

Another computer on this network has the same IP address as this computer. Contact your network administrator for help resolving this issue. More details are available in the Windows system event log."

I don't know how to view the event log or I would post that as well.
Is Vista acting as a DHCP server for the Ubuntu box? You may also want to type "winipcfg" into search/run and click Release All, and then click Renew All.

EDIT
Just thought, Windows doesn't provide a DHCP server. You may have to configure the IP address statically (the range of 192.168.0.2 to 192.168.0.254)

---

### Post by cabbiinc on 2008-12-21
> **Frak said:**
> You may have to configure the IP address statically (the range of 192.168.0.2 to 192.168.0.254)

How do I do that? And to which machine should I do it too?

---

### Post by Frak on 2008-12-21
> **cabbiinc said:**
> How do I do that? And to which machine should I do it too?
Leave the Vista machine as it is, but on the ubuntu box, go to the network manager and specify an IP address. Make sure the ip range is within the one I specified.

---

### Post by cabbiinc on 2008-12-21
> **Frak said:**
> Leave the Vista machine as it is, but on the ubuntu box, go to the network manager and specify an IP address. Make sure the ip range is within the one I specified.

On the Ubuntu machine settings are:

IP address: 192.168.0.43
Subnet mask: 255.255.255.0
Gateway address: 192.168.0.1

Still no dice.

I'm pretty sure that we have the Ubuntu machine set properly. I still can't get Vista to share anything anywhere. I can't get it to start the ICS. I can't get it to see the Ubuntu machine, or even recognize there's even something on the end of the cable. The Ubuntu machine can see Vista though.

---

### Post by cabbiinc on 2008-12-21
On the Vista machine I just tried pinging all addresses from 192.168.0.0 to 192.168.0.255. The only 2 that returned were 192.168.0.1 (dsl modem) and 192.168.0.3 (Vista itself). I didn't get a ping return from the Ubuntu machine.

I am running with no firewall right now on the Vista machine as well.

---

### Post by jerome1232 on 2008-12-21
I'm willing to bet the reason Vista won't turn on ICS (which makes it a dhcp server and internet gateway) is that Vista is trying to give itself the ip address 192.168.0.1 and the modem already has that address, hence the conflict. No idea how to work around it unless the modem can switch it's internal ip address.

---

### Post by cabbiinc on 2008-12-21
> **jerome1232 said:**
> I'm willing to bet the reason Vista won't turn on ICS (which makes it a dhcp server and internet gateway) is that Vista is trying to give itself the ip address 192.168.0.1 and the modem already has that address, hence the conflict. No idea how to work around it unless the modem can switch it's internal ip address.

You know, it just dawned on my that this is what the problem was. Every time I try to initiate ICS it comes up with a warning that it's going to changes Vista's IP to 192.168.0.1. I didn't make the connection until I did the ping test (pingtest.exe found at MajorGeeks.com). I'll try to see what I can do about this.

---

### Post by jerome1232 on 2008-12-21
On Vista pop open your favorite web browser and delete anything in the address bar, then type in [http://192.168.0.1](http://192.168.0.1), that should either bring you to a Web Interface for your modem or ask you for a Username and Password, then bring you to the Web Interface. Have a poke around and see what you can see.

---

### Post by cabbiinc on 2008-12-21
> **jerome1232 said:**
> On Vista pop open your favorite web browser and delete anything in the address bar, then type in [http://192.168.0.1](http://192.168.0.1), that should either bring you to a Web Interface for your modem or ask you for a Username and Password, then bring you to the Web Interface. Have a poke around and see what you can see.

Ok, so I went in and poked around and changed the IP address of the modem to 192.168.0.2, my wifes XP computer is set to 192.168.0.4 using the ethernet port on the modem, my Vista computer is set to 192.168.0.3 using the USB port on the modem, and the Ubuntu is set to 192.168.0.43 using the LAN port. Vista still comes up with a generic error when trying to start ICS. 

I even tried starting it in the services.msc file. It starts then stops imediately saying that some services will stop when not in use. ](*,) It'd be more gratifying to just whack my head into a wall.

While trying to start the ICS through the Network and Sharing Center > USB connection I get the message "An error occurred while ICS was being enabled." ](*,) Thanks for the detailed info Vi$ta.

---

### Post by cabbiinc on 2008-12-21
This couldn't be something as simple as plugging the ethernet cable in backwards is it? I mean the plug can only go in one way, but what if I turned the cable around, put the Vista end into Ubuntu and the Ubuntu end into Vista.

I'd have to crawl into the attic to do it so what do you think?

---

### Post by jerome1232 on 2008-12-21
Won't have an affect. Doesn't matter which end goes where as long as they both go somewhere. 

I'd be ](*,) head too. So if I'm getting this right you have something like this

```
    
Ubuntu
  |
cat 5 (crossover)
  |
  |
vista---USB----DSL Modem-----cat 5------xp
```

I'm not entirely sure if this can work... Getting a router would sure make your life easier (I picked my netgear up at a thrift store for 7 bucks lol, it does great)

---

### Post by Frak on 2008-12-21
> **jerome1232 said:**
> Won't have an affect. Doesn't matter which end goes where as long as they both go somewhere. 

I'd be ](*,) head too. So if I'm getting this right you have something like this

```
    
Ubuntu
  |
cat 5 (crossover)
  |
  |
vista---USB----DSL Modem-----cat 5------xp
```

I'm not entirely sure if this can work... Getting a router would sure make your life easier (I picked my netgear up at a thrift store for 7 bucks lol, it does great)

Aye on the router. It would make this loads easier.

> **cabbiinc said:**
> While trying to start the ICS through the Network and Sharing Center > USB connection I get the message "An error occurred while ICS was being enabled." ](*,) Thanks for the detailed info Vi$ta.

In the attempt to lighten spirits

[IMG]http://failblog.wordpress.com/files/2008/11/fail-owned-vista-dns-fail.jpg[/IMG]

EDIT
Question, have you bridged the USB and Ethernet connections?

---

### Post by cabbiinc on 2008-12-21
Yep, you have it right. But I see that others get it to work, and I already have all this and was just hoping to get it going.

I've tried it bridged and not bridged.

---

### Post by cabbiinc on 2008-12-21
Update, after a few hours of ](*,) I went into Device Manager on the Vista machine and asked Window$ to check for updates on the Mac Bridge. It came back with an unsigned new driver so I installed it (note to anyone reading this, create a restore point before doing this). Now I can ping the Ubuntu computer but still can't "see" Ubuntu on the Vista computer.

Oh wait, it now works!!! \\:D/ \\:D/

---

### Post by jerome1232 on 2008-12-21
Gratz! So I take it the file sharing and everything is working now? If so don't forget to mark as solved. (Thread tools)

---

### Post by cabbiinc on 2008-12-22
> **jerome1232 said:**
> Gratz! So I take it the file sharing and everything is working now? If so don't forget to mark as solved. (Thread tools)

Well I still don't have file sharing.

But thank you thank you thank you all for sticking with me.

---

### Post by Frak on 2008-12-22
Hooray :)

---

