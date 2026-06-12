---
title: "WinFF installed, but..."
date: 2008-11-27
forum: Multimedia Software
---

### Post by patchin_house on 2008-11-27
*Karaj geamikoj!*

O.K., I know I'm missing something this day... I finally got WinFF installed, but it appears that I'm missing video conversion options -- and therefore missing the real transcoding goods. 

I must be if I can't transcode from raw DV to Xvid (AVI) or Ogg Theora... or do you think I should be using something else?

BTW, I tried transcoding with Kino. It'd be fine, if the sound didn't go out of sync midway...

Philip David, with the flap missing in his head
(Esperantists will know what that means)
2008.11.27

---

### Post by kostkon on 2008-12-01
> **patchin_house said:**
> *Karaj geamikoj!*

O.K., I know I'm missing something this day... I finally got WinFF installed, but it appears that I'm missing video conversion options -- and therefore missing the real transcoding goods. 

I must be if I can't transcode from raw DV to Xvid (AVI) or Ogg Theora... or do you think I should be using something else?

BTW, I tried transcoding with Kino. It'd be fine, if the sound didn't go out of sync midway...

Philip David, with the flap missing in his head
(Esperantists will know what that means)
2008.11.27
You need to install the version of *FFmpeg* that is provided by the [*Medibuntu* repository]("http://medibuntu.org/"). Add this repository to your software sources list (instructions on how to do it are [here]("http://help.ubuntu.com/community/Medibuntu")) and then install *FFmpeg*.

---

### Post by FakeOutdoorsman on 2008-12-01
> **patchin_house said:**
> *Karaj geamikoj!*

O.K., I know I'm missing something this day... I finally got WinFF installed, but it appears that I'm missing video conversion options -- and therefore missing the real transcoding goods. 

I must be if I can't transcode from raw DV to Xvid (AVI) or Ogg Theora... or do you think I should be using something else?
Are you saying your WinFF installed without any of the presets?  The version of ffmpeg in the repo is quite old and I believe the settings used in WinFF are designed for newer ffmpeg releases.
> **kostkon said:**
> You need to install the version of *FFmpeg* that is provided by the [*Medibuntu* repository]("http://medibuntu.org/"). Add this repository to your software sources list (instructions on how to do it are [here]("http://help.ubuntu.com/community/Medibuntu")) and then install *FFmpeg*.
There is no Medibuntu ffmpeg for Intrepid.  The stock repo ffmpeg doesn't support some formats.  To enable more you can use the ["unstripped" ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3") which are available in the Ubuntu multiverse repo.

---

