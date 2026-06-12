---
title: "No sound through bluetooth headset"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by xueg0i on 2007-03-27
Hello,

To use skype more conveniently I have a bluetooth dongle and headset. These work perfectly on winxp, but in Feisty I run into some problems. Pairing works, but the moment I should get some sound from either skype or some other source, I do hear the headset connect (soft ssssssssssssssh) and I see on my terminal:
```
xueg0i@my_box:~$ btsco -v 00:12:EE:15:B5:9B
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected
Using interface hci0
speaker volume: 12 mic volume: 11
[COLOR="Red"]i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+VGS=12
Sending up speaker change 12
```
[/COLOR]but no sound!

When disconnecting I see:
[HTML]speaker volume: 12 mic volume: 11
driver is not in use
disconnected SCO channel[/HTML]
I installed all avaible bluetooth debs and loaded the btsco module. I'll post a relevant part of dmesg:
```
snd-bt-sco revision 1.16 $
snd-bt-sco: snd-bt-scod thread starting
snd-bt-sco: playback_open
snd-bt-sco: prepare ok bps: 16000 size: 5462 count: 24
snd-bt-sco: prepare ok bps: 16000 size: 5462 count: 24
snd-bt-sco: playback_trigger 1
snd-bt-sco: setting playback to bspcm
Bluetooth: SCO (Voice Link) ver 0.6
Bluetooth: SCO socket layer initialized
snd-bt-sco: capture_open
snd-bt-sco: capture_prepare
snd-bt-sco: prepare ok bps: 16000 size: 5462 count: 24
snd-bt-sco: capture_prepare
snd-bt-sco: prepare ok bps: 16000 size: 5462 count: 24
snd-bt-sco: capture_trigger 1
snd-bt-sco: setting capture to bspcm
snd-bt-sco: capture_trigger 0
snd-bt-sco: setting capture to NULL
snd-bt-sco: playback_trigger 0
snd-bt-sco: setting playback to NULL
snd-bt-sco: Disposing of previous socket count 3
snd-bt-sco: file_count is 1 (expected 3)
hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
hci_scodata_packet: hci0 SCO packet for unknown connection handle 1

```
I hope someone can point me in the right direction. All help is apreciated,

Xueg0i.

---

### Post by the.unclean.cpp on 2007-03-27
Well...I don't really have a solution...but why the heck are you using Feisty? Wait a bit until it's done...You have Edgy Eft instead...Which works great!

---

### Post by xueg0i on 2007-03-27
Well, I understand your concern. I have Edgy on my desktop, but in that case I was not even able to pair my headset. Feisty also resolved some other issues I had with my new laptop.

For the problem at hand, I don't think it is Feisty related. I guess it has something to do with relaying the sound in the right way.

---

### Post by dnns on 2007-03-29
Same problem here, finally got my Logitech HS02-V07 to pair with my diNovo Laser bluetooth dongle after much trouble and now this :sad:. Hint: if you're getting pairing errors such as:

"Can't create connection: Input/output error"

"Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied"

then try deleting

/var/lib/bluetooth/xx : xx : xx : xx : xx/linkkeys                      #x's are your dongle's MAC address

Now I'm going to try and sort out the sound problem. I'll post here if I make any progress.

---

### Post by fruchtsorbet on 2007-03-31
the same here (using Feisty):
pairing and connecting works, but no sound ... :(

---

### Post by udude on 2007-04-10
Same here. using Motorola HT-820 as headset and the PC-850 dongle.
I tried skype and xmms. On edgy it works great, but I had an annoying SPDIF issue so I couldn't hold myself and upgraded ](*,) 
feisty fixed the S/PDIF problem (yey!) but when it comes to bluetooth system hangs. It seems that when user space apps are starting to send the actual audio, the whole thing freezes... i.e. by pressing the skype call button or xmms play. 
mouse not moving, kbd not responding, no graphic updates (the kernel returned its soul to the creator?). oh, and yes, In some of my attempts I also got the static from the headset

Is there a bug on this issue we can follow?

Update Apr 11:
After dist-update today, system no longer hangs. BT-Sound is still not working on headset. 
Also no noticeable error/warning related messages in syslog, dmesg, or the btsco app.

---

### Post by tlacuache on 2007-04-27
> **udude said:**
> ...when it comes to bluetooth system hangs. It seems that when user space apps are starting to send the actual audio, the whole thing freezes... i.e. by pressing the skype call button or xmms play. 
mouse not moving, kbd not responding, no graphic updates ...

I still do have this problem on feisty. I followed the directions linked to from [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup). I can connect to the headset fine using btsco, and I can try to start a call in Skype, and I hear the speaker on my ear "turn on", but then my whole computer locks up. What can I do?

I read something somewhere about setting enableavrcp to 0 to avoid freezes with bluetooth, but i don't know what file this goes in.

Any help?

-Seth Grover

---

### Post by PartisanEntity on 2007-04-28
Are there any updated How To's to get a bluetooth headset working with Feisty?

---

### Post by Roner on 2007-04-29
I spent a lot of time on this, and got it up and running on Feisty. The howto is [here]("http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset").

---

### Post by John Jason Jordan on 2007-11-18
That how-to didn't work for me, but I found a different one that did work. Here is a how I got sound out of my new Sony DR-BT50 bluetooth headphones with Gutsy amd64 on a Lenovo T61 Thinkpad. Bluetooth is working fine and I managed to get the headphones paired up using Blueman. Blueman is not in the Ubuntu repositories, but you can download it and install it with Gdebi. However, although I got the headphones paired up fine, for a long time I couldn't get sound (e.g., from Rhythmbox) out of the headphones instead of the speakers or the headphone jack. I found the secret here:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration)

I had to make a file ~/.asoundrc and put into it:

pcm.bluetooth {
	type bluetooth
	device 00:13:A9:B2:82:5F
}

Where the device is the address listed in Blueman. 

After getting the headphones paired up I found another item in the volume control dialog box. Previously under File > Change Device it listed "HDA Intel (Alsa mixer)" and "Analog Devices AD1984 (OSS Mixer)." Now there is a new one, "BT Headset (Alsa Mixer)." After checking it and making the .asoundrc file the headphones are working perfectly. The sound from these headphones is awesome. If you are a serious music fan you won't be disappointed.

I also have the volume buttons working (since flashing the BIOS). They work fine for controlling the sound from the speakers and the headphone jack, but they don't have any effect on the headphones. Oh well, the volume controls on the headphones work fine, and that is all I need.

---

