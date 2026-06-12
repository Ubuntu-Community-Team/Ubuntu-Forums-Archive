---
title: "Scan New Videos 0.22"
date: 2009-11-26
forum: Mythbuntu
---

### Post by nasha on 2009-11-26
Hi Guys,
I've read everywhere that to scan in new videos under 0.22, you enter MythVideo and press the m-key... Doing this returns me to the main menu.

Is there something i'm missing? There seems to be no 'MENU' key binding associated with MythVideo.

regards,
Nasha

---

### Post by neutron68 on 2009-11-26
> **nasha said:**
> Hi Guys,
I've read everywhere that to scan in new videos under 0.22, you enter MythVideo and press the m-key... Doing this returns me to the main menu.

Is there something i'm missing? There seems to be no 'MENU' key binding associated with MythVideo.

regards,
Nasha
It sounds like you are running into the same situation I saw.  
On my system, the MythVideo plugin was not loaded during a default install of Mythbuntu.  
I had to go into the Mythbuntu Control Centre and click on the Plugins tab, and then install the MythVideo plugin.

After doing that, I got the Setup > Media Settings > Video Settings option.
I also got the Watch Videos choice under the Media Library menu choice, and the Scan For Changes message became available with a press of the M key.

Best wishes,
Eric

---

### Post by nasha on 2009-11-27
> This isn't my issue, as MythVideo is installed. Im not using a defaut install of Mythbuntu, i have upgraded from 9.04 + 0.21.

All previous videos work fine, but i am unable to bring up the menu with the M key, it just returns me to the main menu frm MythVideo, hence i am unable to load new video files.

There must be something amiss here?

Nasha

After closer inspection of key bindings, the M key was associated with a global jump-point to jump to the main menu. After removing this key binding, i am able to bring up the menu. Seems the key binding was overriding the menu popup screen.

Regards,
Nasha

---

### Post by neutron68 on 2009-11-27
> **nasha said:**
> After closer inspection of key bindings, the M key was associated with a global jump-point to jump to the main menu. After removing this key binding, i am able to bring up the menu. Seems the key binding was overriding the menu popup screen.

Regards,
Nasha
Where do you view the key bindings?

Thanks.

---

### Post by Neon Dusk on 2009-11-27
> **neutron68 said:**
> Where do you view the key bindings?

Thanks.

If you have mythweb installed you can see them at http://<hostname>/mythweb/settings/mythtv/keys

where <hostname> is the name of the backend.

---

