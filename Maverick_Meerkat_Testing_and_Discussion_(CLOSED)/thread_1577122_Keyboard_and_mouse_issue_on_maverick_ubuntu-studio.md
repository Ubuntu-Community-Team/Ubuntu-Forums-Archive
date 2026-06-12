---
title: "Keyboard and mouse issue on maverick ubuntu-studio"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dancer_69 on 2010-09-18
Hello,
I recently install maverick and I have a strange behaviour of mouse and keyboard. Everytime I reboot mouse and keyboard aren't acceessible on gdm login window and for arround 3 minutes after ubuntu desktop appears(I have a timed autologin).
My keyboard is logitech G11, and mouse is a wireless usb logithech too.
How can I solve this issue? Any ideas?

---

### Post by dancer_69 on 2010-09-18
Problem solved accidentlly when I updated grub.
I don't know how, because I tried to change resolution for grub screen, and when I updated grub and reboot machine,I was able to use mouse and keybord as normal.
[B]
EDIT:[/B]
Speak to fast.
After reboot I tried to change plymouth theme and update initramfs, resault:
1. plymouth splash screen doesn't work(I get only console messages)
2. keyboard-mouse problem came back

Tried again the above procedure, only update-grub & update-burg, and reboot.
But now I have again mouse-keyboard issue.

---

