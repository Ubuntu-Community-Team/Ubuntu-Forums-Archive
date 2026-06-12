---
title: "Please start supporting Toshiba L305"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by DGeeez on 2009-03-29
I'm still much a newbie to linux, but I spent the last two weekends downloading and burning a dozen or so Linux distros. I could have spent that time learning more about how to do all those things which require the command line, I appreciate why such things are needed and have no gripes about that. Problem is that I need systems which work before I can get down to learning much, and the new laptop doesn't have Windows on it (forgot to defrag the partition before shrinking it, hated Vista anyway, and wouldn't miss it if Ubuntu just worked). My own stupidity aside, it's extremely frustrating to find out that very few Linux distros support wireless service on my Toshiba Satellite L305-S5933, but even more disappointing to find that none of the three Ubuntu flavors which I've tested on live CD are among them. The network menu, next to the speaker (for GNOME), has the "Wired Network" option disabled, and yes, my wireless detection switch is on. My sound has also become unacceptably anemic, but that's consistent with all tested Linux distros, through which I could get any sound at all. I would still use Ubuntu GNOME if it worked - it's a bit on the dull side, but it's much, much easier to get around than anything KDE. Am I missing a key workaround, or is my laptop technology just too new or obscure for Linux?

I would be most grateful for any assistance in resolving my wireless and/or sound problems on this laptop (Toshiba Satellite L305-S5933).

---

### Post by s.dalas on 2009-03-29
for your wireless connection check this out.

[http://ubuntuforums.org/showthread.php?p=6966293#post6966293]("http://ubuntuforums.org/showthread.php?p=6966293#post6966293")

post back for any troubles

---

### Post by Ericyzfr1 on 2009-03-29
Wired Network Option disabled? Mine is grayed out until I connect a cable and connect by itself. 
I think you need to make a list of all the items you want to solve and browsing the forum for answers.
Every distributions handle hardware differently and a lot of settings are applied by default. As long as you were able to install Ubuntu, the hardest part is behind you.

---

### Post by s.dalas on 2009-03-29
> **Ericyzfr1 said:**
> Wired Network Option disabled? Mine is grayed out until I connect a cable and connect by itself.

i think this is what he is trying to say.
and yes being more specific with more information would be helpful for all

---

### Post by DGeeez on 2009-03-29
I am having problems connecting to my wireless router through my laptop with all flavors of Ubuntu. I'm a linux newbie who has downloaded about a dozen or so distros, in search of one which works well on my brand-new laptop (Toshiba L305-S5933). Not to be snotty about it, but they all caused problems which I didn't have under Windows on that machine (comparable resource wastefulness not among them), but a critical problem is that it should be able to find my wireless connection. DreamLinux can't accept my phone card when it's plugged in, but it does detect my network named "linksys", plus the neighbor's networks, too. My laptop has a wireless switch, which I made sure was on.  Furthermore, Ubuntu is stepping on my attempts to manually add that network, which it failed to recognize from the start. Here is what happened with the Ubuntu GNOME cd: 

1. There is a nasty red triangle on my network icon on the top GNOME bar. 

2. A right click of the this icon reveals that "Enable Networking" is checked, good. 

3. A right click on the same icon shows that the "Wired Network" is greyed out, dead. Ok, just now I realized that was not "Wireless Network", which appears in a similar menu of at least one distro I've tested. So it doesn't look like I have any wireless control at this level.

4. On this particular boot from the cd, "Auto echo" is greyed out, too. 

5. The other two options between right-click and left-click lead to the same window, where I go to the "Wireless" tab of "Network Connections and attempt to add "linsys", just as it had appeared when Vista and a few Linux distros were able to detect it. 

6. I type this into the Connection Name box, but the "OK" button remains disabled.

7. The "SSID" box, which I wouldn't know anyway, remains blank.

8.  The "Mode" box defaults to "infrastructure", and I leave it at that.

9. Another box which I know nothing about, "BSSID", is left blank.

10. Ditto with "MAC address".

11. The box for "MTU" defaults to "automatic".

12. The "OK" button remains disabled.

13. I push the "Cancel" button and notice that under the default tab "Wired", is this line "Auto eth0" is set to "never", and although I push the "Edit" button, I see no obvious way of changing this condition through the "Editing..." screen.

Any idea what the cause of this is, if it isn't my hardware? I would be most grateful to anyone who can help.

Thanks.

Oh, one more thing - under the "Editing Auto etho" window, the "Connect automatically" option was checked, therefore I don't see why I'm having this problem. No, I don't have the cable plugged in, because I don't plan to use one on my laptop - it's wireless enabled, and activated for that, so why isn't Ubuntu detecting my linksys network?

---

### Post by DGeeez on 2009-03-29
Sorry about the repeat here, since the title was not specific enough, I just had to see what would happen if I changed it (surprised that I could) instead of start a different thread. If I had the option, I would close this thread, now that I've opened up "Can't get wireless support for Toshiba L305 S5933".

---

### Post by s.dalas on 2009-03-30
> I type this into the Connection Name box, but the "OK" button remains disabled.

Yes you have to put connection name and ssid ( the same name ) to enable "ok".

I see you have linksys so type linksys in both fields. if you don't have a password for your connection it will work fine i have linksys too. if you have a password you have to edit the wireless security tab.
the other settings left them as default.
the wired connection "auto eth0" is automating enable when you put a cable no settings at all.

---

### Post by tiredchris on 2009-04-23
I wouldn't say that wifi support for this machine is unavailable, you just haven't done enough searching. I'm running the exact same machine and it works perfectly for me. I know I didn't find the answer on ubuntuforums so use google, its your best friend. I think the search terms were something allong the lines of   machinetype (linux/ubuntu) not working, or   machine drivers for (linux/ubuntu).

I really can't remember how it worked out, but I think I ended up using a wrapper to use the windows wifi driver.

Keep searching, its out there.

Edit: Found it. Follow the directions at the following link and wifi should work. Did the trick for me.

[https://answers.launchpad.net/ubuntu/+question/66395](https://answers.launchpad.net/ubuntu/+question/66395)

---

### Post by swinky on 2009-05-07
I have a Toshiba Satellite L305-S5891. I'm not sure exactly what the differences are between this one and your model. Do you know what wireless card the L305-S5933 has?

My model is using the Atheros ar5007eg card, which was not supported very well (if at all) in Ubuntu 8.10, but works out of the box in 9.04. I'd recommend trying out the latest version and see if it works for you!

Unfortunately some of the newer Toshiba models are not very Linux friendly, but the newest version of Ubuntu fixes a lot of the problems I was having before.

---

