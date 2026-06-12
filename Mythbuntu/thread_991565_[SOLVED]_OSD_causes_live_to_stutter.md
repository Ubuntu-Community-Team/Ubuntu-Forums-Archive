---
title: "[SOLVED] OSD causes live to stutter"
date: 2008-11-23
forum: Mythbuntu
---

### Post by laffinet on 2008-11-23
As the thread topic states, whenever the onscreen display comes up (changing a channel, displaying information) live TV stutters until the OSD is off again.

Any idea what I can do about this ? 

There is something mentioned [here]("http://www.mythtv.org/wiki/index.php/XvMC#OSD") but I don't quite understand what I'm supposed to do.

---

### Post by SiHa on 2008-11-24
Does it stutter the whole time the OSD is up, or just when it is fading?

You can disable the fade from your TV Settings -> OSD menu

---

### Post by dmfrey on 2008-11-24
Are you using a nvidia card?  Have you tried enabling XvMC?  If so, have you tried changing your playback profile to utilize XvMC?

---

### Post by Caps18 on 2008-11-24
I picked a simple black and white OSD with no fade.  There is still some transparency with my OSD, but it isn't as graphic intensive I guess.

---

### Post by laffinet on 2008-11-24
Thanks. XvMC is enabled.

Have picked another OSD which fixed it for now. 

Will play around with profiles when I get a bit more time.

---

### Post by jMon54 on 2008-11-25
I have the same issue as you - just out of curiosity, which OSD did you choose which worked?

---

### Post by laffinet on 2008-11-26
I'm not at home at the moment so can't check but I think it was called "mirror widescreen" or so.

Note: I have since discovered that this hasn't fully solved my problem, I still get the occasional stutter. Not as bad and as often, but still there. Might have to do some tweaking via profiles after all.

---

### Post by jMon54 on 2008-11-27
Well, for me I still suffered with the issue in HD.  After a bit of tweaking, I now have another major issue:

<code>
root@kubuntu:~# cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.
root@kubuntu:~#
</code>

I made a small change in my xorg.conf (Option "NVAGP" "3" had a "1") and now it works as it should.

---

### Post by laffinet on 2008-11-27
So you got rid of the stutter ? What settings are you using ?

---

### Post by gatecrasher on 2008-11-28
> **laffinet said:**
> So you got rid of the stutter ? What settings are you using ?

I just got rid of my stuttering with this setup in my xorg.conf:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"  
    Option "NVAGP" "3"                 
EndSection


```


I tried NVAGP 1 , but I could never get it to work. Then I used 3 and it worked. I never tried 2.

---

### Post by jMon54 on 2008-11-28
My xorg.conf is like the poster's above. I tried a few different OSDs and they all work flawlessly now.  Yay!

I also reinstalled the nvidia driver recommended by Envy.

And now I get this in konsole:

root@kubuntu:~# cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

I also reinstalled the nvidia driver recommended by Envy.

---

