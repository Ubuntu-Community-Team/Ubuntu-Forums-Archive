---
title: "Recommondations for Linux friendly wireless USB?"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by whoopsbob on 2009-09-14
I wasn't careful enough when buying my most recent laptop and I've got an unsupported wireless card, so I want to buy a USB adapter. Anyone got recommendations for something that'll just plug and play on most distros, and is cheap and well built? I know there are lists out of there of what's compatible with Linux, but that doesn't mean it's a good buy

---

### Post by Genius314 on 2009-09-14
I use this thing: [link]("http://www.belkin.com/IWCatProductPage.process?Product_Id=179211"), it's $40 and it works fine.
But I'm also on a desktop... I wouldn't want that thing sticking out the side of my laptop.

What kind of laptop is it? Maybe someone has a fix?

---

### Post by whoopsbob on 2009-09-15
> **Genius314 said:**
> I use this thing: [link]("http://www.belkin.com/IWCatProductPage.process?Product_Id=179211"), it's $40 and it works fine.
But I'm also on a desktop... I wouldn't want that thing sticking out the side of my laptop.

What kind of laptop is it? Maybe someone has a fix?

The wireless card is a Realtex rtl8192se. I've done some research on-line and I'm pretty sure there's no solution right now, especially for 64 bit.

And honestly I'd rather spend $40 for something that just works than to spend 5 hours mucking around with modprobe and ndiswrapper and all that crap

---

### Post by Lupgaru on 2009-09-15
> **whoopsbob said:**
> I wasn't careful enough when buying my most recent laptop and I've got an unsupported wireless card, so I want to buy a USB adapter. Anyone got recommendations for something that'll just plug and play on most distros, and is cheap and well built? I know there are lists out of there of what's compatible with Linux, but that doesn't mean it's a good buy

You could try this  [http://www.amazon.com/Linksys-WUSB54GC-Compact-Wireless-G-Adapter/dp/B000CRFI8A](http://www.amazon.com/Linksys-WUSB54GC-Compact-Wireless-G-Adapter/dp/B000CRFI8A)

I have 2 of them and I distro hop quite a bit. They do well on laptops and desktops, and also  come with a 6' extention. Must be installed in windows but just plug and play in Linux (Ubuntu, Mandriva, Mepis, DSL, Knoppix, Puppy to name a few)

Good Luck.

P.S. Make sure your wireless card is disabled on your laptop to avoid conflicts. Make sure the model # is WUSB54GC, others will not work.

---

### Post by Cuba71 on 2009-09-15
For less than $15 you could get a Belkin F5D7050 or a D-Link DWL-G122 that work out of the box on Jaunty or Karmic (I own both and have tested them).
They both use the rt73usb driver.

They are as cheap as they can get, but I don't know if they'd fit your rquirements.

---

### Post by slowtrain on 2009-11-04
Hi Cuba71:  I spent 2 days trying to get a Belkin F5D7050 to work.  The problem is that I got a Belkin F5D7050 v4000, for which I was unable to find any working driver (yeah, I tried the community page for exactly this model--can no longer download the driver source).  So, if you get a Belkin F5D7050, get a v3000, which has a supported chipset.  Not sure how you'll be able to tell which version you're getting, because it doesn't seem listed on the box or by many vendors.

---

### Post by jivabill on 2010-03-15
Well, I don't want to rain on everyone's parade but if you look thru the threads on the networking forum here you will see a long litany of problems and troubles with the Linksys WUSB54GC USB adapter.

I just spent for the second time in a couple months a couple hours reading and digesting the situation.  What I found is that there is no very good remedy other than ones that take three pages single spaced of command line magic and may or may not work in the end.

I have a WUSB54GC myself and have tried different things to get it to work on my HP Laptop that is running 8.04LTS.  I even tried WIFI Radar out of the repository, which is by the way, several versions back from the latest current stable version of WIFI Radar and for that reason has no support.

One post I found stated that WIFI Radar would make the USB Adapter work.  If you turned off the Network Manager applet.  That may be but I as yet have not had much success and my install of WIFI Radar lacked the connect button on the GUI.  For reasons as yet unknown.

My take on this issue, the use of USB WIFI Adapters in Ubuntu, is that the nicest thing to say is it is an area that is just not working yet.

By way of contrast, I have a friend who has a netbook with XP Pro on it.  I plugged my WUSB54GC into a USB port on his netbook, it discovered the Adapter, downloaded all the software, installed it AND started working flawlessly in under 5 minutes.

Until Ubuntu produces those type of results with simple hardware items like USB Adapters, the market penetration of Ubuntu will remain marginal.  Certainly is too bad.  

Anyway, that's my two cents.  I have another laptop a Dell C610 with XP Pro on it, I'll use my Adapter there installed in a parabolic reflector antenna that I built to enhance its performance.

---

