---
title: "pulsaudio equalizer woes"
date: 2019-02-01
forum: Multimedia Software
---

### Post by boldfish2 on 2019-02-01
HI I cannot seem to add pulsaudio equalizer. I have read lots and lots about changing your sources list file to add new sources but tinkering with this can break your distro so I am stumped . the error i am getting when I try to add the ppa is Failed to fetch [http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
. The threads opened on this are not very useful at all to a newb.

---

### Post by howefield on 2019-02-01
That particular PPA appears to have become defunct with repositories only available for 14.04, 14.10 and 15.04.

[https://launchpad.net/~alex-wv/+archive/ubuntu/pulseaudio-equalizer-ppa](https://launchpad.net/~alex-wv/+archive/ubuntu/pulseaudio-equalizer-ppa)

Which tutorial / website are you following ?

---

### Post by Autodave on 2019-02-01
Please keep in mind that everyone here is volunteering: there are no paid positions.

---

### Post by slickymaster on 2019-02-01
Thread moved to **Multimedia Software** for a better fit

---

### Post by mc4man on 2019-02-01
In 18.04 and newer there is a pulseaudio-equalizer package available in standard Ubuntu repos. You'd need to edit /etc/pulse/default.pa to actually use it as outlined here
[https://askubuntu.com/questions/980876/how-do-i-start-pulseaudio-equalizer](https://askubuntu.com/questions/980876/how-do-i-start-pulseaudio-equalizer)
Once you do as noted in the accepted answer it should start up.  Most likely is to add those 2 lines to end of the file. (as root
You can manually create some presets in it's toolbar., screenshot

A more expansive and configurable option would be to use pulseaudio effects. Page here
[https://github.com/wwmm/pulseeffects](https://github.com/wwmm/pulseeffects)
It's actively maintained and has packages for 18.04/18.10 in a ppa as noted in above page.

---

