---
title: "Bluetooth Stereo (a2dp) in Gutsy"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by lodp on 2007-12-06
After ugrading to Gutsy recently, I was delighted to find that it was very easy to get my Bluetooth stereo headset (Nokia BH-501) to work, by just performing a one-step operation described here: [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)


> 
modify your ~/.asoundrc to contain

[QUOTE]pcm.bluetooth {
   type bluetooth
   device 00:11:22:33:44:55
}

[/QUOTE]

.. and then selecting "bluetooth" as the Alsa device in the various players.

Getting this to work in feisty was a pain in the behind -- installing various packages, inserting kernel modules, running daemons ... it seems the bluez-utils included in gutsy did away with that all.

Now I would like to re-write the out-dated community dokumentation page here: [https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

But there's a couple of things I don't know enough about:

The bluez-utils wiki page linked to above says you **don't ** have to get bluetooth-alsa, plugz, sco and all that. So does the new "bluetooth" alsa device provide two-way (duplex) connection, so you can use it with skype?

I actually couldn't make it to work with Skype -- when I selected the "bluetooth" alsa device, I did get mono sound on the left channel, but Skype would complain that the audio capture device wasn't working.

Can anyone comment on this?

---

### Post by frank320 on 2008-02-03
You make it sound soooo... simple. I have Gutsy, a Motorola DC800 (like a stereo
headphone), and can obtain its MAC(?) address via hcitool scan. Beyond that, I am
lost... and have spent hours trying to make it work.

For one thing, how do you "select "bluetooth" as the alsa device in the various players'?

All of which sez: HELP:(.

If you do write an updated HOWTO, I would read it instantly.

Regards...

---

### Post by inozemtsev on 2008-03-01
I just installed Ubuntu on my laptop today, still fighting with a few things, but my bluetooth headphones are working :) I have a pair of Etymotic Ety8s. 

Here's what I did:
[LIST=1]
[*] Make sure you have bluez-utils installed

[*] Put headset into pairing mode

[*] Run ```
hcitool scan
``` This will get you the headset's address.

[*] Use the bluetooth applet to pair the headset to the PC. The PIN was 0000 in my case, so the default PIN of 1234 in hcid.conf didn't work.

[*] Make an .asoundrc file in your home directory with the following contents:
```

pcm.bluetooth {
        type bluetooth
        device XX:XX:XX:XX:XX:XX
        profile "hifi"
}

```
The other "profile" options are "auto" and "voice".

[*] Edit /etc/bluetooth/hcid.conf. Find the line ```
discovto 0;
``` Add ```
pageto 2400;
``` after this line. This ups the page timeout. Without this, using any other bluetooth device causes uncontrollable stuttering in the audio. I have a bluetooth keyboard, and every keypress would kill the music ;) Experiment with this value.

[*] I use Rhythmbox for music. To route audio to bluetooth in any GStreamer app, use this command:
```

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink buffer-time=6000000 latency-time=1000000 device=bluetooth"

```
Huge latencies are needed for stutter-free playback when CPU use is somewhat high, like starting a program. Experiment with these values.

[*] To play sound through your sound card again, use
```

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```
I made two launchers on the panel to switch between speakers and headset for now. A proper script would be better, of course :)
[/LIST]

Now, the only thing I'd like to get to work are the control buttons on my headset. There is a ctl_bluetooth plugin in bluez_utils, but I have no idea how to get it to work. Anyone know this one?

---

### Post by mptpro on 2008-03-02
Thanks inozemtsev!

Your solution finally solved my problem of connecting my plantronics headset via bluetooth!

It works great in Amarok and Totem Player.

However, it doens't work with mplayer nor smplayer.  I think it may be that it uses xine instead of gstreaemer.

Any ideas?

---

### Post by uhappo on 2008-03-04
My simplest solution was to install Blueman BT-program and use Audacious

Here is the how-to

[http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=5](http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=5)

---

### Post by inozemtsev on 2008-03-05
One more thing: I found out that the skips in music weren't caused by insufficient buffers or the page timeout. The problem was that my DiNovo Edge keyboard switched to master mode, and the headset stayed as slave. So, every time I pressed a key, I got a skip in the music. The solution: switch the headset to master mode also:

```
sudo hcitool sr XX:XX:XX:XX:XX:XX MASTER
```

Now, does anyone know if it is possible to make hcid do this automatically when the headset is paired? I have to run this every time I reconnect my headphones, and it's annoying.

---

### Post by inozemtsev on 2008-03-05
Solved. Add to your /etc/default/hcid.conf:

```

device XX:XX:XX:XX:XX:XX {
	name "Xxxx";
	auth enable;
	lm master;
	passkey "0000";
}

```

---

### Post by lodp on 2008-03-12
The Ubuntu Wiki page for bluetooth audio is still out-dated and refers mainly to the low-quality sco thing.

..to get back to my question: can anybody confirm that just by installing bluez-utils (and performing roughly the steps that inozemtsev posted above, you can also get a two-way (sound+microphone) connection to a regular (non-ad2p) bluetooth hands-free?

I could go and update the wiki page according to this then, and delete all that misleading stuff about sco..

---

