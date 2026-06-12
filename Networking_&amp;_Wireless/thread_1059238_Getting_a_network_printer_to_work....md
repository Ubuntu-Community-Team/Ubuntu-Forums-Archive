---
title: "Getting a network printer to work..."
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by turinturambar on 2009-02-03
I am running Intrepid on a Dell Latitude D610 laptop.  I am connected to my school's wireless network, on which there are several printers, one of which I want to print to.  

To add the printer, I go to System=>Adminstration=>Printing and click the "New" button.  The screen I get is attached as "addprinter.jpg".  I want to connect to the Sharp AR-M550U that is listed there, so I click it, and in the next screens it guides me through getting drivers for that model and installs the printer as "printer".  All well and good.  

But it won't print.  In openoffice writer, I hit control+p, print to "printer", and nothing comes out of the printer.  In the notification area, a printer icon even appears and then goes away.  But nothing comes out.  No error message or anything.  Not being able to find a solution yet, I thought I'd ask the forum directly.

Thanks for any help you can give me.

:)

btw I'm a fairly experience Windows user but just switched to ubuntu a month and a half ago, so please pardon my ignorance.

---

### Post by cariboo on 2009-02-03
Have you tried the cups web interface to see if there are any error messages? Open Firefox and in the address bar type:

[http://localhost:631](http://localhost:631)

you should see something like the attached screenshot, the rest is pretty self evident.

Jim

---

### Post by turinturambar on 2009-02-04
Thanks for the help.

I went through the web interface by clicking "add printer", putting in a name, selecting the printer I want, selecting a driver, and then clicking "add printer".  It then asks for a username and password.  Is that because of the school's network, or is it part of the cups system?  If its part of the cups system, what do I put in?

this is probably the problem, huh...

thanks.

---

### Post by turinturambar on 2009-02-04
I just tried putting in the username and password for MY laptop, and it installed just fine.

But then I went into Writer and tried to print a page and nothing comes out of the printer.  I can enter the print queue, and on the cups page you sent me to I can see the printer.  It says it is idle and accepting jobs.  But it won't actually print.

Do I need a cups password or a school password?

thanks.

---

### Post by vwidor on 2009-02-06
Same problem here.
There is no error message, but nothing comes out of the printer.
The log says the page was printed.

tcpdump only shows this lines (192.168.73.2 is the printer):
---
22:45:04.200498 arp who-has 192.168.73.2 tell 192.168.73.6
22:45:04.205242 arp reply 192.168.73.2 is-at 00:80:77:7a:c9:38
22:45:04.205277 IP 192.168.73.6.51704 > 192.168.73.2.9100: S 2331739507:2331739507(0) win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
22:45:04.213118 IP 192.168.73.2.9100 > 192.168.73.6.51704: S 378262245:378262245(0) ack 2331739508 win 4096 <mss 1460>
22:45:04.213169 IP 192.168.73.6.51704 > 192.168.73.2.9100: . ack 1 win 5840
22:45:06.030184 IP 192.168.73.6.51704 > 192.168.73.2.9100: P 1:484(483) ack 1 win 5840
22:45:06.039725 IP 192.168.73.2.9100 > 192.168.73.6.51704: . ack 484 win 4096
22:45:06.770127 arp who-has 192.168.73.5 tell 192.168.73.129
22:45:11.040751 IP 192.168.73.6.51704 > 192.168.73.2.9100: F 484:484(0) ack 1 win 5840
22:45:11.048642 IP 192.168.73.2.9100 > 192.168.73.6.51704: . ack 485 win 0
22:45:11.053079 IP 192.168.73.2.9100 > 192.168.73.6.51704: FP 1:1(0) ack 485 win 0
22:45:11.053098 IP 192.168.73.6.51704 > 192.168.73.2.9100: . ack 2 win 5840
---

---

