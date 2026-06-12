---
title: "Correct way of chaning lirc configuration ?"
date: 2008-07-07
forum: Mythbuntu
---

### Post by erland on 2008-07-07
What is the correct way to change the lirc configuration in Mythbuntu 8.04 for various applications without risking it to be overwritten during upgrades ?

Can I safely change the ~/.lirc/mythtv file or should I add a new file in ~./lirc/ which contains my additional key-mappings ?

---

### Post by superm1 on 2008-07-08
Anything in ~ is fair game to modify.  This stuff only gets changed if you rerun mythbuntu-lirc-generator (possibly from MCC).

---

### Post by countcobolt on 2008-07-08
I must say that I needed to do everything manually as the MCC lirc configuration part got locked. Running with irrecord + configurating lircrc was the easiest solution to me

---

### Post by erland on 2008-07-08
I suppose the mythbuntu-lirc-generator will overwrite the files in ~/.lirc/ ?
Will it only overwrite files it knows or will it clear the whole ~/.lirc directory ?

The reason I'm asking is that I tought it would be a good idea to put my own files as for example:
~/.lirc/myth_custom

In that case I only have to remember to add new includes if mythbuntu-lirc-generator is run some time by accident through MCC.

---

