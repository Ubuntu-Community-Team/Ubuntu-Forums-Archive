---
title: "Interesting problems with Live USB ."
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-09-21
Just been testing this out using the Startup Disk creator from lucid.

Got the daily livecd iso yesterday (20 Sep). Anyway I double checked the known issues and this forum but not found the same problems. I'll bug this issue shortly.

If I let it just boot without interference it goes to the graphic Try or install and I can get to the desktop just fine. Very quick too.

However if I press a key at start up and choose Try Ubuntu it freezes up. Removing quiet and splash shows it stops at "Starting kernel oops catching service kerneloops speech dispatcher disabled edit /etc/default/speechdispatcher". Anyone else get this.

Also if I choose install after pressing a key it goes to the desktop instead with nautilus and zenity crashed. I'll try to reproduce this and send of crash reports from the live usb.

---

### Post by coffeecat on 2010-09-21
> **philinux said:**
> Anyone else get this.

Was it yesterday's daily that you downloaded yesterday? Sorry, sounds like a silly question, but this morning I downloaded the daily ISO dated 20-Sep-2010 08:11 - the maverick-desktop-amd64.iso image - yesterday's ISO which is the latest available as I post. I used Startup Disk Creator but in Maverick to make a live USB. It worked just fine. I tapped the space bar at startup to get the menu and it booted from Try Ubuntu without problem. I even used it to make a fresh installation which I'm posting from now.

---

### Post by philinux on 2010-09-21
> **coffeecat said:**
> Was it yesterday's daily that you downloaded yesterday? .

Yes. Daily from 20th Sep. Downloaded yesterday. Testing with it today lol.

---

### Post by xebian on 2010-09-21
Since there is now a brand new 9/21 why waste your time on 9/20?

---

### Post by coffeecat on 2010-09-21
> **xebian said:**
> Since there is now a brand new 9/21 why waste your time on 9/20?

Probably because that wasn't available [here](http://cdimage.ubuntu.com/daily-live/current/) less than an hour ago.

---

### Post by philinux on 2010-09-21
> **coffeecat said:**
> Probably because that wasn't available [here](http://cdimage.ubuntu.com/daily-live/current/) less than an hour ago.

+1 lol. I'm just zsyncing now.

---

### Post by philinux on 2010-09-21
Still hangs at the same point with 21 Sept Daily.

---

### Post by coffeecat on 2010-09-21
> **philinux said:**
> Still hangs at the same point with 21 Sept Daily.

I'll dl the 21st Sept ISO and let you know how I get on. Might be a couple of hours though.

---

### Post by coffeecat on 2010-09-21
No. The 21st Sept daily works fine for me. I've tried it on my main desktop and on a Sony Intel graphics laptop and Acer ATI graphics laptop and it boots up fine on all three. I'm posting from the live USB session on the Acer atm. I removed quiet and splash when booting up on the desktop, but I couldn't see any errors.

I'm using the AMD64 desktop ISO. Are you using the 32 or 64-bit? Also, I hate to ask this of an experienced user, but have you tried the USB on any other hardware?

---

### Post by philinux on 2010-09-21
> **coffeecat said:**
> No. The 21st Sept daily works fine for me. I've tried it on my main desktop and on a Sony Intel graphics laptop and Acer ATI graphics laptop and it boots up fine on all three. I'm posting from the live USB session on the Acer atm. I removed quiet and splash when booting up on the desktop, but I couldn't see any errors.

I'm using the AMD64 desktop ISO. Are you using the 32 or 64-bit? Also, I hate to ask this of an experienced user, but have you tried the USB on any other hardware?

64 bit. I have no other machine that can boot via USB. I've also never used a live usb so thats why I'm testing plus learning something new.
Dang bios keeps reverting to boot from HD first too. I've raised a bug. Like I said it only hangs if you choose the press a key option to get the old menu.

The other thing re the install has now gone away.

---

### Post by VMC on 2010-09-21
How are you creating your LiveUSB. Are your using "Startup Disk Creator"? 

I tried the same scenario you used on an AMD64 and it works fine.

---

### Post by philinux on 2010-09-21
> **VMC said:**
> How are you creating your LiveUSB. Are your using "Startup Disk Creator"? 

I tried the same scenario you used on an AMD64 and it works fine.

Yep Startup Disk Creator in Lucid with no persistence as is recommended in the known issues. It boots fine if I keep my paws of until the Try or Install graphic.

---

