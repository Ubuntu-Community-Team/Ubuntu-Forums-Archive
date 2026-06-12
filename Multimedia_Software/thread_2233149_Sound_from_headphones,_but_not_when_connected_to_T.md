---
title: "Sound from headphones, but not when connected to TV monitor"
date: 2014-07-06
forum: Multimedia Software
---

### Post by sam59 on 2014-07-06
Hello,
I have an old desktop with Gigabyte P35C motherboard and Intel Audio. I  have a DVI-HDMI connection to my Samsung TV and analog audio output  (black stereo) to the Audio Stereo input on TV. I had been running XP on  it for a while and no issues with sound or video. I decided to convert  my desktop into Ubuntu. So I installed Ubuntu on side with Windows.  Everything was working until I logged onto Ubuntu and hear no sound. I  kept thinking it was drivers issue. However I saw all cards were  detected ok and on pavucontrol would show the sound toggling when  playing something. I plugged in my headphones and voila I could hear the  sound. However for some reason the sound is not playing through the TV  speakers. It works find with XP. I tried and followed many suggestions  on this forum including the guide without success. So hope someone can  help me work through this issue. Thanks in advance!! Please let me know  if you want me to provide any information.

---

### Post by Vladlenin5000 on 2014-07-07
Hi, welcome.

The thing may be as simple as selecting the correct audio output device. Some cards show the line-out (rear) and the headphones (usually) front as two different devices. In this scenario it usually doesn't toggle automatically by sensing the plugged/unplugged status like the Windows proprietary driver does (more often than not, at least) so you have to manually select the intended output.

---

### Post by sam59 on 2014-07-07
Thanks for the welcome Galiza!! :) How do I select the intended output?

---

### Post by papibe on 2014-07-07
Hi sam59.

I had a similar problem long time ago. I had a Dell computer that had DVI connection. I connected it to the TV using a DVI-to-HDMI cable for the video, and a mini-plug to stereo RCA cable to transfer the sound. The TV was a Sony Bravia, and had an special connection to receive video and audio separately.

Just like you, initially I had no sound.

The problem was a little tricky. Although that TV interface was designed to receive signals separately, it was also auto detecting the sound. If it detected sound on the HDMI signal, it won't use the audio transmitted over the sound cable.

Apparently, my DVI-to-HDMI cable created a dummy sound signal: something like a inaudible hum that triggered the TV to think it was sound inthere.

After attempting to solve the problem through the TV menus, this is how I solved that problem:

When a computer recognizes a monitor is because the computer reads the monitor's [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") information of the monitor. An HDTV sends an extended EDID thus telling the computer it also can handle audio.

I obtained the TV's EDID data and save it on a file. Then I removed the extended block, recalculated the checksum, and tell the driver (Nvidia) to used the custom EDID file instead of requesting data to the TV. This way the computer would think that the TV is just a monitor (no sound).

I turn off both the computer and the TV, turn on the TV and finally when the computer rebooted, I had sound!

Hope it help. Let us know if you need more help with that.
Regards.

---

### Post by sam59 on 2014-07-07
Thanks Papibe.

I had run across such information while mucking  around on my own. Downloading nvidia-settings yielded an emtpy GUI  window (DO i need some drivers for this? The "Additional Drivers"  section has the "open source" version of Nvidia installed.)
I then  proceeded to download the read-edid utility and used the get-edid to get  the EDID block. I saw the byte 126 or 0x7E was 00  ([http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)).  Which I believe means there is no subsequent audio information  proceeding the EDID block in HDMI. So i think this portion is ok and  doesn't need any changing. I also notice that i don't have  /etc/X11/xorg.conf either in case I want to make any changes.

I  believe I tried unplugging HDMI from TV and just playing sound also, but  it didn't work though I don't think I rebooted or turned TV on or off.  Please let me know if I can provide any other information to sort this  out.

---

### Post by papibe on 2014-07-08
I used the Nvidia driver because I had an Nvidia card. In your case, we have to solve the problem using the Intel driver.

What is the size of the EDID data? Is it 128 or 256 bytes?

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by Yellow Pasque on 2014-07-08
Is there a reason you use black instead of green jack?

---

