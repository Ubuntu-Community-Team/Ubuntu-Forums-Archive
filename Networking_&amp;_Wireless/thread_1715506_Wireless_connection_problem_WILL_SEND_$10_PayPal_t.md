---
title: "Wireless connection problem WILL SEND $10 PayPal to whoever provides a fix!!!!!!!!!!!"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by mydock on 2011-03-27
So, heres the deal! I am an experienced programmer who loves to code. It has been my biggest hobby since I have been 15 years old. I Recently had twins (11 months old on march 27th) and had to sell all of my servers, computers, and software program rights/licenses.

All I have been wanting to do lately is start back up. I got a great job managing and cooking at a popular restaurant chain and finally got my money back up. Although I have a decent paying job, I still can't afford to just shell out hundreds for a new laptop/desktop, so I bought an old Toshiba Satellite Pro 4600 running win xp pro for simple coding and internet browsing purposes! 

Anyway, I love linux and am sick of windows, not to mention the version of windows on this laptop is so screwed up and plaqued with virus, it takes me an hour to reboot, connect to the internet to post one simple forum post.

I decided to go with ubuntu 10.4. Never used Ubuntu before, but I already love it, exept for one thing! I CANNOT CONNECT TO MY WIRELESS ROUTER FOR ANYTHING!!!!
I am beyond frustrated. I first installed 10.10, searched online for a fix and most people were saying they downgraded to 10.4 and it fixed the problem. 

[B]My problem since 10.4 is, I simply cannot connect to my wireless router!

Everything is valid, the DNS, IP, etc. I can obviously connect viaWindows, but not in ubuntu 10.4. It shows up under wireless, I go to connect, and all the bars flash for about a minute. After that, it states that I am disconnected and offline. I have tried multiple times to no avail. I have searched everywhere for the fix, and this is no straight answer. I have tried EVERY step in the written ubuntu help knowledgebase  and searched online for hours for a fix. I have tried every suggestion, from installing BS packages to writing command terminals for a fix.[/B]

THE PROBLEM IS SIMPLE! I cannot connect to my wireless network. Is it really that hard to find a fix? I shouldn't have to work for hours to get it to work. Im just so frustrated, and all I want to do is get ubuntu up and running with networking. I know my laptop is old, but that cant be the reason, why could I connect in XP and not on here? PS, I am running off my neighbors router. Its actually my router. He has internet, I asked him if I could use it if I gave him a router (since he has an xbox 360, all he wanted was xbox live), so rj45 wired ethernet is not an option for me. Im SO frustrated and all I want is to run ubuntu with internet. Thats why I WILL send $10 to whoever gives me a fix via PayPal instantly!!!!!

I would paste my wireless info here but I cannot seem to keep the copy after booting from ubuntu back to windows and refuse to write down all of that crap and manually type it on here! 

PLEASE HELP!! And please don't tell me to google it or to search harder, I have searched everywhere, and cannot find [B]a straight answer/fix!

THANK YOU!!!!!:P
[/B]

---

### Post by spiky001 on 2011-03-27
Hi I probably wont help much but have you tried running off of live cd? Can you connect to internet while using cd? And you will need the result of lspci to find out what wireless card you have. If you look at the bottom of output it shold mention wireless card post that part

---

### Post by mydock on 2011-03-27
Live CD? Sorry, Im new to Ubunutu, not sure what you mean by that...

But I insalled ubuntu through download, and used daemon tools lite to mount the image, and installed the boot helper to boot to ubuntu.

There has to be some way to connect to my router? This is the most frustrating thing. What good is it if I cant connect to the internet through wifi???!

---

### Post by spiky001 on 2011-03-27
Ok sorry If you download the ubuntu cd there is an option to run the OS from cd without changing PC you can check if all works ok before installing. It is also a good idea to have eth0 connected while installing it helps to find drivers as need be

---

### Post by bkratz on 2011-03-27
> **spiky001 said:**
> Hi I probably wont help much but have you tried running off of live cd? Can you connect to internet while using cd? And you will need the result of lspci to find out what wireless card you have. If you look at the bottom of output it shold mention wireless card post that part



Additional note. If you drop to the terminal (Applications>>accessories>>terminal) and enter


```
lspci >> ~/Desktop/lspci.txt

```

It will create the requested file on your desktop which you then can transfer to a thumbdrive to post the requested output from the windows system.  It might be slow, but other requested inputs can be similarly created.

---

### Post by dacoolio on 2011-03-27
I'd assume you have the drivers for the wireless card if you can attempt to connect with it. Is your wireless network using WEP or WPA? Maybe something with those settings is throwing it off. Maybe try resetting the wifi to being an open network for a few minutes and test it again. Good luck :)

---

### Post by Joel.S123 on 2011-03-27
I think it's an Agere Systems MPC13A-20/R card.

---

### Post by mydock on 2011-03-28
> **dacoolio said:**
> I'd assume you have the drivers for the wireless card if you can attempt to connect with it. Is your wireless network using WEP or WPA? Maybe something with those settings is throwing it off. Maybe try resetting the wifi to being an open network for a few minutes and test it again. Good luck :)

Its an unsecured network... is that what you mean by resetting to an open network?

