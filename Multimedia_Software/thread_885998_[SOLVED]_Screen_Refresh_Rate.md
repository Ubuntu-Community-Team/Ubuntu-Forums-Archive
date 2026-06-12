---
title: "[SOLVED] Screen Refresh Rate"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Alexander-GG on 2008-08-10
Hi all,

I have NVIDIA GeForce 5200 FX card and Samsung SyncMaster 943NW LCD monitor. The normal (recomended by the manufacturer) refresh rate for my monitor is 60HZ (maximum 75HZ). When I installed the NVIDIA driver (offered by UBUNTU) it set my monitors refresh rate to 50HZ and I'm not able to change it. I have tried everything. I installed the NVIDIA settings manager too, but it works until next boot and it shows that I have CTR monitor instead of LCD. Then I tried to change xorg.config. Do not tell me that it works. I set refresh rate to 60HZ (as it was expalind in several posts that I found) but now Ubuntu monitor settings manager shows refresh rate 90HZ.

I have no idea what to do. The only Linux which can properly detect the monitor type and refresh rate is Mandriva (I have tried almost all linuxes), but I don't like the KDE interface and Mandriva has not a good support for my country. Besides, I used to Ubuntu and I think it's the best Linux with Gnome desktop.

Maybe someone knows how to set proper refresh rate in Ubuntu? Please, help me.

---

### Post by Alexander-GG on 2008-08-16
Well, I'm back to Windows. I will try Ubuntu once again in Octomber, when the new version will be available.

---

### Post by perlluver on 2008-08-16
Well if you are still here, did you try installing nvidia-settings in Synaptic, and setting the refresh rate through there?  Sorry the help came late, but I hadn't seen the post before.

---

### Post by Alexander-GG on 2008-08-17
Sure, I installed nvidia-settings manager, but it works until next boot and also it shows that I have CTR monitor instead of LCD. When I set the proper resolution and refresh rate in nvidia-settings manager, than ubuntu screen or monitor manager shows me the different refresh rate. I tryed almost everything. I have no idea, if Mandriva Linux One can determine everything properly, why it's so hard to implement the same teqhnology in Ubuntu?

Thank you for your comment. But, now we have a war in the country and it's very hard to think about other things. Thank you!

---

### Post by Krydahl on 2008-08-17
Yeah, mine shows 50Hz - I did some research though, and as far as I can make out, with an LCD the refresh rate is pretty meaningless anyhow. When you change it to 60, can you actually see any difference in video performance?

---

### Post by z0mbie on 2008-08-17
You need to add the following line under subsection **Screen**, see below for example context for 60Hz refresh rate:

```
SubSection     "Display"
        Depth       24
**        Modes      "1280x1024[COLOR="Red"]_60[/COLOR]" "1024x768" "800x600" "640x480"**
 EndSubSection
```

---

### Post by Alexander-GG on 2008-08-18
My monitor is 1440x900 wide. I Made the proper changes to xorg.config, but it's don't work.

---

### Post by ZarathustraDK on 2008-08-18
I have the same problem. Nvidia 7800GT.

nvidia-settings stick until next reboot. Then it's back to 50 Hz. It's quite visible when running compiz and moving windows, spinning the cube etc.

I've had the problem since...well...forever. Think I heard once that it has something to do with the Gnome-guys and the Compiz-guys not being able to agree with who's fault it is, I could be wrong though.

If only it was a matter of setting nvidia-settings as a startup-process, but alas, gnome has lost the ability to set startup priority for programs, at least in the Sessions-tab. Don't know if there's some other way to do it. Wont matter much though I think, nvidia-settings defaults to "auto-select" (50 Hz) whenever you restart. Quite a pickle, wish they'd fix it.

---

### Post by Alexander-GG on 2008-08-20
You know, I tried to remove nvidia card from PC. Without nvidia card Ubuntu detects the screen resolution and refresh rate perfectly, but without nvidia card compiz doesn't work.

---

### Post by Alexander-GG on 2008-08-20
No, it's almost impossible to see any difference between 50HZ and 60HZ. But, if you are typing some documents or if you are making some other work on PC which takes a lot of time, your eyes will be tired very soon.

---

### Post by Krydahl on 2008-08-20
I don't believe so.

An LCD monitor does not flicker, regardless of what the refresh rate is. It has a backlight that is on constantly so there is unlikely to be an impact on eye strain. If your eyes are getting tired, look at your contrast and brightness settings.

I've read claims that, when gaming, refresh rate can make a difference if you graphics card is pumping out high fps. Effectively, the fps becomes limited to the refresh rate. I've also read claims that there are some odd interactions with VSync and refresh rate at high fps causing tearing but I can't find a particularly authoritative source for these - just opinions on various forums.

---

### Post by lian1238 on 2008-08-20
Try playing with the refresh rate for compiz. Run ccsm and under General Options -> Display Settings, UNcheck Detect Refresh Rate. Then put 200 as the Refresh Rate. You can try putting it very low, like 10 and see if the settings is taking effect. If not, restart compiz with the command ```
compiz
```or the command you normally use. With LCDs, a low refresh rate doesn't cause the screen to flicker. 

When typing, try zooming in or increasing the font size so your eyes aren't in overdrive. You can increase the system font size by going to System->Preferences->Appearance (or rightclick on desktop -> Change Desktop Background). Then go to Fonts, Details and increase the Resolution.


Remember to take a break once in a while. I use the "Take a Break" feature from the Keyboard Preferences. I set it to 60 mins which is a good amount.

---

### Post by Alexander-GG on 2008-08-22
Thanks a lot for the comments. I set my monitors brightness and contrast to minimal. My monitor has very high dynamic contrast - 8000:1. Sure, I'm making a breaks. 

But, I dont think that it's a big problem or it's very hard for Ubuntu team to work on this problem. This is just a some kind of bug. If other linuxes solved this problem (I mean Mandriva), why not do the same in Ubuntu? Tweaking of nvidia card in Ubuntu takes so many time and nerves that it negatively covers all positive sides of Ubuntu.

But, I love Ubuntu and I hope the next version of Ubuntu will be without this bug.

---

### Post by Wickd on 2008-10-19
Hi there had exactly this problem. Did you select 'Save to X Configuration File' after you set the resolution? that should take care of your resolution settings upon restart

Cheers

---

