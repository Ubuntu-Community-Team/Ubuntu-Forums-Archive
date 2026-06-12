---
title: "Unity loading on Classic Desktop"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by encefalocardia on 2011-03-17
New member here.

Recently I just took the plunge and made Ubuntu my main and only system (On a Macbook Pro, funny enough). Im finding the experience great and challenging.

However, after todays unity update (2.6.6 I believe) Unity loads on top the gnome panels on Classic. I can temporaily fix this using metacity --replace. Any way to permanently solve this?

BTW, I have another problem with my Apple Bluetooth Keyboard. It does not get detected at startup and I have to scan for it and then connect it via hidd. Should I open a sepparate thread about this problem? Thanks in advance.

---

### Post by ranch hand on 2011-03-17
One thread per problem makes searching by others with a problem able to find the thread.

I hope that 11.04 is not your production OS.   It is not ready for that at all.  Dual booting with a stable release is a much better option so that your data is protected and gives you a platform from which you can access the testing OS' files and chroot into that OS to update/upgrade and repair things.

You could select the standard Gnome session at login.  Once you activate the login box there are some options on the bottom panel for your session.

---

### Post by encefalocardia on 2011-03-17
I'm already selecting the Classic Desktop session, that is where Unity is loading too. The Desktop Session loads fine, with Unity without the gnome panels.

---

### Post by mc4man on 2011-03-17
If logging into the Classic desktop loads the unity launcher then open ccsm (compizconfig-settings-manager) and disable the unity plugin if it's enabled.
(separate compiz profiles are maintained for Desktop (unity) and Classic logins

---

### Post by ranch hand on 2011-03-17
Well if you do not like Unity you could just remove some of the packages through Synaptic until it quits.

Or you could wait for the update/upgrade cycle to catch up to your hardware.

filing a bug would probably be a good idea if there is not one already.

---

### Post by encefalocardia on 2011-03-17
> **mc4man said:**
> If logging into the Classic desktop loads the unity launcher then open ccsm (compizconfig-settings-manager) and disable the unity plugin if it's enabled.
(separate compiz profiles are maintained for Desktop (unity) and Classic logins

That did the trick, thanks!

---

### Post by encefalocardia on 2011-03-17
> **ranch hand said:**
> Well if you do not like Unity you could just remove some of the packages through Synaptic until it quits.

Or you could wait for the update/upgrade cycle to catch up to your hardware.

filing a bug would probably be a good idea if there is not one already.

I like it ok. I'm just waiting for it to mature a more. It's quite unresponsive and buggy right now. I'm sure once Natty reaches final it will be great.

---

### Post by ranch hand on 2011-03-17
It will not be long now but in the mean time you could try just disabling the bugger.

Another thing, if this is not your main OS, is to do a complete clean install.  If you follow the Unity threads you will have seen that there has been many things that changed but the settings are left over from the old version and even the places where files "live" has changed.

I am not big on reinstalling but there are times that it does do the trick the easiest way.   If this is true in your case I certainly do not know.

---

