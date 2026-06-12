---
title: "Which nvidia driver to I have/need?"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-25
Can anyone with a GeForce 6200 tell me
1) what drivers they're using
2) which way they installed them
3) what their xorg.conf looks like
4) what o/p they get from **glxgears -printfps**
5) what [K|X][Uu]buntu version they're using?

Or just generally how to see which nvidia driver version I'm using and how to decide which one
best suits my card?

Thanks,
P

---

### Post by pandu.rs on 2006-12-25
I have a Geforce 6200 and it works fine for me with dapper (it should work with edgy too, but i have not tried it)

I followed the instructions from 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by pickarooney on 2006-12-25
I'm using Edgy.
Can I see your xorg.conf, the video device section?

---

### Post by pandu.rs on 2006-12-25
Section "Device"
  identifier "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
EndSection

---

### Post by pickarooney on 2006-12-25
hmm, actually can you post the whole thing, just so I can copy it and reset X, test glxgears?
I noticed my card is autodetected as NV40 whereas everyone else with this card seems to have NV44

---

### Post by pandu.rs on 2006-12-25
here it is

I am using dapper. In any case i recommend u to take a backup of ur xorg.conf

---

### Post by pickarooney on 2006-12-25
Thanks. I tried it and it improved things ever so slightly, mostly because the TV-out option was disabled. Changing the resolution of the TV in my own xorg.conf gave me the same boost, from 600-800 fps, but that's still only about a third of normal speeds I think.
The driver I'm using seems to be 1.0-9631. Maybe I'll try with an older one.

---

### Post by pickarooney on 2006-12-25
Just wondering now if people aren't squishing the output window to the minimum when testing with glxgears. I can get 6000+ if I do that, but am back to 600 in the standard window size, 18 in fullscreen.
I tried globs and got results of about 100-200fps for most of the tests, but have no idea if that's good or bad.
Google-earth now starts up and displays OK, but as soon as I try to zoom in anywhere the system crashes.

Tux-racer makes everything crash also.

Anyone recommend a decent driver version or tweak to make things a bit more stable?

---

### Post by pickarooney on 2006-12-26
pandu.rs, can you check in the nVidia settings what driver version you're using? I reckon the one I have is not compatible with this card.

---

