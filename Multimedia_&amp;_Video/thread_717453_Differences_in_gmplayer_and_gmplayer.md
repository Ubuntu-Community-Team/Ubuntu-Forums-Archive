---
title: "Differences in gmplayer and gmplayer"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by akwatve on 2008-03-07
I was assuming that gmplayer is just mplayer with GUI support. But I think there something thats broken/not working properly in gmplayer.
Last few weeks I have been experimenting with various audio and video plugins. What I observed is mplayer-nogui is much elegant in handling different ao and vo plugins. In many cases gmplayer just hangs or crashes with unhappy error messages.

For example,

1) when I use pulse as the output audio plugin, gmplayer refuses to recognize it. so i dont get any sound.
But If I replace gmplayer with old fashined mplayer and invoke mplayer -ao pulse XYZ, it works sweetly.

2) Xvideo does NOT work in BOTH despite having installed libxv1 (both binarya as well as dev) packages. (note: i installed dev package becoz someone advised to do so in one of the threads)
But becoz -vo xv fails in both versions of mplayer and I am using proprietary drivers, I am assuming there is something else to the problem than just mplayer configuration

3) When I try to use gl or gl2 as video plugin, gmplayer just HANGS. Most of the times it does not give any error message. It just stops responding and kill -9 remains the only way to kill it. On the other hand, Sometimes gmplayer throws and error message "could not allocate buffer. expect a major speed penalty"

Can anyone shed some light on whats happening here? As far as my videos are considered, I can play them with vlc so I am not really bothered about the problems. But I want to understand whats wrong and also want to document my experience with mplayer.

Thanks,

P.S. With -vo x11 option if i play the video in full screen, it does not stretch the image but simply paints rest of the screen black. Is this default behavior ? Or is there any way to explicitly tell mplayer to stretch the image ?

mplayer again handles both gl and gl2 without any problem.

---

