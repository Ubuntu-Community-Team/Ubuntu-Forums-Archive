---
title: "Firefox 3.6.9pre don't work well in hotmail.com"
date: 2010-07-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-07-31
as you can see in the attached picture but 3.6.8 does work fine why is that?

Thanks in advance.

---

### Post by VMC on 2010-07-31
> **aviramof said:**
> as you can see in the attached picture but 3.6.8 does work fine why is that?

Thanks in advance.

I can't view that format, but if in closing hotmail account and you get the message that hotmail didn't close correctly, I get that no matter what OS or browser I use.

---

### Post by aviramof on 2010-07-31
xcf is a default format of ubuntu of screen files and i can't close my hotmail account i need there live id  because i have mcitp certifications.

---

### Post by 23dornot23d on 2010-08-01
(the xcf file opens ok in Gimp after downloading ..... you would think xcf files would open directly though)


I found something similar to this screen shot ..... when I directly go into Hotmail

But for some strange reason ..... 

**going into HOTMAIL from AMSN .... works ok for me**

and I have just got used to going into it this way .....

But as you say it must be a fault somewhere ....




I always thought before now it was MSN .... that have messed it up .... as I do not get it on any other
mail managers.

---

### Post by bikeboy on 2010-08-01
They've messed up their browser detection with changes to Hotmail. It now thinks you're using a mobile browser. In case it wasn't clear, the problem is a change in Hotmail, not in Firefox.

Use [http://chrispederick.com/work/user-agent-switcher/](http://chrispederick.com/work/user-agent-switcher/) to fool Hotmail into thinking you're using Firefox 3. In fact, just changing your user agent to 3.6.8 might even work, though I haven't tried.

---

### Post by 23dornot23d on 2010-08-01
Cheers for clarifying that ..... it makes sense now ... the screen layout that is .......
that does not explain why it works ok when linked back from aMSN though 

whats the difference - more to the point can the same thing be replicated within firefox. 

As it always works fine if I get aMSN to open my hotmail messages in firefox.

---

### Post by bikeboy on 2010-08-02
Not sure, can't explain the aMSN difference. What I do know is that the same thing just started happening in the Firefox nightlies (what will become 4.0) when it was fine for ages. I suspect the "pre" in the user-agent messes things up on the 3.6.x series.

Using the Net feature of the Firebug extension you *might* be able to find what the difference is.

---

