---
title: "Unity Launcher Icons Keep Changing?"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mindswap1 on 2011-04-21
So I know It's not a big deal, but my Unity Launcher Icons for Trash and Workspace Switcher keep changing and I don't know why. Instead of having the Stripped trash can icon for trash bin I get the old transparent recycle bin icon. And instead of having the black and white workspace switcher icon i get the old purple one. Any way to fix this?

---

### Post by cariboo on 2011-04-21
You could try:

```
unity --reset-icons
```

be warned that this sets the launcher icons back to the default, anything you've added to the launcher will be gone.

---

### Post by Mindswap1 on 2011-04-21
So I tried it, and sadly it didn't work. The Garbage Can Icon is still using the old transparent garbage bin instead of the striped one, but the workspace switcher icon is back to the new one. Did they just decide to not use the striped trash can icon? I included a pic of how mine looks.

This is a known bug as I understand, but it was said to be fixed. Here is the link for the bug report. And I did see the update tht was supposed to fix it, but it hasn't worked for me. 

> [http://fossplanet.com/f10/%5Bbug-761289%5D-re-trash-ws-switcher-icon-unity-resets-defaulticon-theme-event-deletion-emptying-trash-orafter-upgrade-129636/](http://fossplanet.com/f10/%5Bbug-761289%5D-re-trash-ws-switcher-icon-unity-resets-defaulticon-theme-event-deletion-emptying-trash-orafter-upgrade-129636/)

---

### Post by mc4man on 2011-04-21
> **Mindswap1 said:**
> So I know It's not a big deal, but my Unity Launcher Icons for Trash and Workspace Switcher keep changing and I don't know why. Instead of having the Stripped trash can icon for trash bin I get the old transparent recycle bin icon. And instead of having the black and white workspace switcher icon i get the old purple one. Any way to fix this?

The striped trash icon is gone, the ws icon should be the black and white one
Update unity to the latest ver (unity 3.8.10-0ubuntu2) and then log out/in

---

### Post by Mindswap1 on 2011-04-21
Oh that would make sense thank you for your help :).

---

