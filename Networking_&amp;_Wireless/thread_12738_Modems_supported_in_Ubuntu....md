---
title: "Modems supported in Ubuntu..."
date: 2005-01-26
forum: Networking &amp; Wireless
---

### Post by FXWGBill on 2005-01-26
Can someone please give me a list or some suggestions as to what modems or model modems are supported in Ubuntu.  I have seen all kinds listed, but I would like to know for positive I will have no trouble.  It's hard to tell anymore what is a Winmodem and what isn't.  So if I could have a few examples of FULL modems tht Ubuntu will recognize on installation, I would very much appreciate it.

Thanx,

FX

---

### Post by cletusbaird on 2005-01-27
I too am having trouble getting ubuntu to recognize modems. However, I have run many other distros of linux and a good place to find out what is generally supported in linux is [www.linuxant.com](www.linuxant.com). I am assuming you have some kind of internet connection. :)

---

### Post by az on 2005-01-27
No.  Go to linmodems.org.  Linuxant only sells one modem driver.  linmodems.org has up-to-date information on just about all the modems that work under linux.  Linuxant is the only company to charge for their product.

Get a hardware modem.  You cannot tell by the name brand or price tag.  A usb external modem may or may not be a hardware modem.

If you want a software modem that has a gpl driver, you can try to find one based on the intel chip that can use the alsa snd8x10m driver.  Good luck, since it is never written on the box.  And intel has several chipsets.  In any case, these companies change hands so often that what is supported now, may not be next month.  So unless you want to run the same kernel for as long as you own your modem, you'd be stuck.

---

### Post by taken on 2005-01-30
What is a software modem?
Note: The question is geniune. I have never heard about them. (I am new to linux and computers in general) which is probably why I am having so many problems with making things work. :D

---

### Post by oldreb on 2005-01-30
Hello taken,

   A software modem is often called a win modem.  It is a cheap modem that uses windows software to do most of the modem work.  My laptop was always running hot and slow while online until I got rid of my win modem and installed a real modem.  I learned mine was a win modem from some online site that identified which modems were winmodems.

old reb

---

### Post by king_arthur on 2005-01-30
Hello FXWGBill,
     
     nobody here asking the most important question so far:
 
 [center][size=4]Do you **really** need an internal modem?[/size]
 [/center]
      
 Winmodems are internal modems i.e. a pci plugin cards. They have been designed specifically with Microsoft Windows in mind, hence, lots of problems with Linux.
  Al beit this is a bumpy ride, [Linuxant]("http://www.linuxant.com/drivers/") might offer the solution if you are prepared to pay for it. (I did try their free driver, which is limited in connection speed, a few years ago and it worked well)
     
   If you are not commited to a PCI-modem, buy yourself an old external 56k V90 standard modem _**any of them will work, no problem at all**_,  as they must obey to the at&t set of commands, provided you have the right cables for connecting to your [**Serial** / **RS**-232 **Port**]("http://www.beyondlogic.org/serial/serial1.htm").
     
     These days of aDSL and cable internet, you can find a second hand for only a few dollars on ebay.

---

### Post by oldreb on 2005-01-30
I have a laptop, connected to a Westell DSL modem via a usb cable.  I just loaded ubuntu on my spare HD.  Ubuntu offers to set up for a Ethernet cable but not a usb cable.   Later I discovered that I could save tons of work by just using the provided "ubundu live CD" on top of XP.

   Will it work if I install a pmcia Ethernet card in my laptop?  Can it be made to work with the USB cable?

    I was orginally trying Linux because win98 is a piece of crap, but XP is cool.  Now I am interested to try Ubuntu to look at a different system.

   Mandrake 8.2 was the last linux I tried. It was flakey and ran at half the speed of win98 dial up online.  It was prone to crash and wreck my HD. So I gave it up.  ubuntu loaded up with ease and I haven't had to run it on the typed in codes at all.  

    The main and only problem is getting online.

old reb

---

