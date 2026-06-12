---
title: "Promblem playing 1080dp videos."
date: 2011-03-03
forum: Multimedia Software
---

### Post by utkarshjadhav on 2011-03-03
I use nVidia graphics card.here are specifications-
```

utkarsh@utkarsh-desktop:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:a0000000-bfffffff(prefetchable) memory:d0000000-d1ffffff ioport:c000(size=128) memory:d3000000-d307ffff(prefetchable)

``````

utkarsh@utkarsh-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

```I have also downloaded nVidia graphics drivers.
[COLOR=Red][B]
1080dp videos arent playing well.
Can anyone help me with this?[/B][/COLOR]

---

### Post by Kirboosy on 2011-03-03
Have you tried playing them in [VLC]("http://www.videolan.org/vlc/")

I have found VLC is the only way I can play HD videos on my computers.

---

### Post by WannabeFantasma on 2011-03-03
Meaning on Youtube or a real video?

---

### Post by BicyclerBoy on 2011-03-03
Assume you are talking about real video MPEG4/10 H264AVC 1080i..

To take full advantage of the 9400GT you need:
proprietary nvidia drivers
vdpau libs
player with vdpau support (MythTV, XBMC, mplayer)

The other option is vdpau-vaapi wrapper lib & player with va-api support (mplayer, VLC)
VLC with va-api must be compiled.
I think the splitted-desktop ppa has VLC with va-api.

VA-API does not work as well as vdpau & is not as configurable.

For later ..there are some vdpau configuration options to get the best performance..

A core2duo can decode H264 1080i no problem, just does not look as good as the h/w decode vdpau.
Note: the 9400GT can do 1x advanced de-interlacing (AFAIK MA) & not 2x (AFAIK VA).
decodes H264 1080i just fine.

Have you installed the nvidia driver ?
It is much easier to get a packaged pre-compiled 3rd party ppa nvidia driver..
The nvidia install process is painful & you need the kernel headers package & lots of build tools.

---

### Post by utkarshjadhav on 2011-03-07
I am trying to play video from my HDD.
I have installed driver recommended by ubuntu utility-'Hardware drives'
I also tried to Compile mplayer with VDPAU support on Ubuntu as instructed on
```

http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/

```
but all in vain.It irritates ...specially when you go through such a painful long process.
Mplayer now has succumbed like anything and refuses to play anything :(
F1!

---

### Post by BicyclerBoy on 2011-03-07
That blog is 2 years old...
That's an ice-age in mplayer terms..

You can get pre-compiled nvidia drivers & vdpau & (s)mplayer (with vdpau) for lucid & earlier..
[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa?field.series_filter=lucid")

lucid & later graphics driver from x-swat ppa linked in the above...

---

