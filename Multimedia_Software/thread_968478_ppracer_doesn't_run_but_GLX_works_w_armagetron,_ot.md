---
title: "ppracer doesn't run but GLX works w/ armagetron, others"
date: 2008-11-02
forum: Multimedia Software
---

### Post by chrislpnt on 2008-11-02
My system is Kubuntu 8.10. When I try to run ppracer I get

[FONT="Courier New"]*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)
[/FONT]
I can run armagetron in fantastic speed with no problems, though. Indeed:

[FONT="Courier New"]glxinfo |grep render
[/FONT]
gives me

[FONT="Courier New"]direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
[/FONT]
I have searched Google up and down but everybody with the same symptom seems to have trouble with GLX which I clearly don't have. I can also run OpenGL screenservers just fine. I don't know where to look for a solution. Anybody got any ideas?

Thanks,
Chris

---

### Post by 2oucan on 2008-11-26
I have the same/similar problem.

After a fresh installation of Ubuntu/Edubuntu 8.10 (first time installation on this machine) I opened ppracer to see if 3D was working and it worked fine (first time I've had 3D acceleration on my Toshiba Portege 7200/S3 Savage MX - thankyou Ubuntu). Then I got greedy/curious and played with the ppracer advanced settings then ppracer wouldn't work (black screen). I have tried removing ppracer and reinstalling it, then complete removal and reinstall, restarting, reloading the savage files,  but ppracer won't start from the launcher or from the command line and I get the same message

*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)
tim@tim-laptop:~$ glxinfo | grep "render"
direct rendering: Yes
OpenGL renderer string: Mesa DRI Savage/MX/IX 20061110 AGP 1x x86/MMX/SSE
tim@tim-laptop:~$ 

The 3D part (molecule editor) of Kalzium works so i I couldn't figure it out.

[COLOR="Red"]_**I then tried to start ppracer from the command line as root and it worked**_[/COLOR].

I then tried to launch it from the games menu again and from the command line as user but it won't launch. It only launches when you are root.

I'm still lost.

---

