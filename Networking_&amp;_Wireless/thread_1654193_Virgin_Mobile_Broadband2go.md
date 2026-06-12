---
title: "Virgin Mobile Broadband2go"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by zoggerman on 2010-12-28
I've tried pretty hard to make this USB data device work. So far I have an account I started over their tech support line, they took my money for one month service. I can even login there, I definitely have an active account according to their website, but I know this device needs something else.

  Using network manager it finds the dongle readily and correctly identifies it, I can make a new account, and it makes a connection, but can only surf their website and no others. I tried manually using wvdial with the same results, I get the DNS server numbers, etc. 

 So, my question, has anyone been able to get one of these working and surfing normally in Ubuntu without *first* activating it with a windows connection? If so, how, as I have no windows machine to access at all?

 Thankyou in advance, and yes, I did read the threads here first and search a lot and read some pages elsewhere, but can't seem to find a success story *without* that pesky windows activation first step. The modem works, network manager works, wvdial has always worked, but this thing just won't surf past their site is all. There's one little piece of the puzzle missing and can't seem to figure it out or find it.

---

### Post by zoggerman on 2010-12-28
Anyone have any clue? I live out in the sticks and am trying to get something approaching broadband here. Cheapest raggiest windows machine around here is a hundred bucks, which I just can't swing just to use for 15 minutes or something like that to activate a dongle,and I am sorta tapped as it is now. And no, none of the bubbas I know around here even have a computer...for real. There was one family near me but they moved.  Has anyone had any luck with WINE? Now I regret not installing it previously, am using a cheap cell phone connection now so I can't rally download it and install it.

TIA

---

### Post by trinitydan on 2010-12-28
> **zoggerman said:**
> Anyone have any clue? I live out in the sticks and am trying to get something approaching broadband here... ...And no, none of the bubbas I know around here even have a computer...for real. There was one family near me but they moved.  Has anyone had any luck with WINE?

Damn, I thought I was in the boonies.  :D  No computers???  

I wonder if it has kernel level drivers?  If not, you may be able to get it to run in wine through the USB.  Did you see if the program will run in Wine yet?  That's an important first step.  If it does and the device does not use kernel level drivers you could make a sym link and get the USB to be recognized by Wine, but this only works with simple devices like my DeLorme GPS, and not with iPods and Zunes etc.  It might be worth a shot.

---

### Post by oldsoundguy on 2010-12-28
Be apprised that Virgin leases it's tower space from Sprint (formerly Southern Pacific Railroad).  If you have crappy reception for Sprint (a common occurrence when you get more than 5 miles either side of a rail line), you will have crappy reception with Virgin.  I dumped them last year.

---

### Post by zoggerman on 2010-12-28
> **oldsoundguy said:**
> Be apprised that Virgin leases it's tower space from Sprint (formerly Southern Pacific Railroad).  If you have crappy reception for Sprint (a common occurrence when you get more than 5 miles either side of a rail line), you will have crappy reception with Virgin.  I dumped them last year.

Already use sprint through a reseller and my reception is perfectly fine. That is the iden network. The CDMA network is what the dongle runs on and it too gets a good reception, I can plug it in, get to just their website fine. 

The problem is you need a windows xp sp2 or 3 or newer windows machine to do the first activation, apparently they need to transmit something back to the dongle to get it running correctly for their purposes. You have to do the activation through a windows centric "admin panel" that is contained someplace in the dongle. Under ubuntu I can't see it or find it, but network manager makes it work as a modem, I just can't authenticate via any other method. I tried going through their tech support, got an account established, I have the dialin number assigned and so on, you use that for the account name then your official password, got that, but even inputting that doesn't allow you to really get online, you stay stuck on their web page only.

So anyway, the question was, if anyone who actually owns one of these things has been successful in getting it fully authenticated without that windows step. Every single web page and thread I have found on them there internets after a lot of looking, that says "success", All had to start with a windows connection, THEN it will work with linux.

You see there's a difference, getting it to work as a modem is easy, getting it to work as an authenticated user on the virgin mobile network is windows or later version mac only.

The reason why I don't have WINE is I never needed it before, been over ten years now since I really needed or even bothered to use windows anything, so never bothered to install it. The cell/tether connection I have now is just too slow, would take all day to do that pitiful small download to even attempt it to see if that method would work, and by then most likely I'd get kicked off my cellphone for massive misuse/tethering, so I don't want to chance it. As it is, I jump on and off for a few minutes now and then.

Thanks for the reply!

---

### Post by zoggerman on 2010-12-28
> **trinitydan said:**
> Damn, I thought I was in the boonies.  :D  No computers??? 


I wonder if it has kernel level drivers?  If not, you may be able to get it to run in wine through the USB.  Did you see if the program will run in Wine yet?  That's an important first step.  If it does and the device does not use kernel level drivers you could make a sym link and get the USB to be recognized by Wine, but this only works with simple devices like my DeLorme GPS, and not with iPods and Zunes etc.  It might be worth a shot.

Naw, no WINE, see my other reply below. I *would* chance that download, IF I knew for a fact that it was doable then, if someone had done it previously and reported the A-OK on it. I just don't want to bork the only pitiful connection to the net I have now by over use.

