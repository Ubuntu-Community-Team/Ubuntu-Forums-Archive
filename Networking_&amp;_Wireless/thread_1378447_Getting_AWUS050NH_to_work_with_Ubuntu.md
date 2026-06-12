---
title: "Getting AWUS050NH to work with Ubuntu"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Curran.michael on 2010-01-11
I've recently purchased an Alfa AWUS050NH and I am attempting to use it with Ubuntu.  The device is recognized by Ubuntu when plugged in and can detect APs.  However when attempting to connect, it only spins the connection icon for a while and then disconnects.

Does anyone one know if there is a way to use this device at full strength with Ubuntu?

I specify full strength because it is possible to rmmod the rt2800usb driver that it loads by default and use the rt2780sta instead, but the device can barely connect to an AP 20 feet away then.

---

### Post by feedmecereal on 2010-02-09
Did you ever get this working? I just bought one of these by mistake and I'm pretty desperate to connect to my new apartment's WiFi.

---

### Post by Curran.michael on 2010-02-09
Nope still not working at full strength.  Using the fallback drivers is a poor solution, but I haven't really benchmarked it.  I tried to sign up for an account at serialmonkey where they maintain the RT drivers, but it's been weeks with no reply to my sign up request.

It's kind of odd to see a hardware vendor take all the right steps, but the community just kind of fall flat on this one.  Heck, I'd throw $20 in a pot to get it fixed...

---

### Post by feedmecereal on 2010-02-09
Even if it doesn't work well, how do I get the rt2780sta drivers at least barely working?

---

### Post by Curran.michael on 2010-02-10
The easiest way is to blacklist the default driver, see here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7967762](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7967762)

---

### Post by feedmecereal on 2010-02-10
> **Curran.michael said:**
> The easiest way is to blacklist the default driver, see here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7967762](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7967762)

**YAYYYY!!!** I got it working!\\:D/

It seems to work just fine now even though I've only been using it for a few minutes.

---

### Post by ww2 on 2010-03-27
I'm considering to purchase this device. Does anyone else have feedback on its signal strenght with the rt2780sta drivers?

---

### Post by feedmecereal on 2010-03-27
I usually get around 80-100% but I have to point out that I'm not exactly sure where the antennas are at my apartment building. One downside is that it doesn't seem to work with the live CD/USB by default. Other than that I haven't had any problems.

---

### Post by ww2 on 2010-03-28
Interesting. What transfer speed (..., 150 mbps, 300 mpbs) do you usually get?

---

### Post by feedmecereal on 2010-03-28
I'm really not sure of the maximum transfer speeds because I only use it to connect to my apartment's WiFi. I'm also not really an expert with wireless.

Edit: My apartment's internet connection seems to max out at 1.5 Mbit/s and it reaches that most of the time.

---

