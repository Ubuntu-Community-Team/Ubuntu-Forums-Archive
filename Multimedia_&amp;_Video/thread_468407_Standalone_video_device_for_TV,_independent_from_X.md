---
title: "Standalone video device for TV, independent from X desctop"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by kostos on 2007-06-08
Hi guys, 
couple months ago i've got an idea to make more or less functional  media center from my desktop and switched from windows to kubuntu. The idea was to make implementation transparent for user - i want TV/VCR appearing like TV and behave like TV/VCR, with no worrying that the PC is stay behind it. I mean interface must be simple and i do not want user to log in to to X, start something there, and have playback terminated if i'will login into desktop or reload X server or switch to console mode etc. 

Therefore wanted to get full control over my hardware to have TV-output present in the system as standalone graphical device controlled  independently from desktop's monitor, lets say independent direct framebuffer(?). Sure, you will agree that TV used for watching video rather working as second monitor, may be considered as separate device and it not need to run windows managers and desktops.  

But i found no way to configure my GF6200 SE to appear in the system as two separate devices: TV and monitor. I had no problem with installing NVidia drivers and getting TV working on separate X-screen, but i had no chance to find any advise or ready solution how to split videocard to two devices. 

Is it possible in principle? I've searched trough internet, but never met solution described above, regardless would it based on NVidia or any other card or two different cards..

Is it possible in practice in reasonably cheap hardware configuration? If you can refer some project where it implemented, could you please share URL - probably example could help me to set configuration needed.

---

### Post by rklauco on 2007-06-10
Well, don't know if it helps, but...
I made different solution. Ultra quiet PC with no moving parts - old laptop with CPU fan turned off, running [Geexbox]("http://geexbox.org/en/index.html") on it from old 128MB flash drive and connected to main server using ethernet.
Also, the laptop has an MS MCE remote, so it acts as a usual media center. The USB TV card works just fine, the only thing it does not provide s recording.
But it is totaly quiet and works independently from my workstation.

In the second room, where server is located, there is usual Ubuntu distribution acting as data server/tv recorder and running [freevo]("http://www.freevo.org") on it.

Not realy an answer to your question, but maybe a step ahead in the effort...

---

### Post by kostos on 2007-06-13
Hi rklauco,
using standalone PC as Ethernet-shared TV-OUT is not too bad workaround, i feel i will managed at the end to replace old dvd-player by my piii which is mostly used for backup  purpose now and this ready to use solution will useful for that. 

But anyway it is still interesting to have in the system video devices independent from X. As minimum it will increase utilisation of resources of modern desktop and decrease number of computers in home network.

---

