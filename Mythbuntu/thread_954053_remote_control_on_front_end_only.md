---
title: "remote control on front end only?"
date: 2008-10-20
forum: Mythbuntu
---

### Post by meanmrmustard on 2008-10-20
I have a master FE/BE machine in one room and would like to be able to use a remote control on the FE only machine in the other room.
Is there a way to do this without having a TV card in that machine?
I'd like to replace the keyboard that I'm using now.

---

### Post by issih on 2008-10-20
Yup, thats no problem, provided you can get a remote working on the front end machine, it will work just fine..

I can use my macbook's silly little apple remote for instance, and my backend is on my desktop pc.

hope that helps

---

### Post by meanmrmustard on 2008-10-20
What sort of receiver must I use?
I was hoping an extra Logitech model for a mouse/keyboard would do the job.
Probably not though, eh?

---

### Post by SiHa on 2008-10-21
How's your soldering?

You could make a homebrew serial receiver. I'm using the 'more advanced' version found mentioned here:
[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)

I've got two of these working, I've even used one of them to replace the in-built receiver on my Hauppauge card, because I can't stop the card filtering out repeat keypresses.

Once built, just plug into your com port and do```
sudo dpkg-reconfigure lirc
```Select **Homebrew 16x50 compatible**. If you plug into the external COM port you want **ttyS0**, for internal it's **ttyS1**.

That should configure LIRC for you, you'll need to then either record an lircd.conf, or find the appropriate one in **/usr/share/lirc/remotes**

If you want to use the internal port, you'll need to fit a 10-way IDC female box-header onto a piece of ribbon cable. Pin numbers map 1-1 to the 9-way d-sub (Pin 10 is N/C of course!)

If you want to try this and run into problems or need more info, I'll help if I can.

One last thing, if you're planning on using a Hauppauge remote. I've found that (for Nova-T single, and Nova-T 500 Dual, anyway) the codes generated using the inbuilt receiver are different to the codes using a homebrew receiver. The codes for a PVR350, in **/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge** work fine.

HTH

Simon

---

### Post by meanmrmustard on 2008-10-21
Soldering will be no problem.
I'll give it a go.
Thanks!

---

