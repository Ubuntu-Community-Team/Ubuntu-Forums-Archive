---
title: "Skype Video Chat on Ubuntu 9.10"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by macsdev on 2010-01-09
Hi,

I recently shifted to Ubuntu from Windows and the one software I miss badly is Skype, especially the Video Chat. I did install the Skype Software from their website (Version 2.1). It does not have a Video Chat facility as far as I can see. Am I missing something?

---

### Post by garryknight on 2010-01-09
Open the main menu (the white-on-blue S at the bottom-left of the main Skype window), click Options, then Video Devices. Check the Enable Skype Video box and "Start my video automatically when I am in a call". All calls will be video-enabled from that point onwards, provided that you have a working webcam showing in the "Select webcam" box.

---

### Post by macsdev on 2010-01-12
My web camera is working fine as seen from the setting you have mentioned. But, I don't see any option to make a video call even though the contact has enabled video chatting.

---

### Post by Linuxforall on 2010-01-12
Do you see video cam working in the video tab of skype options, if not you will have to start skype with the command LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype in terminal.

---

### Post by macsdev on 2010-01-15
It's working fine. The only difference is in the Windows version, there are separate options to make a video call and a audio call. Here, there is only one call button. Thanks for the help ppl.

---

