---
title: "intel/ati dualhead black monitor - brightness set to 0 (acpi issue?)"
date: 2013-01-02
forum: Multimedia Software
---

### Post by kometonja on 2013-01-02
i'm using arch linux but had this issue with other distributions as well on hp pavilion g6 laptop with intel and radeon graphic card including Ubuntu 12.04

when i modify xorg.conf file to enable dualhead (such as VGA1 leftOf LVDS) using **intel** driver it works fine except LVDS ("laptop monitor") has brightness set to 0 and is blank. using media keys i can increase it and it's fine. when waking up from screensaver it's blank again..

1) is this graphic driver or acpi issue? can i disable it somehow or change default value of brightness? i've tried video=SVIDEO-1:d kernel parameters and some other hints from arch wiki, doesn't work for me.

2) this is irrelevant but still weird.. when i make VGA1 (external monitor) primary and LVDS rightOf it, after boot I have to modify xorg.conf and change VGA1 to VGA2 for dual head to work. After restart its VGA1 again and so on...

---

