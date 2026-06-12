---
title: "ATI Video Card Drivers."
date: 2013-03-23
forum: Multimedia Software
---

### Post by edtrud on 2013-03-23
Hello, I am fairly new to Ubuntu, and im having a couple problems getting Ubuntu working. Ive searched the forums and found sound links to the ati video card drivers. (Catalyst) and I cant seem to install it. Everytime I open it is opens a text editor or something of that sort, but it freezes.

---

### Post by QIII on 2013-03-23
*Moved to **Mulitmedia & Video***



Hello and welcome!

Can you tell us a little about the specs of your machine and how you installed the driver?

I'm not convinced that what you are seeing is a video driver issue, but we'll start there.


QIII

---

### Post by edtrud on 2013-03-23
6GB Ram,Core 2 Duo @ 2.8ghz ,ATI Radeon 4800 HD 1GB Video Card

---

### Post by QIII on 2013-03-23
And which version of Ubuntu?

---

### Post by edtrud on 2013-03-23
Newest. 12.10

---

### Post by QIII on 2013-03-23
Well, unfortunately, that would be the problem.

AMD/ATI placed everything earlier than HD 5xxx series codes in a legacy driver branch.  Unfortunately, that driver will only work with X Server 1.12.  

12.10 uses X Server 1.13.

You have three choices:

1.  Use the open source Radeon driver installed by default.  It will be entirely sufficient for the needs of the vast majority of users.
2.  Install 12.04, which uses X Server 1.12.  It's an LTS (Long Term Support) that will be supported until 2017.
3.  Find one of many guides that tell you how to downgrade X Server to 1.12, patch your kernel and use a dead-end legacy driver.

I recommend so strongly against the last that I won't even suggest where to find out how to do that.  The problem is that with a system so patched, it is impossible to predict what may happen in the future if you try to update or upgrade.

If you are interested in that route, I'm sure someone will come along with a suggestion.

I'm sorry to bear such news.  ATI made a business decision based on their cost/benefit analyses and we came up short.

(You could buy a newer card, but that's money and I won't tell you how to spend that!  ;)  )

---

### Post by edtrud on 2013-03-23
I see, Well When installing Ubuntu I pressed on an option button in the top right hand corner bar that Said High resolution, and the screen turned big. And all My Windows are large, even if the icons for the menu are small. I checked my Resolution for the display and its at 1024:768

---

### Post by edtrud on 2013-03-23
Didnt work out, Found a link with a driver, but didnt work and screwed up my resolution for Ubuntu. Ended up downgrading versiona and completely re-installing it. got 12.04

What Driver Do i get now?

---

