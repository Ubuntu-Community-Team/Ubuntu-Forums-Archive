---
title: "Music Sound Track Isolater Program???"
date: 2007-09-12
forum: Multimedia Production
---

### Post by rendo on 2007-09-12
My buddy who's an uber linux newbie is looking for a program that can isolate music from soundfiles.  By this I mean isolate the tracks of say the guitars, drums, bass, etc etc.  I've tried looking for such a program, but have been unable to find one.  Does anyone know if one exists via Linux/Ubuntu that can do this for him?  Thanks.

---

### Post by stmiller on 2007-09-12
This is not possible to do, with any software on any platform. :)

---

### Post by rendo on 2007-09-12
They do it on TV though!?!?!? :(  Damn, well that sucks.

---

### Post by nalmeth on 2007-09-12
I think it is possible, but not as easy as seen on TV ;)

XMMS has a plugin that allows you to strip the vocals off of a track. There is some kind of functionality that performs that. It is not that simple to do, and its functionality depends on how the audio file was mastered

---

### Post by SuperDuck on 2007-09-12
"Vocal zappers" typically do some mid-range EQ dips as well as lowering the volume of the center of the stereo signal - the typical location of most vocals.  There are a few "bass removal" programs that claim to allow you to remove the bass track but are pretty much just high pass filters.  

Once something has been mixed from a multi-channel recoring setup to a stereo file, all you can futz with are the two tracks you're given!

---

### Post by liquid circuit on 2007-09-12
"Vocal remover" plugins/effects essentially work by subtracting the right audio channel from the left audio channel (and vice versa), which is easily performed by flipping the polarity of one of the audio channels.  If something was panned to the center of the stereo image, that means that sound would be basically identical in both channels, so by flipping the polarity of one of the channels that causes destructive interference to make it seem as if that center sound has been removed.
```
LeftOutput == LeftInput - RightInput
RightOutput == RightInput - LeftInput
```

A slight variant of this method is also commonly used in stereo "enhancers"/"wideners"/"expanders".

If you have a set of old-school speakers with typical speaker wire (red/black wires), you can approximate this effect by connecting one of the speakers with the black wire connected to the red contact and the red wire to the black contact; the other speaker should be connected normally (red-to-red, black-to-black)... this is perfectly safe and will not harm your equipment.  If you try this, you have to sit in the "sweet spot" (equal distance to both left and right speakers) to hear the effect maximally.

Lead vocals are typically mixed directly into the center of the stereo image, so their volume can be effectively manipulated through this method (or variations).  However, effects such as reverb/chorus are also typically applied to vocals (and practically every other instrument); these effects usually are also used to impart some sort of stereo effect, thus reducing the potential for complete removal through this type of vocal removal process.

Also, it is usually the lead/main vocal that is mixed directly to the center; backup/accompanying vocals may be mixed slightly/drastically panned to the left/right and therefore would not be significantly affected by this type of process.

Finally, it is not just vocals that are typically mixed directly to the center.  Typical pop production usually places the bass drum and the bass line directly in the center of the stereo image, causing those instruments to be significantly affected by this same "vocal" removal process.

I regret to inform you that it is at this time impossible to perfectly extract/remove an individual instrument for a stereo recording.  As a musician/wannabe producer, I can sympathize with you; I wish I could do it as well.... fixing bad recordings would be waaaay easier if it were possible.  This type of effect will always cause some sort of negative side-effect on the audio quality (ie: losing the impact of the bass drum/bass line, when you just wanted to remove the vocals).

The current alternative is to find a part of the song with the desired instrument/riff playing alone, chop that part out, and then loop it.... less than ideal, but this is also part of the art of sampling; a staple of hip-hop production.

This is not platform specific; this is the nature of recorded audio.

---

### Post by stmiller on 2007-09-16
It totally depends on how the panning and mixing is done for a track, for any of the various hack to sort of work.

You can isolate things which are dead center (vocals sometimes) and somewhat try to remove that center info, but you also remove *everything else* in the middle (bass, parts of drums, etc). Then you are only left with a mono sound file, and one which does not sound like the original, though you could slap it together and make a quasi-stereo hack to make a stereo version.

This is like trying to remove only "the blue paint" from an elaborate 19th century painting, or removing just the 'first violins' from a Mahler 1 recording. Not possible, as audio we have is a mix and individual instruments are not isolated in any part of the audio file.

---

### Post by directcharitycontribution on 2007-09-17
midi

---

