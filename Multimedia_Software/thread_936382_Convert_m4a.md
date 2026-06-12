---
title: "Convert m4a"
date: 2008-10-02
forum: Multimedia Software
---

### Post by patrickaupperle on 2008-10-02
I am about to buy a new "mp3 player." It supports MP3/WMA/WAV/FLAC/APE. I have quite a few m4a files on my computer. What I want to know is:
1. What should I convert them too?
2. How would I go about converting them?

I am not afraid of the command line.

---

### Post by Yellow Pasque on 2008-10-02
The only thing that would make sense is MP3. You lose with a proprietary format like .m4a [http://wiki.videolan.org/MP4_audio](http://wiki.videolan.org/MP4_audio)
Basically, your audio is already in a compressed, lossy format, and converting will make the audio quality worse.

---

### Post by patrickaupperle on 2008-10-02
> **Temüjin said:**
> The only thing that would make sense is MP3. You lose with a proprietary format like .m4a [http://wiki.videolan.org/MP4_audio](http://wiki.videolan.org/MP4_audio)
Basically, your audio is already in a compressed, lossy format, and converting will make the audio quality worse.

MP3? Are you sure this is best? Not ogg or something? I want to lose the minimum amount of quality. Well, as long as the size does not jump up over 10 megs. I include this because I used some lame decoder/encoder combo that took my 2 mb m4a and made it a 15 mb flac. Yes this player does play oggs. I noticed it was not listed in the first post. Dang Newegg. The player is "Cowon D2" if that helps.

---

### Post by Paul41 on 2008-10-02
Going from one lossy to another lossy you are going to lose some quality no matter which you choose. I would personally choose ogg if my player supported it and mp3 otherwise.

---

### Post by patrickaupperle on 2008-10-02
> **Paul41 said:**
> Going from one lossy to another lossy you are going to lose some quality no matter which you choose. I would personally choose ogg if my player supported it and mp3 otherwise.

Thank you for the reply. Does ogg have any real advantage over mp3, besides being open (which is a real plus)? I ask because there is currently a tag reading issue with ogg. Tracks end up out of order.

---

### Post by Paul41 on 2008-10-02
Some people say ogg sounds better than mp3 and I think I have seen it has smaller file sizes (but I could be wrong about that). I would like to use ogg since it is open but my player won't use it so I use mp3 and it honestly works fine for me.

---

### Post by patrickaupperle on 2008-10-02
> **Paul41 said:**
> Some people say ogg sounds better than mp3 and I think I have seen it has smaller file sizes (but I could be wrong about that). I would like to use ogg since it is open but my player won't use it so I use mp3 and it honestly works fine for me.

Those are good enough reasons for me. Ill take sound quality and file size over album order. Thank you for your time. This community's helpfulness is the only reason I stuck with linux. Through all the good and bad times.

---

### Post by Yellow Pasque on 2008-10-02
> MP3? Are you sure this is best? Not ogg or something?
You didn't list ogg as a choice...

> I want to lose the minimum amount of quality.
Converting m4a to mp3 won't sound great. :S

---

### Post by patrickaupperle on 2008-10-02
> **Temüjin said:**
> You didn't list ogg as a choice...


Converting m4a to mp3 won't sound great. :S

> **patrickaupperle said:**
> Yes this player does play oggs. I noticed it was not listed in the first post. Dang Newegg.
Sorry I did not know at the time. It is clearly explained here, though. So, converting from m4a to ogg/mp3 has an audible quality drop?

---

### Post by haydnc on 2008-10-02
I would think the easiest way to find out if there is an audible quality drop would be to try it on one song and find out.

Start up Synaptic Package Manager and do a search for nautilus-script-audio-convert then select it and the other files listed as 'suggested for installation' to be installed.

You can then right click on one of those m4a files and you should be able to pick scripts - audio-convert and convert the selected file to mp3, ogg or do it twice and try both.

I don't remember any huge quality loss last time I used this to convert a m4a to mp3, but it could strongly depend on the original quality of the song compression and a bunch of other stuff like that.

---

### Post by Frak on 2008-10-02
You're buying a player that supports FLAC (Uncompressed)

Just convert it from m4a (super compressed) to FLAC (uncompressed) so you don't lose quality.

---

### Post by patrickaupperle on 2008-10-02
> **haydnc said:**
> I would think the easiest way to find out if there is an audible quality drop would be to try it on one song and find out.

Start up Synaptic Package Manager and do a search for nautilus-script-audio-convert then select it and the other files listed as 'suggested for installation' to be installed.
<snip>

I will try that. Thank you very much for the nice instructions. I'll get back to you tomorrow. Thank you again. As for the flac idea, maybe. I think file size might become an issue, though. Thank you all.

---

### Post by Frak on 2008-10-02
> **patrickaupperle said:**
> I will try that. Thank you very much for the nice instructions. I'll get back to you tomorrow. Thank you again. As for the flac idea, maybe. I think file size might become an issue, though. Thank you all.
The flac size won't increase at all if the already compressed m4a is treated as raw.

---

### Post by patrickaupperle on 2008-10-02
> **Frak said:**
> The flac size won't increase at all if the already compressed m4a is treated as raw.

If that is true, then that is sweet. Thank you. Ill try that too.

---

### Post by patrickaupperle on 2008-10-04
I finally got through research/testing. I am going for ogg. mp3 had a noticable sound quality decrease. flac had about 8x the file size. Both out. ogg wins. Thank you all who helped.

---

