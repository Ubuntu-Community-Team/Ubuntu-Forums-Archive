---
title: "mediatomb + Panasonic tx-p50v20e"
date: 2011-02-04
forum: Multimedia Software
---

### Post by lemmings1975 on 2011-02-04
Hi everybody,

I recently bought a Plasma Panasonic tx-p50v20e and there is an option that allow me to watch Movies, Pictures 
and listen music through DLNA.

For music it's perfect if the format is not recognize he transcodes on the fly. 
For picture it's not yet done but it's for later.

The only problem I've got it's with the video. He starts to play then after 10-15 seconds he freezes, always at the same place. Some video works perfectly and when I look with mediainfo it's the same between the file except 
some are encoded with (*)virtualDubMod 1.15.10 and others with transcode 1.1.5 even with (*)fairuse.
(*) = readable.

at the beginning I thought it was the wifi but even with a cable the problem remains.

Did anyone had this problem and found a solution ?

You can find bellow the arguments I use with Mencoder.

```

<profile name="mencoder-int" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=9000:vrc_buf_size=1835 -ofps 25 -mpegopts muxrate=12000 -af lavcresample=44100 -vf harddup -o %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>
      <profile name="mencoder-1080" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -aid 1 -sid 0 -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=15:vbitrate=200000:vrc_maxrate=12000:vrc_buf_size=1835 -mpegopts muxrate=12000 -vf harddup,scale -xy 1080 -font /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf -subfont-autoscale 0 -subfont-text-scale 20 -slang fr,en -noautosub -ofps 24000/1001 -o %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>

```

resources used:
Ubuntu 10.10 server no gui
Mencoder : 1.0rc4-4.4.5
Mediatomb : 0.12.1

---

### Post by lemmings1975 on 2011-02-06
up ;-)

I know it's not cool ;-)

---

