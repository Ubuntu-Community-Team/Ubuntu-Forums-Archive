---
title: "New install Mythbuntu 16.04 on PowerEdge 860"
date: 2016-05-01
forum: Mythbuntu
---

### Post by hollywoodpete on 2016-05-01
I recently decided to "upgrade" my server from 14.04LTS to 16.04. I initially used the Software Updater but part of the way through the update, the screen went blank. I decided to be patient, rode my bike for a while, cam back and did a reboot. The server is now locked on the splash screen. I though, no big deal. I would simply install 16.04 with a USB drive and be back in business. I loaded a 8gb Sandisk Cruzer with the 16.04 ISO. I tested it on my laptop and it worked fine. I tried it on the server and got isolinux.bin missing or corrupt. Any help would be appreciated.

---

### Post by hollywoodpete on 2016-05-04
After 3 days and quite a few Google searches I finally was able to get it installed. Hopefully it will help someone else. During the boot the Bios defaults to USB Emulator as Auto. That setting needed to be changed to Hard drive. The USB was recognized and it booted. It may boot to Root: but the command live or live-install should start the installation

---

