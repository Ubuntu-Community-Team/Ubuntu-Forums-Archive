---
title: "Frustration with finding printer on wireless network"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by deejay_99 on 2009-09-13
I'm frustrated. I got a new wireless printer, installed on my wireless network, got it printing on my portable (Windows XP) and desktop (Windows XP) and am trying to get it installed on Ubuntu. 

**It took me literally _under 8 minutes_ to install the printer and have it recognised by both Windows machines, and printing properly.**

Ubuntu does not sense the printer on the network .... so I have to configure it. So I read about this online and realize I need to go to Printer config, ---> choose network printer --->find network printer 

But no network printer comes up !!!!! ... it asks for Host information  ...but the "find" is greyed out !!!!  .... **where do I find info. on host ????  **..... no help anywhere on the screen .... try other screens that ask for information ... end up at Printing Troubleshooter.

In the Printing Troubleshooter...... it asks for Server name .... or server IP address .... **where do I get this information ???**  Of course, there is no information on how to find these things !!!! ...... Sad

 This is where I am now .... **still not installed and I have already spent 30 minutes ... with no results !!!!!!** **To me, this should be easy, effortless and a complete no-brainer.** I think Ubuntu needs to improve in this area. I'm sorry to rant, but this is just a silly waste of time ... no Windows user will EVER put up with this nonsense.

Anyways, I really appreciate any help  (detailed instructions please ... I'm a newbie) in getting my printer installed. 

Thanks

---

### Post by jimbo3 on 2009-11-15
I am having the same problem but I have spent a lot more time on it to no avail. I have a Netgear Router which is wired to the internet and am trying to connect my Leximark 4900 series printer wirelessly. anyone able to help please?

---

### Post by ingridt on 2009-11-17
These links helped me with my Brother wireless installation:

for the brother-drivers:
[http://solutions.brother.com/linux/en_us/download_prn.html#DCP-585CW](http://solutions.brother.com/linux/en_us/download_prn.html#DCP-585CW)
and their instructions:
[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

Find the appropriate pages for your particular printer.

I took some extra help from:
[http://ubuntuforums.org/showthread.php?t=590793]("http://ubuntuforums.org/showthread.php?t=590793")

And the helppages of CUPS
[http://localhost:631/help/network.html#DHCP](http://localhost:631/help/network.html#DHCP)

:KS[B]Actually CUPS did the job, after I installed the drivers. Going to "Admin" in CUPS, you will find an option "Find printers". Once it is found, simply take all the defaults and test.
[/B]
If the printer is recognised by the Windows PC in the same network, it should also be working in Linux. 

A power off/on of the printer may help if it is not found at first.

---

### Post by jimbo3 on 2009-11-17
Afraid its all too complicated for me. I am an average person willing to have a go at most things, but in the absence  of clear instructions I am afraid that Ubuntu is a dead duck for me. What I need a step by step walk through in plain, non techie language. Its a pity because what I have seen of it Ubuntu is a better system than Windows. I appreciate your efforts and thank all of you for your kind assistance.

---

### Post by Dude-PWB- on 2009-11-17
> **deejay_99 said:**
> I'm frustrated. I got a new wireless printer, installed on my wireless network, got it printing on my portable (Windows XP) and desktop (Windows XP) and am trying to get it installed on Ubuntu. 

**It took me literally _under 8 minutes_ to install the printer and have it recognised by both Windows machines, and printing properly.**

Ubuntu does not sense the printer on the network .... so I have to configure it. So I read about this online and realize I need to go to Printer config, ---> choose network printer --->find network printer 

But no network printer comes up !!!!! ... it asks for Host information  ...but the "find" is greyed out !!!!  .... **where do I find info. on host ????  **..... no help anywhere on the screen .... try other screens that ask for information ... end up at Printing Troubleshooter.

In the Printing Troubleshooter...... it asks for Server name .... or server IP address .... **where do I get this information ???**  Of course, there is no information on how to find these things !!!! ...... Sad

 This is where I am now .... **still not installed and I have already spent 30 minutes ... with no results !!!!!!** **To me, this should be easy, effortless and a complete no-brainer.** I think Ubuntu needs to improve in this area. I'm sorry to rant, but this is just a silly waste of time ... no Windows user will EVER put up with this nonsense.

Anyways, I really appreciate any help  (detailed instructions please ... I'm a newbie) in getting my printer installed. 

Thanks

That's because the Windows software for the printer does all the work for you, so you don't have to know anything about networking or network printing, it just does it. That's why when things go wrong in windows, the average user doesn't know how to fix it. At least in linux, if there is a problem, you will know where to look, because you took the time to learn how to set it up in the first place. Please don't blame linux because you don't know how to set it up. If your printer manufacturer didn't supply the proper software for your linux install, then bad on them.

However, every network device, wireless or not will have an IP address, it's up to you to know what that IP address is. It should be listed in your available wireless access points, or you may have to look in your router configuration to find that IP address.

Edit: My bad, just noticed this was a somewhat dated post. :redface:

---

### Post by ingridt on 2009-11-18
> **jimbo3 said:**
> Afraid its all too complicated for me. I am an average person willing to have a go at most things, but in the absence  of clear instructions I am afraid that Ubuntu is a dead duck for me. What I need a step by step walk through in plain, non techie language. Its a pity because what I have seen of it Ubuntu is a better system than Windows. I appreciate your efforts and thank all of you for your kind assistance.

First step if you still want to give it a try: find the drivers for your printer. You should look on the manufacturer's site, or you could search on [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

Meanwhile you could already try CUPS, because Ubuntu has a number of drivers available. On my Jaunty it was installed and working without any effort. 
Type [http://127.0.0.1:631/](http://127.0.0.1:631/) in your browser: this opens something that is installed on your harddisk. Then go to the tab "Administration" and click "Find new printers". (printer and network should be on and connected)

---

### Post by jimbo3 on 2009-11-18
Thanks for the advice ingridt. Unluckily I have learned there are no drivers for my Lexmark 4900series so it looks like I will have to get another printer. I will still use Ubuntu because it seems to be such a good system, I will just have to print through Windows until I get one.):P

---

