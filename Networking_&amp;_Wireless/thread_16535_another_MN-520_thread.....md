---
title: "another MN-520 thread...."
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by joezane on 2005-02-22
i just switched over from Mandrake 10.1 to Ubuntu.
in general i really it. i nice clean solid distro with debians awesome package management.

however!
i have 2  issues so far.

one is that when i first start up. the 'X' in the middle of the screen for x starting up, just sorta stays in the middle of the screen on top of everthing.
after about 5 mins it goes away on its own. VERY weird. i'd love to make this stop (anyone?).
but i'm mainly writing because of my wifi card....

i purchased the uber-cheap m$ mn-520 because it is supposedly supported under linux (i've had crappy wifi experience with linux in the past).
under mandrake i was thrilled that the card was recognized my harddrake. configure and worked out the box! woo-hoo 
 \\:D/ 


no such luck under ubuntu.

 :| 

i've tried everything my somewhat limited knowledge  is able to muster and here's all i get.
both lights (power and wireless) on the card are light (but not blinking).
the gui config doesn't see a wifi card at all.

i've edited /etc/pcmcia/config with the following lines:
card "Microsoft Wireless Notebook Adapter MN-520 1.0.3"
version "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
bind "orinoco_cs"

nothing.

ifconfig doesn't show the card 
and iwconfig just spits out 'no wireless extensions'

oh. and yes, i have wireless tools installed....

any help would be SUPER appreciatted.
i'd love to ubuntu on the machine but i need the card to work!
i know it can be done as others have gotten it working.....

---

### Post by joezane on 2005-02-22
also,
i'm not sure if this helps, but in the gui...
Computer -> System Configure -> Networking

when i choose add+ wireless 
nothing shows up in the drop to pick a card.

---

### Post by joezane on 2005-02-22
ok.
one more thing...

i just did modprobe orinoco_cs
and i got this:

WARNING: Eroor inserting hermes (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/hermes.ko): operation not permitted
WARNING: Eroor inserting orinoco (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/orinoco.ko): operation not permitted
WARNING: Eroor inserting orinoco_cs (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/orinoco_cs.ko): operation not permitted

a quick check of dmesg shows no sign of orinoco_cs

so it seems like the driver isn't loading...

but i have no idear how to fix that.

anyone?

---

### Post by nocturn on 2005-02-22
[QUOTE=joezane]ok.
one more thing...

i just did modprobe orinoco_cs
and i got this:

WARNING: Eroor inserting hermes (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/hermes.ko): operation not permitted
WARNING: Eroor inserting orinoco (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/orinoco.ko): operation not permitted
WARNING: Eroor inserting orinoco_cs (/lib/modules/2.6.8.1-386/kernel/drivers/net/wireless/orinoco_cs.ko): operation not permitted

a quick check of dmesg shows no sign of orinoco_cs

so it seems like the driver isn't loading...

but i have no idear how to fix that.

anyone?[/QUOTE]

Where you root?
Try sudo modprobe orinoco_cs

---

### Post by joezane on 2005-02-22
i just did a re-install on the off chance that something just wasn't right.....

i know longer get any errors reported by modprobe.
but the card still doesn't work.


same symptoms

---

### Post by joezane on 2005-02-22
it seems like maybe pcmcia service isn't working?

i see no mention of it dmesg
and when i do modprobe pcmcia_cs i get a module not found....

?

lsmod shows orinoco_cs as loaded
but no pcmicia_cs

---

### Post by joezane on 2005-02-22
lsmod reports that orinoco_cs is loaded but used by 0



anyone?

 ](*,)

---

