---
title: "problems getting Ndiswrapper on 10.04"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by JesseJones on 2010-05-12
hey all,

I've just installed 10.04 netbook remix on my samsung n-130 netbook. Wireless isn't working. I cant seem to find a linux driver for my card (a realteck8191 i believe). I am trying to get the windows drivers to work using Ndiswrapper following a guide I found here 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

however when I get to step

2.2. Installing Packages

it tells me to download a file based on what version I am running. the most recent version in the list is 9.10 I am however am running 10.04. What do I do? will it still work if I dl the 9.10 version?

or anyother solutions?

any help would be appreciated!!

J.

---

### Post by oleink on 2010-05-12
> **JesseJones said:**
> hey all,

I've just installed 10.04 netbook remix on my samsung n-130 netbook. Wireless isn't working. I cant seem to find a linux driver for my card (a realteck8191 i believe). I am trying to get the windows drivers to work using Ndiswrapper following a guide I found here 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

however when I get to step

2.2. Installing Packages

it tells me to download a file based on what version I am running. the most recent version in the list is 9.10 I am however am running 10.04. What do I do? will it still work if I dl the 9.10 version?

or anyother solutions?

any help would be appreciated!!

J.

It should work all the same as long as the card existed during 9.10

---

### Post by JesseJones on 2010-05-12
it did work,

I was able to get the driver and load it with Ndiswrapper.

It worked, I think... The driver shows up and it says hardware present. But still no wireless signals.

the guide I was following

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

says to (3.6.2. Configuring Wireless Network Settings using network-admin (Network Admin))

first step is to Open the Networking Admin tool (System | Administration | Networking)

only problem is there is no networking under System-Admin on UNR 10.04

any ideas what I should do next?

---

### Post by Crio on 2010-05-13
May be they meant NetworkManager ?  It is used for network config in standard Ubuntu, though I have no idea about UNR specifics

---

