---
title: "Nvidia driver error"
date: 2009-12-25
forum: Multimedia Software
---

### Post by kenichiaeb on 2009-12-25
[FONT=Arial][SIZE=2][SIZE=2]Hi all, I'm new in this forum, and a little in ubuntu, before all, I'm sorry if my English is a little bad, cos I'm Argentinian and my language is **Spanish**.
I have been using it for 2 weeks and i love it, but there is a problem witch is teasing me.
The problem is that I installed the nvidia drivers, and the first time it worked very well, but when I turn off my computer and then I turn on it, the settings select the 800x600 resolution, and when I change the resolution again to 1024x768 and restart my computer, again the 800x600 resolution. I readied a similar problem in this forum, and I tried like 10 solutions, and none of them worked, so this is my question: [/SIZE][B][SIZE=2]how can I save the settings of nvidia?[/SIZE]

[/B][/SIZE][/FONT][FONT=Arial][SIZE=2]Thanks for you help[/SIZE][/FONT]

---

### Post by HappyFeet on 2009-12-25
You need to do:
```
gksudo nvidia-settings
```
Make your changes, and save. But that might not work, so here is the rest:
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by kenichiaeb on 2009-12-25
Hi again, thank you, it worked.
But I have another problem now, the window's title and buttons are gone, I don't have the close, maximize or minimize buttons and even the shadows of the menus, I tried changing the theme for another, and rebooting again but it didn't work, what can I do now?

---

### Post by HappyFeet on 2009-12-25
```
sudo apt-get remove --purge metacity
```
then
```
sudo apt-get clean && sudo apt-get autoremove
```
then
```
sudo apt-get install metacity
```

---

### Post by kenichiaeb on 2009-12-25
There is another problem yet that i didn't see before...
The terminal doesn't work... It's just a white square, I write something but it still in blank, so I tried to do what you said trought the recovery mode and whitout the "sudo", but it didn't work either, what you recommend to do?
Thanks again

---

### Post by HappyFeet on 2009-12-25
In recovery mode, you can become root and execute those commands without sudo by doing 
```
sudo -i
```
then run those commands without sudo.

---

### Post by HappyFeet on 2009-12-25
If you can get to your desktop, you can get a "terminal" by doing Ctrl-Alt-F2, then do the commands.

---

### Post by kenichiaeb on 2009-12-25
Ok, let me try
No, nothing works...
I think I'm going to reinstall

---

### Post by kenichiaeb on 2009-12-26
Okey, now it works perfect
The problem was that I didn't read the "Hit the button labeled show output".. actually I did, but I don't know why i didn't do it haha, what I did was save the config file with another name, and copy it's content and paste to the new file.
Anyway, now I reinstalled and done your first instruction and it worked perfect
Thank you for your help. Greetings!

---

