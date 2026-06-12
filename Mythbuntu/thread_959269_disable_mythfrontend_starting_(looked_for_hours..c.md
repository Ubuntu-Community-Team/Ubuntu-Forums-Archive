---
title: "disable mythfrontend starting (looked for hours..cant stop it!)"
date: 2008-10-26
forum: Mythbuntu
---

### Post by zeltak on 2008-10-26
Hi guys

Ive installed xbmc and would want to keep only mythbackend as my PVR. I disabled (even deleted) mythfrontend from the autostart (in .config folder) but no matter what i do it mythfrontend starts on login. ive looked for a solution for hours..can anyone help?

thx in advance

Zeltak

---

### Post by zeltak on 2008-10-30
Hi

does no one know the soution (devs etc..?) im sorry to bring it up again but i cant use my HTPC since mythfrontend screws up xbmc and the remotes...please can anyone give me a direction?

thx

Zeltak

---

### Post by SiHa on 2008-10-30
Would a re-install be too painful?

---

### Post by zeltak on 2008-10-30
Hi 

thx for the answer. i really dont think a re-install is necessary. everything works well. i just dont want mythfrontend to autostart thats all

thx , i would love to hear any suggestions 

zeltak

---

### Post by Monsieur Gonzalez on 2008-10-30
Hi,
I've gone the same way. XBMC is quite ahead of Mythtv except for the PVR capabilities. 

To disable autostart of Mythfrontend, just go to Applications->Settings->Settings Manager->Autostarted Apps and uncheck MythTV Frontend. You might also want to add XBMC so that it autostarts on login.

---

### Post by klc5555 on 2008-10-30
> **zeltak said:**
> Hi

does no one know the soution (devs etc..?) im sorry to bring it up again but i cant use my HTPC since mythfrontend screws up xbmc and the remotes...please can anyone give me a direction?

thx

Zeltak


Not elegant, but how about using a terminal, finding the "mythfrontend" executable, and renaming, i.e. "mythfrontend.bak". If the mystery script can't find mythfrontend, it can't execute it, and then at least you should get error message in mythfrontend.log to help track down the offending script and edit it directly.

---

### Post by zeltak on 2008-10-30
Hi guys and thx for the answers!

I did of course try to disable and even delete the Applications->Settings->Settings Manager->Autostart option but it still comes up.

klc5555, i guess i could do that but i do want to run mythfrondend sometimes manually to edit/delete records so i dont want to mess with the scrips or remove it completely, just not have it pop at at bootup

thx again

Zeltak

---

### Post by klc5555 on 2008-10-30
> **zeltak said:**
> Hi guys and thx for the answers!

I did of course try to disable and even delete the Applications->Settings->Settings Manager->Autostart option but it still comes up.

klc5555, i guess i could do that but i do want to run mythfrondend sometimes manually to edit/delete records so i dont want to mess with the scrips or remove it completely, just not have it pop at at bootup

thx again

Zeltak


Renaming the executable should do that for you. Then, on the odd occasion that you need to run mythfrontend, now renamed to, say, "mythfrontend.bak" (but still in its same location in the directory path), you simply open a terminal on the desktop and issue the command "mythfrontend.bak" and mythfrontend launches. Easy.

Once mythfrontend is running, either automatically or as an ordinary user application, the executable itself is not invoked again by the backend or by the OS, as far as I know. It's an independent application.

Should some odd unforseen difficulty appear, mythfrontend.bak can always be renamed back to "mythfrontend" and you're back to where you started.

---

