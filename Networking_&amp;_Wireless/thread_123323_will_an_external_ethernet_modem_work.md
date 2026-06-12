---
title: "will an external ethernet modem work"
date: 2006-01-29
forum: Networking &amp; Wireless
---

### Post by markcaetano@gmail.com on 2006-01-29
ok

since i cant solve my problem with my internal pci modem
i have decided to take another path
THE BLUE CABLE:mrgreen: 
aka external ethernet dialup modem
will this work

bunt(ubuntu)has a problem with my modem but not with my ethernet
card so will this work!!

PC->ethernet card->[COLOR="Blue"]----ethernet-----cable[/COLOR]->D-link"internet server"->phone cable->internet

theres ya diagram

now to the question when i put the "external modem" to the phone line with
a dial tone an plug it into the ethernet card. will it sense it automatically
and i can surf the net and download bunt 6.04 "dapper drake"
or do i have to screw around in the terminal for an hour

---

### Post by az on 2006-01-29
Where I live, a cable modem uses dhcp, while adsl uses pppoe.  You can set the ethernet connection to dhcp when you configure the network using the networking tool.  For pppoe, you need to use pppoeconf, AFAIK.

sudo pppoeconf
and follow the instructions.

Takes about 66 seconds to do, in all.

---

### Post by markcaetano@gmail.com on 2006-01-29
problem is i cant get broadband cos the phone company wont install a mini exchange closer to us cos i live too far from the excange

the main question is will it work:-k

---

### Post by dickohead on 2006-01-29
So you're using a dial-up modem, as in - 56k? Uses the RJ11 socket rather than the RJ45 (6pin not 8)? To get your dial-up PCI modem working with ubuntu you should try something called Linmodem. Most PCI based dial-up modems use Lucent Win Modem chipsets, which used to suck for Linux! But recently (ironically since ADSL is on the rise the need for them is lessening) most cards will now work quite well with Linux, the older the better!

---

### Post by markcaetano@gmail.com on 2006-01-29
well its from 2000 so im in luck
128k adsl was still in the labs then

---

### Post by az on 2006-01-29
[QUOTE=markcaetano@gmail.com]problem is i cant get broadband cos the phone company wont install a mini exchange closer to us cos i live too far from the excange

the main question is will it work:-k[/QUOTE]

I didn't realise there was such a thing as an external dialup modem which connects through a cat5 cable.  Usually it is through a serial port.

Can you find out what protocol it uses?

Also, you are not talking about ISDN, are you?

---

### Post by markcaetano@gmail.com on 2006-01-29
this is how the external modem works

from my ethernet pci card is a cat5 rj45 cable to the modem"internet server" the from the modem goes a standard phone cable rj11to the plug in the wall

---

### Post by markcaetano@gmail.com on 2006-01-29
how do i find out the protocol

now that u mention it azz, i think it might be PPP

---

### Post by markcaetano@gmail.com on 2006-01-29
yup didnt work
will u please look at my [other problem]("http://ubuntuforums.org/showthread.php?p=691409&posted=1#post691409")and
give me ur opinion

thanx heaps

---

### Post by markcaetano@gmail.com on 2006-01-30
to clear up a few things my external modem is a dial-up modem tha can be connected to the pc with either a cat5 cable or a serial cable

---

### Post by mips on 2006-01-30
What you want to do is Dial On Demand Routing.

The principal this works on is that you internet server/modem listens for what you define as "interesting traffic" and then fires up a dialup connection to your ISP.

On the Linux side there should be very little to configure if anything, basic tcp/ip config.

On the Internet server side you will have to define interesting traffic and your ISp parameters. You must be carefull because you could keep the phone line up the entire time.

**Please tell us the exact model of your D-Link device with a web link to the product.**

In theory I see no reason why this should not work.

---

### Post by mips on 2006-01-30
Would I be correct in assuming you have a D-Link DP-602 Internet Gateway for Analog/ISDN Modem ?

[http://www.dlink.com.au/default.aspx?FolderID=515&ArticleID=1776](http://www.dlink.com.au/default.aspx?FolderID=515&ArticleID=1776)

If this is what you have then it should not be to hard getting online ;)

---

### Post by az on 2006-01-30
[QUOTE=markcaetano@gmail.com]to clear up a few things my external modem is a dial-up modem tha can be connected to the pc with either a cat5 cable or a serial cable[/QUOTE]
Do you have the serial cable?  Cuz that's working out of the box.  You would be happier with gnome-ppp from universe, but to connect to a serial modem works fine.

---

### Post by markcaetano@gmail.com on 2006-01-30
yep thats the dlink modem
jow did u find it???:confused:

---

### Post by mips on 2006-01-30
[QUOTE=markcaetano@gmail.com]yep thats the dlink modem
jow did u find it???:confused:[/QUOTE]

If I told you I'd have to shoot you ;)  Just browsed dlink oz site.

