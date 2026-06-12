---
title: "Not able to connect to internet"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Skipper' on 2010-03-13
Problem Fixed!!

---

### Post by n0dix on 2010-03-13
Wireless or wired?
Do you have router?
Which is your network card?
Please, post more details about your configuration.
Also read in the forum similar problems.

---

### Post by Skipper' on 2010-03-13
Wired
Router
D-Link 802.11g/2.4GhZ

---

### Post by lidex on 2010-03-13
Go to a terminal: "applications>accessories>terminal" and enter this command:
```
sudo lshw -C network
```
Enter your user password when prompted. Include the output in your next post.

---

### Post by Skipper' on 2010-03-14
> **lidex said:**
> Go to a terminal: "applications>accessories>terminal" and enter this command:
```
sudo lshw -C network
```Enter your user password when prompted. Include the output in your next post.

Still not working...

---

### Post by Choragos on 2010-03-14
Can you please cut and paste the text from the terminal when you run that command?  Can you also type 
```
ifconfig
```which will show you if linux knows that a network connection is there in the first place?  In a working system, you should have something called eth0 with some information.

---

### Post by Skipper' on 2010-03-14
> **Choragos said:**
> Can you please cut and paste the text from the terminal when you run that command?  Can you also type 
```
ifconfig
```which will show you if linux knows that a network connection is there in the first place?  In a working system, you should have something called eth0 with some information.

When I tried the ifcommand it show alot of info
and something called eth0

---

### Post by lidex on 2010-03-14
> **Skipper' said:**
> Still not working...

That's not meant to fix anything, only to supply info on your system for us to diagnose. Run the command again and post the terminal output here.

---

### Post by Skipper' on 2010-03-14
EDIT: Problem Fixed!

---

### Post by n0dix on 2010-03-14
> **Skipper' said:**
> EDIT: Problem Fixed!

Two things:
1. Which is the solution? Someone else can have the same problem
2. Add the Solved tag to the title.

---

