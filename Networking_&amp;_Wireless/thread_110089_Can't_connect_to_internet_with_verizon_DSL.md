---
title: "Can't connect to internet with verizon DSL"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by tommcd on 2005-12-30
Hi, I just installed Ubuntu5.10 on my old PC. Everything went ok except that my network settings weren't auto detected, so I entered IP address manually (ie, I entered the IP address that displays when you do IPCONFIG in windowsXP). I can't get on the internet at all. DSL works fine on my WindowsXP rig. 
Can someone please help me do this? I don't know squat about linux, so I need detailed instructions please, if possible. I would really like to get up and running with Ubuntu! Any help appreciated, thanks!

---

### Post by mips on 2005-12-30
First try this guide and tell us where you get stuck, [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

then you can also look at this [http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon](http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon)

---

### Post by tommcd on 2005-12-30
umm, I looked at the first guide:
 [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) ,
 but I'm not sure what to do with that code. Where does it go? Please tell me what I need to do (in plain english) to figure out how to get online. As for the second guide:
[http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon](http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon) , I don't even know what a terminal is. Remember, I'm a total linux noob. I may help to know that my DSL uses PPPoE.  Any help appreciated thanks.

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=tommcd]umm, I looked at the first guide:
 [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) ,
 but I'm not sure what to do with that code. Where does it go? Please tell me what I need to do (in plain english) to figure out how to get online. As for the second guide:
[http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon](http://ubuntuforums.org/showthread.php?t=89839&highlight=verizon) , I don't even know what a terminal is. Remember, I'm a total linux noob. I may help to know that my DSL uses PPPoE.  Any help appreciated thanks.[/QUOTE]
The stuff in the "code" blocks are examples of an interactive terminal session.  You are supposed to open the Terminal program (which is under the Accessories menu) and type the commands in.  

The prompt is shown in some of the examples.  When you see "$" think "C:\>" from Windows.

---

### Post by tommcd on 2005-12-30
Do I type the code in terminal from the first link:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) , or from the second:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) 
Do I type all that stuff, or just the first part?
Isn't there an easier way? Would getting a router help?

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=tommcd]Do I type the code in terminal from the first link:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) , or from the second:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) 
Do I type all that stuff, or just the first part?
Isn't there an easier way? Would getting a router help?[/QUOTE]
A router generally makes things a bit easier when you want to have more than one PC share your home network.  

Also, it helps you when talking with tech support, sometimes.  Verizon doesn't officially support Linux, but if you are knowledgable about your system, they can help you configure the modem.  If you have a router, though, they are generally a little better at helping you out configuring the router (even if it is not a supported router), because many routers pretty much work the same way.

Once you get the router set up for Windows, Ubuntu will pretty much work automatically.  Just set your network card up to use DHCP and the router should take care of the rest.

Basically, the idea behind the first link that mips gave you is that you have a step by step troubleshooting guide as to what might not be working.  Each step is designed so that we can tell that the supporting infrastructure works before we examine the next layer.  As a simple example, it's kind of like:

1) First check that the cables are plugged in.
2) Next check if the computer detects the hardware.
3) Next check that the ethernet cards are able to broadcast to each other.
4) Next check that TCP/IP networking works.

If any of the lower numbered steps failed, it would be a waste of time to check the higher numbered steps first.

Does that make sense?

---

### Post by tommcd on 2005-12-31
Thanks for the info. If I can get the PC to work with a router in windows then I can just hook up the Ubuntu system and it will work? Is that right? 
How do I set my network card to use DHCP? Does the router take care of that?
The PC I have Ubuntu on has 2 network cards. One is on the motherboard and one is a PCI network card. Is that a problem? Both show up as active in Ubuntu. I tried both of them and nothing. They both work under widows.
Also, in this thread: 
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
Is that the stuff I should type in terminal?

---

### Post by tommcd on 2005-12-31
If I can get the PC to work under windows with a router then it will work with Ubuntu automatically? Is that right? I will get a router then if this is true.
How do I set the network card to use DHCP? Does the router take care of that?
 Also in this thread:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
Is that the stuff I type in terminal?
The PC I have Ubuntu on has 2 network cards, 1 on the motherboard and 1 is a PCI card. Is that a problem? They both work under windows but not Ubuntu.

---

### Post by mips on 2005-12-31
What DSL device do you have, make & model ???

You might already have a router and not know it as some companies configure them in bridged mode...

Dont worry, we will get you up & running.

---

### Post by tommcd on 2005-12-31
My modem is a Westell wirespeed, not sure of the model # right now because I'm at work. It is not a router (as far as I know). It only has one ethernet port. I will look at the modem when I get home and provide any additional info I can. Next week when I get a chance I will try troubleshooting with the info in the links you guys gave me. Not too sure I can make much sense of all that stuff though.
Any advice on what kind of router to get. Guess it needs to support DHCP, right?  Thanks for any advice.

---

### Post by vasudevank on 2005-12-31
i have verzion dsl, get a cheap d-link DI-524 router, it supports dhcp, ubuntu "just works" with it

---

### Post by mips on 2006-01-02
[QUOTE=tommcd]My modem is a Westell wirespeed, not sure of the model # right now because I'm at work. It is not a router (as far as I know). It only has one ethernet port. I will look at the modem when I get home and provide any additional info I can. ....[/QUOTE]

I had a look and Westell does have wirespeed routers by the way, we just need to know what model you have.

---

### Post by etetley on 2006-02-10
the westell wirespeed (2100,2110) is most likely what u have im guessing its a modem that u have

all you should need to do is set up a pppoe dialer of some sort (if there isnt one already installed by default on ubuntu im at work...at a verizon dsl call centre:P(dont beat me up) so i dont know ill check and edit when i get home) and then pop in your verizon username and password and then hit connect (since u say its pppoe and your using ethernet). 

*also note westell wirespeeds dont give out private ip addresses ie 192.168.x.x unlike the 2200, 6100 or 327w which are modem/router models so right now your ip has  just a regular non routable 169.x.x.x ip address(at least thats what it always defaults to in windows thus giving you a limited or no connectivity warning in XPsp2)

your ip should be recieved when you make that pppoe connection

- hope this gives you and everyone else here the theory of what is going on here im a kubuntu/linux n00b so i dont know how to do anything else as far as the dialer goes..

---