### Post by jonas73 on 2005-01-30
I'll re-ask FXWGBill's original question. Does anyone know of any internal modem that is recognized/supported during installation? And yes, unfortunately I do have to use an internal modem. Thanks!

---

### Post by az on 2005-01-30
"Does anyone know of any internal modem that is recognized/supported during installation?"

Sure.  Just about any internal _hardware_ modem.  There are too many brands to name, but they have three big chips on the board (or so), not just one or two.  This is of course a general rule since I have not seen every modem on the planet.

---

### Post by oldreb on 2005-01-30
Here is a link to win modem information. If your modem is a winmodem, then I assume it will not work for linux.

[http://start.at/modem](http://start.at/modem)

   The sales people I talked to, didn't know jack about winmodems but swore they had no such thing. 

    I used a list something like this to get a hardware Pcmcia modem and tossed my winmodem.  It is worth the investment to buy a hardware modem even if you don't use Linux.

old reb

---

### Post by FXWGBill on 2005-01-31
I have been doing some digging and searching around on this....  and So far have found ONE!!!  That says without a doubt it is an onboard controller type modem AND says Linux right in the dissertation.  It is also a pci type, I did find several ISA types, but that doesn't help me.

The model I found is:

Zoom model 2920

and it  looks like a site called ebuyer.com has about the best price so far, but you can do a search for that particular model and decide what you want to do.  What I am finding is from around 65 to 75 bucks...

I am still researching it, and if I find any other good ones, I'll try to post it...

Thanx,

FX

---

### Post by jonas73 on 2005-01-31
[http://www.usr.com/products/home/home-product.asp?sku=USR5610B](http://www.usr.com/products/home/home-product.asp?sku=USR5610B) also works. lists linux (kernel 2.3 and higher) in the specifications. newegg.com has it for $65.

---

### Post by king_arthur on 2005-01-31
oldreb,
 
 [QUOTE=oldreb]
 I was orginally trying Linux because win98 is a piece of crap, but XP is cool. Now I am interested to try Ubuntu to look at a different system.
    
 Mandrake 8.2 was the last linux I tried. It was flakey and ran at half the speed of win98 dial up online. It was prone to crash and wreck my HD. So I gave it up. ubuntu loaded up with ease and I haven't had to run it on the typed in codes at all. 
    [/QUOTE]
    
   We all may have our good reasons to switch over to Linux. 
  If you really believe that win-XP is "cool" and Mandrake is "flakey" and runs half speed, you better stay with win-xp. :cool:
    
    It will make your (computing) life a lot easier...

---

### Post by clparker on 2005-01-31
You know, I used to work for an ISP i should really rather leave nameless, but I was a Dial Up technician, People called me with their dial up problems, I worked there for a long time, and one thing they started doing after I quit was a move towards no suport whatsoever for Linux. Fact of the matter is simply this; Over 90% of the modems out there are what we in the industry call 'soft' or 'win' modems, that is they are dependent on software to do both compression, flow control, and error correction. A 'hard' modem actually has hardware within the device itself to do these things, those really are the modems that are practically guanteed to be Linux compatible. Many of the modems out there may or may not be linux compatible, belive me, i worked in the industry, the damned things are a dime a dozen. Dozens upon dozens of O.E.M's make the things, many are no longer supported, after buyouts, and busts. That's why i bought this USRobotics Modem, not because it was Linux compatible but a hardware modem, because it wasn't dependent on windows to do work for it. Do yourself a favor, go buy a U.S. Robotics modem that is a Hardware modem. You'll be glad you did.

---

### Post by az on 2005-01-31
Some examples:
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=44940&item=6740217668&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=44940&item=6740217668&rd=1)
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=44940&item=6739541549&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=44940&item=6739541549&rd=1)

These should go for under 40 or 50 dollars...




This is _not_ a hardware modem:  It is a controllerless modem.  No drivers should be required!
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=3693&item=6739303970&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=3693&item=6739303970&rd=1)

nor this one:
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=3693&item=6740462200&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=3693&item=6740462200&rd=1)
controllerless means two chips instead of three (some call it a semi-hardware modem)
Requires Pentium 233 upwards.  (Hardware modem does not have such restrictions.)



