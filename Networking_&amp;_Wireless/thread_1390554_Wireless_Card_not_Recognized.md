---
title: "Wireless Card not Recognized"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by a-web on 2010-01-25
Using xubuntu 9.10 on a Compaq Presario 2100.

After a shutdown the computer no longer recognizes my Linksys external wireless card.  I can't even get the power light on the card to light up.  This was not after any updates or system changes...

---

### Post by a-web on 2010-01-26
I tried a different card in my PCMCI slot, but to no avail.  I ended up getting back online by sharing internet from a mac through an ethernet cable.

Is there any way to test if my PCMCI slot is broken?  (Other than trying my wireless card in a different computer with a PCMCI slot, since I don't have one.)

---

### Post by chili555 on 2010-01-26
With the card inserted does this tell us anything?```
lspcmcia
```

---

### Post by ant2ne on 2010-01-26
> **a-web said:**
> I can't even get the power light on the card to light up.troubleshoot bad card. Can you verify that it works in other device?

---

### Post by a-web on 2010-01-26
> **chili555 said:**
> With the card inserted does this tell us anything?```
lspcmcia
```
This is the input with and without the card inserted:```
a-web@Cutter:~$ lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
a-web@Cutter:~$ lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
```Doesn't look good...

And ant2ne, I have two cards which "stopped working" and no other device to try them on.

---

### Post by chili555 on 2010-01-27
Looks like a defective card to me. One last thing to try is to open a terminal and ***without*** the card inserted, do:```
sudo tail -f /var/log/messages
```Insert the card. Any interesting kernel messages pop up?

---

### Post by a-web on 2010-01-28
> **chili555 said:**
> Looks like a defective card to me. One last thing to try is to open a terminal and ***without*** the card inserted, do:```
sudo tail -f /var/log/messages
```Insert the card. Any interesting kernel messages pop up?
This is the output without the card:```
a-web@Cutter:~$ sudo tail -f /var/log/messages
[sudo] password for a-web: 
Jan 28 15:47:31 Cutter kernel: [   19.391540] eth0: DSPCFG accepted after 0 usec.
Jan 28 15:47:31 Cutter kernel: [   19.391564] eth0: link up.
Jan 28 15:47:31 Cutter kernel: [   19.391584] eth0: Setting full-duplex based on negotiated link capability.
Jan 28 15:47:34 Cutter kernel: [   21.812046] AC'97 1 does not respond - RESET
Jan 28 15:47:35 Cutter kernel: [   23.353304] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
Jan 28 15:47:35 Cutter kernel: [   23.353337] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
Jan 28 15:47:35 Cutter kernel: [   23.353382] pci 0000:01:05.0: putting AGP V2 device into 4x mode
Jan 28 15:47:35 Cutter kernel: [   23.487544] [drm] Setting GART location based on new memory map
Jan 28 15:47:35 Cutter kernel: [   23.487562] [drm] Loading R100 Microcode
Jan 28 15:47:35 Cutter kernel: [   23.487614] [drm] writeback test succeeded in 1 usecs
```And nothing changes when I insert the card.  Dead slot?

---

### Post by chili555 on 2010-01-28
> And nothing changes when I insert the card. Dead slot?Or dead card. Do you have another card to try in the slot? A pal with another laptop to try your card?

---

### Post by a-web on 2010-01-30
> **chili555 said:**
> Or dead card. Do you have another card to try in the slot? A pal with another laptop to try your card?I have two cards... both have the same response.  And it started on the same day...  I will try another laptop.  But I am marking the thread as "solved" since I am convinced my PCMCI slot is shot.  Thanks.

---

