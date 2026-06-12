---
title: "Question about Ubuntu startup / shutdown"
date: 2010-08-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rax_m on 2010-08-04
Hi 

Does anyone know if the Ubuntu startup / shutdown screens are going to change for Maverick?

I really hate that purple / off-black colour behind the Ubuntu logo. It should either be all black, or another colour completely. 

Thanks
Rax

---

### Post by ranch hand on 2010-08-04
There are other themes out there.  I am not sure what they all are as I can't run them anyway.

You can take the "splash" instruction out of your menu in /etc/default/grub and just have a black screen with messages.   Of course removing "quiet" in the same place will give you more messages if you like an active screen.

---

### Post by MacUntu on 2010-08-04
Just change it yourself.
[LIST]
[*]Open '/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script'
[*]Find the lines starting with 'Window.SetBackgroundTopColor' and 'Window.SetBackgroundBottomColor' and set them to ```
Window.SetBackgroundTopColor (0.00, 0.00, 0.00);
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);
```
[*]Run 'update-initramfs -c -k all'
[/LIST]
Tadaaa, black background.

---

### Post by rax_m on 2010-08-04
Thanks MacUntu... that works almost perfectly. There's a brief second where the logo still has a bit of purple in a block around the letters. 

But I don't mind too much.Thanks for all the other replies. 

Cheers

---

### Post by jerrylamos on 2010-08-04
I do "quiet" with no splash, boots up in 20 or 30 seconds anyway no sense slowing down boot with superfluous graphics.

My background is my wife in a bathing suit on a beach so that's the first real screen I see.

I shut down with Ctrl-Alt-Del and Enter, only takes 2 to 4 seconds so I don't notice what's on the screen.

Jerry

---

