---
title: "TiMidity playback problems"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by function1 on 2006-11-17
I ran through the [MidiSoftwareSynthesisHowTo]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo"), but I did achieve the desired result. I did not install the timidity-patches-eaw package, and I do not think I need to: playing a midi file with timidity on the command line (i.e. `timidity mymid.mid') works. I modprobe'd all the modules listed (snd-seq-device, snd-seq-midi, snd-seq-oss, snd-seq-midi-event, and snd-seq) and then ran `timidity -iA -B2,8 -Os1l -s 44100'. I got the following message: ```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
```
Looks good. I have a look at `pmidi -l':
```
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
128:0     TiMidity                          TiMidity port 0
128:1     TiMidity                          TiMidity port 1
128:2     TiMidity                          TiMidity port 2
128:3     TiMidity                          TiMidity port 3

```
Cool. So then I try to play a midi with pmidi `aplaymidi --port 128:0 mymid.mid' and I hear nothing. No output in the pmidi terminal window, and in the timidity terminal I see: ```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
```
Looks normal to me, but I hear nothing. Again, playing the file directly with timidity as `timidity mymid.mid' works.
I was speaking with someone on the #ubuntu chan on freenode and he recommended that I look at `strace -fF aplaymidi --port 128:0 mymid', the output of which I have pastebin'd at [http://pastebin.com/826804]("http://pastebin.com/826804"). (Note the "<unfinished ...>" bit at the bottom--I had to ctrl+c it, because nothing was happening). I am not sure how a midi session is supposed to work, so I can really only look for explicit error messages in the strace output. I see "No such file or directory" for the files "ld.so.nohwcap' and "/etc/asound.conf". The asound.conf file sounds perhaps like its a bit more generic that just dealing with midi playback, yet audio seems to work fine overall on my system. I did not get anywhere with googling 'ld.so.nohwcap'.

P.S. I am running Edgy on a Thinkpad T60, audio chipset AD1981HD with Intel HDA interface.

---

