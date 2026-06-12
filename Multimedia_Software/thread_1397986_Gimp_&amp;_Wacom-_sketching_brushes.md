---
title: "Gimp &amp; Wacom- sketching brushes"
date: 2010-02-03
forum: Multimedia Software
---

### Post by chisle on 2010-02-03
I have been recently using the GIMP, transferring from adobe photoshop. and the truth is i have been pleasantly surprised with GIMP, especially when comparing prices from the two. Anyway the one thing i have not been able to do, that i assume is possible is make a brush that i am able to sketch with with my wacom tablet. what i mean by this is in adobe i was able to create a brush that would react affectively to the pressure senstivity and i would get nice realistic looking sketches that looked like pencil sketches. when i barley pressed on my tablet i would be light and when i pressed hard i was able to get the black line needed. i have messed around with the pressure settings on the brushes but havent noticed any difference when i press hard on my tablet or barely press at all. any help or perhaps pre made brushes for this purpose would be appreciated. thanks in advanced.

---

### Post by Favux on 2010-02-04
Hi chisle,

If your Wacom tablet supports pressure you should be able to get pressure in Gimp.  Maybe you haven't configured the extended input devices in Gimp?  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

What release of Ubuntu are you using?  Which Wacom tablet do you have?

---

### Post by chisle on 2010-02-04
i have the intous 3 and i am using Karmic right now

---

### Post by Favux on 2010-02-04
Hi chisle,

Did the Wacom wiki help any?  Or still no pressure?

If no pressure let's look at your output of this command in a terminal:
```
xinput --list
```

---

### Post by chisle on 2010-02-04
thanks. you wewre right. just needed to go into the preferences. thanks again, every where i was reading never mentioned that. i thought i was going to have to go into the xorg file and everything.

---

### Post by chisle on 2010-02-05
one last thing, would you happen to know how i can keep my preferences for my wacom tablet so when i restart my computer the settings save

---

### Post by Favux on 2010-02-05
Hi chisle,

Sure, you need to set up wacomcpl's (Wacom Control Panel) .xinitrc file so it starts when you start X.  But depending on your .fdi you may need to rename things or change your .fdi, depending on how you want to handle things.

See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") for more explanation and alternate .fdi's.  It will link to Section 3 on setting up wacomcpl.

---

### Post by chisle on 2010-02-05
just read your tutorial on how to save your calibration settings. great stuff. thanks been a great help!

---

### Post by benmoran on 2010-02-05
If you're new to using Gimp, I recommend episode 66 from the "Meet the Gimp" videocast. It covers all the settings, including tablet settings. You might want to give it a watch in case you're still not clear on something. 

[http://meetthegimp.org/episode-066-setting-up-gimp-26-and-looking-into-the-future/]("http://meetthegimp.org/episode-066-setting-up-gimp-26-and-looking-into-the-future/")

---

