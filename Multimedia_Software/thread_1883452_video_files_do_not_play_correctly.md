---
title: "video files do not play correctly"
date: 2011-11-19
forum: Multimedia Software
---

### Post by kurja on 2011-11-19
Any videofile does not play correctly, there's a bright green "interference pattern" over the image. Other than that, they work. It's the same thing with Lucid's default player and vlc, and I'm using the default video drivers with an ati 9600 card. Youtube etc videos do not exhibit this problem, just any local video files.

Any ideas..?

---

### Post by WasMeHere on 2011-11-19
Hi kurja,

Try to install good software and codecs etc according to the
[[COLOR="RoyalBlue"]_Comprehensive Multimedia & Video Howto_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Have fun finding out about Ubuntu :-)
Olle

---

### Post by kurja on 2011-11-19
> **Olle Wiklund said:**
> Hi kurja,

Try to install good software and codecs etc according to the
[[COLOR=RoyalBlue]_Comprehensive Multimedia & Video Howto_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Have fun finding out about Ubuntu :-)
Olle

Tack så mycket Olle,

I'll try that. However, I would have expected to be able to play the most ordinary video formats without needing to install anything, is this usual with ubuntu?

---

### Post by kurja on 2011-11-19
update - I followed those instructions and apparently installed a ton of stuff half of which I won't need and the other half of which I don't even know what that stuff is, and video playback is just as before :^/

---

### Post by WasMeHere on 2011-11-19
Due to the distribution method of Ubuntu and licensing limitations of multimedia software it is not possible to include into the installation disks or iso files. I think one important reason is that computers can be sold with Ubuntu installed. But as end user you can download it (more or less?) legally.

Other flavours of linux need not follow this restriction if the only way of distribution is via downloading to end users. For example Linux Mint, which is based on Ubuntu, includes a good collection of libraries and codecs in the iso files.

Sorry that it did not help you. Then there is some other problem. Maybe the computer is too slow in combination with your software.
- What computer is it?
- What Ubuntu version (10.04, 11.04, 11.10)
- What Ubuntu flavour, 'vanilla' Ubuntu, Kubuntu, Lubuntu, Xubuntu ...?
- Have you tried to run a proprietary graphics driver for your card (nota bene linux specific)?

Browse the Ubuntu Forums for ATI drivers!

---

### Post by kurja on 2011-11-19
> **Olle Wiklund said:**
> Due to the distribution method of Ubuntu and licensing limitations of multimedia software it is not possible to include into the installation disks or iso files. I think one important reason is that computers can be sold with Ubuntu installed. But as end user you can download it (more or less?) legally.

Other flavours of linux need not follow this restriction if the only way of distribution is via downloading to end users. For example Linux Mint, which is based on Ubuntu, includes a good collection of libraries and codecs in the iso files.

Sorry that it did not help you. Then there is some other problem. Maybe the computer is too slow in combination with your software.
- What computer is it?
- What Ubuntu version (10.04, 11.04, 11.10)
- What Ubuntu flavour, 'vanilla' Ubuntu, Kubuntu, Lubuntu, Xubuntu ...?
- Have you tried to run a proprietary graphics driver for your card (nota bene linux specific)?

Browse the Ubuntu Forums for ATI drivers!
This is a desktop PC, with Lucid 10.04, my GPU (radeon 9600) is no longer supported by the proprietary drivers. I can view those same videos just fine if I use Windows. The thing is that the videos open up in the player(s) just fine, I get audio and everything seems otherwise ok except that colors are somehow "off" and there's this weird bright overlaid "noise pattern".

---

### Post by WasMeHere on 2011-11-19
Bra då vet jag lite mer om varför och hur det inte riktigt fungerar, kurja!

Have you tried with different screen resolutions and/or refresh rates? 

Would it be worth trying Ubuntu Studio with the real time kernel?

Have you any experience of other linux variants? For example Knoppix is known to be good at recognizing hardware. Maybe you can find some success story about linux and your graphics card on the internet?

If you have the time, try several linux flavours from live CDs or USB drives!

Have fun finding out :-)
Olle

---

### Post by kurja on 2011-11-19
ta det lugnt, min svenska är mycket begränsad ,)
 
