---
title: "liquidsoap-1.4.1 in Ubuntu 20.04 missing output.shoutcast plugin"
date: 2020-12-17
forum: Multimedia Software
---

### Post by jauling on 2020-12-17
I upgraded my Ubuntu VM from 18.04 to 20.04. This in turn has upgraded the liquidsoap package from 1.1.1-7.2ubuntu1 to 1.4.1-1build1. I use liquidsoap to stream mp3 audio to my shoutcast server, but I noticed that liquidsoap-1.4.1 in Ubuntu 20.04 seems to be missing the output.shoutcast plugin.

In the logs:
```
Dec 12 19:23:33 feeble liquidsoap[1355]: Starting liquidsoap channels: radioname.liq
Dec 12 19:23:33 feeble liquidsoap[1372]: At line 13, char 0-17:
Dec 12 19:23:33 feeble liquidsoap[1372]: Error 4: Undefined variable output.shoutcast
```

And if you try to query the output.shoutcast plugin:
```
# which liquidsoap
/usr/bin/liquidsoap
# liquidsoap -h output.shoutcast
Plugin not found!
```

Checking the plugins that liquidsoap knows about:
```
# liquidsoap --list-plugins-xml | grep -o "<label>output\..*"
<label>output.alsa</label>
<label>output.ao</label>
<label>output.dummy</label>
<label>output.external</label>
<label>output.file</label>
<label>output.file.hls</label>
<label>output.gstreamer.audio</label>
<label>output.gstreamer.audio_video</label>
<label>output.gstreamer.video</label>
<label>output.harbor</label>
<label>output.harbor.ssl</label>
<label>output.icecast</label>
<label>output.jack</label>
<label>output.oss</label>
<label>output.portaudio</label>
<label>output.pulseaudio</label>
<label>output.sdl</label>
<label>output.udp</label>
```

I've already [reported]("https://github.com/savonet/liquidsoap/issues/1437") this on the liquidsoap github dev repo, but so far no traction yet. Has anyone ran into this issue, and is there a workaround? I've confirmed this issue also exists on a fresh install of Ubuntu 20.04.

---

### Post by Yellow Pasque on 2020-12-17
Buildlog says it was buit with Icecast/shoutcast support: [https://launchpadlibrarian.net/470289415/buildlog_ubuntu-focal-amd64.liquidsoap_1.4.1-1build1_BUILDING.txt.gz](https://launchpadlibrarian.net/470289415/buildlog_ubuntu-focal-amd64.liquidsoap_1.4.1-1build1_BUILDING.txt.gz)

output.icecast is listed in your plugins. Maybe the program should be using that?

---

### Post by jauling on 2020-12-18
I'll need to look into if that's possible... but I'm not sure that is a valid workaround (yet). I realize these two streaming services are pretty similar. 

I did check the liquidsoap-1.4.1 changelog [here]("https://github.com/savonet/liquidsoap/blob/1.4.1/CHANGES.md"), which doesn't have any entries about the shoutcast plugin being removed or deprecated or replaced with icecast. Also looked at the changelog specific to the Ubuntu 20.04 build; same deal: [http://changelogs.ubuntu.com/changelogs/pool/universe/l/liquidsoap/liquidsoap_1.4.1-1build1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/l/liquidsoap/liquidsoap_1.4.1-1build1/changelog)

I think submitting a bug report via [launchpad]("https://launchpad.net/ubuntu/+source/liquidsoap/+bugs") is most likely the most appropriate, thanks.

---

### Post by Yellow Pasque on 2020-12-18
> **jauling said:**
> I think submitting a bug report via [launchpad]("https://launchpad.net/ubuntu/+source/liquidsoap/+bugs") is most likely the most appropriate, thanks.

It won't hurt, but it's most appropriate when the Ubuntu package exhibits the problem and upstream doesn't. If I have time and motivation later today, I'll try building the latest stable version in my 20.04 VM and see if it has the same issue.

---

### Post by Yellow Pasque on 2020-12-24
Well, I tried building latest stable and the build failed with an entirely different issue. Hmmm.

---

### Post by jauling on 2020-12-31
Not sure when this will get any traction, so I decided to side-step this issue by switching over to icecast2 for both the server and the liquidsoap output. This is working flawlessly so far, and I feel a bit less dirty by using a full opensource solution :D

---

