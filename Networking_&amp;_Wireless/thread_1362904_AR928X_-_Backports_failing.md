---
title: "AR928X - Backports failing?"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Zilliano on 2009-12-23
I have an Asus G50V laptop, which comes with an Atheros AR928X wireless card, which a has been as host of problems to get a connection with.
However, I stumbled up the solution of installing the Karmic backports (generic and wireless, to be specific).
It completely fixes my wireless, but now there is a new problem.
Every time I reboot, I have to reinstall the backports, or else on the next boot my wireless tries to connect to my router, which has the same signal strength as when I DO reinstall the backports, but it fails every time- it just keeps trying until it times out.
However, when I actually install the backports before shutting down, on the next boot up, the connection is near instant.

There are no changes in location or in the router going on... Just the difference of reinstalling the backports or not.
Is there a fix for this, or am I stuck having to do that forever?

---

### Post by Zilliano on 2009-12-23
...Oooookay, apparently it connects if try to connect twice or so, then let it sit without trying to connect for about 5 minutes, then try to connect again.

---

### Post by zozza on 2009-12-23
I also have the same adapter and the same kind of problems including very slow wireless with the connection not loading on start-up.  

What did you download for the backports?  I have updated my sources.list file with deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main universe multiverse restricted

and then apt-get upgrade and apt-get update.

However, I cannot see a specific file for wireless here [http://packages.ubuntu.com/karmic-backports/](http://packages.ubuntu.com/karmic-backports/)

Please tell me the command you used to get updated generic and wireless karmic backports.

Thanks.

---

### Post by zozza on 2009-12-23
OK it's this I assume: linux-backports-modules-wireless-karmic-generic

I have not noticed any change in speed though.

What changes did you see?

---

### Post by Zilliano on 2009-12-23
Oh, I just used my synaptic package manager.
Look for linux-backports-modules-wireless-karmic-generic.
Also install linux-backports-modules-karmic and linux-backports-modules-karmic-generic.

Hope that helps. :D

---

### Post by Zilliano on 2009-12-23
> **zozza said:**
> OK it's this I assume: linux-backports-modules-wireless-karmic-generic

I have not noticed any change in speed though.

What changes did you see?

Ah, well, I dunno about speed, but it went from one bar and not being able to get any internet connection at all to 3 bars (sames as my Windows 7 installation, where it works perfectly) and fairly fast internet speed, though I believe it's a bit slower than the Windows installation- probably because Wireless N isn't supported for Ubuntu, at least in my case.

---

### Post by Zilliano on 2009-12-23
I still have to reinstall the Backports.... Seriously, does anyone know what's going on?

---

### Post by Zilliano on 2009-12-24
So... No help, I take it?

---

### Post by Zilliano on 2009-12-24
I swear to God this kind of crap is going to make me go back to using strictly windows... at least when Windows breaks, I can fix it.

---

### Post by jeannacav on 2009-12-24
I am having something like this trouble too.
I am describing it like this and nobody seems able to help either!
I am really glad my wired works, but wait ...

I did the backports stuff and synaptic worked and my router connects perfectly....
Until a neighbor comes or goes.
This means sometimes I am undisturbed for 20 minutes and sometimes for 3 hours.
Since I bought this laptop I have had both on so I could watch and see what was going on.

But I got tired of being reminded that it was failing, and I now turn it off when my system reboots.
So, I should not even hear about the need to reconnect - right?
WRONG.

Now, I am having the wireless inform me that my neighbors systems need a password. I just got 2 of those today.
It seems to never stop searching for a connection even when I am off wireless.
I have repeatedly turned off or deleted them, to no avail.

What gives with this?

I am replying here because I think these are all related.
My and perhaps your wireless is being effected by other routers near me.
I have an acer 5517 with the same AR9285 as I believe yours.
(I am using jaunty since the saqme problems seem to be happening with karmic and I am doing other things.)

I wish this could be fixed.

thank you,
jeanna

---

### Post by coffeecat on 2009-12-24
I am posting from a laptop with the Atheros AR928X wireless chipset. Like everyone else, the connection was flaky at first, but since I installed the packages linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic, my wireless has been rock-solid.

@Zilliano, I can't explain the strange behaviour you are seeing. All I can say is that those two packages (you probably only need to install one) bring in the dependency linux-backports-modules-2.6.31-xx-generic where 2.6.31-xx matches your presently installed kernel. It's the linux-backports-modules-2.6.31-xx-generic package that actually contains the backported drivers. So far I have been through the 2.6.31-14, -15 and -16 kernels. Each time the backports package was updated to match and each time wireless has been fine.

Make sure you have either/or/both the linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic packages marked in Synaptic. That will ensure that the numbered package which actually contains the drivers will be installed to match the kernel. I really cannot understand why you need to re-install them. Once installed they stay installed. The modules are simply stored in the appropriate subfolder in /lib/modules from where they are automatically loaded into memory as and when needed.

Which kernel are you running?

---

### Post by Zilliano on 2009-12-24
I'm not sure it's just interference for me... I mean, I have other routers around me, but my wireless just..... well, in the exact same spot, it sometimes connects, and sometimes doesn't.

If I have to set up my router differently, I will, but I have no idea how to get it to freaking stop.

It might not be the backports, though..... I didn't install them this time, and it worked.

So, I dunno.

When it's not working, though, a fix that always works is to boot into kernel 2.6.31.14 (or whatever it is... Since I updated after the initial installation, it seems to have both 2.6.31.14 and 2.6.31.16) and install the backports there, then restart and boot into 2.6.31.16. Then it works. I'd really love to know what's going on here. >.<

---

### Post by coffeecat on 2009-12-24
> **Zilliano said:**
> I'm not sure it's just interference for me... I mean, I have other routers around me, but my wireless just..... well, in the exact same spot, it sometimes connects, and sometimes doesn't.

If I have to set up my router differently, I will, but I have no idea how to get it to freaking stop.

I wonder if this is the problem - interference on the same frequency. It only takes a few times for the interference to go away at the same time as you do the reinstall and reboot for you to think that it was the reinstall that did the trick. Coincidence is a tricky thing! :)

