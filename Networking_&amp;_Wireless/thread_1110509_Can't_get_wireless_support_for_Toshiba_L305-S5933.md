---
title: "Can't get wireless support for Toshiba L305-S5933"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by DGeeez on 2009-03-29
I am having problems connecting to my wireless router through my laptop in all flavors of Ubuntu. I'm a linux newbie who has downloaded about a dozen or so distros, in search of one which works well on my brand-new laptop (Toshiba L305-S5933). I'm getting problems from all of them which I didn't have under Windows on that machine (comparable resource wastefulness not among them), but there were a few which didn't fail to immediately detect my wireless connection. which is critical for my laptop. I'm a newbie, so I don't mean to be haughty about this, but DreamLinux (which can't accept my phone card when it's plugged in) does immediately detect my network named "linksys", plus the neighbor's networks, too. My laptop has a wireless switch, which I made sure was on.  Furthermore, Ubuntu is stepping on my attempts to manually add that network, which it failed to recognize from the start. Here is what happened with the Ubuntu 8.1 (GNOME) cd: 

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

Oh, one more thing - under the "Editing Auto etho" window, the "Connect automatically" option was checked, therefore I don't see why I'm having this problem. I did this without the cable plugged in, because I never planned to use one on my laptop - it's wireless enabled, and activated for that. I tried it just now with the cable plugged in, but I still couldn't get wireless detection. Well, I am a newbie, and used to seeing wireless, once enabled, showing detection of all detectable networks. Is Ubuntu supposed to be different in that way, or is it really a Toshiba hardware issues (there were some distros which would not load at all on this machine, and Puppy Linux couldn't handle my display screen). Why isn't Ubuntu detecting my linksys network?

---

### Post by s.dalas on 2009-03-30
> I type this into the Connection Name box, but the "OK" button remains disabled.

Yes you have to put connection name and ssid ( the same name ) to enable "ok".

I see you have linksys so type linksys in both fields. if you don't have a password for your connection it will work fine i have linksys too. if you have a password you have to edit the wireless security tab. 
the other settings left them as default.
the wired connection "auto eth0" is automating enable when you put a cable no settings at all.

---

