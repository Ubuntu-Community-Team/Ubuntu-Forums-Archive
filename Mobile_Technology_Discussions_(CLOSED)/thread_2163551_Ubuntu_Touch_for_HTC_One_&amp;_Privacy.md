---
title: "Ubuntu Touch for HTC One &amp; Privacy"
date: 2013-07-18
forum: Mobile Technology Discussions (CLOSED)
---

### Post by BretMan on 2013-07-18
I recently heard about Ubuntu Touch (for smartphones) and am excited about the possibilities to be free of Google and Microsoft and other trackers. I've only had a cell phone up to now and am about to take the plunge and am leaning towards an HTC One Mini, coming out soon.

I saw on the Ubuntu compatible devices list that the HTC One X is listed as ready. Is this the same as the HTC One and HTC One Mini?

Also, can someone explain to me how Ubuntu Touch as well as for PCs, protects my privacy? Do those OSs use a different browser and email than the FF and TB I'm already using? What about malware protection? Lastly, does Touch replace Android or does it install along with it and I select which OS I want to use when I turn it on?

Thank you,
Bret

---

### Post by Nr90 on 2013-07-18
Canonical is only porting Ubuntu Touch to the Google Nexus devices. Other ports are provided by the community.
Therefor there will not be a Touch port at the launch of the One Mini. The community might provide one quickly, slowly or not at all.

Privacy is too big a subject to discuss in a few lines. For one all the source code behind Ubuntu Touch is open source, so you and everyone else can see what is going on.
firefox and thunderbird do not have a Touch UI version yet. I doubt thunderbird ever will, but FF might very well develop one. Canonical and the community are developing a web browser, a mail client and other core apps.

Touch fully replaces Android.

If you want to use Ubuntu Touch full time instead of Android straight away, I'd get the Nexus 4.

---

### Post by grahammechanical on 2013-07-18
To confirm, Ubuntu Touch phone, smartphone & tablet devices will not be a kind of dual boot with Android system. They will be Ubuntu Touch devices, plan and simple.

Malware protection? At the moment we have a certain level of protect regarding software installed through the Ubuntu Software Centre because before applications are allowed into the software centre the code is audited. This is why it can take a long time for a developer to get an application accepted in the software centre.

If we download software from web sites then we do not have the same level of protection as anything could be in the code. Canonical is encouraging developers to develop apps for Ubuntu Touch using the Ubuntu Development Kit and to use a method of packaging that Canonical calls 'click.' 

This package system will speed up the acceptance of apps into the software centre and also give protection. As part of the 'click' packaging method the developer has to include with the code a manifest, a description of what the code does and the permissions the code needs.

If from examining the manifest it seems that the code will do nasty things to the OS and the user's data, then the application for acceptance will be refused. If everything seems fine the app will be accepted and the manifest will be used to create an AppArmor profile. If, whilst the app is running it tries to get access to an area that was not defined in the manifest or to use permission for something not defined in the manifest and so not fitting its AppArmor profile, then the app will be blocked.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

[http://www.webupd8.org/2013/05/ubuntu-might-get-new-simplified.html](http://www.webupd8.org/2013/05/ubuntu-might-get-new-simplified.html)

As for privacy, then you have define what you mean by privacy protection. For example, your cell phone when switched on makes frequent broadcasts to the cell phone radio masts. 'They' know which cell area your phone (and you) are in throughout day and night. If you have a mobile with GPS, then 'they' know where you are to within a few feet. Scary? Do not have a mobile phone. Ubuntu cannot protect you from that.

Regards.

---

### Post by ypBym3P on 2013-08-07
> **BretMan said:**
> 

Also, can someone explain to me how Ubuntu Touch as well as for PCs, protects my privacy? 
Bret

Historically Ubuntu Desktop has been pretty good about protecting privacy by not sending unknown/unwanted outgoing connections onto the internet. Basically, what you did on your computer stayed on your computer. Unfortunately, this is no longer the case with the recent Ubuntu releases.

However, you can manually configure Ubuntu to protect your privacy by uninstalling and configuring various things. If you install a version later than 12.04, you will need to make these manual configuration changes to protect your privacy. Some internet research should help you find the settings changes you will need to make to achieve the privacy you are after.

An Ubuntu Touch default install in all likelihood will not be very privacy friendly (based on the recent default installs of Ubuntu Desktop). So you will probably need to make similiar settings adjustment in Ubuntu Touch as well for Privacy.

> **BretMan said:**
> 
I saw on the Ubuntu compatible devices list that the HTC One X is listed  as ready. Is this the same as the HTC One and HTC One Mini?

Bret

No, the HTC One X is a different phone. The HTC One Mini has not been ported to Ubuntu Touch yet. You will have to wait and see if the community ports it in the future.



Cheers :)

---

### Post by 3rdalbum on 2013-08-08
It all depends entirely on what you consider "privacy" and acceptable transmission of data.

If you're looking to evade the NSA, you need a lot more than just Ubuntu to do that. The NSA can intercept all internet traffic across multiple nations, including all your online activities and any data sitting on Facebook's servers, so you'd need some kind of encrypted data channel going from your computer to somewhere else in a neutral country. A VPN, basically. You can use them on Windows too of course.

As you type into "Dash Home" on Ubuntu it sends the search query - but NOT your IP address or other identifying information - to Amazon's servers as a search query to be fulfilled. Ubuntu 13.10 will expand this to a wide range of useful websites, so by typing into the Dash you can search your own computer AND the web.

Every mainstream web browser sends certain information to any website you visit: IP address (from which the site can derive your ISP and approximate location), web browser version, operating system, screen resolution, plugins installed, the last page you visited and any search terms you had to type in to find the website.

These systems can be turned off or worked around  - they are there to be helpful - but they can also be turned off on Windows too. If you've moved to Ubuntu for privacy reasons, the move probably didn't make a lot of sense because the real threat to privacy is what you voluntarily send across the internet, intending it to be for "Friends only".

---

### Post by BretMan on 2013-08-09
Thanks very much for your complete replies. I learned a lot.

My privacy concerns are mostly focused on being tracked for location and for my online interests. I just don't think it's anyone's business but to those I want to know and that may be just me sometimes. I also deal with confidential information being involved with R&D, so I want what's in my phone or PC to be accessible only to me. Right now, I apply a security protocol of encrypting messages and files then sending them and receiving them that way - a bit of a pain but secure. My Firefox browser uses every tracking and script blocker add-on available. I also do routine anti-malware/virus scans.

I heard about the new VPN approach and that makes sense to access geo-blocked countries web sites for sourcing purposes. I also heard about [Tails - Privacy for anyone anywhere]("https://tails.boum.org/")  which I'll give a try and supposedly works with Ubuntu. However since it provides a clean disconnect from any PC, I'm not sure if while browsing I can bookmark sites to the thumbdrive or store other data on the same thumbdrive, which would be necessary to me.

So it seems I can't get the smartphone I want (HTC One Mini) with Ubuntu Touch - bummer. The youtube videos about Touch gave me the impression it was about to be the next big thing in a matter of months. It would be great if there were "Tails" type software for smartphones. People are now becoming aware of snooping and "middleman" threats everywhere and I'm pretty sure there is a strong market for that if it were available. One reason Blackberry's are still so popular outside the US is because of their security features. I just hate the thought of Google or Microsoft snooping into my life.

---

