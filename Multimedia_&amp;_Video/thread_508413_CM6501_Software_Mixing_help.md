---
title: "CM6501 Software Mixing help"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by danielj57 on 2007-07-24
Need some help getting my sound working :), have got Ubuntu feisty fawn (AMD64).

Heres the problem, my sound works, in that only one application can access the sound card at a time, but I need to use Wine (CS: S) and teamspeak, which obviously can't happen with my device not supporting hardware mixing. I installed alsa-oss and the alsa source drivers, then made sure everything was up-to-date. Tried to load the 2 programs (Teamspeak and Wine) together again, no sound in one again, (i used the aoss command also, same) so I attempted to set up my /.asoundrc using the same settings that I used in Ubuntu Dapper (x86) which for some reason hasn't done the trick... so being new to linux and all, I was wondering if some of you pro's will help me out :)
My ./asoundrc for all whom it may concern :)

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/daniel/.asoundrc.asoundconf>

#
#My sound card
#

pcm.cm6501 {
        type hw
        card 1
        mmap_emulation true
	nonblock true
}

#
#Dmix and Dsnoop mixing
#

pcm.!playback {
        type dmix       	# dmix plugin for mixing the output
        ipc_key 1234    	# a unique number
	ipc_key_add_uid true    # add current uid to unique IPC key
	ipc_perm 0600   	# IPC permissions (octal, default 0600
        slave {
                pcm "cm6501"
                period_time 0
                period_size 1024
                buffer_size 8192
		channels 6
                rate 48000
        }
bindings {
        0 0 #left
        1 1 #right
	2 2 #rear left
	3 3 #rear right
	4 4 #centre
	5 5 #lfe
        }
}

pcm.!capture {
        type dsnoop     	# dsnoop plugin for input
        ipc_key 5678    	# another uniqe number
        ipc_key_add_uid true    # add current uid to unique IPC key
        ipc_perm 0600            # IPC permissions (octal, default 0600)
        slave {
                pcm "cm6501"
                period_time 0
                period_size 1024
                rate 48000
        }
}


#
# combine playback/capture device
#

pcm.!duplex {
        type asym
	playback.pcm "playback"
        capture.pcm "capture"
}

#
# making the playback/capture device default
#

pcm.!defualt {
type plug
slave.pcm "duplex"
}

#
# for oss compatibility
#

pcm.!dsp1 {
type plug
slave.pcm "duplex"
}

ctl.!mixer1 {
type hw
card 1
}

#
#My 5.1 upmixer
#

pcm.!ss51 {
	slave.pcm       "duplex"
	slave.channels 6
	route_policy duplicate
}
```

---

