---
title: "AVCHD on Ubuntu"
date: 2011-04-07
forum: Multimedia Software
---

### Post by Kururu Souchou on 2011-04-07
I'm sure that there should be a way to use AVCHD on Ubuntu. Don't recommend Wine. That's for my last resort, I'll use the program that came with my Panasonic. Throw me anything.

---

### Post by Revolutionary101 on 2011-04-08
What are you looking to do with AVCHD? Are you doing playback, editing, and/or exporting to or from AVCHD?

---

### Post by cotcot on 2011-04-08
I recommend to transcode the AVCHD file to more common file types and use the video editor of your choice to edit.
I recently discovered that kdenlive does a good job in transcoding avchd with the DVxHD codec. Load the clip (no need to put it on the timeline); right click gives a menu where you select "transcode". Then you get transcode options for file sizes. The filesize is larger but I saw that sound and video were synchronised. In kdenlive you can see the command line instruction with ffmpeg. I have not yet played with it to see if it works good with lower bitrates.
Before I did the transcoding with ffmeg (in terminal)but not with the DVxHD option.
Then editing with the transcoded files is easy. Editors enough (Kdenlive, Openshot, Pitivi, Kino, Blender, Cinelerra, Lives). Look and feel for yourselve which editor suits you best. There is a trade off to do between easy learning and features. In my case it is blender (keyframes and effects are great).

---

### Post by Kururu Souchou on 2011-04-13
> **Revolutionary101 said:**
> What are you looking to do with AVCHD? Are you doing playback, editing, and/or exporting to or from AVCHD?

I need to at least get videos from my camera PANASONIC BLAH I DONT KNOW

---

### Post by oldskool on 2011-04-13
I have AVCHD video too - m2ts files from a Sony HD Cam. 

I just need a way to burn them but authored as AVCHD so they will play in my blueray player. 

Any ideas? 

I dont want to use the bundled software under wine. There must be a solution for this native to ubuntu.

---

### Post by cotcot on 2011-04-13
Oldskool :  I have seen an AVCHD/blue ray option in the render menu of Openshot.

For transcoding my own AVCHD files (Canon HF100) I have found suitable parameters in Blender : 

Output : Xvid (preset)
Encoding :  Format AVI ; Codec Xvid (from Xvid preset)
Audio Codec : AC3  changed bit rate from default 32 to 256; changed samplerate from 44100 to 48000
25 fps
Thick the "De interlace" box in the video properties (the Canon stores 25p in 50i; each 1/25 s a full frame is taken and split in 2 half frames with pair and unpair lines at 1/50 s interval; the difference with real 50i is that in real 50i only half a frame is taken each 1/50 s alternating pair and unpair lines)

Sound is synchronised.
Than I use the transcoded files for video editing in Blender.
I do not burn DVD or Blue Ray because play back through HDMI directly from the laptop is too easy.

---

