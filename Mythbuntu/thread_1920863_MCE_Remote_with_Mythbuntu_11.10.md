---
title: "MCE Remote with Mythbuntu 11.10"
date: 2012-02-05
forum: Mythbuntu
---

### Post by cliveb on 2012-02-05
I recently built a new Mythbuntu 11.10 system on an Acer Revo 3700, and bought one those "Vista MCE remotes" - the sort you can get on eBay for about £12. It works to a certain extent - for example I can select and play recordings, but can't pause. I assumed that the lirc mappings needed to be modifed, but then to my suprise found that it seems as if lirc isn't even installed. My guess is that the MCE remote is masquerading as a keyboard, and it just happens that some of the keys are useful, while others are missing (eg. there is no button on the MCE remote that produces a 'P' keyboard press - hence no way to pause). Is that a reasonable deduction? Here is an extract from DMESG when I plugged in the MCE's USB receiver:

```

[327275.616036] usb 2-1: new low speed USB device number 3 using uhci_hcd
[327275.858693] input: HID 05a4:9881 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input10
[327275.858944] generic-usb 0003:05A4:9881.0004: input,hidraw3: USB HID v1.10 Keyboard [HID 05a4:9881] on usb-0000:00:1d.0-1/input0
[327275.990961] input: HID 05a4:9881 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input11
[327275.991274] generic-usb 0003:05A4:9881.0005: input,hidraw4: USB HID v1.10 Mouse [HID 05a4:9881] on usb-0000:00:1d.0-1/input1

```

My question is this: in order to get full remote functionality in Myth frontend from the MCE remote, will I need to install lirc or is there some other (perhaps simpler) way of reconfiguring which keyboard keys are emulated by the MCE remote buttons? And if I do need to install lirc, are there any guides to setting it up with the MCE remote? For example, how would I get the Linux kernel to recognise the MCE IR receiver as a remote rather than a keyboard?

Thanks.

---

### Post by wyliecoyoteuk on 2012-02-05
You don't need LIRC.
Read my exlanation here:
[http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/](http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/)

---

### Post by ecwanet on 2012-02-05
I also have Mythbuntu 11.10 and one of these vista remotes(does it say vrc-1100 on the back somewhere? The vendor and device ids on mine are the same as those on yours). It presents as a hybrid device, being a keyboard and a mouse, without the use of any lirc drivers.

I found that trying to install lirc just made things worse. You don't need to. By default, key presses are passed to whichever application window has the "focus" (sorry, win-speak) and that is Mythfrontend if it's on top.

So, in Mythfrontend go to utilities/setup>edit keys and find the context/function you need (say, TV playback>pause) then right arrow (real keyboard or remote) brings up four boxes, the first of which probably contains a letter P. Tab to the next empty one and press enter to open the key set dialogue. Now press either the pause key or the play key on the remote and the key sequence is captured. Then use the arrow keys to go to the "OK" box and press enter. You're done.

I said to press either of the pause or play keys because they give the same signal, like a sort of two-button toggle.

Now repeat for all the contexts and functions you want to set and save the setting when you exit.

None of the mouse functions, including the pad and its right and left buttons register in "edit keys" so you can't use them in that way. By the way, on this remote the "i" button is the same as the mouse right click key, which is a shame.

I haven't mastered the volume up/down and mute keys yet as the OS audio controls seem to grab them first.

Good luck.

---

### Post by cliveb on 2012-02-06
> **ecwanet said:**
> So, in Mythfrontend go to utilities/setup>edit keys and find the context/function you need (say, TV playback>pause) then right arrow (real keyboard or remote) brings up four boxes, the first of which probably contains a letter P. Tab to the next empty one and press enter to open the key set dialogue. Now press either the pause key or the play key on the remote and the key sequence is captured. Then use the arrow keys to go to the "OK" box and press enter. You're done.
Please forgive me for having my brain out of gear. I should have figured this out for myself, of course.

Many thanks for pointing me in the right direction.

---

### Post by cliveb on 2012-02-08
A quick follow-up. (I had originally posted another question but then realised that it was a pretty stupid one which had an obvious answer)...

When you set up the key bindings using the "Edit Keys" feature feature as described by ecwanet, some of them (eg. pause) work fine, but others (eg. fwd, rwd) simply refuse to do anything.

After various experiments, I came to the conclusion that MythTV ignores the Shift part of the key combination, so keys that send things like Ctrl+Shift+B invoke whatever is bound to Ctrl+B in MythTV. Therefore in order to set up the key bindings for those buttons on the MCE remote which include a Shift as part of the key combination, it's necessary to use a real keyboard so you can set up the key binding without the Shift.

---

