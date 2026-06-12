---
title: "Internet connection issues"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by confusion22 on 2011-02-01
Okay, today I installed Ubuntu for Netbooks on my daughter's netbook computer - this was a computer received through my kids' school, and basically until today was running on Windows 7 - it used to log in through some sort of education server, but this stopped working today! (It's no longer a school based computer, so it makes sense that access was eventually cut off). 

Anyway, it made sense for me to install a new OS on it, and I'd heard about Ubuntu, so decided to install it! Now, I think the computer actually had to be logged into the server in order to connect to the Internet, as when I did the install it said there was no network connection. I ended up using a cable and connecting it that way, with the hope that once it was all installed I'd be able to connect via wireless...(I elected to do a full install and remove the original OS so there's nothing else on the computer anymore except the Ubuntu and associated software).

However, once it was installed it couldn't find a wireless connection, and even though I've plugged it in using the cable to the router, I still can't access the Internet... There was some option to install Broadcom or something, but when I tried that it failed to install.

Sorry if I haven't explained this well ;) I'm used to getting a computer, turning it on and seeing the wireless network pop up straight away!

---

### Post by mips on 2011-02-01
In a terminal post the output of **lspci -v** here.

---

### Post by grahammechanical on 2011-02-01
You are used to buying a computer with an Operating System pre-installed and set up by the manufacturer. Now, you have chosen to Do It Yourself. I do not understand everything you say. You do not need to be connected to the Internet in order to install Ubuntu. You have just proved this. 

The installation process should detect the built in network adapters and install a program to manage network connections. This is called Network Manger. Do you see a network icon? It should look like a wedge of curved lines radiating upward. If you are not connected to any network either by wire or by wireless then there will be a red exclamation mark over the icon. Do you see this?

If you switch the computer on with the cable connected to the router it may make a connection to the router. If this happens you will see the network icon as two arrows going in opposite directions. I am assuming that you have installed Ubuntu 10.10.

Alternatively, you can left click the icon and select a wired network connection. You will need to do this if the computer has more than one wired network adapter. The computer will then connect to the router and you should have Internet access.

If you see available wireless networks then you know that your wireless adapter has been recognized and the drivers are installed. Select your wireless network. If there are no wireless networks available then you will need to install a driver for the adapter.

With a wired connection established go to system>Administration>Additional Drivers. See if there are any additional drivers available, especially for wireless, for your computer. These are drivers that are owned by a particular manufacturer. They can be downloaded and installed for free but they cannot be distributed by Ubuntu.

It is also the policy of the developers of Ubuntu not to include these kinds of drivers but to give users the choice of installing themselves. This is why the installation of these drivers does not take place during installation.

Regards.

---

### Post by confusion22 on 2011-02-01
Thanks for your response! Sorry my original post was so unclear ;) 

> **grahammechanical said:**
> You are used to buying a computer with an Operating System pre-installed and set up by the manufacturer. Now, you have chosen to Do It Yourself. I do not understand everything you say. You do not need to be connected to the Internet in order to install Ubuntu. You have just proved this. 

The installation process should detect the built in network adapters and install a program to manage network connections. This is called Network Manger. Do you see a network icon? It should look like a wedge of curved lines radiating upward. If you are not connected to any network either by wire or by wireless then there will be a red exclamation mark over the icon. Do you see this?

Okay, if I'm not connected by a cable, I get the radiating lines and the red exclamation mark. When I click on this, the computer can't find any wireless connections.

> 

If you switch the computer on with the cable connected to the router it may make a connection to the router. If this happens you will see the network icon as two arrows going in opposite directions. I am assuming that you have installed Ubuntu 10.10.

Yup, this is also the case. I get the two arrows going in opposite directions. Now, since I posted my original query I've noticed that there DOES seem to be some data transfer (as in, Ubuntu will install updates, albeit very slowly). I went into firefox today and was actually able to do a Google search lol. BUT it only worked once... (usually it just times out... I was assuming earlier that I had no connection to the Internet because of this) so I dunno if it's the computer or the cable...but I'm getting a really lousy slow connection (which is bizarre... the other computer connected wirelessly to the router gets a perfectly reasonable download speed).
> 
Alternatively, you can left click the icon and select a wired network connection. You will need to do this if the computer has more than one wired network adapter. The computer will then connect to the router and you should have Internet access.

If you see available wireless networks then you know that your wireless adapter has been recognized and the drivers are installed. Select your wireless network. If there are no wireless networks available then you will need to install a driver for the adapter.

With a wired connection established go to system>Administration>Additional Drivers. See if there are any additional drivers available, especially for wireless, for your computer. These are drivers that are owned by a particular manufacturer. They can be downloaded and installed for free but they cannot be distributed by Ubuntu.


When I look for additional drivers I get a couple of Broadcom drivers show up, I tried to install both of these yesterday but both failed to install... I guess this is my problem! I wonder if it has something to do with the speed of the internet connection? I haven't a clue why it's so slow...it's behaving as if I was on an incredibly slow dialup network or something...and yet the cable is plugged directly into the router, so I'd expect it to be faster than my usual wireless connection.
[/QUOTE]

I am trying to install them again... we'll see if it works! 

Oh and until yesterday this computer worked perfectly well wirelessly, and never had a problem with Internet speed. The cable I plugged it into the router with is brand new, never been used before so it should work fine.

---

