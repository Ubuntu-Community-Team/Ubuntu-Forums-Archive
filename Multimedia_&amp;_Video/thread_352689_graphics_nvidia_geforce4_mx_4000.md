---
title: "graphics nvidia geforce4 mx 4000"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by jtmedin on 2007-02-03
Got no response so will try again. I have a lcd dvi monitor which requires 1024x768 resolution. Trying to get it to work with v6. Need an expert to give me some help. HELP TIA

---

### Post by pseudonym on 2007-02-04
Sounds like you need to reconfigure your X server (graphics) settings - Open up a terminal and type - ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as they apply to you, making sure to choose 'nv' as your driver and to specify 1024x768 in the list of resolutions. Then restart your X server by pressing Ctrl+Alt+Backspace

If you want to install the accelerated nvidia driver follow Method 1 in [this guide]("http://albertomilone.com/latest_nvidia_udsf_edgy.html"). For your card, you need to install the 'legacy' nvidia driver.

---

