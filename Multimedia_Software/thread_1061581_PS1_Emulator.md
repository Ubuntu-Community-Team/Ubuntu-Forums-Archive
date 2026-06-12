---
title: "PS1 Emulator"
date: 2009-02-05
forum: Multimedia Software
---

### Post by RealG187 on 2009-02-05
```
mpg@MIKED6:~/Desktop/pSX$ ./pSX
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
mpg@MIKED6:~/Desktop/pSX$ 

```

My friend got a PS1 emulator working on his computer working. He copied it to my USB hard drive and it doesn't work. I get the output above when I use the terminal to run it...

EDIT: WTF if I type "gksu killall pulseaudio" then run it, it works, my friend found that out...

---