A few months ago I was getting some irritating wireless problems. By using some sort of sniffer app (can't remember which or which OS) I found that there were at least two or three wireless networks around me that were broadcasting on channels 1, 6 and 11. That's 2 or 3 each. I was using channel 6 at the time. So I changed mine to channel 8 and since then I've been OK.

And don't forget that baby alarms, cordless phones and passing camels breaking wind also use the 2.4GHz band. All of those, and old microwave ovens, are a source of interference. See:

[http://en.wikipedia.org/wiki/Electromagnetic_interference_at_2.4_GHz](http://en.wikipedia.org/wiki/Electromagnetic_interference_at_2.4_GHz)

Can you change the channel in your router?

---

### Post by Zilliano on 2009-12-24
Yes, I can. Let me see if that helps any.

---

### Post by Zilliano on 2009-12-24
Hmm, no change/help after setting the channel to something no one else around here uses... but I downloaded wifi radar, and a new stitch in the plot showed up. Apparently, where the wireless gets stuck is at 'Acquiring IP Address', so... I dunno if that's relevant, but I remember trying the WICD manager and it getting stuck on acquiring IP address, too, so I figure that's my issue.

---

### Post by coffeecat on 2009-12-24
> **Zilliano said:**
> Hmm, no change/help after setting the channel to something no one else around here uses... but I downloaded wifi radar, and a new stitch in the plot showed up. Apparently, where the wireless gets stuck is at 'Acquiring IP Address', so... I dunno if that's relevant, but I remember trying the WICD manager and it getting stuck on acquiring IP address, too, so I figure that's my issue.

How about setting your machine up with a manually configured IP address? I really don't know if that will help though.

---

### Post by Zilliano on 2009-12-24
Tried that, still to no avail. >.<

---

### Post by Zilliano on 2009-12-24
I'm losing my mind over this. Sometimes it connects, other times it doesnt. @.@

---

### Post by SeatherMar on 2009-12-24
Same issue here with the AR928X. I'm on a Dell Studio XPS 13. Tried the backports with no luck. I even tried the wireless-compat drivers. I get connections but get intermittent disconnects. I also tried wicd. No luck.

This is obviously a common issue as one can search for wireless issues in karmic and find something having to do with Atheros cards.

---

### Post by jeannacav on 2009-12-24
> **coffeecat said:**
> I am posting from a laptop with the Atheros AR928X wireless chipset. Like everyone else, the connection was flaky at first, but since I installed the packages linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic, my wireless has been rock-solid.


Make sure you have either/or/both the linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic packages marked in Synaptic. That will ensure that the numbered package which actually contains the drivers will be installed to match the kernel.....
Which kernel are you running?

I am using jaunty.
Does it make all the difference? I didn't think so with all the trouble I saw on posts, it seemed about equal.

Actually, I am wondering why I cannot turn it off?
It is marked as off, yet today it told me I needed to provide my pwd for the neighbor's networks??
thank you,

jeanna

---

### Post by coffeecat on 2009-12-25
> **jeannacav said:**
> I am using jaunty.
Does it make all the difference? I didn't think so with all the trouble I saw on posts, it seemed about equal.

Actually, I am wondering why I cannot turn it off?
It is marked as off, yet today it told me I needed to provide my pwd for the neighbor's networks??
thank you,

jeanna

Several points here, and I've re-read your previous post.

Yes, using Jaunty might make a difference in that the version of the ath9k driver might be a different one. Jaunty has an earlier kernel, and the drivers are to be found in the kernel modules. Also, you are using the AR9285 chipset which is not the same as the AR928X - or so I understand. You might want to search the forum specifically for threads about the AR9285 chipset in Jaunty, rather than in Karmic.

If you want to turn wireless in network manager off, right-click on the NM applet icon and untick the 'enable wireless' box. Whenever you want to switch it back on again, simply right-click and re-tick the box.

If you're being pestered for the passkey for a neighbour's network, it sounds as though you accidentally clicked on that network once and now NM "remembers" it and wants the password. I've done that myself. This is how to stop the prompts. Right-click on the NM applet icon and choose 'Edit Connections'. In the little window that opens, select the Wireless tab and highlight the network name that has been bothering you. Then click on the delete button, and you won't be bothered again.

In your earlier post you said:

> I did the backports stuff and synaptic worked and my router connects perfectly....
Until a neighbor comes or goes.
This means sometimes I am undisturbed for 20 minutes and sometimes for 3 hours.With the neighbour coming and going, do you mean the network being switched on and off? Because, if so, this sounds like an interference problem. Perhaps your neighbour's network is using the same channel as your router. Have a look in one of my earlier posts about channels and interference. Here in the UK we can use channels 1-13, but I believe in the US you are restricted to 1-11. Anyway, try changing the channel in your router. If it's on 1, try 11 or 6, or anything in between until you get a stable connection. Unfortunately, the frequencies overlap but with a bit of trial and error you should be able to avoid interference.

If you need help with changing channels in your router, post back with details of make and model.

---

### Post by jeannacav on 2009-12-25
> **coffeecat said:**
> Several points here, and I've re-read your previous post.

Yes, using Jaunty might make a difference in that the version of the ath9k driver might be a different one. Jaunty has an earlier kernel, and the drivers are to be found in the kernel modules. Also, you are using the AR9285 chipset which is not the same as the AR928X - or so I understand. You might want to search the forum specifically for threads about the AR9285 chipset in Jaunty, rather than in Karmic.



If you're being pestered for the passkey for a neighbour's network,..... Right-click on the NM applet icon and choose 'Edit Connections'. In the little window that opens, select the Wireless tab and highlight the network name that has been bothering you. Then click on the delete button, and you won't be bothered again.

In your earlier post you said:

With the neighbour coming and going, do you mean the network being switched on and off? Because, if so, this sounds like an interference problem. Perhaps your neighbour's network is using the same channel as your router. Have a look in one of my earlier posts about channels and interference. Here in the UK we can use channels 1-13, but I believe in the US you are restricted to 1-11. Anyway, try changing the channel in your router. If it's on 1, try 11 or 6, or anything in between until you get a stable connection. Unfortunately, the frequencies overlap but with a bit of trial and error you should be able to avoid interference.

If you need help with changing channels in your router, post back with details of make and model.

Thanks coffeecat,
[I thought AR928X meant AR928something. I did not realize X was a specific number.]

In the end Synaptic did the install so it should know what is here and what is not...correct?


If I do change the router channel will it change it for all my computers? Or is this a single interface with this computer?
I guess my question is will another computer be able to find the new channel as easily?
I obviously do not get this.

I do not understand how to change the channel, so I would like some help. It would be really nice to have this working properly.

Thank you for your help,

jeanna

---

### Post by coffeecat on 2009-12-26
> **jeannacav said:**
> If I do change the router channel will it change it for all my computers? Or is this a single interface with this computer?
I guess my question is will another computer be able to find the new channel as easily?

The "channels" are merely slightly different frequencies around the 2.4GHz range. See [here]("http://en.wikipedia.org/wiki/IEEE_802.11#Channels_and_international_compatibility") to see the overlaps I mentioned. It's only the wireless router you need to worry about - that is what determines the particular channel your network is using. The wireless networking driver on any OS should be able to detect this automatically. When I changed my router channel from 6 to 8, my Ubuntu, Windows and MacOS machines all connected quite happily without me having to do anything.

> **jeannacav said:**
> I do not understand how to change the channel, so I would like some help. It would be really nice to have this working properly.

You need to log into the web configuration interface of your router to be able to change the wireless channel. Have a look in your router manual to get the specifics. But in general terms, connect to the router with an ethernet cable - always do this if you are going to change wireless settings. Open Firefox (or any web browser), and type the IP address of your router in the address bar. This is usually 192.168.1.1 or 192.168.0.1 or 10.0.0.1 depending on the make of your router. Your manual should tell you the actual address for your device, or you could right-click on network manager and click on 'Connection Information'. The address is the one listed as 'Default Route'.

Once you've entered the router IP address and pressed enter, you'll be prompted for the admin username and password. If you haven't set these yourself the defaults will be in the manual - often something as obvious as 'admin' and 'admin'. Once you've logged in you'll be in the configuration interface. Look under 'wireless' and you should be able to find where to change the channel. All changes have to be saved otherwise they'll be lost when you power down the router.

If you need more help, post details of the router - make and model.

---

### Post by jeannacav on 2009-12-26
Looks good coffeecat.
I changed from 11 to 6 and it looks good 95% for now.

My other machines are a mac, and an xo-laptop.
The xolaptop is not able to connect via ethernet at all and when it was booting and searching for a wireless connection point it bumped jeanna-ubu off, After I changed to channel 6 it searched again but did not bump the ubu. Sooo, it looks good.

Thank you so much.

I turned on janitor this morning and it gave me a list of things to delete 3 of which were backports items.
Do you think it is safe to let janitor remove all of them?
(In each case, it does say something else has taken its place.)

Thanks again.

jeanna

Well,
Foss just joined and knocked me off again. So, I guess it is not fixed. yet.
I am gonna run the janitor and hope for the best.

Second edit
5 hours later.
I am closing for the night.
It seemed to get dangerously close once or twice but never went totally off.
It does seem odd that it has a hard time with the router that is 2 feet away and yet pickups the full signal of others so far away I don't even know their names, but as long as I can stay connected, it is ok.
never ran the janitor.

THANK YOU COFFEECAT

jeanna

---

### Post by coffeecat on 2009-12-27
> **jeannacav said:**
> 
never ran the janitor.

I'm glad to hear it. I've come across threads where Janitor has taken out essential things. I've never bothered with it myself but, like a lot of things like this, you probably need to be very cautious about anything it's recommending to remove. Deleting the backports items doesn't seem to be a good idea.

Let's hope the channel change helps long term. Don't forget that things like baby monitors and a whole load of other stuff can interfere with wireless. There's a lot of interference near that frequency. So it's not just a matter of monitoring your neighbours' networks. Older microwave ovens can be a problem as well - or so I believe. You might have to try a number of different channels over a period of days before you are confident you are OK.

And maybe it's the case that the Atheros driver in Jaunty is simply not particularly good.

Good luck!

---

### Post by Zilliano on 2009-12-30
Still battling Karmic with no results, dangit. >_>

---

### Post by Zilliano on 2010-01-10
Okay, seriously, has this been solved yet?

---

### Post by n125 on 2010-01-10
I've been having [connectivity issues]("http://ubuntuforums.org/showthread.php?t=1376220") as well. The backports solution also gave me the exact same problem, except that I have the AR9285 in the Asus 1005HA. In fact, installing them broke Firefox 3.5.7, which needed to be reinstalled; it would no longer start until then. After that everything seemed to work fine, until my display turned off because the computer was idle--this froze the entire system and it needed to be turned off completely. After the OS booted up again, of course, the backports failed. 

Prior to all these connectivity issues, I had wireless running on 9.10 just fine for a period of about 3-4 weeks though, so I don't know what suddenly went wrong. I have to use Windows until I find a solution. :(

---

