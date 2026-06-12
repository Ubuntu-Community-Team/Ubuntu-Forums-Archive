---
title: "[SOLVED] Sound on Dell Precision WorkStation 410 MT"
date: 2008-08-16
forum: Multimedia Software
---

### Post by rmckean on 2008-08-16
This workstation comes with an onboard Crystal Sound CS4237B that was not recognized on startup. I'm running Ubuntu ver 8.04. Through reading threads and trying myself to resolve this it is now recognized. However I still have no sound. Running the sound tests from sound preferences I get this error. audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument.

Any suggestions as to how to resolve this would be appreciated. Thanks

---

### Post by rmckean on 2008-08-16
I did a search on launchpad and I believed I have resolved my issue. I just found that the setting of sound (System - Preference - Sound), all settings were in "auto detect".
I changed to ALSA, and press "Test" ...it works!!! Thanks

---