[http://search.ebay.com/pci-hardware-modem_W0QQsofocusZbsQQsbrftogZ1QQfromZR10QQsojsZ1QQcatrefZC6QQftrtZ1QQftrvZ1QQfsopZ1QQfsooZ1](http://search.ebay.com/pci-hardware-modem_W0QQsofocusZbsQQsbrftogZ1QQfromZR10QQsojsZ1QQcatrefZC6QQftrtZ1QQftrvZ1QQfsopZ1QQfsooZ1)

---

### Post by cletusbaird on 2005-01-31
I now have my old ISA 33.6k modem from an old 486 computer configured and running ubuntu linux. 
Since it is a hard modem albeit a slow one..it works with
All Mandrakes 7 thru 10.1, all Redhats 6.o thru Fedora core 3... and now Ubuntu as well. 
I don't have a lot of money, so recycle a lot of stuff others don't want.

 If I use the free 14.6 k trial modem for my winmodem(Rockwell HSF 56K) from linuxant and link it with the ISA.. I get 48.2. I didn't want to givem $15 for the driver.

 Neat thing is all the Linux distros  recognize the old ISA 33.6.     Windows XP doesn't..unless you do some special config tricks.

The Rockwell has no built in drivers for the XP Professional..but, if I tell windows Xp its a Fujitsu Modem it will work well at the 56K that the Modem was designed to run  Win 98 and Win Me at drivers are naturally avilable for it for those old windows.

Ubuntu wiki has  suggested to use sudo PPP config from any terminal , choose create a connection,leave name as a provider, follow the bouncing ball on the other questions,select dynamic if it applies, by follwoing the questions you can manually configure your modem..
If you are running windows as well ttys2 =COM3,ttys1=COM2 ...etc
After writing your configuration, go back in to Advanced -advanced option..add user...Add a PPP user.exit change and finalize.

If I confused anyone, please visit UBUNTU Wiki...because  this works if your modem can be configured for linux.

By the way my old dinosaur computer is a Pentium II with 20 mb hard drive.. with 
that old ISA modem...but,it works..at 300 mhz;but so am I ..retired 62 yr old systems installation and development engineer.

---

### Post by stuart on 2005-07-18
[QUOTE=FXWGBill]Can someone please give me a list or some suggestions as to what modems or model modems are supported in Ubuntu.  I have seen all kinds listed, but I would like to know for positive I will have no trouble.  It's hard to tell anymore what is a Winmodem and what isn't.  So if I could have a few examples of FULL modems tht Ubuntu will recognize on installation, I would very much appreciate it.

Thanx,

FX[/QUOTE]
 Hi

Hope it gets through this time last time I was kicked out but maybe it kept the reply so here it is again in case

Looks like any Company person or group promoting Linux has his work cut out to produce a product that works in toto and does not behave like a window beta release and don’t get me wrong I don’t love windows, I don’t have any choice if I want results.

Bottom line I am trying UBUNTU with the remote hope that someone has got his act together to resolve one of the biggest challenges of time laptop connectivity. I have tried most others just for the look and feel and the other funnies offered. So far no luck and the hours spent are very high.

What the world has forgotten is that it does not matter how nice anything looks GUI if you cannot get out to the world it is a waste of time. Most people who use laptops and move around i.e. road engineer salesman or whoever and international travelers or  engineers need to communicate. Now in worlds that do not have the rocket science networks ADSL and all the other fancy support mechanisms and goodies there is a problem( you still need a modem in many if not most instances). This goes one step further not all people can afford those fancy issues and Linux is designed to assist in catering for the not so fortunate markets. Then there is the country issue, welcome to my world (Or rather Mark Shuttleworth should remember the African problem as he used to be a South African).
Back to reality I have a Fujitsu Siemens C series notebook. After hours when not involved with the family I investigate many things. One of the things that is still not resolvable by Suse Mandrake Redhat and all the others is the Winmodem issue. Bill still has the upper hand. Until someone or the companies producing the goods throws money in the direction of the problem by providing the drivers for the hardware they produce ( AUDIO DISPLAY AND MODEM PLUS OTHERS), products such as Linux will play second fiddle to the fire breathing giant. I ask you who in his right mind buys a pretty decent laptop (There are many) to be mobile and then has to buy a separate modem, another Memory stick that will interface then run in dual boot so his Cell (Mobile )  PDA will Sync and Backup to Office 2000 as it does not to Open Office 2 (as there is no PDA Sync), buy another mouse so their USB mouse does not freeze up intermittently, struggles as the Acrobat Software for  secure document generation is up the spout. Then we move on to DVD issues so I still have to boot into windows to watch my legally purchase DVD, not to mention other software like MS Project and the likes of and I wont even get onto the subject of printers (no time).
Then the investigation fortunately I can play on windows at night to try and find software to get Linux to work. I have been everywhere downloaded close to 50 megs of drivers and recompiled packages all to no avail, things just don’t get going . 

So the system powers up on the laptop in one and more of the popular flavors of Linux and most of the browsers open and the Office Packages open and looks pretty, but it is not a solution.

In Africa we learn from the Lion. He is king and does not worry about the jackal getting a few scraps. Even a few jackals are not a problem people these are the scraps. And when the jackals fight over the scraps the lion does not raise an eyebrow. We need another lion to sort out the problem. I am sure old Bill Gates chuckles when he observes the various flavors of Suse Mandrake redhat slackware ubuntu and he says let them fight. Economics says focus on the minority percentage and all you can get maximum is the minority target.

I am afraid to say that it is going to be a long walk to the demise of windows if it ever happens. So far Superior knowledge, Superior tactics.

You see the world is a funny place once someone develops something of value or has something of value he attaches a price to it. So did dear Mr Gates. There is not such thing as a free lunch. You pay for what you get and it is free don't complain and don't expect the world. That you have to pay for and if you don’t (AKA free) you have to make other expensive plans to cover the shortfalls and you may as well bough the stuff in the first place.

The only way ban money, ban economics and ban exploitation. Not everyone wins the lottery

I keep on trying  in order to keep the brain stimulated, and If I am successful to resolving any of the issues I will inform the world. Sleep tight Mr Gates

On a lighter note Suse 9.3 is the best so far and at least they get half way there. Ask them Novel  they will be able to help in some instances.

Motto " Never Give Up"

---

### Post by dshadywun on 2005-07-18
[QUOTE=azz]No.  Go to linmodems.org.  Linuxant only sells one modem driver.  linmodems.org has up-to-date information on just about all the modems that work under linux.  Linuxant is the only company to charge for their product.

Get a hardware modem.  You cannot tell by the name brand or price tag.  A usb external modem may or may not be a hardware modem.

If you want a software modem that has a gpl driver, you can try to find one based on the intel chip that can use the alsa snd8x10m driver.  Good luck, since it is never written on the box.  And intel has several chipsets.  In any case, these companies change hands so often that what is supported now, may not be next month.  So unless you want to run the same kernel for as long as you own your modem, you'd be stuck.[/QUOTE]
 MAKE EASY MONEY ONLINE WITH PAYPAL!

PLEASE READ YOU WILL BE THANKING ME LATER   :)

