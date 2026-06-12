---
title: "Enabling dmix in 9.4"
date: 2009-07-17
forum: Multimedia Software
---

### Post by nightfly19 on 2009-07-17
I seem to be having difficulty enabling dmix for alsa under Ubuntu 9.4. I have a asound.conf file in /etc/ that the contents of which will supposedly enable it. My audio device is **00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**. My long term goal is to be able to run a jack server while allowing other sources to play audio as well that do not support jack.


asound.conf file:
```

pcm.pmix {
        type dmix
        ipc_key 1024 # unique IPC key

        slave {
                pcm "hw:0,0"
                period_time 0 # reset to the default value
                period_size 1024 # in bytes
                # buffer_size or periods can be commented
                # they both represent the same thing in different values
                buffer_size 8192 # in bytes
                # periods 128 # INT
                rate 44100
        }
        bindings {
                0 0
                1 1
        }
}

# redirect default PCM device into dmix (pmix) plugin
pcm.!default {
        type plug # auto rate conversion plugin
        slave.pcm "pmix"
}

ctl.!default {
	type hw           
	card 0
        }

ctl.pmix {
	type hw
	card 0
    }

# legacy OSS /dev/dsp support, also redirects intp dmix (pmix) plugin

pcm.dsp {
    type plug
    slave.pcm "pmix"
}

pcm.dsp0 {
        type plug
        slave.pcm "pmix"
}

```

---

