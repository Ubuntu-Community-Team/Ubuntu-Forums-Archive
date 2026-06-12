---
title: "Bluetooth headphones"
date: 2009-01-22
forum: Multimedia Software
---

### Post by John Jason Jordan on 2009-01-22
I have been struggling for over a week to get my Sony DR-BT50 headphones working in Intrepid. In Hardy all I had to do was turn them on before launching a sound app and the sound automatically came out of the headphones instead of the speakers. After upgrading to Intrepid it seems impossible. And just now I tried the live CD of Jaunty and I couldn't get them to work in Jaunty either. The headset works fine with the bluetooth transmitter that I bought for my iPod. And they are paired in the bluetooth applet. Also, I have a bluetooth mouse and a bluetooth cell phone, and both are paired and connect fine. In other words, the problem is in the audio modules and their configuration, not bluetooth.

I have tried the how-to here:

[http://forums.overclockers.com.au/showthread.php?t=694010]("http://forums.overclockers.com.au/showthread.php?t=694010")

But when I try the pactl command on line 18 it gives me an error that the module cannot be found (when the pulseaudio module is not running) and, when the pulseaudio module *is* running it takes a long time and then times out. After it times out pulseaudio is locked up so hard I have to use kill-9 to kill it. There are no messages in any logs. Even strace shows no messages.

I currently have about 20 hours of personal time invested in troubleshooting this. So far I haven't gotten even a pop or click out of the headphones. Meanwhile, regardless of all the packages I have installed and uninstalled, tweaked, configured and otherwise mutilated, the speakers work perfectly.

I could really use more suggestions. Does anyone have any ideas?

---

### Post by markbuntu on 2009-01-23
Here are a few more places with bluetooth info

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

---

### Post by John Jason Jordan on 2009-01-23
> **markbuntu said:**
> Here are a few more places with bluetooth info

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

The Ubuntu community link is essentially the same as the overclockers page. The problem is that the pactl commands on line 15 in the Ubuntu community page hang pulseaudio and give me a timeout message. Since I cannot tell pulseaudio that the headphones exist, when I later go into pulseaudio manager and click on the Devices tab, it does not show any bluetooth devices. The author of the community page gave great instructions, but not a word about what to do when they don't work. 

As for the wiki, I tried a command line that I found there:

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "sbcenc ! a2dpsink device=XX:XX:XX:XX:XX:XX"

(Changing the address for my headphones.) This is supposed to make it work for at least totem, rhythmbox and banshee. However, afterward I could launch any of the three applications, but they would all hang if I tried to play anything.

Fortunately the wiki gives another line to switch it back to speakers:

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

And after giving it this command the three applications play sound without hanging. But still only through the speakers.

My headphones worked fine in Hardy. But ever since I upgraded to Intrepid I have not been able to get a peep out of them. Not even a pop or a click.

---

### Post by 005587 on 2009-03-25
I get stuck on line #18 where is says 'connection refused'
I can't get past this error for nothing....

---

