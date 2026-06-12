---
title: "A (nother?) 9.10 wireless issue"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Jesper W. on 2009-12-23
Hello fine forum'ers -

I've been searching the forums for info on this - so far, however, it has not helped me very much, so here I go:

Being new to Linux, I just installed Ubuntu 9.10, which went off without a hitch as far as I can see - looks spiffy, too. I put it in my machine next to an XP (with the option for either appearing at start-up - not really savvy on what this is called), as this is a test on my work computer which, if all goes well, should lead to rolling out Ubuntu on 5-6 workstations. 
However, like other users I too am unable to connect to my wireless network, and the nature of the inability has me baffled...

First off, Ubuntu clearly listens for networks, and it picks up on mine as well - it is shown among the available ones when I click the network icon in the top bar - but I still can't get accepted onto the network.
I have read through the [https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html) - and then I hit a dead end, because my system came back with no ESSID. In older versions of Ubuntu this means you have to fiddle with WPA, I found out, so just to be safe I checked all I could (being not a very impressive geek at all) and it seems WPA is installed and working fine.

I then read through another thread which seemed to address mostly the chipset of the troubled user - but I really hope I am in the wrong when imagining that every install has to be manually checked for chipset compatibility...!?
'Cos that will definitely throw a monkey wrench in any plans to use this across several computers, all of which are different and used by people who are not me.

So, to summarize and form a question - I have fully working wireless capabilities in Ubuntu (= driver, WPA etc.) as near as I can tell, the access point is working (it's a 1TB Time Capsule, fyi, and I can reboot in XP and use it fine), but it won't accept my password.

So how do I go about fixing this? - is there a "how-to" concerning this particular 9.10 issue somewhere (as it seems to be somewhat persistant)?

Thank you in advance for any help - and I would like to take this opportunity to wish you all a merry christmas!!

Jesper W.

---

### Post by gordintoronto on 2009-12-23
A wireless router can be set up to not broadcast its ESSID, and it sounds like yours is set up that way.  (This adds a tiny little bit more security to the network, but nothing which will keep out an experienced hacker.)  However, you must know it in order to connect.  Surely the XP network properties includes this information?

You also need to know which type of security the router has, and the password.  Armed with this information, you can right-click on the network icon, and select "edit connections."

None of this is specific to 9.10, or even to Linux.  You still need the same information to connect from a new Windows computer.

However, you raise a good point about wireless hardware.  Once you know the ESSID, encryption type and password, you should boot each computer using a LiveCD, and try to connect to the wireless router.  If you have six computers with different hardware, odds are that at least one of them will be more difficult to connect with.

---

### Post by Jesper W. on 2009-12-24
Thank you for your answer - I don't recall having seen an ESSID anywhere during setup in XP, or indeed having had to enter it (or, for that matter, any other physical IDs), neither for setting up the Time Capsule nor for the wireless USB unit... I'll look into it though.
Actually, come to think of it, the Ubuntu network manager doesn't ask for ESSID either - it asks for SSID and/or for a MAC address, which I don't know. 
I tried entering the SSID of the USB dongle and of the Time Capsule - since I don't really know which one it wants, though the TC one seems logical - and neither worked.
It does however list the security option I need (which is WPA/WPA2 Personal), and I did enter the password... no luck so far.

Anywhoo, I'm off work for a few days (something called Christmas, I gather) - when I get back to it I'll try some more stuff and keep y'all posted on progress (if any), in the hope that it might help others. Feel free to chime in with any other tips if you have them!

Happy holidays everyone!

:)
JW

---

### Post by coffeecat on 2009-12-24
@Jesper W., in this context, SSID and ESSID can be thought of as the same thing. See:

[http://en.wikipedia.org/wiki/ESSID](http://en.wikipedia.org/wiki/ESSID)

The SSID is set in your router. It is nothing to do with your USB dongle. It is the name of your network, so....

> **Jesper W. said:**
> First off, Ubuntu clearly listens for networks, and it picks up on mine as well - it is shown among the available ones when I click the network icon in the top bar - but I still can't get accepted onto the network.

... whatever is being shown among the available networks, and which you're identifying as your network, is the SSID. And it's clearly not hidden. And, since network manager is showing networks, the wireless device in your computer must be working under Ubuntu and you can safely ignore 99% of those threads you've been looking at.

What do you mean by not being accepted on the network? When you click on your network, are you prompted for a passkey? The prompt will tell you what type of encryption passkey you are being asked for - WEP or WPA and which type of either - so all you have to do is to enter the passkey that you would have had to enter first time you connected wirelessly with Windows. And when you connected with your Mac, for that matter. I presume you use a Mac since you mention Time Capsule.

Question: when you first got your router, did you configure it yourself? Did you set up a WEP or WPA key? That's the one you need to connect with network manager. If, by chance, your ISP provided you with a wireless-router already configured with a passkey and you have lost this, you can log into the router web configuration interface with a wired ethernet connection and retrieve it. Or, if your ISP provided you with a ready-configured wireless router, turn it upside down and see if the WPA key is on a label underneath. :wink: No, seriously. I've seen that.

By the way, you don't need to bother about MAC addresses, unless you've set up MAC address filtering in the router. But it sounds as though you haven't if Windows can connect OK.

---

### Post by Jesper W. on 2009-12-26
Thanks Coffeecat, for that short & sweet pin-down - I kinda got the idea that SSID was a network identifier (I already read that Wikipedia entry) but it looks just like any other physical address, hence my confusion; I had pulled up quite a few numbers and strings in the terminal, and I'm not used to dealing with these inner workings very much.

- oh, and for ruling out the MAC address issue as well.

Looks like my answer to your question makes things no clearer; - I set up the wireless myself (using Airport Utility on the PC - and yes, I am usually a Mac user, nicely spotted ;) ) and assigned WPA/WPA2 Personal security, for which I am indeed prompted when I ask Ubuntu to log on to my network.
And I enter it, and I am still refused access - the system will keep trying for about a minute (the spinning icon in the top bar), re-prompt me, I'll re-enter, and over again, until after the fourth or fifth try it declares that we're offline.

It actually looks less and less like an Ubuntu issue, but it must be since I can reboot in XP and the wireless network is up fine every time...
I suppose I should get on the network with an ethernet cable and work up from there - as I said: I'll keep you posted! :)

'spect
Jesper W.

---

### Post by Jesper W. on 2010-01-21
Well, I'm back - and I tried hooking up to network by wire today.
It worked, yay for that.

But I still can't get any response via wireless, and now I also can't seem to find out how to access my remote drive (a Time Capsule, which is also my internet router, obviously), and every attempt to find a solution quickly degenerates into geek speek, even beyond my (sort-of everyday geek) capacity...
I think I'm going to have to postpone the introduction of Ubuntu laden computers to a team of particularly non-computer savvy women indefinitely - but thanks to you all for trying to help.

:)
Jesper W.

---

### Post by BOFslime on 2010-03-02
I was having this same issue, I could see my AP broadcasting its SSID no problem, but it would never connect. Looks like the linux driver, while able to see my AP, doesn't like it configured as N only (even though both card and AP are capable).  Once I switched my AP to allow G, I was able to connect.

---

