---
title: "[SOLVED] Recommend PCI or PCIe 1x Video Card"
date: 2008-07-31
forum: Mythbuntu
---

### Post by bmwman on 2008-07-31
Hello, I have a IBM ThinkCenter PC which I use for my backend. I want to plug it to my TV in the living room - 50"Phillips plasma. The problem is the PC has only VGA port and the TV has HDMI or S-Video or component. I've seen VGA-component cables online but i'm not sure if that's a good solution. I have DVI-HDMI adapter which I use with my laptop and it works fine, but i need to get DVI output port on the PC.

Can you recommend any cheap-O video card that's either PCI or PCIe 1x with DVI output? 

My biggest concern is compatibility  and drivers.

Thanks

---

### Post by nasha on 2008-07-31
My recommendation is GeForce 7200 GS. Its dirt cheap, available in PCI or PCIe (as well as low profile im pretty sure), and supported by Mythbuntu out of the box.

---

### Post by bmwman on 2008-07-31
WOW, that's even cheaper that I thought I would have to spend! :D

I'll definetly look into it. Is there any difference that it's 64bit and machine is 32 or I need to look for the 32bit version?

---

### Post by newlinux on 2008-07-31
You don't want to get a PCI card because I don't the think the PCI bus supports enough throughput for high definition (you'll have a harder time finding a PCI vid card these days anyway). Stick with PCIe Newegg has some cheap 7 series vid cards for ~$20 last i checked.

---

### Post by bmwman on 2008-07-31
I have one PCIe slot and i think it says 1X on it. Most of these cards are 16X. That's a problem, right?

---

### Post by gsrcrxsi on 2008-07-31
yep. a x16 card wont fit in x1. the slot of x1 is physically smaller.

---

### Post by bmwman on 2008-07-31
Sucks. I have to find something for PCI then. That PC is like 2 years old, it works for the purpose and i just need to find a way to make it work with my TV.

---

### Post by bmwman on 2008-07-31
I just bought a VGA to Component RCA cable, but it doesn't show anything on the TV. Anybody knows if something needs to be enabled or installed in Mythbuntu? I've heard something like enable TV-out thru the VGA but i'm not sure if there is such a thing

:(

---

### Post by bmwman on 2008-08-02
The VGA to Component cable didn't work. I kinda knew that but wanted to give it  a try. I returned the cable which was $35 and bought a 256MB GeForce 6200 PCI card. It seems to work for now and I'm happy. That was the only card for a regular PCI, not PCI 16x that I could find for around 50 bucks.

Thanks for all the suggestions. I hope this is helpfull to others.
Cheers.

---

