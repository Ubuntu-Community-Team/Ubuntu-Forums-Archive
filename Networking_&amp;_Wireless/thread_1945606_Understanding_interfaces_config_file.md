---
title: "Understanding interfaces config file"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by usafahpng on 2012-03-23
Hello Everybody:  I am new to Linux.... 
I have these stanzas (lines) in config file:  interfaces  

auto lo 
iface lo inet loopback  
auto wlan1 
iface wlan1 inet static   

I could not find any information on these:  
auto, lo, wlan1, iface, loopback  

Where can I get information about the above items? 

What command do can I use to get more information on the items above? 

I tried commands like man and whereis and got nothing.
 
Can you explain what the lines in the config file do in some detail?  

Thanks.

---

### Post by chili555 on 2012-03-23
You can find additional information in:```
man interfaces
```If Network Manager is running, as it is by default in all but server and a very few other Ubuntu installations, this file only need contain the lo or loopback lines. NM will take care of all these details for you quite well in most cases.

Your wlan1 lines are saying that you want wlan1 to start automatically on boot and to have a static IP address. The address you want it to have is not named, nor is the access point or router identified. No encryption password is mentioned. The system will not connect in these circumstances.

You have said, in effect, "I want you to go connect to ... "

Is wlan1 your wireless interface? wlan0??

What are you trying to accomplish?

---

### Post by usafahpng on 2012-03-23
Hello Chili555:
 
>  If Network Manager is running, as it is by default in all but server and a very few other Ubuntu installations, this file only need contain the lo or loopback lines.  
 
I looked for description on what is "lo", and you reply seems to indicate lo is actually loopback.
 
