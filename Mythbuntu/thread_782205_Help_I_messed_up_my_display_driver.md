---
title: "Help: I messed up my display driver"
date: 2008-05-04
forum: Mythbuntu
---

### Post by mixersoft on 2008-05-04
I had a working mythbuntu install, but i couldn't get widescreen 1680x1050 screen resolutions. So I went into the MCC xfce config applet and picked out the Intel i810 driver and my Dell 2005FPW display set to widescreen 1680x1050.

Now when I reboot, the screen goes to black at the end of the startup sequence.

I can still ssh to the server and reverse the changes, but what do I edit to make it work again? And what do I do about getting widescreen resolutions?

m.

---

### Post by SniperKIng on 2008-05-05
Which driver are u using? nvidia, ati?

If one of them then using alt+ctrl and f2 should get u to command line where using envy would allow u to reinstall the correct drivers for your system.

ps reading again i see u use the intel drivers. my bad.

---

### Post by mixersoft on 2008-05-05
what is envy? and by your msg, I assume that it doesn't work for the Intel 945GC IGP. Any other suggestions, or should I just reinstall?

---

### Post by SniperKIng on 2008-05-05
Envy is a godsend of a program lol, it automated to installation of both nvidia and ati video drivers and has saved my life on may occations :). i dont think it works for intel drivers no. Its probabily best to wait and see if someone replys here who uses intel as im sure they would know better then me.

Though if u dont have much installed, videos/ recordings etc i would just reinstall.

---

### Post by mixersoft on 2008-05-05
Thx. I can reinstall, it's not that big a deal for me. But I'm still stuck with the problem of getting 1680x1050 working with my Intel 945 IGP. Can anyone offer a suggestion?

---

### Post by GordonEndersby on 2008-05-06
Use ssh to log into your mythtv box from another machine on your network.
once logged in cd to /etc/X11
xorg.conf should have been backed up when you made your last change just copy the backup using sudo cp over the new xorg.conf that isnt working.
Look at the file dates using ls -al to work out which is the correct backup.

If the utilities such as ssh, cd, cp, sudo, ls and the xorg.conf for X11 are not known to you, read up about them on the net because you will need this background knowledge a lot to get mythbuntu working correctly.

Gordon

---

### Post by mixersoft on 2008-05-07
Thanks. That works, I got my desktop back. 

But i'm still stuck without widescreen resolutions on the xfce desktop. However, I also noticed that I can't start the mythTv frontend from this config (ubuntu server + apt-get install mythbuntu-desktop). 

Does anyone know if I need to add from ubuntu desktop -- because I get widescreen resolutions from gnome??

---

