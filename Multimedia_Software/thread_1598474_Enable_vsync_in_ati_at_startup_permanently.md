---
title: "Enable vsync in ati at startup permanently"
date: 2010-10-16
forum: Multimedia Software
---

### Post by dnyal on 2010-10-16
Hi y'all.
Thanks in advanced for any reply. Here's the problem.
I've got an ati 4330 in a Dell 1464 laptop. I just installed Ubuntu 10.10 64 bits. It didn't enable compiz by default, so I downloaded the proprietary drivers (fglrx) using synaptic. After that I got compiz working, but... I get this window tearing. I don't know how to explain it, it's something like this:
This is a regular window with open source ati driver (0's are windows, ignore the dashes)
00000000000000000---------------00000000000000000
00000000000000000---------------00000000000000000
00000000000000000--------->----00000000000000000
00000000000000000--------->----00000000000000000
00000000000000000--------->----00000000000000000
00000000000000000---------------00000000000000000
00000000000000000---------------00000000000000000
If I move the window horizontally, it keeps its shape. This is what happens using the proprietary ati driver:
00000000000000000--------------00000000000000000
00000000000000000--------------00000000000000000
00000000000000000-------->-------00000000000000000
00000000000000000-------->-------00000000000000000
00000000000000000-------->-------00000000000000000
00000000000000000-------------------00000000000000000
00000000000000000-------------------00000000000000000
The window kind of tears, and the torn parts are laggy This only happens when moving, and it's really annoying. 

So, I did some googling and found a solution: set "wait for vertical refresh" in ati catalyst at "always on" (the other 3D settings are already set at max). It works, till I reboot. Then the windows go laggy again. I go to ati catalyst and, surprisingly the wait for vertical refresh **is at always on**. But if I change it to any other option and put it back to "always on", then "apply" and "ok", it goes back to normal. 

I've tried: disabling catalyst AI, sync-vsync=on, and sync to vertical refresh rate in compizconfig. None of this works to keep the "always on" really in "on" after reboot.
I don't want to go to catalyst every time I boot to get rid of that windows tearing. I'd appreciate any solution to permanently keep the vsync on at startup.
Thanks.

---

### Post by debili on 2010-10-28
did you get it to work? I mean, does it stay the same after a reboot? i have the same issue...

---

### Post by dnyal on 2010-11-01
> **debili said:**
> did you get it to work? I mean, does it stay the same after a reboot? i have the same issue...

No, I'm sorry. Apparantly no one has any idea about this. The only "solution" I figured out was to put a ATI Catalyst icon on the desktop so everytime I log in to my account I go right away to Catalyst to solve the tearing. I really tried to fix that, but haven't found anything yet. I've got everything updated, still doesn't work.

---

### Post by snakesqzns on 2010-11-03
I have the same issue.  I haven't tried this yet but maybe you could try setting VSync using aticonfig with options like --set-pcs* and --sync-vsync at login?  --set-pcs would require root access though...

---

### Post by CarpKing on 2010-11-03
Last I heard window tearing was unavoidable with fglrx and Compiz.  You may be noticing an improvement.

---

### Post by dnyal on 2010-11-11
> **snakesqzns said:**
> I have the same issue.  I haven't tried this yet but maybe you could try setting VSync using aticonfig with options like --set-pcs* and --sync-vsync at login?  --set-pcs would require root access though...

I tried those commands, still the same. I checked the ati config file in X11 to see if the command --sync-vsync was there for start-up, and it is. So, I think the problem must be "inside" the driver. I hope ADM adds some fix in newer versions of this driver. I haven't tried the --set-pcs command 'cause I don't know how it works. I'll google around about it.

---

### Post by ram0s on 2010-11-30
Same problem here, this is very annoying. I've been googling around for a solution to this but it seems theres no way of making it work after reboot.
Wouldn't some kind of script, running on startup, work around the issue? The commands from aticonfig all depend on a reboot. If there was a way to make some startup script with the "deactivate vsync / reactivate vsync always on" and then reboot the graphical sub-system, it could be done, I think. There would be some expected screen flickering while logging in (like if you changed resolutions), but it is a minor drawback compared to having to deactivate vsync and then reactivate it again manually, every time ubuntu starts.
Any news on your end?

Cheers. ^^

---

### Post by 5oak on 2010-12-15
Same annoyance here. I have to enable "sync to v-blank" every reboot if I want to watch video w/out tearing...

Would LOVE a workaround!

---

### Post by gianvito on 2010-12-17
Same problem here with a Mobility HD3650... if someone has a solution it would be appreciated..

---

### Post by Ko$ on 2010-12-20
+1

VAIO/Radeon 5470

---

### Post by Klump on 2010-12-26
Same here, 5700, no open source drivers available.

---

### Post by yourwhiteshadow on 2011-03-21
+1

the funny thing is that when i want to watch something, i'll just go watch it in XBMC and for some reason the tearing goes away...don't know exactly how that works...

---

### Post by gianvito on 2011-03-21
The problem has been solved in the new AMD drivers... it's possible to enable the "tear free desktop" in the control panel and everything works ok ;)

---

### Post by Milamber_Cubed on 2011-03-21
> **gianvito said:**
> The problem has been solved in the new AMD drivers... it's possible to enable the "tear free desktop" in the control panel and everything works ok ;)

Indeedy. See here:

[http://ubuntuforums.org/showthread.php?t=1708208&highlight=ati+tear+free](http://ubuntuforums.org/showthread.php?t=1708208&highlight=ati+tear+free)

---

### Post by Klump on 2011-03-21
> **gianvito said:**
> The problem has been solved in the new AMD drivers... it's possible to enable the "tear free desktop" in the control panel and everything works ok ;)

Yes, that works :)

---

### Post by dnyal on 2011-05-04
Thanks for your answers. I'll try that solution on 11.04 and let you know. So far, the latest ATI driver is 11.3 and that tear-free option seems to exist since 11.1. I'm gonna wait till 11.4 hoping there'll be some improvement.

---

### Post by Yellow Pasque on 2011-05-04
11.4 is already out.

---

