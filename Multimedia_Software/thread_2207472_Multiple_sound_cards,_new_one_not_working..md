---
title: "Multiple sound cards, new one not working."
date: 2014-02-23
forum: Multimedia Software
---

### Post by archaeometrist on 2014-02-23
Because of the stuff I do, I run multiple sound cards (one USB, the built-in, and I just added a Creative Audigy FX PCIe - ALC898).  The computer is a new one Dell 7010 MT i7 with Intel PCH sound (ALC269VB).  I run Ubuntu 12.04LTS and while everything looks good (the cards show in aplay and arecord -l, no error messages, plus they show up in Sound Settings) the card doesn't work.  Doing the speaker test is ineffective - the buttons work but you hear nothing from the card except a loud click in the left earphone when you first push the left button.  running dmesg does show the outputs for the card as inputs but that's the only strange thing I've noted (it also shows in amixer and alsamixer).  If I try to go in and change certain settings, my computer locks up - I have to physically power it down.  It reboots without trouble if that happens.

I think from the symptoms one of two things is happening (maybe both) - the Audigy card is somehow paralleling with the built-in audio although it shouldn't and if they get too different everything locks up.  The other possibility is that somehow the card is in some sort of digital mode and I can't figure out how to check that.

I was running a system with an Audigy II, the USB unit, and the built in audio before and they worked well together (using 32 bit Ubuntu 12.04LTS).  Sadly, the Audigy II won't work at all with this computer - it's not being recognized as existing even though I would activate the PCI (normal) slot.

I don't have a lot of money to be spending on fancy audio cards... I just needed a third one for interfacing with speakers (and on occasion a microphone).  The built-in audio has the bandwidth and gain I need for my equipment, and the USB audio handles its stuff without a problem.

---

### Post by Yellow Pasque on 2014-02-23
Has the card ever worked under any OS?

Have you tried reinserting the card and/or a different slot?

What mobo do you have and is the BIOS updated?

---

### Post by archaeometrist on 2014-02-25
The motherboard is the one that comes in a Dell 7010 MT with the i7 processor - and there is no identifying number as far as I can see (the computer is new).  I spent an hour or two trying to find out more about it, but so far no luck (just got innundated by thousands upon thousands of advertisements when I googled the model).  I haven't checked the bios and doubt that will be a problem (brand new computer and PCIe has been around for years now - and I think that's true for the card as well).  There is only one slot that it will go in - not possible to restack.  I don't know about the card working in another OS... I only have Ubuntu 12.04LTS on my computers (the other an older laptop) and don't have access to a computer that has the right kind of slot.

---

