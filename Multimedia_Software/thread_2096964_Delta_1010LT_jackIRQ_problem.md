---
title: "Delta 1010LT: jack/IRQ problem"
date: 2012-12-21
forum: Multimedia Software
---

### Post by Floating Point on 2012-12-21
Ubuntu (12.04 or 12.10):
When my Delta 1010LT is sharing IRQ with a USB controller, jack only works with it when there is some input through USB (for example, I have to move my mouse for qjackctl to be able to start up jack server and sound is playing through Delta only while I am doing something with the mouse). If there is no mouse conected, I can't start jack server.

If Delta is plugged into PCI which does not share IRQs with anyone, I can't do anything using jack.

But, pulseaudio works in all situations.

The motherboard is [http://ark.intel.com/products/59506/Intel-Desktop-Board-DH77KC](http://ark.intel.com/products/59506/Intel-Desktop-Board-DH77KC)

Did anyone have some similar issues?

---

