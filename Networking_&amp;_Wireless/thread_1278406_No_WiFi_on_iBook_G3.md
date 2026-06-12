---
title: "No WiFi on iBook G3"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by BothEyesShut on 2009-09-29
Hello Everyone,

I've searched and searched for different solutions to this problem, but everything I've tried comes up nil.  

The story is, I'm a teacher trying to get a colleague's old iBook G3 running Jaunty, and I'm pleased with myself in getting the screen resolution right as well as everything else -- except the WiFi, which just won't work no matter what I do.  Wired networking works fine, though.

I've installed Wicd Manager, and I can see my available networks, but the signal strengths show at "-1%", and connecting to the network using WPA Encryption with a passphrase hangs at "Validating authentication" and never connects.

I'm tearing my hair out, gentlemen.  I know nobody wants to deal with such an old lappy, but I've got to and I'm so very close to a perfect Linux system!

Thanks in advance,

Sean

---

### Post by jml on 2009-09-29
First, this may be a stupid question, but do you know that the wireless card actually works?  Was it able to connect to wireless networks with the original Mac OS installed?  Not just view networks, but actually connect.

Second, can you connect to an unencrypted wireless network?

Third, the low signal strength makes me suspect a problem with the connection to the antenna.  If I remember correctly, the early Airport card had a "pigtail" connecting the card to the antenna.  If that came loose, it might exlpain your problem.

Hopefully someone else will have some ideas for you as well.  Good luck.

Joe

---

### Post by BothEyesShut on 2009-09-29
Ah, good questions, of course.

The card was able to connect under the old OS last week.  I don't have any unencrypted sources to try to connect to, but I'm certain the PW is correct, as my newer lappy is using it now.  

I think it's a driver issue, but the forums are fairly bleak -- many say that WiFi on a G3 is not supported under Ubuntu.  I keep trying to put different drivers in via USB, but many of the terminal commands don't work.   I'm kindof running in circles.  At this point, I'm wondering if maybe I ought not just get an old distro and try it, instead. . .  Or Kubuntu, but my colleague is much less savvy than I am and may be put off by anything less user-friendly than Ubuntu.

Any thoughts?

Thanks again for such a quick response :)

-Sean

[EDIT] I just rebooted, and to my complete lack of surprise it seems that I've screwed with the configs enough to keep Jaunty from booting now, so my next move will be to reinstall.  Any advice on what distro I should use?

---

