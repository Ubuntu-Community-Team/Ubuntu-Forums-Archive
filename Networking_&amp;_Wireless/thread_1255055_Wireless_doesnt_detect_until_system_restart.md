---
title: "Wireless doesnt detect until system restart"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by akber on 2009-09-01
For the most part my wireless works, although sometimes the network will be detected and TRY to connect, but it will never succeed. It always connects for awhile and then says that i have disconnected from my previous network, and then nothing happens. If i reboot the wireless works fine. 

Is there any way to work around this, rebooting everytime i disconnect or change locations is really cumbersome.

---

### Post by shredder12 on 2009-09-01
try switching off your wireless switch for a while and then turn it on again..
see if you can detect the wireless networks and connect.

---

### Post by akber on 2009-09-01
If this works, im gonna feel like a ******* fool.

---

### Post by shredder12 on 2009-09-01
Actually your problem seems to be more than jst turning the wireless switch on and off..
It could be some driver or wireless card compatability issue..
but if this method temporarily connects you then at least you won't have to reboot again and again..

---

### Post by akber on 2009-09-01
Yeah although the connectivity problem is solved by switching the wireless on/off, messenger programs like skype still require a system restart to connect properly.

---

### Post by akber on 2009-09-01
bump

---

### Post by shredder12 on 2009-09-02
> **akber said:**
> Yeah although the connectivity problem is solved by switching the wireless on/off,
So, does this mean that you can now see and connect to wireless networks??
If that's so then are you not able to connect to internet??

>  messenger programs like skype still require a system restart to connect properly.

Can you surf the web.??

---

### Post by akber on 2009-09-03
I can surf the web and detect wireless networks fine, but yes, skype requires a complete system restart more often when i am at school, perhaps because of the proxy settings, and the proxy settings i suspect are why pidgin messenger cannot connect at all when i am at school, gives me an error: no address associated with hostname. 

But sometimes on my home network with default proxy settings (i have to change the proxy settings if i want to connect to the school network) skype still requires a complete system restart. That is usuallly when i am just transferring from another network. 

And just as an add-on, is pidgin not connecting because of a proxy problem or is it something more? Other students i think can connect with msn messenger while at school.

---

### Post by shredder12 on 2009-09-03
No, proxy settings don't seems to be a reason for complete system startup..
have you tried restarting jst your networking service

```
sudo /etc/init.d/networking restart
```

and about pidgin.. I am not sure about the error..
but most of the establishments allow messenger services to bypass proxy server.

so you may try no proxy as an option..
or if this is what u have been trying then change it to use your proxy server..

---

### Post by akber on 2009-09-06
Sorry for not responding, hopefully this thread isnt lost in the depths of the forums by now. 

I tried the network restart, but skype still requires a complete *system *restart in order to connect properly. If i havent mentioned this before, this only occurs when using a school connection with unique proxy settings enabled. Pidgin also cannot connect (at all) when at school.

---

### Post by akber on 2009-09-06
Sorry for not responding, hopefully this thread isnt lost in the depths of the forums by now. 

I tried the network restart, but skype still requires a complete *system *restart in order to connect properly. If i havent mentioned this before, this only occurs when using a school connection with unique proxy settings enabled. Pidgin also cannot connect (at all) when at school.

---

### Post by shredder12 on 2009-09-07
> **akber said:**
> 
I tried the network restart, but skype still requires a complete *system *restart in order to connect properly. If i havent mentioned this before, this only occurs when using a school connection with unique proxy settings enabled.

So, it means you use the proxy setting in skype. I can't think of any other solution to your problem.. disabling networking and then starting it could help.. 

>  Pidgin also cannot connect (at all) when at school.

Well, it seems schools are not friendly for messengers. :(

---

### Post by jward3010 on 2009-09-07
> **shredder12 said:**
> Well, it seems schools are not friendly for messengers. :(

Absolutley true, they regard talking to friends in general as an evil to be contained. 

Anyway, this is a long standing problem I've had with wireless connectivity under Ubuntu especially when it comes to putting a laptop into stanby, going to some different location, bringing it out of standby and the wireless card not being able to search for any networks, as if the process of standby disables communication between the kernel and wireless card. You need to do a restart to refresh networks, whcih realistically is ridiculous. 

But it seems to be down to horrible ACPI problems which have always been a problem within Linux, which is another story.

---

### Post by pbjelly123 on 2009-09-07
Been curious about this Skype issue for sometime now.  Helpful.  Thanks guys

---

### Post by akber on 2009-09-08
Yeah I thought that the proxy would be the thing for pidgin, but all my friends who are using msn messenger have no problem connecting so i am pretty perplexed. 

And and i can go in and out of standby however many times i want and for as long as i want at home and skype and everything else will work fine-- EXCEPT FOR TRANSMISSION (bittorrent is another issue i will address later, i need this fixed first)

Also, when i apply proxy settings i click "Apply System Wide", does that have anything to do with it? I think i remember not doing it once, but i am pretty sure i had the same problem. 
Its not so much that i really want to chat and use skype at school, its just i hate it when i CANT figure out what the problem is. 

As for the bittorrent thing, i know it wont work in school because they have blocked all ports. BUT it still wont work at home! And my desktop has no problems with it although its on a LAN connections if that has anything to do with it. Do i need to forward ports? (If i do, please for the love of god tell me how, i have no idea). Do i need to change settings in the torrent client?

---

### Post by jward3010 on 2009-09-09
> **akber said:**
> And and i can go in and out of standby however many times i want and for as long as i want at home and skype and everything else will work fine-- EXCEPT FOR TRANSMISSION (bittorrent is another issue i will address later, i need this fixed first)
Depends what wireless device you're using. Some are fine, others spurious.

> **akber said:**
> As for the bittorrent thing, i know it wont work in school because they have blocked all ports. BUT it still wont work at home! And my desktop has no problems with it although its on a LAN connections if that has anything to do with it. Do i need to forward ports? (If i do, please for the love of god tell me how, i have no idea). Do i need to change settings in the torrent client?
YES you do need to forward ports, thats your problem. You need to go into your router configuration page and open them there. 

But first things first, you need two pieces of info from your PC - your IP address and the port that Transmission wants to use. 
1. IP adress: Type in a terminal ```
ifconfig
``` 

for your IP address

2. In Transmissions settings / preference page there's a section for port numbers, see what it has randomly set (you can change it of course), write the number down. This is also where you'll come to test the port.

After that its router configuration time...

Open Firefox and type 192.168.1.1 or 192.168.1.254 (or 192.168.0.1 or 192.168.0.254) into the address bar and you should get to your router config page. If there's any passwords to enter find them, enter them and maybe take a screenshot of the page. What router do you use at home.

---

### Post by akber on 2009-09-09
Ok i got the port number, (4322) and i got into the router page. 
The router i use at home is a ZyXEL  P-660R-D1

So how do i forward the port?

Edit: Ok since i just opened transmission (and i havent opened it since i found it wasnt working, like a week ago) and without doing any of that stuff it is now downloading fine. But the port is still closed. Even though its working i would still like to know how to open the port. Thanks.

---

