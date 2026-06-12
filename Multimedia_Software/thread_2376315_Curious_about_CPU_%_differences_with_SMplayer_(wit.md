---
title: "Curious about CPU % differences with SMplayer (with MPV backend) vs MPV standalone"
date: 2017-11-01
forum: Multimedia Software
---

### Post by Roasted on 2017-11-01
Hi friends. I've been a user of MPV for some time. After having recently switched to Wayland and set my mpv.conf to read "gpu-context=wayland" to obtain a much lower processor usage with hardware acceleration, I lost the window decorations. Not the end of the world, but after seeing a heated flame/turf war about this on a discussion forum elsewhere I figured it was time to start tinkering around in the world of MPV frontends as it sounded like there won't be an actual resolution to this (and frankly, MPV without decorations isn't that glorious in my opinion). In my search it looked like SMplayer had a decent following so it felt natural to try it out. So far, I'm really liking it, but there's something I'm curious on.

I have a 4K video downloaded to my laptop that I use to test. Laptop is running a 7th gen i5 along with Ubuntu 17.10. I'm using the Wayland session. When I play the 4K video in MPV, I get about 2-3% CPU usage. This is done after adding gpu-context=wayland to my MPV.conf. This is the only line in my MPV.conf at this time.

SMplayer fires up using MPV as the back-end. Okay, fine. Perhaps I misunderstand, but that (to me) suggests that MPV resource usage when using SMplayer *should* be somewhat equivalent to that of using MPV alone. When using SMplayer, it spawns an MPV process, and this MPV process uses on average 18% CPU.

i.e.:
SMplayer (with MPV) = 18% CPU
MPV (standalone MPV) = 2% CPU

I'm curious as to why this is. I don't believe the extra 16% is coming from SMplayer itself, as SMplayer spawns its own separate "SMplayer" process, which uses 0-1% CPU.

In my SMplayer preferences, I have "auto" set for hardware acceleration. I dug through the logs and found this very, very long command that SMplayer is executing to launch MPV. I copied that command and pasted it into terminal to run MPV manually via the same means SMplayer seems to launch it. One by one I removed the many flags, one at a time, until I found my CPU usage change. The flag that seems to do it is --no-config. If I remove that option, keeping the rest of the command the same, my CPU usage drops from 18% down to about 2% like I was seeing with standalone MPV. So this brings up the first question and I'm curious if someone can confirm this: I assume SMplayer is leveraging --no-config because it's anticipated that the SMplayer GUI settings will "take charge" instead of using MPV.conf, yes?

Moving on, within SMplayer, if I disable hardware acceleration, my CPU usage spikes up significantly more (50-60%). This suggests that it's doing -something- good when I set it to auto. If I set it to vaapi, though, it goes back to the 50-60% range. If I choose vaapi-copy, it hangs around 18-19%. So perhaps SMplayer's "auto" function is using vaapi-copy, maybe? The performance findings suggest that, but who knows. All other options (vdapu, cuda, etc) all use 40%+ CPU, so it almost has to be using vaapi-copy.

I mentioned I use gpu-context=wayland in my MPV.conf. Even if I padd gpu-context=wayland into the Advanced >> Mplayer/MPV field, it still yields around 18-19% CPU usage.

So I guess what I'm wondering is, what is happening that's different from SMplayer (with MPV backend) versus standalone MPV that I would see different results like this? Is it possible SMplayer is doing some extra legwork because I'm in a Wayland session that MPV isn't doing? No, the differences aren't earth shattering to be comparing 18% vs 2% usage (not like it's 300% vs 3%) -- I'm just genuinely curious.

Thanks for any insight!

---

### Post by SeijiSensei on 2017-11-01
You don't tell us what video adapter you're using and, if appropriate, whether you installed the proprietary driver.  As an NVIDIA user, I'd attribute the difference in CPU usage to whether SMPlayer is using hardware acceleration or not.  Does the 4K video use H.264 as its video codec?  Most adapters support acceleration of H.264 but not necessarily other codecs.  If you view an ordinary video at 720p or 1080p do you see the same CPU differences?

---

### Post by deadflowr on 2017-11-01
This add anything to what you see:
[https://community.ubuntu.com/t/hardware-accelerated-video-playback/304]("https://community.ubuntu.com/t/hardware-accelerated-video-playback/304")

---

### Post by SeijiSensei on 2017-11-01
You don't tell us what video adapter you're using and, if appropriate, whether you installed the proprietary driver.  As an NVIDIA user, I'd attribute the difference in CPU usage to whether SMPlayer is using hardware acceleration or not.  Does the 4K video use H.264 as its video codec?  Most adapters support acceleration of H.264 but not necessarily other codecs.  If you view an ordinary video at 720p or 1080p do you see the same CPU differences?

I just played a BD rip at 1080p encoded with H.264 and FLAC audio.  SMPlayer+MPV and MPV alone were within a few percentage points of each other in terms of CPU usage via top.

---

### Post by Roasted on 2017-11-01
> **SeijiSensei said:**
> You don't tell us what video adapter you're using and, if appropriate, whether you installed the proprietary driver.  As an NVIDIA user, I'd attribute the difference in CPU usage to whether SMPlayer is using hardware acceleration or not.  Does the 4K video use H.264 as its video codec?  Most adapters support acceleration of H.264 but not necessarily other codecs.  If you view an ordinary video at 720p or 1080p do you see the same CPU differences?

I just played a BD rip at 1080p encoded with H.264 and FLAC audio.  SMPlayer+MPV and MPV alone were within a few percentage points of each other in terms of CPU usage via top.

I just tried another video, specifically a 1080p H.264 video. My findings were nearly the same, in that SMplayer was in the high teens % wise while MPV standalone was a matter of 1-2% steady. If I comment out gpu-context=wayland in MPV.conf when using MPV standalone (thus disabling it), my CPU usage for the MPV process when using MPV standalone goes up to about 19-20%. I'm totally speculating here, but it makes me question if SMplayer is not passing the same level of hardware acceleration flags when using MPV as the backend. Clearly gpu-context=wayland is the ticket to having solid hardware acceleration with MPV standalone when using it in the Wayland session, but everything else equal, SMplayer still falls a bit short. Even Totem with the same video only uses about 3% of CPU steady (Totem!), so that's what has me curious if there's a way to trigger SMplayer into working a bit more like, well, regular MPV and Totem. 

My laptop has an i5-7200u. I'm just using the Intel graphics here in this case. Didn't install any additional GPU drivers.

> **deadflowr said:**
> This add anything to what you see:
[https://community.ubuntu.com/t/hardware-accelerated-video-playback/304]("https://community.ubuntu.com/t/hardware-accelerated-video-playback/304")

Hi there. I did see this discussion but I neglected to reply as I was still trying to figure out details of what I was seeing. Didn't want to interject in a discussion without knowing more. :)

---

### Post by mc4man on 2017-11-01
What version of smplayer are you using? The repo smplayer can not use gpu-context=wayland so it cannot use vaapi hwdec. (whether any smplayer can I haven't checked
To lay out - 
vaapi hwdec in wayland requires gpu-context=wayland
vaapi-copy hwdec does not require gpu-context=wayland

So it's likely you're getting vaapi-copy which provides some cpu savings but not to the extent of vaapi.
Also running mpv in smplayer's window does take a bit more cpu, generally inconsequential, a few % points.

In regards to window deco.
With no hwdec you should get deco in wayland with recent mpv
With vaapi-copy you'll also get  deco
With vaapi hwdec there will be no deco.
With gpu-context=wayland there will be no deco even if not using hwdec.

Edit: unless really needed hwdec is discouraged as it's potentially not  rendered as accurately as without it.

---

### Post by Roasted on 2017-11-01
> **mc4man said:**
> What version of smplayer are you using? The repo smplayer can not use gpu-context=wayland so it cannot use vaapi hwdec. (whether any smplayer can I haven't checked
To lay out - 
vaapi hwdec in wayland requires gpu-context=wayland
vaapi-copy hwdec does not require gpu-context=wayland

So it's likely you're getting vaapi-copy which provides some cpu savings but not to the extent of vaapi.
Also running mpv in smplayer's window does take a bit more cpu, generally inconsequential, a few % points.

In regards to window deco.
With no hwdec you should get deco in wayland with recent mpv
With vaapi-copy you'll also get  deco
With vaapi hwdec there will be no deco.
With gpu-context=wayland there will be no deco even if not using hwdec.

Edit: unless really needed hwdec is discouraged as it's potentially not  rendered as accurately as without it.

Hey there. Thanks for the detailed info. That helps a lot. In a slight wave of ignorance I assumed what SMplayer I had installed from 17.10 repos was the latest. Slight difference (v17.7 vs v17.10 of SMplayer), so I pulled down the PPA and updated. I'm still tinkering with different combinations of settings, but so far I'm not getting the 'low level' of CPU usage with SMplayer (using MPV backend) as I was getting with Totem (!) or MPV standalone. It doesn't really seem any different to before. That said I'm still trying different things out, so who knows what might come from this.

I've heard some folks discourage the use of hardware acceleration, but I've really only heard that from forum posts and whatnot I've seen when researching MPV. Ironically, MPV seems to do the best hardware acceleration I've seen. Perhaps there's a technical argument to back it up, but from a user perspective, I quite like hardware acceleration and haven't had any issues with it (aside from trying to make it work in SMplayer as good as it does in MPV since the lack of window deco in MPV is rather meh). My wife and I just watched a movie on my laptop with a 7th gen i5 proc and the fan didn't even bother kicking on. Can't say that about software acceleration -- software acceleration spikes this processor a considerable amount.

---

### Post by mc4man on 2017-11-02
If you want a more useful & verbose mpv log when using it thru smplayer then in smplayer > Options > Preferences > Advanced add the option,
```
--log-file=~/mpv.log
```
(- for mpv that option would just be this in mpv.conf if wanting in home folder..
log-file=mpv.conf

---

### Post by Roasted on 2017-11-02
Thanks. I've actually been doing SMplayer log dumps to get an idea of what's happening. This little gem sticks out to me, though I'm unsure what I can do about it.

```
Playing: /home/jason/Videos/Puppies-4K-Ultra-HD-Video.mp4
 (+) Video --vid=1 (*) (h264 4096x2304 23.980fps)
 (+) Audio --aid=1 --alang=und (*) (aac 2ch 44100Hz)
[vaapi] libva: va_getDriverName() failed with unknown libva error,driver_name=(null)
[vaapi] Failed to initialize VAAPI: unknown libva error
[vaapi] libva: va_getDriverName() failed with unknown libva error,driver_name=(null)
[vaapi] libva: va_getDriverName() failed with unknown libva error,driver_name=(null)
VO does not support requested hardware decoder, or loading it failed.
```

I mean, it says it failed to load vaapi, so I must not be able to leverage vaapi in its true form. That's probably why "auto" defaults to vaapi-copy. When using just MPV alone, I get the best performance when the only thing I pass is gpu-context=wayland. So I tried to add gpu-context=wayland in Preferences > Advanced > Mplayer/MPV > Options: and typed in "gpu-context=wayland" there. Likewise, I disabled hardware acceleration elsewhere within the SMplayer preferences. This way I wasn't specifically calling upon vaapi, but I was using (from what I can tell) only gpu-context=wayland, much like how MPV alone acts since that's the only entry in MPV.conf when I get the ultra low CPU usage with MPV. From my understanding, not calling on vaapi in SMplayer settings yet having gpu-context=wayland there should "mirror" how I was using MPV before, problem is there's no major difference with SMplayer like I was expecting (hence what sparked the questions around this thread).

I'll keep tinkering with it as I feel there must be something I'm missing, but honestly, for my day to day video playing usage it might be time to appreciate the work that has gone into Totem for a bit. Totem, somewhat ironically, is literally the only player hitting the checkboxes: supports excellent hardware acceleration, has the basic features I want, and actually (gasp) has window decorations. :) I'll keep plugging away at this but eh, maybe I'm just against a wall and SMplayer doesn't support vaapi in the way I thought. The other gui frontends to MPV seemed to have their own differences or struggles (had hardware accel issues in Gnome MPV, for example), so.. meh. Might be time to appreciate what works today and revisit as software gets organically updated over time.

---

### Post by Roasted on 2017-11-02
I kept messing around with SMplayer a bit. I do believe you're right, that SMplayer is falling back to vaapi-copy, which isn't quite as efficient as vaapi, but better than nothing.

I compared the performance in X versus Wayland. All things equal otherwise. Same machine, same 4k video, etc. I only took out the part that caught my eye as seen below.

SMplayer in Xorg session:
```
Using hardware decoding (vaapi).
AO: [pulse] 44100Hz stereo 2ch float
VO: [gpu] 4096x2304 vaapi[nv12]
```

SMplayer in Wayland session:
```
[vaapi] libva: va_getDriverName() failed with unknown libva error,driver_name=(null)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vaapi] libva: va_getDriverName() failed with unknown libva error,driver_name=(null)
AO: [pulse] 44100Hz stereo 2ch float
Using hardware decoding (vaapi-copy).
```

So... I wonder if this is a limitation specifically of SMplayer, or a problem with Wayland. I'm leaning towards SMplayer given MPV standalone can run vaapi without error... and the CPU usage suggests that it's working (2% or so).

---

### Post by mc4man on 2017-11-02
I can't see that you would get hwdec in mpv without specifying it, what's the actual mpv version you have? (mpv -v in terminal will show.
The option gpu-context=wayland  just allows vaapi thru wayland

If you go mpv --no-config --gpu-context=wayland /path/to/vid  whats does it report?

Ex. here
$ mpv --no-config --gpu-context=wayland '/home/doug/Desktop/amostviolentyear-clip1_h1080p.mov' 
Playing: /home/doug/Desktop/amostviolentyear-clip1_h1080p.mov
 (+) Video --vid=1 (*) (h264 1920x816 23.976fps)
 (+) Audio --aid=1 --alang=eng (*) (aac 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch float
VO: [gpu] 1920x816 yuv420p
AV: 00:00:01 / 00:01:00 (2%) A-V:  0.000

$ mpv --hwdec=vaapi --gpu-context=wayland '/home/doug/Desktop/amostviolentyear-clip1_h1080p.mov' 
Playing: /home/doug/Desktop/amostviolentyear-clip1_h1080p.mov
 (+) Video --vid=1 (*) (h264 1920x816 23.976fps)
 (+) Audio --aid=1 --alang=eng (*) (aac 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch float
Using hardware decoding (vaapi).
VO: [gpu] 1920x816 vaapi[nv12]
AV: 00:00:01 / 00:01:00 (2%) A-V:  0.000

Totem seems to work ok with hwdec (the gstreamer-vaapi plugin) though not nearly as efficient as mpv but as good or even better than vlc.
One big drawback to totem is it only sizes it's video window once, on first run. After that vids open in last used size which many times is inappropiate to the vid being played.

---

### Post by Roasted on 2017-11-02
I'm running MPV through (your?) PPA (mc3man). Current version is: 2:0.27.0+git2~ amd64  (as reported by dpkg -l mpv)

I'm also running the latest SMplayer through rvm's PPA -- 17.10.2-1~artf amd64.

I took your suggestion with running --no-config along with gpu-context. Here are the results:

```
jason@JasT470:~$ mpv --no-config --gpu-context=wayland Videos/Puppies-4K-Ultra-HD-Video.mp4 
Playing: Videos/Puppies-4K-Ultra-HD-Video.mp4
 (+) Video --vid=1 (*) (h264 4096x2304 23.980fps)
 (+) Audio --aid=1 --alang=und (*) (aac 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch float
VO: [gpu] 4096x2304 yuv420p
AV: 00:00:15 / 00:02:29 (10%) A-V:  0.000 Dropped: 59

```

My i5 7200u CPU with integrated graphics ran at about 45-50% CPU, so it appears to have been just running through software acceleration. Makes sense since you mention that gpu-context=wayland doesn't "do" anything besides allow vaapi to be usable if called upon.

In SMplayer's case, it actually runs MPV with --no-config, and then (from what I can see and understand) enables flags to pass to MPV based on what you adjust within the GUI preferences of SMplayer. There is an advanced preference menu where I can pass my own flags through. I added: --gpu-context=wayland --hwdec=vaapi vo=opengl. This seemed to work, and it worked well (vaapi seemed to work based on the CPU usage being a matter of 2% or so), but it launches MPV in its own window -- it doesn't keep MPV embedded within SMplayer, which isn't really preferred of course. So I guess in the end, I *can* make SMplayer work with MPV and vaapi, but its windowing behavior is even more irritating than MPV's lack of window decoration (when in a Wayland session with vaapi enabled). Best case scenario with SMplayer is to leverage vaapi-copy, which uses a bit more CPU, but behaves muuuch better as far as the way it handles the windowing of its own application.

Totem is a neat little player that's seemingly come a long way. I can hit hardware acceleration levels out of the box to comparable CPU usage to that of MPV standalone with vaapi enabled -- that's huge to me as an end user. The only irritating part about Totem is when it comes to pasting a video link in to watch a video from the internet, as that's a 7 step process to accomplish. MPV handles this by launching via terminal, which is neat but I don't care for as that requires launching a terminal window *each* time I want to watch an internet video (no thanks), or via dragging and dropping -- which has its own struggles as it's not verbose whatsoever. There are times I drag/drop a video link to MPV and I sit there wondering -- did it fail? Is it just buffering slow and still trying to load? Who knows -- it's not telling me anything. So I have that behavior to compare to the way Totem handles internet hosted videos (youtube, etc) with it being a several step process. SMplayer takes care of *all* of this by just letting me hit CTRL U, paste a link, hit enter, and go. (just my semi candid opinions on the behaviors of video apps I've been using and why I have a vested interest in SMplayer particularly with MPV as the backend, since MPV still remains amazing despite my 0.02 of interfacing with it on the front end).

As it stands now, I can do vaapi-copy with SMplayer in Wayland, but not vaapi. When in an X session, vaapi works fine. Given MPV itself can run vaapi when I call it in Wayland seemingly without issue, it confuses me how SMplayer (using MPV as backend) cannot do this. Might have to dig more.

---

### Post by mc4man on 2017-11-02
Ok, your basically seeing what's currently the state in Wayland with mpv & smplayer. Mpv's wayland performance has gotten much better over the last couple of months & probably will continue to do so over time.
I'd expect smplayer to support wayland better though it could be a while in coming.
While I've designed mpv.desktop with unity in mind you could get some useful info from the quicklists provided which also work in gnome-shell. Just pin/add  mpv to the launcher > r. click on to view. I add or remove some items of interest from time to time. (ex. just removed link to [stats.lua page]("https://github.com/Argon-/mpv-stats") as it's now part of mpv

Overall vaapi-copy may be your best current bet for mpv/smplayer or even mpv itself  if window deco & some form of hwdec matters...

---

### Post by Roasted on 2017-11-02
> **mc4man said:**
> Ok, your basically seeing what's currently the state in Wayland with mpv & smplayer. Mpv's wayland performance has gotten much better over the last couple of months & probably will continue to do so over time.
I'd expect smplayer to support wayland better though it could be a while in coming.
While I've designed mpv.desktop with unity in mind you could get some useful info from the quicklists provided which also work in gnome-shell. Just pin/add  mpv to the launcher > r. click on to view. I add or remove some items of interest from time to time. (ex. just removed link to [stats.lua page]("https://github.com/Argon-/mpv-stats") as it's now part of mpv

Overall vaapi-copy may be your best current bet for mpv/smplayer or even mpv itself  if window deco & some form of hwdec matters...

Yeah - I've seen the quicklist in Gnome. I thought that was genius. Bravo. :) In regard to vaapi, it's difficult to tone it down after you've seen what vaapi is capable of, but perhaps I should accept the partial vaapi success as a work in progress and just leverage vaapi-copy. After all, vaapi-copy is still a massive improvement. It takes my CPU usage (I've seen it as high as 70%) down to 19%, which is the max I've seen when using vaapi-copy. It's even lower than that when I'm playing my usual videos and streams, which are almost always 1080p or lower. That's a huge improvement, and one worth pursuing for sure. 

The only thing frustrating me now is my mpv.conf only contains hwdec=vaapi-copy, and now my CPU usage reflects that of vaapi-copy, but dragging and dropping local videos to the MPV window isn't working. I hate to say it, but I think I'll have to focus entirely on SMplayer for day to day use. I suspect this may have something to do with Wayland (?), but the last thing I want to do is bring it up on github and instigate yet another war about Gnome/Wayland/etc, as that's been a rather consistent debate there. I've also thought about putting in a feature request for being able to just CTRL V when the MPV window is open to append the copied link to MPV -- perhaps I'll do that, although I suspect that kind of feature isn't the intended target of MPV. 

Having MPV as the backend to SMplayer is a combination that's difficult to ignore though. I mean, you get the functions of a decent GUI (once you adjust the theme preferences a bit -- the default SMplayer UI theme was enough to turn me away for years until I realized that it's easily themeable), and the MPV backend is just gold. All that said, it does make me question what on earth Totem is doing to work the way it does with its CPU usage when running a local 4k video. I mean, it's good... quite good... a little better than hwdec=vaapi-copy even. I didn't expect that from Totem (sorry Totem devs), but kudos on the improvements.

---

