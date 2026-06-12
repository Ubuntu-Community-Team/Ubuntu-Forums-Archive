---
title: "About to give up on wireless"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by twally on 2009-08-08
I've got about 20 hours involved in this one, and I'm done trying.  I have my setup and what I've tried so far.  If you can figure it out, you're better than me.

It's sad because my wireless worked fine for 2 months until about 4 days ago.

Dell XPS 1330
Hardy 8.04
Intel Corporation PRO/Wireless 3945ABG


Yes, I've installed the Hardy backports
Yes, I've installed wicd
Yes, I've tried booting to an older kernel (2.6.24-16-generic vs. 2.6.24-24-generic)
Yes, I've checked the logs in my router to verify that a connection attempt was made.
Yes, the wireless is up... ifconfig wlan0 up

Yes, I've played with /etc/network/interfaces
Yes, I've tried sudo iwconfig (using hex and s:ascii_key)
Yes, I can get a connection with wireless security disabled (not acceptable)
Yes, I've rebooted a million times.

The only progress I made was that the backports improved iwlist scan functionality... I can consistently see the same networks, including mine.

The newer kernel wouldn't except my key when using iwconfig wlan0 key s:ascii_key

Considering the router logs indicate that an attempt was made to connect, my best guess is that the key is not getting to the router in a proper manner.  I know it's the right key because I can access the router admin interface and see it.

I'm not about to give up on ubuntu, but it would be nice if the laptop could find wireless networks like Windows XP and Vista (out of the box)

Thanks for any help anyone can provide.

twally

---

### Post by Soley on 2009-08-08
I don't know about all Dell's, but I know my wife's dell's wifi worked out of the box with Jaunty. Unless you have your heart set on using Hardy, I would do a dist-upgrade & see how that goes.

But that's just me. I always had a horrible time getting wifi to work in previous versions of Ubuntu. I also tried an old USB dongle I had lying around on my computer just to see if it would work. It did. It just seems to work with 9.04.

---

### Post by starcannon on 2009-08-08
Something is way wrong, I run 8.04 and 8.10 on laptops, and the  Intel Corporation PRO/Wireless 3945ABG chipset is my chipset of choice because it just works, I have to do nothing to get wifi going.

Have you tried turning the wifi off, waiting 30 seconds, and turning it back on (with the switch or hotkey)?

I would help you, but I honestly would not know how to troubleshoot  Intel Corporation PRO/Wireless 3945ABG chipset, as I have never had to do anything except put in my wifi username and password through the GUI, just clicked on my network up pops the uname and pword field, and I'm connected; I use WPA, but I've also used some of the wierd stuff at college with same ease.

I have 6 different laptops with this chipset in them, 2 of them are Dells.

---

### Post by twally on 2009-08-08
Soley, thanks for the recommendation on upgrading to jaunty.  I had that in the back of my mind as the last resort, but was resisting since it seemed overkill, but it worked.  I guess I just needed one person with the same hardware to tell me that's what worked for them to do it.  I'm on the wifi connection now after the default jaunty setup (out of the box)


the power of community to the rescue.... thanks again

---

