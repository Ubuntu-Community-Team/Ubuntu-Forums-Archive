---
title: "so i had my wifi manger stop picking up wifi..."
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by JuicyCouture on 2011-01-05
ubuntu was working great on this laptop, an acer aspire 5520 with an atheros 5001 right from the start - then yesterday after i signed back in from screensaver, something messed up with the keychain, the wireless icon started doing its searching animation and kept asking me to re-enter my WPA key, it wouldnt stop - i restarted and then it didnt even have networks available anymore, "wireless disconnected"

now i looked around everywhere trying several different approaches, and nothing happened. so i wiped ubuntu this morning, reinstalled and now its good again.

i just want to know, im sure it was some fluke - but do you guys have any idea what may have caused this, and what i can do henceforth to stop it from happening again?

it was something to do with that damn keychain i know it...
:KS

---

### Post by JuicyCouture on 2011-01-05
for anyone who is interested - it happened again tonight (around the same time i would say...curious) 

anyway, i tried one other thing tonight and it finally worked - i disabled networing...shut the computer OFF (not restart) come back and i guess it reset itself

thank jeebus but i wish this wouldnt keep happening

its such a good OS but i see what people are saying abotu the networking problems

is there some other replacement network manager i could get?

---

### Post by Bucky Ball on 2011-01-05
Are you using 10.10? Has some probs at the moment. 10.04 is stable.

wicd. System->Admin->Synaptics Package Manager and search for it. Wicd will install and *uninstall* Network Manager in the process.

---

### Post by JuicyCouture on 2011-01-05
ah it just happened again - im notcing it only happens when i leave the computer unattended

i was on it for like 4 hours no problem, i leave for 20 minutes to watch hockey, come back and the wireless icon is searching like crazy. disable networking, shut off/turn on - enable networking, it comes back

go on for another 3 hours no problem, leave for 15 minutes again - come back and its lost the connection

yes i'm using 10.10, what are you saying i should do with WICD?

thanks

by the way whats the best way to get a posting history on this forum? i know clicking on my avatar and "find more posts by this user" works - what else is there?

---

### Post by Bucky Ball on 2011-01-06
'Search' (third from right at top of thread), 'List all your threads' (or posts).

When you are online, go to Synaptic Package Manager, search for wicd, install it.

---

### Post by JuicyCouture on 2011-01-06
one last thing, theres a whole bunch of them listed

(wicd, wicd-gtk, wicd-daemon, wicd-cli) -_- what do i dooo!?

---

### Post by Bucky Ball on 2011-01-06
Just install 'wicd'. That will drag in what it needs. Once that's done reboot.

I just installed it myself and noticed it didn't remove Network Manager. If you are still on Network Manager when you reboot, remove that using Synaptics.

---

### Post by JuicyCouture on 2011-01-06
k i'll do it if it happens again which im counting on any moment...

thx bud

---

### Post by FastTiger on 2011-01-06
I have the same problem, and switch to Wicd and it didn't do me any good. 

Here my thread: [http://ubuntuforums.org/showthread.php?p=10313220#post10313220]("http://ubuntuforums.org/showthread.php?p=10313220#post10313220")

There are some solution that didn't work for me but may work for you.

---

### Post by JuicyCouture on 2011-01-06
well like i said, i seem to simply have to 'restart' the network manager, as its not a driver problem or hardware connectivity problem - the thing just stops doing its just sometimes. so i disable it, turn the computer off and on, then enable and bam its there. 

i tried all sorts of things, shell commands to restart the network service - only this has worked for me. 

like i said if it happens again i'll do the other guys idea and post the results

edit: i read that thread thanks im sure one of those is bound to work

---

### Post by grahammechanical on 2011-01-06
You want to know what is causing this. It could be happening because of some power saving setting either in BIOS or in Ubuntu. It could be switching off the network or wireless adapter.

I do not know if this will solve the problem but go to System>Preferences>Startup Applications. Select the Options tab and click the button that says Remember Currently Running Application. If you do not have any applications running, the system might just remember that network manager was running and it might restore network manager when power save is de-activated.

I have no proof that any of this is any good. But there has to be a better way to fix things than re-installing or changing network managers.

Regards.

---

### Post by Bucky Ball on 2011-01-06
> **grahammechanical said:**
> ... there has to be a better way to fix things than re-installing or changing network managers.

Regards.

Really? All depends on the wireless card. Changing to wicd is a cinch and for some it solves all problems. Re-installing, I would agree, is going a little overboard (unless 10.10 is causing problems and you are trying 10.04 LTS). ;)

"You want to know what is causing this?" Guess that's why the OP posted the thread, but you never know, your guesswork might do the trick, grahammechanical. Fingers, toes, and eyes crossed ...

---

### Post by JuicyCouture on 2011-01-06
hasnt happened since yesterday, i like the guys idea about the thing turning off the wireless card

what is the keychain by the way, whats the difference between that and the system asking me for my user password>?

---

### Post by JuicyCouture on 2011-01-06
somethign else interesting i just noticed

i could trigger the loss of connection when connecting to the same two videos

i had a flash video going on two different sites, they started to chug and the audio started skipping - 3 seconds later loss of connection

reboot, do my usual fix routine - its good for a while, i put those exact same videos up again side by side, it cuts out

interdesting...

---

### Post by JuicyCouture on 2011-01-06
yeah something is definitely triggering it

i just left for 4 hours and nothing

theres always a video involved when it happens...

interdesting...

---

