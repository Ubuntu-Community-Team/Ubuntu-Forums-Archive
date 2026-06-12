---
title: "[SOLVED] Nvidia drivers Please edit your X configuration file (error) need help"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by dandixon on 2008-03-11
I want to start off saying I know there is a lot of post about this and I've read and tried most of then. Really need help.

this is my error when trying to run the nvidia drivers.
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

can some walk me thought how to fix this?
Everything was work until i installed vmware server ( which also I can't get to work :)  )

Thanks
Dan

---

### Post by gtdaqua on 2008-03-11
what version are u running?

anyway there is a nice guide i prepared. 

[Gutsy Latest NVIDIA on DELL - walkthrough]("http://ubuntuforums.org/showthread.php?t=596875")

I just installed the latest NVIDIA version 169.12 (feb 26 release). There is Mar 7 release too - but try the stable 169.12. 

Let me know how it went.

Note: If you cant see the screen or only a cursor blinks on the top left, then press Ctrl+Alt+F1 to go direct to command prompt and perform the installation. Print the guide if you have to before entering command line.

---

### Post by dandixon on 2008-03-11
Im running Gutsy

I give it a shot.
Thanks

---

### Post by gtdaqua on 2008-03-11
> **dandixon said:**
> Im running Gutsy

I give it a shot.
Thanks

It should definitely work if you followed the guide. Has never failed me. One thing to note is that whenever you upgrade the kernel, you need to reinstall the NVIDIA driver. NVIDIA has to compile the drivers for the new kernel.

---

### Post by dandixon on 2008-03-11
comand not found
sudo /etc/inid.d/gdm stop

should it be sudo /etc/init.d/gdm stop

Also login as root I know this should be easy but when i have try to do that in the past i just get wrong password.

---

### Post by zxscooby on 2008-03-11
did you try the command 

```
 sudo nvidia-xconfig
```

---

### Post by dandixon on 2008-03-11
ya did work.

---

### Post by dandixon on 2008-03-11
gtdaqua  

Dude you are my hero.
Thanks man work like a charm

---

### Post by gtdaqua on 2008-03-11
> **dandixon said:**
> comand not found
sudo /etc/inid.d/gdm stop

should it be sudo /etc/init.d/gdm stop

Also login as root I know this should be easy but when i have try to do that in the past i just get wrong password.

this will not work if you are running on recovery mode because "gdm" or "kdm" would not have loaded. gdm is for GNOME and kdm is for KDE. 

Anyway, am glad it works for you now!!

---

### Post by gtdaqua on 2008-03-11
> **dandixon said:**
> gtdaqua  

Dude you are my hero.
Thanks man work like a charm

can u change the thread title to have "[SOLVED]" like this:

```

[SOLVED] Nvidia drivers Please edit your X configuration file (error) need help

```

So anyone in future can take this for a quick reference.

---

