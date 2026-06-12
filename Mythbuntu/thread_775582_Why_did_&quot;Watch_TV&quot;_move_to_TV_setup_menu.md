---
title: "Why did &quot;Watch TV&quot; move to TV setup menu?"
date: 2008-04-30
forum: Mythbuntu
---

### Post by dajt on 2008-04-30
Hi,

I installed Mythbuntu and had it working. I went into the setup menu trying to find a way to make the DVD I'd imported appear under "Watch Videos" and went in and out of a few setup options. I didn't change anything drastic.

Then I found myself starting at the Setup menu whenever the mythtv front end started. I had to hunt around and finally found "Watch TV" hidden away in the TV Setup menu.

I've uninstalled the front end and am reinstalling it now to try and fix this.

Anyone else seen this happen?

Regards,
David.

---

### Post by Titus A Duxass on 2008-04-30
I experienced something similar with an install of 8.04 last weekend.

I lost the live tv menus totally, the first menu was the setup menu.

I simply reinstalled (less than 1 hr start to finish).

---

### Post by dajt on 2008-04-30
Good to know I'm not the only one.

Uninstalling and reinstalling just the front end didn't fix it, so a clean install it is I guess.

This would really annoy me if I had hours of TV recorded and lots of the kid's DVDs imported...

I'm installing off a 7.10 live CD, but perhaps I got the 8.04 stuff via the net. I didn't do any large upgrades because when I did that yesterday my DVB-T card wasn't recognised afterwards!

Update: Before reinstalling everything I decided to try and see where the menu structure is held. Looking at the XML files it seemed okay, but poking around led me to figure out how to run the front end, then I found the options, and when I did:

```
/usr/share/mythtv/mythfrontend.sh -r -v all
```

and then started the front end as usual, I had my normal menus back.

Regards,
David.

---

### Post by pjbgravely on 2009-01-19
Thanks dajt,

   I looked myself but couldn't see the options you recommended. Must be a rare bug because I couldn't find anyone else with a solution. It was a pain running it. I couldn't use it with ssh.

Paul

---