--well, to be fair, I don't know every single soul around here, but of the people I do know, they have like satellite TV or something. I really need a windows boot to dork around with this thing, and was trying to avoid having to purchase a windows machine just to get it activated, because then I would never use it again most likely and people are still real high on what they want for old crap. Heck, there's someone trying to sell a used compaq keyboard for fiftenen bucks around here! Full computers of the old pentium sub nothing range go for decent bucks, those that sell anyway, and I just slap won't pay that much for old ancient junque. Local computer shops want a hundred for something with 256 megs old style PC133 ram..prices like that (I called all the local ones, sheesh they want a lot for junk), and like I said, tapped right now anyway.


Thanks for the reply! My post is just more looking to see if there are any advances with the people who actually managed to make this work, or figured out the windows centric secret formula when they used their windows boot to do the first activation. I know several folks here have done it, but near as I can see they all just dual boot or have access to a handy windows machine to do the first step. After that in 10.4 or 10.10 is just works. I'm running 10.4 and network manager sees the device and can deal with it, my prob is dealing with virgin mobile and no direct access for linux folks.  Went through the same crap with the satellite internet dudes, wouldn't even come out if you were running linux.

---

### Post by trinitydan on 2010-12-28
I found this:

"Installation was straightforward on both, although admin-level  privileges were required on the Mac as the software installs kernel  extensions in the computer's System directory. An unusual reboot is  required here."

Here:
[http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=3224224](http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=3224224)

From the looks of things, Wine would have been a waste of your time/bandwidth anyway as the sym link method I was reffering to will not work with kernel level drivers.  Sorry I can't help.  I hope you can figure it out or find a Windows machine to use.

---

### Post by zoggerman on 2010-12-29
> **trinitydan said:**
> I found this:

"Installation was straightforward on both, although admin-level  privileges were required on the Mac as the software installs kernel  extensions in the computer's System directory. An unusual reboot is  required here."

Here:
[http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=3224224](http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=3224224)

From the looks of things, Wine would have been a waste of your time/bandwidth anyway as the sym link method I was reffering to will not work with kernel level drivers.  Sorry I can't help.  I hope you can figure it out or find a Windows machine to use.

Look on this page

[http://www.novatelwireless.com/index.php?option=com_content&view=article&id=162&Itemid=107](http://www.novatelwireless.com/index.php?option=com_content&view=article&id=162&Itemid=107)

OK, on novatels site they readily admit this works under Linux, but you need that windows step, this is established. That page shows the admin software they most likely use, the "MobiLink Connection Manager & Driver Installer" which is the windows only part. The drivers under that are irrelevant for our purposes because we can already get the thing acting as a modem, it dials out just fine as it is. Or maybe there is one more thing with the windows drivers, the links are there for that as well. I know you need to input three numbers, and so far just the two numbers get inputted o the linux side. Maybe there is more, but seems rather important to get that third number going...

  Now, all we need is someone (anyone who knows what they are doing and can decipher what is what here, which ain't me) to look at those windows bits and determine where the SECOND phone number goes in the connect script I am guessing, but the clue is in there. When these devices are activated, the actual dial out number (on mine anyway) is #777.  They issue you a phone number (labeled MDN) which is your user name. You pick a six digit number for a password. This is normal stuff, but wait, there's more! Now there's a second phone number they issue you (all of this so far can be accomplished over the phone, no windows needed) that is labeled MSID. that thing right there, what is that??  I don't know what that MSID is, and there is no place so far on the linux side to input it, at least I can't see where it goes, in either a raw wvdial connect script, or in network manager. 

This is apparently the crucial step to be able to log in and get going surfing, all the other "admin" jazz contained in that windows software is irrelevant, as you can do the same thing online anyway, check megs used with your plan, time remaining, cash remaining,, add cash to the account, that stuff. I can login to mine and do all that stuff now! Just can't surf past their site... 

I am guessing all of this amateur analysis so far, but that second phone number needs to be in the mix, I just don't know where to put it, and I don't know what "MSID" is either. 

I don't know another appropriate place to ask either, who is working on this aspect of the kernel and networking, etc? Being able to skip the windows part would be a great leap forward for linux (any time that happens), plus help out not only me but the millions of people stuck in the burbs and rural areas who have no other option for anything of a connection besides slow expensive dialup. 40 bucks a month for much faster than dialup plus NO CAPS according to their advertising is not too shabby at all. This beats the pants off of all other cellular based data plans out there at this time.

If any kind soul reading this could please forward this thread, etc to the appropriate smart guys who work on this networking stuff, at canonical or gnome or at the kernel level, etc, I would certainly appreciate it! I can keep monitoring here for responses. Thanks in advance to all who have tried to help so far!

---

### Post by Tig3rzhark on 2011-02-07
Ok, I have managed to get on the Internet using Virgin Mobile Broadband2go.  

However, the only site I can visit, is [http://www.virginmobile.usa.com]("http://www.virginmobile.usa.com").

No matter what I clicked, I couldn't go anywhere else.  I couldn't even go into my account to purchase the bandwidth.

A little help would be nice.  I'm using the usb modem that they were selling for 69.99 at Radioshack.

Could anybody help me with this?!?

What makes it more worse, has to do with the fact that even after purchasing bandwidth, I can only access one website.  What type of crap is that?

---

