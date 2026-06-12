---
title: "How to print from Leopard to Ubuntu ?"
date: 2008-03-26
forum: Mac OSX
---

### Post by MrGando on 2008-03-26
Hi guys , I have done what I usually thought would work to print from Leopard to Ubuntu .

1) I enabled shared printers in ubuntu.
2) Went to my Leopard machine went to localhost: 631

I chose ipp , gave the thing the url to my printer ( tested in safari ) 

[http://192.168.0.100:631/printers/LaserJet-6MP](http://192.168.0.100:631/printers/LaserJet-6MP)

192.168.0.100 is my ubuntu server , LaserJet-6MP is the exact name of the printer.

Chose the LaserJet 6 MP driver 

When I try to print in leopard it actually sends a job somewhere, but ubuntu is not printing a thing. 

:(

Could you guys help me ????

---

### Post by sillyxone on 2008-03-26
you have to add the printer in OSX a special way. I did this with Tiger, not sure about Leopard.

When you go to add a printer, instead o selecting IPP and type in the URL, hold Option and click on "More Printer ..."

In the popup dialog box, select "Advanced" in the listbox at top, in "Device" listbox, choose "Internet Printing Protocol using HTTP", give it a name, and type "http://192.168.0.100:631/printers/LaserJet-6MP" in the URI box. Then select the printer model as usual.

---

### Post by MrGando on 2008-03-26
Hi, thanks for your quick reply.

I think that method is not working in leopard.

I tried the following

[http://localhost:631](http://localhost:631)

Chose Internet Printing protocol ( not ipp , but HTTP )

And then selected the HP LaserJet Driver . 

Not working :(

Anyone has this problem ?

---

### Post by sillyxone on 2008-03-26
just curious, when you are on the Mac, you're supposed to use 192.168.0.100:631 or whatever the IP of Ubuntu machine is, instead of  localhost:631. Can you be a little more clear?

localhost refers to whatever the machine you are working on, alternatively you can use 127.0.0.1

---

### Post by MrGando on 2008-03-26
when I said localhost:631 , I meant that I did that in localhost and tried to add the printer via the CUPS web interface  ( 1.3.6 )

That's what I always did in Tiger and I thought it worked , unless I'm missing something here.

---

### Post by sillyxone on 2008-03-26
> **MrGando said:**
> when I said localhost:631 , I meant that I did that in localhost and tried to add the printer via the CUPS web interface  ( 1.3.6 )

That's what I always did in Tiger and I thought it worked , unless I'm missing something here.


the problem is, when you say localhost, it could mean the Ubuntu machine, or the Mac machine, depending on whichever you were working on.

let me give an example of how I setup a CUPS server on Ubuntu:

- my Ubuntu machine IP is: 192.168.0.100
- my Mac machine IP is: 192.168.0.21
- my printer happens to be a network printer with IP 192.168.0.150, if you connect the printer directly to Ubuntu machine via USB or parallel port, ignore this number. The printer has sharename of [http://192.168.0.100:631/printers/MySpecificPrinter](http://192.168.0.100:631/printers/MySpecificPrinter)

- when I'm on my Ubuntu machine, I would point the browser to localhost:631, or 127.0.0.1 and I can manage MySpecificPrinter

- when I'm on my Mac machine, I would point the browser to 192.168.0.100:631 to REMOTELY manage MySpecificPrinter. If I point my browser to localhost:631 while I'm on my Mac, I would be managing whatever printer setup on my Mac (OSX use CUPS too, and actually CUPS is copyrighted by Apple). 

Thus, when you are on your Mac, add printer by using Print Center, don't use the browser. Use the web browser if you want to REMOTELY manage the printers on Ubuntu server, by pointing it to 192.168.0.100:631.

Again, localhost or 127.0.0.1 represent the machine you are working on. For example, if I'm on my Mac, then localhost, 127.0.0.1, and 192.168.0.21 all point the same Mac machine. Similarly, if I'm on the Ubuntu, localhost, 127.0.0.1 and 192.168.0.100 all point to the Ubuntu machine.

You just need to state the problem clearer now.

---

### Post by Foster Grant on 2008-03-30
Silly's on the right track ... use Print Center (and thus Apple's Bonjour implementation of Zeroconf/Avahi) to set up the printer.

---

### Post by MrGando on 2008-03-30
Hi guys, when you talk about print center, do you mean

System Preferences -> Print & Fax ?? ( On Mac OS ) ?

---

### Post by Foster Grant on 2008-04-02
> **MrGando said:**
> Hi guys, when you talk about print center, do you mean

System Preferences -> Print & Fax ?? ( On Mac OS ) ?

That should be it.

---

