---
title: "Ubuntu 11.10: nVidia, TwinView, HDMI, stutter when scenes move fast"
date: 2011-12-21
forum: Multimedia Software
---

### Post by veroslav on 2011-12-21
Hi,

I have a small issue when watching videos on my 42' LCD TV that is connected to my computer through an HDMI connection.

I am running Ubuntu 11.10 (64-bit) and my computer specifications are as specified in my signature below. I am using proprietary nVidia driver and set the output preferences for my TV according to below (in nVidia Settings):

- VSync on and applied to TV
- Using TwinView, 1920x1080, 60 Hz, Clone, all set manually

When I watch a MKV video through the setup above on my TV, it works good until the camera in the movies starts moving fast in the scenes.

In these cases I experience a noticable stutter in the picture, mostly at the screen edges, and stutter progressively increases with the speed of the scene movement.

What could be the cause for this behaviour? I am suspecting the frequency set for the tv in nVidia-Settings (manually set to 60 Hz) but isn't that the default frequency for a LCD screen?

Thanks in advance!

Kind Regards,
Veroslav

---

### Post by veroslav on 2011-12-21
I forgot to mention that I use Gnome-Shell when watching videos on the TV through this setup, as I haven't managed to resolve the screen tearing compiz is causing when I use a Unity 3D session for this.

/Veroslav

---

### Post by boast on 2011-12-21
did the lag only appear once you started connecting your computer to the TV?

---

### Post by veroslav on 2011-12-21
Hi and thank you for your reply, boast.

I tried playing the same footage only on my computer monitor (LCD 23'') and it appears that it is the same problem there as well, mixed with a little bit of screen tearing, which I don't experience when watching on the TV. My computer monitor is connected through a DVI cable.

Any suggestion on what is causing the issue?

Kind Regards,
Veroslav

---

### Post by boast on 2011-12-21
I'd probably first start out with the video player. Is VDPAU being used? Did you try using mplayer and then VLC, or different kinds of players?

---

### Post by veroslav on 2011-12-22
Hi again boast,

I am not sure about VDPAU, I will have to check when I get back home later today. Do I have to install any extra packages in order to get VDPAU support? If I understand it correctly, it enables the hardware accelerated video playback?

I have used SMPlayer and the movie player (Totem I think) and I have observed same behaviour in both.

I used to use VLC player before but I found that it actually added even more stutter in the videos and even caused a horribly noticable lag in the playback. I mean, my hardware spec should be fine for this purpose (720p hd video playback) right?

I would also like to mention that I use a DVI/HDMI adapter for the signal from the video card into the TV, if it helps.

Thanks again!

Regards,
Veroslav

---

### Post by boast on 2011-12-22
(assuming you are using the nvidia binary blob)

in smplayer video settings you can select VDPAU as the codec method [img]https://tdb0.files.wordpress.com/2009/07/smplayer-vdpau.png[/img]

---

### Post by veroslav on 2011-12-23
Yes, that is where I selected it yesterday, in SMPlayer. Here are the results :)

SMPlayer: In VDPAU mode, the stuttering has improved, perhaps some tearing has been instroduced in the fast paced scenes but I can live with it. The only problem I have with SMPlayer (and had it before) is that few times during the playback, the picture just freezes for a second (sound continues) and then continues playing, minor issue, but I am only experiencing it with SMPlayer.

Movie Player (Totem): VDPAU is not available from the preferences so it still stutters during the fast paced scenes. However, the playback is continuosly smooth otherwise.

VLC Player: I've enabled hardware decoding and the playback seems smooth enough, kind a like SMPlayer's, with some minor tearing during fast paced scenes. However, no matter what subtitle encoding I set, it wont recognize Swedish characters such as å, ä and ö, but displays them as question marks :( 

I would prefer to get the subtitles working in VLC but I realize this is a completely different issue and I will create a new thread for this.

One more question/remark: I noticed in nVidia settings that my LCD tv seems to report 50HZ as refresh frequency, where I was using 60Hz for the signal transmitted to the tv via HDMI before. Could this introduce the stutter? I've lowered the signal frequency to 50Hz but I haven't noticed any difference in the tv picture, except that the playback does seem a little less smooth now.

Also, what is the mplayer command one needs to issue in order to open a movie with subtitles and vdpau directly from the command line? I would like to try this one as well.

Any more general tips on this topic would be highly appreciated.

Thanks again for your help so far, boast.

Regards,
Veroslav

---

### Post by boast on 2011-12-23
I would say the tearing would be dealing with VSYNC and using a composite desktop/effects. 

Can't think of a reason for the stuttering though. Maybe enabling the extreme frame dropping might help, or increasing the caching of the player?

for mplayer command line i think its , mplayer -vo vdpau -sub file.sub file.mkv

---

