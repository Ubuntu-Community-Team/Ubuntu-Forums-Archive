---
title: "Radeon HD 6850 Works No More"
date: 2013-02-28
forum: Multimedia Software
---

### Post by redbikemaster on 2013-02-28
SO I had a Radeon HD 6850 on my Lubuntu 12.10 machine running fine. I opened the case to rearrange components to make it look nicer. In doing so, I moved the graphics card from the first PCIe x16 slot to the third one. Now, Minecraft blackscreens, and I try to open the AMD Catalyst Control Center, but it gives me the message:

There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No AMD graphics driver installed, or the AMD driver is not functioning properly. Please install the AMD driver appropriate for you [sic] hardware, or configure using aticonfig.

What do I do to fix?

I tried setting the BIOS to put VGA primary to PEG3 (whatever that means), so it's not trying to read the first slot as default. I need this fixed ASAP, because I'm hosting a LAN party next week!

---

### Post by redbikemaster on 2013-03-01
So I figured out my BIOS settings, but things are much worse.

i reinstalled fglrx, using the latest driver from AMD's website. Now, I go to login, and no login dialog box appears.
I tried out autologin, but now I just get a black screen.
I even tried switching from lightdm to gdm, but that didn't work.

i really need this computer running immediately! I also need it for school tomorrow!

---

### Post by QIII on 2013-03-01
Did you uninstall the older driver before installing the new one?

---

### Post by redbikemaster on 2013-03-01
I did. I was very thorough, too.

---

### Post by QIII on 2013-03-01
With some Gigabyte boards, you have to at least fill the first x16 slot for the others to work.

Did you try putting it back in the first one?

---

### Post by redbikemaster on 2013-03-01
No, I haven't. If I do, should I switch the bios setting back?

I tried installing lightdm-gtk-greeter per this thread: [http://ubuntuforums.org/showthread.php?t=1807612](http://ubuntuforums.org/showthread.php?t=1807612)

This is because my system displayed text saying 'Stopping System V runtime compatibility'. Now, I can't get to a CLI, the screen just flashes black on and off.

---

### Post by QIII on 2013-03-01
I'd go back to where you were.  Set the BIOS back and put the card in the first x16 slot.

---

### Post by redbikemaster on 2013-03-01
I will when I can. I now have to write a three page paper for my English class by hand. I am really regretting 20 credit hours.

Thanks for the help, Qlll. (Are all of those L's or i's?)

---

### Post by QIII on 2013-03-01
Capital "eyes".

Q followed by the Roman Numeral III

---

### Post by redbikemaster on 2013-03-01
Enlightened, I am, QIII (Q The Third).

---

### Post by redbikemaster on 2013-03-03
UPDATE: I put the card back in the first slot and reverted the BIOS setting. I haven't been able to check the operation of the driver due to the fact that when I attempt to boot, it gets to what should be the login screen, then the screen stays black while the monitor backlight flashes on and off. Even Ctrl-Alt-F1 can't get me out of it. It looks like I'll need to boot off the install disk and do something, but what?

---

