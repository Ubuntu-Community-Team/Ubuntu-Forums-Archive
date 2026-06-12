---
title: "USB HID remotes in frontend"
date: 2013-08-17
forum: Mythbuntu
---

### Post by Erik-NA on 2013-08-17
Have installed a new Mythbuntu 12.04 frontend using a MCE Philips RC260 remote IR-controller which identifies itself as a HID USB keyboard device. As I understand it, there is no need for lirc support since the remote is identified a USB keyboard.

The key mappings are not the same as a classic IR controller using lirc and that is my problem - I want the same key mapping. There are a number of guides on the Internet, but I have not found any especially for mythbuntu 12.4.

The best I have found is this [http://www.mythtv.org/wiki/Generic_HID_%22MCE%22_Remotes#XKB_Remapping](http://www.mythtv.org/wiki/Generic_HID_%22MCE%22_Remotes#XKB_Remapping) written for Mythbuntu 11.04. I cannot determine if xbcomp in Mythbuntu 12.04 has built in support for "per device support" which is important if you also have a standard USB keyboard. (the supplied patch for xbcomp is not working in  Mythbuntu 12.04)

Is there any out there, using MythBuntu 12.04, who has succeeded to remap the remote controller with the same key map as standard MCE IR remote controller?

---

### Post by Erik-NA on 2013-08-18
After some testing, it seems that Mythbuntu 12.04 does not have "per device support" since my main USB keyboard is affected

---

