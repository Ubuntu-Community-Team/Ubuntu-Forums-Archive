---
title: "[SOLVED] Mythbuntu control centre problem"
date: 2007-10-15
forum: Mythbuntu
---

### Post by fatbastard spice on 2007-10-15
Just installed gutsy on an AMD64 box and trying to get myth installed using mythbuntu control centre. Problem i'm having is that whenever i try to add the roles i get a broken packages message

E:Unable to correct problems, you have held broken packages

There's no problems with apt updates or upgrades, though the update does throw up quite a few ignores as it's looking for translations that don't exist. Would the translations be confusing the control centre?

---

### Post by govee on 2007-10-15
I have a similar problem. I loaded AMD64 RC and all was fine. I configured MYth and I could watch TV. I ran update manager and it says lots of files to upgrade. I say ok and downloaded and updated, restarted. At that point I notice that it loads directly to Desktop not Myth and I try to open Myth Frontend and it has been removed from the menu (Backend has been removed as well). I still have the Control Center. I select it and then select Primary Front and Backends and Apply. I then get the held broken packages failure. 

Looks as though another reload is in order.

---

### Post by superm1 on 2007-10-15
It sounds to me like both of you guys performed apt updates before they were synced completely to your mirror.

There was a last mythtv update yesterday, that adds logging functionality to the frontend.  

Try to reload your package lists and make changes once more.

---

### Post by govee on 2007-10-15
will do

---

### Post by govee on 2007-10-15
I hate to sound like the Newb that I am, but are u saying if the update manger says partial update I should stop and not upgrade till the full is available?

---

### Post by superm1 on 2007-10-15
> **govee said:**
> I hate to sound like the Newb that I am, but are u saying if the update manger says partial update I should stop and not upgrade till the full is available?
Yup, things have gone astray likely for this exact reason.  

You can hit the button to reload the package lists in there and see if your mirror is synced up now.  

You may have to actually do an apt-get dist-upgrade from the command line however, depending on why it won't upgrade right now.  Be wary of any packages it asks to remove.  If it wants to remove something, that's a *bad* idea typically :)

---

### Post by govee on 2007-10-15
Ouch! I was blindly saying yes on the "remove" thing. I assumed it was only getting rid of things that were replaced by new.

---

### Post by fatbastard spice on 2007-10-15
Thanks for the replies - yep seems a wait was all that was required. Working fine next morning.

---

