---
title: "Help! I killed X!"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by FurryNemesis on 2006-06-22
Having followed this [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")
guide for my Nvidia Geforce MX460 Go (I used the non-legacy drivers and method 1 btw, seeing as my card wasn't on the list), I then restarted the server.

The Ubuntu splash screen came up. Then I got a blank screen with a frozen command prompt.

I tried restoring my old xorg.conf from the command line in Grub using (sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf) - it wasn't interested (unrecognised command) and the error repeated. I tried the xorg.conf reconfigure trick - unrecognised command.

I re-installed the lot and 

(sudo apt-get install nvidia-glx)
(sudo nvidia-xconfig)

edited xorg.conf to read "nvidia" instead of "nv"

Reboot.

Same problem.

Long story short, is there anything I can do from grub to regenerate a clean xorg.conf? I've tried (sudo dpkg-reconfigure xserver-xorg) but that gives me an unrecognised command. 

More importantly, can I somehow use the livecd to pull off the same trick?

Thanks.

---

### Post by will_in_wi on 2006-06-22
The grub command line is used to manually boot OSs. It is not used like the normal command line. The way to do it with the livecd is to use the rescue mode. When the livecd boots, type rescue into the : . This will put you into a prompt that you can modify your installed system with.

Another option is to go into "single user mode". First, when the grub screen comes up, select the ubuntu line and hit e. Then select the line that starts with kernel, hit e again, and add the word single to the end of the line. Then hit b. This should get you to a prompt with admin permissions.

---

### Post by tseliot on 2006-06-23
[QUOTE=FurryNemesis]Having followed this [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")
guide for my Nvidia Geforce MX460 Go (I used the non-legacy drivers and method 1 btw, seeing as my card wasn't on the list), I then restarted the server.

The Ubuntu splash screen came up. Then I got a blank screen with a frozen command prompt.

I tried restoring my old xorg.conf from the command line in Grub using (sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf) - it wasn't interested (unrecognised command) and the error repeated. I tried the xorg.conf reconfigure trick - unrecognised command.

I re-installed the lot and 

(sudo apt-get install nvidia-glx)
(sudo nvidia-xconfig)

edited xorg.conf to read "nvidia" instead of "nv"

Reboot.

Same problem.

Long story short, is there anything I can do from grub to regenerate a clean xorg.conf? I've tried (sudo dpkg-reconfigure xserver-xorg) but that gives me an unrecognised command. 

More importantly, can I somehow use the livecd to pull off the same trick?

Thanks.[/QUOTE]
Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

---

### Post by FurryNemesis on 2006-06-25
Fantastic! The grub trick worked and I now have a working system again. Thank you both :)

---

