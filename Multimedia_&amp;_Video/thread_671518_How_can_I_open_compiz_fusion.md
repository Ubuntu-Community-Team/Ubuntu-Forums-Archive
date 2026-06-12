---
title: "How can I open compiz fusion?"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by lemonicetea on 2008-01-18
I have successfully installed latest driver on my laptop, which has a X1400 graphic card. But I still can't open compiz..What should I do?

---

### Post by RomeReactor on 2008-01-18
Hi. I'm not certain about this since I don't have an ATI card, but I think you need to install XGL:
```
sudo aptitude install xserver-xgl
```
Next, restart your display by pressing CTRL+ALT+BACKSPACE, and then try to enable the effects in 'System->Preferences->Appearance->Visual Effects'.

There is a new driver developed by ATI that provides hardware acceleration without XGL, but it hasn't hit the repositories yet, and it seems it still has a few bugs.

---

### Post by lemonicetea on 2008-01-19
> **RomeReactor said:**
> Hi. I'm not certain about this since I don't have an ATI card, but I think you need to install XGL:
```
sudo aptitude install xserver-xgl
```
Next, restart your display by pressing CTRL+ALT+BACKSPACE, and then try to enable the effects in 'System->Preferences->Appearance->Visual Effects'.

There is a new driver developed by ATI that provides hardware acceleration without XGL, but it hasn't hit the repositories yet, and it seems it still has a few bugs.
I followed somebody else's post to install ATI driver,, the first step is to remove "xserver-xgl" module. But why we need to reinstall that? what's the difference between the original xgl and late xgl...Thank you very much.

---

