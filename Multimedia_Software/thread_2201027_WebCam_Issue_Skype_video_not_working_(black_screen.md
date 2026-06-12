---
title: "WebCam Issue: Skype video not working (black screen), in Ubuntu 12.04"
date: 2014-01-22
forum: Multimedia Software
---

### Post by roberto.rojnic on 2014-01-22
My Skype (4.2.011v) video devices is not working. I get a black image. I tried my webcam (CIF Single Chip /dev/video0) with Cheese and it works fine. 

My search for a solution online yielded the following input do type in the Terminal. 

My input in the Terminal :: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

Terminal Output ::
 
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored. 
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored. 
`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load 

(skype:7913): Gtk-WARNING **: Failed to load type module: (null) 

`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load 

(skype:7913): Gtk-WARNING **: Failed to load type module: (null) 

`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load 

(skype:7913): Gtk-WARNING **: Failed to load type module: (null)

Can anyone please explain what this means and/or suggest what I have to do to fix the issue?

Thank you for your time!

---

### Post by wertsmhvonline on 2014-02-25
My system: Ubuntu 12.04 LTS, 64-bit. Logitech C310 HD webcam

I had a similar problem, the webcam not working in Skype, but functioning normally in Cheese, Camorama.
In Skype, the webcam was not even recognized (the drop-down list was empty).
After having unsuccessfully tried re-installing Skype, and all various ways of starting Skype with extra options (as suggested in many messages), the solution that worked for me was actually simple:

- In the home folder, remove the hidden '.Skype' directory. This can be achieved in Nautilus: open the home folder, press Ctrl+H to show all hidden directories, and rename the '.Skype' directory to something like "dotSkype-old" (or delete it altogether)

All Skype settings will be lost, and Skype will ask for your Skype name and pass-word on next start-up.

In my case this procedure led to Skype recognizing my new webcam, and now the webcam works in Skype, in Cheese, in Camorama.

P.S.  My problem was probably related to the fact that I changed webcams. The previous, an old Philips SPC710NC, broke down and I replaced it with the Logitech. The .Skype folder perhaps also contains some specific configuration data on the webcams, which prevented the new webcam from being recognized.

---

### Post by roberto.rojnic on 2014-04-03
Thanks for the response to my post! I have tried this option, and it does not work. I am searching for other options. 

Thanks

---