There is no password for it, Id see that as being a problem, its problem enough on this old computer connectijng to wireless networks with passwords, always telling me the password has to be 40 or 104bits or whatever even know its the right password!!


But im not sure if I have the right drivers loaded for it. 
It says the card is a intel corporation 82801 mobile pci bridge rev 13 
it also says intel corporation 82815 chipset agp bridge rev 11

this has become extremely frustrating so thats it ubuntu just doesnt work with wireless networks!?

Still willing to send somebody $10 to give me a correct fix, will even raise it to $20! Getting desperate...

---

### Post by mydock on 2011-03-28
Ok so I just checked the wireless cards supported in the wiki, and mine doesnt seem to be listed.

So thats it then? Ubunutu is no good for me!? Man thats really a shame if so, I really want to run ubuntu, I love it already, really like the software center.

If this is true, can you guys suggest any other linux OS thats similiar to ubuntu that got similiar features such as the application center?

If I can still connect even know my wireless card isnt supported, wtf do I do to make it work!?

:(

---

### Post by walt.smith1960 on 2011-03-28
One solution would be to buy a USB adapter that is supported.  This is one that has been plug & play for me since 9.04:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152&Tpk=trendnet%20tew-424UB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152&Tpk=trendnet%20tew-424UB")

I keep this one around just because Ubuntu really needs a network connection to be set up.  How to download updates and restricted software without a network connection?  It's simple with a wireless adapter that is recognized "out of the box".   I have two other wireless N USB adapters-Netgear WNA1100 & TrendNet TEW-649UB but they both need (fairly easy) tweaks in distros prior to 11.04.  They're both plug & play in 11.04.

---

### Post by skypie on 2011-03-28
This may Help,I installed oracle Virtual Box and installed Ubuntu it pcks up you Computers connections instantly,I have a Huawei220 and it wouldn't intsall in Ubuntu.
But in Virtual instantly!I know it's cheating but now I can use and update  hope this helps

---

### Post by Hippytaff on 2011-03-28
If you can run the wireless script (link below) and post the wireless results it will provide some details that might help people diagnose the problem.

---

### Post by mydock on 2011-03-28
> **Hippytaff said:**
> If you can run the wireless script (link below) and post the wireless results it will provide some details that might help people diagnose the problem.
Will do. Ill post it ina little bit here

Say I downloaded mandriva, fedora or debian, would I have the same problem?

---

### Post by Hippytaff on 2011-03-28
> **mydock said:**
> 
Say I downloaded mandriva, fedora or debian, would I have the same problem?
It's hard to say without knowing what is wrong...try it :-)

---

### Post by TBABill on 2011-03-28
> **mydock said:**
>  
I would paste my wireless info here but I cannot seem to keep the copy after booting from ubuntu back to windows and refuse to write down all of that crap and manually type it on here! 
 
PLEASE HELP!! And please don't tell me to google it or to search harder, I have searched everywhere, and cannot find **a straight answer/fix!**
 
**THANK YOU!!!!!:P**

 
Seriously, you will need to help us out to help you out. You can't say you refuse to give us info but want us to hand you a fix. Not trying to sound rude, but we can't just imagine what your hardware is. 
 
Easy fix to the problem. Get a Flash Drive and copy the info into a text file. Then restart into Windows and open the file, paste it here. or just write down the info from ```
lspci
``` or ```
lsusb
``` that starts with NETWORK. 
 
Once we know your hardware it'll be much easier to help. Till then we're just guessing. And do us a favor, donate the $10 to an open source project or a charity instead of trying to incent users to help. We do it because we want to, not because someone offers cash.

---

### Post by mydock on 2011-03-29
> **TBABill said:**
> Seriously, you will need to help us out to help you out. You can't say you refuse to give us info but want us to hand you a fix. Not trying to sound rude, but we can't just imagine what your hardware is. 
 
Easy fix to the problem. Get a Flash Drive and copy the info into a text file. Then restart into Windows and open the file, paste it here. or just write down the info from ```
lspci
``` or ```
lsusb
``` that starts with NETWORK. 
 
Once we know your hardware it'll be much easier to help. Till then we're just guessing. And do us a favor, donate the $10 to an open source project or a charity instead of trying to incent users to help. We do it because we want to, not because someone offers cash.
  Working on that now. Itsjust very time consuming, having to boot into ubuntu and back to xp, it literally takes30 mins to xp to boot up!!!!!!!!!!!!!!! And will do, Im going to donate the leftover funds in my paypal account to GNU, thanks for the suggestion

---

### Post by d3v1150m471c on 2011-03-29
```

#this will show you your wifi device
lspci | grep -i network

```Post the output here for additional help. Also, personally i'd rather you just keep the money. helping another linux user is payment enough, or rather donate it to FOSS projects you use and/or Ubuntu. Once you get the name of your wireless device you can do a google search for newer or different drivers for it. there is a decent chance you will be able to install them from the repositories if you find them but they may be source code and if so we can walk you through it. If you just hooked your pc up via ethernet you won't have to keep switching operating systems to solve the problem.

```

#if you can get a new driver from the repos:
sudo apt-get install <name of the package>

```if it's source code or comes with instructions be sure to read them carefully.

---

