---
title: "Possible glitch in GIMP's dialog boxes"
date: 2011-01-07
forum: Multimedia Software
---

### Post by SnickerSnack on 2011-01-07
I want to run this by the forum before filing a bug report since it may be an easy fix that I'm just not aware of and can't find.

First some background:

Lenovo Thinkpad x61 tablet
Xubuntu 10.10 64-bit
Gimp 2.6.10
xf86-input-wacom 0.10.8
three (3) pointing devices total
---wacom
---thinkpad trackpoint
---logitech G5

While using GIMP, several of the dialog boxes have an odd problem, including Save and Preferences.  When I open the Save dialog, no mouse inputs (any of the three) are received unless I first hover over the open image and the brush/tool/etc registers on the image.

These steps reproduce the problem:

1. Open new image.
2. Click File then Save, do not hover over the image window itself.
3. The Save dialog box does not receive mouse inputs.
4. Move the Save dialog out of the way and hover over the image briefly so that the tool registers and the mouse pointer changes.
5. Go back to the Save dialog and now mouse inputs are received.

This glitch does not arise if the Save dialog is opened via keyboard commands.

Is there a setting I need to change, or should I report this as a bug?

---

### Post by Cherry Cotton on 2011-01-27
It might be related to this: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/556670](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/556670) I have the same computer as you (though I’m running Ubuntu 10.10 i386), and I have a similar-but-worse problem. (I’m “Tina Russell” on the bug report)

---

### Post by SnickerSnack on 2011-02-18
Thanks for your reply.  I've commented on that bug report.

---

### Post by sethtriggs on 2011-03-02
I wonder if adding "Linux Input" to the Input Controllers options in GIMP might help? I was having this trouble today and that seems to have solved the issue at least temporarily. I'll see.

-Seth

---

### Post by SnickerSnack on 2011-04-18
> **sethtriggs said:**
> I wonder if adding "Linux Input" to the Input Controllers options in GIMP might help? I was having this trouble today and that seems to have solved the issue at least temporarily. I'll see.

-Seth

That doesn't seem to make any change for me.

What settings did you use?  I get "State: Device not available: Permission denied" for any device I try.

Thanks for replying.

---

### Post by Indolence on 2011-04-21
I experience this also.

In my case, having the extended input device 'wacom bamboo1 stylus' set to anything besides disabled presents the issue, regardless of the state of the other extended input device 'wacom bamboo1 cursor'. Disabling the wacom-stylus while leaving the wacom-cursor enabled allows me to open and use dialogues with the wacom tablet without issues, but at the cost of pressure sensitivity (because the stylus is disabled).

I've had the issue in Kubuntu/Ubuntu 10.10 64-bit and openSUSE 11.2 32-bit, on two different computers but using the same graphics tablet.

---

