---
title: "Error Exception in captureState of plugin Mirobridgeconfig"
date: 2010-04-17
forum: Mythbuntu
---

### Post by williammanda on 2010-04-17
During the MCC setup (I have installed ubuntu lucid beta 2 then MCC) I keep getting this error while applying any changes. See screenshot. I disabled all my plugins since I noticed a new entry "microbridgeconfig" but it still stays there.

Also I can't seem to load codecs as I usually do. I select Enable DVD Support and hit apply. It looks like to is processing then it comes back to the codec screen without Enable DVD Support unchecked with the previous error. See codec screenshot.

---

### Post by williammanda on 2010-04-17
> **williammanda said:**
> During the MCC setup (I have installed ubuntu lucid beta 2 then MCC) I keep getting this error while applying any changes. See screenshot. I disabled all my plugins since I noticed a new entry "microbridgeconfig" but it still stays there.

Well this issue has gone away since I logged out and back in. The plugins I have installed are weather, video, music and mythweb.

The second issue is still open. I will start another thread.

---

### Post by Lepy on 2010-04-19
I am also getting the Mirobridgeconfig error upon upgrading to 10.04. Trying anything in MCC causes it to crash, even clicking on the Mirobridgeconfig tab and selecting "Step #1: Install Miro and/or dependancies" or "Uninstall MiroBridge" and applying.

Running MCC from a terminal gives errors like "MirobridgeconfigPlugin_error: The MythTV video and/or image directories are not configure properly, correct and retry installation, errors are displayed in log"

But, I haven't tried to install Miro...hrmmm

---

### Post by Lepy on 2010-04-19
Other errors shows that fanart, screenshot, banner, etc directories not set. After setting these dirs in mythtv-setup, error is gone.

However, MCC is still crashing when trying to set an IR blaster with error "Don't know how which D-Bus type to use to encode type "NoneType"

---

