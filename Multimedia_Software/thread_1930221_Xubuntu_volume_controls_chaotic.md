---
title: "Xubuntu volume controls chaotic"
date: 2012-02-23
forum: Multimedia Software
---

### Post by aquabanianskakid on 2012-02-23
I have an odd problem with the sound on my Xubuntu 11.10 installation. If headphones are plugged in I can control the volume using the physical volume buttons on the laptop but cannot use the volume controls in the system tray. If the headphones are not plugged in then the physical buttons don't work and I have to configure the volume from the system tray. It seems like the controls are each assigned to one volume output instead of the master volume like they usually would be. Any ideas on how to fix this? I tried searching for a solution but honestly I couldn't even think of a simple search term for this problem.

---

### Post by LewisTM on 2012-02-23
Xubuntu uses the ALSA mixer while volume in Ubuntu is controlled by Pulseaudio.
That can give rise to some conflicts.
One thing you can try to reconcile them is to create file /etc/asound.conf with the following contents:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```
That will redirect the ALSA mixer to control Pulse devices.
Hope this helps!

---

### Post by aquabanianskakid on 2012-02-23
That kind of worked. I still have a problem. The volume buttons and volume application in the system tray are both effecting the output volume of the headphone jack, but they are still functioning independently as if one is controlling the headphone jack directly and the other is controlling the master volume. If I unplug the headphones the volume won't adjust using the physical buttons. Only the sound dialog in the system tray. So I'm assuming the system tray is controlling the master volume and the physical buttons are controlling the individual volume.

---

### Post by videodrome on 2012-02-23
Xfce has a weird bug I've noticed over the years regarding the volume tray applet.

Instead of left-clicking on the tray volume applet to bring up the window with the controls in it, instead right-click on it and select "properties."

Now where it says "sound card" hit the drop-down menu and select something other than what is already selected. 

Then, select it back to where it was.

This always fixes it for me.

---

### Post by aquabanianskakid on 2012-02-23
I'm using xubuntu 11.10, it doesn't seem to have any kind of right click dialog. I have tried switching back and forth in the sound settings though and nothing has changed.

---

### Post by LewisTM on 2012-02-23
> **aquabanianskakid said:**
> I'm using xubuntu 11.10, it doesn't seem to have any kind of right click dialog. I have tried switching back and forth in the sound settings though and nothing has changed.
I think aquabanianskakid is using the sound indicator plugin, not the Xfce mixer panel item. That's what's installed by default in Xubuntu.
You can try to use Xfce mixer in your panel instead and see if that helps. It controls ALSA while the indicator controls Pulseaudio. Both can be modulated by using the mouse wheel, a handy shortcut.
If you find that you no longer need the sound indicator, just remove the indicator-sound-gtk2 package.
Removing Pulseaudio would also take care of that. If you do, just remember to remove/rename your custom /etc/asound.conf as well.

Cheers!

---

### Post by aquabanianskakid on 2012-02-23
I went ahead and removed pulseaudio to simplify things a bit and decided to give the XFCE mixer a try. I'm still having the same problem. It looks like I just need a way to tie both the speaker and headphone volume to the physical volume buttons on the computer. I can still adjust the headphone volume with the physical buttons but I still have to open mixer to adjust the speaker volume. Strange, it seems like it would be fairly easy to tie the headphone and speaker volume together. Thanks for all the advice so far.

---

### Post by LewisTM on 2012-02-23
Okay, so let's set the physical buttons manually:

1) Disable the XFCE volume daemon from your application autostart list. You're going to take care of what the daemon does, and probably does wrong

2) Add two new application keyboard shortcuts for Xfce:
```
amixer set Master 5%+ #Volume up
amixer set Master 5%- #Volume down 
```
Bind them both to your respective multimedia keys.
You can test the commands in a terminal first to make sure they work.

3) If it works, you can try to re-enable the daemon to see if it conflicts with your new shortcuts. Without the daemon, you won't see volume notifications, although you'll still hear the change.

---

### Post by aquabanianskakid on 2012-02-23
It works if I use PCM in place of master. Is it possible to assign two commands for one button? I tried ```
amixer set Headphone 5%+ #Volume up && amixer set Speaker 5%+ #Volume up
``` Sadly it didn't work. I would like to set it so I can raise or lower the volume for both the headphones and the speaker instead of the PCM volume.

---

### Post by LewisTM on 2012-02-23
> **aquabanianskakid said:**
> It works if I use PCM in place of master. Is it possible to assign two commands for one button? I tried ```
amixer set Headphone 5%+ #Volume up && amixer set Speaker 5%+ #Volume up
``` Sadly it didn't work. I would like to set it so I can raise or lower the volume for both the headphones and the speaker instead of the PCM volume.

Try something like that as a keyboard shortcut
```
sh -c "amixer set Headphone 5%+ && amixer set Speaker 5%+"
```

---

### Post by aquabanianskakid on 2012-02-23
PERFECT! That did the trick. Thanks for your help. This was such an odd problem I was a little worried that no one would know of a solution.

---

