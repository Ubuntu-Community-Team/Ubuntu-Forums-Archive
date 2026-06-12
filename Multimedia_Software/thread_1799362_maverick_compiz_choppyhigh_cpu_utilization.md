---
title: "maverick compiz choppy/high cpu utilization"
date: 2011-07-07
forum: Multimedia Software
---

### Post by mixmastamyk on 2011-07-07
Hi all,

Been using Maverick on my Dell Studio XPS for many months without issue.  

About a week or two ago, compiz has been acting funny and using a lot of cpu time, making everything "choppy," especially after resuming from suspend.

I've googled and searched the forum, but all the related posts seem to be several years old.

I tried selecting the previous kernel but it didn't help.  Was there a bad update to compiz or ati graphics?

My info:
```

> lspci | grep VGA
21:02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]

> grep -i driver /etc/X11/xorg.conf | uniq
	Option	    "VendorName" "ATI Proprietary Driver"
	Driver      "fglrx"

> glxinfo | grep direct
direct rendering: Yes

> dpkg -l compiz | grep ii
6:ii  compiz     1:0.8.6-0ubuntu9.2       

```

To get things back to normal I have to do this:

```

> compiz --replace &
> killall gnome-panel

```

---

### Post by beew on 2011-07-07
Did you enable the transparent desktop?

---

### Post by mixmastamyk on 2011-07-07
Not entirely sure what you are referring to.  I looked thru compiz settings and did not find anything by that description.

I have some of the effects on, but not too fancy.  Desktop has one of the standard images (brown/grey rocks getting thrown).  Terminal has true transparency on.

It works fine for many mins and after I restart compiz, so I don't think the machine is overtaxed.  Seems like a bug that degrades performance over time.

---

### Post by modal1 on 2011-07-14
I was having a similar issue with Fedora running Compiz with lots of stuff enabled but with a nVidia card. 

In the Compiz Settings Manager under Utility, enable Error Notifications and set the Hide Timeout to zero or 10 sec....something other than -1. 

I repeatedly received the following error:
"animation settings mismatch in animation selection list"

So I opened Effects/Animations and reset everything to defaults (the button with the paintbrush) and the errors went away. 

I am still getting an occasional CPU spike but not as many and not nearly as crippling to the system.

Hope that helps.

---

