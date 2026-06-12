---
title: "ADSL howto??"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by notepad on 2005-12-10
i see a lot of people saying they cant get their ubuntu system online with adsl in various forums but im not finding any answers (i have found a few people saying yay my adsl works on ubuntu and not saying how they did it). i am trying to connect to internode using roaring penguin. internode supports both pppoe and pppoa and recommends using roaring penguin.

roaring penguin is installed and configured and running pppoe-start doesnt seem to do anything. ive tried running pppoe-start after configuring eth0 to use dhcp, and ive tried running pppoe-start after configuring eth0 to use a static ip address (192.168.0.1). ive also tried it after running ifdown eth0. no matter what i try i cant get this system to connect. i am running win xp on the same machine and it connects no problems.

any ideas?

---

### Post by BobSongs on 2005-12-10
I don't know how much this will help. But here goes.

I posted [this thread]("http://www.ubuntuforums.org/showthread.php?t=92036") a couple weeks back when setting up my friend's PC with Edubuntu.

This is his situation. PC + highspeed modem and no router. So his solution was to use the command-line **pppoeconf**. It's a wizard of sorts. And it required a restart. Now, I'm new to Ubuntu. But an occasional reboot isn't a bad thing.

Cheers, mate.

---

### Post by mips on 2005-12-10
The thing that I dont get is a lot of people use broadband router style devices with an ethernet port. These devices will do the PPPoE & authentication and a lot of other things for you so why even use PPPoE ???

I dont see the point in offloading the PPPoE stuff from a router to the PC. You are using more of your PCs resources, why ?

Sure people with a modem dont have a choice but the rest have no need for PPPoE and are just complicating their lives...

---

### Post by BobSongs on 2005-12-10
> **mips]The thing that I dont get is a lot of people use broadband router style devices with an ethernet port. These devices will do the PPPoE & authentication and a lot of other things for you so why even use PPPoE ???.[/QUOTE]

When highspeed connections were finally accessible to mere mortals the setup was basically a network card and high speed dialer, period. (Routers were astronomically priced said:**
> Hence this post.[/URL])

Today I imagine most folks are opting for the more expensive setup which includes router. That's fine because it's an immediate connection and lower overhead on the processor/RAM. But there's no GUI assistance for those who have the more basic setup. And when that's the case it's no fun hunting up and down the menus looking for something similar to what XP offers. Agreed?

[QUOTE=mips]I dont see the point in offloading the PPPoE stuff from a router to the PC. You are using more of your PCs resources, why ?
It's cheaper. "A PC is a hole into which one continually pours money." However some people believe once they buy their basic machine... they don't need to spend any more. Weird, eh? ;) 

So, **notepad**, did my link help?

---

### Post by mips on 2005-12-10
Some very valid points there. I nearly got a USB modem as well at one stage as they are cheap but decided it is worth it to cough up a bit more.

I was referring more to people that already have routers trying to get them running via PPPoE. I suppose not everybody knows/understands the difference when it comes to the modem/router side of things as it is just a 'box' to get onto the net.

---

### Post by BobSongs on 2005-12-10
[QUOTE=mips]Some very valid points there. I nearly got a USB modem as well at one stage as they are cheap but decided it is worth it to cough up a bit more.

I was referring more to people that already have routers trying to get them running via PPPoE.[/QUOTE]
:oops: Ah. Well. On that point I'd agree. I was mistaken in thinking you were wondering why someone would opt for an inferior system. And quite honestly the dsl thing here in Canada started off with suppliers having a grip on product sales. And the sure gouged us. But since their start deregulation has occured and now parts are cheap at the local FutureShop.

:rolleyes: Today the reasons for a bad setup are not as convincing. A PC is a rich man's toy, in my opinion. Arguably some need to use it from time to time. But it's forever demanding new software or hardware. And in 5 years a system is so hideously behind the times that it gets swapped out for a new one.

[QUOTE=mips]I suppose not everybody knows/understands the difference when it comes to the modem/router side of things as it is just a 'box' to get onto the net.[/QUOTE]
True. But router instructions are fairly basic these days. Great big sheets included in the box make even the "PC challenged" able to set one up within an hour.