I'm off to sleep now. I'll write up a procedure for you in the morning on how to get up & going.

---

### Post by markcaetano@gmail.com on 2006-01-30
actually it looks the same but its a DP601-M

---

### Post by mips on 2006-01-31
_**The Product:**_
[http://www.netmaster-uk.com/Images/products-page/D-Link%20DP-601M.htm](http://www.netmaster-uk.com/Images/products-page/D-Link%20DP-601M.htm)

_**First download:**_
[http://www.dlink.com.au/tech/resources/files/internets/inter_setup.zip](http://www.dlink.com.au/tech/resources/files/internets/inter_setup.zip)
[http://www.dlink.com.au/tech/drivers/files/internets/601m_210.zip](http://www.dlink.com.au/tech/drivers/files/internets/601m_210.zip)
[ftp://files.dlink.com.au/Product%20Info/DP-602/Manuals/DP-602%20Manual%20Rev.%2002.pdf](ftp://files.dlink.com.au/Product%20Info/DP-602/Manuals/DP-602%20Manual%20Rev.%2002.pdf)  # For DP-602 but cannot find DP-601 manual.

# You might want to consider upgrading the DP-601 firmware to v2.10

_**Physical Connection:_**
Connect the DP-601 to your PCs ethernet port. 
The cable should be a **[COLOR="Red"]Crossover[/COLOR]** cable as this device would usually plug into a hub/switch and thus use a straight cable. If you go PC to DP-601 it will be the opposite, there might be a mdi to mdi-x switch on the back of the DP-601 to do the x-over but I doubt it.
Make sure device is powered on.


**_PC Config:_**
Go to Sytem->Admistration->Networking
Select your ethernet adapter and ensure it is active.
Configure the TCP/IP settings for the adapter as follows
**IP Address:**             192.168.100.10
**Netmask:**                255.255.255.0
**Default gateway:**     192.168.100.1
**DNS:**                      xxx.xxx.xxx.xxx #Please obtain the DNS/Nameserver IPs from your ISP
**DNS:**                      yyy.yyy.yyy.yyy #Please obtain the DNS/Nameserver IPs from your ISP

# You could try and use DHCP here and in theory you should get an IP address but with static at least it will stay constant if in the future you want to implement any filtering/firewalling etc.


**_Testing from a terminal:_**
Do a **ifconfig -a** and the you should see the above config reflected for the ethernet inface.

Do a **ping 192.168.100.1**  and you should get a response from the DP-601 indicating that your everything is correctly setup and working to the DP-601

Do a **route -n** and you should see a default route configured.


**_DP-601 Config:_**
Open a web browser and in the Address bar space enter 192.168.100.1 followed by the enter key.
You should now be presented with the Web Admin interface to the DP-601

Here you must configure the DP-601 for the following-
**Operation Mode**		# LAN-WAN Internet server
**DHCP Server**		# Disable if you are not going to use it.
**ISP Telephone Number**	# Put the local access number here
**ISP Username**		# Remember some ISPs require a full username like [email]userid@myisp.domain.net[/email], verify with your ISP.
**ISP Password**
**DNS IP Address**		# Yes, again !
**Maximum Idle Time**	# How long to disconnect after connection becomes idle, 1-65535min default=30minutes
**Change password**		# DP-601 Password, default=none
**Baud Rate**		# Serial interface speed, default=115200
**Dial Up Mode**		# Dial on Demand

**[COLOR="Red"]SAVE your settings !!![/COLOR]**

# You should also be able to telnet to the device, telnet 192.168.100.1 and configure it this way.
# Please note that I could find no PDF manual for the DP-601 so I made a few assumptions based on the DP-602 manual but the above parameters would be the basic ones required. I suggest you browse throught the various tabs in the Admin window to see what goes where. If you get stuck you can always capture screenshots of easch tab and mail them to me.

**_Note:_**
Whats going to happen now is the device is going to dial-out every time there is traffic on the ethernet port wich is basically permanently. I'm sure you dont want this as lots of countries use time based billing for local&ISP calls.
You will have to do the following-
1. Disconnect the phone line after each session, this is also good against lightning.
2. Disable/Enable the ethernet interface via the **sudo ifdown eth0** & **sudo ifup eth0** commands that you could have as a script accessible via two icons on your desktop.
3. Someone else might have a brighter idea ;)

Another thing is your PC will be using MTU values of about 1500 which is not suitable really for dialup so i would advice lowering the MTU value to about 492 or something in that area but the best value is obtained through experimentation. Check if the DP-601 has any options to change the MTU !

To change your MTU values on the PC you have to edit your **/etc/network/interfaces** file and add the line mtu 492 under the interface.

```
# The primary network interface iface
eth0 inet static
address 192.168.100.10
netmask 255.255.255.0
gateway 192.168.100.1
mtu 492
```

Ok, now my fingeres are buggerd from typing....

**Good luck an let us know how it goes....**

---

### Post by mips on 2006-02-01
Did this work ?

---

### Post by markcaetano@gmail.com on 2006-02-03
Im Sorry to say[SIZE="7"]:cry: I DONT USE UBUNTU ANYMORE:cry: [/SIZE]
MY Dear computer died RIP 2006
however please keep me up to date about ubuntu via email
[email]markcaetano@gmail.com[/email]

because i am using xp and hating every ******* minute of bill gates watching and keylogging me i cant wait to get back to my beautiful ubuntu system
however my powerboard surged and everything on it no longer works
including my dear dell pc

so please send me an email to notify me when DAPPER DRAKE!!!\\:D/ comes
out so i can have 100% control over all my files

please try to understand how pissed i am
and dont ignore this post please email me!!

---

### Post by brentroos on 2006-04-12
*

---

### Post by mips on 2006-04-12
[QUOTE=brentroos]Regardless of your OS, use a serial cable with this type of modem, not ethernet. You can use ethernet, but the serial interface will not a have any problems, no matter what OS you're using. I realize you say your computer doesn't work anymore, but anyone else who is curious might want this info.

...

And like the other user suggested, use Gnome-PPP, available via apt-get. I think you need to enable universe for this.

...
[/QUOTE]

I think you and some others here don't understand that this device is not a standard modem.

It is a dial-up router/server. It has NO serial port. It does not function like a normal modem. You can ONLY use the ethernet port. It is basically a router with built-in analog modem, kinda similair to a ISDN router. Functions on the principal of Dial On Demand Routing.

So a serial cable & PPP is useless in this case...

---

### Post by brentroos on 2006-04-13
*

---

### Post by mips on 2006-04-14
[QUOTE=brentroos]Well excuuuuse me. Just kidding. You're correct. This is not a modem. This is a router with an RJ11 interface, it sounds to me.

 
Since Mark said that it does have a serial interface I assumed that point to point was what he was seeking. PPP will work with certain types of routers, just to let you know. PPP is part of the TCP/IP stack within the Network Layer of the OSI Model, is it not (yes it is)? I am a CCNA, and have studied PPP extensively. However, I must have read this too fast, and/or assumed that he was trying to use this device to dialup to an ISP, so I apologize for my assumption. I think this device would probably be more useful in a WAN environment, hmm? 

Also, since many quality routers do have a serial interface, as well as ethernet, I also made this assumption. I must admit, I am much more familiar with Cisco routers, than I am with D-Link or Linksys, or whatever router from Best Buy and whatnot. My work in networking consists mainly of Cisco routing.

Anyhoo, thanks for pointing this out dude. I mentioned the serial modem also for the benefit of anyone else wondering how to dialup, since there seems to be a few questions in the forums on the subject, and for the fact that on ebay one of these devices can be purchased for not very much $$. In fact, since these devices are out of date as of today, ebay is most likely the best and easiest way to find such a device with a serial interface.

I am merely trying to help others with what for some reason hasn't been understood by many. This may be due to the rather large size of the forums at this point, which might make it a bit difficult to organize, and/or navigate for new users. It does sometimes take some searching to find the correct answers.

I love the community here, and as for my knowledge and expertise on what I happen to know, am willing to participate and contribute what I can for the benefit of others, and for the good of the community and Ubuntu Linux in general.

Once again thanks for pointing this out. As for what I mentioned in the previous post, the easiest solution for a dial-up connection would be to purchase a hardware modem with a serial interface to connect to a dialup isp.

As far as this particular device in question, I still fail to understand why someone would want to use this nice device merely to dialup to an isp, since the complexity far exceeds the function in question, imo, at least for someone not familiar much with TCP/IP.

At any rate, good posts guys. It's definately an interesting discussion to say the least.

One last note, I'd love to have a device like this to play with at home![/QUOTE]

People are not always familair with technology/terminology so they might post certain 'untruths' if i could call it that ;)    Once you look up the facts thought the picture changes a bit, ie RJ-11=Serial port etc. Usually better to look up the device.

Use to work for a telco in the cisco field and did the whole ccna/ccnp/voice specilisations thing,. Certifications are a money making racket imho. Was fun though, worked on anything from a 800series to 7600series router + top end switches, call managers & wireless stuff but had enough after 10 odd years in the field.

The cisco stuff is really much better than the rest of the stuff out there, especially stuff targeted at the home/soho market.

yeah, a hardware serial model is probably the easiest option out there...

If you want a device like that to play with at home llook for a old Cisco 700 series, I know they did ISDN but not sure about analog.

---

### Post by brentroos on 2006-04-24
%

---

### Post by markcaetano@gmail.com on 2006-10-05
ok im back... loong holiday with winblows](*,) why did i do it
open to any further suggestions

---

### Post by mips on 2006-10-05
Did you read post #17 ? It's pretty much outlined there what you have to do.

If you don't like that advice then I cannot help you, sorry.

---

