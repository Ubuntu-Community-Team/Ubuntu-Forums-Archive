---
title: "How to set up wifi and adsl (complete beginner)"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by arminius24 on 2010-05-18
Hi everyone,

I just switched from windows to lucid lynx 10.4, but I am really frustrated because I have no idea about how to set up Internet (both adsl and wifi). I have checked the documentation and browsed for hours but the solutions out there never seem to apply to my case, so I beg for some personalized help on how to set up Internet. The only things I know are how to get to the terminal and that I am on an HP laptop. I beg you if you request information you give me a hand at how to find it, given my inexperienced level. Thanks a lot!

Kind regards from Japan,
Ashley

---

### Post by cariboo on 2010-05-18
A description of your setup would be most helpful. Are these two separate connection issues?

---

### Post by NTHQ on 2010-05-20
What exactly is your problem? I also have an HP laptop and had issues with Wifi.
Check my post on [this thread ]("http://ubuntuforums.org/showthread.php?t=1357525")see if it applies to you.

---

### Post by TheGnomeOfMetal on 2010-05-20
when your using wireless goto the terminal and type in [COLOR=navy]sudo lshw -C network[/COLOR] exactly as it appears. Put in your password. you wont see it being typed so make sure it is right before you press enter. (btw the sudo command allows you to run things temporarily as the root user). after you type your password and hit enter a output should pop up in the terminal which shows your wireless card and either the word CLAIMED,UNCLAIMED,ENABLED, or DISABLED. after you do that, post your wireless card information and which one of the words it said.

---

