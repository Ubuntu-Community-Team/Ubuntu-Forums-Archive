---
title: "Ubuntu 10.10 CD Hangs"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Nicallen63 on 2010-09-03
I am new to using Ubuntu, i used it a few times in the past but not extensively. I am trying to install it on a separate partition on my mac but im running into a problem right from the get go. When i boot off of the Ubuntu CD and click "Install" or "Try Ubuntu without installing" it just goes to a black screen with an underscore blinking and hangs there. Anyone ever have this happen or know how to fix it? Ive tried it with the 32bit and 64bit versions. I have a macbook Pro(5,3) running OS X and Windows 7, i created two new partitions, one for Ubuntu and one for a swap, dont know if any of that matters at the point im at right now.

---

### Post by CandidMan on 2010-09-03
Hi there,
This is no guarantee, but I had this problem as well maybe for different reasons.

What I did was :
At the CD screen with all of the options, press F6 for other options at the CD boot menu
Select "nomodeset"
Continue with either 'try Ubuntu...' or 'install ubuntu'

Hope this helps

---

### Post by alexmurray on 2010-09-03
I get the same thing on my MacBook Pro 5,1 - you need to enable the 'nomodeset' option - under 'Other Options' by pressing F6 at the livecd boot screen. This is likely a bug in the nouveau driver I think or it fighting for the framebuffer... would be worth filing a bug in launchpad.

(Beaten to the punch by CandidMan it seems)

---

### Post by Nicallen63 on 2010-09-03
Thanks ill give that a shot.

---

### Post by JoyceBabu on 2010-09-04
I was able to install Ubuntu 10.10 in Parallels Desktop without any issues today.

---

### Post by Nicallen63 on 2010-09-04
Another quick question, will i be able to read my music off of my mac side from my Ubuntu partition?

---

### Post by vgrisham on 2010-09-04
Yes, you can access your stuff in OS X. See [this]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid") page for your requirements for your specific model. In order to write to the HFS+ partition, you'll need to disable journaling. In OS X, go to the Disk Utility. Select your Macintosh HD partition. Then hold down Control while clicking the file menu. Select Disable Journaling.

---

### Post by vgrisham on 2010-09-04
CandidMan and alexmurray,

I installed using the 'nomode' option but the new Ubuntu install won't boot. Did you guys encounter this? It's basically giving me [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393") error seen when Lucid was in beta.

---

### Post by Nicallen63 on 2010-09-04
Im getting the same error, i tried [this]("http://ubuntuforums.org/showthread.php?t=1442133&highlight=pramin+flush+timeout") but it didnt seem to do anything.

---

### Post by Nicallen63 on 2010-09-04
Im going to try installing 10.4.1 and see if that is successful. May 10.10 just hates my computer.

---

### Post by vgrisham on 2010-09-04
10.04-1 works really well on my 5,3. Maverick just entered Beta. Ill wait for 10.10-1.

---

### Post by Nicallen63 on 2010-09-04
Everything seems to be working fine with 10.4.1 now, only problem i have is my wireless. It sees my network but doesn't seem to ever actually connect with it, i know the password i put in is correct but it still just constantly sits there trying to connect.

---

### Post by vgrisham on 2010-09-04
Take a look at the wireless section of this guide....

[https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

---

### Post by Sef on 2010-09-04
moved to MMTnD

---

### Post by Nicallen63 on 2010-09-05
> **vgrisham said:**
> Take a look at the wireless section of this guide....

[https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

Doing that was what enabled me to see my wireless network. Still cant connect though. Also i have another problem, my computer screens wont come back on after being suspended. I can hear the hard drives and fans kick back on but the screens just go to a black screen.

---

### Post by cypro66 on 2010-09-10
I have exactly the same on my MBP 5.2 ... Hope that someone has a fix for this,,,,

---

### Post by CandidMan on 2010-09-14
Hi again,
sorry i didn't follow up sooner. Not getting my e-mails about new posts for some reason.
Glad to hear you're at least getting up and running.
Afraid I'd be in over my head troubleshooting wireless connections

Worth posting for a bump at least ):P

---

