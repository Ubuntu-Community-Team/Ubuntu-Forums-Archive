---
title: "cdtray gui control"
date: 2012-11-26
forum: Multimedia Software
---

### Post by neil.the.blue on 2012-11-26
Hello,

I just got a new box for my daughter, but the cd front is 'designed' to hide the open/close button. Is there a gnome/unity gui (12.10) that will open/close the cd tray when it is empty?

Thanks
Neil

---

### Post by 2F4U on 2012-11-26
Not sure if there is a GUI tool, but what about the eject tool?

---

### Post by neil.the.blue on 2012-11-26
Sorry I should have added, she is only young and doesn't understand the terminal yet. I need to make it really easy so I don't get called every time she wants to change a cd :)

---

### Post by BigJules on 2012-11-26
Have you tried assigning a spare key (like the "0" in the keypad) to the eject task? Does it in one hit without the need for mouse etc.

Go to system settings > keyboard > shortcuts > sound & media; assign your hot-key to 'Eject'
OR 
write a macro invoking 'eject -T' and assign it to a hot-key using xmacro or similar

Cheers, Dad   :guitar:

---

### Post by pkadeel on 2012-11-26
Adding to BigJules method, you can also create a launcher on desktop with eject command for ejecting and closing the cd tray. On laptops, the closing usually does not work because of the manual close mechanism of cd trays.

Create a new file on your desktop using any text editor and put the following code in it
```

[Desktop Entry]
Name=CD
Exec=eject -T cdrom
Terminal=false
Type=Application

```Close the file and rename it "CD.desktop"
change its permissions to Execute or in terminal
```

chmod 0700 ~/Desktop/CD.desktop

```This launcher will toggle CD tray. If closed, it will open the tray. If open, it will close the tray

---

### Post by neil.the.blue on 2012-11-26
Thank you, two great ideas. I will try both and see which one works best for her. :)

---

