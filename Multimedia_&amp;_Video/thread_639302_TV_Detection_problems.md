---
title: "TV Detection problems"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by steenbras on 2007-12-13
I'm not sure if this is a common experience, but as a new convert to Ubuntu (and a new fan) my biggest gripe comes when I plug my laptop running Gutsy into my TV.

There is no autodetection of the TV, and corresponding expansion of the desktop, but I can get it working by configuring Screens and Graphics. But there are 3 things that annoy me:

1. I can't select an L-shaped desktop - ie a higher resolution left-side (laptop) and lower res right-side (TV) like I could in Windoze - both screens appear to have to have the same resolution. If you can, I couldn't get it to work.

2. After detection, a reboot or a restart of XWindows is required

3. When unplugging the TV, I can't easily return to my original desktop configuration. I get stuck in 640 x 480 and am offered no higher resolutions.

I've overcome this by having 2 xorg.conf files - one for standalone and one for dual view, but it's a pain having to swap them around between reboots. I'm posting this for 2 reasons - either I'm being a dunce and there are easier ways to do it, or else perhaps this is something that could be looked at in future releases of Ubuntu?

---

### Post by Chainz on 2007-12-13
I'd like to know how to solve that too... have same problems.

After trying to connect my Kubuntu laptop to TV, I end up in low res and can't even enter resolution configurator since it just crashes when I want to lunch it :(

---

### Post by steenbras on 2008-01-09
For those who do have the same issue, these are my findings:

I don't have autodetection, so when I plug in my TV I need to configure it. HOWEVER, I don't use the standard Gnome System->Administration->Screens and Graphics utility - I use nvidia-settings (you need to sudo).

Then you can click the detect displays icon - you should see a box appear representing your TV. Then click the advanced... button. Again I can't get an L-shaped desktop, but you can choose to have a separate desktop entirely owned by the TV. Save this to your xorg.conf (you must press that button) and exit the utilty.

You then need to restart your x-server - CTRL-ALT-BACKSPACE

Reverse the process when you unplug your TV.

It's not automated, but it takes no more than 10 secs when you've done it a few times.

---