Your response is valid. I'll be more careful before I load my elephant gun next time.

;)

---

### Post by notepad on 2005-12-13
thanks for the link bob it looks good. ill see if i can get the machine to connect this weekend.

ive just found an adsl linux howto suggesting to configure a static address of 10.0.0.1 on eth0. of course! that makes perfect sense considering the address of the modem is 10.0.0.138. im keen to give that a bash. i might even remember to let you know how it goes.

---

### Post by BobSongs on 2005-12-15
Fabulous. I await your response.

Cheers, mate

Bob

---

### Post by runlevel0 on 2005-12-15
ADSL is fairly easy. The best bet on *any* OS, either Win, Linux, BSD or Mac... is a router. 

There are many routers in the market which serves as both USB modems or router. A good choice is the Alcatel Speedtouch, which have a good support at kernel level if you want to use it as a modem.

Using it as a modem, normally doesn't requiere any special setup, just check that the PPPoE module is loaded 

```

modprobe pppoe

```

The rest of the setup can be done from either network setup GUI in Gnome (Preferences: Network) or KDE (Sistem config icon on the panel).

It could happen that your USB Modem is not propperly supported (they normally are, but there are exceptions) and you have to tamper with settings or even have to recompile the kernel. In the case of the Speedtouch thgis is not necessary, but I can only speak for what I know.

