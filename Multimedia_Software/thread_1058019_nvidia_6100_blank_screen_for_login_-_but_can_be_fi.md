---
title: "nvidia 6100 blank screen for login - but can be fixed"
date: 2009-02-02
forum: Multimedia Software
---

### Post by pchaffey on 2009-02-02
Hi all,

I have a problem when rebooting a machine which goes to a blank screen when you should be able to enter your login details. All is not lost, as I can goto a console (ctrl alt f1) and place a safe vesa xorg.config on top of the nvidia created xorg.config file, then restart the window manager (sudo /etc/init.d/kdm restart - kde in my case). The login screen appears and I can use the slow vesa driver as expected.

Now here is the wierd bit, if I go back to the console and replace my temporary vesa xorg.config with the nvidia created file, and restart the window manager as before, the nvidia driver / xorg.config work perfectly. No errors or warnings get reported in the log file /var/log/xorg.0.log in either case. I cannot find any errors or warnings at all - if anyone can suggest a log file to post please do so.

I am using kubuntu 8.10 with the very latest nvidia driver (from thier website) 180.22, but strangely this same effect occured before with the 177.xx drivers from ubuntu restricted drivers.

This is a server like machine, so the problem is not great as I reboot rarely - but I am still puzzled...

thanks in advance if anyone can give me any pointers...

---

