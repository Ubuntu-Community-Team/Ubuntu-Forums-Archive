---
title: "Can't play hd videos on ubuntu 10.04."
date: 2012-02-26
forum: Multimedia Software
---

### Post by agentfortyseven on 2012-02-26
Hello everyone,
I'm having tough time playing hd videos on my Ubuntu 10.04. I don't see any problem with 240p or 360p resolution videos. But as soon as I switch to 480p or higher, the video turns into a mere slideshow of photos although I do have a high speed internet connection. I've got a Dell latitude E6400 laptop with 4 GB RAM and 512 MB graphics card (NVIDIA). It still won't help. Can you please help me figure out the problem?

EDIT: I'm talking about flash videos over internet.

---

### Post by papibe on 2012-02-26
Could you post the result of these commands?
```
lspci | grep -i vga

apt-cache policy nvidia-current

apt-cache policy libvdpau1
```

Also, what video player are you using?

Regards.

EDIT: BTW, I have a Dell Dimension E520, an Nvidia 9500GT, running 10.04, and I'm able to play full HD video.

---

### Post by soryu on 2012-02-27
try another player.(i'm doing that now) hopefully it will get better
i've got a radeon hd4200 video card and 720 is not great it skips a little. i'ts  fine on windows  i can  go 1080 no prob.
maybe it's just ubuntu.
maybe it's just my settings.

---

### Post by agentfortyseven on 2012-02-27
> **papibe said:**
> Could you post the result of these commands?
```
lspci | grep -i vga

apt-cache policy nvidia-current

apt-cache policy libvdpau1
```Also, what video player are you using?

Regards.

EDIT: BTW, I have a Dell Dimension E520, an Nvidia 9500GT, running 10.04, and I'm able to play full HD video.

Hey there thanks for the reply man. Well I got the following reply when I ran those commands:

hitman@ubuntu:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G98M [Quadro NVS 160M] (rev a1)

hitman@ubuntu:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 195.36.24-0ubuntu1~10.04.1
  Candidate: 195.36.24-0ubuntu1~10.04.1
  Version table:
 *** 195.36.24-0ubuntu1~10.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Packages
        100 /var/lib/dpkg/status
     195.36.15-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Packages

hitman@ubuntu:~$ apt-cache policy libvdpau1
libvdpau1:
  Installed: (none)
  Candidate: 0.3-2build1
  Version table:
     0.3-2build1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages

I use vlc player but I'm talking about the lagging hd videos over internet. The hd videos on my laptop plays just fine.

---

### Post by agentfortyseven on 2012-02-27
> **soryu said:**
> try another player.(i'm doing that now) hopefully it will get better
i've got a radeon hd4200 video card and 720 is not great it skips a little. i'ts  fine on windows  i can  go 1080 no prob.
maybe it's just ubuntu.
maybe it's just my settings.

hi there,
Can you suggest me some?
thanks

---

### Post by papibe on 2012-02-27
Thanks.

You have you install the video acceleration libraries:
```
sudo apt-get install libvdpau1
```
Then install SMPlayer:
```
sudo apt-get install smplayer
```
Then configure SMplayer to use vdpau by going:
```
SMplayer -> Options -> Preferences -> General -> Video
```
There, set the 'Output driver' to:
```
vdpau
```
finally restart SMplayer, and test some movies.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by agentfortyseven on 2012-02-27
Well I'm sorry I wasn't very clear about my question. I was talking about the flash videos on youtube or anywhere on internet and not the ones downloaded on my laptop.

---

### Post by agentfortyseven on 2012-02-27
> **papibe said:**
> Thanks.

You have you install the video acceleration libraries:
```
sudo apt-get install libvdpau1
```Then install SMPlayer:
```
sudo apt-get install smplayer
```Then configure SMplayer to use vdpau by going:
```
SMplayer -> Options -> Preferences -> General -> Video
```There, set the 'Output driver' to:
```
vdpau
```finally restart SMplayer, and test some movies.

Hope it helps, and tell us how it goes.
Regards.
I tried this and couldn't get the lagging hd flash videos on youtube to go any faster. Any other suggestion.
Thanks.

---

### Post by soryu on 2012-02-27
> **agentfortyseven said:**
> Well I'm sorry I wasn't very clear about my question. I was talking about the flash videos on youtube or anywhere on internet and not the ones downloaded on my laptop.

oh, streaming hd videos don't play that well on my laptop either they tear.
 well not as good as they play in windows.
i'm currently using the vlc plug-in i guess ill switch over to something different.
do a search for" multimedia how to" it will tell you how to switch plug ins correctly.
it should work for 11.10

---

### Post by soryu on 2012-02-27
derp.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[https://sites.google.com/site/tipsandtricksforubuntu/multimedia](https://sites.google.com/site/tipsandtricksforubuntu/multimedia)

---

### Post by agentfortyseven on 2012-02-27
> **soryu said:**
> oh, streaming hd videos don't play that well on my laptop either they tear.
 well not as good as they play in windows.
i'm currently using the vlc plug-in i guess ill switch over to something different.
do a search for" multimedia how to" it will tell you how to switch plug ins correctly.
it should work for 11.10

pretty weird though because this never happened to me before when I had the same ubuntu 10.04 on my desktop. wonder what could be wrong.

---

### Post by agentfortyseven on 2012-02-27
> **soryu said:**
> derp.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[https://sites.google.com/site/tipsandtricksforubuntu/multimedia](https://sites.google.com/site/tipsandtricksforubuntu/multimedia)
hey buddy are you trying to say adding medibuntu repositories would solve the problem. I'm gonna log off for now because its too late here. but thanks anyway and do reply.

---

### Post by soryu on 2012-02-27
a little more down on the page to  step 2/5
or further down to flash troubleshooting.

just did the troubleshooting step. it helped  hd streams aren't tearing even in fullscreen.
ill try a different plug in see what happens.
still not as smooth as windows though.

---

### Post by soryu on 2012-02-27
> **papibe said:**
> Could you post the result of these commands?
```
lspci | grep -i vga

apt-cache policy nvidia-current

apt-cache policy libvdpau1
```Also, what video player are you using?

Regards.

EDIT: BTW, I have a Dell Dimension E520, an Nvidia 9500GT, running 10.04, and I'm able to play full HD video.

what player are you using?
my hd videos aren't smooth  they seem to skip a frame or two.
i upgraded from 10.04 to11.10.

---

### Post by soryu on 2012-02-27
> **papibe said:**
> Thanks.

You have you install the video acceleration libraries:
```
sudo apt-get install libvdpau1
```Then install SMPlayer:
```
sudo apt-get install smplayer
```Then configure SMplayer to use vdpau by going:
```
SMplayer -> Options -> Preferences -> General -> Video
```There, set the 'Output driver' to:
```
vdpau
```finally restart SMplayer, and test some movies.

Hope it helps, and tell us how it goes.
Regards.


also tried this but got a white screen.

---

### Post by papibe on 2012-02-27
@agentfortyseven

After you installed libvdpau1, you can add hardware acceleration to flash on Firefox by following this [steps]("http://ubuntuforums.org/showpost.php?p=11255771&postcount=23").

Regards.

---

### Post by papibe on 2012-02-27
> **soryu said:**
> also tried this but got a white screen.
I'm afraid those steps won't work for you since you mentioned you had a radeon hd4200. Those instructions are for systems with Nvidia cards only.

Regards.

---

### Post by agentfortyseven on 2012-02-27
> **papibe said:**
> @agentfortyseven

After you installed libvdpau1, you can add hardware acceleration to flash on Firefox by following this [steps]("http://ubuntuforums.org/showpost.php?p=11255771&postcount=23").

Regards.
When I ran the command from the link you gave me (i.e.[FONT=monospace] [/FONT]$ strings /usr/lib/firefox/plugins/flashplugin-alternative.so  |grep -i vdpau) I got the following reply

VDPAU,H264,
VDPAU,Device 
VDPAU,
libvdpau.so
libvdpau.so.1
glVDPAUInitNV
glVDPAUFiniNV
glVDPAUUnregisterSurfaceNV
glVDPAUSurfaceAccessNV
glVDPAUMapSurfacesNV
glVDPAUUnmapSurfacesNV
glVDPAURegisterOutputSurfaceNV

Should I proceed further? Because this output seems to be a tad different from the one that you wrote on that post.

---

### Post by papibe on 2012-02-27
> **agentfortyseven said:**
> Should I proceed further?
Yes. There are references to vdpau, and that should be enough.

Tell us how it goes.
Regards.

---

### Post by agentfortyseven on 2012-02-27
> **soryu said:**
> a little more down on the page to  step 2/5
or further down to flash troubleshooting.

just did the troubleshooting step. it helped  hd streams aren't tearing even in fullscreen.
ill try a different plug in see what happens.
still not as smooth as windows though.
I'll try to do that soon. But I guess for now its one thing at a time. thanks anyway. hope your problem gets resolved too.

---

### Post by agentfortyseven on 2012-02-27
> **papibe said:**
> 
Tell us how it goes.
Regards.
Everything seemed good so far although now my adobe flash plugin crashes quite often after the workaround. 
Also the hd YouTube videos (1080p or 720p) aren't as fast as a 240p or a 360p video. I didn't notice this immediately after the tweak because there was a drastic improvement from before but I still believe that this isn't as fast as it could get. I can say this for sure because the same video runs much faster (or should I say smoother) on a friend's windows laptop which isn't any better than mine when you talk about GPU.

---

### Post by agentfortyseven on 2012-02-28
And the worst part is that now I can't move the streaming button at all without screwing up the video (but the audio would play just fine). Can anyone tell me what's wrong.

---

### Post by agentfortyseven on 2012-05-02
The solution for this thread would be upgrading to 12.04.
However my adobe flash plugin crashes quite often even after the upgrade.
Down with these freaking b*stards at Adobe for not resolving the adobe flash player issue for more than a year now. I wonder if they get paid by Linux rivals for doing this.:mad:

---

### Post by BicyclerBoy on 2012-05-02
Some people find that hardware accelerated flash is less stable.

Adobe have now stopped all (flash) linux support. All future linux flash support is to come via a new api called pepper.
Pepper is supported by Chrome but not Mozilla..

There is an "opt-in" WebM & native browser H264 streaming from Youtube..this is much nicer to use than flash..but most material is still flash only.

The flash-replace plugin (firefox)  works on some sites..
"lovinglinux" has a good tutorial & config tool for flash browser plugins.

---

### Post by The Rnegade on 2012-05-02
> **agentfortyseven said:**
> Hello everyone,
I'm having tough time playing hd videos on my Ubuntu 10.04. I don't see any problem with 240p or 360p resolution videos. But as soon as I switch to 480p or higher, the video turns into a mere slideshow of photos although I do have a high speed internet connection. I've got a Dell latitude E6400 laptop with 4 GB RAM and 512 MB graphics card (NVIDIA). It still won't help. Can you please help me figure out the problem?

EDIT: I'm talking about flash videos over internet.

a possible solution might be to install adobe flash from the adobe website instead of the ubuntu repos

---

### Post by agentfortyseven on 2012-05-02
> **BicyclerBoy said:**
> Some people find that hardware accelerated flash is less stable.

Adobe have now stopped all (flash) linux support. All future linux flash support is to come via a new api called pepper.
Pepper is supported by Chrome but not Mozilla.

Thanks for that piece of info. I guess we'll have to wait until the end of this year when google comes up with Pepper. A total independence from adobe would have been amazing but lets hope this is a major step towards that.
I can already see chrome replacing firefox as the default browser in the next version of ubuntu.

---

### Post by agentfortyseven on 2012-05-02
> **The Rnegade said:**
> a possible solution might be to install adobe flash from the adobe website instead of the ubuntu repos
That wouldn't help because we already have the same updated version in ubuntu repos.

---

### Post by BicyclerBoy on 2012-05-02
The big hope for independence was Apple refusing to allow flash & the big push for WebM to allow the web to remain free open source.

Apple was just controlling revenue streams.
Google was hoping to use WebM for Youtube & not have to pay licence fees to mpeg-la.

I'm not sure google is less scary than Adobe..but a browser API should be less revolting to use than the flash plugin.

---

### Post by agentfortyseven on 2012-05-02
> **bicyclerboy said:**
> the big hope for independence was apple refusing to allow flash & the big push for webm to allow the web to remain free open source.

Apple was just controlling revenue streams.
Google was hoping to use webm for youtube & not have to pay licence fees to mpeg-la.

I'm not sure google is less scary than adobe..but a browser api should be less revolting to use than the flash plugin.

+1

---

