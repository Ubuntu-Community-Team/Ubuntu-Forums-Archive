---
title: "3COM509TP not detected during install"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by jamesr on 2006-02-09
Hi All,

I have just installed Kubuntu 5.04 (Hoary Hedge where do these names come from?).

The Installation was satisfactory in the end after several installs with so far one outstanding point, Networking is not setup. The nic 3Com509TP was not recognised in the automatic procedure whereas during an "expert" install I was able to install the nic manually.

As a follow up I found a reference
> 
DNAPPER
just found this in bugzilla:
<https://bugzilla.ubuntu.com/show_bug.cgi?id=11517>

--Quote--
Bugzilla Bug 11517 - No support for 3c509 in instaler

I tried instaling Hoary on a system with a 3c509 nic. The standard installer
would not find it, and the expert installer would allow me to select it from a
list of cards.
This enables it during installation but I had to put 3c509 in /etc/modules to
enable it in the installed system.

3c509 is an isapnp card so it should be safe to probe it (loading the module
fails if the card is not present).
--End Quote--


I did the following
sudo modprobe 3c509
no errors
but ifconfig only shows lo

but ifconfig eth0

shows info 

2 questions

1) what is the dhcp command? In debian it is dhcpcd but that does not work in Kubuntu/Ubuntu. Is it Dhclient but do I have to do 
sudo dhclient

2) What  file do I need to edit make process automatic ie during Boot up.
In Corel I could go into Console before starting KDE and run a little command file.

---

### Post by jamesr on 2006-02-09
Hi All,

 perhaps I should done a little more googling and reading before firing off this question.

But I have answered some of my questions 

> 1) what is the dhcp command? In debian it is dhcpcd but that does not work in Kubuntu/Ubuntu. Is it Dhclient but do I have to do 
sudo dhclient


Answer is yes 

> 
2) What file do I need to edit make process automatic ie during Boot up.


First edit modules file
sudo nano /etc/modules

and add a line
3c509 
at the line of the file

Second edit interfaces file 

sudo nano /etc/network/interfaces

add lines
auto eth0
iface eth0 inet dhcp

I am still unable to update the clock in the boot up sequence but seems to be a resolver issue, ie next problem to solve.

---

