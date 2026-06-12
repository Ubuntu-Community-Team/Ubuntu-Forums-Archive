---
title: "TvTime How to for Kworld plustv analog lite pci (SAA7134)"
date: 2008-08-09
forum: Multimedia Software
---

### Post by buntunub on 2008-08-09
**UPDATED - 1 February 2009 - (General Guide for Ubuntu (Hardy/Intrepid 32 or 64 bit, but also proven to work in Fedora10 64 bit as well)**

This is by no means comprehensive for this crazy chip set, so take out of this what ya need and add to the thread to help others. This ~should~ work for most saa7134 chip sets. Here goes -
References:
[Gentoo wiki]("http://en.gentoo-wiki.com/wiki/Saa7134")
[V4LWiki]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page")

Some background. lspci -vv info

```
03:0a.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
	Subsystem: KWorld Computer Co. Ltd. Device 7128
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (4000ns min, 10000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fdefe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

```

dmesg | grep saa

```
saa7130/34: v4l2 driver version 0.2.14 loaded
saa7134 0000:03:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
saa7134[0]: found at 0000:03:0a.0, rev: 1, irq: 18, latency: 32, mmio: 0xfdefe000
saa7134[0]: subsystem: 17de:7128, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
saa7134[0]: board init: gpio is c0407f
input: saa7134 IR (Kworld/Tevion V-Str as /devices/pci0000:00/0000:00:10.0/0000:03:0a.0/input/input7
saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner' 2-0060: chip found @ 0xc0 (saa7134[0])
tuner' 2-0061: chip found @ 0xc2 (saa7134[0])
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134[0]: registered device radio0
saa7134 ALSA driver for DMA sound loaded
saa7134[0]/alsa: saa7134[0] at 0xfdefe000 irq 18 registered as card 1
saa7134 IR (Kworld/Tevion V-Str: unknown key: key=0x03 raw=0x03 down=1

```

In this configuration I have just that card in the system. You will have to swap configurations for multiple card arrays (card, tuner, video, etc.) but the basics are the same. Hardy picks this card up on as unknown, and auto assigns it the incorrect tuner/card, so you'll have to fix that. Picture quality is generally excellent ootb, but sound [COLOR="Red"]IS[/COLOR] an issue. Some have reported that splitting the configurations up into two separate cards works, but I do it here the old fashioned way.

1. Plug your card in and power up the machine.
2. Upon boot up and login, pop a terminal and check your lspci and dmesg (as above) to make sure that the card was detected. If it wasn't, then you will have to manually modprobe your card into the kernel which I am not going to cover here.
3. Refer to that Gentoo link above for tuner and card inputs. You have to insert some options into your /etc/modprobe.d/options file thusly -

(for Ubuntu)
```
$sudo gedit /etc/modprobe.d/options
```

(For Fedora)
```
#gedit /etc/modprobe.d/saa7134
```

I input the following:

```
#options saa7134 card=42 tuner=17
options saa7134 card=59 tuner=56
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1
```

note: card and tuner #'s [COLOR="Red"]WILL[/COLOR] vary according to your specific card and input (NTSC, PAL, SECAM, etc). However, tuner=17 seems to be the common tie for all of the Kworld cards that I have stumbled across. *Card 42, Tuner 17 works as well but I commented it out above because the other combo worked a little bit better for me.*

Some report that the following should be added to the file as well, however, I did not add this, and have no issues with my card.

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
```

4. Reboot.
5. Launch tvtime. You should get a nice picture, but probably no sound. You can use tvtime channel scan options here, which work quite well. Now, on to sound. Two options here - alsa, or oss. The Saa7134-alsa-V4L wiki (linked above) has detailed instructions for oss, which I now use because there is no audio offset like there is when I use ALSA. For alsa, you don't need to do much of anything in Hardy because the saa7134-alsa module is already loaded. [COLOR="Red"]The KEY is, either way, you must specify 32000 for sampling rate for this card to get regular sound[/COLOR]. In general, this should work from terminal after you start tvtime -

```
$arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```

You will probably see a delay of a second or two from live tv here. To fix this, you will need to specify a device. This is the tricky part here because you need to know what hardware you have for sound. You can do in terminal -

```
$arecord -l
```

to see what you have. I have a fairly general setup (no fancy sound card here!), and this works for me, but in truth, I have never been able to achieve 100% synch, and it does drift over time or when switching channels -

```
$tvtime -M | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51
```

This command gives me tvtime in windowed mode with perfect picture and synchronous sound. Almost home now!.. I hate having to use a terminal every time I want to use tvtime, and using arecord like that always messes my system up because it stays open even after I close tvtime, forcing me to manually kill it every time. So, I created a bastardized script which you can create using vim, vi, nano, or any text editor like gedit, kate, etc.. in /home/user, named kworld_alsa.sh to make things easier as follows:

(For ALSA)

[PHP]#!/bin/sh
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51 & tvtime -M;
wait 1 tvtime
killall arecord;
killall aplay;
killall tvtime[/PHP]

(For OSS. Like said above, oss works perfectly for me with fully synchronized sound without the use of the audio cable. Note that you will have to install oss for this to work.)

[PHP]#!/bin/sh 
sox -c 2 -s -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp & tvtime -M; 
wait 1 tvtime 
killall sox; 
killall tvtime[/PHP]

Note: Dont forget to make this script executable with chmod +x, or simply right click the script and check the "Allow executing file as program" check box in the permissions tab of the properties. 

Yea, I know, its a hack job but it works. I'm no shell scripting guru so I do what I can. Inputs are most welcome. :)

I hope this helps. I have spent waaaay too much time on this google'ing around and following various wiki's mostly to no avail, so believe me, I definitely feel your frustration with getting these cards working in Linux! I have not heard of a working solution with these cards in Mythtv, so if anyone knows how to get that working, please feel free to post a solution! Please do post your solutions/workarounds, because everyone benefits!

---

### Post by k40nflux on 2008-09-13
this was a wonderful thread! thanks for all the help, but im still having problems with audio. when i do arecord -D etc etc, it seems to work, but i dont hear audio, all i hear is two loud blips and then it gives me underrun errors. 

heres my lspci:
```

imtiaz@kocher:/dev$ lspci | grep SAA
02:08.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

```

dmesg:
```

imtiaz@kocher:/dev$ dmesg | grep saa
[   41.621347] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.623479] saa7134[0]: found at 0000:02:08.0, rev: 1, irq: 19, latency: 64, mmio: 0xfe1ffc00
[   41.623488] saa7134[0]: subsystem: 17de:7128, board: :Zolid Xpert TV7134 [card=43,insmod option]
[   41.623507] saa7134[0]: board init: gpio is c0407f
[   41.762336] saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
[   41.762354] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762368] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762382] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762396] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762410] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762423] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.762437] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.313765] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   42.321757] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   42.374637] saa7134[0]: registered device video0 [v4l2]
[   42.374666] saa7134[0]: registered device vbi0
[   42.889153] saa7134 ALSA driver for DMA sound loaded
[   42.889197] saa7134[0]/alsa: saa7134[0] at 0xfe1ffc00 irq 19 registered as card -2
[ 2063.305041] saa7134 ALSA driver for DMA sound unloaded
[ 2112.092903] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 2112.093299] saa7134[0]: found at 0000:02:08.0, rev: 1, irq: 19, latency: 64, mmio: 0xfe1ffc00
[ 2112.093311] saa7134[0]: subsystem: 17de:7128, board: :Zolid Xpert TV7134 [card=43,insmod option]
[ 2112.093324] saa7134[0]: board init: gpio is c0407f
[ 2112.211066] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[ 2112.219055] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[ 2112.251025] saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
[ 2112.251044] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251059] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251073] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251086] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251100] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251114] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.251128] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 2112.272589] saa7134[0]: registered device video0 [v4l2]
[ 2112.272963] saa7134[0]: registered device vbi0
[ 2112.496244] saa7134 ALSA driver for DMA sound loaded
[ 2112.496291] saa7134[0]/alsa: saa7134[0] at 0xfe1ffc00 irq 19 registered as card -2

