---
title: "Video stabilisation for Ubuntu (deshaking), can be a CLI"
date: 2021-06-27
forum: Multimedia Software
---

### Post by mkoniecz on 2021-06-27
What would be the best way to remove shakiness from video? I am fine with using CLI

I found:

- [https://ubuntuforums.org/showthread.php?t=1875543](https://ubuntuforums.org/showthread.php?t=1875543) (without answer)
- [https://askubuntu.com/questions/19095/video-stabilisation-software](https://askubuntu.com/questions/19095/video-stabilisation-software) (uselessly ancient, I hope that something better was created in meantime, any new question would be closed as duplicate)
- [https://askubuntu.com/questions/228841/what-ubuntu-compatible-software-is-available-to-remove-shaking-from-a-video](https://askubuntu.com/questions/228841/what-ubuntu-compatible-software-is-available-to-remove-shaking-from-a-video) managed to get answer before closure, but is missing info how can I actually install it
- [https://www.imakewebsites.ca/posts/2018/02/17/stabilizing-gopro-video-with-ffmpeg-and-vid.stab/](https://www.imakewebsites.ca/posts/2018/02/17/stabilizing-gopro-video-with-ffmpeg-and-vid.stab/) mentions --enable-libvidstab But I get "unrecognized option '-enable-libvidstab'.
- [https://theswitch.boards.net/thread/10146/using-ffmpeg-linux-stabilizing-shaky](https://theswitch.boards.net/thread/10146/using-ffmpeg-linux-stabilizing-shaky) recommends adding random ppa and is for 18.04
- [https://video.stackexchange.com/questions/19089/youtube-like-video-stabilization-on-linux](https://video.stackexchange.com/questions/19089/youtube-like-video-stabilization-on-linux) deshake was not helpful at all, shakiness remained

---

### Post by mkoniecz on 2021-06-28
See [https://user-images.githubusercontent.com/899988/123581713-bedf1500-d7dc-11eb-8342-933db99da7f2.mp4](https://user-images.githubusercontent.com/899988/123581713-bedf1500-d7dc-11eb-8342-933db99da7f2.mp4) for an example of what I want to unshake

---

### Post by Holger_Gehrke on 2021-06-28
'--enable-libvidstab' is not an option to ffmpeg but an option to 'configure' if you're installing ffmpeg from source. You can see what options were given at that stage by calling ffmpeg from the command line without any options or arguments. The ffmpeg in the repositories was compiled without that option.

Holger

---

### Post by steve234 on 2021-07-01
Shame deshake didn't work for you, I had good results with that on mountain bike footage.

Try Blender, there are plenty of tutorials for stabilisation - using single or double point tracking IIRC. No reason that wouldn't work for your laser cutter footage

---

### Post by steve234 on 2021-07-02
So, I've tried blender on your clip following [this 6 minute tutorial]("https://www.youtube.com/watch?v=982RL4a899g") and found some improvement. It still retains a bit of zoom, but I imagine that could be fixed by trying different markers, and playing with the autoscale setting.

[Here is the result]("https://github.com/thephatmaster/blender_stabilisation/blob/main/Laser_cutter_stabe0001-0316.mkv").

---

### Post by mkoniecz on 2021-07-31
> **steve234 said:**
> So, I've tried blender on your clip following [this 6 minute tutorial]("https://www.youtube.com/watch?v=982RL4a899g") and found some improvement. It still retains a bit of zoom, but I imagine that could be fixed by trying different markers, and playing with the autoscale setting.

[Here is the result]("https://github.com/thephatmaster/blender_stabilisation/blob/main/Laser_cutter_stabe0001-0316.mkv").

Thank you very much! I used it on my site, it is good enough (and I probably should take a better video than with a potato quality smartphone).

---

