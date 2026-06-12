---
title: "Finding the IP of my printer on the network"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by xigen on 2011-02-01
I am having trouble getting my ubuntu 10.4 system to 'see' my network printer (brother HL-6050DN).

1) how do I find the IP address of my printer?
2) are there any known issues with my topology?  

ubuntu box      | 
storage         |  --> switch --> router
printer         |

---

### Post by mips on 2011-02-01
[http://welcome.solutions.brother.com/BSC/public/eu/gb/en/faq/faq/000000/002600/000056/faq002656_000.html?reg=eu&c=gb&lang=en&prod=hl6050dn_all&Cat=112](http://welcome.solutions.brother.com/BSC/public/eu/gb/en/faq/faq/000000/002600/000056/faq002656_000.html?reg=eu&c=gb&lang=en&prod=hl6050dn_all&Cat=112)
> 
B: How to check the IP address of your Brother machine


If your Brother machine was purchased Network Ready, then the IP address can be determined via the control panel of the Brother machine or by printing a Report Page which is called **User Settings** list or **Network Configuration (Network Config)** list. For more information on how to find the IP address on the control panel of the machine or print a Report Page, please refer to the User's Guide or Network User's Guide for your machine. The latest User's Guide or Network User&#8217;s Guide is available in the Manuals section.




C: How to verify that both IP addresses of your PC and the Brother machine are correct and located in the same segmentation.


C-1: Please make sure all the followings points from a to c are applicable for both IP addresses of your PC and your Brother machine.


The addresses (bold texts) are same as below:


PC IP address: 192.168.1.2
Brother machine IP address: 192.168.1.199


The end addresses are different and the address is within 2-254.


The addresses are unique among all connected devices on your network environment.

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser)
[https://help.ubuntu.com/10.04/printing/C/printing.html#network](https://help.ubuntu.com/10.04/printing/C/printing.html#network)

---

### Post by xigen on 2011-02-01
success !

It was a simple matter of putting the printer IP address (192.168.2.6) in the printer settings.

Phew.  3 weeks of low-level-headache ... solved.

Best,

MW

---

