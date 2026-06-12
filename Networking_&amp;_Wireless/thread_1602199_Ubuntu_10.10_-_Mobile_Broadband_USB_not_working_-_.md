---
title: "Ubuntu 10.10 - Mobile Broadband USB not working - 4 devices tested"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by NathanScrivener on 2010-10-21
Hi, I am running Ubuntu 10.10 on Hp Mini 110. I can't get Mobile Broadband to work ... whenever I plug a USB device in, nothing is detected and there is no option to connect to mobile broadband.

The devices I have tested are; 

1. ZTE MF636
2. ZTE MF626
3. Huawei K3565-Z
4. Nokia 5800XM phone in PC Suite Mode (works on my other laptop running Ubuntu 10.04)

I have tried uninstalling with a full purge of USB-Modeswitch and then reinstalling it. 

This machine is upgraded from 10.04. It wasn't working in 10.04 either.

If somebody would be kind enough to help, I would be very grateful.

Thank you.

---

### Post by alexfish on 2010-10-21
Hi

try sakis3g, it also has good diagnostics 

**[*Sakis3G*  - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=_xfATNXQK8jh4Abx14CoDA&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

Suggest (usb modeswitch embedded)

they also have a forum , very helpful

in Ubuntu 10.10 you may have to disable modem-manager 

alexfish

---

### Post by NathanScrivener on 2010-10-21
Thank you very much for your reply Alexfish. This script seems to find the modem and initiate a connection.

However it is not as ideal as a working connection with the Ubuntu network manager. This should work .. and works on other machines I have tested.

One thing is that I had installed the Betavine Vodafone Connection Manager. I think that this may have broken things. It is like Mobile Broadband built in scripts have been simply disabled.

I'd really like it if anybody had any ideas about repairing the out-of-box functionality.

Thanks
Nathan

---

### Post by alexfish on 2010-10-21
Have you contacted Betavine about the problem

---

### Post by NathanScrivener on 2010-10-21
Hi Alex, thank you again for your reply, yes I have posted on there, but their forums do not seem very active. 

Hopefully somebody on one of the two forums will provide some insight!

---

### Post by alexfish on 2010-10-21
you are not alone on this one

[VMC software from Betavine{ vodafone mobile  connect re:Betavine Connection Manager}]("http://ubuntuforums.org/showthread.php?t=1548553")

perhaps leave some remarks on same thread

if you have further problems

feel free to post back here , see if we can help

regards

alexfish

---

### Post by NathanScrivener on 2010-10-21
Thanks! I will try the steps mentioned in that thread to restore the system.

I agree, totally irresponsible for their software to break core functionality in Ubuntu without having an option to reinstate it.

Simply removing the software through Synaptic did not fix things.

---

### Post by alexfish on 2010-10-21
Hi

Now if your system has been restored , can you explain in detail,  the objectives that led to installing this type of software.

there may be other ways 

alexfish

---

### Post by NathanScrivener on 2010-10-21
Hi,

I haven't actually done that yet but intend to try out the steps you mentioned in that thread.

The appeal that the Betavine software offered was that it would supposedly allow sending SMS messages. This is to aid with pre paid data packs which can be purchased via SMS messages, much easier than having to phone Vodafone to make a purchase.

Unfortunately the SMS functionality did not work for me anyway so I elected to remove the software.

Thanks again
Nathan

---

### Post by alexfish on 2010-10-21
hi

Normally Vodafone have a web service page for setting up accounts even for prepaid

try searching vodafone accounts + country

once the account is set up this will allow the options you want ,even payment with vouchers, so  the functionality of payment is the same , have you tried this

as for sms texts possibly try wammu , think it may be in synaptic

there may be one thing hindering the sms texting on 10.10 ,

when the connection is made with the Network Manager then the second function of the modem may not be accessible

to overcome this you can use sakis3g in combination with wammu

forgot to add ( the Vodafone Accounts pages are normally accessible even if your balance is zero )

alexfish

---

### Post by bill.denbigh on 2010-10-21
I have exactly the same problem with my globe tattoo ZTE 626 modem. This i understand is a problem with modeswitch 1.1.4 that is now included in ubuntu 10.10

A similar problem is reported in:
[https://bugs.launchpad.net/ubuntu/+s...ch/+bug/626568]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568")

I have been trying to find help with this here:

[http://ubuntuforums.org/showthread.php?t=1595964](http://ubuntuforums.org/showthread.php?t=1595964)

and:

[http://ubuntuforums.org/showthread.php?t=1594029](http://ubuntuforums.org/showthread.php?t=1594029)

but to date have had no help...

Sorry to not give you a solution, just misery loves company :wink:

---

### Post by alexfish on 2010-10-21
Hi Bill

the device you relate to is not your device 626

however  , zte 626 should work , First reinstate the usb_modeswitch as original

see  what happens ,Please post back on you own thread , if still a problem

regards

alexfish

---

### Post by Vtwin on 2010-10-22
Hi I'm quite new to Linux and Ubuntu and so what I'm saying may not be a good idea but it worked for me with my ZTE 112 in the UK. I have a new install of 10.4 with no updates done at all yet and I don't have modeswith installed either. You'll have excuse it if my explanation is a bit newbie.

I used network manager to add my mobile broadband details
I opened the terminal and did lsusb which showed up my dongle with the ID numbers 19d2, 0103.
I then did sudo gedit and navigated to /lib/udev/rules.d/61-mobile-action.rules. I don't know how use the terminal to navigate so did this using gedit itself.
At the bottom you see the device ZTE MF6XX. I copied/pasted and changed the "2000" to my own number "0103. When I rebooted I had 3 mobile as an option and now it works fine, so far.
Perhaps this could work for you but as I say it was far more by luck than judgement.

---

### Post by beercz on 2010-10-22
I've been having similar problems (see [http://ubuntuforums.org/showthread.php?t=1240240](http://ubuntuforums.org/showthread.php?t=1240240)) and have reverted back to 10.04 temporarily because of this and other issues with 10.10.

When I have more time I will have another go with 10.10.

---

