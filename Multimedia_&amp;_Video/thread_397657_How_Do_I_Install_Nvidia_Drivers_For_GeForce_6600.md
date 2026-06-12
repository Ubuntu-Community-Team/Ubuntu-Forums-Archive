---
title: "How Do I Install Nvidia Drivers For GeForce 6600?"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by PyroMessiah on 2007-03-30
So I'm a total newbie.  I love the OS so far, but I'm having slightly glitchy video right now.  I'd like to install nvidia drivers, but I have no idea how to do so.  Can anyone help?

---

### Post by Slim Odds on 2007-03-30
> **PyroMessiah said:**
> So I'm a total newbie.  I love the OS so far, but I'm having slightly glitchy video right now.  I'd like to install nvidia drivers, but I have no idea how to do so.  Can anyone help?

Go to NVidia web site
Download driver
sudo chmod +x <filename>
sudo sh <filename>

That should do it

---

### Post by slayerboy on 2007-03-30
> **PyroMessiah said:**
> So I'm a total newbie.  I love the OS so far, but I'm having slightly glitchy video right now.  I'd like to install nvidia drivers, but I have no idea how to do so.  Can anyone help?

If you are using 6.10, then try [Envy ]("http://www.albertomilone.com/nvidia_scripts1.html")( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )
 

It's easier to use and I've never had a problem with it.:)

---

### Post by jbumgar on 2007-03-30
I didn't have any luck with envy.  Still no Nvidia.

---

### Post by johnc4510 on 2007-03-30
Here's the how to for the binary drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by DoorGunner on 2007-03-30
If all else fails i used the ubuntu_edgy wiki

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

just look up graphics card section and it works fine.

---

### Post by PyroMessiah on 2007-04-01
Okay Slim Odds suggestion worked.   Thank you very much!!! :)

---

### Post by tseliot on 2007-04-01
> **jbumgar said:**
> I didn't have any luck with envy.  Still no Nvidia.

I guess you didn't enable the Universe repository. Nevermind...

---

### Post by DoorGunner on 2007-04-01
I have a question for using the NVIDIA site drivers. It used to be at one time that everytime you had a kernel change you would have to reinstall the drivers. I knew the repository drivers usually changed or upgraded with the kernel. 

Is this still the case or am I  out of date on this? :-k 

I have been doing it the repository way for so long I havent really kept up with it all.

---

