---
title: "Hauppauge remote issue"
date: 2007-10-22
forum: Mythbuntu
---

### Post by meanmrmustard on 2007-10-22
I'm presently using the  "grey remote" (A415-HPG) which worked fine after the initial install but now the 'back/exit' button does nothing.

That command, along with all the rest, show up when i run irw, and it worked fine for the first few hours of use.

Has anyone else experienced anything like this?

---

### Post by ickyb0d on 2007-10-22
> **meanmrmustard said:**
> I'm presently using the  "grey remote" (A415-HPG) which worked fine after the initial install but now the 'back/exit' button does nothing.

That command, along with all the rest, show up when i run irw, and it worked fine for the first few hours of use.

Has anyone else experienced anything like this?

Yeah, my back button does nothing as well.  I used to have it mapped to  escape, which was nice.  With a fresh install, i know that the power button is mapped to escape, so you can use that instead of the back button.

If you want, you can also probably copy the entry for the power button in your ~/.lircrc and just link it to the back button as well.

---

### Post by meanmrmustard on 2007-10-22
Cool, thanks! I'll give it a shot.

---

### Post by meanmrmustard on 2007-10-23
Hmmm.... my power button doesn't escape either, even though .lircrc says it does.

---

### Post by drarmi on 2007-10-25
Is the correct event used for the remote?


Follow this [link]("http://parker1.co.uk/mythtv_tips.php") and read under "Make the LIRC Device Static"

---

### Post by meanmrmustard on 2007-10-31
The command in the instructions does not list my IR device - it lists power button (FF) and power button (CM), keyboard, mouse,PC speaker and Macintosh Mouse button emulation... whatever that is.

---