```

when i try to use arecord i get this:
```

imtiaz@kocher:/dev$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplayRecording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
underrun!!! (at least 663.848 ms long)

```

and arecord -l shows
```

imtiaz@kocher:/dev$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Live [SBLive! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4780]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Camera [Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


i think card=43 may be wrong i dont have a zolid xpert, i have a kworld analog plusTV lite PCI card. anybody got any ideas for me?

tvtime displays a picture, but i cant get audio to work for the life of me!

thanks!!

---

### Post by kingpin7151 on 2008-10-18
make sure ur audio cable is plugged into ur sound card.... seriously, i am such a noob and have a sound card and the pci tv card and i had the audio cable plugged into my sound card but got nothing, then plugged it into the line out audio on my sound card and hey presto it worked...

only problem is that all my other programs run through the original sound card and so i havta keep switching the plugs... also the sound from the pci tv card doesnt stop... even when tv time is stopped... (unless i switch off the computer and back on)


dunno, think it might be due to the fact i have the sound card ASWELL as the tv card... 

anyone have any ideas?

---

### Post by buntunub on 2008-10-27
Follow the steps of the guide, but particularly:

> 3. Refer to that Gentoo link above for tuner and card inputs. You have to insert some options into your /etc/modprobe.d/options

You can experiment around with this until you get optimal settings. You also need to be sure your using the correct frequency settings on your app and etc, etc. Lots of things to futz around with here. I know this chipset works very very well in Intrepid as I have been testing it extensively. I get a much better quality picture and WAY better sound output now strait out of the box with Kubuntu Intrepid and all I had to do was set the card options.

---

### Post by adamkane on 2009-01-06
Many thanks for the HOWTO. I have a KWorld PlusTV PVR TV 7134 SE. The HOWTO didn't work, until I disabled Compiz. So the following step should be step 1.

System -> Preferences -> Appearance -> Visual Effects -> None

---

### Post by buntunub on 2009-02-01
After many more moons of messing around with this card on both Ubuntu an Fedora, I have now tweaked and hacked my way to this card running very well indeed now. I have updated the thread with the newest info above.

---

### Post by shane2peru on 2009-05-27
Thanks!!! this worked for me, how can I record the input?  Record my old vhs to put them on dvd?

Shane

---

### Post by wbee on 2009-05-27
Buntunub,

Thank you.

Walking much the same frustrating path you walked,I also got it so the audio and video were about a second and a half apart.

Since you invited comment,I post this asking for an alternative,though I appreciate the work and your post.

I have card=82 tuner=54 and video in 9.4. It could be my imagination,but it seems a little better than it was in 8.10.

When I entered $arecord -l in the terminal,it returned command not found.

My sound card is a Soundblaster Audigy SE,which the terminal recognizes as sound card 0.  System>Preferences>Sound> recognizes this to be CAO106(Alsa Mixer)

My saa7134 tuner is TDA 8275,which the terminal recognizes as sound card 1. (TDA 8275 was the part recognized as tuner=54.)

I have the audio output from the TV tuner card cabled to the *shared line in/mic in input on the aforementioned sound card.

Is there a way to get Ubuntu  to recognize a 3200 sampling rate,separating that function from the rest,to simply switch among the preferences?

That is,for example,to play audio cds, streaming fm, and tv time while listening to music, simply use the three "auto detects" and the CAO106 as the default mixer device.

Is there a way to avoid having to always command at the beginning and kill at the end?(Though I do appreciated the information and the work it took to get it.)

If so,couldn't I simply choose the line in,instead of analog front,and feed the saa7134 from audio playback to the same mixer? It would be two channel stereo in either instance.

Understand I know that might be an ignorant question,but with the tv card and the sound card cable linked,is there a way to recognize the 3200,to simply select the audio source?

Thank you,

----------------

W

---

### Post by shane2peru on 2009-05-29
Ok, I have been digging like crazy to find out how to capture my vhs videos.  This is driving me crazy because I don't think it should be sooo complex.  My buddy with Windows hooked his up and started recording vhs stuff  :oops:  and me the "geek" can't seem to get it with my Linux OS.  Here is what I have dug up:

TV Card notes
**To play video:**
```

mplayer -tv driver=v4l:norm=ntsc:channel=3:amode=1:adevice=/dev/dsp1:width=704:height=480:chanlist=us-cable tv:// 
```
&#8226; this one needs work still

--------------------------------------------------------------------------------------------
```
play -q -s -c 2 -r 48000 -t alsa /dev/dsp1 & tvtime
```

&#8226; Works with distorted sound

-------------------------------------------------------------------------------------------------------
 
```
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - & tvtime 
```
&#8226; seems to work too with sound distortion

--------------------------------------------------------------------------------------
```

#!/bin/sh
echo
tvtime  &

sleep 4

echo
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay - &

```
#this script works for me

------------------------------------------------------------------------------------------------
**To Record Video:**
```

cat /dev/vbi0 > newfile.mpg
```
or 
```
cat /dev/video0 > test.mpg 
```
alt. you can try cp
those are what everyone reccommends, however they don't seem to work with analog card.

---------------------------------------------------------------------------------------
```
mencoder -tv driver=v4l -oac copy -ovc copy -o priceless-video-data.avi tv:// 
```
Seems to produce something too, although not currently working
----------------------------------------------------------------------------------------

```
gst-launch v4l2src ! filesink location=out.mpg
```
yet another option didn't work for me.

-----------------------------------------------------------------------------------------
			
```
mencoder -tv driver=v4l2:device=/dev/video0:input=1:width=768:height=576 tv:// -o test001.avi -oac lavc -ovc lavc
```
!!!This sort of worked!!!

ntsc=720x480
---------------------------------------------------------------------------------------------------------------------

```
mencoder -tv driver=v4l2:device=/dev/video0:input=1:width=768:height=576 tv:// -o test001.avi -oac lavc -lavcopts acodec=ac3:abitrate=192 -srate 48000 -af lavcresample=48000 -of mpeg -ovc lavc -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800: keyint=15:dc=10:vstrict=0 -vf scale=720:576,harddup -ofps 25

```

So that is my notebook thus far.  If anyone is good with command line mencoder seemed to be the only thing to give me some actual output video, although it was not good at all (bw with green lines) it was more progress than I have made thus far.  I think many of those commands were put together with PAL and I use NTSC which could be causing some of the problem.  I'm really pretty ignorant about all this, just plugging in commands and seeing what I get.  These two pages were of great information:

[http://www.datorklubs.lv/~ralfs/pc/linux/v4l.html](http://www.datorklubs.lv/~ralfs/pc/linux/v4l.html)

[http://lwn.net/Articles/261820/](http://lwn.net/Articles/261820/)

I also took some of these from the forums here.  Like I said, the expertise of some of you all would greatly be appreciated!

Shane

**EDIT:**
```
mencoder -tv driver=v4l2:device=/dev/video0:input=2:width=352:height=576:fps=30:alsa:adevice=hw.0:amode=0:audiorate=44100:forceaudio:immediatemode=0 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=3000:vbitrate=2500:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg
```
This seems to work the best for recording thus far, however I still have a green picture although it is fairly clear.  And still no audio in the recording. (I have s-video cord or rca jacks and seems as though the s-video works a little better.)

---

### Post by shane2peru on 2009-05-29
Ok this is what I have come up with thus far.  ```
#!/bin/bash
mencoder -tv driver=v4l2:device=/dev/video0:input=1:norm=ntsc:outfmt=yuy2:width=720:height=480:fps=30: -o "testvideo.avi" -nosound -oac lavc -ovc xvid -xvidencopts bitrate=3000:aspect=4/3 -ffourcc xvid tv:// &
sleep 4
arecord -D hw:1,0 -c 2 -r 48000 -f S16_LE -t wav testvideo.wav 
```
to stop it I run ```

killall arecord mencoder
```

Then to merge the video and audio files, I have to run:
```

mencoder -audiofile testvideo.wav -oac mp3lame -ovc copy testvideo.avi -o mergedvideoaudio.avi

```
The audio still comes out distorted, however we are making progress.  If anyone has any ideas about getting the audio  a little cleaner I would love to hear it! 

Shane

---

### Post by Gen2ly on 2009-05-29
Ok, i think i got it now.  Looks like this is a video capture program for tv tuners, right?  I know that video capture is still pretty new in Linux so i guess alot of ppl just dive right in.

---

### Post by shane2peru on 2009-05-29
ok here it is:

```

mencoder -v tv:// -tv driver=v4l2:device=/dev/video0:input=1:adevice=/dev/dsp1:norm=ntsc -ovc raw -oac pcm -of avi -o experimentaltest.avi

```

This will record the audio and video together.  The problem is the audio is still distorted, however really it isn't it seems that if it is played in vcl you can slow it down and it comes out fine.  It is as though it is recorded at a slightly faster speed, and played back consequently the same way, faster.  I don't have any idea for fixing this issue, but the good news is this can be done!

Shane

---

### Post by shane2peru on 2009-05-30
Ok, here is the final edition:
```

mencoder -v tv:// -tv driver=v4l2:device=/dev/video0:input=1:norm=ntsc:adevice=/dev/dsp1 -srate 48000 -speed .7 -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -of avi -o $videoname.avi

```

This is what I'm using.  I had to add the -speed .7 option to slow down my video it was playing back too fast and the audio was distorted.  I hope someone can use this to help.

Shane

---

### Post by shane2peru on 2009-06-01
Where there is a will there is a way.  Last one worked sort of, but this one seems to work well, I did a short clip, burned it to DVD (RW) and it seemed to work very well.  I ended up having to record the sound with arecord, instead of mencoder, mencoder refused to record sound for me.  Here is my script:
```

#!/bin/bash
read -p "What do you want to name the video?   :"  videoname
read -p "How many minutes for the video? (guess high if in doubt)     :"  time
read -p "Where do you want the video saved to? (full path place (no trailing slash))  :" location
b=$((time*60))
mencoder -v tv:// -tv driver=v4l2:device=/dev/video0:input=1:norm=ntsc:width=720:height=480:fps=29.97 -nosound -ovc lavc -lavcopts vcodec=mjpeg -of avi -o /home/$USER/$location/$videoname.avi & arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav /home/$USER/$location/$videoname.wav &

sleep $b
killall -9 mencoder arecord
mencoder -audiofile /home/$USER/$location/$videoname.wav -oac mp3lame -ovc copy /home/$USER/$location/$videoname.avi -o /home/$USER/$location/merged$videoname.avi

exit

```

This is posted as a help, please be careful using it as you could potentially overwrite videos you already have.  It also creates very large files you will need a lot of extra space for recording videos.  Any questions feel free to ask and we will see what we can do to help.  

This is meant strictly as an addition to this thread, it isn't meant to steal from this thread.  I have the same card, and therefore figured all this info should just go in one place.

Shane

Thanks buntunub for helping me get my card working properly.

---

### Post by shawnvdm on 2009-07-26
Hi Shane2peru      

Not sure if you have sorted out your problems yet but I have long struggled down this path and you may find some of my results usefull, else ignore:  I made a file called record-tv, then chmod +x to make it exacutable The opening a word editor added the following:
 __________________________________________   

#!/bin/bash 

CH=$1
BITRATE=$2
TIME="$3"
FILE="$4"

TARGETDIR=/mnt/win_d_linux/tv
NAME="`/bin/date +%Y%m%d_%H%M`_ch"$CH"_$FILE".avi.pcm

#video1 = asus  

mencoder -tv driver=v4l2:device=/dev/video1:adevice=/dev/dsp2:audiorate=32000:width=640:height=480:input=0:normid=0:channel=$CH:chanlist=us-cable -vf yadif -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=$BITRATE:keyint=30:vhq:vqmin=3:vqcomp=0.7:aspect=4/3,v4mv,q=5 -oac pcm -endpos $TIME -o $TARGETDIR/$NAME tv://   

__________________________________________________   

I put this in a bin directory in my home folder. So I just open a terminal and type 
record-tv the-tv-channel-number the-bitrate-I-want(usually 3800) the-length-to-record a-file-name 
e.g 
record-tv 20 3800 00:30:00 naruto-anime 

This record channel 20 for 30 minutes

 ________________________________________   

an explanation of the values used.
I have 1 audio card, 2 tv cards. 
My saa7133 is my 2nd tv card.  so it gets the index /dev/video1. The first card gets video0. 

The Sound part means my audio card is dsp0, the 1st video card's sound is dsp1 so my saa7134 card is dsp2. You will have to change these numbers depending on your setup. 
*You have to use audiorate=32000 as the tv soundcard is not 48000.

Mencoder assume this is the default. Your audio comes out really funny. I used gnome alsa mixer to set the recording levels on the card (once only, kmixer does not have this option). It hasn't changed in last 4 years. 

If you run mencoder its initial screen tells you the cards input and norm numbers and what they mean. Norm 0 for me is NSTC. input 0 is the tv. So if you want to record a video tape you would change input to 1 (for me) to record composite in.   

_______________________________________   

If you have a good source you may select to copy to the hard drive first then apply the program again with the codec you want and the deinterlacing you want. Especially if you have a slower pc.   I selected msmpeg4v2 a long time ago for compatability reasons. Other than file size it seems to give me quality at the right speed. My older pc's struggle with live recording in mpeg4 xvid or h264. If I was really interested I would record raw then run a script to convert to h264.  Note if you have a slower pc then yadif the deinterlacer may just push it to far, I generally cant do yadif and convert to mp3 with my older pc's.

 ________________________________________________   

mencoder for me has been the better solution out of the other choices mentioned - milage may vary, 
   _________________________________________________ 

I run a script every now and then to compress the audio. I have copied it below for you. The only requirement is you install a program called chcase. 

Note if you dont need to or dont want to bother, then remove the avi.pcm in the name and just leave it .avi (above in the record-tv script)  

so from a terminal I type this:  

for nam in *avi.pcm; do nice mencoder "$nam" -o "$nam.converted-avi" -ovc copy -oac lavc -lavcopts acodec=libmp3lame:abitrate=224; done;  chcase -x 's/avi.pcm.converted-avi/avi/' *avi.pcm.converted-avi

This will go through the directory and change any .avi.pcm file. Of course if you recorded raw you can put all your favourite mencoder options in here and let it run for the number of days needed to convert. Else if you have the latest hottest fastest pc with a volume knob that goes to 13 then you can replace the original pcm to the above oac options.  

Lastly when you are sure you have done the right stuff you can: 

rm -f *.avi.pcm  

PLEASE PLEASE PLEASE PLEASE note the last command has the highest potential for an outcome that ends in tears and holes punched in walls.  

Hope that was helpfull. The terminal is your friend and something I find very powerfull, the windows grafic stuff cant do this as easily or quickly 

__________________________________ 

Hope that helped. 

Shawn

Note just realised you need to make sure your saa7134 has its alsa option turned on. Depending on your computers flavour its done in
/etc/modprobe.conf

I copied the relevant section below

options saa7134-alsa index=2
options saa7134 noninterlaced=1 vbibufs=32 tsbufs=32 card=25,25,25,25 tuner=43,43,43,43 vbi_nr=1,2,3,4

Note the "options saa7134-alsa index=2" index sets the cards sound to dsp2. change yours here to suit. Note your sound card should be index=0

Generally auto detect works well so you probably just want "options saa7134 noninterlaced=1 vbibufs=32 tsbufs=32"

Thats about all the mysterious secrets I can think of for recording on linux. Its pretty simple when you understand that you just have to tell it how you want to set up the hardware. I have found not setting these options usually lands me in trouble. When its set its frozen in stone and my scripts I write work (well have worked for the last 10 years)

---

### Post by shawnvdm on 2009-07-26
Just carrying on, If you are interested in recording non-interlaced video (compresses better etc) then you can change the following 

set mencoder width=720:height=288

then instead of ydif

-vf dsize=768:576

and add outfmt=yv12

You loose a small bit of quality but etc etc. Mencoder has a phenominal amount of options, you tweak acording to your computers ability. 

Any way hope this is all usefull. It was interesting reading about your struggles. I hope to see some final solutions and learn from your success.

PS I still like the look of yadif over this so I don't use it. Note yadif itself has a number of options as well depending on processor power.

---

### Post by shane2peru on 2009-07-26
shawnvdm

Wow, thanks for the wealth of information!  I did finally get it working and failed to post my results here, at any rate I will do that now.  I don't pretend to understand all the options and everything that I used in my script, it was a long drawn out process of trial and error, mostly error. :)  
```

#!/bin/bash
#This is now working don't mess with this script!  It is a lot of work to get it back to what we have now.
read -p "Which device? TV=0 Composite1(RCA jack)=1  Svideo=3 (only from Camcorder):  "  n
read -p "What do you want to name the video?:    "  videoname
read -p "Where do you want the video saved to? (/home/$USER/ is assumed (type directory name without trailing slash/)):  " location
read -p "How many minutes for the video? (guess high if in doubt hh:mm:ss or mm:ss):    "  time
read -p "Hit play then hit enter" null  
b=$((time*60))

function sound {
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav /home/$USER/$location/$videoname.wav & sleep $b && killall arecord
}

####################### Primary command this is ##1 Number ONE!   ######################################
###  Any trials and errors must be done below this line! 
############This will be the opts disk that I burn.  Doing the same video twice. To see if there is any difference.
#mencoder -tv norm=NTSC:driver=v4l2:width=720:height=480:input=$n:fps=30000/1001:alsa:adevice=plug.saa7134 tv:// -endpos $time -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -noskip -skiplimit 4 -mc 0 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o /home/$USER/$location/$videoname.mpg #this one seems clearer than the old avi one I was using.

####################### ^^^^^^^^^^^^^Primary command this is ##1 Number ONE!^^^^^^^^^^^^^#############################
##################  This is the no opts disk that I recorded, keep for the testing purposes, don't change this line.
**#opts 1 - didn't really notice a difference with this and the options: ,harddup -noskip -skiplimit 4 -mc 0  **

mencoder -tv norm=NTSC:driver=v4l2:width=720:height=480:input=$n:fps=30000/1001:alsa:adevice=plug.saa7134 tv:// -endpos $time -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o /home/$USER/$location/$videoname.mpg

#opts 2 - came out a shorter video 20 min segment, was only 14min. 
#mencoder -tv norm=NTSC:driver=v4l2:width=720:height=480:input=$n:fps=30000/1001:alsa:adevice=plug.saa7134 tv:// -endpos $time -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d -noskip -skiplimit 4 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o /home/$USER/$location/$videoname.mpg


```
I cut out a lot of the extra junk I had left in my script with it commented out (right under opts 1 (I made it bold) is the line that is working for me).  You really have to pay attention to what is commented out and what isn't.  At any rate that gives me the quality that I want to turn it around and create a DVD out of it.  I'm using this on a pretty regular basis now.  I'm teaching Sign Language and recording the classes, and putting them on DVD with the out dated equipment that I have.  Works like a charm.  When I have to re-setup everything again in the future, I will have to re-visit this thread to re-learn how I did it all.  So, all notes and information here is helpful.  Thanks for sharing!

Shane

---

### Post by buntunub on 2009-11-28
Sorry I haven't been back at this thread in a while, and very much appreciate all the inputs - thats the beauty of the Open Source world! I hope this thread has been a help to all and please continue updating as new info becomes available.

---

### Post by Dieter-AR on 2010-05-15
I have a kworld pvr-tv 7134se, all channels working from scratch in TVtime but no sound, i have an onboard sound card and a 5.1 pci sound card, I'm using the last one, this tv tunner doesn't have audio output so i can't plug in a wire to the soundcard audio input. I tryed with "sox -r 32000 -2 -t alsa hw:1,0 -t alsa hw:0,0" but no success "sox FAIL formats: can't open output file `hw:0,0': snd_pcm_open error: Device or resource busy". I'm totally new on this OS so please give me some help :P. Thanks in advance for your time guys.

---

### Post by tommah04 on 2010-09-15
hello, I just bought this card and went through the steps, up until you say to start tvtime... this same thing happened before the steps as after...

tom@tom-desktop:~$ sudo tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/tom/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Segmentation fault
tom@tom-desktop:~$ 


i'm sure its probably something small and stupid, so any help would be great

---

### Post by sbjaved on 2012-12-06
I've been trying to get Kworld pci analog pvr 7134se to work with ubuntu 12.04. So far using card=153 and tuner=56, I get no video output in tvtime . It seems my card gets recognized but it won't recognize the tuner. I've tried tuner=43, tuner=17 as well with no luck. Here is dmesg:

```
02:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
	Subsystem: KWorld Computer Co. Ltd. Device [17de:712b]
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at fe400000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel modules: saa7134

```

```
saad@Home-Server:~$ dmesg | grep saa
[  303.242493] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[  303.242537] saa7134 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  303.242545] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 16, latency: 32, mmio: 0xfe400000
[  303.242556] saa7134[0]: subsystem: 17de:712b, board: Kworld Plus TV Analog Lite PCI [card=153,insmod option]
[  303.242578] saa7134[0]: board init: gpio is 80407f
[  303.268375] input: saa7134 IR (Kworld Plus TV Anal as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/0000:02:00.0/rc/rc0/input7
[  303.268430] rc0: saa7134 IR (Kworld Plus TV Anal as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/0000:02:00.0/rc/rc0
[  303.416001] saa7134[0]: i2c eeprom 00: de 17 2b 71 10 28 ff ff ff ff ff ff ff ff ff ff
[  303.416014] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416024] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416034] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416043] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416053] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416063] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416073] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416083] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416093] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416102] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416112] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416122] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416132] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416142] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.416152] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  303.495999] saa7134[0]: registered device video0 [v4l2]
[  303.496552] saa7134[0]: registered device vbi0
[  303.498308] saa7134[0]: registered device radio0
[  303.502661] saa7134 ALSA driver for DMA sound loaded
[  303.502694] saa7134[0]/alsa: saa7134[0] at 0xfe400000 irq 16 registered as card -2

```

Any help...?

---

### Post by sbjaved on 2013-01-09
Ok, I got my card working with card=59 tuner=48, but the picture quality is abysmal.

---

