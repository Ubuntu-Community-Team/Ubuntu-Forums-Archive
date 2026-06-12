---
title: "Uninstalling video card driver/black screen"
date: 2011-01-04
forum: Multimedia Software
---

### Post by Zors on 2011-01-04
I recently swapped a hard drive from another computer I was using.
The previous computer had nVidia video card (i think it was 9500? something like that), and the new computer has an ATI Radeon 4200 HD video card.

Now, when I boot it up on my new comp using the same hard drive, I get a black screen and my monitor just switches from digital, analog, hdmi. I'm guessing that the video card drivers are still installed, but I cannot switch back the hard drive since my other comp is far away from where I live. If I boot up with ubuntu CD however, it loads fine.

I have many important files on the previous install though, and I'm not sure how to get to it. I wouldnt mind reinstalling ubuntu as long as I can get those files back.

Thanks for any help you can give.

---

### Post by mikewhatever on 2011-01-04
You could simply mount the drive while running from cd, navigate to /home/username/ and copy all the files you need.

---

### Post by Zors on 2011-01-04
How do I do that? (Sorry , new to linux)
I'd be running ubuntu from the CD, but I would need to access the hard drive by mounting... how do i do this?
Also, when I try to access it using the GUI, it says that I dont own that folder so I cant access it.

'The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "my name here"'

---

### Post by Bucky Ball on 2011-01-04
Try this:

Open a terminal (Applications->Accessories->Terminal)
Type: 'sudo nautilus' (without apostrophes)

You now have whatever permissions you like on everything as you are in as root. Don't hang about like that for long, though, as root can do some _***real***_ damage. Do what you have to do and close Nautilus (file browser).

---

### Post by ajgreeny on 2011-01-04
Using then live CD, open nautilus with root permissions using command ```
gksu nautilus
```and you can then open and/or copy anything to an external drive, and then if needed, reinstall the OS from scratch.

---

### Post by Zors on 2011-01-04
EDIT: I found out how to get access following this thread
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way)

Thanks to everyone that helped :D

---

### Post by ajgreeny on 2011-01-04
You obviously have installed with an encrypted filesystem, so I will now have to bow out of these discussions as I have never dealt with such things, and can therefore not suggest where to go from here.

---

### Post by Bucky Ball on 2011-01-04
> **Zors said:**
> EDIT: I found out how to get access following this thread
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way)

Thanks to everyone that helped :D

Good news. If your issue is solved, help others by following the last line of my signature ...

Good luck with it all. ;)

---

