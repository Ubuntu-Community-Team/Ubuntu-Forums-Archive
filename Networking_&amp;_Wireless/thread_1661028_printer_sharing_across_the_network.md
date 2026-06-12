---
title: "printer sharing across the network"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by ubun2warrior on 2011-01-06
Hi  i have a printer which is shared across the network. All the computers have ubuntu installed. I want that some computers should not be allowed to use this printer.   Please tell me what should i do ??  ubun2warrior

---

### Post by ubun2warrior on 2011-01-06
i want to block some computers from using the network printer which is shared on the network...

---

### Post by mickwombat on 2011-01-10
How are you sharing this printer?

If it is via Samba, then you can just have an allowed list for the $print share or a block list.  This can be done either using the username or the ip address of the computers if they have static addresses.

---

### Post by ubun2warrior on 2011-02-20
hi

i have samba installed. how do i create a allowed list or block list for the print share.i mean where in the system do i edit/create this list.
the systems do have a static ip.

rgds

---

### Post by ubun2warrior on 2011-02-22
hi

any suggestions ??

rgds

---

### Post by ubun2warrior on 2011-03-05
> **mickwombat said:**
> How are you sharing this printer?

If it is via Samba, then you can just have an allowed list for the $print share or a block list.  This can be done either using the username or the ip address of the computers if they have static addresses.

hi

where should i create this list, please explain ...

regards

---

### Post by ubun2warrior on 2011-03-29
can someone plz tell me how to create a block list step by step

---

### Post by Morbius1 on 2011-03-29
I haven't done this in a very long time but this can be done using the CUPS server itself. This is from my notes:

I have a printer named "HPprinter":

Edit /etc/cups/cupsd.conf as root:
```
gksu gedit /etc/cups/cupsd.conf
```Add the following to the end of the file:
```
<Location /printers/HPprinter>
         Order Deny,Allow
         Deny From All
         Allow From 127.*
         Allow From 192.168.0.101
         Allow From 192.168.0.104
</Location>
```Save the file and restart cups:
```
sudo service cups restart
```
The only hosts that can access the printer in this case was local, 192.168.0.101, and 192.168.0.104

You would have to substitute:

- your own printer name for HPPrinter
- and you would have to add a new "Allow From ... " line for every ip address that you want to grant access to that printer.

That was it. If it doesn't work then just remove the lines you added and restart cups again.

---

### Post by irv on 2011-03-29
> **Morbius1 said:**
> I haven't done this in a very long time but this can be done using the CUPS server itself. This is from my notes:

I have a printer named "HPprinter":

Edit /etc/cups/cupsd.conf as root:
```
gksu gedit /etc/cups/cupsd.conf
```Add the following to the end of the file:
```
<Location /printers/HPprinter>
         Order Deny,Allow
         Deny From All
         Allow From 127.*
         Allow From 192.168.0.101
         Allow From 192.168.0.104
</Location>
```Save the file and restart cups:
```
sudo service cups restart
```
The only hosts that can access the printer in this case was local, 192.168.0.101, and 192.168.0.104

You would have to substitute:

- your own printer name for HPPrinter
- and you would have to add a new "Allow From ... " line for every ip address that you want to grant access to that printer.

That was it. If it doesn't work then just remove the lines you added and restart cups again.

And don't forget you have to have all static ip address on all your pc's. If they are set to dynamic they will change and this will be a problem.

---

