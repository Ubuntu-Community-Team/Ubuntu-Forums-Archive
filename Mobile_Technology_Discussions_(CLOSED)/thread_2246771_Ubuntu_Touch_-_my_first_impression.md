---
title: "Ubuntu Touch - my first impression"
date: 2014-10-03
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Pelvur on 2014-10-03
Here is my first experience with Ubuntu Touch.
I was teased enough to try Ubuntu on Android, but after installing it, I couldn't boot into Ubuntu. The Ubuntu sign appeared on black screen, and nothing else happened for a long enough time. So since I anyway just opened boot loader and had to reset my Android, I decided to make clean installation of Ubuntu Touch onto my Nexus 4.
That went well. &#8216;Well&#8217; means the phone booted into OS, picked up a carrier network, I was able to setup wireless during initial setup. It was late evening already, so I decided to set an alarm and go to sleep and play with the new OS next day. I wasn't able to setup an alarm. Hours and minutes jumped on their own. I set up for 6 am, it rolls itself to 4 am. Well, I set it for 8 am, it rolls itself to 6 am (kind of what I need). But when I&#8217;m done, it shows that alarm is set to 4 am. I tried to install an app for alarm, I found one in the store, I installed it, but it didn't open. I waited for about five minutes for it to open - no success.
Fortunately, after I restarted the phone, the problem with clock app disappeared (it comes back after factory reset though). But just to be on a safe side, I used backup alarm for today.
I was able to connect my phone to my car multimedia via bluetooth, but although it shows connected, the music still plays through phone speaker and not through the car. Not sure about phone calls, didn't have a chance to try that.

There is option to register your evernote account, but there is no app. Why do I need the account then?
Amazon, Ebay, facebook, twitter, gmail are preinstalled.
Camera is lagging a bit. 
To open any application, it takes several seconds. Literally, you sit and wait for it to open. Simple things like calendar and calculator - 5-6 seconds to open. 

I tried to connect to wireless network in my office and failed. I can see the network initially, but when I tap it, nothing happens, when I tap couple more times, all networks disappear, and I&#8217;m not able to see them before I restart the phone. And then I cannot connect to it anyway. And I cannot get data through carrier as well, so unless I'm on WiFi, I cannot connect to internet. 

Didn't find shortcuts for turning silence mode on. Had to go to system settings=> sounds and turn it on there. Not the shortest way. 

I guess I shouldn't mention about lack of applications, that&#8217;s obvious. I was disappointed that there was no way to setup the corporate account, but other than that I did not expect much anyway. If things like WiFi and Bluetooth work ok, I could probably survive with it for a while, but without it, I don&#8217;t see the point. Most probably, this first day will be my last day, and I will flash android back this evening. Whenever I get new phone (I think about original Moto X), I can play with my nexus some more, but having Ubuntu as the only phone is not an option right now. I understand why Canonical still do not provide Ubuntu phones &#8211; it is simply not ready.

---

### Post by grahammechanical on 2014-10-03
Have you reported these bugs? If not then, what is the point of installing what is in effect a developer image? 

