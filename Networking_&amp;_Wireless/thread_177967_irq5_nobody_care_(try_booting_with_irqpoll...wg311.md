---
title: "irq5: nobody care (try booting with irqpoll...wg311v2"
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by stock99 on 2006-05-17
hi,

  I was killing my windows xp on my old p3 450MHz pc and puting ubuntu 5.1 Then my wg311v2 stop working. But the exact same card work on the new p4 celeron machine flawlessly with ubuntu5.1 (don't even need to manual config after selecting DHCP and seting essid on installation screen). 

  Then i play around and put reinstall ubuntu in sever mode and found the message on starting up network interface..

* configuring network interfaces .... [ok]
* Waiting for network interface to come up .....


[4294721.182000] irq5 : nobody cared (try booting with the irqpoll' option.
[4294721.182000] Handlers:
[4294721.182000] [<e0aae5c4>] (acx_interrupt+0x0/0x501 [acx_pci])
[4294721.182000] disabling IRQ #5


I don't think its driver issue anymore. Can anyone help me with this? RIght now my network card can't ping anything (except 127.0.0.1 and what ever assigned ip are fine). The LED is flashing green. 

I am not so sure what does that message mean. Shall I disable sth? 

ps: In windows installation , there isn't a problem.


Appreciated any suggestion!

Stock99

---

### Post by it.henrik on 2006-05-17
Have a look in bios if something else is assigned to irg5 ... if I remember correctly soundblasters usually wants the irq5 too. If it is a really old soundcard or network card you can prob change the irq of the card with a jumper on the card. google for manuals if you cant find them :)

---

### Post by stock99 on 2006-05-17
so different OS using different IRQ for a sound card? Or windows is somehow able to reassign either wireless card or sound card to diff irq? The pc has sound chip built-in on board. Not sure if i can disable that. 

Anyway, i will try to unplug all card (except video) to see if it work. The computer currently has scsi for the old 4x burner.

---

### Post by stock99 on 2006-05-17
the bios doesn't allow me to change IRQ for sound (if an onboard one use such). I have disable it and it make no difference. The scsi card is using irq11 which shouldn't be problem.

---

### Post by stock99 on 2006-05-18
ok i finally work it out... it turn out that if i disable some irq, the error message will just change from irq5 to 10 or sth else. So i add in the irqpoll option in the grub boot menu. After that during start up the error message still display but now my card work like a charm.
-------------------------------------------------------

1) boot into the system and edit /boot/grub/menu.lst , and look for like start like

title Ubuntu, kenrel 2.6.12-9-386
root (hd0,)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 irqpoll ro quiet splash
                                                                    ^^^^

initrd  /boot/initrf.img-2.6.12-9-386
savedefault 

.
.
.


  ps: look at where i add in irppoll


---------------------------------

Hopefully , it clear enough for someone encounter same problem like me and looking for solution :)

chris

---

### Post by stock99 on 2006-05-19
was play around a bit with bios setting and now it seems to switch to disabling irq10.  Instead of using "irqpoll" , i use "apci=noirq"  . This completely remove the error message at bootup and seems working fine.

---

