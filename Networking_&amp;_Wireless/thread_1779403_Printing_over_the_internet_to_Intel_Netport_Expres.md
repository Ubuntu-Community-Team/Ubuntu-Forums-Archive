---
title: "Printing over the internet to Intel Netport Express"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by ibod on 2011-06-10
Hi 
My first question after reading the manual and doing a load of googling.

Is it possible to to print to a printer on a netport express 10/100 over the internet ?

I have printing working from all computers on the same internal network as the netport express. 

But I have two phone lines with two routers / ISP's 

And I would like the computers on the other network to be able to print the the first networks printer.

---

### Post by DavePlummer on 2011-06-10
A quick Google search returned many articles on setting up Internet Printing Protocol (IPP) with the Netport Express, so it should be possible.

---

### Post by ibod on 2011-06-10
Hi 
I read these but could not get the computer to see the printer over the internet 

In add printer 
Network Printer
Internet Printing Protocol

I entered :-

Host:  [external IP address of the other network]  
Queue: [/LPT2_PASSTHRU]

and when I click [Verify]

I get the error 

"Inaccessible This print share is not accessible"  

Anyone know where I am going wrong

PS I have the port the print server listens on forwarded in the router to the internal IP of the print server.

---

