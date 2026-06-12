---
title: "PVR-150 Blaster in 8.04"
date: 2008-04-29
forum: Mythbuntu
---

### Post by Trimble Epic on 2008-04-29
I've seen a bunch of posts about the blaster not working in 8.04.  I just did a fresh install from scratch using 8.04, and I know the settings now include an option to use PVR150 and dish network somehow... But, I didn't find the PVR150's firmware .bin file.  My question is:  Is the FIRMWARE for the 150 now included in Mythbuntu?  Or are we still expected to go get the firmware and put in into place before we can even hope to get the blaster working?

---

### Post by yfaykya on 2008-04-30
I downloaded it from [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24). I think it might not be distributable due to licensing issues (last time I asked) but that may have changed. I did have to fight with hardy a little bit to get it to work (not mythbuntu - regular hardy).

---

### Post by kefkathemad on 2008-05-01
What did you do to get it to work in Hardy. I'm having the same problem.

---

### Post by BatPenguin on 2008-05-12
Yes, please post instructions on how to get PVR-150's blaster to work with Hardy. I had it under Gutsy but now it's broken. I've been trying to follow different guides (including using a custom lirc from here: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)) but so far haven't been able to make it work. It seems like half the guides say that you have to use the lirc_pvr150 module and others talk only of i2c. Could somebody who has it working please let us know how it was done so we could copy your setup? Thanks.

---

### Post by BatPenguin on 2008-05-13
OK, replying to my own post since I got this working. So this post is just to explain the steps to other people who might have problems with this:

- I have a PVR-150 with its blaster
- I'm using Hardy & Hardy's itvtv driver

To get it working I downloaded the modified Lirc sources from here:

[HTML]
http://www.blushingpenguin.com/mark/blog/?p=24[/HTML]

I had a problem with compiling it, so I had to make one more change: the compiled lirc_pvr150 module wouldn't load, it would fail with the error "lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio".

In that page, on messages 231-233, this is explained as a feature that has been removed from the later versions of IVTV. So to get it working, you have to remove "sections of the code in drivers/lirc_pvr150/lirc_pvr150.c that call ivtv_reset_ir". So, before compiling, I edited the lirc_pvr150c file and commented out this:

```

#void ivtv_reset_ir_gpio(struct ivtv *itv);
```

(to comment stuff out in the code you add /* in front of the commented part and */ at the end. So: 

```

/*#void ivtv_reset_ir_gpio(struct ivtv *itv);*/
```



...and then I compiled it. I had a ready-made lircd.conf already, so I just made sure hardware.conf was set ok and that only lirc_dev and lirv_pvr150 were being loaded. Rebooted, and it worked.

I probably won't be subscribing to this thread for long anymore but if somebody is having a problem with the same hardware and Hardy, feel free to contact me by private messages. I hope this helps someone!

---

### Post by paynoattention on 2008-12-09
BatPenguin, You rock!!! I was pulling my hair out all day trying to resolve the 'disagrees about symbol version' messages thinking it was a module symbol version issue. As you pointed out it was just an obsoleted symbol all along. It's a LOT easier to comment out a symbol reference that isn't used anymore than to get module symbols from different compiles to match.

---