Have you ever wanted to make some money online. I have not had much success up to this point. To be honest I am totally sceptical about any get-rich quick scheme I have ever heard about.

Well then I found this PayPal Money making guide. I read some more about it and saw people reporting that they had made a few thousands of dollars. Well of course I didn’t believe it. Would you.

Then I decided to try it. So I looked for a mailing list and sent 5 dollars to every person on that list then entered my name. It only cost me $25, which is cheap compared to what i made from it!!!

Now its time for the next stage,  posting my message on numerous message boards. The reason for posting messages is so u can get more people to send!

And the more people who send the more money you make and the more money they will eventually be making.

Hopefully there are enough people out there who will see this message and take the chance, so that this will work and make alot of people alot of money.

If you past this up now and relize later that this really works, you will regret not trying it sooner? If you start now just imagine all the money you will make in a few months it will definitly be in the thousands.

Ive been doing this for 3 months and already have $5,540. And theres still money coming in!! Im just trying to spread the word so that everyone can enjoy this as much as i am.

So here’s the 5 step plan.

1. Copy this letter and save it in your computer and/or on a floppy disk. I suggest you print this for future refrence. :)

2. Send 5 dollars to every PayPal account on the list below (If you don’t have PayPal sign up for one at this link: [https://www.paypal.com](https://www.paypal.com))

1) [email]krstic12@hotmail.com[/email]
2) [email]gatman973@yahoo.com[/email]
3) [email]nets45@walla.com[/email]
4) [email]tedd745@yahoo.com[/email]
5) [email]dshadywun1@yahoo.com[/email]

