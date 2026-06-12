---
title: "Really confused about wireless on Dell Mini 9 running 10.04"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by elzee on 2010-06-02
Greetings all,

So I have a dell mini 9 running 10.04 and everything works great EXCEPT wireless.  I had the previous version of Ubuntu running wireless on this thing just fine except I cant remember for the life of me how I got it working.  I have a bcm4312

This has been a major headache ever since I upgraded (read clean install) to 10.04.  Just for giggles, I installed PclinuxOs and wireless worked just great.  I really don't understand why the most popular distro out there is having this problem.

So anyway, I have searched high and low all over the internet trying to find a solution and finally just figured i would ask here.  I have read all sorts of "fixes" for this problem but don't really understand alot of them. Like the difference beteween the b43 and the sta drivers i found under hardware and which one of these should be activated etc.  Also, i have read about solutions involving ndiswrapper and another thing that can be installed using the CLI but I can't figure out what exactly these things actually DO.

So, I have also read about "blacklisting" some of the drivers and this just confuses me even more, especially since half of the "solutions" out there involve installing them etc.  One other thing-after the clean install nothing shows up under the drop down menu for the internet connections.  However, when I go to enable the b43 driver and then restart, it will show the wireless connections but won't actually connect to any of them.

Anyway, I was just hoping we could get some kind of consensus here about  exactly what steps can be taken to remedy this problem.  Preferably steps that a noob like me can understand and make sense of.  I really don't want to move to a different distro as I really like ubuntu netbook other than this problem.

---

### Post by wojox on 2010-06-02
What are your choices in Hardware Settings?

---

### Post by elzee on 2010-06-02
> **wojox said:**
> What are your choices in Hardware Settings?

I assume you mean Hardware Drivers?  Its a choice beteween Broadcom B43 wireless driver and Broadcom STA wireless driver.  I have the B43 one enabled.  

Crap!  I just updated everything and rebooted and now no wireless connection choices are showing up.  AAAaargh!

---

### Post by elzee on 2010-06-02
Oh, btw the other thing besides ndiswrapper that I have read about and told to install is something called fwcutter...I have no idea what either of these things are actually for...:confused:

---

### Post by wojox on 2010-06-02
For my Dell BCM4312 I use Broadcom STA wireless driver. After activating unplug you Ethernet cable and reboot and configure from your nm-applet.

---

### Post by elzee on 2010-06-02
> **wojox said:**
> For my Dell BCM4312 I use Broadcom STA wireless driver. After activating unplug you Ethernet cable and reboot and configure from your nm-applet.

Ok i will try that but first, what is an nm-applet and how does one configure it?
And could you tell me can I do this from synaptic or just do it from Hardware Drivers?  I ask because in synaptic, I see some other things having to do with STA like-
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source

---

### Post by wojox on 2010-06-02
> **elzee said:**
> Ok i will try that but first, what is an nm-applet and how does one configure it?

It's the Network Manager Applet in your upper panel. :)

---

### Post by elzee on 2010-06-02
> **wojox said:**
> It's the Network Manager Applet in your upper panel. :)

Ok, I've got the STA installed and activated.  I rebooted and everything.  Network manager is still showing nothing.  Wireless networks is greyed out and says disconnected underneath it...

---

### Post by gonjaman on 2010-06-02
Hi Elezee,

I'm in the same boat trying to get a Tenda wireless device to work. Like you, it worked in 9.4, somehow - now in 10.4 I can't get it to work.
Its close - the wireless keeps disconnecting and reconnecting and asking for my router password, but won't actually allow me to get the internet.
Anyone out there who can help?

---

### Post by elzee on 2010-06-02
Can someone please help?  I've tried everything it seems like and no luck:confused:

So, ive just downloaded ndiswrapper in synaptic but i simply dont know how to use it...

---

### Post by wojox on 2010-06-02
> **elzee said:**
> Can someone please help?  I've tried everything it seems like and no luck:confused:

So, ive just downloaded ndiswrapper in synaptic but i simply dont know how to use it...

Never used ndiswrapper, but I did have luck installing on earlier versions with this:

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by elzee on 2010-06-04
> **wojox said:**
> Never used ndiswrapper, but I did have luck installing on earlier versions with this:

```
sudo apt-get install bcmwl-kernel-source
```


Yup, thats it right there!  The difference for me anyway was doing a completely clean install and then immediately going to the cli and putting that in.  And then rebooting...

The only thing I can possibly think of that made a difference was the clean install, and not having tried a bunch of other things first, like installing the b43 driver under the hardware menu.  

Anyway, I am happily posting this using my wireless setup.
More detailed instructions are on the link...
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Thank you for your help wojox!:P

---

