---
title: "some work, some don't"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Doughsay on 2006-06-19
I am using Dapper on my toshiba m200 tablet pc, built in wireless is ipw2100.  Worked fine out of the box, except that I can only connect to some wireless networks.  So far it's pretty much 50/50.  The networks i'm trying to connect to are all WEP, and most of them are encrypted.  I just don't know how to troubleshoot this properly.

I'm using Network Manager, not the bult-in network applet.  But regardless, I still get the same problems using the standard way as well.  What can I do to properly diagnose my problems?

Basically what happens is I select the network to connect to, it asks for a WEP key, I enter it, and then it sits there trying to connect but never does.  Obviously I've checked the keys over and over again and they are correct.  Can anyone help me?  I'm sorry I can't provide any more info.

---

### Post by x64Jimbo on 2006-06-19
Could be the difference between a "shared" or "open" key system. There's a special option that's needed to connect to shared key systems. I'm pretty sure that the network manager program doesn't account for this option/iwconfi when it's manipulating iwconfig in the background. Credit for this solution goes to misterhung in another thread:
> 
I thought I may be able to add something that will help.

When one is using a shared key, simply enter the key under "WEP key" in the wireless interface config window (in Ubuntu's Networking configuration app) PREFIXED by the word "restricted" (that's "restricted" followed by a space, then the shared WEP key). You'll not be able to see what you are typing, so you'll have to trust your fingers. :)

[http://warmachine.3cx.org/misc/wireless-config.jpg](http://warmachine.3cx.org/misc/wireless-config.jpg) 

See the iwconfig man page for more.


---

### Post by Doughsay on 2006-06-19
Thans for the quick response.

As the quoted post implies, the built-in Ubuntu network applet doesn't give you the option to choose between "shared" and "open" keys.  The "Network Manager" applet which I am using DOES let me specify.  Regardless, I tried what that post said about prefixing "restricted" in front of the key in the built-in network applet, and it still didn't work for me.

---

### Post by Doughsay on 2006-06-19
I was a little unclear on the kinds of networks I'm trying to connect to.  Some are WEP and some are not.  Some work and some not.  But it's not related to wether or not it's encrypted, because it seems some ununcrypted ones don't work either...  But that could be for other reasons I guess.  All the unencrypted ones that I WANT to connect to, work.

---

### Post by vivedekananda on 2006-09-03
I don't know it this helps, but I had problems connecting to my
wireless network with WEP encription in linux, while everything worked fine when I was in windows.

I figured out that i had to use "iwconfig wlan0 key open XXX"
(where XXX is the wep key) and after I could connect to the network.
Seems that by default "iwconfig wlan0 key XXX" equals to "iwconfig wlan0 key restricted XXX" which didn't work with my router.

good luck

---

