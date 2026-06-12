---
title: "network printers from work to home"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by proevofanatik on 2010-01-23
i am able to connect to a windows machine from kubuntu 9.10 using a logmein firefox addon. but what im wanting to do is control the house pc (vista) from my workplace pc (kubuntu) and when i want to print from the house pc i want it to print off my workplace printer. is that possible?

it might sound strange but windows xp is going to be obsolite in 2014. the house pc has vista and i need that to run the payroll software i have used for years. i dont want to use a different payroll software because im used to this one and it doesnt install on wine. so im thinking that if the payroll software is installed in the house pc, i could control it from my work and use the software that way. but i want the pay slips to print off in my work.

thanks

---

### Post by proevofanatik on 2010-01-24
i know that you can network printers in the same network. but i just want to know if i can print from a different network.

thanks

---

### Post by flabdablet on 2010-01-24
The way I'd do this is set up a ssh connection from the home PC to your work machine, or vice versa if firewall configuration is easier that way, and use that connection to forward port 631 on the home PC to the work PC. From your home PC's point of view, that would make it look like the Ubuntu machine's IPP (print) server was actually running on the home PC itself; you could connect to any of the work printers via [http://localhost/printers/printer-name](http://localhost/printers/printer-name).

Post back if you can't find stuff on setting up a ssh conection that makes sense to you.

---

### Post by proevofanatik on 2010-01-25
tbh m8 networking is very new to me. i know how to connect pcs to a wireless router obviously. but im not too sure about more advanced stuff. if its not too much hassle could you guide me on how to do this?

---

### Post by flabdablet on 2010-01-27
OK, I'll start with an overview of what I propose, then keep drilling down until we get to bits you know how to do.

First thing: you don't want to use printing or file sharing protocols over the Internet without some kind of encrypting wrapper. Doing so is all kinds of insecure.

Second thing: the simplest encrypting wrapper I'm aware of is called "ssh port forwarding". This requires a ssh (secure shell) client on one end, and a ssh server on the other. If you have a choice, it's easier in practice to put the ssh server on the Ubuntu side. I'll assume that's what we'll be doing for the rest of this explanation but if it turns out we need to do it the other way that will be OK too.

Once we can persuade a ssh client to connect to a ssh server, we can also tell them to set up "port forwarding". This neat trick means that network-accessible services running on one of the computers can be made to look as if they were running on the other. All the traffic passing between the computers to make this work gets encrypted by ssh and is therefore safe to route via the Internet.

So the jobs that need doing are:

1. Install a ssh client on your Windows box.
2. Install a ssh server on your Ubuntu box.
3. Get the ssh client talking securely to the ssh server.
4. Set up forwarding for Internet Printing Protocol (port 631) and make it easy to set up and tear down.
5. Make your Windows box print via the IPP service that it now has effectively local access to.

Let's start with 1:

There's a nice free Windows ssh client called [PuTTY.]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") The easiest way to install it is to download putty-0.60-installer.exe from the [download page]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") onto your Windows box and run it. Accept all the defaults. PuTTY itself and a bunch of other handy bits and pieces will end up in (typically) C:\Program Files\PuTTY.

2. Getting a ssh server installed on your Ubuntu box is even easier: just install the openssh-server package, either in a Terminal window with **sudo apt-get install openssh-server** or using the graphical package manager.

3. Several substeps:
3.1. Open an external (internet-facing) TCP port on your workplace's Internet router, forwarded to port 22 on the Ubuntu computer (note: although this is also called "port forwarding", it's not the same as what we'll be doing later with ssh. Yes, this naming overlap is confusing. It's also standard jargon, unfortunately).
3.2. Start PuTTY on the Windows computer, give it the name (or IP address) of your workplace's Internet router and the number of the external port you opened, and verify that you can log in to Ubuntu from Windows with your usual Ubuntu username and password.
3.3. Use PuttyGen on the Windows computer to create a private/public key pair for identification purposes.
3.4. Copy the public half of that into ~/.ssh/authorized_keys on the Ubuntu computer.
3.5. Verify that you can now log in to Ubuntu from Windows without needing to enter a password.
3.6. Disable password-based login in the ssh server, so that the only way to connect to it is using the ID keys we set up in 3.4. This means that even if your Ubuntu username is kind of obvious and your password isn't particularly strong, ssh will not become a back door for black hats.

Step 4 also has several subteps:
4.1. Save all the necessary logon and port forwarding details as a PuTTY profile.
4.2. Add a shortcut to the Windows desktop that starts PuTTY using the saved profile, so all you need to do to bring up the connection is double-click the shortcut, and all you need to do to close it down is close the resulting window.
4.3. Verify that you can now access the Ubuntu computer's CUPS admin page by pointing a web browser on the Windows box to [http://localhost:631](http://localhost:631)

Substeps for step 5:
5.1. Make sure the Ubuntu box is set up to share the printer you want to use.
5.2. Install the appropriate printer driver on the Windows box.
5.3. Add a new network printer to Printers and Faxes.

The only part of this I can't give you specific guidance on is forwarding an external TCP port on your workplace router to port 22 on the Ubuntu machine, because I don't know what equipment you're using. Here's a [fairly comprehensive guide]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") (don't let them sell you any software). 22 is the correct *internal* port number for ssh, but I suggest you *don't* use port 22 externally - pick a random number somewhere between 20000 and 50000 instead. PuTTY can easily be told what port number to use, and a little bit of security by obscurity will reduce your exposure to random Internet port scanning somewhat.

---