> [COLOR=#333333][FONT=Ubuntu]Ubuntu for devices is still under development. Installing an Ubuntu for devices image may make your device unusable. Important features may be missing or broken. New images may introduce new features and may break existing features as development continues. Ubuntu for devices does not yet provide a reliable replacement for your current handset, phone or tablet.[/FONT][/COLOR]

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

Canonical does regular usability testing using ordinary people. This kind of testing has often shown up bugs and also the need for some of the core apps to be re-designed. The development of Ubuntu for devices will continue for some months beyond the release for retail of actual devices by the two OEMs signed up by Canonical.

Regards.

---

### Post by balloons on 2014-10-03
> **Pelvur said:**
> Here is my first experience with Ubuntu Touch.
I was teased enough to try Ubuntu on Android, but after installing it, I couldn't boot into Ubuntu. The Ubuntu sign appeared on black screen, and nothing else happened for a long enough time. So since I anyway just opened boot loader and had to reset my Android, I decided to make clean installation of Ubuntu Touch onto my Nexus 4.

Multiboot works great for this. Check it out! BTW, which version did you install? Is it perhaps quite old?
> **Pelvur said:**
> 
That went well. ‘Well’ means the phone booted into OS, picked up a carrier network, I was able to setup wireless during initial setup. It was late evening already, so I decided to set an alarm and go to sleep and play with the new OS next day. I wasn't able to setup an alarm. Hours and minutes jumped on their own. I set up for 6 am, it rolls itself to 4 am. Well, I set it for 8 am, it rolls itself to 6 am (kind of what I need). But when I’m done, it shows that alarm is set to 4 am. I tried to install an app for alarm, I found one in the store, I installed it, but it didn't open. I waited for about five minutes for it to open - no success.

The clock app handles alarms; did you discover the bottom edge gesture? This experience makes me think you are using a quite old image.
> **Pelvur said:**
> 
Fortunately, after I restarted the phone, the problem with clock app disappeared (it comes back after factory reset though). 

Sounds like a bug. If you are running the latest version, you should file it. [https://bugs.launchpad.net/ubuntu-clock-app/+filebug](https://bugs.launchpad.net/ubuntu-clock-app/+filebug)

> **Pelvur said:**
> 
But just to be on a safe side, I used backup alarm for today.
I was able to connect my phone to my car multimedia via bluetooth, but although it shows connected, the music still plays through phone speaker and not through the car. Not sure about phone calls, didn't have a chance to try that.

Phone calls should work; not sure about music actually, I haven't tried.
> **Pelvur said:**
> 
There is option to register your evernote account, but there is no app. Why do I need the account then?

The reminders app installed by default handles this

> **Pelvur said:**
> 
Amazon, Ebay, facebook, twitter, gmail are preinstalled.
Camera is lagging a bit. 
To open any application, it takes several seconds. Literally, you sit and wait for it to open. Simple things like calendar and calculator - 5-6 seconds to open. 

Application startup time is a known issue and work is being done to address it. You are not alone on this!

> **Pelvur said:**
> 
I tried to connect to wireless network in my office and failed. I can see the network initially, but when I tap it, nothing happens, when I tap couple more times, all networks disappear, and I’m not able to see them before I restart the phone. And then I cannot connect to it anyway. And I cannot get data through carrier as well, so unless I'm on WiFi, I cannot connect to internet. 

What's the detail on the wifi network in the office? Does at home work? Sounds like there might be something unique.

> **Pelvur said:**
> 
Didn't find shortcuts for turning silence mode on. Had to go to system settings=> sounds and turn it on there. Not the shortest way. 

I guess I shouldn't mention about lack of applications, that’s obvious. I was disappointed that there was no way to setup the corporate account, but other than that I did not expect much anyway. If things like WiFi and Bluetooth work ok, I could probably survive with it for a while, but without it, I don’t see the point. Most probably, this first day will be my last day, and I will flash android back this evening. Whenever I get new phone (I think about original Moto X), I can play with my nexus some more, but having Ubuntu as the only phone is not an option right now. I understand why Canonical still do not provide Ubuntu phones – it is simply not ready.
If you are willing to keep providing feedback and helping us refine the image, check out multiboot as I said and dual boot between the two. Join the ubuntu-phone mailing list ([https://launchpad.net/~ubuntu-phone](https://launchpad.net/~ubuntu-phone)) to stay up to date about what is going on.

---

### Post by Pelvur on 2014-10-03
I agree, this is still in development... for like 2-3 years already. So I expected it to work better. But yes, I have reported the bug regarding the clock app.

---

### Post by Pelvur on 2014-10-03
> **balloons said:**
> Multiboot works great for this. Check it out! BTW, which version did you install? Is it perhaps quite old?

The clock app handles alarms; did you discover the bottom edge gesture? This experience makes me think you are using a quite old image.

It was utopic, so I guess it was quite new.

> Sounds like a bug. If you are running the latest version, you should file it. [https://bugs.launchpad.net/ubuntu-clock-app/+filebug](https://bugs.launchpad.net/ubuntu-clock-app/+filebug) 

I did report a bug.




> The reminders app installed by default handles this

Ye, I found that out already.


> What's the detail on the wifi network in the office? Does at home work? Sounds like there might be something unique.

Home network works. The office one might be due to some restrictions, it might require special software installed which we only have for Android and iOS.


> If you are willing to keep providing feedback and helping us refine the image, check out multiboot as I said and dual boot between the two. Join the ubuntu-phone mailing list ([https://launchpad.net/~ubuntu-phone](https://launchpad.net/~ubuntu-phone)) to stay up to date about what is going on.

I'd love to keep it, the system is beautiful, but I need the functions, so even if I install dual boot, I hardly will boot into Ubuntu. However, as I said, once I get a new phone (plan to do it till EOY), I will install Ubuntu again on my Nexus. I might try multiboot before that though.

---

### Post by nikkkko on 2014-10-10
I installed last night on my Nexus 4 by multirom, which was incredibly easy btw.  I was also quite underwhelmed by the UT experience - two showstoppers for me which prevent me trying it out seriously.

1 No CardDav that I can see so I can't populate my address book. (I use fruux)
2 No cut and paste that I can make work so no work around for the above...

Otherwise quite slick in operation.

---

