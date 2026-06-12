---
title: "Login screen resolution"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by Spamuel on 2006-07-21
Hi guys, this is my first post so please bear with me.

I've used both Ubuntu and Kubuntu and I've settled for the latter, however once thing has bugged me in each. The login screen is at a completely different resolution (1280x1024) to what I've set on my desktop and the resolutions contained in xorg.conf (1024x768 @ 85Hz is what I'm used to).

I've tried using the free default Mesa driver and the ATI driver (which I am now using) but this makes no difference. I've attached my xorg.conf if I'm missing something obvious.

Thanks for your help,
Sam

---

### Post by Spamuel on 2006-07-22
No one got any suggestions? :(

---

### Post by ishimaru_kaito on 2006-07-22
I have this same problem, and I'm looking into it.  I am pretty sure it's got something to do with the conf files for Gnome, as my Desktop pc will have a login of 1600x1200 (on the limit of my monitor) and once logged in, I am using 1280x1024.  Give me a day or so, and I reckon I'll have it cracked!
Hopefully :???:

---

### Post by Spamuel on 2006-07-22
Ah I've fixed it :) 

I ran **sudo dpkg-reconfigure xserver-xorg** and made sure to select my preferred resolution along with the correct keyboard and video card drivers. Now everything is how it should be.

Maybe reconfiguring X edits more files than I was aware of, maybe someone with greater knowledge can enlighten us. :D 

Kind regards,
Sam

---

