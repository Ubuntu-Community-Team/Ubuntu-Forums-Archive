---
title: "Gosh! 11.04 mostly stable with Nvidia open source drivers!"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CookieNinja on 2011-02-18
Just updated and finally found the desktop edition session works, and I can see unity! Please don't break it before I've given it a good go!

Still a little buggy, though. I right-clicked on the bin and selected emptying it only to find my whole desktop freezing. Restarting gdm did the trick, though!

I'm seeing quite a few problems with Unity, from a usability perspective, though! I'm seeing a number of very basic scenarios where it's very easy for the user to perform actions that do not work in the way that I expect them to. They're things a user could learn to understand, but a big part of me wonders whether or not they should have to! I've made a couple of mistakes a few times within a short space of time ... where I think the UI could be more helpful.

The bar along the top where the menu for every application is going to go is a right mess, too! Maybe trying to influence Gnome Shell would've been a better direction to take. I had less issues with that, when I tried it last.

---

### Post by mc4man on 2011-02-18
There was a small change to the mesa experimental lib that should allow alot more nvidia cards to use unity, don't expect you'll see breakage from that anymore.

There was a change to exposing the launcher w/ mouse trigger when using any of the 3 autohide modes that may prove to be a bit confusing initially. (some adjustments are being made there.

Curious - what do you mean by "bin"?

---

### Post by CookieNinja on 2011-02-18
> **mc4man said:**
> 
Curious - what do you mean by "bin"?

The rubbish bin, or trash can if you're American.

---

### Post by coffeecat on 2011-02-18
> **CookieNinja said:**
> The rubbish bin, or trash can if you're American.

Here in the UK my rubbish bin can't decide whether it's a rubbish bin or a wastebasket when I open it with Nautilus.

Typical British muddling through, if you ask me. :wink:

---

### Post by CookieNinja on 2011-02-18
> **coffeecat said:**
> Here in the UK my rubbish bin can't decide whether it's a rubbish bin or a wastebasket when I open it with Nautilus.

Typical British muddling through, if you ask me. :wink:


I've never noticed that, but I remember reading about it. Mind you, neither of those terms are in touch with the recycling era we;re living in, so there'll probably be a law to ban both terms!

I'm not so sure about the stability of Unity with the open source Nvidia drivers now, either :( Found far too many ways to crash it, most of them involving use of the various searching options that overlay the desktop. I also don't like the lack of visual clues as to how to close them, either. I just click the mouse a few times outside of it and it goes. Hardly an intuitive mechanism.

---

### Post by coffeecat on 2011-02-18
> **CookieNinja said:**
>  Mind you, neither of those terms are in touch with the recycling era we;re living in, so there'll probably be a law to ban both terms!

Seeing as how there's a recycle bin on the Windows desktop, I think there might be some resistance to using that term in Ubuntu, however ecologically friendly it is. :)

> **CookieNinja said:**
>  I'm not so sure about the stability of Unity with the open source Nvidia drivers now, either :(

I'm sorry to hear of all the traumas people with nvidia cards and Natty are going through at the moment. It's made me glad that I converted to ATI graphics on my desktop during the Maverick testing cycle, and that I have ATI in one of my laptops. The open source ATI driver (with the right card) has been a joy to use in Lucid, Maverick and now Natty.

---

### Post by mc4man on 2011-02-18
> I'm not so sure about the stability of Unity with the open source Nvidia drivers now, either Found far too many ways to crash it, most of them involving use of the various searching options that overlay the desktopNot too sure that has anything to do with the drivers, though you never know
Using the dash or applications/files places repeatability does tend to crash compiz, I just think they still need some work (I can get about 12 -20 uses before compiz crashes

It may be marginally useful if the places icons included a 'quit' option, though they do close when selecting an item in them, or clicking elsewhere, so not really needed - the dash can closed by clicking on ubuntu icon

---

### Post by CookieNinja on 2011-02-18
> **coffeecat said:**
> Seeing as how there's a recycle bin on the Windows desktop, I think there might be some resistance to using that term in Ubuntu, however ecologically friendly it is. :)



I'm sorry to hear of all the traumas people with nvidia cards and Natty are going through at the moment. It's made me glad that I converted to ATI graphics on my desktop during the Maverick testing cycle, and that I have ATI in one of my laptops. The open source ATI driver (with the right card) has been a joy to use in Lucid, Maverick and now Natty.

I have too many bad memories of using the closed source drivers and sub-standard open source ones. Outside of alpha/beta releases, my experience with the closed source Nvidia drivers has been pretty much perfect for me. I'll probably look into the whole ATi driver thing when it comes to my next upgrade in a few years time (I don't tend to upgrade the CPU/Motherboard/Gfx very often, and this system is less than a year old).

---

### Post by clivejo on 2011-02-21
I must say I prefer Nvidia over ATI any day!  My last computer purchase was based on a decision to avoid ATI at all costs!

Unfortunately, it seems Nvidia are being a bit slow in getting a driver out.  But I'm currently using nouveau and managing OK.  I have tried installing the Nvidia driver via restricted driver and manually but no success as yet.

However, I keep experiencing random freezes which I cant seem to get to the bottom of.  Any else with the same?  So far it seems to be Pidgin and FireFox, but as these are the programs I spend most time in I dont think its actually a problem with the applications.

---

### Post by Harry33 on 2011-02-21
> **clivejo said:**
> I must say I prefer Nvidia over ATI any day!  My last computer purchase was based on a decision to avoid ATI at all costs!

Unfortunately, it seems Nvidia are being a bit slow in getting a driver out.  But I'm currently using nouveau and managing OK.  I have tried installing the Nvidia driver via restricted driver and manually but no success as yet.


If you have xserver 1.10 series (1.9.99.*) installed nvidia proprietary drivers do not yet work.
Now that xserver 1.10 rc2 has been released, it will not take long until new NVidia drivers are released too.
I bet xserver 1.10 compatible NVidia driver is released sooner than AMD's fglrx driver.

---

### Post by clivejo on 2011-02-21
Yes I agree, Nvidia are normally very quick as getting out drivers and the thing that made me pick Nvidia over the rest.

Still two months to go, so I wont be getting my knickers in a twist just yet!

---

