---
title: "ADSL setup help required , intrepid ibex"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by AndrewKeith80 on 2009-02-07
I am an expert computer user with years of experience. I am helping my sister in law install ubuntu on her old computer . She is not an expert computer user and is only going to use email and web surfing. 

I installed intrepid ibex with no problem. but here is where ubuntu fails miserably. 

1) i added a dsl connection. HOW THE HELL DO I GET IT UP !!! ???
2) network manager applet is missing. It went missing by itself.
3) I refuse to run anything in the terminal because my sister in law will just shrug and say, why dont we just use windows instead of typing giberish in the terminal
4) i cant change any networking options in network configurations. I just get , connection update failed, read only.

at this point .. i totally agree with her. Its painful to use ubuntu as a desktop computer unless everything magically works out of the box. 

Other misc problems
1) Skype doesnt install, it complains about cannot installing libqt4-core
2) libqt4-core doesnt install, complains about dependency problems. It doesnt complain in english though, since i dont consider its error messages comprehensible in english.

Any newbie help available? .. or should i switch to windows ?

---

### Post by bettlebrox on 2009-02-07
You can start Network Manager by pressing Alt-F2, then typing nm-applet.

How did you try installing libqt4-core? What's the exact error message?

Also, it be better if you asked each question in a separate thread. That way it's easier for other forum users to determine if a question is answered or not and it makes each thread much easier to read.

---

### Post by x33a on 2009-02-07
check if network manager is added in the statrup programs list.

system -> preferences -> sessions.

if not, then add it to startup.

alternatively you can run "pppoeconf" in a terminal to configure your adsl connection, and create shortcuts for "pon dsl-provider" and "poff dsl-provider" on the desktop. this way your relative won't have to use the terminal.

---

### Post by ugm6hr on 2009-02-08
You need to supply some detail about the modem being used.

If it is a modem-router (generally connected by ethernet), it should work easily - you just need to connect to the setup page (e.g. 192.168.0.1)

If it is a USB modem, give us the full manufacturer detail to see if it has Linux / Ubuntu drivers.  Even if it does, you will almost certainly need to use the Terminal to install it, particularly since you cannot get online without it in order to use some of the automated installation GUIs.

If none of that makes sense - you will need to supply detail from commands from Terminal (which are more useful anyway).  See the Wifi help link below (which also applies to wired).

In summary - once it is online, Ubuntu is easy.  Until then, be prepared for some work.

Also - unless you intend to reinstall annually, I would suggest Hardy 8.04 rather than 8.10, since it is supported for a lot longer.

---

### Post by superprash2003 on 2009-02-08
you might also want to check if you are getting an ip address from your router.. in your terminal type ifconfig and check..

---

### Post by AndrewKeith80 on 2009-02-08
here is an update of my problems

1) The network manager applet disappeared again. I followed some help guides and got the applet back. HURRAH .. after re-adding my DSL connection and clicking connect, guess what , it DISAPPEARED AGAIN. FREAKING UNBELIEVABLE. Seriously !!! 

2) pppeoconf did configure my dsl. however, when i run pon dsl-provider, ppp0 interface has the IP 1.1.1.30 or some other stupid IP which makes it unusable. How do i even start to troubleshoot this amateurish garbage of a program ?

3) I wont be using skype. Kind of no use since there is no dsl connection due to ubuntu ibex being stupid.


The modem i will be using is not a router but a bridge. 

My sister in law is already begging me to switch to windows. Even with windows problems, its certainly usable by even the most basic user.

---

### Post by ugm6hr on 2009-02-09
> **AndrewKeith80 said:**
> The modem i will be using is not a router but a bridge. 

I'm not 100% au fait with networking terminology, but I don't understand how a network bridge can connect to ADSL.

Perhaps a link to the manufacturer's manual or web page might help.

Also - a link to your ISP's "How to connect" page (even if it is for Windows / Mac) would help.

It appears you are trying lots of things, but not giving useful feedback on what happens to us; hence, it will be impossible to offer advice.

I realise you have plenty of IT experience, but if you are posting here for advice, you have to give people a chance to help.  If you are merely posting out of frustration, I would be happy to move this to the Testimonials section.

If you are experimenting - it might be worth looking at gnome-ppp instead of Network manager (the latter is for ethernet rather than dialup).

The errors with skype installation are because you are not online.  It will install easily if you have internet connection.

---

### Post by AndrewKeith80 on 2009-02-26
just an update. 

I have managed to get my DSL connection to work. 
1) network manager applet is missing. It went missing when i uncheck the enable network. Once missing, it never comes back
2) I couldnt create launchers for pon and poff. It says cannot create child process.. I am not bothered to fix it.

Well, long story short, my sister in law totally hated ubuntu because it was so buggy for non-technical users. We switched to windows.

IMHO , I agree with her that unless you have extensive computer experience, using ubuntu is a chore and doesnt even come close to windows or mac when it comes to home user experience. 

The thing that puzzles me is why arent programmers focusing on creating a better user experience?  Its a shame that the user interface is the weakest portion of ubuntu (or linux in general).

---

