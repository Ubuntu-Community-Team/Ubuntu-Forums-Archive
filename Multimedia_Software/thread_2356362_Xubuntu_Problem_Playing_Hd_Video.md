---
title: "Xubuntu Problem Playing Hd Video"
date: 2017-03-22
forum: Multimedia Software
---

### Post by barryp3uk2 on 2017-03-22
I just did a clean install of Xubuntu 16.10 from Ubuntu Main 16.04 (including formatting my /home partition.)
  Since then I'm finding that I can't play HD 1080p x264 mkv files any  more. Basically they freeze VLC & cause serious jumping in Parole  & MPV Media Player.

  I didn't have this problem in Ubuntu Main 16.04 - I can't play files I played fine then.
  I have tried changing VLC settings such as file cache to no avail. If I run VLC from the terminal I get

> [INDENT]   [h264 @ 0x7f3358ce0420] error while decoding MB 54 29, bytestream -7
      [00007f3358c019b8] mkv demux error: Dummy Element at unexpected position... corrupted file?
      [00007f3358c019b8] mkv demux error: Dummy element too large or misplaced at 115569287... skipping to next upper element
      [00007f3358c019b8] mkv demux error: This element is outside its known parent... upping level

 [/INDENT]

Here are some laptop specs

> [INDENT]   Processor     : 2x Intel(R) Celeron(R) CPU B815 @ 1.60GHz   Memory         : 3895MB (1349MB used)
      Operating System   : Ubuntu 16.10 (Xubuntu)
      Kernel: Linux 4.8.0-41-generic, Architecture: x86-64
      -Display-
      Resolution     : 1366x768 pixels
      OpenGL Renderer        : Mesa DRI Intel(R) Sandybridge Mobile 
      X11 Vendor     : The X.Org Foundation 
      -Multimedia-
      Audio Adapter      : HDA-Intel - HDA Intel PCH
 [/INDENT]


Any suggestions?
  Many thanks, 
Barry

---

### Post by Keith_Helms on 2017-03-23
It's probably a video driver problem.   What video card is in the laptop?

---

