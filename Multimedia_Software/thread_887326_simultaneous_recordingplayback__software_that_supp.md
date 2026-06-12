---
title: "simultaneous recording/playback  software that supports pulseaudio"
date: 2008-08-12
forum: Multimedia Software
---

### Post by bezz86 on 2008-08-12
Hi all,
I'm currently trying to set up pulse audio to take an input from a sound device on Ubuntu and play it back on my debian laptop.

My setup is as follows:

sound source--->m-audio transit line in--->Ubuntu Hardy Heron--->Pulse Audio--->Debian laptop sound output

I've been trying different approaches for a few days and the only way I have found is to use a combination of arecord and paplay in the terminal window. Unfortunately this introduces latency issues, which I am trying to keep to a minimum.

I have been able to record a sound using sound recorder, and then play it back using amarok. The waveform on amarok seems to sync with the sound i'm hearing so here is minimal to no latency.

Now I'm wondering if there is any software available that will let me send my line input source over the network using pulse audio with no latency issues?

---

### Post by markbuntu on 2008-08-12
pulse audio has a built in rtp sender. You should look at the faq at the official pulse audio wiki. it is something like /pulse.org/wiki or wiki/.pulse.org. or something like that. Try a google search.

---

### Post by bezz86 on 2008-08-12
I haven't been able to get the rtp setup perfect yet to send between the 2 linux boxes.
I'm trying to shy away from rtp as in the end this setup will be used with a linux--->windows xp setup. Unfortunately the rtp module isn't available on the windows end ](*,)

---

### Post by markbuntu on 2008-08-13
You can also steam with vlc, you can probably set up a proxy on your network to catch it, but I don't know how. I have not got into that networking stuff for a long long time.

---

### Post by bezz86 on 2008-08-14
thanks, I'll give vlc a try. So far I've set it up between the two linux boxes via rtp, however I am getting some latency issues. I've been messing around with the daemon.conf file, trying to get the delay down a bit. Unfortunately using the src-sinc-fastest resample method seems to have made the delay even worse!

---

### Post by markbuntu on 2008-08-14
If the buffers are too big, that will cause latency problems. Also, network priority setting will effect streaming sound.

---

### Post by willskills on 2008-08-14
I'm sure Rudd-O won't mind me posting this, he dropped in to the #icecast IRC channel on freenode, and was chatting about something he is developing.

[http://projects.rudd-o.com/radio-jockey](http://projects.rudd-o.com/radio-jockey)

Is this what you are looking for?

Edit - I just re-read your post - I think even in a LAN environment, it is very difficult to not have some latency.

---

### Post by bezz86 on 2008-08-15
Just mucking around with vlc at the moment.. I've been able to get it to play a music file over the network to the windows pc quite easily, but for some reason it wont let me use my m-audio usb soundcard as the input device. Using the command 
```
cat proc/asound/devices
```

I was able to find my m-audio digital audio capture as [1- 0] however I haven't the slightest clue as to how to enter it into the 'Audio device name' field in VLC. :confused:

---

### Post by bezz86 on 2008-08-15
> **willskills said:**
> I'm sure Rudd-O won't mind me posting this, he dropped in to the #icecast IRC channel on freenode, and was chatting about something he is developing.

[http://projects.rudd-o.com/radio-jockey](http://projects.rudd-o.com/radio-jockey)

Is this what you are looking for?

Edit - I just re-read your post - I think even in a LAN environment, it is very difficult to not have some latency.

radio-jockey is next on the list, cheers!

---

### Post by markbuntu on 2008-08-15
> **bezz86 said:**
> Just mucking around with vlc at the moment.. I've been able to get it to play a music file over the network to the windows pc quite easily, but for some reason it wont let me use my m-audio usb soundcard as the input device. Using the command 
```
cat proc/asound/devices
```

I was able to find my m-audio digital audio capture as [1- 0] however I haven't the slightest clue as to how to enter it into the 'Audio device name' field in VLC. :confused:

If you are using pulse audio, you can set the default capture device in the Pulse Audio Volume Control, pavucontrol. Then you can set the vlc input device to default and that should work.

---

### Post by bezz86 on 2008-08-17
> **markbuntu said:**
> If you are using pulse audio, you can set the default capture device in the Pulse Audio Volume Control, pavucontrol. Then you can set the vlc input device to default and that should work.

I just tried this, however as I need to communicate with windows I had to set the default server to the windows box which meant that only the windows sources showed up in the volume control. Is there any way to get the ubuntu source to show up even though the default server is the windows pc?

Thanks heaps for your help so far!

---

### Post by bezz86 on 2008-08-17
used module-tunnel-source on the windows default.pa to grab the ubuntu line input as a source. All seems to connect except i only get static on the windows end.. no sound. Seems its one problem after another with this...

---

