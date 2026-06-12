---
title: "Xserver failed"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by hoehaver on 2006-07-07
im on my dads computer right now. i was trying to add video ram and i added the line like....VideoRam          '3200" or something like that, it doesnt work, it crashed my xserver. on the log in without the xserver how to i open the configure file for the Xserver, i know what i need to delete. i just dont know how to get there.

---

### Post by hoehaver on 2006-07-07
wait....i forget if it was the xserver file or the....um....f86...file......damn

---

### Post by tonyr on 2006-07-07
> **hoehaver said:**
> im on my dads computer right now. i was trying to add video ram and i added the line like....VideoRam          '3200" or something like that, it doesnt work, it crashed my xserver. on the log in without the xserver how to i open the configure file for the Xserver, i know what i need to delete. i just dont know how to get there.

One of your boot options should say 'recovery mode'.  That one should
drop you into the single user console (no graphics).  The info
you added should have been in **/etc/X11/xorg.conf**.   From the
console you should be able to edit the file with **nano** or **vi**.

---

### Post by hoehaver on 2006-07-07
what exactly do i type in into the console. im a novist. and i have no idea what nano isir the other you mentioned

---

### Post by tonyr on 2006-07-07
**nano** is a simple visual text editor.  There is a command list
at the bottom of the screen.  the '^' character means CTL, so ^X means
CTL+X.  Use the arrow keys to move around.  The **delete** or 
**backspace** should delete text backwards.

At the command prompt do
```

nano /etc/X11/xorg.conf

```

If you mess it up, you can ^X which should exit without saving.  
^O writes out your modifications.  ^X will ask if you want to save changes
(if you made any) to which you can answer 'n'.

How did you get **the VideoRam 3200** in there in the first place?

---

### Post by hoehaver on 2006-07-07
my buddy was helping me out, raf. hes a programmer, he told me to type a line into the termenal and when i hit enter the.conf file poped up so i could edit it. he told me to type in  VideoRam        "3600"  but it didnt work i just got my opengl working for my interneal video card, i needed some video ram so i could play bzflag, the file he told me to go to didnt exist, so thats why i had to type in the "videoram ect ect"

---

### Post by hoehaver on 2006-07-07
thank you very much, it worked, and i fixed it.......do you know how to modify your video ram? the file its sopost to be in...it was blank....i dont know but on boot up it says i have 1mb of video ram, thats not enough.

---

### Post by tonyr on 2006-07-07
If I understand you correctly, the file **/etc/X11/xorg.conf** was
empty or did not exist.  Is that right? So when you fixed it this
time, the only line in there was the one with **VideoRam  3200**?

Has this ubuntu installation ever worked, I mean, shown you a graphic
desktop instead of the console?  If it has, there should be
some file or files in the directory **/etc/X11**.  If you are
back in the graphic desktop, open a terminal (Applications->Accesories->Terminal) and type at the prompt
```

ls -l /etc/X11

```
or type the same thing at the white-on black console.

---