[COLOR=blue]What I am looking for, among other things ,is to how to find information on what auto, lo, loopback, wlan1, etc.... which would save a lot of asking in the future....[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]How do I do that using a Ubuntu machine?[/COLOR]
[COLOR=#0000ff][/COLOR] 
 
I did "man intefaces" but there was not much information there..
 
When I ran command  "man interfaces,"somewhere in there, it said this:
 
Examples of how to setup interfaces can be found in:
/usr/share/doc/ifupdown/examples/network-interfaces.gz
 
[COLOR=blue]Question:  How do I open this file and read the document?[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff]thanks.[/COLOR]

---

### Post by usafahpng on 2012-03-23
>   [COLOR=#0000ff]Question: How do I open this file and read the document?[/COLOR]
 
 
I was able to see the ntework-interfaces.gz file, but still do not know the following :
 
I have these stanzas (lines) in config file: interfaces 

auto lo 
iface lo inet loopback 
auto wlan1 
iface wlan1 inet static 

I could not find any information on these: 
auto, lo, wlan1, iface, loopback 

Where can I get information about the above items? 

What command do can I use to get more information on the items above? 

I tried commands like man and whereis and got no userfull description..

---

### Post by chili555 on 2012-03-23
The lo and loopback lines are used internally by your system. Do not disturb or change in any way those lines.

wlan1 should be the wireless interface you wish to control manually and not with Network Manager. Do you have a wireless interface? Is it wlan1? Find out with:```
iwconfig
```If you do not have a wlan1 and, most especially, if you do not wish to control and configure it manually outside of NM, I'd remove those wlan1 lines.

Where did the wlan1 lines come from? Did you add them?

[http://en.wikipedia.org/wiki/Loopback](http://en.wikipedia.org/wiki/Loopback)> On Unix-like systems, the loopback interface usually has the device name lo or lo0.

---

### Post by RyanRahl on 2012-03-23
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

and

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

should shed some light for you

---

### Post by redmk2 on 2012-03-23
> **usafahpng said:**
> Hello Chili555:
 

 
I looked for description on what is "lo", and you reply seems to indicate lo is actually loopback.
 
[COLOR=blue]What I am looking for, among other things ,is to how to find information on what auto, lo, loopback, wlan1, etc.... which would save a lot of asking in the future....[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]How do I do that using a Ubuntu machine?[/COLOR]
[COLOR=#0000ff][/COLOR] 
 
I did "man intefaces" but there was not much information there..
 
When I ran command  "man interfaces,"somewhere in there, it said this:
 
Examples of how to setup interfaces can be found in:
/usr/share/doc/ifupdown/examples/network-interfaces.gz
 
[COLOR=blue]Question:  How do I open this file and read the document?[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff]thanks.[/COLOR]
 The man pages (TFM) does explain it all.  You may not have understood what it reveals.  For instance on the matter of the term *auto, * the man page says```
The file consists of  zero  or  more  "iface",  "mapping",  "**[COLOR="Red"]auto[/COLOR]**"  and
       "allow-" stanzas. 
    Here is an example.
       **[COLOR="Red"]auto[/COLOR]** lo eth0 **[COLOR="Blue"]<-- this brings the interface(s) up automatically[/COLOR]**
       allow-hotplug eth1

Lines  beginning with the word "**[COLOR="Red"]auto[/COLOR]**" are used to identify the physical
       interfaces to be brought up when ifup is run with the -a option.  (This
       option  is  used by the system boot scripts.)  Physical interface names
       should follow the word "**[COLOR="Red"]auto[/COLOR]**" on the same line.  There can be  multiple
       "auto"  stanzas.  

```

What that means is the term *auto * is used to configure a specific interface to be automatically bring up the interface via a boot time script.  The *physical interface * is referring to *eth* or *wlan* or *pan* or any other label that defines the specific NIC.

---

### Post by hpng on 2012-03-25
example for config file     /etc/network/interfaces
Brings up interface &#8220;lo&#8221; by ifup 
[COLOR=Red]
auto lo[/COLOR]

#next define logical interfaces using iface
[COLOR=Red]
iface lo inet loopback[/COLOR]


OK, here is how I understand the above:
"auto" above allows ifup to start interface "lo".
As i understand it, "lo" is loopback.
Then, I see logical interfaces defined using iface for lo and loopback in next  like so:
[SIZE=3][SIZE=4][COLOR=Red]
iface lo inet loopback[/COLOR][/SIZE][/SIZE]

So why are there two SAME loopback logical interfaces, "lo" and "loopback" in above line?


I am perplexed!

---

### Post by redmk2 on 2012-03-25
> **hpng said:**
> 
OK, here is how I under stand the above:
"auto" above allows ifup to start interface "lo".
As i understand it, "lo" is loopback.
Then, I see logical interfaces defined using iface for lo and loopback in next  like so:
[COLOR=DarkOrange]**iface lo inet loopback **[/COLOR]

So why are there two SAME loopback logical interfaces, "lo" and "loopback"?
I am perplexed!

No need for oversize fonts here.  Read the COC on that matter please.
Edit: Thanks for removing most of the oversized fonts.  :-)

I think your over thinking the matter.  The term auto can me used with ***any** * iterface label.  If we state ***auto eth0*** then we bring up the real interface eth0.  If we state ***auto lo*** then we bring up the virtual interface lo (the loopback interface).  If you want to do both in one line you can do this:  ***auto eth0 lo***

The next line typically is (as you said): ***iface lo inet loopback***.  This says the the *[COLOR="Blue"]interface named lo[/COLOR]* is to [COLOR="DarkGreen"]use the internet settings (address) of *loopback network*[/COLOR].  That infers the IP address of 127.0.0.1 (from the network 127.0.0.0 /8  ).

The RFC 1700 defines the loopback addressing.  Read [**[COLOR="Blue"]here[/COLOR]**]("http://en.wikipedia.org/wiki/Localhost") for more info.

---

### Post by hpng on 2012-03-25
From [COLOR=#6666CC]/usr/share/doc/ifupdown/examples/network-interface

I saw these lines:

[/COLOR]auto eth0 eth0:1

The above lines means eth0 and eth0:1 will be "started" when computer starts up
What is the difference between eth0 and eth0:1"
Does eth0:1 and eth0 means you can have two interface ( as in virtual interface ) to 
same ethernet hardware card? 

is eth0:1 same as eth0.1?

Is there a good intro (book or otherwise) to networking configuration setup for newbies?


[COLOR=#6666CC]

[/COLOR]

---

### Post by redmk2 on 2012-03-25
> **hpng said:**
> From [COLOR=#6666CC]/usr/share/doc/ifupdown/examples/network-interface

I saw these lines:

[/COLOR]auto eth0 eth0:1

The above lines means eth0 and eth0:1 will be "started" when computer starts up
What is the difference between eth0 and eth0:1"
Does eth0:1 and eth0 means you can have two interface ( as in virtual interface ) to 
same ethernet hardware card? 

is eth0:1 same as eth0.1?
I think you mean *"Is eth0:0 same as eth0.1?" * First we need to understand the computing terms we are using.  See below```

[COLOR="DarkGreen"]Physical[/COLOR] = object in our world
[COLOR="Magenta"]Real[/COLOR] = a state with both physical and software aspects
[COLOR="RoyalBlue"]Virtual[/COLOR] = a state with only software (and firmware) aspects
[COLOR="Sienna"]Alias[/COLOR] = a second reference to an object or state

```
To answer both of your questions:  The terms *eth0:0* and *eth0:1 *are labels for 1 [COLOR="DarkGreen"]physical device[/COLOR].   The label eth0:1 is an [COLOR="Sienna"]alias[/COLOR] of eth0:0.  It allows you to apply 2 IP addresses to 1 physical device.  Do not think of them as 2 interfaces.  The distinction is subtle but important down the road.
> 
Is there a good intro (book or otherwise) to networking configuration setup for newbies?
[COLOR=#6666CC]

[/COLOR]
Maybe something like [**_[COLOR="Blue"]this[/COLOR]_**]("http://www.inetdaemon.com/tutorials/internet/ip/whatis_ip_network.shtml").  

Networking is a multiple layered concept.  You could spend days reading about the [**_[COLOR="Blue"]physical layer[/COLOR]_**]("http://en.wikipedia.org/wiki/Physical_layer") (PHY) or the [**_[COLOR="Blue"]data-link layer[/COLOR]_**]("http://en.wikipedia.org/wiki/Data_link_layer") (DLL).

The [**_[COLOR="Blue"]networking layer[/COLOR]_**]("http://en.wikipedia.org/wiki/Network_layer") is what most folks think of when they say networking,  but it really is only the *addressing *of the devices on the network.

This is a little long winded, but it gives you an idea of the scope of things.  Of course you can always just ask here in these forums on specific questions.

---

### Post by Ms. Daisy on 2012-03-25
Another good link I really liked was this

[http://www.trainsignal.com/blog/free-computer-training-videos/free-networking-training-videos/page/2](http://www.trainsignal.com/blog/free-computer-training-videos/free-networking-training-videos/page/2)

Aimed at the beginner, very simple to follow.

---

### Post by kevdog on 2012-03-25
Just checking in -- is there a specific reason you need to edit the interfaces file by hand?  I can think of many however usually these are associated with running a lot of servers of virtual machines.  It doesn't sound like you are doing these things but I could be wrong.

---

### Post by Ms. Daisy on 2012-03-25
The way I read the OP is he wants to find information about auto, lo, wlan1, iface, loopback because he didn't know what they were.

Kevdog makes a good point though, don't edit the interfaces unless you know what you're doing.

---

### Post by redmk2 on 2012-03-25
> **kevdog said:**
> Just checking in -- is there a specific reason you need to edit the interfaces file by hand?  I can think of many however usually these are associated with running a lot of servers of virtual machines.  It doesn't sound like you are doing these things but I could be wrong.
Why not?  You can't permanently harm anything?  If someone asks how something works, I take that as a positive step.  The worst that can happen by messing with the configuration is a complete reinstall.

More cogent advice might be; make a copy of the file before you start messing with the configuration so you have a way back to a functioning system.

If I listened to those *in the know *who told me *don't do that*, I would not have the complete understanding of how the system works.  Experience in recovering from mistakes is just as important as technically learning how the system functions.  Besides, it creates great war stories.  :-)

---

### Post by Ms. Daisy on 2012-03-25
As long as you're aware that you can create problems by messing with the configuration, then yes- go ahead and mess with it.  The way I learn to do stuff is to break it then fix it as well. But I do like to be aware first that I can really screw stuff up if I mess with x, y, or z.  

The OP didn't understand basic networking concepts and has 3 beans which leads me to believe that he may not be aware of the potential for damage.

---

### Post by kevdog on 2012-03-25
I wrote an entire tutorial about configuring interfaces from the command line -- that's a testimony to how I believe things can be done completely differently than the "norm".

As Ms. Daisy stated however, asking questions such as what is the loopback interface, makes me believe we should establish some basics prior to moving onto more advanced topics.  How has the system been configured that the OP is now getting a eth0:1 interface -- this is entirely possible however this question isn't usually asked -- which makes me believe someone has done something to the system and is now trying to recover from some catastrophe without spilling the beans.  I'm just asking for a little transparency.  The more I know what went bonkers in the system, the more I could probably help.

---

### Post by redmk2 on 2012-03-25
> **kevdog said:**
> I wrote an entire tutorial about configuring interfaces from the command line -- that's a testimony to how I believe things can be done completely differently than the "norm".

As Ms. Daisy stated however, asking questions such as what is the loopback interface, makes me believe we should establish some basics prior to moving onto more advanced topics.  How has the system been configured that the OP is now getting a eth0:1 interface -- this is entirely possible however this question isn't usually asked -- which makes me believe someone has done something to the system and is now trying to recover from some catastrophe without spilling the beans.  I'm just asking for a little transparency.  The more I know what went bonkers in the system, the more I could probably help.

No one is doubting your technical prowess.  My response to the OP was to point out the the man pages did include a description of the terms (s)he was interested in. 
  
The response that you are questioning was not to the OP, but rather a secondary question by another user.  Regardless of the situation, I don't judge something (or someone) without the facts, and the facts are, nobody asked how to edit the interfaces file.  

What both users did ask,  and I answered without making assumptions, was what was the meaning of the various terms.

---

### Post by Ms. Daisy on 2012-03-26
and IMHO, redmk2, you did a nice job explaining it all. 

The post that prompted kevdog's comment:
[QUOTE=hpng]From [COLOR=#6666CC]/usr/share/doc/ifupdown/examples/network-interface

I saw these lines:

[/COLOR]auto eth0 eth0:1[/QUOTE] That file is in the examples folder and therefore not an actual configuration, correct?

---

### Post by redmk2 on 2012-03-26
> **Ms. Daisy said:**
> and IMHO, redmk2, you did a nice job explaining it all. 

The post that prompted kevdog's comment:
 That file is in the examples folder and therefore not an actual configuration, correct?
I think this is about as far as I want to go with this.  @kevdog has been on these forums for quite a long time and has contributed tremendously.  My thoughts were more to the point that we should not judge what others capabilities or interests are.

The /etc/network/interfaces file is the traditional way to provide configuration parameters for *ifup *and *ifdown*.  As to the file that you mentioned.  It's more like a textbook on the interfaces file.  As a matter of fact in comes compressed as a .gz file and is included with other documentation.

---

### Post by Ms. Daisy on 2012-03-26
> **redmk2 said:**
> My thoughts were more to the point that we should not judge what others capabilities or interests are.
Fair enough. Agree to disagree.

---

