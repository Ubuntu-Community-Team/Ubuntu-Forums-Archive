---
title: "Cant get 3DFX Voodoo Card to work...."
date: 2006-04-27
forum: Multimedia &amp; Video
---

### Post by azmansell on 2006-04-27
Hi there, i have ubuntu running on an old pc (celeron 733) which has an onboard 2mb graphics card but also has a 3dfx voodoo 3 card card installed (i think its 8 or 16mb)

Ive been trying to get the voodoo card working but cant seem to do it although it shows up in devices.

i have tried to change the default graphics card in the bios and swapping the monitor from the onboard to the voodoo proir to loading up but this gets half way through loading then i am left with a blank screen.

Do i need to install driver for this?

cheers in advance!

---

### Post by kostkon on 2006-04-27
Hi azmansell,

when you get the blank screen when you try to boot with the voodoo card. I mean, do you see anything of ubuntu, like the loading screen with the splash image? Do you get instead of the gdm a blank screen, is that what you mean?

If that is the case, it looks like a driver problem to me.

Boot in recovery mode and follow this from the wiki:

[https://wiki.ubuntu.com/Voodoo3doesnotdo3d]("https://wiki.ubuntu.com/Voodoo3doesnotdo3d")

---

### Post by azmansell on 2006-04-29
Hi there,
the problem has changed slightly since the last time i tried to use it. now it tells me that the settings are incorrect and lands me at the command prompt. luckily i backed up my xorg.conf file, so ive managed to get everyting back to normal....still no voodoo though.

should my voodoo just plugin and work or have i got to set it up properly?(i followed a lengthy tutorial and the above is the result, unfortunately i cannot find the tutorial to paste in)

---

### Post by Aramil on 2006-04-29
I have the exact same card although with a slower processor.My problem is that when i trie to change my Screen'resolution the only choice that I have is 640x480.This is not possible because when i was running Win98 I used 800x600 .I tried to reconfigure xorg but it seems that I m doing something wrong so i restored my original settings..Can anybody help me?

---

### Post by Dgudaitis on 2006-05-01
this is the same problem I have.  I am testing out Ubuntu on an older PC with a voodoo 3 video card.  I can only get 640x480 res.  I have looked at the wikiubunto site and the directions looks pretty challenging. [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)  

 Is there an easier way?  I mostly live in a mac world and command line entry seems foreign now.

---

### Post by ramday on 2006-05-08
I'm having this problem as well only its with a Voodoo 5500 AGP. When I use the card in windows I can go up to 1600 by 1200. I am assuming we need to install drivers for the card manually because Ubuntu does detect the card during installation.


[QUOTE=Aramil]I have the exact same card although with a slower processor.My problem is that when i trie to change my Screen'resolution the only choice that I have is 640x480.This is not possible because when i was running Win98 I used 800x600 .I tried to reconfigure xorg but it seems that I m doing something wrong so i restored my original settings..Can anybody help me?[/QUOTE]

---

### Post by Barronmore on 2006-05-12
I also have a voodoo 5500 64meg graphics card and I'm having problems with it..  I've installed Kubuntu and I can get all the way up to where KDE would inititate and I just see a blinking bar at the top of my monitor.  

I'm running a Dell OptiPlex GX110 with 256 MB of ram and a 4MG onboard video card. I would just go back to the onboard Video Card but it does the same thing as the Voodoo.  Right now I'm actually using this machine with a MempisLIte Live CD but even that took awhile to kick in.

Does anyone have any suggestions to get this card to acutally boot Kubuntu or even get back to my 4meg card?  

Thanks

---

