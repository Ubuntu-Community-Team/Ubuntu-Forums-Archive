---
title: "Outdoor router client manager"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by Gangsingen on 2006-02-27
First of all, I´m new to Linux, and my english isn´t the best, but hopefully I can form my question correct enough to make you understand what I mean.

I get connected to the internet via my ISP through a wireless connection. I am connecting to an outdoor router via a pc-card (Orinoco silver), and a pretty big antenna on my roof.

In windows xp I connect to my ISP through a software, Client manager. In the client manager software I have to choose:

1. Profile Name (doesnt matter)
2. Connection type (set to outdoor router client)
3. License key (ZMK9-OM3S-1ZG3-I2OC-JINS *just an example*)
4. Pass phrase (public)
5. Frequency channel (13)
6. Network id (2)
7. Transmit rate (high)

Now I want to use Linux instead, and connect to my ISP. The question is: Is there a "Client manager" software for Linux?

Thanks!

//Jukka

---

### Post by mips on 2006-02-27
Who is the ISP and do you have a link to their site ?

---

### Post by Gangsingen on 2006-02-27
The ISP is the municipality I live in. I´ve asked them about the client software for Linux, and they didn´t know. The website is  [http://www.gagnefselverk.se/?page=Bredband](http://www.gagnefselverk.se/?page=Bredband)   and there isn´t much information at all.

---

### Post by mips on 2006-02-27
I'm sure there must be some way to do it but unfortunately I do not know how.
Should be able to use a script or something like that to relay the same information.

How do they cater for OSX etc ?

Do you have a username & password or do you just use a license key.

The website has no usefull information and I suspect the municipality got some 3rd party company to install & manage the network. Maybe find out who they are and ask them for help.

---

### Post by Gangsingen on 2006-02-27
Thank you for your help!

I don´t insert any other info in the Client manager than those things I described in my first post. All hardware needed for the connection is provided by the ISP, because the license key works for one single MAC-number. The license key also determines the speed of the connection.

I´ll give the a call tomorrow to figure out how to get it working!

Again, thanks for your help!

//Jukka

---

### Post by Swappo on 2006-03-10
Did you get it to work?

I have the same ISP as you and live in the same area.
I run Windows on my workstation and sharing the connection from that computer to my notebook with ubuntu on it.

---

### Post by Gangsingen on 2006-03-23
Nope. I haven´t found any solution yet...but I can harly accept that there´s no way to get it working in Linux... :(

---

### Post by mips on 2006-03-29
I looked & looked and could not find anything. The suppliers mention there is NO Linux/MAC ORC software.

I tried to test the software but it would not work seeing I don't have a orinoco card.

The ORC uses a miniport NDIS driver.

---

### Post by mips on 2006-03-31
I think I *"might"* have found a ORC for linux but I *"think"* it is for RedHat7.3 or something of the sorts. Will keep you posted.

This software uses proprietry TurboCell technology. As far as I can tell it is not even being further developed for existing platforms.

Edit, looking at the file contents and it is for windows only. I downloadloaded something else which has Linux source code but it looks like the wavelan2 driver only.

After looking at the source a bit more it looks like it allows you to define a License Key etc. I have contacted the author of the code for assistance.

---

### Post by Gangsingen on 2006-04-11
Thank you very much mips!

I will keep checking this thread, if you find a solution for us. thanks again!

//Jukka

---

### Post by mips on 2006-04-11
[QUOTE=Gangsingen]Thank you very much mips!

I will keep checking this thread, if you find a solution for us. thanks again!

//Jukka[/QUOTE]

Right now I'm pretty stumped. I've e-mailed the source code to Lambert and asked for his assistance.

---

