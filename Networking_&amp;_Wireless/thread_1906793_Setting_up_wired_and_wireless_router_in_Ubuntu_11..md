---
title: "Setting up wired and wireless router in Ubuntu 11.10"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by Conscript on 2012-01-10
I am a grubby college student who just switched to Ubuntu after years of wrathing at Windows.

I have the intellect to install Ubuntu, but not use it properly or efficiently. So there is my life story, I don't know jack about Linux.  That is why I am here.

The apt complex I live in has a cable connection (I think) and all the rooms are wired with cat5.  I have a desktop with ubuntu and a laptop with ubuntu.  I want to setup the router so that I can run my desktop into it and use the wireless part of it for my laptop.

I have a Linksys model: WRT54G Router Ver. 6.  I can plug the ethernet it and light blink, but that is the extent of my wisdom.  I don't know much about ubuntu and don't want to break it.  Nor to I want to brick the router.

Using only the ethernet cable I can get internet access, which is what I am doing now.  Just tired of switching computers with the ethernet cable is all.

Looking for tech advice if any is out there, friend told me I should ask the Ubuntu Gods (forum) for wisdom.

If any can help, I will be most appreciative.

---

### Post by coldte on 2012-01-10
hi, It appears you have the same problem as me ,I have a similar problem and like you know zip about setting up the network despite over three days trying  to accomplish it.
Both pcs are on Internet but cannot see each other. would also appreciate a response.
regards

---

### Post by varunendra on 2012-01-10
Hi, and welcome to the forums both of you!

Since the 'Ubuntu Gods' seem too busy to notice your request, I guess it is okay if I try my wits for the moment.

> **Conscript said:**
> Using only the ethernet cable I can get internet access, which is what I am doing now.  Just tired of switching computers with the ethernet cable is all.

Have you read the user manual for your router? If you just have to plug in the cable to get connected, I believe it is already configured as needed, and you don't need to mess up with either LAN or WAN part of its setup. Just have a look at pages 13-14 of [this manual]("http://homedownloads.cisco.com/downloads/userguide/WRT54G_UG_WEB_20070529.pdf"), and make sure the SSID and encryption options (preferably- WPA Personal) are set and SSID broadcast is enabled. Then scan for wireless network availability in your laptop.

I have handled a few wireless access-points/routers, but not this specific one. So can't say if there are any other settings you need to check. But based on experience with the few others I've handled, the above should be all you need to do on router's part.



**_EDIT_:**

@coldte,
Your problem seems a bit different. Please provide us the details of the setup and the problem, including router model and operating systems involved. If it is significantly different (which it seems to be), I'd suggest to start a new thread with the details, and post a link to it here so we can follow.

---

### Post by Conscript on 2012-01-10
I should add one other problem I have.  I inherited this router from my father in-law.  I know that the beast works having used it in the past.  But I don't have the cd that comes with it.  So if there is an install screen, I don't have access to it.  Because I have looked in the Ubuntu network tab under system settings and saw nothing even close to the options presented.

Is there a way to obtain installation without the cd?  Because alot of the menus in the pdf you mentioned (which I downloaded) are nowhere to be found.

Color me puzzled.

---

### Post by varunendra on 2012-01-11
> **Conscript said:**
> Is there a way to obtain installation without the cd?  Because alot of the menus in the pdf you mentioned (which I downloaded) are nowhere to be found.
Don't worry about that, you don't need the cd or an installation software to manage a router/access-point. All of them have inbuilt web interfaces which present all the options and settings needed to setup/manage it (i.e., the screens/menus you've seen in the pdf).

Assuming its access and security settings are currently at factory defaults, follow page-7 of the pdf manual. It says its default LAN IP is **192.168.1.1**, user ID for login is 'blank', and the login password is '**admin**'.

So open your browser, type-
> [http://192.168.1.1](http://192.168.1.1) in the address field, and press 'Enter'. If the access settings are at factory default, you should immediately get a login authentication dialogue box. Leave the 'user-name' field blank, type **admin** as password and press 'enter'. Once you are logged into the web-management interface, you'll get all the menus you've seen in the pdf. Try the suggestions in my previous post afterwards. If the maze of menus seems confusing, some screenshots may help as the ones included in the pdf manual are too blurry to examine.

---

### Post by Conscript on 2012-01-14
I got to the IP address router site, but the site appeared all jacked up.  Missing windows and everything,  it looked like good old british dentistry.

Trying a different browser,  perhaps firefox isn't up to snuff?

We are closer than we were before however.  Hooray?

---

### Post by varunendra on 2012-01-14
> **Conscript said:**
> We are closer than we were before however.  Hooray?
I hope so :)
But it seems you have a connection problem with the router even with the cable interface, because that login page and the subsequent pages should open like a breeze since you are accessing them over LAN.

Accordingly, please test:
```
ping 192.168.1.1
```
the replying time should ideally be less than 1ms.

---

### Post by spacecheck on 2012-01-14
> **Conscript said:**
> I got to the IP address router site, but the site appeared all jacked up.  Missing windows and everything,  it looked like good old british dentistry.

Trying a different browser,  perhaps firefox isn't up to snuff?

We are closer than we were before however.  Hooray?
If the site does not appear properly, you may have javascript turned off in firefox. Turn it on with "Edit, Preferences, Content" and put a check in the box for "Enable javascript".
Then refresh the router page in the browser.
If images are not appearing properly, you may need to select additional options on the "Content" page mentioned above.

Also, after varunendra finishes assisting you with setting up your connection, don't forget to change the access data for the router, giving it a non-standard username and more secure password, using a longer combination of upper and lowercase characters interspersed with numeral.

Good luck!

---

