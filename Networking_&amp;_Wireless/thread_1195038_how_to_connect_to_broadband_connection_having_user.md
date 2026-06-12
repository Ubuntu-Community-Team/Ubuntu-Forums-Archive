---
title: "how to connect to broadband connection having username and password???"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by rushikesh988 on 2009-06-23
hello friends can somebody tell me how to connect to the broadband having username and password ...


I got a modem from my ISP and In windows I used it to connect to internet by choosing an option " A broadband that requires username and password "  so can somebody tell me how to do it in ubuntu

---

### Post by nnamdi on 2009-06-23
you could use "wvdial" connect the modem to your comupter then type
```

sudo wvdailconf 

```
it should detect your modem, then edit the paameters by using gedit or vi

```

sudo gedit /etc/wvdial.conf

```
then input the necessary parameters dont forget to remove ; in front the them then save it 
then go back to your terminal type
```

sudo wvdial

```
it would connect and pls dont close the terminal ok 
have fun!!!:popcorn:

---

### Post by rushikesh988 on 2009-06-23
hey I have used this commands before to connect my MOTOROLA MOBILE FOR INTERNET    but will it work for BSNL ethernet port modem

---

### Post by nnamdi on 2009-06-23
hmmmm hope ur modem is not a closed source hardware and which of the ubuntu are u using?

---

### Post by jonobr on 2009-06-23
Hello


Just to take things from the start,

what type of modem is it?
How do you connect to it?

Is this dsl or dialup?

Are your presented with an ethernet port, or a telephone line or something?

Theres a lot more details needed here

---

### Post by rushikesh988 on 2009-06-23
> **nnamdi said:**
> hmmmm hope ur modem is not a closed source hardware and which of the ubuntu are u using?

I am using UBUNTU JAUNTY JACKPOLE

---

### Post by rushikesh988 on 2009-06-23
> **jonobr said:**
> Hello


Just to take things from the start,

what type of modem is it?
How do you connect to it?

Is this dsl or dialup?

Are your presented with an ethernet port, or a telephone line or something?

Theres a lot more details needed here
It is wired external  modem . 
I used to connect to it with ethernet port.
It is DSl (It requires username and password and No no have to dial )
I have presented it with ethernet port.
I am using jaunty jackpole .
my modem have 3 ports 1) Telephone line in 2)ethernet port to connect to my pc 3)power

---

### Post by jonobr on 2009-06-24
Hello

Thanks for the info.

Im guessing you have used a splitter cable to filter your pots (telephone) line from your dsl and the dsl end goes into the modem which presents  the pc with ethernet.

In that case could you post the results of ifconfig
and also execute the command dhclient 
and see if ifconfig changes.

If it doesnt any output from dhclient may help

namste

---

### Post by rushikesh988 on 2009-06-24
namaste  he he

---

