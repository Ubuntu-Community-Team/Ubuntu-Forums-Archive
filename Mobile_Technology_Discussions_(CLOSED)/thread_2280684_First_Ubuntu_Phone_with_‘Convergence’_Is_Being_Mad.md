---
title: "First Ubuntu Phone with ‘Convergence’ Is Being Made!"
date: 2015-06-01
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Linuxratty on 2015-06-01
Can we get excited yet? Why yes we can!:popcorn:
> The first Ubuntu Phone that will be capable of turning into a desktop PC will be made by Bq.

**A tentative launch date of October 2015** has been set for the convergence device, though this is likely to changed depending on the state of ‘converged’ code within the Ubuntu OS itself.

[http://www.omgubuntu.co.uk/2015/06/first-ubuntu-phone-with-convergence-is-being-made-by-bq]("http://www.omgubuntu.co.uk/2015/06/first-ubuntu-phone-with-convergence-is-being-made-by-bq")

---

### Post by grahammechanical on 2015-06-01
I am excited because a converged device will have to run desktop applications when it is connected to desktop peripherals and at the moment Ubuntu Desktop next, which is the phone OS running on the desktop, does not do that.

We have been told that there will be a desktop version of Ubuntu running on Mir with Snap packaging instead of Debian packaging. We have yet to see an ISO image for that. We have also been told that on the phone Snap packaging will replace Click packaging.

I am putting it all together and I get Ubuntu Snappy Personal (desktop) and Ubuntu converged phone both being built on Wily Werewolf (15.10 development) code base and both being usable by the end of October. 

I may not buy the phone but then again I may do but I am sure wanting to test Ubuntu Snappy Personal on my desktop machine.

Regards.

---

### Post by Jordan_Roberts on 2015-06-24
> **grahammechanical said:**
> I am excited because a converged device will have to run desktop applications when it is connected to desktop peripherals

But what about when you're on the go and you don't have any peripherals connected? Because I for one would like to run "desktop" Firefox **all the time**. The limited and truncated nature of all mobile browsers is the main reason that I am interested in Ubuntu convergence.

---

### Post by grahammechanical on 2015-06-25
> **Jordan_Roberts said:**
> But what about when you're on the go and you don't have any peripherals connected? Because I for one would like to run "desktop" Firefox **all the time**. The limited and truncated nature of all mobile browsers is the main reason that I am interested in Ubuntu convergence.

Is that also true of Firefox for Android and the Firefox browser in the Firefox OS? I wonder, in those use cases is Firefox the same code as Firefox on the desktop? Or is it a specially crafted version of Firefox for running on mobile devices?

And there is the problem. With Ubuntu phones the apps in the phone app store can be designed to scale properly and work usefully on phone, tablet and desktop size displays and to conveniently switch when the different screen size is detected and to notice when a keyboard and mouse are present. But desktop applications are not designed to scale down to tablet and phone screen sizes. They are not designed for touch screen operation. And changing this is the responsibility of the developers of the particular application.

Canonical engineers can code Unity 8 to detect when it is running on a phone or tablet and connected to a desktop monitor, keyboard and mouse, and then switch to the appropriate mode. As I understand it the device will still function as a mobile phone and the phone/tablet apps will be available when being used as a PC but I very much doubt if it will be possible to switch to PC mode and use the desktop apps when the device is purely a phone. I do not think that is part of the design. 

There is another difficulty. At present all applications that run on Ubuntu desktop are packaged as Debian packages (deb). But the Ubuntu phone requires applications to be packaged as Click packages and in future as Snap packages. It is all part of the security model for the Ubuntu phone. It remains to be seen just how converged a converged Ubuntu device will be.

As part of the convergence strategy there will be a Ubuntu desktop version that runs on the Mir display compositor and has Unity 8 and Click apps just like on the phone. It will also have Snap apps. But something has to be done to use the existing deb applications like Firefox and Libreoffice and not break the security model for convergence. We are awaiting an ISO image that can be installed on a desktop/laptop machine for testing. How things turn out it remains to be seen.

Do not have expectations that cannot be fulfilled. Or make demands that the developers have no intention of accepting.

Regards.

---

### Post by afclemenson on 2015-06-30
I have seen the ubuntu bq e4.5 floating around ebay from time to time. I have been thinking about buying one just to play with (not as main phone because the hardware is apparently pretty weak).

Will software for the version coming out in October be completely different from the ubuntu bq e4.5 or just updated (apart from the "convergence" ability)?

---

### Post by grahammechanical on 2015-07-01
The only mobile phone that I have is what you might call a "dumb" phone in contrast to a "smart" phone. And I do not use that phone all that much.

I have heard that with Android phones the OS on the phone only gets upgraded to a newer version of Android if the manufacturer of the phones decides to push out the newer version of Android. Not only that but each manufacturer modifies Android in some way. So, that there is a fragmentation of Android.

Things are done differently with the Ubuntu phone. And again, it is what I have heard. To start with Canonical takes responsibility for keeping the device up to date with the exception of any software that the OEM has added to "brand" the device.

Next, Ubuntu phones receive Over The Air (OTA) updates. There have already been 4 OTAs since Ubuntu phones were on the market. And work has started on OTA 5 to be pushed out sometime in July. This means that all those first BQ phones now have an OS that is as up to date as all those second BQ phones. And both devices will be up to date with the recently released Meizu phone. 

To give a practical example. The Ubuntu phone OS was first built on the Ubuntu 14.10 code base. Then after 14.10 was released work was done on producing Ubuntu 15.04. By means of OTAs any Ubuntu phone running on the 14.10 code base has now been upgraded to the 15.04 code base. It is intended that a Ubuntu phone purchased today will over time have the same Ubuntu OS as a phone released on the retail market in a year's time.

App developers can upgrade their applications and get the updated versions in the app store in a very fast and easy manner. In fact it is possible to have an older and a newer version of the same app in the app store at the same time. So, the Ubuntu phone does not need to be running year old apps if the developer has published newer versions in the app store.

Regards.

---

### Post by vq1 on 2015-07-06
I hope this is true. I want my next phone to be ubuntu. The MX4 and E5 are tempting but I'm going to try to hold out for a new one.

---

### Post by Jordan_Roberts on 2015-07-10
I don't know about the code, but from the user's perspective, bizarrely and annoyingly, the browser on Firefox OS does not resemble the Firefox browser on the desktop in any shape or form.

> **grahammechanical said:**
> But desktop applications are not designed to scale down to tablet and phone screen sizes. They are not designed for touch screen operation. And changing this is the responsibility of the developers of the particular applications.

The only thing I would really need to surmount these obstacles is ZOOM. That is it. A good, system-wide zoom function allows the user to make up for any lack of screen real estate, and to zoom in on any elements/buttons that might be too small.

Sure, by relying on frequently zooming in/out, it would still take a bit more time and effort for me to use desktop applications in that matter on the phone's screen, compared to using the handicapped mobile versions of those applications on the phone's screen. But it would definitely work, and I only care about the results. 

I am certainly not saying that every user should be forced to switch to the desktop mode while on the go...but why would you not give people the option at least? I thought the whole point of an open source device was to give people more options and more control.

> As I understand it the device will still function as a mobile phone and the phone/tablet apps will be available when being used as a PC but I very much doubt if it will be possible to switch to PC mode and use the desktop apps when the device is purely a phone. I do not think that is part of the design.

Then, sorry to say, I don't want it. If it is a phone that can only be used as a phone (except under very strict and specific conditions), then I could just continue using one of the thousands of phone models that already exist. There is no point to convergence if it can never give us the level of flexibility that I have just described.

---

### Post by Jordan_Roberts on 2015-10-16
> [COLOR=#000000]Do not have expectations that cannot be fulfilled. Or make demands that the developers have no intention of accepting.[/COLOR]
[COLOR=#000000]

It would appear that they have accepted the demand (i.e. to be able to run desktop Firefox on the phone) with this [recent decla]("http://thevarguy.com/open-source-application-software-companies/101515/canonical-says-ubuntu-phones-will-run-any-linux-app-open-")[ration]("http://thevarguy.com/open-source-application-software-companies/101515/canonical-says-ubuntu-phones-will-run-any-linux-app-open-"):
[/COLOR]> 
[COLOR=#1B1B1B][FONT=-apple-system-font]Smartphones running [Ubuntu Linux]("http://ubuntu.com/") from [Canonical]("http://canonical.com/") may soon support not just mobile apps, but all programs for open source, Linux-based platforms. That's according to developers working on bleeding-edge versions of [Ubuntu for phones]("http://www.ubuntu.com/phone").
...[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]This week, Ubuntu developer Michael Hall [posted proof]("https://plus.google.com/+MichaelHall119/posts/KQLz2aeizno") of Canonical's progress toward full Ubuntu convergence in the form of a screenshot from an Ubuntu-based Nexus 4 running desktop apps, including [GIMP]("http://gimp.org/") and [Firefox]("https://www.mozilla.org/en-US/firefox/new/").[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]...
After Hall posted the screenshot, Softpedia [confirmed]("http://news.softpedia.com/news/ubuntu-phones-will-run-any-linux-application-on-top-of-unity-8-494496.shtml") with him that Canonical's plan is indeed to make it possible to run any Linux application on Ubuntu.[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]
As Hall recognized, not all Linux applications designed for desktops and laptops are likely to work well on phones, for practical reasons. "I doubt anybody would expect window controls and GIMP to play well on [small screens]," he wrote, noting that the graphics-manipulation program would be difficult to use without a bigger screen and traditional peripheral devices.[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]
Still, across-the-board support for Linux apps on phones would be a standout feature for Ubuntu. Android, the more popular Linux-based mobile operating system, can't actually run standard Linux apps at all. Generally speaking, [Apple]("http://apple.com/")'s (APPL) iOS and [Microsoft]("http://microsoft.com/") (MSFT) Windows for phones also don't support the desktop versions of apps for their respective ecosystems.[/FONT][/COLOR]
[COLOR=#000000]





[/COLOR]

---

### Post by Ginzel on 2015-11-20
Would [Neo900]("http://www.neo900.org") support ‘Convergence’, please?

---

