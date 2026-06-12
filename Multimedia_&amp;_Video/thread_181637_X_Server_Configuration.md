---
title: "X Server Configuration"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by kerius on 2006-05-24
I'm new to the Linux world.  Wiped my Win. 95 machine and installed Ubunto BB 5.10.  About a week into running it I decided to unstall a new graphics card.  After installation I booted and got a screen that said the following:

**"...failed to start X Server... It is likely not setup correctly..."  **

After viewing the X Server output to diagnostics and the detailed X Server output, it said the following:

**"X Server is now disabled.  Restart GDM when it is configured correctly."**

A login appeared at the command line.  After logging in and entering a password it displayed the following:
[B]
kerry@hyperion: ~$[/B]

Not being familiar with command line driven stuff I thought I would turn to this forum for help.  My IT at work (who turned me on to Linux) said I would have to find a way to configure the X Server so it could look for the new graphics card drivers.  

Any recommendations?

Kerry

---

### Post by johnc4510 on 2006-05-24
What is the graphics card?
Did you install the drivers and if so, which ones?
If you installed the drivers, did you enable them?
Post the answers to these and I will try to help.

---

### Post by kingmonkey on 2006-05-24
type

```

sudo dpkg-reconfigure xserver-xorg

```

This will reconfigure your x server for you.

---

### Post by kerius on 2006-05-24
Thank you,

That's exactly what I was needing.  I'll try it tonight when I get home.  Just one more thing.  Can you help me know what to expect after typing this in.  I assume X Server Config will come up.  Then I'll need to define new graphics card, load drivers???

Thanks in advance,

Kerry

---

