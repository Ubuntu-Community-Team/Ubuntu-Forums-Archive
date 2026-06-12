---
title: "[SOLVED] Accidently installed Nvidia Driver --&amp;gt; I Lost Visual!"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by chinasteve2000 on 2007-11-08
Hey! I've never posted for help, but I find myself needy.

Somehow, I decided that since there was a Nvidia driver available in the System menu of Ubuntu Studio (Feisty) that I could just install it. Next time I turned on the computer, the Ubuntu Studio splash/loading screen comes up, but not Gnome Desktop. I hear the sound for entering my password/username, but then what's the use if I can see nothing? Can anyone help me revert back please???

Little did I think about what sound card I have...or DON'T have, that is. Is there a way to go back to the default video driver, or the last one I was using? Ubuntu Studio installed just fine and I've not been having any big problems.

Could anyone guide me through the steps I need to save my computer from my driver jam?


I have a Tecra 2100 that I got used and therefore couldn't get XP installed on it a couple years ago. After a year of tinkering, I learned to depend on Ubuntu and found it a great alternative.

I'm a user who types things in Terminal when other people tell me what I need, but I can't find myself around a file system with it yet. But I've been using Ubuntu for nearly 2 years, almost exclusively for one. I started with Breezy, loved Dapper, and I'm enjoying Feisty now. I am not interested in Vista at all. =;

Thanks for whatever help you can offer!

---

### Post by eye208 on 2007-11-09
> **chinasteve2000 said:**
> I hear the sound for entering my password/username, but then what's the use if I can see nothing?
When you hear the sound, press Ctrl-Alt-F2. A text mode terminal screen should appear. Log in and then enter

sudo dpkg-reconfigure -phigh xserver-xorg

This should detect your video card automatically and update the X.org configuration file accordingly. Depending on your setup you might be asked some questions about your monitor's resolution etc. When you are done with this step, press Ctrl-Alt-Del to reboot.

If the graphical login screen is still invisible after the reboot, press Ctrl-Alt-F2 and log in again, then enter

sudo dpkg-reconfigure -pmedium xserver-xorg

This time you will be given the option to bypass automatic configuration and choose the video card driver manually instead. If you are not sure about the type of video card, pick "vesa" from the list. This will work with any card. Press Ctrl-Alt-Del to reboot again. You should get a graphical login screen after the restart. Now you can use Restricted Drivers Manager to enable the accelerated driver for your video card, if available.

---

### Post by GunkaBob on 2007-11-09
Thanks eye208 - your suggestion worked for me, as I had the same problem.  I got into trouble when going into System->Preferences->Desktop Effects.  I received the warning about need to enable the NVIDIA accelrated graphics driver - apparently I don't have an NVIDIA card - as afterward I would boot with no video and may display would say "Out of range"

 I did have to default to the vesa video option as my video hardware was not automatically detected.  Guess I have to crack the case to see what I have.:KS

---

### Post by eye208 on 2007-11-09
> **GunkaBob said:**
> I received the warning about need to enable the NVIDIA accelrated graphics driver - apparently I don't have an NVIDIA card - as afterward I would boot with no video and may display would say "Out of range"
The out-of-range warning does not mean you are using the wrong driver, only the wrong resolution. You can fix that too by reconfiguring xserver-xorg. Just bypass automatic monitor detection and pick the supported resolution(s) from the list instead.

---

### Post by chinasteve2000 on 2007-11-12
> **eye208 said:**
> The out-of-range warning does not mean you are using the wrong driver, only the wrong resolution. You can fix that too by reconfiguring xserver-xorg. Just bypass automatic monitor detection and pick the supported resolution(s) from the list instead.

Thanks a lot Eye!

I tried your multiple options and couldn't get the Nvidia driver working (in case it could) and then switched to the vesa option. It worked fantastically...back to the old view of everything.

Thanks for your answer...it was right on target!

Sincerely glad to be back to normal,
Steve

---

