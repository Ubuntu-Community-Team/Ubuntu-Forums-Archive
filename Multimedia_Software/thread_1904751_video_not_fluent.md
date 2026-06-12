---
title: "video not fluent"
date: 2012-01-05
forum: Multimedia Software
---

### Post by debili on 2012-01-05
hi all,

I've just build a new workstation replacing my old box where I've experienced problems with video, well not only video. by playback it's not fluent, like tearing.. the picture is torn in half in the middle or in other words, i see a line. same if i move windows accross the desktop quickly. 

well i've finished with my new machine with new hadrware lik the i72600k processor and i'm experiencing the same!  i'm still using the same videocard as in the old system nvidia gt520silent, could this be related to the videocard??? I've read a lot of posts about settin up your compiz, sync to v-blank and so on but nothing seems to help...getting crazy.

does anybody have these problems on their systems?

thank you all

---

### Post by WienerWuerstel on 2012-01-05
hi deblii,

Do you use Totem to watch your Videos? I heard a lot of People have problems using this Video Player and I suggest to you that you try SMPlayer. SMPlayer is far better than Totem and also supports VDPAU which let's the Graphics Card do the dirty work. 


Use this Command to install it:
```
sudo apt-get install smplayer libvdpau1
```

---

### Post by debili on 2012-01-05
> **WienerWuerstel said:**
> hi deblii,

Do you use Totem to watch your Videos? I heard a lot of People have problems using this Video Player and I suggest to you that you try SMPlayer. SMPlayer is far better than Totem and also supports VDPAU which let's the Graphics Card do the dirty work. 


Use this Command to install it:
```
sudo apt-get install smplayer libvdpau1
```

hi, thank you! but i don't think it's related to a video player as it happens both on the desktop (wen moving windows for example) and on flash played from the web.. also in smplayer.. it's driving me nuts

---

