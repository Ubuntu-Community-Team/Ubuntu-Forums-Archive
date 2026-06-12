---
title: "Streamzap"
date: 2007-12-12
forum: Mythbuntu
---

### Post by voctikal on 2007-12-12
Just got a streamzap remote. Works great as soon as i plugged it in.  

Had a question about the button mapping. Nothing seems to work except the arrows and the ok button.  Does anyone with this remote know what the defaults are?

Or if someone could tell me how to map the buttons?

Not sure how to pull up the lirc config file or what to type for the buttons.

---

### Post by superm1 on 2007-12-12
> **voctikal said:**
> Just got a streamzap remote. Works great as soon as i plugged it in.  

Had a question about the button mapping. Nothing seems to work except the arrows and the ok button.  Does anyone with this remote know what the defaults are?

Or if someone could tell me how to map the buttons?

Not sure how to pull up the lirc config file or what to type for the buttons.
Do the updates, you should see a new mythbuntu-lirc-generator show up.  Open up mcc and hit the checkbox to regenerate the dynamic button mappings and hit apply.

Restart myth and you should hopefully have some more button mappings in place.

If not, then you will have to manually modify ~/.lircrc and ~/.mythtv/lircrc

---

### Post by voctikal on 2007-12-13
Just in case the update doesnt fix it.  What do I need to type in the terminal to change the commands.  Or ever better is there a website that tells what the commands are.

---

### Post by williammanda on 2007-12-13
Try this link:

[https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)

---

### Post by nimda79 on 2007-12-17
Here's the lirc that I use, just replace it under your home\username\.lircrc

---

