---
title: "Terminal Server Client"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by mollycule on 2011-01-12
I have Ubuntu Netbook Remix (so Unity) on an Asus Eee PC.  I need to see if I can connect remotely to my HP desktop that runs Windows 7 Professional.  I'm trying to get Microsoft Visual Studio to work somehow, since I need to use it in my programming class.  I tried installing it through Wine, but it's rated Garbage and it didn't work.
I know remote desktop works at my school because a) the profs use it sometimes and b) I almost got it to work back when my netbook still had Windows Starter (I could see the computer I was trying to connect to's desktop, but then it froze and kicked me off).  
I installed Terminal Server Client and attempted to run it, but I couldn't get it to connect.  It says, "Error [the IP address] unable to connect."
I looked up the IP address using ipconfig in command prompt on the Windows machine, and I tried the IPv4 address and the Default Gateway and neither worked.  I also tried using the IP address IPChicken told me I was using, but no luck there either.

Suggestions?  Or do you know a way to get Microsoft Visual Studio 2008 to run on Linux?

---

### Post by PatchesTheCaveman on 2011-01-12
Do you have Remote Desktop enabled on the Windows machine?  The settings are accessible by clicking Start, right-clicking on Computer, and clicking Properties.  There is an option to access Remote Desktop settings in the blue bar on the left of the System control panel that appears.

---

### Post by mollycule on 2011-01-12
Yeah I do have it turned on, I forgot to mention that, sorry

---

### Post by PatchesTheCaveman on 2011-01-12
Are you connecting to it from outside the network?  In that case, you need to use your external IP address, and go in your router configuration and forward port 3389 to the Windows machine.

---

### Post by mollycule on 2011-01-12
At the moment, they're even connected to the same access point because I'm trying to see if it will work at all first in my room, but when if I eventually try it elsewhere on campus, it will be the same network, but it's a campus-wide network that's routed through three different buildings, so I don't know if that will impact that or not.  How do I find the external IP address? And I can't access the router, it's probably protected (and I don't know the IP address for it, and it's attached to the ceiling outside my dorm room).

In any case, somebody told me about Geany, which is a C editing program for Linux that has a lot of features and is probably a lot like Visual Studio.  I think this will work for me for that purpose.  Of course, being able to access my files remotely too would be awesome...

Thanks for the help so far!

---

### Post by PatchesTheCaveman on 2011-01-12
I see.  Depending on how your school network is set up you might not be able to remote desktop across the campus network.  To check, open a terminal and run:
```
ifconfig -a
```
If your IP address is 10.something, anywhere between 172.16.0.0 and 172.31.255.255, or its 192.168.something, you will probably not be able to use remote desktop.

As for just doing your programming in Linux, Eclipse is one of the most popular Integrated Development Environments (IDEs).  It has a similar featureset to Visual Studio.  Several of my CS classes required it.  (My school uses Linux for everything but classes strictly related to Windows development.  All but one of the CS computer labs run Ubuntu!)

Best of all, it's included in the Ubuntu repositories. To install Eclipse for C/C++ development, install the *eclipse-cdt* package using the Ubuntu Software Center, Synaptic, or by running this command on a terminal:
[code]sudo apt-get install eclipse-cdt[/i]

Please note that if you're just doing console (text) programming, you should be able to do everything on Linux.  But, if you're doing GUI (graphical) stuff, you'll need to use Visual Studio, as Windows uses a completely different API for graphical programming.

Eclipse also supports many different other programming languages, so you'll also be able to use it later for classes in Java, PHP, Python, and many other languages.

---

### Post by mollycule on 2011-01-13
It is 10.something, but I've (almost) successfully done it before, like I'd mentioned above.  Oh, well :)

Thanks for telling me about Eclipse!  Someone else told me about Geany, which looks pretty good too.  We're doing pretty basic stuff, probably nothing with GUI.

Thanks!

---

