---
title: "hda-intel channels keep being reassigned"
date: 2010-08-17
forum: Multimedia Software
---

### Post by jabeavers on 2010-08-17
I'm using asound.conf (.asoundrc) to split the channels on my SigmaTel STAC9221D into 4 independant stereo outputs. I've got it working, but the channels keep being assigned to different routes (or whatever). I can't figure out why they keep moving, and my sound gets put on different channels. I don't even know where to start with this, but I will post my asound.conf file and part of my alsa-base.conf file.

asound.comf:
pcm.!default
{
	type plug
	slave.pcm "ch1-2"
	ttable.0.0 1
	ttable.1.1 1
}
ctl.!default
{
	type hw
	card 0
}
pcm.outs
{
	type dmix
	ipc_key 2048
	slave
	{
		pcm "hw:0,0"
		channels 8
		periods 128
		period_time 0
		period_size 1024
		buffer_size 4096
	}
	bindings
	{
		0 0
		1 1
		2 5
		3 4
		4 3
		5 2
		6 6
		7 7
	}
}
pcm.ch1-2
{
	type plug
	slave
	{ 
		pcm "outs"
		channels 8
	}
	ttable.0.0 1
	ttable.1.1 1
}
ctl.ch1-2
{
	type hw
	card 0
}
pcm.ch3-4
{
	type plug
	slave
	{
		pcm "outs"
		channels 8
	}
	ttable.0.2 1
	ttable.1.3 1
}
ctl.ch3-4
{
        type hw
        card 0
}
pcm.ch5-6
{
	type plug
	slave
	{
		pcm "outs"
		channels 8
	}
	ttable.0.4 1
	ttable.1.5 1
}
ctl.ch5-6
{
        type hw
        card 0
}
pcm.ch7-8
{
	type plug
	slave
	{
		pcm "outs"
		channels 8
	}
	ttable.0.6 1
	ttable.1.7 1
}
ctl.ch7-8
{
        type hw
        card 0
}


pertinent info from alsa-base.conf:
options snd-hda-intel model=5stack position_fix=1 index=0

I used the position_fix=1 because I was getting garbage from the left channel and this fixed it.

Please help, this is the last step to getting my perfect sound!! :)

John

---

