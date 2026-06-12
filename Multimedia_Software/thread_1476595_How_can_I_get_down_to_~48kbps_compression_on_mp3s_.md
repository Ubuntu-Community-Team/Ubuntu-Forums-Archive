---
title: "How can I get down to ~48kbps compression on mp3s using SoundConverter?"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Eoghanalbar on 2010-05-08
For some reason it seems like the lowest it goes is ~64kbps (~ implying variable bitrate).

So yeah, any thing that'll let me do the compression limbo better? (How low can you go? :P) A different program? Unlock bonus stage? What?

Thanks!

~Owen

---

### Post by arsadogi on 2010-05-26
I am wondering exactly the same thing.
Although the file size seems to be correct.

---

### Post by arsadogi on 2010-05-26
I think i found an answer.

When you choose VBR (variable bit rate) encoding then it does not make any sense to assign a bit rate encoding value when you convert an audio file to mp3. The common mp3 bitrates (125 kbps , 254 kbps, 320kbps) refer to CBR (constant bit rate) encoding.

As a sidenote , it is suggested to use VBR when the audio quality is the priority.

source -> [http://www.mp3machine.com/news/842](http://www.mp3machine.com/news/842)

---

### Post by Eoghanalbar on 2010-05-27
Actually, it MUST make some sense to assign a bit rate encoding value to VBR, because right there under preferences it gives you the option to set the target bit rate (from "~64 kbps" to "~320 kbps").

Note the "~" sign, which is absent when you switch to CBR.

Actually I emailed the guy in the credits of the program (Gautier Portet), and he said:

[I][INDENT]
You can change the quality by hand, using gconf-editor.
VBR quality 9, aka "~64 kbps" is the minimum in VBR mode, but you can
set the mode to CBR, and then change
the bitrate in gconf-editor: got to app/SoundConverter, and edit the
"mp3-cbr-quality" to the desired bitrate.
The valid bitrate in CBR mode are 8, 16, 24, 32, 40, 48, 56, 64, 80,
96, 112, 128, 160, 192, 224, 256 or 320.

Setting a custom quality/bitrate is planned for next version.

Cheers ![/INDENT][/I]

Which, frankly, I don't understand. I COULD figure it out if I tried, I think, but... who knows if I'll ever get around to it.

---

### Post by kassoulet on 2010-05-31
First "~" means approximately. So ~64 kbps should be near to 64 kbps.

MP3 has 3 bitrate control modes:
  CBR: all frames are stored using a contant bitrate.
  VBR: each frame gets a bitrate calculated using a quality setting and actual sound data.
  ABR: the same as VBR, but try to converge to a given bitrate instead of using only sound quality.

SoundConverter only allows you to choose from 6 quality levels, from 64 to 320 kbps.

If you absolutely want a specific bitrate, let's say 48 kbps, you'll have to change it by hand using gconf-editor. Let's play a bit: launch gconf-editor and soundconverter, locate the soundconverter keys in apps/SoundConverter, and change the settings in soundconverter's preference dialog, you'll see the gconf keys changing, nice uh?
You can now change the keys on gconf to force soundconverter to allow any bitrate you want.

Just remember that "~64kbps" in VBR mode is *already* the lowest possible quality (9). You should switch to CBR or ABR, and there you can change the corresponding key to the bitrate you want.

You will also notice that mp3 sounds awful in small bitrates :)

I hope this is clearer.

---

### Post by Eoghanalbar on 2010-05-31
I know the "approximately" sign, yes. A rate of approximately 48 kbps was what I was originally aiming for.

What I was thinking was, every Constant BR setting had a corresponding Variable BR setting, and I already knew that 48 kbps was *possible* (though not offered from the drop-down for either there), so I was extrapolating to guess that a 48 kbps rate was probably possible for both. Not so?

I'm compressing masses of language lessons, which I already know from past experience sound perfectly fine to me ultra compressed.

> If you absolutely want a specific bitrate, let's say 48 kbps, you'll have to change it by hand using gconf-editor. Let's play a bit: launch gconf-editor and soundconverter, locate the soundconverter keys in apps/SoundConverter, and change the settings in soundconverter's preference dialog, you'll see the gconf keys changing, nice uh?
You can now change the keys on gconf to force soundconverter to allow any bitrate you want.

Okay, so I really didn't know how to use that advice, so I just thought about it for a second, and typed "gconf-editor" into a terminal, and bang! I get a nice GUI I can intuitively figure out how to use! And now I've got my soundconverter preferences nicely telling me: "Bitrate mode: ABR ; Target bitrate: ~48 kbps". *Perfect.* Hell yeah that's nice! =D

I feel almost like not a complete frustrated newb anymore :P Thanks man!

So, Mr. Portet already told me the options for CBR ("8, 16, 24, 32, 40, 48, 56, 64, 80, 96, 112, 128, 160, 192, 224, 256 or 320"). It's the same spread for ABR, then?

Thanks again, Kassoulet! =D

---

