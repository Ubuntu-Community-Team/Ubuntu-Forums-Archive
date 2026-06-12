---
title: "[SOLVED] Multi Monitor Setup with nvidia-settings won't save!"
date: 2008-11-09
forum: Multimedia Software
---

### Post by Irwin J. Finster on 2008-11-09
Hi,

I have the nvidia graphcis drivers version 177 installed and working in Ubuntu 8.10. I use the nvidia-settings to set up my dual monitor setup, and when I click apply, all is running beautifully. I then click on "save to x configuration file" and the nvidia settings manager closes. But when I restart the system the next time the settings are lost. I tried to run nvidia-settings via sudo from the consol but with the same effect. Can anyone help me?

---

### Post by lovinglinux on 2008-11-09
Try adding the following command to System >> Preferences >>Session.

```
nvidia-settings -l
```

This works for me.

---

### Post by Irwin J. Finster on 2008-11-11
Thank you very much, this worked out fine! Why does this work? What does this option do?

---

### Post by lovinglinux on 2008-11-11
> **Irwin J. Finster said:**
> Thank you very much, this worked out fine! Why does this work? What does this option do?

I have no idea :D

I knew that if you add nvidia-settings to the session it works because it loads the video settings, but the nvidia  GUI shows up too, which is kind of annoying. Then I saw the -l option on another thread about video tearing, so I figured this option should load the nvidia-settings without the GUI. So I tried and it worked.

Please don't forget to set the thread as solved using the "Thread Tools" menu.

---