IMPORTANT: when u send the money please include the comments "Please add me on your mailing list" this makes this whole process legal.

Question:  Why send people money?         Answer: IF you dont send money to the e-mail addreses your chances of making money off this are slim. The reason for that is, When you send money and ask them to "Please add me on your mailing list" they will put your e-mail on there ads. Therefore your e-mail  will spread dramaticly over thousands of forums for people to see so will make you alot of $$$$$ MONEY $$$$$!!!!

 The next step is important so pay attention!

3. After sending the money to the paypal accounts, What you need to do is....

Remove the e-mail from the number 1 spot off the list. ( THIS PERSON IS NOW OFF THE LIST BUT IS NO DOUBT COUNTING ALL HIS MONEY!!!)
Then put the e-mail from the number 2 spot in the number one spot.
Then take the e-mail from the number 3 spot in the number 2 spot.
Then take the e-mail from the number 4 spot to the number 3 spot.
Then take the e-mail from the number 5 spot to the number 4 spot.

Ok now there is the last empty spot put your e-mail in this spot. So when your done it should look like the list below.

1) [email]gatman973@yahoo.com[/email]
2) [email]nets45@walla.com[/email]
3) [email]tedd745@yahoo.com[/email]
4) [email]dshadywun1@yahoo.com[/email]
5) YOUR E-MAIL

4. You could use this letter to send to your friends and post on forums. Try to post this on all the sites you possibly can because people who see this. The more money you will make.

5. Sit back and just watch your paypay account get filled with money. Dont spend it all at once!!!!!                     

Thank you

---

### Post by tdjokic on 2005-07-24
stuart, there are many simple rules about things you consider complicated, but you must find way to read this rules. There is whole technology to learn so very new thing as new OS. For example: [http://www.knoppix.net/wiki/Main_Page](http://www.knoppix.net/wiki/Main_Page)  .  

And for longtime user of MS Windows Linux is a new OS, and it is not easy to learn it, no way. I am not promoting Linux, I am everage user, nothing more than that.

- softver modems - often don't work under Linux, 1 (one) chip usually
- pseudo- or half-harware modems, 2 chips - on the box you will very often find word "hardware", only to make it different from softver winmodems, and this is very bad habit, I must agree
- hardware modems - internal, 3 chips, no need for any driver
- hardware modems - external, SERIAL(!), for Com port, work on any OS, w/o driver; there is one or two known eksternal, serial modems that DO NEED DRIVERS, and ARE NOT REAL hardware modems, but they aro so rare I doubt any of you will encounter any. Hint: ONLY 4 LED is WRONG, MUST BE 6 or more!

Unfortunately, more and more new mobo's dont have any Com port any more.

- USB external modems - very "winmodem"ish, usually very dificult or impossible to work with Linux, with some exeptions(?)

There are many Linux distribution. Ubuntu is only one of them. If you don't have fast Internet conection, you can use multi-CD distribution and everything is on your table. Look at [www.distrowatch.com](www.distrowatch.com) for more details.

You simply don't have enough informations, that's all. One very important information is: nobody force you to use Linux, this is your choice.

---

