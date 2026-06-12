---
title: "Just installed Nvidia 6200 no video now"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by ksujason on 2008-01-14
I just installed my new Nvidea 6200 video card in my computer. When I booted it the first time, I left the monitor cable plugged into the motherboard VGA connector. Everything booted fine and when it came up I was asked if I wanted to install the restricted driver. I answered yes and it said a reboot was required afterwards. I shut the system off and moved the monitor cable over to the new video card and turned it on. 

My system would never boot again. It looks like it is coming up fine and even makes it past the ubuntu splash screen. It then freezes on a screen that says Running local boot scripts (/etc/rc.local)

Does anyone have any suggestions that I may try?

Thank you.

---

### Post by Yellow Pasque on 2008-01-14
Something's wrong with your xorg.conf file. When you get to the screen where it says "running sripts...", press Ctrl+Alt+F1 to get back to the terminal. Then look in the /etc/X11/xorg.conf file (sudo nano /etc/X11/xorg.conf) and see what driver is listed in the Device section. Try changing back to "nv", saving, and rebooting. If that doesn't work, switch the driver to "vesa" and see if you can get X to come up with that.

Also check for any lines that say BusID and make sure they match the ID of your vidoe card given by the lspci command.

---

### Post by ksujason on 2008-01-14
After typing the command mentioned above, It goes into a screen that has GNU nano 2.0.6   File: /etc/x11/xorg.conf      modified

That is across the top, then at the very bottom are some options like get help, writeout, read file, and etc. I cant seem to run any of these commands.

Sorry, but I am very new to Ubuntu.

Thanks

---

### Post by RomeReactor on 2008-01-14
Hi. As Temüjin said, when you open the file in nano (the command line text editor), scroll down to **Section "Device"**; there, find this line:
```
Driver: "nvidia"
```
and change it to:
```
Driver: "nv"
```
Then press CTRL+O to save the file, CTRL+X to close the text editor, and then:
```
sudo reboot
```
If after rebooting you're not brought back to your desktop, run the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
Accept all the defaults it tells you, except when asked to choose a video driver select **nv**. After that finishes, you should be brought to your desktop. Then you can go to 'System->Administration->Restricted Drivers Manager' and enable the proprietary drivers there.

---

### Post by Yellow Pasque on 2008-01-14
I don't like nano myself either. You can try vim instead. Just hit the i key and you should see the word "INSERT" at the bottom. Now just edit the file as you would with a text editor. When you're done, hit 'Esc', type :x, and press Enter. That will save the file.

---

### Post by RRS on 2008-01-14
You may also have to dissable the mptherboards onboard video.

You'll have to do this from the BIOS before Grub starts.

---

### Post by ksujason on 2008-01-14
Thanks everyone. After changing the driver to nv, rebooting, and then going through the configuration you mentioned, my computer finally booted to where I can see it.

I think it is all working, but is there a way to check if my new card is functioning the way it should be?

I seem to remember trying a command with spinning gears, but I cant remember what it was.

Thanks again.

---

### Post by RomeReactor on 2008-01-14
To see which driver the video card is now using:
```
cat /etc/X11/xorg.conf | grep Driver
```
and look at the last one listed. To check if you have hardware acceleration enabled:
```
glxinfo | grep direct
```
And to see the spinning gears:
```
glxgears
```

---

### Post by ksujason on 2008-01-14
It says I now have the nvidia driver. The gears seem to be spinning fine as well.

I guess everything is good to go.

Thanks everyone.

---

### Post by Yellow Pasque on 2008-01-14
Good to hear. Enjoy

---