I have another gpu card that I can try, it is a newer model and still supported by ati's proprietary driver so if it works or not with that card we'll know more of what's afoot here. Video playback is not a high priority thing for me so I'll refrain from further experiments untill I've tried that other gpu, I'll post back then (that'll be next week).

---

### Post by kurja on 2011-11-25
> **kurja said:**
> ta det lugnt, min svenska är mycket begränsad ,)
 
I have another gpu card that I can try, it is a newer model and still supported by ati's proprietary driver so if it works or not with that card we'll know more of what's afoot here. Video playback is not a high priority thing for me so I'll refrain from further experiments untill I've tried that other gpu, I'll post back then (that'll be next week).

I installed a new ati 3450 agp card, and now videos are intereference pattern-free. Playback is not unproblematic though, there's occasional stutter. Also, I can't get 3D acceleration. Drivers... sigh. If anyone has used this card with Lucid and has been able to get 3D acceleration, I'm all ears.

---

### Post by WasMeHere on 2011-11-26
> **kurja said:**
> I installed a new ati 3450 agp card, and now videos are intereference pattern-free. Playback is not unproblematic though, there's occasional stutter. Also, I can't get 3D acceleration. Drivers... sigh. If anyone has used this card with Lucid and has been able to get 3D acceleration, I'm all ears.

If you switch to the XFCE or LXDE desktop with smaller footprints, you might get rid of the stutter. One way is to install the desktop(s) into Lucid, and select session at login
```
sudo apt-get install xubuntu-desktop
``` or
```
sudo apt-get install lxde
``` another (longer but 'cleaner') way is to make a fresh install of Xubuntu or Lubuntu.

It's easy to install XFCE or LXDE (and remove them if they won't help you) or to test Xubuntu or Lubuntu from a live CD or USB drive.

---

### Post by AlexDudko on 2011-11-26
Have you tried some other software? I have seen the same behavior in Fedora-16 but it occurs only in Totem (didn't try vlc), but other players work just fine.

---

### Post by kurja on 2011-11-26
> **AlexDudko said:**
> Have you tried some other software? I have seen the same behavior in Fedora-16 but it occurs only in Totem (didn't try vlc), but other players work just fine.

I saw no difference when I tried vlc. Now I've put back the X.Org radeon drivers, and now videos seem to play, shall we say, sufficiently.

Only now I can't get any 3d acceleration. Playing UFOai with the older card I got a semi decent 40-50fps with all the fancy shadings etc turned off (not that the game would have actually worked with them on), but now I'm getting less than 10fps - even as it is a turn based game, that's just horrible. I started another thread about it though, [http://ubuntuforums.org/showthread.php?t=1886853](http://ubuntuforums.org/showthread.php?t=1886853)

---

### Post by sudodus on 2011-11-26
Try LXDE! This desktop interface is lightweight and allows more of your computing power to your applications.

---

### Post by kurja on 2011-11-26
> **sudodus said:**
> Try LXDE! This desktop interface is lightweight and allows more of your computing power to your applications.
Thanks for the tip, but wouldn't I be treating the symptoms instead of the problem?

---

### Post by WasMeHere on 2011-11-26
> **kurja said:**
> Thanks for the tip, but wouldn't I be treating the symptoms instead of the problem?
Well, yes you are right,but it might help until you find a good driver for your graphics card. If you 'only' install LXDE as an extra desktop environment, it costs very little to try.

---

### Post by kurja on 2012-01-06
I just noticed that *some* files do play correctly, weird thing is that a file that does play correctly is a "dv avi" file from a video camera while other similar files do not play correctly. Is there a tool that shows me which codec a file needs/uses? Because I think that this is a codec issue.

---

### Post by WasMeHere on 2012-01-13
Normally the video players show what codec is used (there is a menu entry for it). Often the file browser (***Nautilus***) can display it too (right click on the file and select properties ...)

You can also find it running ***mplayer*** or ***ffmpeg*** from the command line while playing or trying to convert. Both of these tools can manage a lot of encodings (codecs). Also ***vlc*** can manage a lot of encodings. I hope that at least one of these tools can manage your files.

---

