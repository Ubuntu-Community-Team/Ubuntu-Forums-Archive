---
title: "wireless access point using old router ?"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by robert shearer on 2011-01-29
I have a D-link modem/router and an 8-port switch as the wired network connection for several computers.

Recently acquired an old laptop + pcmcia wireless card + Belkin wireless router.

I would like to add the Belkin router somehow to the current wired network via the switch and be able to connect the laptop wireless to the net via the Belkin.

Laptop=>Belkin wireless Router=>Switch=>D-Link Router/modem.

I am reasonably conversant with Linux/Ubuntu and Mr Google is my friend, but when it comes to networking I am all at sea and I have never used wireless before.

Is what I am wanting to do possible ??
and if so can anyone guide me with simple steps ?.

tia,
 Bob.

---

### Post by robert shearer on 2011-01-30
Bump ??

is it as simple as disabling dhcp in the wireless router and setting a static ip for it ??

anybody ??

---

### Post by oldsoundguy on 2011-01-30
Don't think you are being ignored.  Until the new servers are installed, things will move a tad slow here.  
As to using a wireless router for a net access point, not sure how that can be done.  But be assured, SOMEONE here has tried it.  You just will have to be patient for your reply.

I use an actual wireless access point that had to be hard wired to the router.

---

### Post by robert shearer on 2011-01-30
> **oldsoundguy said:**
> Don't think you are being ignored.
You replied..I'm not being ignored., Hooray! ):P.
Actually,  New Zealand being the first place to see the light of each new day has a down side.
 I find my forum posts often get buried several pages down before the rest of the world wake for the day and log-on.
So a bump at a different interval (36hr) sometimes works. 

>  Until the new servers are installed, things will move a tad slow here. 
Yeah, aware of that. (see above) 

> I use an actual wireless access point that had to be hard wired to the router.

I am hoping that all I have to do is disable the routing in the Belkin and can use it as an access point too.

Thanks for your reply and encouragement.
Cheers,
Bob.

**EDIT**..thanks for mentioning > access point. Sometimes its just having the right terms that make searching fruitful.
I think I am on my way to having it operational....[http://en-au-support.belkin.com/app/answers/detail/a_id/2826](http://en-au-support.belkin.com/app/answers/detail/a_id/2826)
Will try that after work and report.

---

### Post by FishRCynic on 2011-01-30
You are correct.
Disable Dhcp
Static IP
as an extra measure I removed all the firewall rules that had
been added. 
Thats all i did on the Linksys i have.

---

### Post by robert shearer on 2011-01-31
Ok, trying to set the static ip..seems straightforward in execution but can't get my head around finding out the ip to use.

Most of the searches I have done and the Belkin manual all refer to something formatted like 192.xxx.x.xx.

However, when I run  ```
ifconfig
``` from a box on the network it returns something in the format 10.x.x.1 with the final digit varying depending on which port of the switch I am connected to.

Presumably this is the address of the port of the switch so is it also the static address I should use ? (ie plug the belkin into one of the ports permanently and use its 10.x.x.x address ?)

If not how do I go about finding the correct address ?.

Apologies for the noobish questions though if you can point me in the right direction i think I can do the rest ok.

Cheers 
Bob.

---

### Post by robert shearer on 2011-02-01
> (ie plug the belkin into one of the ports permanently and use its 10.x.x.x address ?)


Well I tried that but could not even access the router afterwards and had to reset it to factory defaults.

Surely someone has a moment to answer this  simple (I would have thought) question.

Well, just plugged the computer direct to the working wired D-Link router and ran ifconfig and that reports a format 10.x.x.x too, so why doesn't it work for a static address on the Belkin when following their instructions to convert it to a WAP ?.

---

### Post by YesWeCan on 2011-02-01
> **robert shearer said:**
> I have a D-link modem/router and an 8-port switch as the wired network connection for several computers.

Recently acquired an old laptop + pcmcia wireless card + Belkin wireless router.

I would like to add the Belkin router somehow to the current wired network via the switch and be able to connect the laptop wireless to the net via the Belkin.

Laptop=>Belkin wireless Router=>Switch=>D-Link Router/modem.

I am reasonably conversant with Linux/Ubuntu and Mr Google is my friend, but when it comes to networking I am all at sea and I have never used wireless before.

Is what I am wanting to do possible ??
and if so can anyone guide me with simple steps ?.

tia,
 Bob.
Howdy down-under.
Well, I would just plug the wireless router in to your existing wired network. The "input" port of the router that you'd normally plug into a cable-modem. That's it you are done.
Now your wireless router should use dhcp to get an IP address assigned to it from your wired router. Then your laptop should use dhcp to get an IP address assigned to it from your wireless.
Normally, all this is automatic.

One slight problem is that you must make sure the wireless subnet is different from the wired or else the laptop won't go to the wireless router to find a wired IP address.
Another problem is that a PC on the wired subnet won't know about the wireless subnet or how to find it unless you tell it or tell the wired router about it.
It depends whether you need two-way-initiated connections or not.

I think it best to have the wireless router get it's IP from the wired router (dynamic rather than static) because this ensures the wired router knows it is there. Otherwise, with a static address you need to tell the wired router about it. In any case it is easier to tell the wired router to give it a fixed address each time it asks for one.

---

### Post by robert shearer on 2011-02-04
> **YesWeCan said:**
> Howdy down-under.
Well, I would just plug the wireless router in to your existing wired network. The "input" port of the router that you'd normally plug into a cable-modem. That's it you are done.

Thanks for that.   
 It works to setup the connection, finds a lease and reports connected but fails after a short time (couple of web pages) just locks up.

> Now your wireless router should use dhcp to get an IP address assigned to it from your wired router. Then your laptop should use dhcp to get an IP address assigned to it from your wireless.
Normally, all this is automatic.
 
seems to be.( apart from above.:confused:)

> One slight problem is that you must make sure the wireless subnet is different from the wired or else the laptop won't go to the wireless router to find a wired IP address.
is this the problem if it connects but then stops ?

> Another problem is that a PC on the wired subnet won't know about the wireless subnet or how to find it unless you tell it or tell the wired router about it.
It depends whether you need two-way-initiated connections or not.

No, do not need to connect to other machines on the local network, just a web connection would be fine, well one that works for more than a page or two !! :confused:

Thanks for the help so far.

---

