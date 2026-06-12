---
title: "split 7.1 device into 8 mono devices"
date: 2013-09-16
forum: Multimedia Software
---

### Post by aspade on 2013-09-16
Taking advice from here [http://forums.debian.net/viewtopic.php?t=57733](http://forums.debian.net/viewtopic.php?t=57733)
I created my .asoundrc file given below. This is for a creative sound blaster live SB 0410 card with 7.1 surround sound.

I am able to split the front left and right (channel 0 and 1) into separate audio devices with each one playing a different song.
I am not able to do the same on the other outputs.

Can someone help out on this.


```
pcm_slave.eightchannels {
   pcm "hw:0,0"
   channels 8
}


#black
pcm.stereo1 {
   type plug
   slave.pcm{
      type dshare
      ipc_key 87882222
      slave eightchannels
      bindings [ 2 3 ]
   }
}


#yellow
pcm.stereo2 {
   type plug
   slave.pcm{
      type dshare
      ipc_key 87882222
      slave eightchannels
      bindings [ 4 5 ]
   }
}




#blue
pcm.stereo3 {
   type plug
   slave.pcm{
      type dshare
      ipc_key 87882222
      slave eightchannels
      bindings [ 6 7 ]
   }
}


#green
pcm.mono_4_1 {
   type plug
   slave.pcm{
      type dshare
      ipc_key 87882222
      slave eightchannels
      bindings [ 0 0 ]
   }
}


#green
pcm.mono_4_2 {
   type plug
   slave.pcm{
      type dshare
      ipc_key 87882222
      slave eightchannels
      bindings [ 1 1 ]
   }
}

```

---

