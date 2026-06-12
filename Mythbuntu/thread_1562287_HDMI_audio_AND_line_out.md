---
title: "HDMI audio AND line out?"
date: 2010-08-27
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-08-27
Hi;

is it possible to setup mythbuntu so I can have HDMI audio AND line out? 

I am using HDMI audio for my tv setup, but would like to also use the line out for some wireless speakers i have.  When i plug in the line out connection i get no output from myth/mythbuntu.

I am guessing this is because HDMI is digital output?  I have checked and the headphone connection in alsamixer is not muted, although it is at volume 00 and i dont seem to be able to turn it up.

Any thoughts anyone?

Thanks

---

### Post by geekyhawkes on 2010-08-27
Im guessing it might be how i have my asound.conf setup.

While i am messing around with alsa, is there a way i can get myth to adjust the hdmi volume or does that mean resampling etc (as its a digital signal)?

Not the neatest asound.conf ever, but this is what i have modified it to, but still not audio out of the headphone socket

```

#new section

pcm.analog {
	type plug
	slave.pcm "analog-hw"
	hint {
	show on
	description "analog output"
	}
}

ctrl.analog {
	type hw
	card 0
	device 0
}

#################
#################

# pcm.mixed-analog [
#	type plug
#	slave.pcm "dmix-analog"
#	hint {
#	show on
#	description " Mixed analog output"
#	}
#}

#ctrl.mixed-analog {
#	type hw
#	card 0
#}

###########SECTION ABOVE DISABLED######

# ctl.optical {
#        type hw
#        card 0
#        device 1
# }

########### Section above disabled, no pcm optical defined#######

pcm.hdmiout {
        type hw
        card 0
        device 3
}


ctl.hdmiout {
        type hw
        card 0
        device 3
}


pcm.analog-hw {
	type hw
	card 0
	device 0
}

ctrl.analog-hw {
	type hw
	card 0
}
# MIGHT NEED A DEVICE ADDING IN HERE ABOVE


pcm.dmix-analog {
	type dmix
	ipc_key 1234
	slave {
	pcm "analog-hw"
	period_time 0
	period_size 1024
	buffer_size 4096
	rate 48000
	}
}

ctrl.dmixanalog {
	type hw
	card 0
}


pcm.!default {
        type plug
        slave {
                pcm multi
                rate 48000
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
}

ctrl.!default {
	type hw
	card 0
}

pcm.myth {
	type plug
	slave {
		pcm multi
		rate 48000
		channels 4
	}
	ttable.0.0 1.0
	ttable.1.1 1.0
	ttable.0.2 1.0
	ttable.1.3 1.0
}

ctrl.myth{
	type hw
	card 0
}	

######Probably in the wrong place#####


# pcm.optical {
#        type hw
#        card 0
#        device 1
#}


pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
	slaves.b.pcm "analog-hw"
	slaves.b.channels 2
        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1
        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
}

ctl.multi {
        type hw
        card 0
}

```

---

