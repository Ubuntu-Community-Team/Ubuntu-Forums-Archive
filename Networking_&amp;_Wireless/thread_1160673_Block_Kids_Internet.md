---
title: "Block Kids Internet"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by actioncomics on 2009-05-15
I am wanting to block the internet from my kid's computers, but still allow them to access the local lan i have set up in the house.  Can anyone give me some ideas on how to do this in Ubuntu?

Ideally I would like to also allow them access to e-mail, so if you have an idea about how to do that please let me know.  but i will start with just in the internet.

To give you an idea of the lan we have set up.  Everything connects to a central router.  But i have shared drives I would like for the to access.  I will also eventually setup a mirror for Ubuntu repositories so we can update their computers without having to connect to the internet.

I just lost my job so I have plenty of time to play with this!:D

---

### Post by gfe on 2009-05-15
I would try going into the router configuration and see if it's possible there. Usually, you can do that from any browser on the network as long as you have the password.

---

### Post by ktrnka on 2009-05-16
You should use opendns for content filtering and you should search for firefox plug-ins that allow for parental control. You might want to look in your router's advanced settings. Many allow you to disable the internet during certain times of the day for specific days of the week using schedules.  If you want to run your own router, you can use [http://www.untangle.com/]("http://www.untangle.com/"). It's open-source packages are free. Let me know if you need more specifics. I'd go and find you more links but I'm rather tired and going to sleep. Good Luck!

---

### Post by ninjapirate89 on 2009-05-16
How tech savvy are your kids? Would it be as simple as uninstalling the web browser and just use thunderbird or evolution for mail?

---

### Post by actioncomics on 2009-05-16
Thanks for the information.  unfortunately my son is very tech savy.  I was using OpenDNS and he found a way around that (not all that hard).  And the router that i am using is really limited.  I search all over for settings that would restrict their access and could not find anything.  I will keep looking.
thanks
ac

---

### Post by ninjapirate89 on 2009-05-16
Do they have their own separate user account? If you set up their account and don't give them the root password then I would think that they will have a considerably harder time connecting to the internet without a web browser.

---

### Post by actioncomics on 2009-05-17
I had thought of that but my son installs and experiments with alot of programs.  I got tired of having to walk to his machine all the time just to type in a password.

Could this be done with 2 network cards?  I have several laying around.

Or is there an entry that could be made in the /etc/host file that could block everything?

---

### Post by ecosprog on 2009-05-17
I have just been through this process myself, and to be honest there isn´t a simple way to solve this issue. If you want a safe Internet system for your kids the best option is to go for a small firewall/router appliance with access restrictions and content filtering enabled.

In my opinion the best approach is to build your own using an old PC/notebook, or better still a dedicated embedded device like one of the ALIX boards ([http://www.pcengines.ch/alix.htm](http://www.pcengines.ch/alix.htm)). For the firewall software I would suggest IPCop or PFSense as both of these have good support communities and also provide the necessary packages for restricting access and content filtering. PFSense is the more comprehensive solution but slightly more of a challenge to install and configure, but once up and running provides an extremely good firewall and a very flexible means of restricting network/Internet access.

I have just upgraded my old notebook based IPCop firewall for a new ALIX2D3 running PFSense on a 4GB micro-drive. I use SquidGuard for my content filtering which itself uses Shalla blacklists ([http://www.shallalist.de](http://www.shallalist.de)) for selecting and restricting Internet access.

This isn´t a cheap solution but for about 150.00€ you get a lot of security and flexibility.

---

### Post by Crafty Kisses on 2009-05-17
Just to get this straight because I'm not understanding the full situation here. I'm assuming they have seperate computers, so why don't you just put like an encryption/password on your router so they can't connect without the password. That's one option, if you're going through wireless, you never mentioned if you were.

The other option would be a firewall of your choice and only allow certain IP addresses you want accessible. As mentioned above there's also SquidGuard, you should take a look at it. [http://www.squidguard.org/](http://www.squidguard.org/). 

Now if they are on the same computer, this should be fairly simple. As seen in numerous tutorials on the Internet, you can run the following:
```
sudo gedit /etc/network/interfaces
```
So if they are connected to the net via wlan, you can add this in the "wlan0" section:
```
pre-up iptables -A OUTPUT -p tcp -m owner --uid-owner username -j DROP
```
Now enter that command again, but now make sure where it says "uid-owner-username" make that the username you want to block the net for. So for example if your kids username is "kid" it would be the following:
```
pre-up iptables -A OUTPUT -p tcp -m owner --kid -j DROP
```
That should do it.

---

### Post by actioncomics on 2009-05-17
Thanks for the suggestions.  I will see what i can do.  Just in case anyone has any other suggestions here is an explaination of my setup.

The kids all have their own computers running Ubuntu.  We connect to the internet via a Uverse router (and it is not a very good one).  that I can see, it does not allow for me to restrict their connection.  All that I am really after at this time is to allow them to access our internal server.  They can surf the internet on a computer next to me so that i can monitor it, however it is getting to be a hassle to transfer files on their thumb drive constantly.  and it is not easy to update their systems.

Thanks again for the help.

---

### Post by ecosprog on 2009-05-17
Looking at your posts again it´s just occurred to me that there is a simpler and cheaper option than my previous suggestion if all you want at the moment is to restrict Internet access.

Using third-party firmware on a suitable router  such as DD-WRT ([http://www.dd-wrt.com](http://www.dd-wrt.com)) on a Linksys WRT54GL will do what you want, and more. These routers can be picked up on eBay for about 50.00€ new. Another firmware option for these routers is Tomato ([http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)) whic will do similar things to DD-WRT.

Unfortumately, this and similar routers don´t sufficient processing power or memory to handle content filtering. But if it´s only Internet access that you´re after, this will do the trick.

---

### Post by ecosprog on 2009-05-17
Just thought I´d include a screen-shot of Tomato showing the Internet blocking facility.

---

### Post by Crafty Kisses on 2009-05-17
The only issue  with Tomato is it only works with certain routers, mostly Linksys. I have Tomato running on my Linksys, works fairly decent.

---

### Post by ecosprog on 2009-05-17
My original suggestion was DD-WRT which supports a bigger range of routers. Also has similar access restiction functionality to Tomato.

I also think that as low end routers go it´s hard to beat the WRT54GL. Lots of them around and they are reasonably cheap. Teamed up with good third-party firmware (there are others on top of the 2 already mentioned) they are powerful little routers.

Gotta come clean and say I have a soft spot for these units as I´ve been using them for the last 5 years. I currently have 8 of these deployed providing a wifi network for myself and a few neighbours out here in the wilds of the Spanish campo.

---

### Post by actioncomics on 2009-05-18
Perfect.  Just one problem.  I gave my router away that had Tomato on it!!!!
I had forgotten that this setting was in there.  thanks for the help this is exactly what i was looking for.

ac

---