### Post by sam59 on 2014-07-08
Papibe, yes I also have a Nvidia GT512 card through which I have  connected my DVI output to TV. The audio comes from the gigabyte  motherboard audio analog out though with ALC889A Realtek.
The EDID is 128 bytes long. Here is the link to the pastebin: [http://pastebin.ubuntu.com/7766917/](http://pastebin.ubuntu.com/7766917/)

[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"): Dunno why I chose the black, but switching to green works in XP as well. I kept it for now as it is the true Line out.

---

### Post by Yellow Pasque on 2014-07-08
Make sure you have correct device selected in pavucontrol. If still not working, get more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by sam59 on 2014-07-08
Yes I had also checked that. When I play sound, the volume toggles but no sound from TV speakers...

Here is the Alsa info... : [http://www.alsa-project.org/db/?f=ca1051b2d28fe54971ba26e2b4a50bf83f372f1d](http://www.alsa-project.org/db/?f=ca1051b2d28fe54971ba26e2b4a50bf83f372f1d)

---

### Post by Yellow Pasque on 2014-07-08
```
Driver version:     1.0.2x-130606-v5.18rc8
```
^When did you install the custom Realtek drivers? That's usually not a good idea (this ain't Windows).

---

### Post by papibe on 2014-07-08
Thanks.

There it is, a 256 bytes EDID:
```
[    21.668] (II) NOUVEAU(0): 	00ffffffffffff004c2da50200000000
[    21.668] (II) NOUVEAU(0): 	2d100103801009780aaea5a6544c9926
[    21.668] (II) NOUVEAU(0): 	145054a1080081800101010101010101
[    21.668] (II) NOUVEAU(0): 	010101010101023a801871382d40582c
[    21.668] (II) NOUVEAU(0): 	4500a05a0000001e011d007251d01e20
[    21.668] (II) NOUVEAU(0): 	6e285500a05a0000001e000000fc0053
[    21.668] (II) NOUVEAU(0): 	414d53554e470a2020202020000000fd
[    21.668] (II) NOUVEAU(0): 	003b471e4617000a202020202020017c
[    21.668] (II) NOUVEAU(0): 	020322f1469004050320222309070783
[    21.668] (II) NOUVEAU(0): 	010000e2000fe305030167030c001000
[    21.668] (II) NOUVEAU(0): 	b82d011d8018711c1620582c2500a05a
[    21.668] (II) NOUVEAU(0): 	0000009e8c0ad08a20e02d10103e9600
[    21.668] (II) NOUVEAU(0): 	a05a0000001800000000000000000000
[    21.668] (II) NOUVEAU(0): 	00000000000000000000000000000000
[    21.668] (II) NOUVEAU(0): 	00000000000000000000000000000000
[    21.668] (II) NOUVEAU(0): 	000000000000000000000000000000e1
```
I would start by making sure the Nvidia proprietary driver is installed and properly running. Right now, the Nvidia open source driver (nouveau) is being used.

Then, you need to convert that file to a binary file, and then make this changes:
[LIST]
[*]Trim the size to 128 bytes (bytes would be referred as 0-127).
[*]Set the extension byte (126) to 0.
[*]Set the byte 127 to a value so that the checksum of the file gives zero.
[/LIST]
Then you need to create a custom xorg.conf that contains a line like:
```
Option	"CustomEDID" "DFP-0:/path/to/customEDID.bin"
```
where DFP, could be either DVI-0, or DVI-I-0 or something similar. Another look at the file /var/log/Xorg.0.log should tell you the proper name (when the Nvidia driver is in used).

Here's a similar work we did on a custom EDID: [Create a custom EDID]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid").

I would gladly help you with more details and directions if you need them
Let us know how it goes.
Regards.

---

### Post by sam59 on 2014-07-08
[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"):  I installed it after the clean install since audio wasn't working and I  was still trying to figure out what was going on. I knew the chip was  Realtek so I tried their drivers. I guess I should get rid of them

[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=774785") 				 				 					 						 	[**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=774785"):  Thanks. It is weird that get-edid utility returns a 128 byte EDID  whereas the open source NOUVEAU has a 256 byte one. I will try this out  and let you know if I have any questions or how it goes.

On a side note: I am using SSO login for this site, but it keeps logging me out every 1 minute.. what's up with that?

---

### Post by sam59 on 2014-07-08
Great. So as soon as I installed Nvidia drivers, rebooted, the sound came on. I didn't have to much with EDID or any settings.. simple as that.. *sigh*...

I also read that 256 byte EDID has been deprecated. Somebody should tell Nouveau to not use it anymore.

Thanks for all the help guys!! :)

---

### Post by papibe on 2014-07-09
I'm glad you got your sound working :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

---

