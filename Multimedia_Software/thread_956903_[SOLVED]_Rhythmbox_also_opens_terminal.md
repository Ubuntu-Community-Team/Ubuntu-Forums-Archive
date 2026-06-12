---
title: "[SOLVED] Rhythmbox also opens terminal"
date: 2008-10-23
forum: Multimedia Software
---

### Post by T-AA on 2008-10-23
Hello,

When i open rhythmbox it also opens a terminal window, when i close this rhythmbox closes aswell.

Is there anyway it stops opening the terminal?

---

### Post by chevy on 2008-10-23
I suspect you have the Python Console plugin enabled.  To see if this is the case, from Rhythmbox select Edit -> Plugins.  Verify if Python Console is enabled.

---

### Post by T-AA on 2008-10-25
Thanks for the suggestion but it didn't do the trick.
I tried with it en and disabled

---

### Post by ad_267 on 2008-10-25
Does this happen if you press Alt-F2 and then enter "rhythmbox"?

---

### Post by T-AA on 2008-10-25
No it does not happen then.
Is there a way i can change the launcher so it doesn't happen then either?

---

### Post by ad_267 on 2008-10-25
So how are you opening it? From the menu or from a desktop launcher? 

If from the menu then you can right click on the menu and select "edit menus" and then right click on the rhythmbox item and select properties to see what command it's running. If it's from the desktop you can do a similar thing by right clicking on the launcher and looking at the command it runs.

---

### Post by T-AA on 2008-10-25
from the menu rhythmbox %M

---

### Post by xc3RnbFO8P on 2008-10-25
Try **rhythmbox %U**

---

### Post by dburnett77 on 2008-10-25
> **T-AA said:**
> Hello,

When i open rhythmbox it also opens a terminal window, when i close this rhythmbox closes aswell.

Is there anyway it stops opening the terminal?

In preferences, on 8.10, I see a selection for "python console".  That might be it.

Menu "Edit...Plugins...Python Console".  Try ticking that.

---

### Post by dburnett77 on 2008-10-25
> **T-AA said:**
> from the menu rhythmbox %M

Try the website, and learn that parameter.  Don't trust these fools...

---

### Post by ad_267 on 2008-10-25
> **dburnett77 said:**
> Try the website, and learn that parameter.  Don't trust these fools...

I'm not quite sure what you're trying to say there. The %U/%F thing is to do with Gnome and the website in question would probably be here: [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

I don't see a %M field listed there, and my launcher uses the %U option, so I think it's safe to try using %U instead. The field could also be removed completely and the command just set to "rhythmbox"

---

### Post by T-AA on 2008-10-26
Sorry for bothering you all.

I must be stupid since i missed this but it hadnothing to do with the %Mor whatever.
In the edit menu there was a dropdown menu type and it had terminal application in it, i just switched it to application.

Thank you all for your suggestions.

---

### Post by bapoumba on 2008-10-26
@ T-AA: in Thread tools, you have the option to mark the thread as solved (just did it for you, responding to your report) :)

---

