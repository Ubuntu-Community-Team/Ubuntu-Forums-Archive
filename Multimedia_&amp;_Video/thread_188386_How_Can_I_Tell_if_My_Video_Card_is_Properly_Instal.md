---
title: "How Can I Tell if My Video Card is Properly Installed?"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by polo_step on 2006-06-04
[FONT="Courier New"]It's apparently recognized and listed in the devices GUI, but it only shows the useless "Status: Status" line.  How do I know if it's really working, or just faked-up with VESA default drivers?

Thanks for any help with this! [/FONT]

---

### Post by steveneddy on 2006-06-05
[QUOTE=polo_step][FONT="Courier New"]It's apparently recognized and listed in the devices GUI, but it only shows the useless "Status: Status" line.  How do I know if it's really working, or just faked-up with VESA default drivers?

Thanks for any help with this! [/FONT][/QUOTE]

Run in a terminal:

glxgears -printfps

This will run a little video for you and give you, in the terminal display, a reading of how many **F**rames **P**er **S**econd the video card is putting out to the display monitor.

---

### Post by polo_step on 2006-06-05
[QUOTE=steveneddy]Run in a terminal:

glxgears -printfps

This will run a little video for you and give you, in the terminal display, a reading of how many **F**rames **P**er **S**econd the video card is putting out to the display monitor.[/QUOTE]
[FONT="Courier New"]OK...so...will it just do nothing if the VESA drivers are installed?

I know about this application from setting up my nVidia card in the desktop, and the rate of the gears being an indicator of the proper functioning of the AGP card, but this is the UniChrome Pro in the notebook (which I'm not using at the moment).[/FONT]

---

### Post by Tomy on 2006-06-05
[quote=polo_step][FONT=Courier New]OK...so...will it just do nothing if the VESA drivers are installed?

I know about this application from setting up my nVidia card in the desktop, and the rate of the gears being an indicator of the proper functioning of the AGP card, but this is the UniChrome Pro in the notebook (which I'm not using at the moment).[/FONT][/quote]

Run in a terminal:

glxinfo

at the top of the output you should see:

direct rendering: Yes

You might get around 500 fps running glxgears if things are working properly for the UniChrome Pro. You may need to disable screensavers as some of them freeze the computer solid with the Unichrome Pro and the "via" video driver.

Also the file /etc/xorg.conf will show the video driver in the "Device" section. It should say "via" not "vesa".

---

### Post by polo_step on 2006-06-06
[QUOTE=Tomy]
Also the file /etc/xorg.conf will show the video driver in the "Device" section. It should say "via" not "vesa".[/QUOTE]
[FONT="Courier New"]Cool!

Thanks very much for the information! :) [/FONT]

---