Things get even easier if you use a router(or setup your modem/router as the latter): Just switch it to your network, open a browser and type [http://IP_OF_YOUR_ROUTER](http://IP_OF_YOUR_ROUTER) (normally it0s 192.168.1.1). Then a login widget will pop up. You need to know the default password and login name.  And remember that the first thing you must do once inside the router's interface is changing your user and password (the settings from the shelf use logins and passwords such as '1234' '1234', and that's known to the hackers).

That's all, your router will do the DNS stuff and even run a DHCP server, so that you can open KDE's Sistem Config > Network > Network settings, select DHCP from the dropdown menu and let your OS do the rest. In this case you won't need to set anything on the router, as it already knows what to do with the settings his own DHCP server gave you.

So that's all, basically. Setting up DSL is so darn easy that nobody cares to write howto's or stuff the like. It's mor difficult to explain than to do. ;)

---

### Post by Ruskie on 2005-12-16
After a lot of tries, I managed to get pppoe "quite" stable, meaning that I don't have to run pppoeconf every reboot. The change happened when I changed the line:
*From:* ```
iface eth0 inet dhcp
```
*To:* ```
iface eth0 inet manual
```
Yet something is not clear to me because, actually, I do have dynamic ip address with my provider...
However, the most weird thing is that now pppoe runs without configuring it everytime but... only the 2nd time I launch it!!! I.e., I run "sudo pon dsl-provider", it loads pppoe module... and not internet, as you can say from plog in which you don't have your ip and you DNSs listed.
Then I do "sudo poff" and "sudo pon dsl-provider" again and voil&#224;! Internet is magically there! How can this be explained? How can I convince pppoe to do the trick on first trial???

Thank you Marco

---

### Post by runlevel0 on 2005-12-16
[QUOTE=Ruskie] Then I do "sudo poff" and "sudo pon dsl-provider" again and voil&#224;! Internet is magically there! How can this be explained? How can I convince pppoe to do the trick on first trial??? Thank you Marco[/QUOTE] I was going to tell you that it was a permissions problem, but it seems that the only thing that is missing is to load the module at startup. Try this : ```
 modprobe pppoe 
pon dsl-provider 
``` If this is what fails, you can laod the module at startup simply by adding it to your /etc/modules file and running modules-update. That should work if the problem was the module.

---

### Post by Ruskie on 2005-12-16
Thanks, I tried and yes, you were damn right! :)
The only thing is that modules-update in my installation is reversed to update-modules, but now it works perfectly.
Muchas gracias!!!

---

### Post by notepad on 2005-12-18
i finally had a chance to try configuring adsl again today and im still having no luck. ive enabled eth0 and set a static address of 10.0.0.1 with a subnet mask of 255.255.255.0.

i uninstalled roaring penguin and opted to try using pppoeconf instead. pppoeconf scans eth0 for an access concentrator and presumably finds one and continues with the configuration process asking me if its okay to modfy certain config files blah blah.

pon dsl-provider returns this bizarre output about rp-pppoe.so loaded (does your pon return that nonsense?) and plog says chap authentication failed. needless to say the machine gives me no internet. how hard can it be?

---

### Post by runlevel0 on 2005-12-18
[QUOTE=notepad]
pon dsl-provider returns this bizarre output about rp-pppoe.so loaded (does your pon return that nonsense?) and plog says chap authentication failed. needless to say the machine gives me no internet. how hard can it be?[/QUOTE]

It's quite simple: 
> 
chap authentication failed


This means that you missed to configure the login name and password or that the authentification mode of your ISP is not CHAP. Normally it's just a question of pass and login, but it could also happen, that yout ISP uses PAP instead of CHAP (It's normally PAP).

Before tampering with the ppp-deamon settings, try again using the proper authentification configuration.

Edit the files 
[COLOR="DarkOrchid"]
/etc/chap-secrets
/etc/pap-secrets
[/COLOR]

That's how they look like:

[COLOR="DarkOrchid"]_/etc/pap-secrets_[/COLOR]
```

#account        remote          password        IP address list
YOUR_USER           *             YUORPASS

```

[COLOR="DarkOrchid"]_/etc/chap-secrets_[/COLOR]
```

#remote         local           secret          IP address list
YOU                 ISP        YOURPASS       10.10.10.2
ISP                   YOU       ISP-PASS         10.10.10.1

```

I can't recall now if the starting script tries to test whether to use PAP or CHAP, thus try writing the /etc/pap-secrets file.
Ask again if it doesn't work, as we already have found the root of the problem the next step to take is twaeking the pppd.

---

### Post by douwe flinx on 2005-12-20
I'm new on this forum, but I see one thing: there is a question: how do I get my ethernet working, and ther's a whole lot of talking about broadband, ethernet, modems and routers, but no answer to the question.
I have the same problem, since about eight days I've been trying to get Ubuntu connect the internet via my smc ethernet card (the one with ADM chips (tulip)). It starts going wrong with the installation of Ubuntu (5.10, for pc) the setup doesn't recognize the card, but sees a Firewire adaptor, wich isn't installed. Afterwards the card is seen, but renamed to Linksys nc 100 ethernet everywhere fast ethernet, but doesn't work.
I had several suggestions from the dutch panel, but nothing was a solution, that's a pity, because no internet means no linux, for you need to contact for everything you want to do .

---

### Post by runlevel0 on 2005-12-20
[quote=douwe flinx]I'm new on this forum, but I see one thing: there is a question: how do I get my ethernet working, and ther's a whole lot of talking about broadband, ethernet, modems and routers, but no answer to the question.[/quote] 

Hmmm sorry.

I was answering to another poster and oversaw your question.

I need some info about your card: the problem is, like in Rusky's question, probably related to your card's module.
'Happy Meal' cards have some strings attached and even Windows would get a headache where it not for the drivers being shipped.

What I need to know is which card you are exactly using, specially if it's a PCMCIA card.

There are at least 6 drivers for smc cards. You can also try one by one and see which one fits.
To load a module (drivers) use the command *modprobe*, to ease things, here''s a list of commands to try:

```

sudo modprobe smc-mca
sudo modprobe smc-ultra
sudo modprobe smc-ultra32
sudo modprobe smc9194

```

If your card is a PCMCIA card you must use this command

```

sudo modprobe smc91c92_cs

```

(Also check that PCMCIA is working)

You can safely load all the modules I told you, as the kernel will only use the one that fits.
Once you have the module/s loaded, try first to restart your network:

```

sudo /etc/init.d/network restart

```

Now first try to see if your network is up and has an assigned IP, a gateway, etc...
```

ifconfig

```

If it is, try pinging Google or your ISP's website to see if you can connect.

If this doesn't work, I would need more info to see what's happening.
to debug this correctly, you could provide us with the output of the boot log.

Do this shortly after booting:

```

dmesg > boot_log.txt

```

This sends the output of dmesg to a file. Copy this file to a Windows partition, so that you can paste it in this forum, and we will see if we can do something in an easy way or we need to recompile the kernel.

---

### Post by douwe flinx on 2005-12-21
thanks so far, I'm going to try al these  options (until one works, of course
:D) and I'll let you know what happened!

---

### Post by douwe flinx on 2005-12-22
Well, here I am. I tryed the suggestions, and here are the results                    .
Excactly: nothing. I'll copy what ubuntu told me:


paulus@ubuntu:&#8209;$ sudo modprobe smc&#8209;mca
FATAL: Error inserting smc&#8209;mca (/lib/Modules/2.6.12&#8209;9&#8209;386/kernelldrivers/netlsmc &#8209;mea.ko): No
such device or address
paulus@ubuntu:&#8209;$ sudo modprobe smc&#8209;ultra
FATAL: Error inserting smc&#8209;uitra (/liblmodules/2.6.12&#8209;9&#8209;386/kernelldrivers/netls mc&#8209;ultra.ko): No
such device or address
paulus@ubuntu:~$ sudo modprobe smc9194
FATAL: Error inserting smc9194 (/liblmodules/2.6.12&#8209;9&#8209;386/kernelldrivers/netlsmc 9194.ko): No
such device
paulus@ubuntu:&#8209;$ sudo modprobe smc&#8209;ultra32
FATAL: Error inserting smc &#8209; uitra32 (/liblmodules/2.6.12&#8209;9&#8209;386/kernelldrivers/net Ismc&#8209;ultra32.ko):
No such device or address
paulus@ubuntu:~$ sudo /etc/init.d/network restart
sudo: /etc/init.d/network: command not found
paulus@ubuntu:&#8209;$ ifconfig
lo      Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet6 addr: ::11128 Scope:Host
         UP LOOPBACK RUNNING MTU: 16436 Metric: 1
         RX packets:9182 errors:0 dropped:0 overruns:0 frame:0
         TX packets:9182 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
        RX bytes: 1190824 (1.1 MiB) TX bytes: 1190824 (1.1 MiB)
__________________________________________________________

paulus@ubuntu:&#8209;$ ifconfig

lo	Link encap:Local Loopback
	inetaddr:127.0.0.1 Mask:255.0.0.0
             inet addr: A1128 Scope:Host
             UPLOOPBACKRUNNING MTU:16436 Metric:1
             RX packets: 11812 errors:0 dropped:0 overruns:0 fl&#8209;ame:0
             TX packets: 11812 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:2196208 (2.0 MiB) TX bytes:2196208 (2.0 MiB)

The output of the logfile is far to big to send to the forum. (five sheets of A4)
If you need them to give me some help please let me know.

---

### Post by daibak on 2005-12-22
[EDITED Fri, 2005-12-23 following next cold boot into Ubuntu 5.10 Breezy Badger
 having done this before switching notebook off last night.
 In a terminal I typed

 sudo gedit /etc/modules

 to add this line to that file

 pon dsl-provider

 then saved changed /etc/modules file and in terminal typed

 sudo update-modules

 When Breezy launched today I was able to launch Firefox browser already connected to the Internet without    further ado. In other words, the make sticky solution is exactly that set out by runlevel0 in above post#11 provided you substitute his modules-update command with correct

sudo update-modules

command in Breezy.
Hope this helps and a big thank-you to runlevel0.]

runlevel0,

With a new Breezy Badger install on this HP Pavilion, with kernel updated to 2.6.12-10-386, I'm having to type sudo pppoeconf command each time I reboot to connect to the Internet with my D-Link ADSL modem. How can I make this stick before I disconnect so that connecting is automatic next time I boot up Linux?

Please detail exactly what I need to type as root in terminal to do what you suggested earlier
```
If this is what fails, you can load the module at startup simply by adding it to your /etc/modules file and running modules-update.
```

Thanks very much. FYI, it's eth0 and DHCP with password and works just fine.

---

### Post by rajaiskandarshah on 2005-12-22
what is the model for the dlink adsl modem ? if it uses ethernet rj45 cable, most likely you can configure the modem from a bridge (which requires pppoeconf) to a router (which means just turn on the modem then connect the ethernet cable to your computer). check how to get to the web based configuration tool (this will also test the connection between your computer's ethernet card and the modem)

other things to also note is to setup the router for dhcp and ubuntu network settings for your isp's primary and secondary dns.

you can probably make use of some of the notes i made for setting up an aztech adsl modem based on a malaysian isp:
[http://ubuntuforums.org/showthread.php?t=106847](http://ubuntuforums.org/showthread.php?t=106847)

---

### Post by ShirishAg75 on 2005-12-23
need to read this whole thread. I've a working ethernet ADSL connect to the net, thanx to a friend but would like to understand what he has done. Would post the gory details later.

---

### Post by ShirishAg75 on 2005-12-23
Hi all,
        Read the whole thread. I have an D-Link 502T Modem/Router. After knowing from people that USB is not that great in terms of support under Linux bought a D-Link 538TX which has an RTL-8139C+ Fast Ethernet chip which is supported by GNU/Linux. Almost all the ethernet cards here have that same chip. The DSL-502T has a web interface & as I dual-boot with windows the username & password is in the router/modem page itself. The ISP gives dynamic IP whenever we connect.
         Now a friend of mine was able to help me with configuring my network config. I would like to know a bit more about what he did. He told me he had given a static IP Address somewhere & the rest the modem/router will do by itself. Here's the things that he did :-
```

vi /etc/resolv.conf
nameserver 61.1.96.69
nameserver 61.1.96.71
:wq!

```
 These I guess are the domain name servers or DNS of the ISP from where the ISP gives the dynamic IP. Am I right or not?

```

ifconfig eth0 192.168.1.2

``` This I guess is saying take all parameters from the modem/router. Again is my understanding right or not?

```

route add default gw 192.168.1.1

```
       Here I'm stumped. I just have no idea. I read the route man but became no wiser. Any webpage or link which makes me understand what is this? & lastly

```

vi /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
dns-nameservers 61.1.96.68 61.1.96.71
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
:wq!

``` I guess this is all of the above. I tried to read the manual of interfaces but it seems I need little bit more background info. on this before I can make sense of what is written there. So if u guys can help me understand what is this or some link where things are written in a layman kinda language would appreciate it.

---

### Post by bscbrit on 2005-12-23
OK, I don't normally spend much time on this forum but I will do my best.

When you type [www.google.com](www.google.com), the computer has to know how to change that textual address to the values that it needs to establish a connection.  This uses a system called DNS which converts the [www..](www..). into something like 123.12.23.121. Your ISP provides 2 separate DNS systems hence the numbers 

nameserver 61.1.96.69
nameserver 61.1.96.71

It has to use numbers here because - this is the system that converts names to numbers and if you used a name, such as dns1.myisp.org, it wouldn't know how to convert it!

The next line gives your Network Interface Card the address of 192.168.1.2.  This is the fixed address for this card.  This is what people sometimes (mistakenly) call their computer's address but it belongs to the NIC.  If you had more than one card, and many people do, you can be on more than one network.  Each card would have its own address.

To talk to the outside world, you need to go via your modem/router.  The line

route add default gw 192.168.1.1

simply tells your computer that the gateway (gw) to the world is via this address 192.168.1.1.  This is the address of your modem/router.

The last chunk of 'code' is simply the whole thing put together in a format that can set your network up when you boot.

If you Google for 'network howto' or even use the link to rute in my sig, you will find lots more information.  HTH

---

### Post by ShirishAg75 on 2005-12-23
Thanx. I was thinking botht the numbers were for the modem/router. Would read rute sometime as well the network concepts howto. Don't know which is the best way forward.

---

### Post by ernesto.kemp on 2005-12-23
Hei Huskie,
whta is the file you changed this line?
I have the same trouble, i.e., have to run pppoeconf at any reboot..

I've posted this message few hours ago in the Desktop discussion list:

I'm running Ubuntu-5.10, and
I have to run pppoeconf at each time I turn on the PC,
despite the fact I've allways answer "yes" at the start-on-boot
option. Following an advise from this forum I've checked
the /etc/network/interfaces file, and all of the required lines
was there , with no remark signal.
Moreover, I saw an icon at the pixmap folder for an
"pppoe on" operation.. What should be the related command or script?
Does anyone can help me ?
Thanks

---

### Post by bscbrit on 2005-12-24
shirishag75,  I know that you just want to get online and use your computer but we all can improve our knowledge and enjoyment by learning more about linux.  It is easy to say that you will get round to reading the documentation sometime but, if you are like me, you will probably put it off.  My recommendation is that you read everything that you can lay your hands on.  Not all at once.  But now, for an example, is a good time to read everything you can find about networks and ADSL so that you understand how your system was connected by your friend.  You'll soon be offering help to newbies who haven't got quite that far...

---

### Post by daibak on 2005-12-24
[QUOTE=ernesto.kemp]Hei Huskie,
whta is the file you changed this line?
I have the same trouble, i.e., have to run pppoeconf at any reboot..

I've posted this message few hours ago in the Desktop discussion list:

I'm running Ubuntu-5.10, and
I have to run pppoeconf at each time I turn on the PC,
despite the fact I've allways answer "yes" at the start-on-boot
option. Following an advise from this forum I've checked
the /etc/network/interfaces file, and all of the required lines
was there , with no remark signal.
Moreover, I saw an icon at the pixmap folder for an
"pppoe on" operation.. What should be the related command or script?
Does anyone can help me ?
Thanks[/QUOTE]
ernesto.kemp,

Have you read my post #19 to this thread? Well, read that post and then my edit  few hours later with the step by step solution to what you gotta type in terminal. I've never had to type sudo pppoeconf since, I'm online ADSL asa Breezy B. boots.

Cheers.

---

### Post by BobSongs on 2005-12-26
[QUOTE=Ruskie]<snip>How can this be explained? How can I convince pppoe to do the trick on first trial???</snip>[/QUOTE]
Ahh. Now there you've lost me. I'm only a beginner still working mostly in the GUI. I've got years of Win/DOS experience that's totaly useless here. Somewhat frustrating, to say the least.

But there are *shell scripts*, the equivalent to DOS *batch files* that can be added to some mysterious folder. Once there they act like entries in the DOS **autoexec.bat** file. But that's all I know at this point. When I get further in the generic Linux tutorials perhaps I'll be of greater assistance.

---

### Post by bscbrit on 2005-12-26
bob, is this what you are looking for?

[http://efod.se/writings/linuxbook/html/system-init-files.html](http://efod.se/writings/linuxbook/html/system-init-files.html)

(and the next few pages from the link)

---

### Post by bscbrit on 2005-12-26
Bob,

It seem to me that /etc/init.d would be the appropriate place for such a script.  I do not use ppp* - my adsl is a modem router which can be easily accessed using ethernet - but I suspect that the required script shouldn't be too difficult.

If you tell me what ppp* commands should be run, and in which order, I can put one together for you.

PS.  Be quick, I go offline tomorrow for about 2 weeks as I visit family and friends in the UK.

---

### Post by notepad on 2006-05-14
well its been a while since i posted to the thread and i dont like it when somebody presents a question then says yay i got it going its all cool now or doesnt say anything at all about the resolution to the problem so heres mine:

i am still absolutely perplexed as to how anybody is using adsl with ubuntu without using a router style adsl modem btw (i challenge anybody to say that they are because i think that it is not possible).

what we did is go out and buy ourselves a dlink 504t router modem. we logged in to the modems config page and told it our internet account's username and password. so the theory from here is incredibly simple: the modem knows how to connect to an adsl internet account and does so when it is switched on. after that, it runs a dhcp server to configuretcp/ip of any machines connected to it and then it performs network address translation to pass internet traffic to and from those machines. all you have to do is set your machines to run dhcp client. the rest is plain sailing. it couldnt be any easier.

---

### Post by dproffessa on 2006-05-14
All you need to do is System-> Administration-> Networking and configure eht0 properties, use DHCP and click DNS tab to add DNS servers say 192.168.1.2 activate and close ypu should be resdy to go, u can put the network icon on the panel so u can see when youre logged on, problem is u nee to repeat this process everytime you boot up, but it works for me my ADSL supports PPPoA

---

