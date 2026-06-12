---
title: "Surround sound in Kubuntu"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by Metallion on 2007-10-03
Somehow my surround sound stopped working when I installed Kubuntu. I had it working before in Ubuntu with gnome and I try to use the same settings now.

I have a .asoundrc file in my home directory with this text in it:
```

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```

When running the Alsa mixer the following channels are set to 100: Master, Master mono, PCM, Surround, Center and LFE. Surround jack is set to shared.

Does anyone know what my problem could be?

Edit: Another thing I might add is that I am using OSS since ALSA is giving me a lot of hickups in the sound.

Edit 2: Alright... I noticed the changed I am making to alsamixer didn't get saved so I saved them with "sudo alsactl store". Now only my front speaker isn't working... Help would still be appreciated! :)

---

### Post by MCMcButtah on 2007-10-03
I'v been using kmix to edit my surround setting in kubuntu and it has worked for me. Maybe you have an ownership/permissions problem with your config file?

---

### Post by Metallion on 2007-12-03
Sorry for digging up my months old thread but just now I  managed to fix it. I figured it'd be good to post this here for other people who are sharing my problem. Besides, this thread is also the first result when I search google for "kubuntu surround".

Eventually I got my surround working perfectly using the following .asoundrc file...

```

pcm.!dmix {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
       channels 6
       period_size 1024
       buffer_size 5120
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}

```

...which I got from this site: [http://gentoo-wiki.com/HOWTO_Surround_Sound](http://gentoo-wiki.com/HOWTO_Surround_Sound)

The sound was very messed up at first but when I increased the period_size and buffer_size it worked just fine.

For the people who are clueless: the .asoundrc file goes in your home directory and you have to create it yourself.

---

