---
title: "NVIDIA driver configuration: Unable to open X config file for writing."
date: 2010-05-13
forum: Multimedia Software
---

### Post by Rykes on 2010-05-13
Hello!
I realise, that questions have been asked in this topic, but the answers in those topics didn't entirely help me.
I open the nvidia settings with "kdesudo nvidia-settings" as I know I need those rights to write the xorg.conf file, but still I get the error : Unable to open X config file '/etc/X11/xorg.conf' for writing.
The research that I've done says the key is the "kdesudo" tag, but as I've mentioned earlier, I am already using that, and it still throws the error.
It was suggested that I should try to save it somewhere outside of etc/X11 , and later overwrite the /X11/ file manually, but I cannot save it elsewhere either. Now I'm not an adept at Kubuntu, but I've figured I must be able to save things in my lolcal "home" folder, but I still get the very same error.
I'm using the recommended NVIDIA driver, and I have a GeForce 9800 GT.
Any answers would be much appreciated.
(I've been trying to get to know ubuntu since the early afternoon, but this problem finally gave me a halt.)

---

### Post by WinterRain on 2010-05-13
> **Rykes said:**
> Hello!
I cannot save it elsewhere either.

Yes you can if you click "show output" and manually copy it to a text file. Then merely copy into xorg.conf file. Reboot.

---

### Post by Rykes on 2010-05-13
Ahh, WinterRain ! May your name be blessed, this one worked like a charm, and yet so simple, I should have thought of it. Nevertheless, I hope one day I can return the favor.
Do you want some chocolate maybe ?

P.s.: And an answer this quick ! Really, awesome.

---

### Post by carolinason on 2010-12-12
install the python-gtk2 package via kPackageKit and the nvidia-settings configuration tool should be able to write to /etx/X11/xorg.conf

---

### Post by denisk on 2011-05-07
Thank you for your suggestion, carolinason. It is much easier to manipulate xorg.conf directly from nvidia-settings UI!

---

### Post by rosco136 on 2011-07-16
> **carolinason said:**
> install the python-gtk2 package via kPackageKit and the nvidia-settings configuration tool should be able to write to /etx/X11/xorg.conf

Brilliant! Got me out of the poo!!
But how did you find out in the first place?

I think Linux is for programmers, not for hardware designers. But if it was not for us, what would there be to program?

Cheers

---

### Post by glide on 2011-12-06
Have this problem too (under Ubuntu 10.04) but python-gtk2 is already installed.
Tried to reinstall it but I have still the error.
Can't even save the file on my ~home.
Have also this error on the terminal:
> VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

---

